---
title: "Help to Recover Lost NTFS Drive."
date: 2012-02-25
forum: New to Ubuntu
---

### Post by davesmith on 2012-02-25
Hi

I'm unable to mount my Seagate external h/d following a failed attempt to upgrade to 11.10. The system can see it - but is unable to mount it. Here is some terminal output:-

<sudo mount /media/sdb>

and the response was:-

<NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS>

However, the drive mounts OK on my friend's windoze xp m/c and the data is accessible

I would like to recover this drive and use it on my Ubuntu. Could someone help please? I need some good terminal code.

Thanks in advance

---

### Post by sudodus on 2012-02-25
Please post the output of the following commands
```
sudo fdisk -lu
```
and
```
cat /etc/fstab
```
That will make it easier to help.

---

### Post by davesmith on 2012-02-25
Thanks

Here is the output of <sudo fdisk -lu>

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008966e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74846834    37423386   83  Linux
/dev/sda2        74846835    78140159     1646662+   5  Extended
/dev/sda5        74846898    78140159     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 2000.3 GB, 2000398934016 bytes
1 heads, 63 sectors/track, 62016336 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00d34d04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  3907024127  1953512032+   7  HPFS/NTFS

_________________________________________________________________

And here is the output of < cat /etc/fstab>

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4c91519a-d6d3-4cec-aa10-afb3bfa5c274 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e8a5d197-cfe9-4082-86bb-accd50dad67d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

_________________________________________________________________________________

I cant see the external drive listed in /etc/fstab - is that what's wrong? Thanks for helping

---

### Post by sudodus on 2012-02-25
You need not have it (or should not have it) in your fstab file.

You can read from ```
man mount
```

```
       The standard form of the mount command, is
             mount -t type device dir
```
So in your case try
```

sudo mkdir -p /mnt/sdb1
sudo mount -t auto /dev/sdb1 /mnt/sdb1

```
But probably you can also [auto]mount it by trying to browse to it with your file browser (Nautilus, Konqueror, Thunar depending of your flavour of Ubuntu).

If this does not work, there is something wrong, that I cannot see from your posted output. What happens if you disconnect it from USB, then shut of the power (if power connection), then reconnect the power and finally reconnect it to a USB port? If no luck, try another USB port! Sometimes USB ports are bad.

---

### Post by davesmith on 2012-02-25
hi Sudotus

I have managed to get the drive to mount using the terminal to add a line to fstab

<gksudo gedit /etc/fstab>

when gedit opened the fstab file, first i saved a backup to "Documents"

then added this code to the bottom of the fstab file

</dev/sdb1 /media/sdb1 ntfs-3g defaults, force 0 0>[FONT=monospace]

I saved the fstab file and tried 

<s[/FONT]udo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h>
[FONT=monospace]
an icon appeared on the desktop "sdb1" - and can open the drive with nautilus and see my data!

The question now is - how can i make it auto boot when i connect the drive to the usb port? usb memory sticks autoboot ok



[/FONT]

---

### Post by chinna saaeb on 2012-02-25
Very long back(may be about 3- 4 years) back I had a similar problem. My NTFS partition was not being recognized by WIndows and perhaps Redhat. It was a dual boot partition.
I could recognize it with slax live and recover the data.
You can try

---

### Post by davesmith on 2012-02-25
I can get the drive to mount, as described above - but only if i use the terminal and sudo

But would be nice to get it to autoboot

---

### Post by roelforg on 2012-02-25
May i direct your attention to:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by sudodus on 2012-02-25
> **davesmith said:**
> hi Sudotus

I have managed to get the drive to mount using the terminal to add a line to fstab

<gksudo gedit /etc/fstab>

when gedit opened the fstab file, first i saved a backup to "Documents"

then added this code to the bottom of the fstab file

</dev/sdb1 /media/sdb1 ntfs-3g defaults, force 0 0>[FONT=monospace]

I saved the fstab file and tried 

<s[/FONT]udo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h>
[FONT=monospace]
an icon appeared on the desktop "sdb1" - and can open the drive with nautilus and see my data!

The question now is - how can i make it auto boot when i connect the drive to the usb port? usb memory sticks autoboot ok[/FONT]

0. If you have the partition in fstab, the computer will try to mount it when booting, and it will be mounted by root (superuser). If you want it to automount afterwards (when you are already logged in), you should not have it in fstab. (I have an external (eSATA) drive in fstab with the option noauto. I do not want to mount it at boot, because it is seldom used. But I want to mount it afterwards, and then can I mount it either manually with sudo mount, or with a 'home-made' kdialog GUI, that can mount and unmount drives.)

1. I want other external drives (USB and eSATA) to automount, so they are not in fstab. This is the case for USB HDDs, flash sticks and flash cards in a card reader, camera as well as mobile phone. These will be automounted in the desktop versions of Ubuntu.

Questions:

- I understand that you have upgraded to Ubuntu 11.10. Is it the 'vanilla' flavour with Unity or gnome 3? Is the file browser Nautilus working? Did it automount this USB HDD before, but not now? Does it work if you boot from a live CD or USB drive?


- If you 'comment away' the drive from fstab (typing # in the first position of the line) and reboot:
What happens if you ***unmount*** (if mounted), ***disconnect*** the USB HDD from USB, then ***shut of the power*** (if power connection), wait for 10 seconds, then ***reconnect the power*** and finally ***reconnect it to a USB port***? It should automount, otherwise I think there is something wrong with your current version of Ubuntu, and until that is fixed, you might need to use the manual mounting.

But it can be more convenient using an alias for example provided you have created a directory [FONT="Courier New"][SIZE="3"]/media/sdb1[/SIZE][/FONT]. ***Try with and without [COLOR="Red"]sudo[/COLOR]***, maybe it will be better to mount as the normal user.

```
alias msdb1='sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1'
``` but it is better to use the UUID, because the drive may not always be assigned to /dev/sdb1. You find the UUID with the command ```
sudo blkid
``` and you should use that string without the quotes "[COLOR="Red"]5921-6A05[/COLOR]" like this (your UUID will be different).
```
alias msdb1='sudo mount -U [COLOR="Red"]5921-6A05[/COLOR] -t ntfs-3g /media/sdb1'
``` or
```
alias msdb1='sudo mount -U [COLOR="red"]5921-6A05[/COLOR] -t auto /media/sdb1'
```

So use the command ***msdb1*** (or select another unique name if you prefer to mount the drive!

*Edit: using the alias command in a terminal lasts only until the terminal is closed, but if you enter the command into ~/.bashrc (at the other aliases) it will be part of the environment for all future terminal windows.*

---

### Post by davesmith on 2012-02-25
Sudodus

I very much appreciate your help this afternoon. Thank you.

However, I cannot get any of the code to automount my Seagate drive - yet.

To answer your questions, prior to the attempt to upgrade to 11.10 the drive was working fine. However, the upgrade was unsuccessful as the m/c repeatedly hung during the install. The drive was connected during the ugrade - but at one stage the m/c locked up. 

So I re-installed the old system which went well - except the drive will not automount.

However, will the entry in fstab the drive mounts ok during boot, an icon appears on the desktop, i can write and copy data. But it needs <sudo umount/dev/sdb1> to unmount it.

I think the drive is ok but something somewhere prevents it from automounting. Other media automount ok, another usb drive, a memory stick, my camera.

Maybe we should start from the begining!

---

### Post by sudodus on 2012-02-25
Do you want it to automount at boot? In this case use the line in fstab. But it means you need to mount and unmount as sudo. An alternative might be to run ```
gksudo nautilus&
``` and mount/unmount it from there (as GUI superuser).

Have you tried to uncomment the line in fstab and tested if the aliases work? It might be more convenient unless you always or almost always have the drive connected. And maybe you won't need to mount it with sudo.

Now that I know that your external drive was connected at the bad upgrading, I suggest that you connect it to a running windows system and run ```
chkdsk /f
``` to repair any error or strange things of the ntfs file system.

---

### Post by davesmith on 2012-02-25
What will chkdsk /f in a windoze system do, exactly? What are the chances that it will further damage the drive and i'll loose all my data? I am thinking about doing it

---

### Post by davesmith on 2012-02-25
Ah, now I think i'm getting close to solving this issue

As mentioned above, adding the following line to my fstab file lets the drive mount during boot

</dev/sdb1 /media/sdb1 ntfs-3g defaults, force 0 0>

However, booting up with the drive unconnected, then connecting it to a USB makes it start up coz i can hear it whirring - but it will not automount

then, running the following in the terminal will mount it:-

<sudo mount /dev/sdb1>

and this code unmounts it

<sudo umount /dev/sdb1> 

So it cant be too difficult to get it to automount, can it?

---

### Post by sudodus on 2012-02-25
> **davesmith said:**
> What will chkdsk /f in a windoze system do, exactly? What are the chances that it will further damage the drive and i'll loose all my data? I am thinking about doing it
I and millions of people have done chkdsk /f since the days of MSDOS. It is considered safe because it has been debugged since decades; it is repairing errors in the file system of Windows (FAT and NTFS).

Many times this 'simple' command will revive a Windows system that cannot be booted after a power failure. Chkdsk can be used with other options to search for and mark bad sectors on a HDD.

---

### Post by westie457 on 2012-02-25
@sudosus

could the bit in red be the problem?

```
Disk /dev/sdb: 2000.3 GB, 2000398934016 bytes
[COLOR="Red"]1 heads[/COLOR], 63 sectors/track, 62016336 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00d34d04
```

If it is would testdisk be the best option to fix things?

---

### Post by sudodus on 2012-02-25
> **davesmith said:**
> Ah, now I think i'm getting close to solving this issue

As mentioned above, adding the following line to my fstab file lets the drive mount during boot

</dev/sdb1 /media/sdb1 ntfs-3g defaults, force 0 0>

However, booting up with the drive unconnected, then connecting it to a USB makes it start up coz i can hear it whirring - but it will not automount

then, running the following in the terminal will mount it:-

<sudo mount /dev/sdb1>

and this code unmounts it

<sudo umount /dev/sdb1> 

So it cant be too difficult to get it to automount, can it?
You can continue like this now. As long as the partition sdb1 is in the fstab file, you can use those short [u]mount commands, because the OS knows where and how to mount it. But I suggest that you change the entry and use UUID instead of the device name, because if another (USB) drive is found before this one, it will 'steal the device name sdb1' and create problems for you.

Since the OS seems to work well now, ***I think you should actually try to edit /etc/fstab putting a # sign at the first position of the line with sdb1 and reboot the computer. ***Maybe it will automount or at least mount, when you click on its icon in the left panel of the file browser. When in the fstab, the partition will only automount at boot time, and not if you connect it after the booting process has finished. If automount still does not work (with the # sign and after reboot), edit /etc/fstab again removing the # sign, and after next reboot you will get back to the current state.

Another option might be to have a script running, that will look for the drive, and when found, mount it. But it will make the computer a little more busy. If you use [FONT="Courier New"][SIZE="3"]cron[/SIZE][/FONT], it could run once every minute. If you want it to run more frequently, you can make a script with a built-in loop and use [FONT="Courier New"][SIZE="3"]sleep[/SIZE][/FONT] to wait, and have the script start at boot or login.

---

### Post by sudodus on 2012-02-25
> **westie457 said:**
> @sudosus

could the bit in red be the problem?

```
Disk /dev/sdb: 2000.3 GB, 2000398934016 bytes
[COLOR="Red"]1 heads[/COLOR], 63 sectors/track, 62016336 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00d34d04
```

If it is would testdisk be the best option to fix things?

Good observation! I didn't notice that. Yes, maybe testdisk could fix that, if it should be fixed. Do you think that could have been tampered with during a failing upgrade or installation to 11.10?

---

### Post by westie457 on 2012-02-25
> **sudodus said:**
> Good observation! I didn't notice that. Yes, maybe testdisk could fix that, if it should be fixed. Do you think that could have been tampered with during a failing upgrade or installation to 11.10?

It certainly would not hurt anything to use testdisk to check the drive geometry and see what it says and if necessary change the number of heads to 255 (which is usually the default setting). **Do not change any other values** just the value for the number of heads. It might make everything okay.

Absolutely no idea what could have caused that number to change as I have not seen it happen to me.


EDIT:  to OP, you can get testdisk either from here [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) or istall from the Software Centre.

---

### Post by davesmith on 2012-02-25
@westie

what is the usage of testdisk and thank you i will try it

---

### Post by davesmith on 2012-02-26
Yup, testdisk found the problem and recommends changing the number of heads from 1 to 128. Not 255 as we thought.

I can mount and dismount the drive and access the data. So I am going to back the drive up and then let testdisk fix it.

Meanwhile i will mark this thread as closed. Thanks for your help

Regards

---

