---
title: "Can't shutdown 11.10"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by vicke4 on 2011-10-25
Hi i have one serious problem in 11.10.i can't shutdown my laptop.if i click on shutdown i redirected to login screen.i can't shutdown using the top right corner shutdown option.now I'm long pressing my laptop power button to shutdown.on startup i can't see Ubuntu emblem also.

---

### Post by egkeat on 2011-10-25
> **vicke4 said:**
> Hi i have one serious problem in 11.10.i can't shutdown my laptop.if i click on shutdown i redirected to login screen.i can't shutdown using the top right corner shutdown option.now I'm long pressing my laptop power button to shutdown.on startup i can't see Ubuntu emblem also.


I'm having the same problem. I can't shut down using anything except pulling the plug.

---

### Post by Jagoly on 2011-10-25
I have the same problem too; its a bug within ubuntu's graphical shutdown thingy's. As a temporary measure, you can issue the shutdown command manually:
```
sudo shutdown now
```
80% of the time this works, but sometimes it completely freezes on the ubuntu splash screen after a few seconds. At that point just hard shutdown anyway.

I really hope this gets fixed soon. It's a pig PITA in 11.10.

---

### Post by robert shearer on 2011-10-25
Pulling the plug just leads to all sorts of other problems.

Here is an acceptable shutdown method...
[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

note that rseiub=reboot and rseiu**o=off**.

---

### Post by Yorkiede on 2011-10-25
I had the same problem and solved it by installing gnome-tweak-tool from the software centre. After it is installed it is invoked in apps under advanced settings. Under desktop I clicked everything to on and restarted the computer. The shutdown icon reappeared on the top right. I also had an extra rubbish bin and a few new icons for network and such, but I started the tweak tool again and just clicked them away, but the shut down button remained.

Hope this helps

---

### Post by egkeat on 2011-10-25
After searching I saw that LibreOffice Quickstarter could be the culprit. I went into Libre and unchecked. Low and behold, it worked.

---

### Post by Gkar on 2011-10-29
Got the same issue but without solution 

It seems to failed en killall process.

Any idea ? 

I run Ubuntu 11.10 32bits which has been migrated from 11.04 clean installation

---

### Post by Jonathan8146 on 2011-10-30
I had the same and found this here [http://askubuntu.com/questions/69083/gui-access-to-shutdown](http://askubuntu.com/questions/69083/gui-access-to-shutdown) which worked a treat:

I experienced exactly this, after upgrading from Ubuntu 11.04 
  Try moving the mouse to top-right (close to the edge of screen) over  the username.  The 'Power Menu' should then replace the 'Switch User'  menu.
  **I initially solved this by changing theme from 'Ambiance' to 'Radiance'**.  By now, this should have been fixed in updates.

---

### Post by ConfusedButEnthused on 2011-11-06
I experience the same on 32bit eMachine T3882, on both 11.04 and 11.10 (went to 11.10 to try to resolve).  Shutdown results in a restart operation for me.  I dual-boot between Windows XP and Linux and simply wait for grub to present the option before forcing shutdown with the button.  My restart operation hangs and freezes, forcing me to shut it off.
I'm excited about trying the 'sudo shutdown -h now' method.  :-k

---

### Post by Eudaimon on 2011-11-08
I'm working on a single button shutdown, and having trouble.  Searched a number of forums/threads, and gconf-editor didn't work, nor did Gnome Tweak Advanced Settin's.   

Any thoughts as to how to set the power button to shut down immediately, without a pop up window?

---

