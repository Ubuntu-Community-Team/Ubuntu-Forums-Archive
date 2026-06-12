---
title: "dual boot problem"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Harisz750 on 2008-04-24
i just installed ubuntu 8.4 in a second partition. i also have winXP, however when grub starts and press esc it shows the boot ment with linux kernel, linux kernel safe mode and memtest, but winxp is nowhere!!!!! so i can't boot into my XP partition... in a different computer i installed ubuntu 7.10 and everything works fine!!!! please help

---

### Post by HDave on 2008-04-24
Here is my GRUB menu item for Windows XP on my dual boot.  I copied it from from /boot/grub/menu.lst

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I suggest you add this to your menu.lst (sudo gedit /boot/grub/menu.lst) making sure you change the "(hd0,0)" to whatever your system requires.

Good luck.

---

### Post by SOULRiDER on 2008-04-24
Are you 100% possitive you didnt install on top of windows? Can you see your windows drive from Linux?

Please, paste the output of
```
sudo fdisk -l
```
Remember to use [code] tags when posting it.

---

### Post by kansasnoob on 2008-04-24
Well, unless you wiped the drive and let ubuntu have the whole drive just take a deep breath.

Can you boot into Ubuntu?

If so see if you have >System>Administration>Partition Editor

You're not going to use it to change anything but it will tell you what you have.

If you don't have it, then go into Synaptic and get it! Just open Synaptic and click on search, then type in gparted. Then install gparted.

Then close synaptic.

When you look in System>Administration you should now see a partition editor. That's GParted. Open it and see what you have. then get back to us.

Even if it means starting a new thread.

If the Windows partition is still there it can be accessed by altering the GRUB menu and/or a few quick moves in GParted.

Patience is a virtue!

---

### Post by Harisz750 on 2008-04-24
thanks HDave ...  this solved my problem. thanks a lot all of you for your quick replies. now i can boot in windows again!!!!

---

### Post by SOULRiDER on 2008-04-24
Bright side, you managed to fix the problem! Bad side.. you managed to fix windows :p

Just joking, im glad you got it working now.

---

### Post by Harisz750 on 2008-04-24
> **SOULRiDER said:**
> Bright side, you managed to fix the problem! Bad side.. you managed to fix windows :p

Just joking, im glad you got it working now.

Yeah,,, unfortunatelly i need windows... not me exactly,, my brother!!! something else, how i mark the thread as solved?????

---

