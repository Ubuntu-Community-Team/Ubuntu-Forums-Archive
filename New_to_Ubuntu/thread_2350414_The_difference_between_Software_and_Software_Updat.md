---
title: "The difference between Software and Software Updater programs"
date: 2017-01-24
forum: New to Ubuntu
---

### Post by waltd on 2017-01-24
Hi all, This is a newbie question.  I have Xubuntu, version 16.10.  I noticed that I have two different programs that update software.  
     1. Software with an "updates" tab on the right side of the window.
     2. Software Updater.  
What is the difference between these two different update programs?  For example, does the Software Updater only update system OS type programs and Software only update application programs?  Or are they two different programs that perform the same function and update all programs, applications and OS system?   
I noticed once that the Software Updater didn't have anything to update, however the Software program had one item to update.  So I'm a little confused which update program is updating which items.  Thanks.

---

### Post by leunam12 on 2017-01-24
Software Updater is the program that allows you to update your system. The other one is for sources and update preferences.

---

### Post by slickymaster on 2017-01-24
The software updater is the generic updater. It will scan, based on a period set in settings, for updates for all your repositories and PPA's you added. Software has its own version of the software updater but uses another way of displaying the updates. It shows them per installed software making it easier to check and to install single updates.

---

### Post by deadflowr on 2017-01-24
> I noticed once that the Software Updater didn't have anything to update, however the Software program had one item to update. So I'm a little confused which update program is updating which items. Thanks.

see:
[https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")

Software updater is update-manager, for the record.

---

