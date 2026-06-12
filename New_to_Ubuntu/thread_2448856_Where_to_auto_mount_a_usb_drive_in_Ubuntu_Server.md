---
title: "Where to auto mount a usb drive in Ubuntu Server"
date: 2020-08-14
forum: New to Ubuntu
---

### Post by shedfullofjunk on 2020-08-14
Hello

I have a question about the location of mounting a usb hdd.
I want to auto mount a usb drive everytime my server starts, I can do this but I'm not sure if the drive needs to be mounted anywhere specific.
At the moment I have it mounting in my home directory, Is there any problem with mounting it in the users home directory?
If so whats the reason? Or can it just be mounted anywhere.
Im the only one using the server so there are no other users. I guess if there were other users It would need to be mounted elsewhere and each users then given permission to access the drive?

Thanks for any information

---

### Post by TheFu on 2020-08-15
"automount" is a very specific tool. It mounts storage, local or network, when requested and later, after it isn't used any longer, umounts that storage "automatically".  On Linux, that is implemented via autofs ... and systemd has mucked with the fstab to support delayed mounting, but the systemd version doesn't remove the mount later.

I don't think you want that.  You just want to configure a mount at boot for some storage.  Because it is USB connected, I would discourage this method, since USB connections can vibrate loose or easily come unplugged.  But it is your system.  I use autofs for all USB and network storage, so when they aren't available for any reason, it doesn't matter until requested.

> Is there any problem with mounting it in the users home directory?
That depends.  When you backup your HOME, does the backup storage have sufficient space to handle the amount this other added storage can hold?  If not, then I would suggest NOT mounting anything under any specific user's HOME directory.
> Or can it just be mounted anywhere.
You can mount it almost anywhere - well - that was true before snap packages and the mandated constraints those require.  In the not-so-infinite wisdom, the snap guys have hardcoded a few approved locations for data that selected snap packages may access, if we ask nice and if the package creator has bothered to setup those specific permissions. Those locations are, exactly:
[LIST]
[*]/home/
[*]/mnt/
[*]/media/
[/LIST]

There are multiple problems with each of those locations being hard-coded and not allowing local control.  Flatpaks allow local control, I hear.   There is a standards document which clearly says where what sorts of storage and files should be placed.  
/mnt/ is for administrators temporary use.
/media/ is for removable media like USB, CDROM, DVDs.
[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) has a quick table overview.  The snap developers really should review those standards.  /home/ isn't anything special, BTW.  HOME directories can be almost anywhere. In a business environment, it is common for HOMEs to be spread across hundreds of NFS disks and only have them mounted as-needed, at login for each specific userid.  The only requirement to specify a HOME directory is in the password DB. Normally, that is in /etc/passwd - a text file, but it can be provided by any network directory like LDAP, AD, NIS, NIS+, x.500 - whatever.  Canonical needs to think more about business desktops when they design these things so they don't screw over potential clients BEFORE even starting.  A Linux desktop is NOT a freakin' cell phone.

> Im the only one using the server so there are no other users. I guess if there were other users It would need to be mounted elsewhere and each users then given permission to access the drive?
Being the only human user doesn't change anything.  Linux is multi-user from the ground up and still is regardless of your belief.  Different userids are running stuff on your system now. There are probably 50 other accounts doing that, perhaps hundreds.
As for file permissions, all popular OSes in the world today follow the Unix permissions model, except 1.  Permissions on Unix are tied to the file system used. Some file systems like ntfs or exfat or fat32 don't support managing Unix permissions.  That means that permissions can only be set for the entire file system during the mount process. User, group, permissions bits, and ACLs can only be set globally through mount options.

So - what would I do given the practical issues in Ubuntu today?  The answer depends on how much storage /home/ has.  In general, I limit a single userid to 25G of storage. This is for backup reasons. After a failure, I don't want to restore 2TB of user data to a HOME.  I want to get the system back up, with the prior system settings, any server settings, any core server data.  all programs back, have userid settings and core user data back, but any excess data that is seldom used can come later.

All that other "huge" data belongs on storage NOT in the HOME, but I might make a symbolic link from ~/data to /media/data to make access slightly easier for the point-n-click types.  Personally, I don't point-n-click much, so I'd just set the cdpath variable. Everyone has their own way of working.

Oh - and I always format storage with LVM + ext4 as the file system, unless there is a specific, required, reason for some other file system.  Flash data storage usually gets f2fs.  I have 1 NTFS partition on a sneaker-net HDD because the video recording HW only writes to NTFS, nothing else. If it worked with any Linux file system, I'd use that instead.

Regardless, if I can't backup the data, then I won't bring it online at all.  For example, a few months ago, I bought an 8TB USB3 HDD when a primary disk was showing failure signs. I didn't buy.  Turns out that primary problem was just a SATA cable. Replacement of the cable solved the problems. That 8TB sits there, without any data.
```
Filesystem                                   Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--8TB--B-lv5_back           ext4  3.6T   68M  3.4T   1% /d/b-D7
/dev/mapper/istar--8TB--B-lv4_back           ext4  3.6T   68M  3.4T   1% /d/b-D6
```
I never allow any partitions to be larger than 4TB for backup reasons. 4TB is pretty large already and takes over a full day to copy.  Notice how I mount that storage under /d/?  I avoid snaps, so there isn't any problem accessing the data.
```
/d$ ls
b-D1/  b-D2/  b-D3/  b-D4/  b-D5/  b-D6/  b-D7/  D1/  D2/  D3/  D4/  D5/ 
```
See a pattern?  Which are primary and which are backups?  Short. Clear. Names.

Hopefully, some others will chime in with how/why they do things. We are all a little different, so one-size doesn't fit everyone.

---

