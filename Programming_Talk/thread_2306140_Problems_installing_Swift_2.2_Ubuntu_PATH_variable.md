---
title: "Problems installing Swift 2.2 Ubuntu PATH variable and BASH"
date: 2015-12-12
forum: Programming Talk
---

### Post by dell44223 on 2015-12-12
Hi, I am an Ubuntu/Linux beginner and cannot figure out what I have done wrong.
I followed the directions on Swift.org for Ubuntu 14.04 and this happens

wills@wills-VirtualBox:~$ PATH=$(getconf PATH)
wills@wills-VirtualBox:~$ echo $PATH
/bin:/usr/bin
wills@wills-VirtualBox:~$ export PATH=/home/wills/swift-2.2-SNAPSHOT-2015-12-01-b-ubuntu14.04/usr/bin:"${PATH}"
wills@wills-VirtualBox:~$ swift
bash: /home/wills/swift-2.2-SNAPSHOT-2015-12-01-b-ubuntu14.04/usr/bin/swift: cannot execute binary file: Exec format error

it happens when I type swift --version too.
Help?

---

### Post by T.J. on 2015-12-13
That error happens when you are trying to run an executable on a processor or operating system that it was not compiled for, such as trying to run a 64 bit program on a 32 bit Linux.  I would humbly suggest that you please double-check your download to make certain that you downloaded the right one for your setup.

---

