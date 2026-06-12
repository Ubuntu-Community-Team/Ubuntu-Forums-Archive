---
title: "Nvidia 8200 onboard restricted drivers problem"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by mike23 on 2008-05-31
After a few problems with my M3N78-EMH HDMI Motherboard, and help from this forum ive managed to get ubuntu up and running!
But now i ran into another problem.. 
This motherboard has onboard nvidia 8200 grafics card. So after enabling the restricted drivers and restarting i get this:

[http://img89.imageshack.us/img89/9058/img1759ec3.jpg](http://img89.imageshack.us/img89/9058/img1759ec3.jpg)  
(foto of my monitor)
Any ideas on how to solve this?

p.s i would not suggest anyone to buy this motherboard.
thanx

---

### Post by phidia on 2008-05-31
If you backed up your previous xorg.conf (/etc/X11/xorg.conf) or it was auto backed up for you-which is frequently the case-you can use the old xorg and then follow one of the [guides]("http://ubuntuforums.org/showthread.php?t=301499") from the multimedia and video forum. Hope that helps.

---

### Post by mike23 on 2008-05-31
I dont know how to use the old xorg...
I also use version 8.04 wich isnt listed in those guides.. is it ok to use the guide of an older version? (that is if i manage to use the old xorg.conf)....
Can any1 give me a hand.... ??

---

### Post by mike23 on 2008-05-31
any1 please? thanx..

---

### Post by SteveNorman on 2008-05-31
your obviously using another computer to post this right? or are you using a live cd?

the way you put a backup copy  in place is to copy the backup to the original:

cd /etc/X11/xorg.conf
cp xorg_backup.conf xorg.conf

---

### Post by mike23 on 2008-05-31
im dual bootin xp which i look forward to get rid of......

someone help please... i mean im desperate here...

---

### Post by mike23 on 2008-05-31
anybody out there.....??

---

### Post by SteveNorman on 2008-05-31
Im sure there is a way to use the live cd to do it,,but I dont know how..since the live cd doesnt affect the harddrive

Have you tried rebooting from the live cd? that will tell you if your vidcard is working,,

you can try to use the live cd and reload the driver, or edit you xorg.conf file, but I dont think it will survive a reboot since the live cd uses RAM not the HD.

If your not to attached to anything re-installing may be the way to go, but wait a bit before you do as someone may have a fix. You may want to post somewhere else to get a different audience.

---

### Post by SteveNorman on 2008-06-01
Do you have another port you can plug your monitor into? And do you get any kind of splash screen before the monitor goes crazy?

---

