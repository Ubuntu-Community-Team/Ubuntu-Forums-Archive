---
title: "[SOLVED] error mounting swap"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by apfergus on 2008-08-12
Some time ago my laptop running Hardy Heron decided it was going to force me to run a manual fsck when I turned it on one morning. I begrudgingly did this in the hopes I could avoid losing all my data. My system now works perfectly fine with one tiny exception: 

When booting up, it will fail to mount my swap partition. It will then sit there for about ten minutes and proceed to boot up normally. So far this has been more annoying than anything else, and most of the time I put it into hibernate mode, anyway, but if someone has a suggestion for fixing it I'd love to have my speedy boot time back.

---

### Post by Elfy on 2008-08-12
You could check first that it is correct in fstab, can you run these in terminal and post the output please

```
sudo blkid
cat /etc/fstab
```

---

### Post by apfergus on 2008-08-12
Output from blkid:
[INDENT]/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-040E" TYPE="vfat" 
/dev/sda3: UUID="eb3b1336-4a88-4146-bbcb-c391e234b6c7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="bba28805-31e2-4d73-96ec-3ea9c2c945e1" 
/dev/sda2: LABEL="OS" UUID="2BC7-A280" TYPE="vfat"[/INDENT]

Contents of fstab:
[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
#UUID=eb3b1336-4a88-4146-bbcb-c391e234b6c7 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3   none   swap   sw   0   0
# /dev/sda5
UUID=bba28805-31e2-4d73-96ec-3ea9c2c945e1 none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0[/INDENT]

---

### Post by Elfy on 2008-08-12
You seem to have sda3 trying to be swap as well as the real swap. Is sda3 mounted at all and do you know whta it should be ?

Can you do 

```
mount
sudo fdisk -l
```

It appears that it used to be /

---

### Post by apfergus on 2008-08-12
Output from mount:
[INDENT]proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
[/INDENT]

Output from fdisk -l:
[INDENT]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11         663     5245222+   b  W95 FAT32
/dev/sda3   *         664       19083   147958650   83  Linux
/dev/sda4           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris
[/INDENT]

---

### Post by bumanie on 2008-08-12
Once booted, in terminal try > swapon /dev/<partition name> [eg, /dev/sda3 or whatever your swap partition designation is]Swap should load on the next boot OK. Not sure if 'swapon..' has to be run as root or not.

---

### Post by Elfy on 2008-08-12
That all looks a bit odd to me - / isn't mounted, sda3 looks like it used to be / and sda5 should be swap.

I think that the fstab should be like

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=eb3b1336-4a88-4146-bbcb-c391e234b6c7 / ext3 defaults,errors=remount-ro 0 1

# /dev/sda5
UUID=bba28805-31e2-4d73-96ec-3ea9c2c945e1 none swap sw 0 0

/dev/sda2 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0

afaik - sudo swapon

---

### Post by bumanie on 2008-08-12
> **forestpixie said:**
> That all looks a bit odd to me - / isn't mounted, sda3 looks like it used to be / and sda5 should be swap.

I think that the fstab should be like



afaik - sudo swapon

Yeah it is sda5, sorry I didn't look  at the output of fdisk -l, I just put sda3 as an example. Having now read fdsik -l it is clearly  swapon /dev/sda5

---

### Post by bumanie on 2008-08-12
> **forestpixie said:**
> That all looks a bit odd to me - / isn't mounted, sda3 looks like it used to be / and sda5 should be swap.

I think that the fstab should be like



afaik - sudo swapon

Yeah it is sda5, sorry I didn't look  at the output of fdisk -l, I just put sda3 as an example. Having now read fdsik -l it is clearly  > swapon /dev/sda5

---

### Post by Elfy on 2008-08-12
Still like to know how it is running when mount doesn't appear to show / :confused:

Unless someone says differently I would open the file to edit and make it look so

```
gksudo gedit /etc/fstab
```

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=eb3b1336-4a88-4146-bbcb-c391e234b6c7 / ext3 defaults,errors=remount-ro 0 1

# /dev/sda5
UUID=bba28805-31e2-4d73-96ec-3ea9c2c945e1 none swap sw 0 0

/dev/sda2 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0

---

### Post by apfergus on 2008-08-12
So I modified fstab to reflect your suggestions and this has cleared up the errors on boot-up regarding failure to mount swap (so thanks for that!). The ten minute pause still persists, however, and in the massive wall of text that appears afterwards there is one line of red text saying that there was a failure to clean /tmp.

---

### Post by Elfy on 2008-08-12
Is swap on now - ```
top
```

I'm not sure whether the /tmp gets completely emptied on close, so would be a bit dubious about saying clear it, but that would appear to be the problem if it is the only fail on boot - I assume at the right there is a [COLOR="Red"][fail][/COLOR]

---

### Post by Elfy on 2008-08-12
Ok I checked, it is empty - reboot and enter recovery mode from grub, you'll get a small menu - go to root prompt

```
cd /tmp
```

check that it is empty, if not

```
rm -R /tmp/*
```

---

### Post by apfergus on 2008-08-12
Hmm. It's not a [fail] line, it seems, but a line that says:
[INDENT] * bootclean: Failure cleaning /tmp. [/INDENT]
Failure to clean the /tmp directory doesn't sound like sufficient cause for a very long hang up during boot, so I suspect there might be a greater problem lurking somewhere in the shadows, but there are no other obvious complains printed to the screen.

And the result of top does seem to indicate that swap is mounted and working:
[INDENT]Swap:  3004112k total,        0k used,  3004112k free,   334808k cached[/INDENT]

---

### Post by Elfy on 2008-08-12
> Failure to clean the /tmp directory doesn't sound like sufficient cause for a very long hang up during bootdepends how long it tries for I assume :) - but if there is nothing else that shows as an obvious error - you could either watch and see where it appears to slow down and note that/them.

Can you make sure that / is mounting properly now with ```
mount
```

Maybe install bootchart - then have a look at that, also of course you could check the system logs - sys>admin menu.


Edi t- if you do install bootchart - they go in /var/log/bootchart

---

### Post by apfergus on 2008-08-12
The current output from mount is thus:
[INDENT]/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
[/INDENT]

The contents of /tmp which are un-clearable seem to all be in a folder called /tmp/apfergus-orbit/ and they cannot even be removed when logged in as root from the recovery console. 

I'll probably have to give my efforts a rest here for a while and get back to work, unfortunately. *grumble*

---

### Post by Elfy on 2008-08-12
*grumble* away - might have to force the file removal then, everyting seems to be mounting ok again.

Have you tried running nautilus as root, to see in there.

```
gksudo nautilus
```

Think it's ```
rm -rf /tmp/*
``` but I would check the command just to make sure.

---

### Post by apfergus on 2008-08-20
Running Nautilus as root worked in the end for deleting the contents of tmp and now my startup time is as fast as it's ever been. Thanks for the help!

---

### Post by Odaym on 2011-01-14
I had the same problem.. "An error occured while mounting swap", S to skip mounting, M to manual recovery
 
I tried doing as you instructed apfergus but it didnt work, any help will be really appreciated, i am in dire need for it to work of course, thank you in advance

---

### Post by Odaym on 2011-01-14
also i'm not being able to edit my /etc/fstab, although im logged in as root, but it tells me that cannot write changes to /etc/fstab [ error writing /etc/fstab: read-only file system] ??

---

### Post by Linyx on 2011-01-14
> **Odaym said:**
> also i'm not being able to edit my /etc/fstab, although im logged in as root, but it tells me that cannot write changes to /etc/fstab [ error writing /etc/fstab: read-only file system] ??

Better to make your own thread ..because this is marked as Solved Already, 
Any way post the Output of...

```
sudo blkid
```Also

```
cat /etc/fstab
```And you can't edit the Fstab as your are a normal user, Although you can edit it when you open something as a Root, i-e, you can edit fstab when you open it in this way

```
sudo gedit /etc/fstab
```

---

