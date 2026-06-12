---
title: "Restore Grub"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by SeanArronD on 2008-08-19
Okay so i have Vista & Ubuntu installed on my computer, when i originally installed ubuntu it was a secondary OS so in vista i got EasyBCD and made the vista bootloader my main one.

Now, after using ubuntu for some time it has became my main operating system and i want the grub bootloader back, how do i go about this?

Sean

---

### Post by spiderbatdad on 2008-08-19
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by SeanArronD on 2008-08-19
I dont have a live CD... is there anyway to restore grub without the need for a live cd?

Sean

---

### Post by banewman on 2008-08-19
Hi SeanArronD,
You can do that with a live cd
Boot into the live cd and open a terminal
type in - sudo grub
 then - find /boot/grub/stage1
this will give an answer like (sd0,1)
then type in - setup (sd0)
(0 will be the first hard drive, 1 will be the second hd
your choice where you set it up, first is standard :))
then type - quit  
and reboot :)

---

### Post by spiderbatdad on 2008-08-19
Sorry I don't know of a way without a live cd or install cd.

---

### Post by caljohnsmith on 2008-08-19
If you can still boot into Ubuntu, which I assume you can, you don't need to use a Live CD. Just do the following in a terminal:
```
sudo grub
grub> find /boot/grub/stage1
[should return your Ubuntu partition in the form of (hdX,Y)]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```

---

### Post by SeanArronD on 2008-08-19
Thanks for the help :)

I thinks its sorted, just need to reboot now :D

Sean

---

