---
title: "Mounting NFS shares from Synology"
date: 2022-11-24
forum: New to Ubuntu
---

### Post by johnster001 on 2022-11-24
Hello all, I'm brand new to Ubuntu (although I used to work in Unix years ago).  I'm in the middle of replacing my Windows home computer with an Xubuntu installation, and am making pretty good progress.  One thing I have to have on this workstation is access to the shares on my local Synology NAS, and I'm running into issues getting that working.  I've created a user on the NAS that matches the username I'm logging into the workstation with, and have granted that user R\W permissions on the shares I'm trying to access.  The NFS settings for my test share are set to allow access to any host on my local subnet, Squash is set to no mapping, Security is set to Sys, and I have enabled asynch, connections from non-privileged ports and access to mounted subfolder.  I have created a mount-point (/mount) and am using this command to mount:

$ sudo mount <IP of NAS>:/volume1/NFSDemo /mount

This succeeds but when I try to access the mount point, I get permission denied. Looking at the mount point I can see that the permissions are set to 000 root root, although before I mounted the share, the perms were 775 root root. If I manually change the perms I can access the files in the share but that just doesn't seem right.  Can someone advise me as to what I need to do to get this going?  I want shares on the NAS to be secure but I need to be able to access them from software that will be running on this workstation.  

Thanks!

---

### Post by TheFu on 2022-11-24
It is permissions on the NAS local storage that need to be fixed.  The NFS client cannot modify anything for root-owned files or directories on remote storage.

BTW, usernames don't matter, it is the UID that must match for NFS to work, or you need to create a client-uid-to-server-uid mapping using some tool that is supported on both sides. idmapd.conf is the normal config.  I've never used it, but, in theory, it is the method to be used.  Whether your NAS supports it, I wouldn't know. My NAS runs Ubuntu Server.

---

### Post by johnster001 on 2022-11-24
> **TheFu said:**
> It is permissions on the NAS local storage that need to be fixed.  The NFS client cannot modify anything for root-owned files or directories on remote storage.

BTW, usernames don't matter, it is the UID that must match for NFS to work, or you need to create a client-uid-to-server-uid mapping using some tool that is supported on both sides. idmapd.conf is the normal config.  I've never used it, but, in theory, it is the method to be used.  Whether your NAS supports it, I wouldn't know. My NAS runs Ubuntu Server.

Thanks for the quick response.  I did ssh into the NAS (Synology) and get the UID and GID of the account, but I hadn't planned on mapping the user accounts.  In doing some digging, it looks like Synology doesn't have a great NFS v4 implementation, so maybe I'll switch to SMB.  My goal is to get SABNZB working on Ubuntu and to have it download directly to shares on the Synology.  I currently have this working well in Windows but I'd really prefer to have the workstation running Ubuntu for many reasons.  If anyone here has any experience in this, please feel free to chime in, otherwise I might create a separate topic for it.

Thanks!

---

### Post by TheFu on 2022-11-24
I can't help with SABNZB, since I don't pirate stuff, but the easy way would be to create a directory with 777 permissions for 2 minutes that is part of the NFS share, then on the client, have a userid you control create another directory inside that new directory so it will be the owner.  From the client, run chmod 775 on that new directory and on the NAS, move it up 1 level to just below the NFS mount.  Don't forget the delete the 777 root:root directory to prevent terrible security issues.  You may want to setup a group for the software and your userid to share access to this location.  If you search these forums for "working together", you'll see the basic method for allowing all the userids in a single group to maintain read/write access for all files and subdirs created below that location.  Standard Unix stuff which you probably already know.

CIFS/samba is a terrible compromise for Unix systems that support NFS.  Please don't do that. Normal Unix permissions are a great way to setup anything you need.  If you are really desperate, you can allow a the root/sudo to control permissions from an NFS client, but this is a huge security failure, IMHO.  If you need it, then you should be able to read the Synology manual enough to figure out how.  NFS performance is better than Samba for any streaming.  If you look in any media center forums, you'll see this is true for everyone and recommended.

---

### Post by johnster001 on 2022-12-01
Following up on this thread.  I initially decided to try CIFS just to see if it was possible, but I didn't want to just drop NFS and, while this is strictly for local network access, I thought that NFS would be more secure so I ended up giving it another shot.  I created a new user on the NAS, recorded the UID and created a user with a matching name and UID on the Ubuntu box.  I set up the NFS perms in Synology and, with much googling, edited the fstab file with some entries to automount the folders:

#mount NAS folder at boot:
<IP of server>:/volume1/FolderName /MountPoint/MountFolder nfs defaults,user,relatime 0 0

Then ran mount -a from a user terminal.  It appears to be working and I can edit files in those folders.  

Now I have a follow-up question, if these folders are mounted and the Ubuntu box loses power, will those shares become corrupted?  I seem to remember a setting that marks the FS as clean on a regular basis to avoid such a problem but I dont remember if it applies to NFS mounted volumes.  I'm happy to google for answers but thought I'd seek out wisdom here first.

Thanks

---

