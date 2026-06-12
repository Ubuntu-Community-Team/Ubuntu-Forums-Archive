---
title: "Enabling core dumps (across sessions)"
date: 2007-07-28
forum: Programming Talk
---

### Post by Yarias on 2007-07-28
I know "ulimit -c [size]" will enable core dumps for the current session, but I'm not exactly sure how to enable them permanently (or enable them outside of a terminal).

I've heard that the proper place to do this is in ~/.bash_profile (I think that's the name).

If it makes a difference, I will not be running the program through a terminal, but in an IDE.

Thanks for any help!

---

### Post by jpkotta on 2007-07-28
Just add it to ~/.bash_profile. Putting a line in ~/.bash_profile is literally like typing it in the terminal, except it runs when you first log in and thus affects everything you do.  Adding a ulimit command in there will set that limit for all shells you start during that login.
```
help ulimit
```
```
man bash
```
See the INVOCATION section of the bash man page.

---

