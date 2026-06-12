---
title: "Login screen resolution - server 11.10"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by lobat67 on 2011-10-19
I have just installed Ubuntu Server 11.10 (x386) onto a HP DL360 G4. Screen display throughout the install process was fine, but on reboot the login screen display is "out of range" for any monitor.  I have managed to tweak the monitor itself and get very small, barely readable characters on screen, however the command line (where I am typing) is off the bottom off the screen and I only see the results of an entered command after I have hit return twice.  

I have hunted for a solution, but anything that seemed promising, even trying to get a GUI installed prompts long lists with "but it is not going to be installed" tagged everything.

---

### Post by lobat67 on 2011-10-22
Please note I am talking about the basic login screen; command prompt to use Windows jargon.  Not changing the screen resolution in a GUI, which BTW works fine.

---

### Post by Graham17655 on 2011-10-22
I'm having similar problems, but have you tried this:
Edit the file /etc/default/grub
Find the line #GRUB_GFXMODE=640x480
remove the # and save it.  (you need to run the editor with root permissions - sudo emacs /etc/default/grub)
Now you need to update grub with sudo update-grub
Reboot and see if it is any better.

My problem is that with a GUI the max resolution is 6480x480 even when I change the line above to 1024x768.  The console looks fine at this resolution but GUI is no good.

N.B. Replace emacs with any other editor name.  I like it as I learn't it about 20 years ago on UNIX.

---

