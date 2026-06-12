---
title: "problem with grub"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by martysha on 2008-05-26
:)
hi everybody,

i have a big problem here with grub installing. first of all, i have 1 hdd with 3 partitions - sda1 for linux, sda2 - windows and sda3 -swap. 
i installed grub for the linux with hd0,0 and it worked perfectly. but after that, i had problems to find what to write for the windows, i wrote hd0,2 in the conf file and it gave me error 13 no executable file

i searched and found in this forum a solution with 

map hd0 = hd1
map hd1 = hd0

so i wrote it in the conf file

and after that it's all broken :( the pc give me "error operating system" on loading

i think now i must try to load grub conf file and after deleting the map lines, write hd0,1 for the windows?

tried to open the grub conf file after rescuing the system, but i can't! please help me - i'm feeling really stupid there #-o

---

### Post by Xiong Chiamiov on 2008-05-26
When loading Windows, you have to use different syntax.  For example, mine is:
```

title		Windows NT/2000/XP (loader)
root		(hd0,3)
#savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1

```

Whenever you're troubleshooting GRUB, [SuperGrubDisk]("http://supergrubdisk.org") is your friend.  Finding it earlier would have saved me *so* much time.

---

### Post by bumanie on 2008-05-26
You will have to re-write grub to (hd0,0) via the live cd. Boot live cd.
In terminal > sudo grub > root (hd0,0) > setup (hd0) > quit Ubuntu should now boot, but windows won't. After that you will have to do a map command in the windows entry (as you suggested) and add it to your /boot/grub/menu.lst
map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
That should work, if not go [here]("http://users.bigpond.net.au/hermanzone/p15.htm") for more info on grub. You can also post a copy of your /boot/grub/menu.lst for someone to look at, that is helpful also.

---

### Post by martysha on 2008-05-26
[B]Xiong Chiamiov,

bumanie,[/B]

:D

thank you so much! i will try it just after i go back home. 


hope it will work this time ;)

---

### Post by meierfra. on 2008-05-26
Try this for Windows in menu.lst:


```
title  Windows
root (hd0,1)
makeactive
chainloader +1

```


(Grub is already installed correctly (edit:get this wrong, overlooked a sentence). So the "sudo grub , root (hd0,0), setup (hd0), quit" will not change anything. The map statement are only used if you have more than one hard drive. You said windows is on /dev/sda2. Grub starts counting at 0. So /dev/sda2 is (hd0,1) in Grub speak.)

---

### Post by martysha on 2008-05-27
**bumanie**

thank you, it worked! now i can boot my linux and grub is working perfectly. 

the problem is that now i cannot boot my windows. i don't have any message when i'm choosing it, so i think that the problem is in the windows boot.ini file. the grub now is working fine and is well configurated (thank you guys)

today i will try to repair the win installation :) hope my grub will not break again :mad: ;)

---

### Post by meierfra. on 2008-05-27
Oops.

I had overlooked this sentence

> and after that it's all broken  the pc give me "error operating system" on loading


So yes, then bumanie's suggestion was right on.

---

### Post by louieb on 2008-05-27
> **meierfra. said:**
> Try this for Windows in menu.lst:


```
title  Windows
root (hd0,1)
makeactive
chainloader +1

```...


> **martysha said:**
> ...the problem is that now i cannot boot my windows. ..problem is in the windows boot.ini file. the grub now is working fine ...

meierfra has it right.  That entry will boot a windows install located in the 2nd partition of the 1st hard drive. 
The map command is used when windows is not on the 1st hard drive. The purpose is to make windows think its on the 1st drive.

---

### Post by martysha on 2008-05-27
> **louieb said:**
> meierfra has it right.  That entry will boot a windows install located in the 2nd partition of the 1st hard drive. 
The map command is used when windows is not on the 1st hard drive. The purpose is to make windows think its on the 1st drive.

ah yes, i see now. i will try to delete the map lines and boot windows like that. 
you think it might be the cause of the problem? :confused:

---

### Post by martysha on 2008-05-27
](*,) ](*,) ](*,) [-(

report from that evening:

i came home, tried to rewrite the grub. still not booting windows, without a message.

ok. i take my win boot disk.. recovery console. deleting and rewriting the boot.ini file. succes.

i restart, choose windows and:

```
Booting Windows

root (hd0,1)
Filesystem is FAT, part. type 0xc
makeactive
chainloader +1

Disk error
Press any key to restart
```

maybe it will be much easier to reinstall all

but i want to know what exactly is the problem! i feel i can fix it ](*,)

---

### Post by meierfra. on 2008-05-27
Lets's first see whether you can boot into Windows without grub:
Boot from the Windows CD, enter the repair console (via "r") and  type

```
fixboot
fixmbr
``` 


and reboot. You should boot  directly into Windows.

To reinstall Grub again, use bumanie's method. Fixboot might have solved  your problem. So try booting into Windows from the Grub Menu again.


For further troubleshooting, post the output of "sudo fdisk -l", and also post menu.lst and  boot.ini. You can get to "boot.ini" from Ubuntu. 
For example you can do

```
sudo mkdir /media/XP
cd /media
sudo  mount -t ntfs-3g /dev/sda2 XP
cat XP/boot.ini 
```

---

### Post by meierfra. on 2008-05-27
Also could you tell as how you installed Ubuntu? Did you resize your Windows partition and then created the Ubuntu partition in front of the Windows partition?

---

### Post by martysha on 2008-05-27
**meierfra,**

thank you for your advice. i followed it strictly. and i'm sure it would work in other circumstances :D explanation below


first, i made fixboot and fixmbr. but i think that there was a big big problem somewhere because after that NOTHING was booting and on the screen i had only  Disk error

so.. like i thought it was necessary to reinstall ;)  last attempt to save failed 

and when i was reinstalling windows i understood where was the problem!!

from the windows the partitions i had were arranged differently!


instead of:
sda1 - linux ext3 
sda2 - win fat
sda3 - swap

i had
G:/ - 200 mb (from buffer 0!!!)
C:/ - WINDOWS
and my linux partition on last place

:confused: 

honestly i don't understand exactly what happened, but i think that it is the reason of my problems.. so of course my fault. 

now i have my win and my linux booting perfectly, YES!! and i've learned much more :grin:

thank you again **meierfra** ;)
(just for your info - i had a brand new empty hdd and i installed linux first, resized the partitions with fdisk and left the second logical volume with fat system sda2 for the windows)

---

### Post by meierfra. on 2008-05-27
> i had a brand new empty hdd and i installed linux first, resized the partitions with fdisk and left the second logical volume with fat system sda2 for the windows

Just for future reference: When  you start with a empty hard drive, its  best to install  windows first and then linux.

> so of course my fault. 

No, no no. At the Ubuntu forums we always blame everything on Windows.:)

> now i have my win and my linux booting perfectly

Good!

And sorry for discrediting bumanie's perfect suggestion yesterday. I was working several cases at the same time and started to get sloppy. (And I always get mad when I see after people do that)

---

