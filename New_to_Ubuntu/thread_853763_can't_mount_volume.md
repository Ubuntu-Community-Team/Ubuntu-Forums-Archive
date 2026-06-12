---
title: "can't mount volume"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by seanmom on 2008-07-08
I have a program and a folder that I want to transfer from a desktop to a laptop.  I am trying to use a Best Buy Geek Squad 512 jump drive, which has been US-disabled.  When I plug it into the laptop, it says "cannot mount volume."  The laptop has unbuntu; the desktop has windows.

Any advice?

Thanks.

---

### Post by iaculallad on 2008-07-08
> **seanmom said:**
> I have a program and a folder that I want to transfer from a desktop to a laptop.  I am trying to use a Best Buy Geek Squad 512 jump drive, which has been US-disabled.  When I plug it into the laptop, it says "cannot mount volume."  The laptop has unbuntu; the desktop has windows.

Any advice?

Thanks.

While the drive is inserted: Issue the command below and post whatever it displays.

```
sudo fdisk -l
```

---

### Post by tamoneya on 2008-07-08
plug the drive into ubuntu and then go to terminal (application ->accessories -> terminal) and type```
sudo fdisk -l
```It will ask for your password.  Then post the output here and we can tell you how to get it mounted.

EDIT:  late again

---

### Post by m_duck on 2008-07-08
Have you just removed the pen drive from the Win pc or used "Safely remove hardware"? I've found that Ubuntu doesn't like it sometimes if you just remove the pen drive. If you plug it back in then use safely remove hardware, then try it in your laptop, it should work.

---

### Post by pbeesley on 2008-07-09
sorry to hijack but I'm having the same issue

I have two external hard drives and I can only get one of them to work and its always the last one I plug in. On the other I get "you are not privileged to mount the volume"

Here's my output ```




Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdea4ccc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8ce9ff8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9553    76734441   83  Linux
/dev/sdb2            9554        9964     3301357+   5  Extended
/dev/sdb5            9554        9964     3301326   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcee01a5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    b  W95 FAT32

Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a4ea6f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       14593   117218241    b  W95 FAT32

```

---

### Post by tamoneya on 2008-07-09
to mount the 250 GB external drive go to terminal and type this:```
sudo mkdir /media/250GB
sudo mount -t vfat /dev/sdc1 /media/250GB
```

for the 120 GB use this:```
sudo mkdir /media/120GB
sudo mount -t vfat /dev/sde1 /media/120GB
```

---

### Post by shift_00 on 2009-03-12
sorry guys to interrupt as well, but i've been looking for a solution for this for a while, please do help, i have two partitions that just won't mount, here is the output to fdisk -l
-----------------------------------------------------------------------
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94a494a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            5959        9461    28137847+  83  Linux
/dev/sda2   *        3527        5958    19535040   83  Linux
/dev/sda3               1        3526    28322563+  83  Linux
/dev/sda4            9462        9729     2152710   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

---------------------------------------------------------------------
sda1, and sda3 won't mount, i used to have i formatted them using GParted, and ever since i am facing this won't mount issue, and that the fstab file isn't updated.

thanks in advance

---

### Post by marie1015 on 2009-04-10
Hi, guys Happy Easter!! I am new here with the same problem. My flash driver was working perfect before I unplugged it without "remove it" first. I have followed the instruction from tamoneya, the message I got is below. 
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd16fd16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4771    38323026   83  Linux
/dev/sda2            4772        4864      747022+   5  Extended
/dev/sda5            4772        4864      746991   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d849646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

I kinda of figured out the "code" based on tamoneya, however doesn't seem to work, I am out of ideas and really frustrated, any help guys?? Please!!!

marie@marie-laptop:~$ sudo mkdir /media/120GB
marie@marie-laptop:~$ sudo mkdir /media/120GB
mkdir: cannot create directory `/media/120GB': File exists
marie@marie-laptop:~$ sudo mkdir /media/80GB
mkdir: cannot create directory `/media/80GB': File exists
marie@marie-laptop:~$ sudo mkdir /media/&#26032;&#23478;&#21367;
marie@marie-laptop:~$ sudo mount -t ntfs /dev/sdb&#26032;&#23478;&#21367;1 /media/120GB
ntfs-3g: Failed to access volume '/dev/sdb&#26032;&#23478;&#21367;1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
marie@marie-laptop:~$ sudo mount -t ntfs /dev/sdb1 /media/&#26032;&#23478;&#21367;
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/&#26032;&#23478;&#21367; -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/&#26032;&#23478;&#21367; ntfs-3g force 0 0
marie@marie-laptop:~$ mount -t ntfs-3g /dev/sdb1 /media/&#26032;&#23478;&#21367; -o force
mount: only root can do that

Eventually I got this message from trial and error, mount: only root can do that, what does that mean?? I think I am really close to the answer (maybe not close at all:KS) 

I would really appreciate some help and seriously thinking about going back to Windows. 


Many thanks guys!!

---

### Post by drowner on 2009-04-10
> **marie1015 said:**
> Hi, guys Happy Easter!! I am new here with the same problem. My flash driver was working perfect before I unplugged it without "remove it" first. I have followed the instruction from tamoneya, the message I got is below. 
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd16fd16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4771    38323026   83  Linux
/dev/sda2            4772        4864      747022+   5  Extended
/dev/sda5            4772        4864      746991   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d849646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

I kinda of figured out the "code" based on tamoneya, however doesn't seem to work, I am out of ideas and really frustrated, any help guys?? Please!!!

marie@marie-laptop:~$ sudo mkdir /media/120GB
marie@marie-laptop:~$ sudo mkdir /media/120GB
mkdir: cannot create directory `/media/120GB': File exists
marie@marie-laptop:~$ sudo mkdir /media/80GB
mkdir: cannot create directory `/media/80GB': File exists
marie@marie-laptop:~$ sudo mkdir /media/&#26032;&#23478;&#21367;
marie@marie-laptop:~$ sudo mount -t ntfs /dev/sdb&#26032;&#23478;&#21367;1 /media/120GB
ntfs-3g: Failed to access volume '/dev/sdb&#26032;&#23478;&#21367;1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
marie@marie-laptop:~$ sudo mount -t ntfs /dev/sdb1 /media/&#26032;&#23478;&#21367;
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/&#26032;&#23478;&#21367; -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/&#26032;&#23478;&#21367; ntfs-3g force 0 0
marie@marie-laptop:~$ mount -t ntfs-3g /dev/sdb1 /media/&#26032;&#23478;&#21367; -o force
mount: only root can do that

Eventually I got this message from trial and error, mount: only root can do that, what does that mean?? I think I am really close to the answer (maybe not close at all:KS) 

I would really appreciate some help and seriously thinking about going back to Windows. 


Many thanks guys!!

Yes, you are right, there was an 'unclean' unmount from windows.

You could boot into a windows machine, plug it in, and then 'Safely Remove Hardware' it. Then it will be fine.

If you really want to 'force' it, then putting 'sudo' before the command will work. It will ask you for your password.
```

sudo mount -t ntfs-3g /dev/sdb1 /media/&#26032;&#23478;&#21367; -o force
```
[B]This 'force' mounting is NOT recommended
You do this at your own peril.[/B] I have no idea what can happen if you force mount an 'unclean' drive. Perhaps somebody else could help you with that.

---

### Post by drowner on 2009-04-10
Oh, and 'only root can do that' - means that only the superuser of the computer (root) can run the command you asked.

In ubuntu you can get temporary superuser privileges by putting 'sudo' in front of the command you wish to run.

---

### Post by marie1015 on 2009-04-10
Thanks drowner, u r so smart, how do u know all of those?? I prob just try my flatmates' pc w Window. I made some yummy pancakes while I am waiting to install Root, haha, life is good!!:guitar:

---

