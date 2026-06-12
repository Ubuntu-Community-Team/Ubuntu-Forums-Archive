---
title: "Minor Problem With Updates"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by john-m-ellsworth on 2014-01-10
I have been using Ubuntu for several years, but I am not a 'power user' like most of you seem to be.  Currently I am running 13.10 on a HP-Pavilion DV-7 Laptop. 

The update manager shows up from time to time as expected, telling me about changes and updates to the system.  I usually close all running programs and then activate the "INSTALL" button.  At the end, rather than receiving "the software on this system is up to date" message, I get a fail message which I can't remember.  Something about removing packages has failed.  If I try to re-run the updater however, then I get the all is current message.  

From my Google inquiry it seems that this has been a problem in the past for other users, but I'm not seeing any similar reports for 13.10.  Being mildly OCD makes me worry that the program isn't ending properly and leaving fragments of old software on my computer.  

Is there a simple fix, or workaround, or should I just quit being so paranoid about this stuff.

---

### Post by oldos2er on 2014-01-10
Could you run the following in a terminal, and if there are any errors copy/paste the whole text output here? ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by rburkartjo on 2014-01-10
just a shot in the dark. here is a link

How to Fix Ubuntu Update Errors
[http://www.maketecheasier.com/fix-ubuntu-update-errors](http://www.maketecheasier.com/fix-ubuntu-update-errors)

---

### Post by john-m-ellsworth on 2014-01-10
Ann, I ran the string in terminal, it scrolled for many many pages with no error.  Finally at the end I received this.... 

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/106 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing phonon-backend-gstreamer:i386 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 phonon-backend-gstreamer:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@Laptop:~$ 


So I guess it looks like I need to reinstall "phonon-backend-gstreamer:i386"  But I have no idea how to do that.

---

### Post by john-m-ellsworth on 2014-01-10
Rburkartjo, 

Thanks, I checked out that link but none of those problems are what I am seeing.  My update runs just fine except at the very end, it gives a message that implies that it did not finish properly.  (I think in the cleanup process).  As I said initially, it isn't a big issue, and every time I manually run the update manager after the error it says my system is up to date, so I don't think I am missing repositories or updates.  I am just being OCD about the updater.

---

### Post by oldos2er on 2014-01-10
Try ```
sudo apt-get install --reinstall phonon-backend-gstreamer:i386
```

---

### Post by john-m-ellsworth on 2014-01-10
Thanks Ann.   That ran and completed with no errors.  So I'll see if things are fixed next time the "auto update" icon shows up on the dash.   And just for a simple walk down memory lane, I used to use IBM OS/2 before switching to Ubuntu.  (I guess I have just always been a windows-hater).

---

### Post by oldos2er on 2014-01-10
Yay for OS/2.  :)  I still miss the WPS.

Anyway, could you please mark the thread 'Solved' under Thread Tools? Thanks.

---

