---
title: "[SOLVED] Unable to boot up vista"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by teumas on 2008-11-20
Hi all, my first post here so be nice :)
I've had vista on my computer for a while and yesterday I installed ubuntu 8.10 on a different hard drive.
Now I can boot up to ubuntu fine but if I choose to boot vista it stops at grub stage 2 and nothing else happens. 
I've googled this and tried different solutions but nothing works.
Well, except that the error message has changed.
First when I tried to boot vista it just jumped back to the list where you choose which os to boot. Then I changed some settings and the result was that it said: error: Invalid or unsupported executable format, when trying to boot vista.
Now I'm stuck at grub stage 2 and I have no idea what to do.

Any suggestions?

---

### Post by SuperSonic4 on 2008-11-20
What happens if you point your BIOS towards vista's hard drive first (or before the ubuntu one)?

---

### Post by teumas on 2008-11-20
I noticed something weired. If I choose my ubuntu hard drive as boot priority, it shows the list of os, click on vista it gets stuck at grub loading stage 2.
if I choose vista drive as priority it shows the same list but instead, when i click vista it just print grub on the screen and gets stuck there.

---

### Post by bennachie on 2008-11-20
I've done a couple of similar installations without trouble, and am not sure exactly what might have caused the problem - there are experts elsewhere on this forum who might chip in. However, you could try [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You will need to download an image and burn a disk (you should be able to do that easily from Ubuntu - or even from the LiveCD). 

Put your new disk into the optical drive before rebooting. The system should boot from the CD, and the software will then allow you to manipulate the boot blocks so that Vista becomes available again. Read the instructions carefully!

---

### Post by PocketDog on 2008-11-20
Did you defragment the Vista partition before installing Ubuntu?

---

### Post by caljohnsmith on 2008-11-20
It sounds like you have Grub installed to the MBR (Master Boot Record) of both your drives. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
From the fdisk output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
And please post that output. We can work from there if you want. :)

---

### Post by teumas on 2008-11-20
Okay, I\m on my live cd atm.
My output is
> 
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f004995

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1465145343   732571648    7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7be3ddac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   382057829   191028883+  83  Linux
/dev/sdb2       382057830   398283479     8112825    5  Extended
/dev/sdb5       382057893   398283479     8112793+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8100

ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'ff00

and thn i did, 
sudo mount /dev/sdb1 /mnt
cat /mnt/boot/grub/menu.lst

---

### Post by caljohnsmith on 2008-11-20
I would first recommend restoring a Windows MBR to your Vista drive; since you can boot the Ubuntu drive just fine, there is not reason you need to keep Grub in the MBR of your Vista drive. Also, based on what you've said about booting Vista, it sounds like you might have also accidentally installed Grub to the boot sector of the Vista partition. If you have a Vista Install CD, how about booting that, going to the command line, and run:
```
bootrec /fixmbr
bootrec /fixboot
```
If you don't have a Vista Install CD, you can instead download and use a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). 

Once you get Vista booting OK from its own drive, then to boot it from your Grub menu, first boot into Ubuntu and open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And then replace the existing Vista entry with:
```
title	   Windows Vista
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
That should be all it takes to boot Vista from Grub, but let me know if you run into problems.

---

### Post by teumas on 2008-11-20
Ok, two things.
I have my cd as first boot priority but if the second pro is my vista hard drive, it wont boot from the cd, instead it prints grub again.
However if i have the ubuntu drive as sec priority it works fine.
And when you say go to the command line, where do you mean? :P
When I booted the vista cd I choosed repair from the gui and there i found a terminal, kinda like cmd and there i wrote bootrec /fixmbr and that worked fine, however bootrec /fixboot produced an error message.
I can't really recall what it was atm, I'm a bit tired and have to go up for schoool in 5 hours. I will check into this further tomorrow.

And thanks a lot for the help so far, i really appreciate it!

---

### Post by teumas on 2008-11-21
so this is pretty much where I stand now. Anyone got any suggestions?

---

### Post by shoot2kill on 2008-11-21
an you boot into ubuntu either form the HDD or CD??

if so, can u run 

```
gksudo gedit /boot/grub/menu.lst
```

and post the output here ???

---

### Post by teumas on 2008-11-21
```

...
## ## End Default Options ##
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e2ba2521-2bdd-496c-a530-dadb02434f57
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e2ba2521-2bdd-496c-a530-dadb02434f57 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e2ba2521-2bdd-496c-a530-dadb02434f57
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e2ba2521-2bdd-496c-a530-dadb02434f57 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e2ba2521-2bdd-496c-a530-dadb02434f57
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```
And yeah, booting linux works fine.

---

### Post by teumas on 2008-11-22
So the problem seems to be grub sitting on my vista partition. Anyone know exactly how to recover the mbr with the vista install cd?

---

### Post by Bucky Ball on 2008-11-22
Caljohnsmith gave a pretty good explanation on the last page.

---

### Post by caljohnsmith on 2008-11-22
How about trying this from your Vista CD:
```
diskpart
```
At the diskpart prompt, type:
```
list volume
exit
```
That should list the drive letters for all your NTFS/FAT partitions, and since you only have one, I think it should list Vista as "C", but use whatever it is as follows:
```
e:\boot\bootsect.exe /nt60 [COLOR="Red"]X:[/COLOR]
```
But replace "X" with the Vista drive letter. If you get an error from that command, please let me know exactly which error it is, and then do:
```
chkdsk /r [COLOR="Red"]X:[/COLOR]
```
And run chkdsk as many times as it takes until it returns no errors, and then try the "bootsect" command again. Let me know how it goes.

---

### Post by teumas on 2008-11-22
it produced an error message, but a pretty strange one. It said that bootsect wasn't a valid commando.

---

### Post by caljohnsmith on 2008-11-22
OK, please see my previous post, I corrected it and think that should work; if it doesn't let me know the error.

---

### Post by teumas on 2008-11-22
Ok, bootsect worked now but gave the error
> The system cannot find the drive specified

And chkdsk gave 
> The type of the file system is RAW.
CHKDSK is not available for RAW drives.

---

### Post by caljohnsmith on 2008-11-22
Did the "list volume" command show your Vista partition, and if so, was it drive C? How about booting your Live CD and post the output of:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Where "-l" is a lowercase L, not a one. Also, if you change your BIOS to boot the Vista sda drive now, what exactly happens?

---

### Post by teumas on 2008-11-22
Ok, list volume shows two entries, where one is the vista cd.
The other, c, shows this information.
Ltr Fs    Type      Size
C   RAW   Partition 699 GB

from the live cd sudo mount /dev/sda1 /mnt returns;
mount: you must specify the filesystem type

And if if try to boot from vista drive it just prints out GRUB and gets stuck there so I have to restart my computer.

---

### Post by caljohnsmith on 2008-11-22
OK, how about trying this from the Live CD, and first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources; then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows Vista partition, choose "boot", then choose "Backup BS"; if testdisk gives you an warning that the "sectors are not identical", then choose "write". After you are done doing the "Backup BS" in testdisk, try:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
If the first command returns an error again about needing to specify the file system type, then start testdisk again:
```
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows Vista partition, choose "boot", then choose "Rebuild BS" this time; if testdisk gives you an warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, again try the mount/ls commands above and let me know if you still get the same mount error.

---

### Post by teumas on 2008-11-22
It worked! Typing from vista as we speak!
Thanks so much for all the help, and not giving up on me :)

---

### Post by caljohnsmith on 2008-11-22
> **teumas said:**
> It worked! Typing from vista as we speak!
Thanks so much for all the help, and not giving up on me :)
That's great news, glad it worked; cheers and have fun with Vista and Ubuntu. :)

---

