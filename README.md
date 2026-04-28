# Crawl4NK Daily CronJob

This project runs a scheduled GitHub Actions workflow to help with interview prep.

It integrates with [Crawl4NK](https://github.com/z0l0y/Crawl4NK) and does the following every day:

1. Pulls the latest Crawl4NK code.
2. Builds `app.json` from workflow inputs, repository variables, and secrets.
3. Crawls backend interview-experience posts from Nowcoder.
4. Exports results (xlsx / md / txt) and uploads them as workflow artifacts.
5. Sends an email summary after the crawl run.

## Main Goal

Automate daily backend interview-experience collection so learning and review can be consistent.

## Configuration

Required secrets:

- `CRAWL4NK_COOKIE`
- `EMAIL_ADDRESS`
- `EMAIL_PASSWORD`

Optional secret:

- `MAIL_TO` (defaults to `EMAIL_ADDRESS` if empty)

Optional repository variables:

- `CRAWL4NK_KEYWORDS`
- `CRAWL4NK_MAX_PAGES`
- `CRAWL4NK_MAX_ITEMS_PER_KEYWORD`
- `CRAWL4NK_OUTPUT_FILE`
- `CRAWL4NK_OUTPUT_FORMATS`

The workflow also supports manual trigger (`workflow_dispatch`) with temporary input overrides.

## Schedule

GitHub Actions schedules run in UTC and can be delayed. This workflow is configured to run at
00:00 China Standard Time (UTC+8) using `0 16 * * *` in the cron expression.

If you need an immediate run or want to validate the workflow, use the manual trigger in the
Actions UI.
