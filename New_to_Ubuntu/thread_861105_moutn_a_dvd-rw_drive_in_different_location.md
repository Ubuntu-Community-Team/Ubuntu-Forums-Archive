---
title: "moutn a dvd-rw drive in different location"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by rockinlinux on 2008-07-16
HEllo,

I installed a new dvd-rw drive and its not mouning in the correct place. My boz is set up with a / partition, /home partition and a 300GB partition mounted in /media named "storage". the dvd drive is mounted in /media/storage. I looked at my fstab and the dvd drive is not listed in the file. how can i get the dirve to be mounted in /media ??

Thanks for the help! have a great day!!

---

### Post by sisco311 on 2008-07-16
use:
```
lshw -C disk
```to find the device name.
You should get a listing, containing something like this:
>  *-cdrom                 
       description: DVD-RAM writer
       product: DRW-1608P3S
       vendor: ASUS
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       l[I]ogical name: /dev/cdrom
       logical name: /dev/dvd
       **logical name: /dev/scd0**
       logical name: /dev/sr0
       logical name: /media/cdrom0[/I]
       version: 1.19
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=readyAdd the device to the fstab:
> /dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0Make sure the mount point(/media/cdrom) exist.

---

### Post by unutbu on 2008-07-16
Please post 
```

cat /etc/fstab
ls -l /dev/dvd
sudo fdisk -l
mount
```

Are you really sure you want to mount the dvd at /media? This is not kosher and will probably break HAL... Would /dvd be ok? or /media/dvd?

---

### Post by sisco311 on 2008-07-16
> **unutbu said:**
> Please post 
```

cat /etc/fstab
ls -l /dev/dvd
sudo fdisk -l
mount
```Are you really sure you want to mount the dvd at /media? This is not kosher and will probably break HAL... Would /dvd be ok? or /media/dvd?

the sudo fdisk -l will not list the cdrom(dvd).

OP:make sure the dvd is mounted when you execute the mount command.

---

### Post by unutbu on 2008-07-16
I didn't quite understand what the OP was saying about a 300GB partition mounted "in /media named storage".
I wanted to find out if the 300GB partition was mounted at /media/storage, or if the dvd was there. 
The fdisk and mount commands might be overkill, but it would give us a better understanding of what's going on.

---

### Post by rockinlinux on 2008-07-16
the 300 GB parition is mounted via Fstab in /media/storage

The dvd drive is mounted right now in /media/storage/dvd-drive is here

see below:

root@home-desktop:/home/home# lshw -C disk
  *-disk                  
       description: SCSI Disk
       product: SAMSUNG HD501LJ
       vendor: ATA
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: CR10
       serial: S0MUJ1NP808516
       size: 465GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RW  DVR-215
       vendor: PIONEER
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/dvd2
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.13
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open


THANKS!!! :)

---

### Post by rockinlinux on 2008-07-16
guess at this point the question is why is it mounted here?  know i can add it to fstab...just want to know why its mounted here by default.

---

### Post by mc4man on 2008-07-16
run
```
 cat /etc/udev/rules.d/70-persistent-cd.rules
``` and you'll see why the /devs are high.
If you create an fstab as in post 2 you be ok

---

### Post by rockinlinux on 2008-07-16
Hello, thanks for everyones help.

Could someone try to explain this and what everything means? I have never seen this before and am very curious...or a link to a good explanation would also be great :)

btw i only have one dvd drive in this box...looks like it is listing 3?

root@home-desktop:/home/home# cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVD-RAM_GSA-H50N (pci-0000:00:1f.5-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# DVD-RAM_GSA-H50N (pci-0000:00:1f.2-scsi-0:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-0:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-0:0:1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-0:0:1:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-0:0:1:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
# DVD-RW_DVR-215 (pci-0000:00:1f.5-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-1:0:0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-1:0:0:0", SYMLINK+="cdrw2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-1:0:0:0", SYMLINK+="dvd2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-1:0:0:0", SYMLINK+="dvdrw2", ENV{GENERATED}="1"

---

### Post by mc4man on 2008-07-16
I have to get to work so can't hang out till tonight. basically an easy thing to fix and or understand. Here's some links
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)

A related situation - became more complex than needed (_post 6 is probably the way for you to address your situation_.)
[http://ubuntuforums.org/showthread.php?t=856818](http://ubuntuforums.org/showthread.php?t=856818)

The basic "flow" - ..75...rules on a boot will detect your optical drives(s) (including usb cd/dvd drives and some usb flash drives) and if it sees them/it as different (or non existent) then what's in ...70...rules it will generate a new entry but will leave previous entries. New entries are always 1 up from existing in terms of scdx and /dev links.
 Then ...70...rules will ck. in /dev for the device (scdx) and links, and create new ones or modify existing ones _if they are in conflict_ with it's entries.
  
Fstab simply ties a device (scdx) to a specific mount point with specific options.(you can use any mount point you want as long as it exists, typical is media/cdrom0 or media/cdrom1 
[http://ubuntuforums.org/showthread.php?t=857317](http://ubuntuforums.org/showthread.php?t=857317) and
[http://ubuntuforums.org/showthread.php?t=855535](http://ubuntuforums.org/showthread.php?t=855535)
 have some more info on this and overall
(note that both had 2 problems, the ...70...rules and an improper ide cable, one also needed some fstab work)

ck. out the links and post back if your confused or unclear

edit: why you have exact duplicate entries for the GSA-H50N is unclear but of no real importance

---

### Post by unutbu on 2008-07-16
This is just a wee minor thing, mc4man, but it may help if in [post #6]("http://ubuntuforums.org/showpost.php?p=5373814&postcount=6")  you mention that you'll need to reboot twice:

According to /usr/share/doc/udev/writing_udev_rules/index.html#builtin,
"Files in /etc/udev/rules.d/ are parsed in lexical order". The first time you reboot 
/etc/udev/rules.d/70-persistent-cd.rules will be empty and so /dev/dvd will be missing (so your DVD drive may not appear to work),
but /etc/udev/rules.d/75-cd-aliases-generator.rules will get parsed afterwards and re-populate 
70-persistent-cd.rules with good rules. The second time you reboot,
70-persistent-cd.rules will get parsed and /dev/dvd, et al should work correctly (provided the fstab is also updated).

---

### Post by mc4man on 2008-07-16
Looking at some stuff you posted a little more closely brings up a couple of questions. Did you run lshw -C disk or sudo lshw -C disk ? I'm fairly new to linux but I've never seen where running that without sudo will return info on a hdd, only info on 'removable' drives'. Do you log in as root all the time?

The other thing is when you ran it you said the dvd drive was mounted (@ /media//storage/dvd-drive, which is curious in itself) yet the results showed this > configuration: ansiversion=5 status=open which indicates no media in the drive. cd/dvd drives don't mount, only the filesystem on the inserted media do. Without an fstab entry for the drive the filesystem should default to /media/<volume name of disk>
I don't think you'll have in issue squaring this up , just thought I'd mention
You may benefit from from running the rest of the comm. unutbu requested to see if anything else 'odd' turns up
> 
This is just a wee minor thing, mc4man, but it may help if in post #6 you mention that you'll need to reboot twice:

You definitively don't have to boot twice, that's saying ..75..rules and ..70 ..rules can't do their tasks properly in one go which is not seen at least here irregardless of what that text says. If it takes 2 boots so be it, never seen it be needed. Test it out on your machine - delete all the entries in ...70...rules, delete your symlinks in /dev, reboot and I guarantee everything is reset in one boot (and be working)
As far as the other Op was concerned there's no discounting what one may do between a and b. He may have switched his drives and or their positions

---

### Post by rockinlinux on 2008-07-16
> **mc4man said:**
> Looking at some stuff you posted a little more closely brings up a couple of questions. Did you run lshw -C disk or sudo lshw -C disk ? I'm fairly new to linux but I've never seen where running that without sudo will return info on a hdd, only info on 'removable' drives'. Do you log in as root all the time?

The other thing is when you ran it you said the dvd drive was mounted (@ /media//storage/dvd-drive, which is curious in itself) yet the results showed this  which indicates no media in the drive. cd/dvd drives don't mount, only the filesystem on the inserted media do. Without an fstab entry for the drive the filesystem should default to /media/<volume name of disk>
I don't think you'll have in issue squaring this up , just thought I'd mention
You may benefit from from running the rest of the comm. unutbu requested to see if anything else 'odd' turns up

You definitively don't have to boot twice, that's saying ..75..rules and ..70 ..rules can't do their tasks properly in one go which is not seen at least here irregardless of what that text says. If it takes 2 boots so be it, never seen it be needed. Test it out on your machine - delete all the entries in ...70...rules, delete your symlinks in /dev, reboot and I guarantee everything is reset in one boot (and be working)
As far as the other Op was concerned there's no discounting what one may do between a and b. He may have switched his drives and or their positions

have not had time to read all or review but i always use sudo su...also when i ran the command there was no disk in the drive.

---

### Post by unutbu on 2008-07-16
Ah. You are right mc4man. /etc/udev/rules.d/75-cd-aliases-generator.rules
contains:

```
ACTION=="add", SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{GENERATED}!="?*", PROGRAM="write_cd_rules", SYMLINK+="%c"
```

The script /lib/udev/write_cd_rules not only writes 
to the file /etc/udev/rules.d/70-persistent-cd.rules,
it also echos
```

echo $SYMLINKS
```
which is sent to 

```
SYMLINK+="%c"
``` which generates the symlink. So 75...rules not only recreates 70...rules, it also can create the symlinks.

---

### Post by mc4man on 2008-07-16
> The script /lib/udev/write_cd_rules not only writes
to the file /etc/udev/rules.d/70-persistent-cd.rules,
it also echos ... ect,
That's good to know, alot of what's in scripts I don't get yet (if ever), so it's useful at least to know what's it's doing .

---

