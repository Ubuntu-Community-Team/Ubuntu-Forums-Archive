---
title: "no longer root user?"
date: 2019-07-09
forum: New to Ubuntu
---

### Post by delaposse on 2019-07-09
I recently started using ubuntu and created a plex media server from my laptop. I couldn't access the contents of my HDD so i followed the steps in the following guide to change the mount point of my HDD to /disks: ([https://forums.plex.tv/t/using-ext-ntfs-or-other-format-drives-internal-or-external-on-linux/198544](https://forums.plex.tv/t/using-ext-ntfs-or-other-format-drives-internal-or-external-on-linux/198544)). At this point i backed up my linux using Aptik and elected to back up everything i could and declined to exclude anything. 

Everything was good until my HDD messed up (managed to format it and sort that out, but details here : ([https://www.reddit.com/r/linux4noobs/comments/caxquf/hdd_error_unmounting_devsda1_target_is_busy/](https://www.reddit.com/r/linux4noobs/comments/caxquf/hdd_error_unmounting_devsda1_target_is_busy/))) At this point i had made some changes like adding winetrks and installing nvidia/amd graphics engines and i probably wasn't as careful as i should have been setting all that up. When i backed all my files in the HDD i decided i should install a clean linux distro and restore what i backed up a few days before. The system was running kinda weird and i figured it was due to the changes i had made the past couple of days.

After installing & restoring i followed the steps on my first link again and made the newly formatted HDD mount from /disks and used rmdir /disks/hdd to reverse my other change. my /etc/fstab looked a little different missing the parts with # which i assumed was fine because those should be just comments. i then installed plex because some apps were not restored and i had to reinstall them. i think it was at this point or prior to it i was prompted to restart for some changes to be applied. 
When i came back to the plex media server i noticed when adding libraries i only had access to / and couldnt find my hdd at all unlike before when i could find it but not see its contents. I did some research but no luck and i went browsing in my / and i noticed that most of the files either have an arrow icon (link) an X or a lock icon. I did some research there and found out i may not be the root user. i tried to use a version of this command i found on this website to grant permissions (sudo chmod ugo+wx /media/username/your_drive) replacing everything after wx with /disks/hdd. It didn't seem to change anything. i then noticed that my terminal says "sam@sam-HP-EliteBook-840-G4" and it seemed weird to me so I'm assuming it didn't say that before. I haven't seen that on any examples of terminal either. what ive come to understand from my research is I'm probably no longer the root user. Another post i found asked a user to run some commands for further details, i have run those commands and provided the results. 

I'm still very new to linux so I'm not sure, but i think not being the root user could cause problems down the line. If possible i would like to change that back. As for the more immediate future i'd like to be able to read my HDD with plex. Any help would be greatly appreciated. Feel like i just wrote a novel...sheesh. 




```
sam@sam-HP-EliteBook-840-G4:~$ whoami
sam
sam@sam-HP-EliteBook-840-G4:~$  sudo cat /etc/group
[sudo] password for sam: 
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:syslog,sam
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:sam
floppy:x:25:
tape:x:26:
sudo:x:27:sam
audio:x:29:pulse
dip:x:30:sam
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:sam
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
systemd-journal:x:101:
systemd-network:x:102:
systemd-resolve:x:103:
input:x:104:
crontab:x:105:
syslog:x:106:
messagebus:x:107:
netdev:x:108:
mlocate:x:109:
ssl-cert:x:110:
uuidd:x:111:
avahi-autoipd:x:112:
bluetooth:x:113:
rtkit:x:114:
ssh:x:115:
lpadmin:x:116:sam
whoopsie:x:117:
scanner:x:118:saned
saned:x:119:
pulse:x:120:
pulse-access:x:121:
avahi:x:122:
colord:x:123:
geoclue:x:124:
gdm:x:125:
sam:x:1000:
sambashare:x:126:sam
kvm:x:127:
clamav:x:128:
rdma:x:129:
sam@sam-HP-EliteBook-840-G4:~$ cd /
sam@sam-HP-EliteBook-840-G4:/$ ls -lh
total 104K
drwxr-xr-x   2 root root 4.0K Jul  9 06:06 bin
drwxr-xr-x   5 root root 4.0K Jul  9 06:16 boot
drwxrwxr-x   2 root root 4.0K Jul  9 05:52 cdrom
drwxr-xr-x  21 root root 4.4K Jul  9 10:48 dev
drwxr-xr-x   4 sam  sam  4.0K Jul  9 10:24 disks
drwxrwxrwx 136 sam  sam   12K Jul  9 10:18 etc
drwxr-xr-x   3 root root 4.0K Jul  9 05:52 home
lrwxrwxrwx   1 root root   33 Jul  9 06:13 initrd.img -> boot/initrd.img-4.15.0-54-generic
lrwxrwxrwx   1 root root   33 Jul  9 05:53 initrd.img.old -> boot/initrd.img-4.18.0-15-generic
drwxr-xr-x  23 root root 4.0K Jul  9 06:10 lib
drwxr-xr-x   2 root root 4.0K Feb  9 18:12 lib64
drwx------   2 root root  16K Jul  9 05:50 lost+found
drwxr-xr-x   3 root root 4.0K Jul  9 06:01 media
drwxr-xr-x   2 root root 4.0K Feb  9 18:12 mnt
drwxr-xr-x   2 root root 4.0K Feb  9 18:12 opt
dr-xr-xr-x 303 root root    0 Jul  9 10:47 proc
drwx------   6 root root 4.0K Jul  9 08:08 root
drwxr-xr-x  34 root root  980 Jul  9 10:48 run
drwxr-xr-x   2 root root  12K Jul  9 06:10 sbin
drwxr-xr-x  17 root root 4.0K Jul  9 08:08 snap
drwxr-xr-x   2 root root 4.0K Feb  9 18:12 srv
dr-xr-xr-x  13 root root    0 Jul  9 10:47 sys
drwxrwxrwt  19 root root 4.0K Jul  9 11:02 tmp
drwxr-xr-x  10 root root 4.0K Feb  9 18:12 usr
drwxr-xr-x  14 root root 4.0K Feb  9 18:20 var
lrwxrwxrwx   1 root root   30 Jul  9 06:13 vmlinuz -> boot/vmlinuz-4.15.0-54-generic
lrwxrwxrwx   1 root root   30 Jul  9 06:13 vmlinuz.old -> boot/vmlinuz-4.18.0-15-generic
sam@sam-HP-EliteBook-840-G4:/$ sudo chown user:group /disks
chown: invalid user: ‘user:group’
sam@sam-HP-EliteBook-840-G4:/$ sudo chown sam:group /disks
chown: invalid group: ‘sam:group’

```

---

### Post by CatKiller on 2019-07-10
> **delaposse said:**
> I'm still very new to linux so I'm not sure, but i think not being the root user could cause problems down the line.

*Being* root will cause you problems.

You log in as a normal user and temporarily elevate your privileges with sudo when you absolutely need to, exactly as you did already. Root can neither log in, nor have a password, on Ubuntu.

Not understanding permissions and wantonly running chown will *also* cause you problems, of course.

---

### Post by delaposse on 2019-07-10
alright. thanks. As long as its all good I am fine for now. i figured out the rest of the stuff.

---

### Post by sisco311 on 2019-07-10
Not sure how you managed, but your /etc directory is owned by your user and group (sam:sam) and has read/write/execute permissions for any user which is a serious security risk. Even if you didn't changed the owner and permissions recursively.

I would do a fresh install.

If you have a recent backup of the directory and files with the correct file permissions you could try to reset them as a practice, but after that I would still recommend a full reinstall.

---

### Post by delaposse on 2019-07-10
Alright i will. I understand a little better than a few days ago. I can try that and then do a fresh install. I'm getting a new motherboard for my laptop soon so i was going to reinstall everything anyway. 

Does the permission issue still apply if this is a personal pc? I chose to get encryption when i installed my system, but I'm thinking maybe user refers to more than just the users signed in to the computer physically.

---

### Post by The Cog on 2019-07-10
> **delaposse said:**
> alright.i understand a little better than a few days ago. I can try that and then do a fresh install. does the permission issue still apply if this is a personal pc?

Oh yes! 
Changing the ownership of files in /etc (or other system locations) will bork the system. Thoroughly. Some programs will refuse to do things because permissions aren't right. Some files have special ownership requirements. Always logging in and running as root **can** work, but is a security vulnerability in that (for instance) bad things in your browser get full system access, and you are very much more likely to accidentally hose your system.

Try to cultivate a split personality and be aware of when you are being a user, and when you are being an admin. They really are different roles. Use sudo to switch to admin mode when the need arises. When being  a user, stay within your home folder. It becomes second nature after a while.

---

### Post by delaposse on 2019-07-10
what lines in the result shows my permissions aren't correct and how should it read. i have a backup, but i want to be sure when i restore it everything is correct

i think this might have had something to do with it. 

[https://forums.plex.tv/t/using-ext-ntfs-or-other-format-drives-internal-or-external-on-linux/198544](https://forums.plex.tv/t/using-ext-ntfs-or-other-format-drives-internal-or-external-on-linux/198544)

```
# The location 
[root@lizum chuck]# mkdir /disks /disks/c /disks/media3 /disks/chuck2t
[root@lizum chuck]# chown -R chuck:chuck /disks
#
```

---

### Post by TheFu on 2019-07-10
TL;DR.

Ownership, groups, permissions and ACLs are the cornerstone of security on all Unix systems.  Screwing with those without a basic understanding will never end well.  Don't ever give "other" write permissions anywhere.  Whenever I see that, I cringe.  Doing so makes the system much more hackable. Not just for local users, but for remote users too.  People coming from Windows seem to confuse local and remote users - there isn't any different on Unix.

Windows people also get confused because on Windows, there are basically 2 file systems, while on Linux there are about 30 file systems.  Windows file systems are problematic when used with Plex or other media sharing software.  We can't tell which file systems you might be using, but know that NTFS or FAT32 don't support chown or chmod commands without a little complex setup.  Most people choose to keep it simple and control the owner, group and permissions using only the mount options.

I use Plex. Have for a few years.

Anyways, when you are knew to Unix-like operating systems, trying to jump into intermediate tasks is hard without gaining the basic knowledge first.  In a business, you'd have a neighbor or mentor who could explain things as you need to know them a few times a day for 6 months.  If anyone posting above were at your computer now, we'd run a few commands, look at the output and explain all those little things that take time and experience to learn.  When you are alone, you are missing many those those tiny details which seem unimportant in Windows, but are very important in Linux.

For example, using/abusing the root userid is a terrible idea.  About 10% of the time, someone new to Unix will trash their system using it.  Best NOT to.

```
sam@sam-HP-EliteBook-840-G4:~$
```
tells me much about the current situation, assuming you haven't customized it.

I know the current userid is sam.  That is an excellent userid. Short, all lowercase, begins with an letter.

I know the hostname for the computer (or virtual machine) is "sam-HP-EliteBook-840-G4".  This is a terrible hostname for a number of reasons. It is long, it has mixed case (should be all lowercase), and the dashes could cause problems.  In theory, the mixed case shouldn't matter, but some programs won't handle the mix correctly.  Next install, I'd make it shorter, all lowercase, numbers are fine AFTER the first character.  It matters more when you have multiple computers and the hostname is used for some security checks.

I know that the CWD is the $HOME.  The ~ says that.  $HOME == /home/sam/ == ~/  == ~sam/   Those are all the same, for this userid.

Lots of these details are covered in basic, beginning, Linux books and classes.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a reasonable, no-hassle, PDF available in multiple languages.

Anyways, for the plex storage, there are a few things I would do.
[LIST]
[*]Use Linux file systems not NTFS
[*]mount the storage using the fstab, don't use point-n-clock mounting
[*]If you want Plex to be able to delete content, then add *sam* to the Plex group and make the group for all Plex media be "*plex*" with write permissions on the directories. To make life easier, I'd set the "set-gid bit" on all those directories so "plex" will be the default group as new files or directories are created.  Can't do that with NTFS.
[*]If you don't want Plex to be able to delete content, then let "other" only have read access - that the ugo permissions.  Leave the media files owned by your userid and your group.  Basically you want 775 for the directories and 664 for files.
[/LIST]
If the Plex storage is NTFS, it is much harder.

---

### Post by 1clue on 2019-07-10
Pretty much what others have said, only I would replace "basic understanding" with "clear understanding" any time you intend to change permissions on a system-installed file.

I've been using Linux both personally and professionally since 1995. I have played the permissions game, and learned not to. At this point I see very few instances where even a single system-installed file needs to have its permissions changed unless the documentation specifically tells you to. Which it won't, unless you're copying a system-supplied demo configuration to a "hot" location and building a config file, or something like that.

You may have issues with permissions on an NFS mount or similar, that is taken care of in the mount command itself.

---

### Post by delaposse on 2019-07-10
thanks for the information. Ive already done a fresh installation and i think that has solved the security issue. When i ran those commands my output was different. I had my host name like that because that was what linux inputted after i made the user name. Ive changed that now. I'm currently using the exfat file system and i mounted the hdd with fstab initially. Is the method of mounting my drive at /disks a security risk? im not sure how to go about these if the first is different from the way its detailed on the plex website:

> 

[LIST]
[*]mount the storage using the fstab, don't use point-n-clock mounting 
[*]If you want Plex to be able to delete content, then add sam  to the Plex group and make the group for all Plex media be "plex" with  write permissions on the directories. 
[*]If you don't want  Plex to be able to delete content, then let "other" only have Read  access. Leave the media files owned by your userid and your group. 
[/LIST]


---

### Post by The Cog on 2019-07-10
You are backing up to exfat??? Don't!
Exfat cannot store Linux file properties and permissions. It doesn't generally matter for user data, but for system files, your restore won't work.
I recommend using ext4 though any proper Linux compatible filesystem will do.

---

### Post by TheFu on 2019-07-10
Each of our setups is about trade-offs.  exFAT is a trade-off that I wouldn't make, but perhaps you don't have any choice for very good reasons

I wouldn't use a non-Linux file system for Plex storage.  exfat is non-Linux, just like NTFS or FAT32.  There are complications when using non-Linux file systems that are easily avoided.  They use slow drivers for access. They don't support native permissions, especially exFAT and FAT32.  NTFS can be coaxed into having some permissions and there are mount options to make it perform a little better, but it won't be near the performance for a kernel mount. The loss of user, group, permissions and ACLs is the real problem for non-Unix file systems.  That matters to Plex, but it matters much more for backup storage.

I've been burned by GUIs.  Just use ext4 if you don't have a specific reason NOT to use it. Life will be so much easier.

I find many of the Plex Forums and website suggestions to be *the easiest to explain*, not the best answers. They found something that works and seems easy.  To me, there is a difference between "working" and "what is optimal" for performance, security, useability.

---

### Post by delaposse on 2019-07-10
Im not backing up my linux system with exfat, im using it for my media and some large files. The system is backed up on and NTFS usb.

---

### Post by TheFu on 2019-07-10
> **delaposse said:**
> Im not backing up my linux system with exfat, im using it for my media and some large files. The system is backed up on and NTFS usb.

Same issues.  Non-Linux file systems introduce issues that would be trivial to solve for native file systems.  NTFS is a poor backup target file system for most Linux backups because it doesn't retain userid, group, permissions or ACLs.  Without those, you cannot expect to restore to a working system.

But if you don't have any choice, then you don't have any choice.  The only way for most people to control permissions on non-Linux file systems is through mount options.  chmod, chown DO NOT WORK.

---

### Post by delaposse on 2019-07-10
Should've know that...formatting the usb now. the reason I'm using exfat for plex is that i would like to able to use the hdd with other systems. Since its secure i think im better off using ext4. ill just keep my larger one as exfat and have those files on both. How would i perform those steps to get plex working? can you help me out?

---

### Post by The Cog on 2019-07-11
If you must use NTFS or exfat for your system backup, then you need to create a tar file rather than just copying the files across, and even that doesn't save Access Control List properties unless you use the --acls flag.

---

### Post by TheFu on 2019-07-11
> **The Cog said:**
> If you must use NTFS or exfat for your system backup, then you need to create a tar file rather than just copying the files across, and even that doesn't save Access Control List properties unless you use the --acls flag.

Or use a real backup tool that doesn't use the file system to store file metadata like permissions.  I think **duplicity** does that, but there are lots of posts here with problems using duplicity.  Usually those posts happen when they need to restore and cannot.  Best to look for failures before you select a backup tool, so you can decide if those failures are user-error, hardware-error, or tool-error.  After picking the backup tool, TEST IT!!!  Make certain you've tried it out for restoring some files from yesterday, last week and 2 months ago.  If you can't do that, then keep searching for a tool.  Also, this forces you do actually learn to use the tool for the most important part BEFORE you need it.  **The restore.**  Backups are worthless without a good restore.

**gnutar** wasn't designed to be used for storing huge files like backups in this age.  Tar was designed for use when HUGE was 250MB <---- MB!!!!, not GB.  If you wouldn't use a ZIP file, then don't use Tar.  That's my rule of thumb.  Obviously, there are different opinions.  I've used tar to actually perform tape backups in the 1990s and to move source code around more recently.

I specifically use native-Linux file systems for my **rdiff-backup** storage to avoid all the issues that come with NOT using Linux-Native file systems, and not just for backups, but for media storage and network shared storage with Windows. rdiff-backup isn't perfect. It creates a mirror of the backup files, then every backup set version is moved forward as a mirror, while older backup sets are gzipped diff files.  It is extremely storage and network efficient, since it is based on rsync, gzip and diff.  Without the rdiff-backup tool, we can manually create any file in any backup date available.  But the most recent backup is always a mirror, so restoring it is a simple 'cp' command ... if you don't just want to use rsync or rdiff-backup tools.  rsync doesn't maintain file ownership, group, permission and ACL changes over time, whereas rdiff-backup do.  None of these tools handle huge files well, so don't expect to backup individual files 2GB and larger using them.  They will try, but fail.  rsync fails at this too. I know. I've tried.  I used rsync for a long time before using it for backups became too long and it couldn't fit the allowed backup window.  rdiff-backup is 95% faster in doing backups than rsync on a day to day basis in my use here.

I consider my flash devices, which are FAT32, to be temporary storage.  I never plan to use exFAT due to patent problems.

I have 1 NTFS HDD that is used for a video recording system here. The HW recorder supports either NTFS or FAT32, so I literally _don't have any other choice._  I pull the files off that storage ASAP and perform all processing on native-Linux storage. About once a month, the NTFS file system will become corrupt, so I have to reformat it and loose parts of the recorded video.  Temporary use only.

To share files with Windows, I use either sftp, scp, or CIFS. On Windows, WinSCP is the sftp/scp client tool.  It would be strange for me to physically connect any storage to Windows.

---

### Post by TheFu on 2019-07-11
> **delaposse said:**
> Should've know that...formatting the usb now. the reason I'm using exfat for plex is that i would like to able to use the hdd with other systems. Since its secure i think im better off using ext4. ill just keep my larger one as exfat and have those files on both. How would i perform those steps to get plex working? can you help me out?

Let's be clear about ext4.  You are calling it "secure", when all we've said is that file owner, group, permissions and ACLs are retained.  Anyone with a Linux system can connect up the disk, mount the ext4 partition and access all the files. 

If you want security, then you'll need to use encryption with a key-based or extremely long, random, passphrase unlock code.

Plex doesn't like it when storage isn't there that it expects to be there always.

---

### Post by delaposse on 2019-07-11
What i meant by secure is that i would be able to let Plex detect it without the steps i took in this link [https://forums.plex.tv/t/using-ext-ntfs-or-other-format-drives-internal-or-external-on-linux/198544](https://forums.plex.tv/t/using-ext-ntfs-or-other-format-drives-internal-or-external-on-linux/198544)  that led to my issue with permissions. Now I'm trying to figure out how  to do it with ext4 without following that method. You detailed some  steps earlier, but i have no idea how to do most of that so I'm looking  it up. I used a password on both my linux backup usb and the hdd i keep  media on for plex. It wasn't a super long + random pass, but the system  said it was strong so I'm just gonna go with that.

---

### Post by TheFu on 2019-07-11
Plex doesn't like it when storage it could access previously isn't available.  What does > I used a password on both my linux backup usb and the hdd i keep media on for plex.  mean, exactly?  Did you LUKS encrypt the storage?  Plex won't like that or any encryption, really.

Above, I provided 2 options for ext4 (or any Linux file system) permissions setup.  Did you pick one to use? Care to share which one?

We can't read your mind. ;)

---

### Post by delaposse on 2019-07-11
I was referring to the one below. I haven't put any files on the hdd yet so i can just take off the LUKS encryption. 

> **TheFu said:**
> 
Anyways, for the plex storage, there are a few things I would do.
[LIST]
[*]Use Linux file systems not NTFS 
[*]mount the storage using the fstab, don't use point-n-clock mounting 
[*]If you want Plex to be able to delete content, then add *sam* to the Plex group and make the group for all Plex media be "*plex*" with write permissions on the directories. To make life easier, I'd set the "set-gid bit" on all those directories so "plex" will be the default group as new files or directories are created.  Can't do that with NTFS. 
[*]If you don't want Plex to be able to delete content, then let "other" only have read access - that the ugo permissions.  Leave the media files owned by your userid and your group.  Basically you want 775 for the directories and 664 for files. 
[/LIST]
If the Plex storage is NTFS, it is much harder.

---

