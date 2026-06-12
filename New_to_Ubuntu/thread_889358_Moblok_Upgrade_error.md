---
title: "Moblok Upgrade error"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by bigtel on 2008-08-14
Can anyone help. I have been getting the following error message when trying to upgrade Mobloker through the package manager.

E: /var/cache/apt/archives/moblock_0.9~rc2-16~hardy_i386.deb: subprocess new pre-removal script returned error exit status 3

I have sent an error report but I would like to know why this is occurring.

---

### Post by mandrill on 2008-08-14
> **bigtel said:**
> Can anyone help. I have been getting the following error message when trying to upgrade Mobloker through the package manager.

E: /var/cache/apt/archives/moblock_0.9~rc2-16~hardy_i386.deb: subprocess new pre-removal script returned error exit status 3

I have sent an error report but I would like to know why this is occurring.

There is a script error, and it looks like you're using a beta version of Moblock. Try iplist from sourceforge, much easier to deal with. 

Good Luck.

---

### Post by nicedude on 2008-08-14
Moblock didn't work for me either but ipblock which is part of iplist software works like it should. So just install it instead as previously mentioned. At sourceforge you want to get a deb package so its easy to install :-) and then you will see ipblock under Applications -> Internet -> Ipblock . Just remember the software package is called iplist but the blocker that is included in it is called ipblock.


Good luck and happy Ubuntu-ing

---

### Post by jre on 2008-08-14
First, what did you update, mobloquer or moblock? The first depends on latter, but only for the latter there was an update lately.
I (Debian packages, moblock-control) have not received a bug report, where did you sent it?

Anyway, can you send more info: The complete output during update and /var/log/moblock-control.log.

Of course you may also try iplist instead, it has the same purpose and uses the same blocklists.

jre

EDIT: The version bigtel uses is the current stable version, at least from my packager's view. It's just not released by upstream, but this version has less (= no) bugs than the official 0.8 version.

But indeed I also guess that it is a script error, either by moblock-control, packaging or LSB init-functions.

---

