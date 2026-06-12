---
title: "[SOLVED] find(1) frontend script puzzle"
date: 2009-01-02
forum: Programming Talk
---

### Post by Cracauer on 2009-01-02
Using find(1):

I can't figure out how to properly combine '-prune' and '!'.  I want to kill certain subdirectories from the results.  "kill" means that 1) I don't want to traverse into them and 2) I don't want them to show up in results.

I can't figure it out. Here is what I have:
```

# create test data
mkdir -p ll/.svn
mkdir -p ll/.xvpics
touch ll/.xvpics/l1       # don't want to see this
touch ll/l1               # want to see this

find . \( -name .svn -prune -o -name .xvpics -prune \) -o \
		\( \! -name .xvpics \! -name .svn \) \
	-name '*l1*'

```

This prevents going into .svn and .xvpics, but it lists .svn and .xvpics (the directories themselves) in the output:

```

$ ./,find
./ll/.svn        # incorrect
./ll/.xvpics     # incorrect
./ll/l1          # correct

```

Any ideas?

A quick google only shows that I'm not the only one with the problem.

---

### Post by odyniec on 2009-01-02
Adding "-false" right after "-prune" should help:
```
find . \( -name .svn -prune -false -o -name .xvpics -prune -false \) -o \
		\( \! -name .xvpics \! -name .svn \) \
	-name '*l1*'
```

---

### Post by Cracauer on 2009-01-02
That does it, thank you so much.

---

