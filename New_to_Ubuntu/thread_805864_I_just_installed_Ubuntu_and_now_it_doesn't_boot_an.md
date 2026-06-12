---
title: "I just installed Ubuntu and now it doesn't boot anymore"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by cantfindtheanykey on 2008-05-24
Okay, so I just installed Ubuntu last night and it was working fine alongside Windows XP, but now i can't boot Ubuntu anymore. I selet Ubuntu drom the OS Selection menu but it just shows the loading screen with the orange bar bouncing back and forth for like three seconds then goes to a text-based program called ntfsramloader or something. The point is, i can't get to my Ubuntu desktop.

---

### Post by Kinst on 2008-05-24
Were you trying to fiddle with graphics card drivers or /etc/X11/xorg.conf?

---

### Post by meindian523 on 2008-05-24
Could you post the following from your Live CD?
```
cat /boot/grub/menu.lst
```
```
sudo fdisk -l
```

---

### Post by cantfindtheanykey on 2008-05-24
Yeah, Ubuntu prompted me to install video card drivers when I was playing around with the visual effects. Do you know what is wrong?

---

### Post by meindian523 on 2008-05-24
If you didn't fiddle around /etc/X11/xorg.conf manually,video card driver installation SHOULD not affect booting.

---

### Post by Kinst on 2008-05-24
It still sounds like driver trouble to me. :( I remember when I installed my ATI driver it borked xorg.conf a whole bunch of times before I got it working.

Try this command and then reboot.

```
sudo dpkg-reconfigure xserver-xorg
```

It resets the xorg.conf file ( X.org is like the graphical system of linux, and xorg.conf is its configuration file )

---

### Post by cantfindtheanykey on 2008-05-24
No, it isn't Linux, it says it is something called "busybox".

---

### Post by Raccoon1400 on 2008-05-24
> **meindian523 said:**
> Could you post the following from your Live CD?
```
cat /boot/grub/menu.lst
```

No, that won't work unless you chroot to your ubuntu partition. Otherwise, you will get the grub file from the CD, if there is one.


Boot the live CD, go into your ubuntu partition, and post the file
/boot/grub/menu.lst

---

### Post by Joeb454 on 2008-05-24
> **Kinst said:**
> It still sounds like driver trouble to me. :( I remember when I installed my ATI driver it borked xorg.conf a whole bunch of times before I got it working.

Try this command and then reboot.

```
sudo dpkg-reconfigure xserver-xorg
```

It resets the xorg.conf file ( X.org is like the graphical system of linux, and xorg.conf is its configuration file )

To do this command, you will need to boot Ubuntu into recovery mode, but then you will only need to run ```
dpkg-configure xserver-xorg
``` because you will already be root :)

---

### Post by prince_of_hackers on 2008-05-24
> **cantfindtheanykey said:**
> Okay, so I just installed Ubuntu last night and it was working fine alongside Windows XP, but now i can't boot Ubuntu anymore. I selet Ubuntu drom the OS Selection menu but it just shows the loading screen with the orange bar bouncing back and forth for like three seconds then goes to a text-based program called ntfsramloader or something. The point is, i can't get to my Ubuntu desktop.

The orange bar is a problem - it often hides the display of messages that could be helpful in providing the information needed to diagnose the source of the problem. To turn it off, when you are at the OS Selection menu, highlight the selection for Ubuntu, and press the "a" key to edit the boot options for that line. Remove the words "quite" and "splash" from the line, and press the enter key to boot the system. You will see a lot of message fly by that you probably don't understand, but hopefully, you should see any error messages from before the boot fails, and can post them here to help us understand what is causing your problem.

Also, as meindian523 said, if you can boot to the live CD you installed from, post the output from "sudo fdisk -l" here. The ntfsramloader thing sounds like it might be something related to how Ubuntu's partitions are coexisting with Windows' partition.

One more piece of useful information to help diagnose the problem would be to try and think what the last things you did, under either Windows or Ubuntu, between the last time you sucessfully booted into Ubuntu, and the first time it failed. Unless a hardware problem is to blame, (unlikely) something must have been changed that affected the boot process.

---

### Post by meindian523 on 2008-05-25
> **Raccoon1400 said:**
> No, that won't work unless you chroot to your ubuntu partition. Otherwise, you will get the grub file from the CD, if there is one.


Boot the live CD, go into your ubuntu partition, and post the file
/boot/grub/menu.lst
That's correct.Me bad:(

---

