---
title: "Unable to mount dc and dvd drives"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by wawadave on 2008-11-04
First i tried to use dvd drive since upgradeing to intrepid.
may or may not be reliven.
did search found where someone wanted fdisk info
bud@bud-desktop:~$ sudo fdisk -l /dev/scd1
[sudo] password for bud: 
Note: sector size is 2048 (not 512)

Disk /dev/scd1: 6836 MB, 6836322304 bytes
255 heads, 63 sectors/track, 207 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x00000000

Disk /dev/scd1 doesn't contain a valid partition table
bud@bud-desktop:~$ 

you put didk in drive the light flashes on and off systems reading the dvd.
you can eject it from menu but door opens then closes quickly.

cd drive does not mount ether

bud@bud-desktop:~$ dmesg | grep hdc scd 1
grep: scd: No such file or directory
grep: 1: No such file or directory


bud@bud-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1095de66-3b05-49ea-83bb-86a1e4b2f1af /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=529bc0d6-8b4c-466b-9134-9d583aee96ec none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by wawadave on 2008-11-04
just tried this:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

bud@bud-desktop:~$ wget [http://media.ubuntu-nl.org/scripts/diskmounter](http://media.ubuntu-nl.org/scripts/diskmounter)
--2008-11-04 09:40:40--  [http://media.ubuntu-nl.org/scripts/diskmounter](http://media.ubuntu-nl.org/scripts/diskmounter)
Resolving media.ubuntu-nl.org... 81.171.100.21
Connecting to media.ubuntu-nl.org|81.171.100.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4864 (4.8K) [text/plain]
Saving to: `diskmounter'

100%[======================================>] 4,864       27.9K/s   in 0.2s    

2008-11-04 09:40:40 (27.9 KB/s) - `diskmounter' saved [4864/4864]

bud@bud-desktop:~$ sudo bash diskmounter
[sudo] password for dg: 
By default the disks will be writable only by root and
bud (bud)
Do you want to make the disk writable by all users instead? (y/n)
y
As of Ubuntu 6.04 (Dapper Drake) there is slightly more NTFS writing support
through a very experimental NTFS FUSE module. Using this seems to work but
is NOT recommended. Do you want to use this? [no] n
Not enabling experimental NTFS write support
Added /dev/sdb5 as '/media/sdb5'
Added /dev/sdb6 as '/media/sdb6'
Added /dev/sdb7 as '/media/sdb7'
Added /dev/sdb8 as '/media/sdb8'
NTFS drives will be mounted read-only!
Added /dev/sdb1 as '/media/sdb1'
fuse: mount failed: Device or resource busy
All windows and mac partitions will now be mounted every time you boot
You do not need to reboot, the partitions are mounted now too
bud@bud-desktop:~$

---

### Post by wawadave on 2008-11-04
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Playback failure:
DVDRead could not open the disk "/dev/scd1".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/scd1'. Check the log for details.

still not able to mount drive.

this is starting to suck.

---

### Post by wawadave on 2008-11-04
bud@bud-desktop:~$ sudo bash diskmounter
By default the disks will be writable only by root and
bud (bud)
Do you want to make the disk writable by all users instead? (y/n)
y
As of Ubuntu 6.04 (Dapper Drake) there is slightly more NTFS writing support
through a very experimental NTFS FUSE module. Using this seems to work but
is NOT recommended. Do you want to use this? [no] y
Not enabling experimental NTFS write support
Ignoring /dev/sdb5 - already in /etc/fstab
Ignoring /dev/sdb6 - already in /etc/fstab
Ignoring /dev/sdb7 - already in /etc/fstab
Ignoring /dev/sdb8 - already in /etc/fstab
Ignoring /dev/sdb1 - already in /etc/fstab
No usable windows/mac partitions found
bud@bud-desktop:~$ 

This is getting to hammer fxcking time!! thats where you fix this by takeing a hammer to the hard drive.

tried to rerun script and choose write suport and now it cannot do that ether.
**** **** ****

---

### Post by bumanie on 2008-11-04
Have you installed multi-media codecs? Go to [medibuntu site]("https://help.ubuntu.com/community/Medibuntu") and follow the directions. You have 2 cd/dvd drives enetered in fstab.

---

### Post by Ecclesia on 2008-11-04
Hi, I am having this same problem.  My DVD drive will open when the eject button is pressed and then close immediately. It is open just long enough to throw a disk in, but it will not read it.

I have installed the mediabuntu library and codecs. Unfortunately, I'm not sure whether the drive worked before installing them, as I didn't try it out.

This drive worked fine under 7.10 (which I just wiped out to do a fresh install of 8.10).

Any suggestions?

---

### Post by wawadave on 2008-11-04
its not the codecs its the drives won,t mount period. i have codecs unless upgradeing to intrepid removed them.

but it won,t open any cd dvd because it won,t mount.

i have now removed the drive all but home partition and rebooted with out them. seems systems still seeing them with

-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1095de66-3b05-49ea-83bb-86a1e4b2f1af /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=529bc0d6-8b4c-466b-9134-9d583aee96ec none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#Added by diskmounter utility
/dev/sdb5 /media/sdb5 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb6 /media/sdb6 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb7 /media/sdb7 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb8 /media/sdb8 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 vfat rw,user,fmask=0111,dmask=0000 0 0
bud@bud-desktop:~$ 

so i need to remove these some how
doing a search for dev but most likely to be locked to me.

this really sucks.

---

### Post by wawadave on 2008-11-04
> **bumanie said:**
> Have you installed multi-media codecs? Go to [medibuntu site]("https://help.ubuntu.com/community/Medibuntu") and follow the directions. You have 2 cd/dvd drives enetered in fstab.
yes because i have two drives one a cd drive
one a dvd drive
both worked before upgrade to intrepid.

 any way to down grade from intrepid?

---

### Post by wawadave on 2008-11-04
so it looks like i,m just plain screwed

---

### Post by bumanie on 2008-11-04
You can't downgrade - it is unfortunate, but upgrades, when done via the update manager do not always work properly (I always do a fresh install). If I recall correctly, there is a warning that upgrading may break your system. May be that is what happened. If it is a new install - I have no idea why your optical drive/s won't work.

---

### Post by wawadave on 2008-11-04
well i physically disconected the drives rebooted with out then tried all things i could only working computer i had with a burner was this one only cd i got that will install is 5.10 really really sucks sucks sucks sucks.
just when its going good then you get gucked 
and no help. well i guess this the gucking i get for the gucking i got.

---

### Post by sisco311 on 2008-11-04
connect your cd/dvd drives and post the output of:
```
lshw -C disk
```

---

### Post by wawadave on 2008-11-05
*-disk:0                
       description: ATA Disk
       product: Maxtor 4D040H2
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: DAH0
       serial: D216W2FE
       size: 38GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000beefb
  *-disk:1
       description: ATA Disk
       product: Maxtor 6L250R0
       vendor: Maxtor
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: BAJ4
       serial: L61PG04H
       size: 233GiB (251GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=7efc3cf7
  *-cdrom:0
       description: CD-R/CD-RW writer
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/cdrw2
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw
       configuration: status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: DVD RW DRU-830A
       vendor: SONY
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom3
       logical name: /dev/dvd3
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: SS25
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom3

---

### Post by bradfallon83 on 2008-11-05
Looking to Hire a Janitorial Cleaning Company? Here are few tips.

Many business owners/managers hire a janitorial cleaning company to take care of all their 

cleaning needs. One of the
challenges is there are so many companies to choose from.

For all your janitorial & cleaning needs choose a janitorial or cleaning company that have 

professional cleaning technicians
who are trained in earth-friendly practices and the use of advanced eco-friendly products 

and equipment & use Green
Certified Techniques and Products

Universal Building Maintenance Inc.provide excellent environmentally friendly janitorial 

service at a competitive price.They
have over 20 years experience in providing janitorial services. They use non-toxic products 

and eco-friendly equipment to
ensure a clean, healthy, and safe environment.Universal Building Maintenance Inc. has been 

able to continually simplify
office cleaning and janitorial services.  

Avail janitorial services (link to [http://ubmaintenance.com/](http://ubmaintenance.com/)) & commercial cleaning 

services([http://ubmaintenance.com/services.html](http://ubmaintenance.com/services.html)) from Universal Building Maintenance Inc. & 

Get $100 Gift Certificate

---

### Post by sisco311 on 2008-11-05
> **wawadave said:**
> 
  *-cdrom:0
       description: CD-R/CD-RW writer
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/cdrw2
       logical name: **/dev/scd0**
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw
       configuration: status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: DVD RW DRU-830A
       vendor: SONY
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom3
       logical name: /dev/dvd3
       logical name: **/dev/scd1**
       logical name: /dev/sr1
       version: SS25
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom3

replace:
> /dev/hdd /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
with
> **/dev/scd0** /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
**/dev/scd1** /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
in the fstab

---

### Post by wawadave on 2008-11-05
Thank you very much for your answer!!

But i have no idea how to find this fstab

and if i do i most likely won,t have permmision to change any thing.

ok did search for fstab and could not save any i changed.

---

### Post by sisco311 on 2008-11-05
type(or copy/past):
```
gksu gedit /etc/fstab
```in a terminal to open the file with the text editor as root.

---

### Post by wawadave on 2008-11-05
ok since i could not change those files.

i went into system/administration 
and set every thing in mount etc to yes.
it can read a cd to copy it but won,t dysplay contents
and i got the unable to mount error again on makeing copy time to write part of cd.  so setting all to yes did nothing. will set all other things in admin to yes and see what happens.

i don,t really care any more about this system as i backed up every thing over network and am out to reinstall though fixing would be nice or knowing how till the next time i get screwed with this.

---

### Post by wawadave on 2008-11-05
> **sisco311 said:**
> type(or copy/past):
```
gksu gedit /etc/fstab
```in a terminal to open the file with the text editor as root.

i can change the lines in there does it save it to the text file?

---

### Post by sisco311 on 2008-11-05
> **wawadave said:**
> i can change the lines in there does it save it to the text file?

yes. press Ctrl+s to save the file and Alt+F4 to quit or use the File menu Save... and Quit options. 

type:
```
cat /etc/fstab
```in the terminal to print the content of the file.

---

### Post by wawadave on 2008-11-05
Thank you thank you thank you!!!!!!!

It works now!!!

Now if i can get write permissions back on all the hard drives that i changed running a script earlier they are now all read only!!!

---

### Post by sisco311 on 2008-11-05
ok

post the output of:
```
sudo blkid
```
and
```
cat /etc/fstab
```

---

### Post by wawadave on 2008-11-05
I removed the "RO" from each of the hard drives in fstab an saved then rebooted all is nearly ok but good enought to continue useing this computer again!!
thank you to all who helped!!

---

### Post by wawadave on 2008-11-05
/dev/sda1: UUID="1095de66-3b05-49ea-83bb-86a1e4b2f1af" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="529bc0d6-8b4c-466b-9134-9d583aee96ec" 
/dev/sdb1: LABEL="NEW VOLUME" UUID="929C-6CEC" TYPE="vfat" 
/dev/sdb5: UUID="66936B34235B2BDD" TYPE="ntfs" 
/dev/sdb6: UUID="761A2D2B1A2CE9B7" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb7: UUID="FA0E44970E444EB7" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb8: UUID="F8365BB5365B739A" LABEL="New Volume" TYPE="ntfs" 


cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1095de66-3b05-49ea-83bb-86a1e4b2f1af /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=529bc0d6-8b4c-466b-9134-9d583aee96ec none            swap    sw              0       0
/dev/scd0        /media/cdrom0   udf,iso9660 user,exec 0       0
/dev/scd1        /media/cdrom1   udf,iso9660 user,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#Added by diskmounter utility
/dev/sdb5 /media/sdb5 ntfs user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb6 /media/sdb6 ntfs user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb7 /media/sdb7 ntfs user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb8 /media/sdb8 ntfs user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 vfat rw,user,fmask=0111,dmask=0000 0 0

tried to open cd fron places removeable media and got this error.

unable to scan cd-rw/dvd +- drive for media changes
cannot evoke check for media on HAL:
org.freedesktop.dbus. error
no reply did not get a repply posible cause include the remote app did not send a repply. the message bus security blocked the repply ploicy blocked the repply the repply timed out over network network conection broken.

so i cannot see it in media ether

and when atempting to see burned dvd from mefia i got above error with this error

mount block device/dev/scd1/:cannot read super block
tring bought music cd now

---

### Post by wawadave on 2008-11-05
ok store bought music cd says unable to mount does not contain music files.

something is terribly wrong with this system.

its been closeing cd dvd draws as soon as you click to open and if you do it again they will stay open till closed. 

a reinstall looks like only way out of this.

i remember 7-8 years ago useing windows and too many simple things would force me to reformat and start again.then i learned lots more and never had to again. i,m in that same newby stage once again.

the hard drive permissions are ok !

---

### Post by sisco311 on 2008-11-05
backup the fstab:
```
sudo cp /etc/fstab /etc/fstab-backup
```

edit the file:
```
gksu gedit /etc/fstab
```

and replace the whole content with:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=1095de66-3b05-49ea-83bb-86a1e4b2f1af / ext3 defaults,errors=remount-ro,relatime 0 1
# /dev/hda5
UUID=529bc0d6-8b4c-466b-9134-9d583aee96ec none swap sw 0 0
#cdrom
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
#floppy
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
#windows
UUID=929C-6CEC /media/sdb1 vfat defaults,umask=007,gid=46 0 0
UUID=66936B34235B2BDD /media/sdb5 ntfs defaults,umask=007,gid=46 0 0
UUID=761A2D2B1A2CE9B7 /media/sdb6 ntfs defaults,umask=007,gid=46 0 0
UUID=FA0E44970E444EB7 /media/sdb7 ntfs defaults,umask=007,gid=46 0 0
UUID=F8365BB5365B739A /media/sdb8 ntfs defaults,umask=007,gid=46 0 0

then reboot.

bug:[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316")

---

### Post by wawadave on 2008-11-06
thank you going to give this a try now!!

---

### Post by wawadave on 2008-11-06
ok that did not work still won,t mount dvd drive did not bother checking the others just going to reinstall and not ever do any important work on linux.

Thank you very much for your time and effort you kindness is appreciated!

---

### Post by Ecclesia on 2008-11-06
I found the answer to the quickly opening/closing drive here:

[http://ubuntuforums.org/showthread.php?t=969761](http://ubuntuforums.org/showthread.php?t=969761)

Go to System->Software Sources->Updates
Click on "Pre-released" (proposed) updates.
Run the update manager and update udev.

This should solve the problem.

I'm not sure why this release of Ubuntu has had so many little, yet major, issues.  This was not my experience with 7.10, and I've had lots of great luck with Debian.  I wouldn't generalize your experience on Ubuntu to Linux in general.  Certainly your install/reinstall experience is not the usual. There are other distributions that seem to be more solid and tested.  As-is, I'm not sure I'll be sticking with Ubuntu, although I do like many of the features.  If I keep having issues I'll switch back to Debian or maybe make the switch to another (I've heard good things about Mandriva lately).

Hope you get things sorted out.

---

### Post by wawadave on 2008-11-08
thx for your repply i finaly finished reinstalling and updateing and reistalling software. took a few days. all the problems are gone.
 so it must have been the upgrade to 8.10

i started this install from fisty -to gustsy beta to 8.04l all was well after all that but 8.10 screwed it over good.

i used mandrake 8. long ago i guess its come a long ways might give mandrivia a go.

---

