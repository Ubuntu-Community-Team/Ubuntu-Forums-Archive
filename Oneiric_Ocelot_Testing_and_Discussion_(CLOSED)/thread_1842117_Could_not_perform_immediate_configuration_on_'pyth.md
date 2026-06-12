---
title: "Could not perform immediate configuration on 'python-pyatspi2'."
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by roberj13 on 2011-09-10
I have been trying to upgrade to Oneiric today. I have been running into some problems with the install. The upgrade starts fine, downloads all of the packages, then on installation of the packages I get:

Exception during pm.DoInstall(): E:Could not perform immediate  configuration on 'python-pyatspi2'. Please see man 5 apt.conf under  APT::Immediate-Configure for details. (2)

A google search on this returned a bug report in Launchpad

[Launchpad bug #836798]("https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/836798?comments=all")

The bug reports as a fix was released but it apparently is broken again. I commented on the bug report  that it seems to be broken again but wanted to see if anyone knows how to get this installed. It seems not everyone is running into this problem.

I also tried to install via live and alternate installs, neither of those worked either but I did not capture any logs of what went wrong there.

Maybe I'll just wait a few days. Dang, boring weekend, kernel.org down android.git.kernel.org down, and can't upgrade to broken stuff to keep me entertained.

---

### Post by shahidpazeez on 2011-09-15
I fixed this issue by install the two packages at-spi2-core & python-pyatspi2 manually. Then run the command do-release-upgrade -d
```
$ sudo apt-get install at-spi2-core python-pyatspi2
```
```
sudo do-release-upgrade -d
```

---

