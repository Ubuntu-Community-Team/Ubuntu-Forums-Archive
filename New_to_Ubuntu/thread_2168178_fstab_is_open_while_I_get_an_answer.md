---
title: "fstab is open while I get an answer"
date: 2013-08-16
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-08-16
Will this line work? Could it blow up the OS? Also, if I add automount to the line, will the OS try to mount it at boot time? And what if it isn't powered up? Can that harm the OS or fstab?

I apologize for posting and waiting for an answer, but there is way too much conflicting, incomplete or outdated information on the 'net. And I've been there for over 2 hours. Thank you for your time.

Using GParted, I formatted this external usb hard disk drive as ext4. I then made /media/[COLOR="#0000FF"]wd160[/COLOR]  -- a directory, in /media. Also /sde and /sde1 show up in /etc/dev 

# /dev/sde1
UUID=884bb7b0-5895-403f-b385-31820ad1c262       /dev/sde1       ext4    nodev,noauto,noexec,rw,         0 0

it is to mount, as user:user an external usb-connected hard disk drive.

mark@Lexington:/media$ blkid
/dev/sde1: UUID="884bb7b0-5895-403f-b385-31820ad1c262" TYPE="ext4" 

and


Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e3367

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048   312580095   156289024   83  Linux

---

### Post by SuperFreak on 2013-08-16
Can't comment on whether that will work although it looks quite different from entries in my fstab. However whether you keep it or not I would suggest you backup the original (working) Fstab. Doing that has saved me a lot of grief in the past


edit: You have the UUID and /dev/sde1 both in fstab. I would have thought you only needed the UUID. Wait for someone with more experience to help you

---

### Post by Werne on 2013-08-16
Usually, if it's plugged in, it will be automounted on boot. If it's not plugged in, during bootup it will offer you an option to press "S" in order to skip mounting that file system (since it's not present). You used "noauto" meaning it won't be automounted upon boot. However, your command is incorrect, fstab works like this:

```
<file system - UUID or /dev/sd*>           <mount point>           <file system type>           <mount options>           <dump>           <fsck, aka file system check>
```

Your fstab entry looks like so:

```
<file system>           <file system>            <file system type>           <mount options>            <dump>           <fsck>
```

You can make a directory somewhere you want to mount your hdd to, then make an entry like this:

```
UUID=884bb7b0-5895-403f-b385-31820ad1c262            /path/to/mount/directory            ext4         nodev,noauto,noexec,rw,user              0      2
```

The "user" option is there so any user can mount the file system, not only root. From "mount" manual page:

```
       The non-superuser mounts.
              Normally,  only the superuser can mount filesystems.  However, when fstab contains the user option on a line, anybody can mount the corresponding system.
```

---

### Post by Mark_in_Hollywood on 2013-08-16
is this "it" then?

# /dev/sde1
UUID=884bb7b0-5895-403f-b385-31820ad1c262       /media/sde1       ext4    nodev,noauto,noexec,rw,user     0 0

0 0 as I have /sda1 as / and /sda3 as /home and /sda5 as swap and fsck runs on / and then on /home and I want the external drive to not run fsck on boot up as it won't be powered up mostly. 

Come to think of it, I don't care if the device is owned by the / only, as all I want to do is as a user be able to place files on the device, read those files and delete them when they are no longer necessary.

---

### Post by Mark_in_Hollywood on 2013-08-16
I have commented out the line that controls the external hard drive for now. Please rest.

---

### Post by Mark_in_Hollywood on 2013-08-16
I did: sudo mkdir /mnt/wd160

sudo blkid

added the uuid to fstab, saved, sudo mount -a (I see no error messages)

line in fstab about this device (160gig hard disk drive)

# /mnt/wd160
UUID=884bb7b0-5895-403f-b385-31820ad1c262	/mnt/wd160	ext4	nodev,noauto,noexec,rw,user,	0	3

repeatedly powering the device on-and-off does not show the labeled drive (wd160) in Nautilus. What did I do wrong?

mark@Lexington:/media$ dmesg | tail
[36282.186517] scsi 20:0:0:0: Direct-Access     WDC WD16 00AVVS-63L2B0         PQ: 0 ANSI: 2 CCS
[36282.186969] sd 20:0:0:0: Attached scsi generic sg5 type 0
[36282.413617] sd 20:0:0:0: [sde] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[36282.414416] sd 20:0:0:0: [sde] Write Protect is off
[36282.414421] sd 20:0:0:0: [sde] Mode Sense: 34 00 00 00
[36282.415258] sd 20:0:0:0: [sde] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[36282.449521]  sde: sde1
[36282.452144] sd 20:0:0:0: [sde] Attached SCSI disk
[36476.357058] EXT4-fs (sde1): recovery complete
[36476.357594] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)

---

### Post by steeldriver on 2013-08-16
The 'noauto' option means the device won't be mounted unless you issue an explicit mount command e.g. 'mount /mnt/wd160' - from [FONT=courier new]man fstab[/FONT] :

```

              noauto do not mount when "mount -a"  is  given  (e.g.,  at  boot
                     time)

```

---

### Post by Mark_in_Hollywood on 2013-08-16
By issue a "command" does that mean powering up the device?

and what does this mean?

mark@Lexington:/media$ df -T

/dev/**sde1**      ext4     153835556   191936 145829172   1% /media/wd160
/dev/**sdf1**      ext4     153835556   191936 145829172   1% /media/wd160

Frightened by this double listing of the same device, I have commented out the line in fstab, deleted the /media/wd160 directory. I have a backup of my fstab in case, but ladies and gentlemen, should it really be this hard to allow a user to create files and save them, copy files, paste files and delete files on an external device?

---

### Post by oldfred on 2013-08-17
I like the suggestions by Morbius1.
And at end you always run the sudo mount -a to make sure you do not have any typos.
My examples are mixed. Some use /media and some use /mnt and many argue over which is correct. There is no correct, just what you prefer. If /media it will show in Nautilus, but some show twice once with an underscore and of course only one works. If in /mnt it will not show in Nautilus unless you drill down from / (root) to /mnt. But I prefer that as I link folders directly into /home and do not want to see the mount.

 from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

   For ext4:
[COLOR=#ff0000]UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2[/COLOR]

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

And you need permissions & ownership

 sudo chmod -R a+rwX,o-w /mnt/data

 sudo chown $USER:$USER /mnt/data

---

### Post by Mark_in_Hollywood on 2013-08-19
Where oldfred wrote:

**sudo chown $USER:$USER /mnt/data**

it should have been 

sudo chown **-R** $USER:$USER /mnt/data

Immediately after the chown -R, I am able to place files on the drive.

FOLKS: ALL BELOW is for reference only. YMMV.

Thank you again, Ubuntu Community.


sudo blkid -c /dev/null

/dev/sdf1: UUID="f3c43eab-5888-4e6d-9755-4807e1bf6f7d" TYPE="ext4" 

sudo mkdir /media/wd160

mark@Lexington:/media$ ls
wd160

gksudo gedit /etc/fstab
UUID=f3c43eab-5888-4e6d-9755-4807e1bf6f7d	/media/wd160	ext4	defaults,noatime   0   0

mark@Lexington:/media$ sudo mount -a
mark@Lexington:/media$

mark@Lexington:/media$ sudo chmod -R a+rwX,o-w /media/wd160
mark@Lexington:/media$

mark@Lexington:/media$ sudo chown mark:mark /media/wd160
mark@Lexington:/media$

BUT on opening the drive in Nautilus and trying to drag a text file into it, I get a "**drive is read only error**". And on "safely removing drive", powering down and powering up again:

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sde1 is already mounted on /media/wd160
mount failed

and on power toggle again:

Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdf1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

tail or so:

mark@Lexington:/media$ dmesg | tail
[40443.116883] sd 15:0:0:0: Attached scsi generic sg5 type 0
[40443.343668] sd 15:0:0:0: [sdf] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[40443.344434] sd 15:0:0:0: [sdf] Write Protect is off
[40443.344439] sd 15:0:0:0: [sdf] Mode Sense: 34 00 00 00
[40443.345182] sd 15:0:0:0: [sdf] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[40443.383321]  sdf: sdf1
[40443.387055] sd 15:0:0:0: [sdf] Attached SCSI disk
[40443.743395] EXT4-fs (sdf1): Unrecognized mount option "uid=1000" or missing value
[40487.090199] EXT4-fs (sdf1): Unrecognized mount option "uid=1000" or missing value
[40553.854213] EXT4-fs (sdf1): Unrecognized mount option "uid=1000" or missing value

SO, I changed the fstab entry to:

UUID=f3c43eab-5888-4e6d-9755-4807e1bf6f7d	/media/wd160	ext4	defaults,noatime	0	0

I can mount this device when I am:

sudo su -

but not otherwise.

---

### Post by Mark_in_Hollywood on 2013-08-20
So, it worked until the 'puter was powered down overnight. Today, on power up of external device, Gnome error message: "Unable to mount . . . Exit code 1".

To RECAP:

This is to mount/unmount a hard disk drive attached to the 'puter via USB cable, and to write and delete files as user:user.

The drive was formatted as: EXT4 using GParted.

The following was done. A subdirectory in /media was created.

sudo mkdir /media/wd160

Check to see the sub-directory

cd /media

ls

wd160

CHECK.

sudo blkid

/dev/sdg1: UUID="f3c43eab-5888-4e6d-9755-4807e1bf6f7d" TYPE="ext4" 

gksudo gedit /etc/fstab

add following line:

UUID=f3c43eab-5888-4e6d-9755-4807e1bf6f7d	/media/wd160	ext4	defaults,noatime,nofail,noexec,user 0 0

Save & exit Gedit.

CHECK.

sudo mount -a

Terminal prompt returns and reports nothing wrong

CHECK.

sudo chmod -R a+rwX,o-w /media/wd160
Terminal prompt returns and reports nothing wrong

sudo chown -R mark:mark /media/wd160
Terminal prompt returns and reports nothing wrong

Open wd160 with File Manager Nautilus.

Place copy of text file into drive. OK
Delete copy of text file from drive. OK

---

### Post by oldfred on 2013-08-20
The fstab mounts are primarily for internal drives. One of the issues of external drives particularly USB is that they may not come up to speed and be mounted in time for the boot process which now is very quick. 
Or fstab tries to mount the drive before it is ready & fails. Your sudo mount -a remounted it and since it was up to speed it then worked.

I do not know how to do it but some add a script to mount at the end or just create a script to click on to mount an external drive or anything that is too slow to mount while booting.

---

### Post by Bubba_Jackson on 2013-08-21
> **oldfred said:**
> The fstab mounts are primarily for internal drives. One of the issues of external drives particularly USB is that they may not come up to speed and be mounted in time for the boot process which now is very quick. 
Or fstab tries to mount the drive before it is ready & fails. Your sudo mount -a remounted it and since it was up to speed it then worked.

I do not know how to do it but some add a script to mount at the end or just create a script to click on to mount an external drive or anything that is too slow to mount while booting.

True, I have personally experienced an issue with fstab while mounting a network drive at startup. Logs showed no errors, but drive wouldn't automount. After startup, running mount -a executed with no problems. Solved it by using the following script in /etc/network/if-up.d/:

```
#!/bin/sh
mount -a
```

Using the same script may solve your problem I think, but I'm no expert at this topic. Maybe if you put this script (and make it executable) in /etc/init.d/, then put a symlink in /etc/rc2.d/ named S99usbauto or something (notice the S99 prefix, so it would execute among the last scripts) pointing to the script in /etc/init.d/, it would solve your problems. Again, I'm not an expert at this topic, just proposing a (possible) solution. Maybe some of the more experienced users can shed some light on this.

---

### Post by Mark_in_Hollywood on 2013-08-21
oldfred and Bubba - you are both correct. This morning, on powering up the 'puter, the splash screen said the wd160 was not ready and did I want to Skip etc. I chose Skip and the OS booted without problem. On powering up the external drive, all is OK. And that is without issuing the sudo mount -a commandline. So, I'm going to re-closed this and again thank you for your time and attention.

---

### Post by oldfred on 2013-08-21
Is the fstab mounting it, or is it getting mounted by Nautilus and udev with defaults from that, not fstab settings. Since you changed ownership & permissions on drive, it should be ok.

As soon as you are done booting & USB drive is up & running, do a mount command.

mount

---

### Post by Mark_in_Hollywood on 2013-08-24
"Is the fstab mounting it, or is it getting mounted by Nautilus and udev with defaults from that, not fstab settings"

I have no idea as to whether fstab or Nautilus and udev are or are not mounting.

BUT, I've taken up enough of the time of others at this forum. It's working good-enough-for-me. If a problem arises where the drive becomes unusable or destabilizes the OS, I'll post and reference this work by you all, here, but for now:

thanks, Ubuntu Community

case closed.

---

