
Updating the Proper application
-------------------------------

I use Tyson to contain the Git repositories obtained from
Github, and modified to conform to the Paddington-Build
structure.

To synchronise the Tyson repositories with the latest
changes on Github, I pull the latest repository, and then
push the changes to Tyson.

Location:

    2014-01-13T11:41:51Z phm@Optiplex:~/Repos/github/proper

Inspect the local repository, and pull the latest from the remote:

    1008> git branch --all
    * master
      remotes/origin/HEAD -> origin/master
      remotes/origin/fsm
      remotes/origin/master
      remotes/origin/parse_transform
      remotes/origin/statem

    1015> git remote -v
    origin  https://github.com/manopapad/proper.git (fetch)
    origin  https://github.com/manopapad/proper.git (push)

    1009> git pull
    remote: Counting objects: 64, done.
    remote: Compressing objects: 100% (40/40), done.
    remote: Total 64 (delta 30), reused 45 (delta 24)
    Unpacking objects: 100% (64/64), done.
    From https://github.com/manopapad/proper
       aa6b088..c37cab8  master     -> origin/master
    Updating aa6b088..c37cab8
    Fast-forward
     Makefile                    |   20 ++++++++++++++------
     README.md                   |    2 +-
     THANKS                      |   10 +++++++---
     rebar.cmd                   |    7 +++++++
     rebar.config                |    3 ++-
     src/proper.erl              |   20 ++++++++++----------
     src/proper_arith.erl        |    6 +++---
     src/proper_statem.erl       |   28 +++++++++-------------------
     src/proper_transformer.erl  |   17 +++++------------
     src/proper_types.erl        |    6 +++---
     src/proper_typeserver.erl   |   15 +++++++++++++--
     test/proper_specs_tests.erl |   16 +++++++++++++---
     test/proper_tests.erl       |    4 ++--
     13 files changed, 89 insertions(+), 65 deletions(-)
     create mode 100644 rebar.cmd


Send the changes to Tyson:

    1017> git remote add tyson tyson:/export/home/gitrepos/proper

    1018> git remote -v
    origin  https://github.com/manopapad/proper.git (fetch)
    origin  https://github.com/manopapad/proper.git (push)
    tyson   tyson:/export/home/gitrepos/proper (fetch)
    tyson   tyson:/export/home/gitrepos/proper (push)

    1019> git push tyson
    X11 forwarding request failed
    Counting objects: 69, done.
    Delta compression using up to 2 threads.
    Compressing objects: 100% (55/55), done.
    Writing objects: 100% (55/55), 6.79 KiB, done.
    Total 55 (delta 38), reused 0 (delta 0)
    To tyson:/export/home/gitrepos/proper
       f7fa99e..c37cab8  master -> master




The bare repository on Tyson is now updated with the latest
changes from Github.  Now I switch to a local copy of the
Tyson repository and merge the changes in the `master`
branch into the `version/1.1.1` branch:


Pull the updates in the Tyson repository:

    2014-01-13T11:45:05Z phm@tyson:~/Repos/gitrepos/proper
    2852> git checkout master
    Switched to branch 'master'
    Your branch is behind 'origin/master' by 16 commits, and can be fast-forwarded.

    2853> git pull
    Updating f7fa99e..c37cab8
    Fast-forward
     Makefile                    |   20 ++++++++++++++------
     README.md                   |    2 +-
     THANKS                      |    9 ++++++---
     rebar.cmd                   |    7 +++++++
     rebar.config                |    3 ++-
     src/proper.erl              |   18 +++++++++---------
     src/proper_arith.erl        |    6 +++---
     src/proper_statem.erl       |   28 +++++++++-------------------
     src/proper_transformer.erl  |   17 +++++------------
     src/proper_types.erl        |    6 +++---
     src/proper_typeserver.erl   |   15 +++++++++++++--
     test/proper_specs_tests.erl |   16 +++++++++++++---
     12 files changed, 85 insertions(+), 62 deletions(-)
     create mode 100644 rebar.cmd

    2856> git branch
    * master
      version/1.1.1

Checkout `version/1.1.1` and merge the changes from `master` into it:

    2857> git checkout version/1.1.1
    Switched to branch 'version/1.1.1'

    2858> git merge master
    Auto-merging src/proper_typeserver.erl
    Auto-merging src/proper_types.erl
    Auto-merging src/proper_transformer.erl
    Auto-merging src/proper_statem.erl
    Auto-merging src/proper_arith.erl
    Auto-merging src/proper.erl
    Merge made by the 'recursive' strategy.
     Makefile                    |   20 ++++++++++++++------
     README.md                   |    2 +-
     THANKS                      |    9 ++++++---
     rebar.cmd                   |    7 +++++++
     rebar.config                |    3 ++-
     src/proper.erl              |   18 +++++++++---------
     src/proper_arith.erl        |    6 +++---
     src/proper_statem.erl       |   28 +++++++++-------------------
     src/proper_transformer.erl  |   17 +++++------------
     src/proper_types.erl        |    6 +++---
     src/proper_typeserver.erl   |   15 +++++++++++++--
     test/proper_specs_tests.erl |   16 +++++++++++++---
     12 files changed, 85 insertions(+), 62 deletions(-)
     create mode 100644 rebar.cmd




The `version/1.1.1` branch that is used by the
Paddington-Build is updated with the latest changes.




