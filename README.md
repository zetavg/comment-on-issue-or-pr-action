# Comment on Issue or PR Action

A simple, zero-dependency, and lightweight action to comment on an issue or PR.

## Sample Usage

```yaml
# ...

jobs:
  example:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      # These permissions are required to comment on an issue or PR
      issues: write
      pull-requests: write
    steps:
      - name: Comment on issue
        id: comment-on-issue
        uses: zetavg/comment-on-issue-or-pr-action@v... # Replace with the latest version
        with:
          issue-number: ${{ github.event.issue.number }} # Or github.event.pull_request.number
          content: |
            Hi there! This is a comment on an issue.

            Here's a list of awesome things:

            * Thing 1
            * Thing 2
            * Thing 3
        # Optional: use a custom GitHub token to comment as a different user or bot
        # github-token: ${{ secrets. ... }}

      - name: Print comment info
        run: |
          echo "Comment ID: ${{ steps.comment-on-issue.outputs.comment-id }}"
          echo "Comment node ID: ${{ steps.comment-on-issue.outputs.comment-node-id }}"
          echo "Comment API URL: ${{ steps.comment-on-issue.outputs.comment-api-url }}"
          echo "Comment HTML URL: ${{ steps.comment-on-issue.outputs.comment-html-url }}"
```
