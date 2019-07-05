# Merge driver for prettier.

A very simple merge driver that allows you to automatically rebase and merge
commits using prettier.

## Git Wrapper

`git-wrapper` contains a wrapper script which will install this merge driver,
and then uninstall it immediately after the command has completed. This
wrapper can be used for running rebases.

```shell
$ /path/to/git-wrapper rebase central/branches/default/tip
```

Do note that if a merge conflict occurs, `git-wrapper rebase --continue`
should be used rather than using `git` directly.

## Manual Setup

In `.git/config`:

```
[merge "prettier-format"]
  name = prettier-format merge driver
  driver = /path/to/prettier-format-merge %O %A %B %P
  recursive = binary
```

In `.git/info/attributes`:

```
*.js  merge=prettier-format
*.jsx merge=prettier-format
*.jsm merge=prettier-format
```
