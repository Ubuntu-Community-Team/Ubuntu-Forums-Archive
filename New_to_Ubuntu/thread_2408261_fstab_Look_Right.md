---
title: "fstab Look Right?"
date: 2018-12-16
forum: New to Ubuntu
---

### Post by echotech2 on 2018-12-16
Sorry, just realized this might be the wrong forum.
   
  Ubuntu 16.04.x fresh install with previous "home", updated to 18.04.1
 
 I thought, maybe incorrectly, that fstab (details below) might have something to do with this:   
My problem I am trying to fix was that going to "File - Open" in many programs (eg: k3b) the Documents, Download, etc directories are shown along with "Other Locations".  If I select "Other Locations" I get two entries: "Computer" & "Movies".  Selecting "Computer" gives me the / directory listing and I can go to/mnt and select the drive/directory I want.

  Note: "Movies" is listed in /media/dave" and it's the only file there:

```
dave@scamper:~$ dir /media/dave
Movies
```

 Everything else seems to be   in mnt:

```
dave@scamper:~$ dir /mnt
2cc15ef2-164e-464a-8fb8-d4af8087b7ad  Data   usb-hd
96f6a154-2ed4-4b96-8cc1-bf6d4b5cbecb  Music  Video
9efda54c-3f24-4bdf-a1cb-c35491766d48  sdb1   wwn-0x50004cf208c521a1-part1

```

 The above 3 uuid's(?) and the wwn-..(?)  entries are empty directories. sdb1 is an empty directory and is the same drive as "Data" according to GPartEd. "Data" has and shows all my files.

  Some thing just looks off to me in fstab, or maybe it's OK?  

  Physical setup: 
 sda = ssd with root and separate /home
 All following disks are single partitions, ext4: 
 sdb = ssd  labelled "Data" 
 sdc = hdd labelled "Movies" 
 sdd = USB Hard drive labelled "usb-hd", to be plugged in for backups then unplugged
 sde = hdd labelled "Music" 
 
  There are also 2 DVD burners and a multi-card reader on this PC.

 fstab:
```
 <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=256edd1a-cef1-4654-b448-c51c468dcee2 /               ext4    noatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=58b0c09a-0c7e-41ae-aa9f-843b7873dc4e /home           ext4    noatime,defaults        0       2
# swap was on /dev/sda5 during installation
UUID=ece2170f-0111-4b40-b089-155be81a00e0 none            swap    sw              0       0
/dev/disk/by-uuid/2cc15ef2-164e-464a-8fb8-d4af8087b7ad /mnt/2cc15ef2-164e-464a-8fb8-d4af8087b7ad auto nosuid,nodev,nofail,noauto 0 0
/dev/disk/by-label/usb-hd /mnt/usb-hd auto nosuid,nodev,nofail 0 0
LABEL=Music /mnt/Music auto nosuid,nodev,nofail 0 0
LABEL=Video /mnt/Video auto nosuid,nodev,nofail 0 0
LABEL=Data /mnt/Data auto nosuid,nodev,nofail 0 0
/dev/disk/by-id/usb-Generic_USB_SD_Reader_9205291-0:0 /mnt/usb-Generic_USB_SD_Reader_9205291-0:0 auto nosuid,nodev,nofail,noauto 0 0
```

---

### Post by TheFu on 2018-12-16
> All following disks are single partitions, ext4:
sdb = ssd labelled "Data"
sdc = hdd labelled "Movies"
sdd = USB Hard drive labelled "usb-hd", to be plugged in for backups then unplugged
sde = hdd labelled "Music" 

This is incorrect. sdb is a whole disk. Any partition would have  a number.  Same for sdc, sdd and sde.  sdb1 would be a patition with a label and UUID.

BTW, 'dir' isn't a Linux command.  We need to see** ls -al** output please.  Seeing the permissions, owner, group is very important on any Unix system.

You can use the /dev/disk/.... links if you like, but you can also use the LABEL= and UUID= constructs instead for a cleaning fstab.  **blkid** will show which devices go with which UUIDs.  Or an **ls -al /dev/disk/by-uuid/* **will too.  For permanently connected disks (SATA/eSATA/infiniband) I'll use UUIDs.  For temporary mounts, I much prefer to use LABELs.

---

### Post by oldfred on 2018-12-16
If you mount a partition in /mnt  or / it will not show in Naulitus.
If you mount in /media/$USER,  which is the default mount when you click on a partition, it will show in Naulitus. But will mount with UUID if not labeled, or by label if labeled.

I link my mounts back into /home, but do not use the /media mount. Primarily since I mount just one large data partition, but then link each folder separately.

---

### Post by TheFu on 2018-12-16
There are many things that experience teaches if a mentor with 30+ yrs of experience isn't available. Unfortunately, "experience" often means "learning by mistakes."

I only use the /media locate by accident. If I'm going to mount anything more than once, it will be to a specific location.  Often that is under /D, or /Data or /misc.  /media is for mounts managed by automatic OS tools that aren't under our control.  If/when those tools screw up, I don't want my data partitions mounted anywhere near them. I've been burned.

I only use /mnt for temporary administrative mounting, as the specification (file system hierarchy standard) says.  I learned a long time ago to follow the standards whenever possible because those people were much smarter than me. If I need a quick place to mount some storage before making a file system, /mnt is where I put it.

For temporary USB mounts, I use autofs and LABELs. That way once the storage is connected, it is made available just by requesting anything in the mount area.  I've worked places where HOME directories were dynamically mounted in this way to keep server resources down when 3,000+ users had accounts.  Got into the habit in the mid-90s and never regret using that technique.

---

### Post by Impavidus on 2018-12-16
```
 <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=256edd1a-cef1-4654-b448-c51c468dcee2 /               ext4    noatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=58b0c09a-0c7e-41ae-aa9f-843b7873dc4e /home           ext4    noatime,defaults        0       2
# swap was on /dev/sda5 during installation
UUID=ece2170f-0111-4b40-b089-155be81a00e0 none            swap    sw              0       0
```These are fine.
```
/dev/disk/by-uuid/2cc15ef2-164e-464a-8fb8-d4af8087b7ad /mnt/2cc15ef2-164e-464a-8fb8-d4af8087b7ad auto nosuid,nodev,nofail,noauto 0 0
```I wouldn't use the entire UUID in the name of the mountpoint. Also, you don't mention this partition in your physical setup. If it's not mounted, your mountpoint is an empty directory. Does the partition exist? If not, the nofail option ensures no error message is generated (and noauto that mounting at boot time isn't even attempted). Maybe you can just remove this line from your fstab and delete the empty directory from /mnt.
```
/dev/disk/by-label/usb-hd /mnt/usb-hd auto nosuid,nodev,nofail 0 0
LABEL=Music /mnt/Music auto nosuid,nodev,nofail 0 0
LABEL=Data /mnt/Data auto nosuid,nodev,nofail 0 0
```These are automatically mounted at boot, but silently ignored if not present. That's OK, if you want that.
```
LABEL=Video /mnt/Video auto nosuid,nodev,nofail 0 0
```Automatically mounted at boot time, but silently ignored if not present. In you physical setup you write you have no Video, but Movies, so this one doesn't exist. Maybe change to Movies?
```
/dev/disk/by-id/usb-Generic_USB_SD_Reader_9205291-0:0 /mnt/usb-Generic_USB_SD_Reader_9205291-0:0 auto nosuid,nodev,nofail,noauto 0 0
```
I wouldn't use such a long path for a mountpoint, otherwise fine.

Your Movies partition is not listed in fstab, so your file manager can automount it in /media/dave/Movies. Fix the fstab to use Movies instead of Videos and it will sit longside the others in /mnt.

The unused directories in /mnt can be removed.

---

### Post by Morbius1 on 2018-12-16
The reason your fstab looks odd is that you used Disks to configure your mounts in fstab. 
> My problem I am trying to fix was that going to "File - Open" in many  programs (eg: k3b) the Documents, Download, etc directories are shown  along with "Other Locations".  If I select "Other Locations" I get two  entries: "Computer" & "Movies".  Selecting "Computer" gives me the /  directory listing and I can go to/mnt and select the drive/directory I  want.

If you want all those mounts to show up together you need to follow [COLOR=#0000cd]**oldfred**[/COLOR]'s advice for the exact reason he posted: Mountpoints under /media or your home directory show up on the side panel of your file manager and File-Open, etc.... So change your mount points to something under /media.

[COLOR=#0000cd]**Note**: Do not mount things under /media/$USER  ( /media/dave in your case ) in fstab. The system will automount things under that folder.[/COLOR]

[COLOR=#0000cd] **Note2**: I have no idea why Disks set all these internal partitions noauto[/COLOR]

I hate to bring this up because I truly believe that the Disks utility should be removed from the repositories so that it is never used but one of the goofiest things it does is mount things under /mnt ( which makes it so it doesn't show up automatically under File-Open, etc ) but then offers an option labeled "Show in User Interface" which adds another option to its bewildering list of options: [B][COLOR=#0000cd]x-gvfs-show.

[/COLOR][/B]What that does is force the mounted partition to show up on the side panel of Nautilus and in File-Open which it would do naturally without x-gvfs-show if it were mounted under /media.[B][COLOR=#0000cd]
[/COLOR][/B]

---

### Post by echotech2 on 2018-12-16
I just spent a long time replying and attempting to  answer everyones questions and all of a sudden everything in the reply box just disappeared, maybe because I had two tabs open, one with original thread I was scrolling through to get the at your questions and one with original thread scrolled down to the reply box.  Restore autosave did nothing.

My mistake on the  disk identification. I knew that eg: sdb meant the whole disk and as the partition took up the whole disk......                                        

  LOL thought:  Would fixing this mess up be as easy as deleting everything from Fstab except / home and swap and rebooting?  There's nothing else on sda.  Stuff that ends up in Documents, Downloads, etc I manually move to "Data" disk.  I'll figure out this linking thing eventually.

  Anyway here is all I have time for right now. I'll continue tomorrow about 1300UTC. 

```
ave@scamper:~$ blkid
/dev/sda1: UUID="256edd1a-cef1-4654-b448-c51c468dcee2" TYPE="ext4" PARTUUID="a9659b41-01"
/dev/sda3: UUID="58b0c09a-0c7e-41ae-aa9f-843b7873dc4e" TYPE="ext4" PARTUUID="a9659b41-03"
/dev/sda5: UUID="ece2170f-0111-4b40-b089-155be81a00e0" TYPE="swap" PARTUUID="a9659b41-05"
/dev/sdb1: LABEL="Data" UUID="1aed6c93-9df9-407a-acdc-33c2b09f827d" TYPE="ext4" PARTUUID="0000ec73-01"
/dev/sdc1: LABEL="Movies" UUID="9efda54c-3f24-4bdf-a1cb-c35491766d48" TYPE="ext4" PARTUUID="000221f0-01"
/dev/sdd1: LABEL="usb-hd" UUID="ee94a57b-777c-4b55-b0bd-336783121283" TYPE="ext4" PARTUUID="00050e93-01"
/dev/sde1: LABEL="Music" UUID="96f6a154-2ed4-4b96-8cc1-bf6d4b5cbecb" TYPE="ext4" PARTUUID="d209820e-01"

```

```
dave@scamper:~$ ls -al /media
total 12
drwxr-xr-x   3 root root 4096 Mar 26  2017 .
drwxr-xr-x  24 root root 4096 Dec  5 07:40 ..
drwxr-x---+  3 root root 4096 Dec 16 07:07 dave

```

```
dave@scamper:~$ ls -al /media/dave
total 12
drwxr-x---+ 3 root root 4096 Dec 16 07:07 .
drwxr-xr-x  3 root root 4096 Mar 26  2017 ..
drwx------  6 dave dave 4096 Sep 25 09:52 Movies

```

```
dave@scamper:~$ ls -al /mnt
total 44
drwxr-xr-x 11 root root 4096 Oct 21 14:23 .
drwxr-xr-x 24 root root 4096 Dec  5 07:40 ..
drwxr-xr-x  2 root root 4096 Apr 18  2017 2cc15ef2-164e-464a-8fb8-d4af8087b7ad
drwxr-xr-x  2 root root 4096 Jun  9  2017 96f6a154-2ed4-4b96-8cc1-bf6d4b5cbecb
drwxr-xr-x  2 root root 4096 Oct 11 08:50 9efda54c-3f24-4bdf-a1cb-c35491766d48
drwxrwxr-x 13 root adm  4096 Sep 20 18:45 Data
drwxrwxrwx  5 dave dave 4096 Sep 20 13:21 Music
drwxr-xr-x  2 root root 4096 Sep 21 05:41 sdb1
drwxr-xr-x  4 dave root 4096 Sep 23 13:21 usb-hd
drwxr-xr-x  2 root root 4096 Oct 21 14:23 Video
drwxr-xr-x  2 root root 4096 Apr 18  2017 wwn-0x50004cf208c521a1-part1

```

I see that the 3 UUID's and the wwn-...  entry all of which contain 0 bytes don't seem show up in blkid.  

sdb1 and "Data" are apparently the same partition. sdb1 directory is empty, "Data" has all my  files.

---

### Post by TheFu on 2018-12-17
I tested x-gvfs-show as a mount option on a 16.04 Mate system with Caja and a few NFS mounts.  It didn't do anything that I could see.

I don't have any directly connected external disks, USB, on the machine, so my test isn't the same as the OP.

Perhaps the requirement for Gnome3 exists?

I would urge extreme caution if mounting a file system under another file system.  Backups are usually performed at the file system level, so placing 1 file system into another file system where both need to be backed up would break my backup techniques without deliberate preventative action.  As Oldfred suggests, using a symbolic link from HOME/Whatever (Music, Documents, Movies, ....) to the location of the storage mount is a viable, convenient solution.

Lots of cooks in this kitchen.  I don't know much about Nautilus or Unity or Gnome3, so I'm out to let much more knowledgeable people help.

---

### Post by ubname on 2018-12-17
Hi echtech2,

i'm using Ubuntu 18.04, have 2 disks (internal) and several "usb drives" and did not had any problem configuring the system installing it and adding the second drive after install using "DISKS", they works.
I mapped the 2nd internal disk to e.g. "/home/ubname/diskdata2 (a folder in my home dir); all usb drives show up when I plug the usb cable).
i would recommend you to not use "weird" filesystems dirs but to use standard file system structure.
I do not understand what you want to do and if your disks are internal or external, if your willing to better explain what is your goal maybe I'll be able to help a bit.

HTH.

---

### Post by echotech2 on 2018-12-17
I guess my first step should be getting the mount points straightened out.

@The Fu  I'm not sure what you mean?  I have 4 internal disk + a USB disk.  The USB Disk is connected/disconnect for doing backups.  All disks are formatted ext4.

@Morbius: The only (GUI) place I could see to change the mount point is in Disks.  Despite your unlike of Disks use it or......?

  My _ideal_ goal would be have sda, the boot disk mount at startup (duh--) and the other disks mount when required, as when saving a file to one them, opening a media player etc. and then go into whatever I have set in power management for that disk when it is no longer in use.  And of course have all the disks show up in File..Open dialogue.  I use Double Commander as a file manager and they all show up there.

---

### Post by Morbius1 on 2018-12-17
> My _ideal_ goal would be have sda, the boot disk mount at startup (duh--) and the other disks mount when required, as when saving a file to one them, opening a media player etc. and then go into whatever I have set in power management for that disk when it is no longer in use.  And of course have all the disks show up in File..Open dialogue. 
Is your original requirement below a subset of the above or is the above now the new requirement:
> My problem I am trying to fix was that going to "File - Open" in many  programs (eg: k3b) the Documents, Download, etc directories are shown  along with "Other Locations".  If I select "Other Locations" I get two  entries: "Computer" & "Movies".  Selecting "Computer" gives me the /  directory listing and I can go to/mnt and select the drive/directory I  want.

I translated that to mean that you want all these partitions to show up together in "Open" and not have to use "Other Location". Am I right?

Why not keep your fstab the way it is but Bookmark the mount points. 

You have a partition that is mounting at boot: 
> LABEL=Video /mnt/Video auto nosuid,nodev,nofail 0 0
Open Nautilus ( not Double Commander - you are using Ubuntu right? ), go to /mnt/Video, then Bookmark it. A bookmark created in Nautilus will show up in "Open" in your applications along with Documents and the rest of the gang. Won't have to use Nautilus again if you don't want to/.

---

### Post by ubname on 2018-12-18
I think you need to mount internal disks at boot time then they probably can go to sleep; otherwise you'll have to mount manually with command line later when you need them.

---

### Post by Morbius1 on 2018-12-18
Found a nice tutorial on how to create bookmarks in Nautilus since they went out of their way to make it difficult: [https://askubuntu.com/questions/1039329/no-hdd-device-mount-icons-on-nautilus-when-run-nautilus-non-root-in-ubuntu-18-04](https://askubuntu.com/questions/1039329/no-hdd-device-mount-icons-on-nautilus-when-run-nautilus-non-root-in-ubuntu-18-04)

Note: At the very bottom you will notice that the responder suggested x-gvfs-show as I did above and the response from the user was:
> Unfortunately the 'x-gvfs-show' doesn't seem to do anything. Could it be permission problem or a bug?
Hmm....

I have a partition mounted in fstab that looks like this:
> UUID=551e67cb-a437-4353-b6e8-9404e2e62700 /mnt/DataL ext4 defaults,x-gvfs-show 0 2
Does not appear in the main side panel of Nautilus itself as I said it would. My Bad.

It does show up in Thunar in Ubuntu however:
[ATTACH=CONFIG]281960[/ATTACH]
And it does show up properly in Thunar in Xubuntu as well as Caja in Ubuntu MATE.

So what we have here is a gnome utility ( Disks ) that offers an option ( " Show in user interface ... x-gvfs-show ) that will not work in Gnome's default File manager ( Nautilus ) but will work for other File Managers. You have to love Gnome folks.

---

### Post by echotech2 on 2018-12-29
I'm going to mark this solved.  I had a computer malfunction requiring motherboard replacement and decided to rearrange everything while I had it all apart.  Thanks to everyone for all their help and tips.

---

