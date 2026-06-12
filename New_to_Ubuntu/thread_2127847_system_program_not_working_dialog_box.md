---
title: "system program not working dialog box"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by cutSn8 on 2013-03-21
Hi I got a pop up window saying something like 'system program not working', inviting me click on to report. I did, and was then asked to enter  my password, which I did.  I then got a few windows and some error message (unable to determine package name perhaps).  Is this legit?  Thanks

---

### Post by slickymaster on 2013-03-21
It could be related to Apport, which is Ubuntu error reporting system. You can try to disable Apport to see if it solves this issue.

Open a terminal window and type the following:
```
gksudo geany /etc/default/apport
```
(you have to use your installed text pad, in my case it's Geany)
Change the value of "enabled" from 1 to 0 (instructions are provided in the text file itself).
Save, exit and do a system reboot.

See the [Apport Ubuntu Wiki]("https://wiki.ubuntu.com/Apport") for the info. There, it is categorically stated that:
> Apport is not enabled by default in stable releases, even if it is installed.

---

