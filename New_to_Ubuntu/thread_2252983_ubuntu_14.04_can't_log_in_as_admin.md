---
title: "ubuntu 14.04 can't log in as admin"
date: 2014-11-16
forum: New to Ubuntu
---

### Post by hanan2 on 2014-11-16
I installed Ubuntu14.04 using wubi from winows7 "64 bit OS", wubi asked to choose a password, i typed it twice and then installed and everything went fine, 
while booting into ubuntu i got a screen that says:
 try (hd0.0) : NTFS5: No wubildr
try (hd0.0) : NTFS5:
then another screen says:
mount : can't read '/proc/mounts': No such file or directory.

then the log in screen , but when i type my username and password it says invalid password, even though i'm sure it's the same password that i chose and username that was typed for me in the wubi interface .
please tell me how can i fix this and be able to log in as an admin.

---

### Post by Impavidus on 2014-11-16
Wubi is deprecated. Better not use it. [http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

If you can manage to boot into recovery mode, try this: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

This may be caused by some problem with keyboard layout or character encoding, which might be different on Ubuntu and Windows.

---

