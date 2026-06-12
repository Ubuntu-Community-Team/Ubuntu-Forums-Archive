---
title: "dell precision 390 dies while installing ubuntu"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by jahern on 2014-05-20
I've attempted several times to install ubuntu from a usb thumb drive but have failed.  its a a dell precision 390 with nvidia quad fx 550 video card.  I can boot from the usb drive and use the os normally until I get an icon in the upper right that talks about driver for video card.  when I try to install that it goes lights out dead.  I don't know if that's the cause but its a symptom.  I had xp on the internal drive and I pulled it, cleared all partitions and made it ext4 with drive utility on another machine running ubuntu 12.04.  I ran memtest86 for several hours and did not find any errors.  

thanks

---

### Post by tgalati4 on 2014-05-21
Don't install the proprietary graphics driver until after performing other system updates.  Reboot after any kernel or xorg updates.  Then check the log files in /var/log for any obvious boot/system errors.  Then attempt to install the proprietary driver, but be prepared to revert to the open video driver if it does not work.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

