---
title: "Black screen at load"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by Mandangalo on 2012-10-01
Greetings! I want to try Linux, but when I boot into Ubuntu I always get a black screen. After my bios loads, I'm asked if I want to boot in Win 7 or Ubuntu. I choose Ubuntu, the screen flashes purple for a second, and then I'm stuck at the black screen. Any thoughts?

I'm using an AUSUS GTX 570 GPU with current drivers, and I'm trying to use the 64 bit version od Ubuntu.

---

### Post by NikTh on 2012-10-01
Hi , 

how you installed Ubuntu ? through windows (wubi installer) or regular Dual-boot with a LiveCd/Usb ? 

Thanks

---

### Post by Mandangalo on 2012-10-01
I have installed it both ways, through the win installer and the CD both. The same problem occurs with both methods.

---

### Post by NikTh on 2012-10-01
Hi , 

Can you boot from a LiveCd/Usb and open a terminal [Ctrl+[Alt]+[t] and give the results of these commands ? 

```
sudo fdisk -l 
sudo parted -l
```You can copy-paste the commands from here to terminal. 
Also , put the results between the brackets so can be readable . [B][noparse]```
Here
```[/noparse]

[/B]If you boot from a LiveCd/Usb stay there , cuz probably I will ask for other results too. 

Thanks

---

### Post by Mandangalo on 2012-10-01
I can't get far enough to use the terminal. When I start from my CD, I get a purple screen for a moment, then a black screen with nothing. I can't do anything at this black screen.
[EDIT] tried again, this time it asked me what language. Then it went black again.

---

### Post by NikTh on 2012-10-01
> **Mandangalo said:**
> I can't get far enough to use the terminal. When I start from my CD, I get a purple screen for a moment, then a black screen with nothing. I can't do anything at this black screen.

Try the nomodeset parameter , see here how : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Mandangalo on 2012-10-01
This got me in. thanks!

---

