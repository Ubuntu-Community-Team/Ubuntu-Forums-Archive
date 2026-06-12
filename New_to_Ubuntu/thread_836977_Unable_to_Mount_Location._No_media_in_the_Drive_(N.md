---
title: "Unable to Mount Location. No media in the Drive (Not recognising CD/DVD Drive)"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by cklf0 on 2008-06-22
Hi. Absolute newbie to ubuntu. Have installed 8.04 and I am now getting 'Unable to mount location. No Media in the drive'. Not recognising any CD's I put into the drive. Very frustrating and starting to think I should have stuck with XP.

Can someone please help me?

---

### Post by azurepancake on 2008-06-22
I am quite new to working with disks and drives with Ubuntu, but I will try to help you either way.

First - put a CD that you know works into your CD-ROM. Try to open up a terminal session (Applications-->Accessories-->Terminal) and then type the following commands..

```
sudo mkdir /mnt/cdrom
sudo mount /dev/scd0 -t iso9660 /mnt/cdrom
ls /mnt/cdrom
```

See what this returns. If it lists the contents of the CD, then it is working and we can set it to do this automatically every time you boot your computer. If it does not work, then output what ever error it returns.

Good luck!

---

### Post by cklf0 on 2008-06-27
Thanks for trying to help. Followed your instructions and it said after:
sudo mount /dev/scd0 -t iso9660 /mnt/cdrom
No Medium Found

Any other ideas? I'm getting to the point wherby I may just stick with XP, which is a shame as I was looking forward to using Ubuntu.

---

### Post by azurepancake on 2008-06-27
Let me just try to get a better idea of how things are setup on your system.

Can you actually see the device when you go to Places-->Computer? 

What does the following command display?

```
 ls -l /dev/scd0
``` 

And perhaps if you post your 'fstab' file, it will help others and perhaps my self get a little better idea of what the problem is. Just type this into the terminal..

```
cat /etc/fstab
```

..and copy & paste the output to a post. 

Don't give up just yet. If we get this working, you'll be so happy you kept on on trying! I don't think I could ever go back to Windows as my main OS.

Thanks

---

### Post by cklf0 on 2008-06-27
Thanks for your help...

> **azurepancake said:**
> Let me just try to get a better idea of how things are setup on your system.

Can you actually see the device when you go to Places-->Computer? 

[COLOR="Blue"]Yes.[/COLOR]

What does the following command display?

```
 ls -l /dev/scd0
``` 

[COLOR="Blue"]/dev/scd0[/COLOR]

And perhaps if you post your 'fstab' file, it will help others and perhaps my self get a little better idea of what the problem is. Just type this into the terminal..

[COLOR="Blue"]carl@carl-desktop:~$ ls -1 /dev/scd0

/dev/scd0

carl@carl-desktop:~$ ls -1 /dev/scd0

/dev/scd0

carl@carl-desktop:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda1

UUID=c88c3495-f759-4285-98de-6bdc60012cbf /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda5

UUID=a6661c61-41fe-4caa-9da5-784740430345 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

carl@carl-desktop:~$ 
[/COLOR]


```
cat /etc/fstab
```

..and copy & paste the output to a post. 

Don't give up just yet. If we get this working, you'll be so happy you kept on on trying! I don't think I could ever go back to Windows as my main OS.

Thanks

---

### Post by unutbu on 2008-06-27
Try this again
```
 ls -l /dev/scd0
```
but the middle part is a "minus ell" not a "minus one".

Also please post the output of 

```
dmesg | grep -i CD-ROM
sudo lshw -C disk

```

---

### Post by cklf0 on 2008-06-27
Sorry. Have been told that before.This is what it has given me...

carl@carl-desktop:~$ ls -l /dev/scd0

brw-rw----+ 1 root cdrom 11, 0 2008-06-28 08:41 /dev/scd0

carl@carl-desktop:~$ dmesg | grep -i CD-ROM

[   24.857673] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5

[   25.008130] Uniform CD-ROM driver Revision: 3.20

[   25.008245] sr 1:0:0:0: Attached scsi CD-ROM sr0

carl@carl-desktop:~$ sudo lshw -C disk

[sudo] password for carl: 

  *-disk                  

       description: ATA Disk

       product: ST3120022A

       vendor: Seagate

       physical id: 0

       bus info: scsi@0:0.0.0

       logical name: /dev/sda

       version: 3.06

       serial: 3JT43115

       size: 111GiB (120GB)

       capabilities: partitioned partitioned:dos

       configuration: ansiversion=5 signature=a3b8a3b8

  *-cdrom

       description: DVD-RAM writer

       product: DVDRAM GSA-H10N

       vendor: HL-DT-ST

       physical id: 1

       bus info: scsi@1:0.0.0

       logical name: /dev/cdrom

       logical name: /dev/dvd

       logical name: /dev/scd0

       logical name: /dev/sr0

       version: JL10

       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram

       configuration: ansiversion=5 status=open

  *-disk

       description: SCSI Disk

       product: Flash Disk

       vendor: CBM

       physical id: 0.0.0

       bus info: scsi@3:0.0.0

       logical name: /dev/sdb

       version: 5.00

       size: 1010MiB (1059MB)

       capabilities: removable

       configuration: ansiversion=2

     *-medium

          physical id: 0

          logical name: /dev/sdb

          size: 1010MiB (1059MB)

          capabilities: partitioned partitioned:dos

          configuration: signature=00199fa1

carl@carl-desktop:~$

---

### Post by unutbu on 2008-06-27
Hi cklf0, I can not find anything wrong with your setup. There is no way of knowing for sure, but I think you are experiencing the bug which is described here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220957)

(There is no way of knowing for sure because no one at least on that thread knows what the source of the problem is yet).

Some have reported that they were able to avoid the problem by using Gutsy 7.10. If you are not completely turned off, I suggest you give that a go. 
I'm sorry for your rough first start with Ubuntu...

---

### Post by cklf0 on 2008-06-27
Thank-you for your help. It really is much appreciated.

---

### Post by tgss2000 on 2008-09-24
Does anyone have an update on this issue, which I believe is covered by Bug Report # 220957?  I found extensive discussion of the issue continuing until early September, apparently followed by silence, and no fix.

I am now experiencing this problem in a (almost) new Hardy Heron installation. The "almost" means that I managed to burn one data DVD, after which the problem appeared. The strange thing is (to me) that during the time I was running Ubuntu using Wubi, I burned a number of DVDs with no problem.

I am a complete Linux newbie and am struggling to deal with this.  I know that I don't want to keep rebooting Windoze to burn DVDs - if I have to do that, I might as well stay there.

Any info will be gratefully received.

Cheers

---

### Post by tgss2000 on 2008-09-27
Just in case anyone does get around to reading the previous message in this thread, it looks like the issue I had was a hardware problem - my apologies!
It's tricky when a piece of hardware decides to start misbehaving just at the time one decides to switch OS's.  In any event, a new drive worked just fine.

---

### Post by ydeardorff on 2010-01-30
I have the or simialr problem. After a windows update while dual booting through a wub installer setup /win Vista and ubuntu both lost the dvd rom.

The both show up, but say unable to mount location no media in the drive, or in vista please insert disk, followed by the dvd tray ejecting.

The dvd rom will seek under boot up, but not read. Once the OS is up and running (either of them) neither will access the dvd drive. 

Im reading a lot about this being a software problem not a hard ware problem, which changing the drive out doesnt fix it.

I contact microshaft, on it, only to have them tell me they no longer support vista, and to have me, have them fix the problem "they" caused, will cost me $59.00.

At this point I can give a damn about windows, but I would very much like to have my dvd drive back in ubuntu!

Here are my results based upon the above posts.






**cat /etc/fstab**


#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=2a1a69c4-adbf-4826-a77f-434b1684f73e none swap sw 0 0
/dev/sda1 /media/windows\040vista ntfs-3g defaults,locale=en_CA.UTF-8 0 0
# Original setting
/dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0


**ls -l /dev/scd0**


lrwxrwxrwx 1 root root 3 2010-01-30 09:30 /dev/scd0 -> sr0


**cat /etc/fstab**


# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=2a1a69c4-adbf-4826-a77f-434b1684f73e none swap sw 0 0
/dev/sda1 /media/windows\040vista ntfs-3g defaults,locale=en_CA.UTF-8 0 0
# Original setting
/dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0


** dmesg | grep -i CD-ROM**


[    3.422141] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530B  NX02 PQ: 0 ANSI: 5
[    3.431185] Uniform CD-ROM driver Revision: 3.20
[    3.431253] sr 3:0:0:0: Attached scsi CD-ROM sr0

[B]
sudo lshw -c disk[/B]
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AD-7530B
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: NX02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: WDC WD5000BEVT-2
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WX20AB9D7162
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=b487b4e 

Now when I put in 

**ls -l /dev/sr0**

brw-rw----+ 1 root cdrom 11, 0 2010-01-30 09:30 /dev/sr0

I get that. Is it possible its just misnamed?

Please get back with me on this. I leave for business in two days and would love to be able to use my laptop, including watching movies.

Now to add insult to injury after repairing grub, I can no longer boot windows vista.

I get the following error:

\boot\bcd
0xc0000001

can anyone help? This is really getting on my nerves.
I have no working dvd drive on the computer, so I dont even have the option of doing the start up repair.

---

