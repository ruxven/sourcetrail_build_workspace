# Sourcetrail Build Workspace

## What is this?

A repository of scripts for building the abandoned [CoatiSoftware Sourcetrail](https://github.com/CoatiSoftware/Sourcetrail) project using Podman containers.

## Why?

It's a useful tool for analyzing C/C++ projects (Java and Python too) and quickly developing an understanding of how the system fits together. If it can be updated to work for newer distributions, it might be able to breathe new life into it (or a potential fork).

### Why not make a fork?

It's not meant to be a fork, though that may come later when upgrading the indexers to use newer LLVM releases.

### Why Podman?

Short answer: it's what Bazzite uses ;)

Longer answer: container-based development enables a system to support many different build environments. Podman offers security integrations over Docker, but the syntax for the Containerfile is largely the same. There are some quirks, but overall it is useful to know how to work with. Docker is normally my go-to, but Podman may have more organizational support given its alignment with Red Hat and security stance.

## How do I use it?

1. Clone this repository
1. Run `./rc.setup`
    1. This clones the original CoatiSoftware repository, and applies a patch for RHEL8 support.
1. Run `./rc.build_container_sourcetrail_el8`
    1. This builds the podman container for compiling sourcetrail in, tags as `sourcetrail-dev-el8:latest`
1. Run `./rc.build_sourcetrail_el8`
    1. Builds the Sourcetrail code in the Podman container using script `./scripts/build_sourcetrail_el8`

This can be expanded on for different distributions and/or LLVM versions. There exists an Ubuntu 20.04 container and build for reference, as it Should Just Work&trade;.
