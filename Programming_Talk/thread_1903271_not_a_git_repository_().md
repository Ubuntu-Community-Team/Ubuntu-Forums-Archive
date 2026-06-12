---
title: "not a git repository (?)"
date: 2012-01-02
forum: Programming Talk
---

### Post by fluca1978 on 2012-01-02
Hi all,
I'm having a problem with a few repositories I manage with git. I moved the repositories to another hard disk and today I have on all of them:

```
$ git status
fatal: Not a git repository (or any of the parent directories): .git

```

However all the data for the repository is still there:

```
$ ls -al
total 8
drwx------ 1 luca luca  464 2012-01-02 09:42 .
drwx------ 1 luca luca 4096 2012-01-02 09:42 ..
drwx------ 1 luca luca    0 2012-01-02 09:42 .externalToolBuilders
drwx------ 1 luca luca 4096 2012-01-02 09:42 .git
drwx------ 1 luca luca    0 2012-01-02 09:42 .settings
drwx------ 1 luca luca    0 2012-01-02 09:42 src
drwx------ 1 luca luca  256 2012-01-02 09:42 target

$ du -hs .git/*
0       .git/branches
0       .git/hooks
0       .git/info
20K     .git/logs
36K     .git/objects
512     .git/refs


```

I have to mention that I moved the repositories from an ext3 fs to a NTFS one, that is mounted as fuseblk, so it could be a permission problem. However even copying back the repositories to an ext3 fs did not solved the problem.

My system is the following:

```
$ uname -a
Linux lferrar3 2.6.35-29-generic #51-Ubuntu SMP Fri Apr 15 17:12:35 UTC 2011 x86_64 GNU/Linux

$ git --version
git version 1.7.1


```

Any idea of what happened?

---

### Post by fluca1978 on 2012-01-02
I found that HEAD and refs/heads are missing, while the remote heads are still in place. This avoid me to run even git-fsck. Any idea on how to solve the problem? Please note that objects are still in place.

---

