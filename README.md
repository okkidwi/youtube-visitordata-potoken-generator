# YouTube VisitorData & PoToken Generator

Credit to [YunzheZJU](https://github.com/YunzheZJU/youtube-po-token-generator)

## Introduction

This project generates `{ visitorData, poToken }` pairs, which are used for YouTube's PoToken authentication process. The generation is automated via a GitHub Actions workflow that can be triggered manually or scheduled daily.

## How it works

The workflow uses the `youtube-po-token-generator` package to generate fresh `visitorData` and `poToken` pairs. These are logged and saved into a file, which is then uploaded as an artifact for easy access. It generates a valid `poToken` using the `visitorData` fetched from YouTube.

### Workflow Steps:
1. **Checkout Repository**: The latest code from the repository is pulled.
2. **Install Dependencies**: The required packages (`youtube-po-token-generator` and `date-fns`) are installed.
3. **Generate Data**: For each entry, a fresh pair of `visitorData` and `poToken` is generated and timestamped.
4. **Log & Upload**: The results are logged to `generated_results.log` and uploaded as an artifact.

## Automation with GitHub Actions

The GitHub Actions workflow automates the entire process of generating visitor data and PoTokens. It provides both **manual and scheduled triggers**:

- **Manual Trigger**: The workflow can be manually executed with a specified number of entries for visitor data and PoTokens. This is useful when you need to generate a specific amount of data on demand.
  
- **Scheduled Trigger**: The workflow is set to run automatically on a daily schedule (00:00 UTC). This ensures that fresh visitor data and PoTokens are generated regularly without manual intervention.

The automation involves the following steps:
1. **Checking out the latest repository code** to ensure the latest changes are applied.
2. **Installing the required Node.js packages** (`youtube-po-token-generator` and `date-fns`) to handle the generation and timestamping.
3. **Generating visitor data and PoTokens** by invoking the `youtube-po-token-generator` package, logging the results, and storing them in a file.
4. **Uploading the results as artifacts**: Once the process completes, the generated results are saved in a log file (`generated_results.log`) and uploaded as a GitHub artifact, making it easy to access and download.

By automating this process, you can ensure that valid PoTokens and visitor data are generated consistently and with minimal manual effort, improving efficiency and reliability.

## Related Works

This project is inspired by [iv-org/youtube-trusted-session-generator](https://github.com/iv-org/youtube-trusted-session-generator).

## Forked from

This repository was forked from [YunzheZJU/youtube-po-token-generator](https://github.com/YunzheZJU/youtube-po-token-generator).

## More

- Debugging the source code from YouTube was challenging due to dynamic changes in the token generation process.
- Modifying injected code or userAgent values can affect the validity of the generated `poToken`.
