---
title: "System freeze - please see kernel log"
date: 2014-09-16
forum: New to Ubuntu
---

### Post by elvaquero on 2014-09-16
Hi guys!

I need this Ubuntu 14 LTS system as stable as possible, but it froze on me last night. Could you please look at the log and maybe hint at a possible culprit? 

[http://pastebin.com/LPf9Xg87](http://pastebin.com/LPf9Xg87)

I would think the problem had started at 5:03, and at 8:47 I plugged in a usb mouse in an attempt to wake it up from an unresponsive login screen. Rebooted at 8:50.

Many thanks for all suggestions and ideas how to go about troubleshooting this!

---

### Post by Y^2om&amp;#7sgP on 2014-09-16
What hardware are you running on?

FWIW, I have 14.04 on an HP and had to upgrade the kernel because of freezing.

I now have 3.14 and no freezing

Just a thought :)

---

### Post by elvaquero on 2014-09-16
mobo: Asrock 970 pro3
cpu: amd fx8350
video: asus 210-1gd3-l

I'll look into upgrading the kernel and report back...

---

### Post by tgalati4 on 2014-09-16
Your log file shows lots of *nouveau* errors.  Perhaps load the proprietary nVidia driver and see if the errors go away.  Your system was not truly frozen, otherwise your mouse would not be registered.  In the future, use another linux computer and ssh into it and keep that running.  If your computer becomes non-responsive, you can use the ssh session to troubleshoot.  If you have Control-Alt-Backspace activated, then you can reset the graphical session to try to get the computer to respond.  Otherwise hit Control-Alt-F1 to get to a terminal session and troubleshoot or shutdown from there.  I would clean out the machine and reseat cables.  Check the power supply.  Video cards can take up a lot of power and cause random issues.  Try a different video card and a different power supply to isolate the problem.

---

