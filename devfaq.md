# moview.io : Developer guidelines

This document defines a list of *good practices* that every developer should
follow.

## Test your code!

This is a must so we have mandatory rules:

First one, core libraries that implements the bussiness logic of the platform
**must be perfectly tested** and integrated with *TravisCI* ( our continuous
integration service ).

Next, all remaining tools, services and applications are optional but we
recomend to do that and it is planned on the [roadmap](roadmap.md) on a
future milestone.

* TODO: How to manually test?
* TODO: How to manually coverage?

## Lint your code!

Please, lint your code before pushing it to *develop* or *master*.

All projects should implement a `make lint` task that analyzes the source
code files searching for linting errors.

This analisis uses the official tool `go-lint`.

## Document your work!

This is important, you see that this project has A LOT of documentation?

Please follow always this rule when you work on moview.io:

1. Check current documentation files for undocumented topics.
2. Check involved component's TODO file for references.
3. Write your documentation.
4. Start discussion :)

## Use git-flow to handle branches and releases.

Another tool that helps a lot, following a session of work fixing an issue
and releasing a new version is described as an example:

```
$ git clone http://github.com/moviewio/tmdb
$ cd tmdb
$ export GOPATH="`pwd`"
$ make deps
$ make build
$ # Now we are going to start to work on an issue, for example number 84
$ git flow feature start 84
$ # The previous command creates a local branch named "84" from develop.
$ [ ... modify files, write tests, write docs ... ]
$ git commit -am "Fix #84"
$ # You can commit as much as changes you need
$ git flow feature finish #84
$ # It merges branch 84 into develop and removes branch 84
$ git push origin develop
$ # Now create the release, for example version 0.3.55
$ git flow release start 0.3.55
$ [ ... bump version, final fixes ... ]
$ git commit -am "bump to 0.3.55"
$ # This change must be commited too
$ git flow release finish 0.3.55
$ # This command merges branch 0.3.55 to develop and develop to master,
$ # creates a tag 0.0.55 and removes local branch.
$ git push origin --all; push origin --tags
$ # Push all changes to github!
$ # Done! Weeeeee! :D
```
