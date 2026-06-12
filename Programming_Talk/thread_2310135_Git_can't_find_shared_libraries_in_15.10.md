---
title: "Git can't find shared libraries in 15.10"
date: 2016-01-16
forum: Programming Talk
---

### Post by ray-jantz on 2016-01-16
I'm running a fresh install of Ubuntu Gnome 15.10.  I installed git using synaptic but when i run 'git push origin master' I get the error:  'error while loading shared libraries: libgnutls.so.26: cannot open shared object file: No such file or directory'  I found a copy of this library that worked, but then I got the same error for libgcrypt.so.11 and libtasn1.so.3, so I also found and installed those, and now the git command works.  I haven't found anyone else with this problem and I know there are a lot of git users on 15.10, so I am wondering what is going on?  Does anyone have any idea why I got these errors?  Thanks.

---

### Post by ian-weisser on 2016-01-16
Git dependencies didn't install.
That's unusual and rare.
Apt downloads and installs dependencies before installing the top-level application.

Many possible reasons: Power loss, corrupted package database, out of RAM, out of disk space, human added non-Ubuntu sources, human introduced a version conflict, human manually installed instead of using packages, human forgot to use sudo, human ignored error messages, human used a --force flag, etc.
Reviewing the dpkg log may shed light on the specific reason, if it matters.

Apt failure is very rare: In a decade of using apt frequently, I have seen apt fail three times, one bug (reported and fixed) and two non-repeatable.
Seems like you got it fixed. Well done!

---

### Post by mc4man on 2016-01-16
> **ray-jantz said:**
> I'm running a fresh install of Ubuntu Gnome 15.10.  I installed git using synaptic but when i run 'git push origin master' I get the error:  'error while loading shared libraries: libgnutls.so.26: cannot open shared object file: No such file or directory'  I found a copy of this library that worked, but then I got the same error for libgcrypt.so.11 and libtasn1.so.3, so I also found and installed those, and now the git command works.  I haven't found anyone else with this problem and I know there are a lot of git users on 15.10, so I am wondering what is going on?  Does anyone have any idea why I got these errors?  Thanks.

Those are [deps]("http://packages.ubuntu.com/trusty-updates/libcurl3-gnutls") of[ git in 14.04]("http://packages.ubuntu.com/trusty/git") not [deps]("http://packages.ubuntu.com/wily/libcurl3-gnutls") of [git in 15.10]("http://packages.ubuntu.com/wily-updates/git").
Maybe you have an older git in your $PATH (~/ or /usr/local

---

