---
title: "NAS and external HDD not visible after reboot"
date: 2018-08-25
forum: New to Ubuntu
---

### Post by troywilkins on 2018-08-25
Hi everyone.

I am a complete n00b when it comes to Linux and Ubuntu.  I have been messing around with computers virtually all my life, learning BASIC programming on the Commodore Vic 20 and Atari 400 before I even started school, getting a 286-based PC (Amstrad PC2286, if anyone remembers those) and then later switching to an Amiga 1200.

I got a Raspberry Pi 3 Model B not too long after they came out, played with that a bit, but didn't do all that much with it after installing RetroPie and getting that setup so I could access it from other machines here.  But that gave me a little taste of what was possible.

So, recently, I decided to stop using one of my Windows 10 PCs for particular tasks, and figured that a headless Linux system would be much more appropriate.  I installed Ubuntu desktop 18.04 LTS on a hp compaq dc7900 ultra-slim desktop (Core 2 Duo E7500, 2GB RAM, 80GB HDD), and then worked at installing what I wanted to run on it and getting it accessible from the Windows boxes here, by SSH, VNC and RDP.  I also removed much of the stuff I wouldn't need, such as Libreoffice and the movie player.

I got SABnzdb, Sonarr and Plex Media Server running on it, and so disconnected it from the monitor, and now have the box sitting under my NAS, and am slowly migrating everything to that and off the Windows 10 machine that was doing all that.  It's not all 100% yet, but I'm still learning.  My media files for Plex are stored all over the place, some on one of my Windows PCs (that one that was running all this stuff), most on external USB HDDs, and some on the NAS, which currently doesn't have anywhere near enough storage for me to move everything to that, but that is the plan eventually.

As it is now, I have one external USB HDD connected to the Ubuntu box, and I have it setup to access 2 shares on the NAS.  I don't know why, but if I reboot the Ubuntu box, or we have a power outage and later the power comes back on, the NAS and external HDD aren't visible to Ubuntu unless I logon and do a "sudo mount -a", so that's an issue I'd like to resolve.

I've also read about Pihole, and attempted to install that, but that didn't work, the install failed part way in, so I removed it.  But that's another thing I'd like to get up and running if at all possible in the future.

Anyway, *does his best Dr. Nick from The Simpsons impersonation* Hi everybody!

---

### Post by TheFu on 2018-08-27
"NAS" is a little vague. NFS or some other protocol?

Also, NX is a more efficient protocol than either RDP or VNC.  x2go is the least-hassle implementation. Clients exist for the 3 main desktops.  Night and day is commonly used by people after they switch to NX.  Plus, NX uses ssh so you can remotely access your desktop from anywhere in the world, if needed.  But if you are good at ssh CLI, you don't need it.  sftp is pretty handy to have and sshfs is amazing, if you need it.

[http://dilbert.com/strip/1995-06-24](http://dilbert.com/strip/1995-06-24) might not fit you, but still funny for "those who know." We're probably about the same age. I started on a Model 1 TRS80.  Found Unix around 1993 and my world changed completely.

---

### Post by troywilkins on 2018-08-27
Hehehe.  I love Dilbert.

Sorry about that, the NAS is a QNAP TS-410.  I believe that runs a form of Linux, and in etc/fstab I have it set to access with CIFS.

The external USB HDD was setup with the Windows machine it was connected to, so it's formatted with NTFS.  It's an old Seagate 1TB.

And yes, I'm aware that RDP or VNC are not particularly efficient, but they get the job done and are only used when I need something graphical anyway, if I only need a command line, then I just SSH in instead.  Still, I'll look into those alternative options, thank you.

If it's any help, here's what I've added to /etc/fstab:

```
//192.168.20.9/tv /media/TV cifs username=guest,password=,uid=nobody,iocharset=utf8,noperm 0 0
//192.168.20.9/Movies /media/NasMovies cifs username=guest,password=,uid=nobody,iocharset=utf8,noperm 0 0
//dev/sdb1 /media/SeagateMovies ntfs username=guest,password=,uid=nobody,iocharset=utf8,noperm 0 0
```

---

### Post by TheFu on 2018-08-27
NTFS permissions are controlled by mount options.  Chances are that 
```
username=guest,password=,uid=nobody,
```
aren't the options you want.  Generally uid/gui mean to use numbers, not usernames or groupnames. There are exceptions, but I always have to check the manpages.

I have 1 NTFS USB device (a video recorder only uses that file system). My mount options for it are:
```
250G -nodev,nosuid,timeout=2,fstype=ntfs,uid=1000,gid=1000 LABEL=250G
```
These are in my autofs setup, so you need to move those around and remove some that wouldn't apply. I mount using the LABEL, though in an fstab, using a UUID would be preferred.  I like to use autofs for any storage that isn't permanent, which applies to NFS and USB storage. Personal preference. 

You can also set the file and directory create masks in the mount options.  For plex, you might want 644 for files and 755 for directories.  The mask would be the xor for that, I think.

I don't use CIFS much, prefer the native permissions that NFS provides.  CIFS is provided for Windows clients, not Unix here. Sorry.

---

### Post by troywilkins on 2018-08-28
Thank you for your prompt response.  I must admit to being a little more confused here now.  I am still very much a n00b, sorry.
> **TheFu said:**
> NTFS permissions are controlled by mount options.  Chances are that 
```
username=guest,password=,uid=nobody,
```
aren't the options you want.  Generally uid/gui mean to use numbers, not usernames or groupnames. There are exceptions, but I always have to check the manpages.
Ahh, okay.  How do I find what numbers to use?  

> **TheFu said:**
> I have 1 NTFS USB device (a video recorder only uses that file system). My mount options for it are:
```
250G -nodev,nosuid,timeout=2,fstype=ntfs,uid=1000,gid=1000 LABEL=250G
```
These are in my autofs setup, so you need to move those around and remove some that wouldn't apply. I mount using the LABEL, though in an fstab, using a UUID would be preferred.  I like to use autofs for any storage that isn't permanent, which applies to NFS and USB storage. Personal preference. 
I had never heard of autofs, and am looking into that now.  This looks to be more suitable, thank you, I was only using fstab became that's what I found when looking for how to mount drives using google.

> **TheFu said:**
> You can also set the file and directory create masks in the mount options.  For plex, you might want 644 for files and 755 for directories.  The mask would be the xor for that, I think.
File and directory create masks?

> **TheFu said:**
> I don't use CIFS much, prefer the native permissions that NFS provides.  CIFS is provided for Windows clients, not Unix here. Sorry.So CIFS is wrong here, should I omit that, or replace it with NFS?  Now I'm completely lost, sorry.

---

### Post by TheFu on 2018-08-28
uid and gid numbers are normally in /etc/passwd and /etc/group  files for home users.  Rather than explain each field, I'll just point you at the manpage for these files.   **man -s 5 passwd** and  **man -s 5 group** Learning to read and understand manpages is an important skill.  You can search manpages using the **apropos** command.

Or you can use the **id** program.

**autofs** might be too complicated for a noob. I'd suggest you just take the mount options that are relevant. Behind the scenes all mount options are used by the correct mount.whatever program regardless of which front-end for mounting is used.  You can manually mount, use the fstab, or use autofs.

Whenever a file or directory is created, the permissions are controlled by the create "permissions mask"  Never forget that Unix is multi-user from the ground up. Files and directories always need to have permissions to be useful.  For file systems like NTFS that aren't easily mapped into the Unix permissions, the system has to provide them for Linux/Unix to use.   That is done by the mount program in home environments. Basically, all files and all directories get the same permissions on NTFS.  For media files, that is probably sufficient.  

"Here" means at my setup. Your setup is different.  My point in sharing that information was so you knew I don't know much about that sort of setup.  Only you can choose what is best for your situation based on your skills, knowledge, needs.  My NAS running Ubuntu Server allows multiple file sharing protocols to be used concurrently for the same storage areas.

---

### Post by troywilkins on 2018-11-18
Ok, I got a bit further, and now that I've got the NAS working properly, have got most of what I want to access on there instead.

But this brings me to a related problem.

I thought, as the NAS is Linux based, and Ubuntu is also Linux based, that the two would work together nicely.  But to be honest, I'm now tempted to wipe the HDD on my Ubuntu box and just install Windows on it.

Why?

Well, my Windows boxes have no trouble accessing the content on the NAS, both reading and writing, no trouble.

However, the Ubuntu box, well, one of the processes on it, is unable to write to the exact same shares on the NAS.  Can read, no trouble, but I need it to be able to write to it as well.

I've asked on Forums specific to the software involved (NZBdrone/Sonarr), and on forums specific to the NAS (QNAP TS-140), and had no luck.

I'm really at my wits end and am so close to just starting again with a Windows install on the Ubuntu box, because that works like it should - I have the same software running on one of the Windows boxes and it can read and write no problem.

As far as I can tell, the NAS should be allowing read and write access to the Ubuntu box for all users, but it seems only root can write.  I've tried various ROOT_SQUASH options on the shared folder on the NAS, and none have made any difference.  I thought maybe the /media/NASTV mountpoint may be the issue, so I tried a CHMOD 777 on that, but no change.  I really have no idea, any help would be very much appreciated.

---

