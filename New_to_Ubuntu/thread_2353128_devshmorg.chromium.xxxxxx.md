---
title: "/dev/shm/org.chromium.xxxxxx"
date: 2017-02-19
forum: New to Ubuntu
---

### Post by alabamatoy2 on 2017-02-19
If I do a *sudo lsof /dev/shm* I get a bunch of seemingly random files open like /dev/shm/org.chromium.snzoQ9 where the last part of the filename is random 6 character gibberish.  What is this, and what is chromium?  Can I stop it, delete it, uninstall it?  If so, how?

My Ubuntu 16.04LTS box is somewhat on the edge as far as being able to do what is asked of it (zoneminder, mostly) and I want to turn off and/or remove whatever is unnecessary.

---

### Post by oldrocker99 on 2017-02-19
Chromium is the open-source version of Google Chrome; it's usually part of most distros. You don't **need** it, especially if you are running Chrome. Or Firefox, or Opera, or...

To get rid of it:```
sudo apt purge chromium
```

---

### Post by alabamatoy2 on 2017-02-19
I just tried...
```
~$ sudo apt purge chromium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'chromium' is not installed, so not removed
```

What else can it be?

---

### Post by Habitual on 2017-02-19
> **alabamatoy2 said:**
> What else can it be?

open a terminal and issue
```
watch -n 1 "lsof +D /dev/shm"
```

This will open a watch on any process using anything in /dev/shm/

Ctrl+[cC] to terminate the watch once you've identified it.
You will have to "babysit" this watched process. Stuff comes and goes in shm (AFAIK)
at will opening and closing of programs (usually graphical?).

Hope that helps.

---

### Post by alabamatoy2 on 2017-02-19
> **alabamatoy2 said:**
> What else can it be?

Its firefox.  Apparently Firefox somehow uses chromium.  Well, blow me down.  Learn something new every day.....

---

