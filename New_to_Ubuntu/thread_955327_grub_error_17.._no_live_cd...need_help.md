---
title: "grub error 17.. no live cd...need help"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by sazan on 2008-10-22
i am getting this error 17 since morning on my system and it is not letting me to get my dual boot os (xp and ubuntu) to boot.. 

i have read a similar thread saying that i need a live cd to solve that problem.. i dont hav d live cd currently .. so i will need to get it from my frend and then do the procedure.. 

so i wanted to ask is that is it possible for me to solve this problem with my start up disk and going into DOS . .. and what shud i do so that i dont encounter this problem again.. 

also i came across d problem for this occur was that my linux OS has been changed to amoeba linux.. how does this happen without me interferring with anythin,,,??

---

### Post by taseedorf on 2008-10-22
your partition ID changed, ...probably because you installed windows after linux?...or another linux?.... anyways... you need a live cd.  unless you can access your files and write them from windows..

---

### Post by sazan on 2008-10-22
> **taseedorf said:**
> your partition ID changed, ...probably because you installed windows after linux?...or another linux?.... anyways... you need a live cd.  unless you can access your files and write them from windows..

i had installed linux after windows... 

i cant access windows since error 17 halts when it gives the message... 

i think i wil get live cd and then carry out wit the solution... but anyone can tel me how i can prevent this to happen in future... and y does it happen??

---

### Post by Ducatiboy Stu on 2008-10-22
Download and burn the SuperGrub LivCD...( Of course you will need a working PC )

It will find your Grub menu and restore it...simple

It really your best bet...

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by sazan on 2008-10-22
> **Ducatiboy Stu said:**
> Download and burn the SuperGrub LivCD...( Of course you will need a working PC )

It will find your Grub menu and restore it...simple

It really your best bet...

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

thanks i will try that ... hope it solves the problem..

---

### Post by sazan on 2008-10-22
hey.. i got my live cd and now in terminal.. this is wat i hav done .. 
1) Boot from the Ubuntu CD
2) Open a Terminal (Applications->Accessories->Terminal)
3) Run "sudo -s"
4) Run "mkdir /ubuntu"
5) Run "mount /dev/sdc1 /ubuntu" (where /dev/sdc1 is your Linux root partition)
6) Run "chroot /ubuntu"
7) Run "cd /boot/grub"

my device.map looks like this

(hd0) /dev/sda

8) then i typed -> grub --device-map=device.map

grub> root (hd0,1)

and i get selected hard disk not found.. 

can anyone tell me wats the solution for this..

---

### Post by caljohnsmith on 2008-10-22
So are you getting the Grub error 17 before you see a Grub menu on start up (or before seeing something like "Press ESC to see menu"), or after you get the Grub menu and select Ubuntu? How about first posting:
```
sudo fdisk -lu
```

---

### Post by sazan on 2008-10-22
> **caljohnsmith said:**
> So are you getting the Grub error 17 before you see a Grub menu on start up (or before seeing something like "Press ESC to see menu"), or after you get the Grub menu and select Ubuntu? How about first posting:
```
sudo fdisk -lu
```

i get the frub error 17 before i see grub menu..

sudo fdisk -lu :->



ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    32820794    16410366   af  Unknown
/dev/sda2   *    32820795    95152994    31166100    7  HPFS/NTFS
/dev/sda3        95152995   312560639   108703822+   f  W95 Ext'd (LBA)
/dev/sda5       125949663   188410319    31230328+   7  HPFS/NTFS
/dev/sda6        95153121   114688034     9767457   83  Linux
/dev/sda7       114688098   125949599     5630751   82  Linux swap / Solaris
/dev/sda8       188410383   312560639    62075128+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 4046 MB, 4046979072 bytes
25 heads, 24 sectors/track, 13173 cylinders, total 7904256 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               8     7904255     3952124    b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-10-22
What happened or what circumstances led up to the Grub error? In other words, what was going on with the computer before you first got the Grub error? Try doing the following from your Live CD to reinstall Grub to your HDD's MBR (Master Boot Record):
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
And post the results of the above commands. Reboot, and let me know if that changes anything.

---

### Post by Duck2006 on 2008-10-22
If "caljohnsmith" way don't not work for you try.

sudo grub
find /boot/grub/stage1  (the output of this use when you use root(hdx,y))
root (hdx,y)
setup (hd0)
quit

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by sazan on 2008-10-23
> **caljohnsmith said:**
> What happened or what circumstances led up to the Grub error? In other words, what was going on with the computer before you first got the Grub error? Try doing the following from your Live CD to reinstall Grub to your HDD's MBR (Master Boot Record):
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
And post the results of the above commands. Reboot, and let me know if that changes anything.

i dont knw how it led to Grub error.. i was installing wine a day before and then i was browsing net.. then i switched off my pc and then the next morning i got this grub error from nowhere... 

i did run d above commands.. for root (hd0,5) ,it worked fine .. then at setup (hd0) i got error saying 'cannot mount the disk'....

after 1 hour of hardgoing i wasnt unable to solve the problem and i wanted the system very bad.. so in the end i just formatted d system and reinstalled the OS... so now it is working fine... but i want to make sure this problem doesnt occur again.. any tips ??

---

