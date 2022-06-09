# Bash script for Dockerfile

This page explains how to create a bash script, which will be invoked in a Dockefile to install Ubuntu package dependencies as part of a container image. This provides a starting point. After completing steps 1-3, you may add specific packages depending on the use case.

1. First use the `set` built in to set shell variables and positional parameters.

```bash
set -euo pipefail
```

Combined flags are explained below.

- e: Exit immediately if a pipelines returns a non-zero status.
- u: Treat unset variables and parameters other than the special parameters `@` or `*` as an error when performing parameter expansion.
- o: Set option. In this case `pipefail`. 
  - If set, the return value of a pipeline is the value of the last (rightmost) command to exit with a non-zero status, or zero if all commands in the pipeline exit successfully. This option is disabled by default.  

2. Next, add line to tell apt-get that we will not give manual feedback during installation.

```bash
export DEBIAN_FRONTEND=noninteractive
```

3. Next update the index.

```bash
apt-get -y update
```
