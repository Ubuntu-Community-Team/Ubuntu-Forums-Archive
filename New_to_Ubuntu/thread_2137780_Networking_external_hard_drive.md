---
title: "Networking external hard drive"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by bubba04 on 2013-04-21
I hate to ask this question as it seems this horse has been beaten before, but I have been struggling with this all day. I am currently running 12.04 desktop version of ubuntu. This happens to be the first time I have ever used a linix based system!!!! So I am an newb to this.

I have used samba gui interface to network folders and successfully been able to acess them from my win 7 pc.

However my goal is to us this linix system as a media server/back up server. In doing this I am trying to network a 2 TB NTSF USB hard drive. From reading it is my understanding that when the hard drive is plugged into the USB it mounts the drive to the profile logged into unix. Thus causing this issues.

I tried following the steps below and was unable to make any progress. No matter what I do I continue to get windows cannot access... "you do not have permession to access....

[http://linuxforcynics.com/how-to/how-to-share-an-external-harddrive-in-ubuntu](http://linuxforcynics.com/how-to/how-to-share-an-external-harddrive-in-ubuntu)

one thought is to change my hard drive to fat32...and just transfer everything on and off it....

I appreciate any help.

---

### Post by SeijiSensei on 2013-04-22
I'm going to suggest a different solution from the one presented in that link.

What we're going to do is mount the external harddrive into the Linux filesystem so it looks like every other set of files and directories that Linux sees.  To do this, follow the steps at [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions).  I have an external mounted as /media/external though my drive is formatted with ext4.  If your drive is going to stay attached to the Ubuntu machine permanently, you might want to think about reformatting to ext4.  If you think you might carry it with you to use with Windows machines, leave it with its current NTFS or FAT32 format that Windows machines can natively read.

Once you have the device mounted, export it with Samba just like you have exported other directories.  You may have some issues with file ownerships.  Once the drive is mounted, type the command "ls -l /media/external" or whatever you called it and see if root owns the directory.  If so, a simple method of managing file ownerships would be to include the two directives
```

force user=root
force group=root

```
in the smb.conf definition for this share.  Then all transactions with the external drive are managed with root's permissions regardless of the identity of the connected user.  If you need to know which user put each file on the external drive, and you are happy with letting any user write to the drive, you could set the permissions on the mount point (e.g., "/media/external")  to 777, which gives all users the rights to read and write, and therefore delete, any file on the external drive.  If that's not an acceptable security policy, then you need to learn about [some of Samba's other access-control options]("http://oreilly.com/openbook/samba/book/ch06_02.html").

By the way, I also share my external drive with [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo"), which is a better choice than Samba if the clients are running Unix derivatives like Linux or OS X.

---

### Post by bubba04 on 2013-04-22
Great thanks for the suggestion.  I will give that shot today and report back.

I definately prefer to keep the drive in NTFS so that I can have the flexibility to move the drive around from time to time if needed. 

I am blown away by this linix OS. Once I get this settled on this soon to be server, I plan on setting up my win 7 pc to duel boot ubunutu and only use win 7 if gaming.....i knew windows sucked...but man.....

---

### Post by bubba04 on 2013-04-22
I appear to be having issues. I am getting the message that the fstab file does not exist? Yall have any thoughts? Thanks again!

here is a screen capture

[ATTACH=CONFIG]241667[/ATTACH]

---

### Post by bubba04 on 2013-04-22
So I am an idiot. 

THIS IS AWESOME. Seijisensei, I sure appreciate the help. It works perfectly now.

---

