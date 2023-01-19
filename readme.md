# Git Workflow

### Overall strategy:
- build off the `dev` branch for consensus codebase.
- push or submit "features" (1 or more commits) as pull-requests on unique branch names, and merge into dev branch via Github
- pull down updates on the dev branch, never commit on the dev branch
- use `git rebase dev` on your feature branch to update your teamates code into your feature before pushing
- create a new feature branch from dev to submit your next batch of commits.

### Things to understand:
 - understanding the "state" of git.
 - creating branches vs switching branches
 - how git incorporates new commits: always *on top* of all previous commits in the same order
 - how to use git rebase correctly, how to create and merge pull requests
 - how to resolve merge conflicts


### Undertanding the state of git
Use `git log` to check what commits you have, and what order they are in on the current branch you are on.

Use `git status` to understand what file changes have happend, what's in staging and if you're within a rebase, and what branch you are on.

Use `git branch` to view all your exisiting local branches and `git branch -a` to view local + remote branches.

### Creating and switching branches:

To create a branch use the `-b` flag with `git checkout`:

```
git checkout -b my-new-branch
```
Note that all the commits from what branch you are currently on will come into the new branch you create.

Don't use the `-b` flag when switching between already existing branches

```
git checkout my-exisiting-branch
```

Use `git branch -D my-stale-branch` to delete an old local branch

### Prepping to submit your commits

```

> git checkout feature-branch-xxx # now you should be on feature-branch-xxx
> git add <file1 file2 file3>
> git commit -m "feature-xxx: did x,y,z"

> git checkout dev
> git pull origin dev

> git checkout feature-branch-xxx
> git rebase dev
(complete any merge conflicts)
> git rebase --continue (if nec)

> git log # check all your commits are on top, none below

> git push origin feature-branch-xxx

(use github to merge in the PR into dev)
