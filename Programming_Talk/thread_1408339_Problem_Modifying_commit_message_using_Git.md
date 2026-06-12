---
title: "Problem Modifying commit message using Git"
date: 2010-02-16
forum: Programming Talk
---

### Post by sharpdust on 2010-02-16
Hello, I am trying to edit a commit message using git. Here is the following commands that I have done:

```
git commit -a -m "A message with a tpyo"
git push origin master
git commit -a --amend "A message with a typo"
git push origin master

```

When I do the last command, git responds back with:

```
To ssh://git@project/testing.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'ssh://git@project/testing.git'
To prevent you from losing history, non-fast-forward updates were rejected
Merge the remote changes before pushing again.  See the 'non-fast-forward'
section of 'git push --help' for details.
```

If I try ```
git push --force origin master
```, it says:

```
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 301 bytes, done.
Total 3 (delta 1), reused 0 (delta 0)
+ refs/heads/master testing eric DENIED by fallthru
error: hook declined to update refs/heads/master
To ssh://git@desiree/testing.git
 ! [remote rejected] master -> master (hook declined)
error: failed to push some refs to 'ssh://git@project/testing.git'
```

The only way to get around this is to ```
git pull origin master
```, but that puts the message:

```
Merge branch 'master' of ssh://project/testing
```

into the log which is not what I want.

I'm absolutely positive there have not been any changes to the repository. Any ideas on why git's complaining about this?

---

### Post by sharpdust on 2010-02-16
Nevermind, I apologize for this message, it was a git-olite configuration problem.

---

