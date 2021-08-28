# actions-release

This is a composite GitHub Actions for my projects; it's responsible for release.

```yaml
on:
  workflow_dispatch:
    inputs:
      version:
        description: version. The next release version (without prefix v)
        required: true
      apply:
        description: apply. Specify whether the actual release should be performed or not
        default: "false"
        required: true
jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      # Do something before running this action

      - uses: yykamei/actions-release-actions@main
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          tag: v${{ github.event.inputs.version }}
          title: Release v${{ github.event.inputs.version }}
          apply: ${{ github.event.inputs.apply }}
```
