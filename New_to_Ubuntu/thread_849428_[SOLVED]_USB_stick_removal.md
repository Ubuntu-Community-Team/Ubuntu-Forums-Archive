---
title: "[SOLVED] USB stick removal"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-07-04
Hi all,

  Can you please tell me when i was using windows and using USB to copy files etc, there was an option called "safely remove hardware". But in ubuntu after i plug in USB it automatically recognizes and opens but i cant find way to safe remove. Please help me what to do on this? Since i heard removing usb without safe removal may result in loss of data or etc. thanks in advance and help me.

---

### Post by Rocket2DMn on 2008-07-04
The drive needs to be "unmounted" first, you can right click the desktop icon and choose Unmount.  Some devices like iPods have an "Eject" option which performs the same function (and it tells you on the ipod that it is safe to disconnect it).

---

### Post by jugganinja0 on 2008-07-04
you could try to right click on the drive and unmount it. Thats what i had to do with a coupleof mp3 players and usb thumb drives. i think and earlier version of ubuntu let me eject it but i may just be thinking things that do not exist.

---

### Post by mailtwogopal on 2008-07-04
hi all,

  thanks a lot. i did so once, but am not known that "unmount" is equivalent to "eject" or "safe remove". anyway thanks for helping this newbie.

---

### Post by Rocket2DMn on 2008-07-04
Yes, unmounting removes it from the filesystem.  A drive must be mounted to read or write from it, so when it is unmounted, it is safe to disconnect.  If it is in the process of writing, it won't let you unmount until its finished - same idea as in windows.

---

