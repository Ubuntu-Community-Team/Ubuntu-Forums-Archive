---
title: "Git Pull All Related Branches?"
date: 2010-09-26
forum: Programming Talk
---

### Post by huangyingw on 2010-09-26
Hello all,
     Suppose the output of my ```
git branch -a
``` is as bellow:
```
* dev
  gcb
  gps
  master
  remotes/gh/dev
  remotes/gh/gcb
  remotes/gh/gps
  remotes/gh/master
  remotes/origin/dev
  remotes/origin/gcb
  remotes/origin/gps
  remotes/origin/master

```
     My goal is to write such a script to do iteration like this:git pull origin/dev into local/dev;git pull gh/dev into local/dev;git pull origin/gps into local/gps;git pull gh/gps into local/gps, etc.
     I totally have no idea about this...

---

