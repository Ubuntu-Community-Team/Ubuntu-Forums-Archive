---
title: "Sword of Fargoal compiling"
date: 2008-12-10
forum: Packaging and Compiling Programs
---

### Post by anjilslaire on 2008-12-10
Hey all,

1st, The source for this game is available in th PC Zip file at [http://www.fargoal.com/](http://www.fargoal.com/)

Now, the source does include a readme that simply requires 'make' for linux. This works fine, and th game works great.

What I'd like is to create a deb for easy install. I've tried checkinstall a few times, and have tried to compile it via
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

However, it fails at checkinstall with the following error:
```

make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

Any thoughts? Can someone try this and report back, or am I missing something painfully obvious?

Thanks :)

---

### Post by anjilslaire on 2008-12-11
bump

---

### Post by anjilslaire on 2008-12-15
Last bump.

No takers?

---

### Post by christhemonkey on 2008-12-21
Please see here: [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

And maybe here: [http://ubuntuforums.org/showthread.php?t=2356](http://ubuntuforums.org/showthread.php?t=2356)

Also read this link from the stickies: [https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

---

### Post by anjilslaire on 2008-12-21
Nope, as mentioned previously, checkinstall fails.

I can compile it with 'make' and get a viable bianey to run th game just find. The problem is there is no configure file, and after make is successful, giving me my binary, checkinstall fails with the error noted and aborts.

Your help is appreciated, but I did do some homework first ;)

---

