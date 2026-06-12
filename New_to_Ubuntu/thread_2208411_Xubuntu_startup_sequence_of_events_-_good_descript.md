---
title: "Xubuntu startup sequence of events - good description required"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by mynot on 2014-02-28
Hi, can anyone please point me to a good description of what happens between Linux loading and the desktop being displayed? What, for example, is the relationship between Linux, X11, lightdm and xfce? What configuration files are used? (Not asking anyone to answer these questions - just point me to a source.) At the moment it's a mystery and solving problems is a matter of picking posts more or less at random and trying things.
Thanks

---

### Post by Bashing-om on 2014-02-28
mynot; Hi !

These for starters:
Bear in mind that 'buntu is constantly evolving, things change rapidly. In particular with the advent of upstart , initramfs and grub.
[http://duartes.org/gustavo/blog/post/kernel-boot-process](http://duartes.org/gustavo/blog/post/kernel-boot-process)
[http://www.LinOxide.com/linux-administration/boot-process-of-linux-in-detail/](http://www.LinOxide.com/linux-administration/boot-process-of-linux-in-detail/)
[http://askubuntu.com/questions/397457/exact-booting-process-of-ubuntu](http://askubuntu.com/questions/397457/exact-booting-process-of-ubuntu)
[https://wiki.ubuntu.com/Booting](https://wiki.ubuntu.com/Booting)

Once you have a general understanding, then one can get specific.

Just remember, what was true yesterday may no longer have any relevance ! Thousands of programmers hard at work.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]just keeps getting better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-02-28
One way is to look at the chain of Upstart actions in /etc/init

I think the short answer is the Linux kernel first, then Plymouth (including the splash screen), which starts lightdm (including the login screen), which starts xfce for the user. xfce is built on top of X.

Don't get too married to that, though. A lot is about to change when Mir replaces X. Mir can start earlier during boot (before login), so Plymouth and lightdm may change.

---

### Post by mynot on 2014-03-02
Bashing-om
Thanks. Been following links from your suggestions for the last hour, and hardly started. (The second link doesn't work, by the way). Plenty to learn.

---

### Post by Bashing-om on 2014-03-02
mynot; Good deal,

Pleasing you are making progress. Warning, learning this operating system is a life long process and is addictive !

The "bad" link: the site has been moved ->  Expertslogin is now migrated to LinOxide. Will update my post and files. Thanks for the advisement.

We are here always to help you over the rough spots, just a keyboard away.

[INDENT]'buntu
[INDENT][INDENT]open source at it's best
[/INDENT][/INDENT][/INDENT]

---

