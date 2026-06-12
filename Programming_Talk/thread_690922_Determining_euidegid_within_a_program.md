---
title: "Determining euid/egid within a program"
date: 2008-02-07
forum: Programming Talk
---

### Post by tinkertim on 2008-02-07
Hello to all, 

In GNU C, what is the safest and simplest way to determine if the egid/euid of a program is different from the user running it?

I've already obtained the uid/gid/euid/egid of the user (and groups), i just want to have additional built in sanity (and possibly disabling some features) should the following occur :

euid/egid of the program is 0, the user does not belong to sudoers, wheel, admin (etc).

euid/egid of the program points to another privileged user, or a privileged group which the user is not a member of.

I know some people will be running my program using the setuid/setgid bits, even though I advise against it, since its faster and easier than dealing with POSIX ACLs. I'd like  to be extra defensive, but can't seem to figure out how to check (from within the program) if the program's euid/egid differs from the user's, without actually reading the attributes of argv[0]. I hope to not do that, since it opens yet another descriptor before I can tell if the program is or isn't running with setuid :) I hope I'm not confusing anyone.

Any help is appreciated.

---

### Post by tinkertim on 2008-02-08
Nevermind, my own typo was driving me nuts. geteuid() is now returning what I was expecting it to return.

---

