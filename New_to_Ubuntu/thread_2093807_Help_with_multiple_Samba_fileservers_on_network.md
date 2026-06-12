---
title: "Help with multiple Samba fileservers on network"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by hollywoodpete on 2012-12-11
I week ago I had a perfectly functional network with several Samba fileservers and clients all working happily together. After a power surge and outage and a couple of updates, my network is a mess. I tried Gadmin-samba to salvage my system and it became completely non-functional. I removed the Gadmin-samba and am now slowly trying to get the network shares working again. Nautilus only recognizes some of the computers on the network but not all of them. Nautilus doesn't connect to the network at all on some of the clients but I can get to the share with smb://workgroup/server.

My first question is:  Does Samba server need to be running on each computer with Samba shares and if it does, does each computer need its own smb.conf file?

---

### Post by redmk2 on 2012-12-11
> **hollywoodpete said:**
> I week ago I had a perfectly functional network with several Samba fileservers and clients all working happily together. After a power surge and outage and a couple of updates, my network is a mess. I tried Gadmin-samba to salvage my system and it became completely non-functional. I removed the Gadmin-samba and am now slowly trying to get the network shares working again.
Gadmin-samba trashes the configuration file on every host it is installed on.> 
 Nautilus only recognizes some of the computers on the network but not all of them. Nautilus doesn't connect to the network at all on some of the clients but I can get to the share with smb://workgroup/server.
The proper form is //SERVER_NAME/share_name.  I don't see what the workgroup would be for.> 
My first question is:  Does Samba server need to be running on each computer with Samba shares and if it does, does each computer need its own smb.conf file?

Any host that is serving files needs to be up and have a correctly configured smb.conf to operate.  The smb.conf file configures the smbd and nmbd daemons (processes).  In fact any host that uses Samba for file sharing (either server or client) uses the smb.conf file for configuration.

---

### Post by hollywoodpete on 2012-12-11
> **redmk2 said:**
> Gadmin-samba trashes the configuration file on every host it is installed on.The proper form is //SERVER_NAME/share_name.  I don't see what the workgroup would be for.]

My mistake. I'm still learning


[Any host that is serving files needs to be up and have a correctly configured smb.conf to operate.  The smb.conf file configures the smbd and nmbd daemons (processes).  In fact any host that uses Samba for file sharing (either server or client) uses the smb.conf file for configuration.

Thanks. That make sense and is the way I set it up.

On my main fileserver I have all the shares set up the same but one of the files show a mounting error. I will attach the smb.conf file

---

### Post by hollywoodpete on 2012-12-11
[More Movies]
    path = /media/sdd1/More Movies
    writeable = yes
;    browseable = yes
    guest ok = yes

[Shared Movies]
    path = /media/sdb1/Shared Movies
    writeable = yes
;    browseable = yes
    guest ok = yes

[Training videos]
    path = /media/sdd1/Training videos
    writeable = yes
;    browseable = yes
    guest ok = yes

[Music]
    path = /media/sdd1/Music
    writeable = yes
;    browseable = yes
    guest ok = yes

[complete]
    path = /home/movieman/Downloads/complete
    writeable = yes
;    browseable = yes
    guest ok = yes

[Music videos]
    path = /media/sdd1/Music videos
    writeable = yes
;    browseable = yes
    guest ok = yes

[TV]
    path = /media/Time Machine/TV
    writeable = yes
;    browseable = yes
    guest ok = yes



All of the shares are accessable except the [TV] shares.

---

### Post by redmk2 on 2012-12-11
> **hollywoodpete said:**
> [More Movies]
    path = /media/sdd1/More Movies
    writeable = yes
;    browseable = yes
    guest ok = yes

[Shared Movies]
    path = /media/sdb1/Shared Movies
    writeable = yes
;    browseable = yes
    guest ok = yes

[Training videos]
    path = /media/sdd1/Training videos
    writeable = yes
;    browseable = yes
    guest ok = yes

[Music]
    path = /media/sdd1/Music
    writeable = yes
;    browseable = yes
    guest ok = yes

[complete]
    path = /home/movieman/Downloads/complete
    writeable = yes
;    browseable = yes
    guest ok = yes

[Music videos]
    path = /media/sdd1/Music videos
    writeable = yes
;    browseable = yes
    guest ok = yes

[TV]
    path = /media/Time Machine/TV
    writeable = yes
;    browseable = yes
    guest ok = yes



All of the shares are accessable except the [TV] shares.
I beg to differ.  :-)

The path is different.  I'll bet the permissions along that path are restricting you.  The directories need to have the eXecute bit set for your user or group for you to enter or traverse the directory.

---

### Post by hollywoodpete on 2012-12-12
"the directories need to have the **eXecute bit** set"


I am lost on this point. I guess I thought if it mounted in media, it would be shared. 

FWIW the drives that share fine are NTFS. The drive I am having a problem with is ext4. My network is really all linux so if there is a better way to mount the ext4 drive to share I am open for suggestions. My goal is to have it available to xbmc devices.

---

### Post by hollywoodpete on 2012-12-12
I changed the way the HD mounts but still am not able to access it.

smb.conf
[Music videos]
    path = /media/sdd1/Music videos
    writeable = yes
;    browseable = yes
    guest ok = yes

[TV]
    path = /media/sdc1/TV
    writeable = yes
;    browseable = yes
    guest ok = yes

---

### Post by Morbius1 on 2012-12-12
> **redmk2 said:**
> I'll bet the permissions along that path are restricting you. 
@hollywoodpete, Post the output of these 2 commands to see if you have to pay up on redmik2's bet:
```
ls -al /media/sdd1
``````
ls -al /media/sdc1
```

---

### Post by hollywoodpete on 2012-12-12
[ls -al /media/sdd1]
total 188
drwxrwxrwx 1 root root  16384 Sep 28 06:57 .
drwxr-xr-x 6 root root   4096 Dec 12 07:00 ..
drwxrwxrwx 1 root root      0 Apr  8  2012 Books
-rwxrwxrwx 1 root root  12292 Apr 18  2012 .DS_Store
drwxrwxrwx 1 root root   4096 Dec 18  2011 Family avis
drwxrwxrwx 1 root root  20480 Dec  6 15:35 More Movies
drwxrwxrwx 1 root root 114688 Dec  8 09:04 Music
drwxrwxrwx 1 root root   4096 Dec  8 09:24 Music videos
drwxrwxrwx 1 root root   8192 Oct 28 18:54 Photos
drwxrwxrwx 1 root root      0 Jan 10  2010 Stand-up Comedy
drwxrwxrwx 1 root root   4096 Jan 14  2012 Training videos
drwxrwxrwx 1 root root      0 Sep 27  2011 .Trash-1000

---

### Post by hollywoodpete on 2012-12-12
[ls -al /media/sdc1]
total 36
drwx------  6 movieman movieman  4096 Jul  7 23:36 .
drwxr-xr-x  6 root     root      4096 Dec 12 07:00 ..
drwxrwxr-x  2 movieman movieman  4096 Jul 13 17:36 Downloads
drwx------  2 root     root     16384 Jun 24 22:17 lost+found
drwx------  5 movieman movieman  4096 Jul  6 19:53 .Trash-1000
drwxrwxrwx 34 movieman movieman  4096 Dec  8 22:00 TV

---

### Post by redmk2 on 2012-12-12
> **hollywoodpete said:**
> [ls -al /media/sdc1]
total 36
drwx------  6 movieman movieman  4096 Jul  7 23:36 .
drwxr-xr-x  6 root     root      4096 Dec 12 07:00 ..
drwxrwxr-x  2 movieman movieman  4096 Jul 13 17:36 Downloads
drwx------  2 root     root     16384 Jun 24 22:17 lost+found
drwx------  5 movieman movieman  4096 Jul  6 19:53 .Trash-1000
drwxrwxrwx 34 movieman movieman  4096 Dec  8 22:00 TV

What I was referring to is that every directory in the path must have an executable bit set for you as a user or as either group that you are a member of, or as a last resort the entity called *others*.

If you wish to check a directory specifically (e.g. /media/sdc1) then you chould use this ```
ls -ld /media/sdc1
```
FYI -- This information is implied with the directory . (dot), which is the current working directory (CWD).  It shows that the CWD is only available to the user *movieman* (no group or other permissions).  

Are you the user *movieman*?  Do you have a Samba user named movieman?  You have restricted the directories (and the files?) to that user only.  If you do that you need to authenticate as that user in Samba.  The underlying Linux permissions trump Samba rights at all times.

I don't think we know the whole story here.  Enlighten us please as to why you have changed this directories permissions for this share.

We need to know the user and the Samba user.  Do you have any other users that will need to access the share?  Remember that some applications create their own system user that will need to access the directory also.

You are not alone as a user on the machine.  :-)  To see all the users try this command from the terminal```
getent passwd
```

---

### Post by hollywoodpete on 2012-12-12
I am the only user of the computer. I have root access. To the best of my knowledge I have not restricted the files to movieman and if I have, I would like to know how to remove that restriction.

---

### Post by redmk2 on 2012-12-12
> **hollywoodpete said:**
> I am the only user of the computer. I have root access. To the best of my knowledge I have not restricted the files to movieman and if I have, I would like to know how to remove that restriction.

I'm not referring to you the human being.  When I use the term user in this context, I'm referring to either a logged in user (name) or a system user that does not log in, but that is spawned by an application.

What is you login name (the username)?  If you are not the user **[COLOR="Red"]movieman[/COLOR]**, I wonder what application did this 

```
[ls -al /media/sdc1
total 36
drwx------ 6 **[COLOR="Red"]movieman movieman[/COLOR]** 4096 Jul 7 23:36 .
drwxr-xr-x 6 root root 4096 Dec 12 07:00 ..
drwxrwxr-x 2 **[COLOR="Red"]movieman movieman[/COLOR]** 4096 Jul 13 17:36 Downloads
drwx------ 2 root root 16384 Jun 24 22:17 lost+found
drwx------ 5 **[COLOR="Red"]movieman moviema[/COLOR]**n 4096 Jul 6 19:53 .Trash-1000
drwxrwxrwx 34 **[COLOR="Red"]movieman movieman[/COLOR]** 4096 Dec 8 22:00 TV
```

I think it would be useful for us to clear this up before we change anything at this point.  We could just change it, but I suspect **[COLOR="Red"]movieman[/COLOR]**  will reappear in the future.

---

### Post by hollywoodpete on 2012-12-12
My username is movieman. My computer is also named movieman.

I don't want to sound like I know what I am doind, but I think you were right about the way the drives are being mounted. The 2 drives that are formated as NTFS work fine but the permission problem may be coming from the way the EXT4 drive is being mounted? I hope this helps. I am lost

---

### Post by hollywoodpete on 2012-12-12
getent passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:104::/var/run/dbus:/bin/false
colord:x:103:108:colord colour management daemon,,,:/var/lib/colord:/bin/false
lightdm:x:104:111:Light Display Manager:/var/lib/lightdm:/bin/false
whoopsie:x:105:114::/nonexistent:/bin/false
avahi-autoipd:x:106:117:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:107:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:108:46:usbmux daemon,,,:/home/usbmux:/bin/false
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:110:119:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:111:122:RealtimeKit,,,:/proc:/bin/false
saned:x:112:123::/home/saned:/bin/false
speech-dispatcher:x:113:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
hplip:x:114:7:HPLIP system user,,,:/var/run/hplip:/bin/false
movieman:x:1000:1000:movieman,,,:/home/movieman:/bin/bash
debian-transmission:x:115:126::/home/debian-transmission:/bin/false
sshd:x:116:65534::/var/run/sshd:/usr/sbin/nologin

---

### Post by redmk2 on 2012-12-12
> **hollywoodpete said:**
> My username is movieman. My computer is also named movieman.

As long as you can keep the user name (your login) separate in your mind from that of the hostname (your computer) I guess it's okay.  Did you create a Samba user account (smbpasswd -a) for movieman (the login)?

---

### Post by redmk2 on 2012-12-12
> **hollywoodpete said:**
> ```
getent passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:104::/var/run/dbus:/bin/false
colord:x:103:108:colord colour management daemon,,,:/var/lib/colord:/bin/false
lightdm:x:104:111:Light Display Manager:/var/lib/lightdm:/bin/false
whoopsie:x:105:114::/nonexistent:/bin/false
avahi-autoipd:x:106:117:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:107:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:108:46:usbmux daemon,,,:/home/usbmux:/bin/false
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:110:119:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:111:122:RealtimeKit,,,:/proc:/bin/false
saned:x:112:123::/home/saned:/bin/false
speech-dispatcher:x:113:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
hplip:x:114:7:HPLIP system user,,,:/var/run/hplip:/bin/false
movieman:x:1000:1000:movieman,,,:/home/movieman:/bin/bash
debian-transmission:x:115:126::/home/debian-transmission:/bin/false
sshd:x:116:65534::/var/run/sshd:/usr/sbin/nologin
```

I don't really need this data.  It was for you to look over.   If you are going to post any data you should post it enclosed in [code] [ /code] blocks so it is formatted.  It's easier to read that way.  There is a **[SIZE="3"]#[/SIZE]** icon at the top of the editor that will provide the [code] brackets.

---

### Post by hollywoodpete on 2012-12-12
> **redmk2 said:**
> As long as you can keep the user name (your login) separate in your mind from that of the hostname (your computer) I guess it's okay.  Did you create a Samba user account (smbpasswd -a) for movieman (the login)?

No. I have one samba username "nighthawk" (don't laugh)
I did check the permissions of the drives using "disk utility" and saw that the problem drive is owned by a group called movieman. I would love to have it in the root group

---

### Post by redmk2 on 2012-12-12
> **hollywoodpete said:**
> No. I have one samba username "nighthawk" (don't laugh)
I did check the permissions of the drives using "disk utility" and saw that the problem drive is owned by a group called movieman. I would love to have it in the root group

I know it seems like a lot of questions, but it's important.  Is the HDD that holds the partition an external USB drive that you just plug in and it mounts?

Post the output of this```
sudo fdisk -l
```

...and post the output of this```
cat /etc/fstab
```

---

### Post by hollywoodpete on 2012-12-12
[CODE][/sudo fdisk -l]
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003801d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   155258879    77628416   83  Linux
/dev/sda2       155260926   156301311      520193    5  Extended
/dev/sda5       155260928   156301311      520192   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90cd1e4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e290bcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   976768064   488384001    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c03c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1953520064   976760001   83  Linux

---

### Post by hollywoodpete on 2012-12-12
[CODE][/# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid        0  0  
# / was on /dev/sda1 during installation
UUID=77fcc4a1-beec-4cc9-98c4-44ca331495c2  /            ext4  errors=remount-ro          0  1  
# swap was on /dev/sda5 during installation
UUID=4ffe8dbe-15db-4b06-b14a-e185f842d5f9  none         swap  sw                         0  0  
/dev/sdb1                                  /media/sdb1  ntfs  nls=iso8859-1,umask=000    0  0  
/dev/sdd1                                  /media/sdd1  ntfs  nls=iso8859-1,umask=000    0  0  
/dev/sdc1                                  /media/sdc1  ext2  errors=remount-ro,ro,user  0  0  
]

---

### Post by hollywoodpete on 2012-12-12
There are 4 internal drives on the computer. One drive for the the OS and 3 drives for media. I also would like to be able to read/write on the drives. I realize now that part of my problem probably came from using the Storage Device Manager "pysdm" to get the drives to automount.

---

### Post by redmk2 on 2012-12-13
> **hollywoodpete said:**
> There are 4 internal drives on the computer. One drive for the the OS and 3 drives for media. I also would like to be able to read/write on the drives. I realize now that part of my problem probably came from using the Storage Device Manager "pysdm" to get the drives to automount.

...and the plot further thickens.  :-)

After  Gadmin-samba, "psydm" is the most dangerous (destructive) application out there.  I know Morbius1 feels the same way. Please tell me you don't use Webmin too.

I want to think about the best course of action for you.  It's getting late here.  So I will follow up tomorrow.

Why do you have a NTFS partitions on a Linux host?

---

### Post by hollywoodpete on 2012-12-13
> **redmk2 said:**
> ...and the plot further thickens.  :-)

After  **Gadmin-samba, "psydm"** is the most dangerous (destructive) application out there.  I know Morbius1 feels the same way. Please tell me you don't use **Webmin** too.

I want to think about the best course of action for you.  It's getting late here.  So I will follow up tomorrow.

Why do you have a NTFS partitions on a Linux host?

Ironically those 3 programs are suggested for easy management for beginners. I have thought about webmin and have played around with it, but do not use it. The files are on NTFS drives because I started with WIN 2003 server. I changed to Ubuntu 9.10 and simply plugged the drives in and they worked fine. I have been very happy until now so I haven't bothered trying to move 1 TB of data off each drive to a storage drive. Do the re-format. And then move the data back. I am working on a RAID file-server that could handle the back-up but it is not up and running yet.

---

