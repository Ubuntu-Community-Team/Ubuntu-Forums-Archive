---
title: "login screen still on gutsy graphical layout"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by Payteer on 2012-05-05
Hello all, 
I have just finished the upgrade to 12.04 following the full process all the way back from gutsy.  Anyway, all looks good and all is working, however in the login screen it is still on the old Gutsy graphical layout and not dated to the newer version, can anyone help?
Thanks.

---

### Post by kazztan0325 on 2012-05-05
Hi Payteer,

Gutsy Gibbon is the code name for Ubuntu 7.10.

Have you really upgraded to 12.04 from 7.10 ??

---

### Post by grahammechanical on 2012-05-05
You need to show us a screen shot or something. The default log in screen of 12.04 is very similar to all previous default screens. It is even called warty-final-ubuntu.png

You can find it in /usr/share/backgrounds along with all the other backgrounds/wallpaper.

Try selecting a static wallpaper and logging out and then back in. You should see the log in background change to the same image as the desktop background/wallpaper that you selected.

Regards.

---

### Post by Payteer on 2012-05-06
Yep, I did an upgrade through each different version, it took a fair few hours, but all done now.  On the screen thingy it is now only stuck on one about two back. 10.10 now  i can't do a screen shoot as in the windows system instead at the moment.
It isn't the background, that is the purple stuff, but the login box is still stuck in the middle, I have seen a friend's version and he has it looking rather nice on the left hand side.

---

### Post by drs305 on 2012-05-06
By login screen, are you talking about the Grub screen? Or is it still booting an older OS?

If you can boot into 12.04, you can rewrite the MBR so that it points to your 12.04 version of Grub. Once you run the following commands from Precise, it should display the Grub menu with Precise listed first and other OS's listed afterward:
```
sudo update-grub
sudo grub-install /dev/sd*X*

```X is the drive letter of the drive the BIOS boots (sda, sdb, etc)

---

