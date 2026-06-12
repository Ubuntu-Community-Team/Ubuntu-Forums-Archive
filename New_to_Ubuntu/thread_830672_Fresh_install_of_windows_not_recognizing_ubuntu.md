---
title: "Fresh install of windows not recognizing ubuntu"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by legatoistheman on 2008-06-16
I just recently did a fresh install(format)of win xp 64 pro tonight on a different hard drive than my ubuntu hard drive.  

Of course Windows was being very difficult(ie. would not read my wireless usb lan card driver install cd because it said there was no driver to install), so I tried to switch back to my linux drive.

Windows boots up now and there is no grub.  No option at all.  Did windows somehow reformat both drives?  I knew what drive was which because the win drive had less memory than the ubuntu drive and I am positive I picked the win drive to reformat on.

Any suggestions for a really frustrated guy who probably wont have internet or be able to play wow for a very long time on his own computer?
thanks
legato

---

### Post by wannadumpwindows on 2008-06-16
Your windows install wrote over grub. You just need to reinstall it. Check here:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by ChameleonDave on 2008-06-16
Windows does not respect other operating systems.  It routinely deletes GRUB from the MBR (Master Boot Record) of your hard drive.

Boot into a Linux live CD, and reinstall GRUB.  The system will then work.  There are various guides available on these fora and on the internet.

---

