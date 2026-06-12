---
title: "two hard drives set up"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by skiddly on 2008-11-13
hi after recent probs i now have 2 sata hard drives installed, my new one with vista on it i connected using the existing leads in pc,the original hard drive with ubunto 8.10 i used a new sata cable now when start pc ubuntu loads and no mention of windows vista so i dissconected the cable from old hd windows now works how do i set up pc so i can use either even if as a last resort i have to use one just for storage, not sure if i asked already or in a different forum but cant find anywhere .

---

### Post by overdrank on 2008-11-13
> **skiddly said:**
> hi after recent probs i now have 2 sata hard drives installed, my new one with vista on it i connected using the existing leads in pc,the original hard drive with ubunto 8.10 i used a new sata cable now when start pc ubuntu loads and no mention of windows vista so i dissconected the cable from old hd windows now works how do i set up pc so i can use either even if as a last resort i have to use one just for storage, not sure if i asked already or in a different forum but cant find anywhere .

Hi and you will have to add windows to the grub and a similar topic is ongoing here
[http://ubuntuforums.org/showthread.php?t=981155](http://ubuntuforums.org/showthread.php?t=981155)

---

### Post by mapes12 on 2008-11-13
Try this: [http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by skiddly on 2008-11-13
i dont know if ive explained properly i dont want to partition a hard drive to share vista/ubuntu i want to run vista from hd 1 or ubuntu from hd 2 depending on what i need to do and need to be set up so i get asked which hard drive i want to use each time i turn on pc if it is possible

---

### Post by Duck2006 on 2008-11-13
> **skiddly said:**
> i dont know if ive explained properly i dont want to partition a hard drive to share vista/ubuntu i want to run vista from hd 1 or ubuntu from hd 2 depending on what i need to do and need to be set up so i get asked which hard drive i want to use each time i turn on pc if it is possible

Yes it is possible. Where it comes to partitioning the drive partition the seccond drive and install ubuntu there. Grub will set it self up on the first drive so you will be able to chose the OS you want to run.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by steve-shinn on 2008-11-13
This can be achieved.

Firstly you have to ensure that the hard drive which contains grub, is set in bios as the first boot device.

Then you have to edit grub accordingly.

---

