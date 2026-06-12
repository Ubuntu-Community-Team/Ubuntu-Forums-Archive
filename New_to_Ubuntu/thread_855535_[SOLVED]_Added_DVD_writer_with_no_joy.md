---
title: "[SOLVED] Added DVD writer with no joy"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by nuddernuby on 2008-07-10
I'm afraid this might be very basic.  

Have added a DVD writer to my 8.04 box.  Followed reassuringlyioffensive's Comprehensive Multimedia and Video How To  ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)), downloaded and installed all the files he recommended, followed all suggestions, but with no joy whatsoever.

Music CD's play distorted garbage, DVD's trigger no response whatsoever.  

The previously installed CD-ROM works perfectly.  Clearly, I have failed dismally with the basic installation/configuration of the hardware.

~$ dmesg | tail has the following output:

> 

[ 7278.973221] sr 1:0:1:0: [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 7278.973229] end_request: I/O error, dev sr1, sector 64
[ 7279.010232] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 7279.010245] sr 1:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 7279.010251] sr 1:0:1:0: [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 7279.010258] end_request: I/O error, dev sr1, sector 64
[ 7279.047305] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 7279.047317] sr 1:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 7279.047323] sr 1:0:1:0: [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 7279.047330] end_request: I/O error, dev sr1, sector 64



Could anybody kindly advise where I should start to solve this?

---

### Post by LowSky on 2008-07-10
Ah I had the same problem. It was cause by using the wrong type of IDE cable. Everything was fixed by using one that can support ATA133 

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Description=IDE+Cable](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Description=IDE+Cable)

Don't worry about it This issue plauged me for weeks, until I just got angry and took everything apart and switch from master to slave to cable select, to trying the analog audio cab;e, to removing a TV tuner card and then used a different cable and some how all got restored

---

### Post by nuddernuby on 2008-07-10
Thanks, LowSky, I'll go hunting and gathering for a different cable. Thought it might be something basic.
](*,)

---

### Post by mc4man on 2008-07-10
You probably should be using an 80 wire cable as mentioned (easy to tell from 40 wire, the 80 is almost smooth, the 40 you can see the individual wires)
You may also want to post the contents of /etc/udev/rules.d/70-persistent-cd.rules, it's possible it could use some attention.

---

### Post by nuddernuby on 2008-07-11
Thank you for your advice re the cable. The new cable is installed and it now plays music CD's.  

I guess the DVD (re-)setup now needs to be addressed.  Here is the complete content of /etc/udev/rules.d/70-persistent-cd.rules

```

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# TSSTcorp_CD-ROM_SH-C522C (pci-0000:00:11.1-ide-1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-ide-1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
# CD-ROM_SH-C522C (pci-0000:00:11.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
# Cruzer (pci-0000:00:10.3-usb-0:6:1.0-scsi-0:0:0:1)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="SanDisk_Cruzer_0774500A5A83246A-0:1", SYMLINK+="cdrom2", ENV{GENERATED}="1"
# Cruzer (pci-0000:00:10.3-usb-0:6:1.0-scsi-0:0:0:1)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:10.3-usb-0:6:1.0-scsi-0:0:0:1", SYMLINK+="cdrom3", ENV{GENERATED}="1"
# CDDVDW_SH-S202N (pci-0000:00:11.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:1:0", SYMLINK+="cdrom4", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:1:0", SYMLINK+="cdrw4", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:1:0", SYMLINK+="dvd4", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:1:0", SYMLINK+="dvdrw4", ENV{GENERATED}="1"


``` 

If I try gxine's health check it reports that it cannot find /dev/dvd.

Only the following can be found: /dev/dvd4 and /dev/dvdrw4 

I guess some serious reconfiguration is still required. Your advice is appreciated.

---

### Post by mc4man on 2008-07-11
Basically this is what your going to do, though you m_ay want to post your fstab first_. While fstab and the symlinks in /dev play a part, the .rules file controls your device name and links.
You may want to read here for more info in a similar though not an exact situation (in your case better to start fresh as far as ....rules file)
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)

Open this file as root
```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
``` and delete everything below what's shown, ie. your file should look like below when your done.
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
``` Then save and exit
This part is optional i believe but is good housekeeping. (from link above)
Run gksudo nautilus and navigate in filesystem to /dev. Inside you'll see links (look like files with an arrow) Delete all of the following you find (what you need will be rewritten when you reboot)
cdrom, cdrom1, dvd, dvd1, cdrw, cdrw1, dvdrw, dvdrw1, sr0, sr1 (sr0,sr1 are far down the page) (In your case the #'s will go higher, ie. up to dvd4, cdrom4, ect.)
Only delete links ! Not scd0 
After that, with _no usb flash drives inserted_, reboot, and your drive should be /dev/scd0, /dev/dvd, dev/cdrom, ect.
Post that fstab and if unclear ask first, basically this is quite easy to do.

edit: don't worry about what's being deleted, what you need will be created upon reboot. The 'flow' is this - 
75-persistent-cd-generator.rules will make a new entry in /70-persistent-cd.rules which will then create new symlinks in /dev. The only thing that will need some manual help is fstab.

---

### Post by nuddernuby on 2008-07-11
So, before I start the modifications, here is what fstab looks like:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/p--desktop-root
UUID=88b36c17-ac8e-49e0-92c9-aaab1caa8bef /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=8bfc7714-fc4b-4ad2-b521-02ef5f6c3bca /boot           ext3    defaults        0       2
# /dev/mapper/p--desktop-swap_1
UUID=13e854a7-b356-4111-9cab-978d545d2059 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/ndas-08014240-0p1 /media/Trekstor vfat defaults,user,noauto 0 0



```

Thank you for your assistance.

---

### Post by mc4man on 2008-07-11
Your going to change that line in fstab to 
> /dev/scd0        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
You can do it now or later.
Anything your unclear on?

The scd0 will depend on what rules does, should be ok. 
After all is done run
```
sudo lshw -C disk
``` to double ck. logical names

---

### Post by nuddernuby on 2008-07-11
Have completed your first set of instructions.
**70-persistent-cd.rules**  now looks like this:

```


# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.

# CDDVDW_SH-S202N (pci-0000:00:11.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# CD-ROM_SH-C522C (pci-0000:00:11.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"

```

Does this affect the proposed change to fstab?

---

### Post by mc4man on 2008-07-11
run the sudo lshw.... and we'll see
edit:
gotta go, would like to see lshw... but 
i'm thinking your fstab should look like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/p--desktop-root
UUID=88b36c17-ac8e-49e0-92c9-aaab1caa8bef /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=8bfc7714-fc4b-4ad2-b521-02ef5f6c3bca /boot           ext3    defaults        0       2
# /dev/mapper/p--desktop-swap_1
UUID=13e854a7-b356-4111-9cab-978d545d2059 none            swap    sw              0       0
/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/ndas-08014240-0p1 /media/Trekstor vfat defaults,user,noauto 0 0
```

---

### Post by nuddernuby on 2008-07-11
The output from
```

sudo lshw -C disk

```

is as follows:

```

 *-disk                  
       description: ATA Disk
       product: Maxtor 6Y080L0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: YAR4
       serial: Y2EKA3AE
       size: 76GiB (81GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00073aee
  *-cdrom:0
       description: SCSI CD-ROM
       product: CD-ROM  SH-C522C
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TS01
       capabilities: removable audio
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
  *-cdrom:1
       description: DVD-RAM writer
       product: CDDVDW SH-S202N
       vendor: TSSTcorp
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/HIGH_SCHOOL_MUSICAL_2
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/HIGH_SCHOOL_MUSICAL_2
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted


```

As you can see, I'm using High School Musical as a test - no joy as yet, though.

Edit: Have rebooted. When inserting DVD error message says it cannot mount the volume as mount point /media/cdrom1 does not exist. Does this provide a clue?

---

### Post by mc4man on 2008-07-11
Have a few more min. 
Do something before editing fstab
The disk you mentioned is mounted, go to the icon on desktop or places -> computer and r. click on the icon or drive -> properties -> volume and see what the mountpoint is. (For High School Musical)
Edit missed your edit , confirm the dvd drive tries to mount at /media/cdrom1 and we'll be good to go w/ editing fstab

---

### Post by nuddernuby on 2008-07-11
Mount point is:  /media/HIGH_SCHOOL_MUSICAL

---

### Post by mc4man on 2008-07-11
Did you edit the fstab as in prior post?
If not go ahead and do so
Also ck. in /media and see if there are 2 folders, cdrom0 and cdrom1
If so remove the disk and reboot, if not let me know

---

### Post by nuddernuby on 2008-07-11
Tried fstab both with and without your proposed edit.

/media has cdrom (link) and cdrom0 - but no cdrom1 (which totem is looking for)

:confused:

---

### Post by mc4man on 2008-07-11
go ```
cd /media; sudo mkdir cdrom1
```
and leave the fstab as was edited (with the 2 lines /dev/scd0 , /dev/scd1)
remove disk reboot ect.

---

### Post by nuddernuby on 2008-07-11
We're making progress.  Got it working with:

gxine  - all OK
vlc    - partial graphics, no sound
totem  - nothing - "could not read from resource"

I need to run. Will continue tomorrow.
Thank you for your patience.

---

### Post by mc4man on 2008-07-11
I got to go too. here's an edit I was typing, though now it may be a matter of getting vlc and totem squared away, most likely unrelated to what we just did.
here's edit anyway
Your cdrom drive is /dev/scd0 and will mount at /media/cdrom0 with a symlink of /dev/cdrom1
Your dvd drive is /dev/scd1 and will mount at /media/cdrom1 with links of /dev/dvd, /dev/cdrom, and a few others.

This is a little more complicated than it could be because you have the cdrom drive on the end connector of your ide cable and your dvdrw drive on the middle connector. The drive on the end connector is 'mastered' over the middle one, (will be the optical drive you can boot off of in your bios)

The 'mastered' drive will always get /dev/scd0, the next drive /dev/scd1. The 'normal' is for the scd0 device to mount at /media/cdrom0, and the scd1 device to mount at /media/cdrom1, though you could change that in fstab if you wanted.

For performance it's generally better to have your dvdrw drive on the end connector and the cdrom drive on the middle one. In that case your dvd drive would have been /dev/scd0, mounting at /media/cdrom0  (and possibly would need to be set as the boot optical drive in your bios)
And forget totem-gstreamer, we'll set you up with totem-xine (much better for everything)

---

### Post by nuddernuby on 2008-07-12
Right, new day - new solutions.
Have reconfigured according to your recommendations. DVD now mastered at end of cable. VLC and gxine work perfectly for DVD playback and installing programmes. Totem still shaky. Should I just uninstall totem?

I'll tackle the next chapter, now: Sorting small hiccups in Sun xVM Virtualbox.

You have been very good at this, mc4man, and patient. Tx.

---

### Post by mc4man on 2008-07-12
As far as totem ck. this post, you could run code box 3 to cover your bases as far as codecs, the totem-xine info is right below.
If there are sound issues with totem (any version) go system -> preferences -> sound and from the drop down for movies and music change from autodetect to something specific, usually alsa.
Gotta go give some estimates, will ck. back later if any issues arise. 
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

Edit : a thanks to you for reading the posts completely and not freaking out over little bumps in the road. I'm fairly confident you see the logic to all this and the relationships between the ...rules file, fstab, and mount points ect.

---

