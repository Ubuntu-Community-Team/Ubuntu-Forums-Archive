---
title: "System Crashed.Dont know what to do."
date: 2008-06-01
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-01
Three days ago when i was working with a dual boot xp and ubuntu hard disk there was a lot of processes running and suddenly my system rebooted.

In next insteed of Grub the screen was just blank with a single cursor point at the top right corner.

Then i tried with my live cd and it took me to BUSY BOX SHELL.

in that it diaplayed a set of messages like

```
ata 4.00: exception Emask 0x0 SAct 0x0 sErr 0x0 action 0x2 frozen
ata 4.00: cmd c8/00:08:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in

```
etc.

i dont know what to do now.

when i tried with windows reinstallation the screen in which it shud show the list of disks to select to install, showed me the message that READ ERROR. the disk could not be read.

whats the cause for this and whats the solution.

then i too got the message

```
ata 4.00: status {DRDY}
                 revalidation failed (errno=-2)

```

in the bussy box shell

---

### Post by rraj.be on 2008-06-01
any one there.

plz help me

---

### Post by raydeen on 2008-06-01
Try booting with your Windows CD and going into Recovery Mode, and then run CHKDSK c:/ -R to see if there are any physical errors on the disk. (I think that's the syntax. type CHKDSK /? to make sure. I run too many OS's to remember :D)

---

### Post by rraj.be on 2008-06-01
Yes this helped me and this with surface test showed me many errors and they are removd later.

the exact syntax is

```
chkdsk [DRIVE] /v /f 
```

but whats the main reason for this type of errors ..

could it destroy my hard disk if it happens many times?

---

### Post by hal10000 on 2008-06-01
This looks as if it could be a hardware error (maybe your harddisk or controller is crashed).
If you cannot boot windows, then you might boot from your ubuntu live-cd and try
[COLOR="Red"]sudo fdisk -l[/COLOR] in a terminal-window.
This shoul show you all connected harddrives and their partitions on your system.
It may look similar to this one on my own computer:
> 
[COLOR="Red"]sudo fdisk -l[/COLOR]


Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xd71ed71e

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1          19      152586   83  Linux
/dev/sda2              20       10218    81923467+  83  Linux
/dev/sda3           10219       19457    74212267+  83  Linux

Platte /dev/sdb: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00000000

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1       18237   146488671   83  Linux
/dev/sdb2           18238       30401    97707330   83  Linux

Platte /dev/sdc: 40.0 GByte, 40020664320 Byte
255 Köpfe, 63 Sektoren/Spuren, 4865 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x37363534

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1   *           1         892     7164958+   7  HPFS/NTFS
/dev/sdc2             893        2840    15647310   83  Linux
/dev/sdc4            2841        4865    16265812+   f  W95 Erw. (LBA)
/dev/sdc5            2841        4802    15759733+  83  Linux
/dev/sdc6            4803        4865      506016   82  Linux Swap / Solaris

Platte /dev/sdd: 82.3 GByte, 82348277760 Byte
255 Köpfe, 63 Sektoren/Spuren, 10011 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x24982497

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdd1               1        5222    41945683+  83  Linux
/dev/sdd2            5223       10011    38467642+   5  Erweiterte
/dev/sdd5            5223       10011    38467611   83  Linux


---

### Post by rraj.be on 2008-06-01
And for your further clarification, Mr hal10000,

i have mentioned that i tried using live cd and in that only i got the above stated error output.

could you mention any other suggestions to boot to that drive please

---

### Post by hal10000 on 2008-06-01
> i have mentioned that i tried using live cd 

ok, i didnt't notice this, but it looks not good for either your harrdive, your cd-drive or your ide-controller. When your system suddenly rebooted as you mentioned above, i suppose you were working on  eihter windows or linux and when you tried to boot your live cd you got the error message.
Now the question: Can you boot your windows CD (or any other bootable CD or DVD like knoppix or a SuSE-live-CD)?
If not, then i suppose either your cdrom-drive or your ide controller is damaged.
Because the errors happend when working on your harddrive _and_ with your live-cd, it might be the worst case, your ide-controller.
If you have another (perhaps old) cdrom or dvdrom drive you should plug this one in instead of your current and try to boot a cd from this device to verify if the error relies on your cdrom-drive.
If the error is not caused to th cd-drive then your ide-controller might be damaged and in this case you might need a new motherboard.

---

### Post by rraj.be on 2008-06-01
when i trien to reinstall my windows using windows disk there was no drive that i could see.

I could boot cd but inside that i am unable to get in to workstation environment.

Its just taking me to BUSY BOX shell.

i am sure that there is no problem with my dvd drive.

---

