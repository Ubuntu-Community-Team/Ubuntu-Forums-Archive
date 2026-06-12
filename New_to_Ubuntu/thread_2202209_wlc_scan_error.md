---
title: "wlc_scan error"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by cigtoxdoc on 2014-01-28
I have been hit again with the wlc_scan error after spending much of the day loading outlook express dbx files into Evolution on the Ubuntu 12.04 side of my DELL Vostro 3500.  The error I received apparently has nothing to do with the Wifi card or drivers.  I was not even using it.  The trouble first occurred when I rebooted after getting a low disk-space warning, clearing files to Trash, but then not being able to empty trash.  The reboot indicated a graphics problem, but the recovery mode will not bring up the low-graphics mode.  I was able to get the output of the /var/log/Xorg.0.log file, but there appears to be no way to copy it to the PC I am using to write this post.  Video driver is nVidia 304.88

How should I proceed to get back to a running system?

John

---

### Post by Bucky Ball on 2014-01-28
Without your error messages or any other information there is not a lot to go on ...

Why can't you copy/paste the log file here? Put it between [code] tags. ;)

---

### Post by cigtoxdoc on 2014-01-28
Thank you for your reply.  The boot problem fixed itself when I tried the CLEAN option from the recovery menu.  However, if there is a way of getting log files from the system when it will not boot, please tell me where I can find a "crib sheet" with the instructions.

---

### Post by Bucky Ball on 2014-01-28
Glad it fixed itself. Please mark thread as solved to help others.

A web search for 'where are log files ubuntu 12.04' will probably turn up some results. ;)

---

### Post by cigtoxdoc on 2014-01-28
I have marked this thread as "SOLVED."  However, I do not know why the problem occurred; but since this is the second time it has happened, it would seem to indicate something in wrong with my system or the combination of software I am using.

John

---

### Post by Bucky Ball on 2014-01-28
The second time? How recently did the other crash happen and was it the same cause; transferring Outlook files to Evolution? 

If it was then you've found a fix if it happens again. If it wasn't then you should 'unsolve' the thread and post what you were doing last time the crash happened if you want to get to the bottom of it. If you do, give as much info as possible, else leave it solved if you're satisfied.

---

### Post by cigtoxdoc on 2014-02-02
It appears that the files I need are under var/log /apche2/and var/log/lghtdm.  They seem to have date/time stamps that correspond to most recent reboot and login.  Even though login to Ubuntu is successful, there are three fleeting lines of error messages. Two of them refer to the wlc-scan error.  However, they do not appear to be in the log files.  Yes, I have changed ownerships and permissions of the log file and the folder they are in to see them.  Where should I look?

John

---

