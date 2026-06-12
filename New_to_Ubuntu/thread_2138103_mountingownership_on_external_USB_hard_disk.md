---
title: "mounting/ownership on external USB hard disk"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by squakie on 2013-04-23
Note to moderators:  Please don't combine this with my thread on shares on this type of drive.  It appears the problem is much more basic than that, so I'd like a separate thread (the other doesn't get any attention).

Given:
[LIST]
[*]an external USB hard disk with a NTFS file system with a subfolder of dwedell 
[*]a userid of dwesamba, member of group dwesamba 
[*]a folder /shares, owned by dwesamba with group dwesamba 
[*]a subfolder of /shares/NAS 
[*]the user dwesamba is a auto-login account 
[*]fstab includes a line for the external USB hard disk to a mount point of /shares/NAS 
[/LIST]

On a boot of the system, the file system on the external USB hard disk does get mounted at /shares/NAS, however, the ownership/group of /shares/NAS changes to root:root, so nobody has any r/w access.  

I had specifically created the dwesamba group so that user in the dwesamba group could have access to the file system for r/w (the idea being they will become samba shares, and the subfolders within /shares/NAS would become the home folders for users). 

Since the boot is run as root, and the mounting is done via fstab during the boot, I assume that has something to do with the mount point changing to root:root at run time.  However, if I umount the file system then /shares shows again as dwesamba:dwesamba  and the /shares/NAS folder shows as dwesamba:dwesamba.

I don't understand this.  I thought the file system being mounted to a mount point owned by a user would make the file system owned by that user.  Is this because the file system on the external drive is NTFS?

If so, a dumb question:  if I change the external drive so it only has an ext4 file system, will Windows users still be able to r/w "normal" Windows files to that file system when it becomes a share?

---

### Post by Kopkins on 2013-04-23
No, windows can't see Ext4 file systems. But there are solutions. Try [Here](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/).

---

### Post by DuckHook on 2013-04-23
> **squakie said:**
> ...if I change the external drive so it only has an ext4 file system, will Windows users still be able to r/w "normal" Windows files to that file system when it becomes a share?Someone else will have to help you with the SAMBA ownership permissions, but I do know that the underlying file structure does not effect how Win users can r/w files so long as this is being done *through SAMBA*. However, if they try to read the disk directly, they can't, not without special drivers at any rate. Samba basically translates all file data into Win requests so that the underlying file system is irrelevant.

---

### Post by squakie on 2013-04-23
Thanks duckhook - I was hoping that was the case so I wouldn't have to use something like cifs.  Basically I'm going to store images from backups on the Windows machines up on the Samba shares, and also create some for sharing things like photos, docs, etc.

I'm going to try the ext4 thing and see what I can get set up!

Thanks!

---

### Post by DuckHook on 2013-04-23
> **squakie said:**
> I'm going to try the ext4 thing and see what I can get set up!

In my opinion, ext4 is so much superior to NTFS that it's no contest. Just make sure that disks don't get filled beyond 80% and there's very little fragmentation, whereas NTFS will need to be defragged every week. I also believe that the ext4 journaling system is better, but this is more a matter of opinion. It's been easier for me to recover from a power outage with ext4 than NTFS at any rate.

You may also wish to look into btrfs if you are starting from scratch, although there are very few tools/utilities that I could find. Even ext4 developer speaks highly of btrfs. I really don't know much about it beyond its reputation as a more advanced product that fills in some holes in the ext4 journal. If you are looking for stability with proven tools/utils, you may want to just stick with ext4.

---

### Post by squakie on 2013-04-24
well, did the switch to ext4, have owner/group and mount point in fstab, and added a udev rule.  How dumb can I get - of course root is going own the file system when it mounts!  I can access the folders in that file system by user, so that's working.

---

### Post by squakie on 2013-06-25
Everything working fine now.

---

