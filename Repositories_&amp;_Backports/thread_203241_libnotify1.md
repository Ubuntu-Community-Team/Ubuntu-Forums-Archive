---
title: "libnotify1"
date: 2006-06-24
forum: Repositories &amp; Backports
---

### Post by kb3hkg on 2006-06-24
As of this morning according to adept, synaptic, and update manager libnotify1 needs to be upgraded. But all the ways I have tried to update it hold it back but don't say way. How do I make this work?

---

### Post by kb3hkg on 2006-06-26
I am still having this problem, but only on one of my machines that is running ubuntu, can someone please help me figure this out?

---

### Post by taavi on 2006-07-06
Run in terminal "dpkg-query -s libnotify1" and also have you modified your sources.list?

---

### Post by kb3hkg on 2006-07-13
haven't modified list since upgrading to dapper. will try that command when I get a chance.

---

### Post by kb3hkg on 2006-08-30
Finally have an internet connection on this machine again. If anyone is still listening I ran the command as asked but it only gives info about the current version. My problem is that it wants to upgrade but can't for some reason.

Here is my sources.list if it helps, I am only posting the actual lines not any of the comments

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

---

### Post by kb3hkg on 2006-09-04
Thanks for the help everyone, but I seem to have it working again.

---

