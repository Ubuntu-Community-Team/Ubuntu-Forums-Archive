---
title: "Error on ./configure"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by kIsS on 2008-05-03
Hello,

Upon running ./configure i receive this message on the last line; 

**Please update PKG_CONFIG_PATH to point at location of gtkmm pkgconfig files directory**

So!  how would i do this? :)

---

### Post by FredB on 2008-05-03
sudo apt-get install build-essential

sudo apt-get install pkgconfig 

Just a guess of course.

---

### Post by ramjet_1953 on 2008-05-03
What are you trying to install?

Have you installed the build essential package?

[COLOR="Blue"]sudo apt-get install build-essential[/COLOR]

Is the package that you are trying to install in the repositories?

Have you enabled the extra repositories in Synaptic?

Have you done your homework and reading-up on compiling from sourcecode and satisfying dependencies?

If you are new to 'nix, I would suggest that you stick to stuff in the repositories and learn to crawl, before you walk.

Regards,
Roger

---

### Post by Perfect Storm on 2008-05-03
> **kIsS said:**
> Hello,

Upon running ./configure i receive this message on the last line; 

**Please update PKG_CONFIG_PATH to point at location of gtkmm pkgconfig files directory**

So!  how would i do this? :)

```
[size=1]sudo apt-get update && sudo apt-get upgrade
sudo apt-get install libgtkmm-2.4-dev[/size]
```

Note, this is on 8.04 the libgtkmm might have a lower number in previous version of Ubuntu.

---

### Post by kIsS on 2008-05-03
Thank you you three :) problem fixed (via the method posted in the first reply).

P.S.  yep Roger, i did my homework! ):P

---

