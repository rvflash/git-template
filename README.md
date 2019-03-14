# Git template

With the option `--template` on the `git init` command, you can specify a directory from which templates will be used.
To do it, whenever you initialize a new repository, you can add a section in your `~/.gitconfig` file.
More information in the documentation of [Git template directory](https://git-scm.com/docs/git-init#_template_directory).

This project provides a directory to use as `git` template directory to simplify the workflow.
Usefull to create global hooks!

> For now, only Golang code has a template directory with a `pre-commit` hook inside.


## Installation

```bash
$ git clone https://github.com/rvflash/git-template.git ~/.git-template
```

## Quick start

To use it for all your future repositories, edit the `~/.gitconfig` and add this section:

```bash
[init]
    templatedir = ~/.git-template/go
```

Or you can specify to use it on the fly when initializing a repository:

```bash
$ git init --template="~/.git-template/go"
```

### Repository with Go code

Exposes a pre-commit hook that launches all the tests, `golint`, `goimports`, `gofmt` and `govet`.
If one of them failed, the commit is aborded.

In order to use more linters without degrading performance, if available, `golangci-lint` is used.