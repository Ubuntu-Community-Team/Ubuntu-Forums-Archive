---
title: "Returning information from Notifications and Progress Bars?"
date: 2010-04-19
forum: Programming Talk
---

### Post by xMemphisx on 2010-04-19
Okay, I'm trying to write a bit of software for my computer, and ideally, I would like to know...

A) When a notification is displayed (and I want to parse the info from the notification window)... e.g., "Computer is now running on battery power" is the information to be pulled.

B) How to retrieve the % of a file transfer, or similar progress bar(s) that are displayed in Gnome.

I've googled around a bit and not been able to come up with much. If anyone could point me in the correct direction, that would be phenomenal. 

Regards,
Memphis

---

### Post by iponeverything on 2010-04-19
> 
A) When a notification is displayed (and I want to parse the info from the notification window)... e.g., "Computer is now running on battery power" is the information to be pulled.

B) How to retrieve the % of a file transfer, or similar progress bar(s) that are displayed in Gnome.


I really don't think you are going be pulling anything from notification window itself. It's only meant to be parsed by a human.  

This is probably as good a place as any start your research:

[https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)

What you are going to want to be watching is the communication between the application generating the notification and the notification subsystem.

---

### Post by lisati on 2010-04-19
Moved to "Programming Talk"

---

