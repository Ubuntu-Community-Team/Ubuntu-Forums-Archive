---
title: "git: Your branch and 'origin/master' have diverged, and have 1 and 3 different commit"
date: 2023-11-09
forum: Programming Talk
---

### Post by maketopsite on 2023-11-09
... after I had removed last 3 commits and pushed to remote:
```

git reset HEAD^ --hard
git reset HEAD^ --hard
git reset HEAD^ --hard
git push https://gitlab.com/myname/myproj  -f
```

```
git status
On branch master
Your branch and 'origin/master' have diverged,
and have 1 and 3 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)

nothing to commit, working tree clean
```

What will happen please if I run 
```
git pull
``` ?

---

### Post by maketopsite on 2023-11-12
output of 

```
git pull

```was empty but it has solved the problem.

---

