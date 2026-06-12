---
title: "Grub Error 15 :("
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Rins on 2008-09-29
Hello,
 I wanted to ask about something - one day i restarted my PC and i saw this:
           Error 15(i couldnt enter neither in my Windows, neither in my Linux OS)
So i loaded my Ubuntu Live CD and i wrote in command prompt something like this:

 sudo grub

grub> find boot/grub/stage1
 (hd?,?)
grub> root (hd?,?)
grub> setup (hd?)
 the operation was succesful, so i restarted again,so i can try the grub menu. I was able to enter in my Windows XP but when i tryed Ubuntu i only got this massage:
Error 15
My question is - can anyone help me, i want to be able to run both systems again - Linux or Windows.

---

### Post by WWSmith36 on 2008-09-29
Grub Error 15 is File Not Found

I would boot to the LiveCD and take a look at some things.  I have a feeling its related to device naming convention.  It could be /dev/hda vs /dev/sda naming convention. It could be UUID assignment to drive versus /dev/sda.

Take a look at your /etc/fstab /boot/grub/device.map /boot/grub/menu.lst and make sure the naming is consistent.

Hope this makes some sense

---

### Post by WWSmith36 on 2008-09-29
This command may come in handy too

```
ls -l /dev/disk/by-uuid
```

---

### Post by Rins on 2008-09-30
hm...thank you for the information, i've opened my menu.lst and i saw that the number of the drive wasn't correct, when i changed it - it worked. :)

---

