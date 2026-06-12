---
title: "can't install gcc and g++ with apt-get"
date: 2006-09-07
forum: Programming Talk
---

### Post by krmane on 2006-09-07
hello,
I want to use ubuntu 6.06.1 as my developer machine along with a desktop.
I realise that the development tools are not installed by default.  I also saw in the pool directory that there is glib and gcc as well as g++, make etc.
but when I put the cd in and say apt-get install build-essentials, I can't get it installing gcc?
is cd not browsed for apt-get?  is internet the only option?
thanks all,
Krishnakant.

---

### Post by thumper on 2006-09-07
try
```
sudo aptitude install build-essential
```
not essentials

---

### Post by ifokkema on 2006-09-07
It might be that the CD is not in your /etc/apt/sources.list. Check that file for a line similar to:
```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```
Then remove the # in the front, save the file, and run:
```
sudo apt-get update
sudo apt-get install build-essential
```

HTH

---

