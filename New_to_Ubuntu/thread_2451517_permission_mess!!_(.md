---
title: "permission mess!! :("
date: 2020-10-05
forum: New to Ubuntu
---

### Post by mmeir0las on 2020-10-05
hello guys,

i've been dealing with linux for a few years now, but limited myself to simple tasks.
well now i've finally given ubuntu 20.04 desktop a go, to set up a server at home.

so far what i wanted to get running, i got running. but i am not sure if security wise everything is correctly set up...

i'm running a syncthing and a jellyfin server. https lets encrypt certificate, reverse proxy with caddy was relatively easy to put in place.
i can access both services remotely over htttps.

now the difficult part - syncthing:

```
drwxrwxrwx 1 root root   4096 Sep 18 19:28 kamera_lg 
drwxrwxrwx 1 root root   4096 Okt  5 18:55 sync_important 
drwxrwxrwx 1 root root      0 Sep 17 19:35 viber_lg 
drwxrwxrwx 1 root root 188416 Okt  5 17:14 whatsapp_lg 
```

these folders are the ones being synched between devices.
these are not smb shares, and don't need to be. synching is done automatically both ways (server -> android, android -> server) over the Android app/syncthing service on ubuntu.
the folders are owned by root (which i think is not wise) and on top of that all permissions are enabled.
my question is how can i correct this without breaking the functionality of the setup?

difficult part II - jellyfin:

drwxrwxrwx 1 root root   4096 Okt  1 11:57 movies

this is a smb share, which i need permission to play movies from (works!), and upload things to from the 2 clients: android phone and windows 10 PC. 
it's always refused.


my smb.conf is:

 ```
[SECURED]

path = /media/Elements/movies
valid users = @server_group
browsable = yes
writable = yes
read only = no
```
 how can i add the 2 clients to the &#8220;allowed list&#8221;? 
would really appreciate some guidance.


i'm sorry for the inconvenience. stay safe guys

---

### Post by TheFu on 2020-10-05
drwxrwxrwx is for lazy people who don't care at all about security.

Learn Unix permissions.  Google for a tutorial, any will do. This stuff has been the same for 40+ yrs. 
Unix permissions can only be modified if the file system involved is a native Linux file system, so NTFS, vFAT, fat32, exFAT do not work.  That is a common problem for people using USB storage. They didn't bother to actually use the correct file system, so there isn't much we can do.

HTTPS is for privacy, not security. Don't confuse those.

Just because something works, that doesn't mean it is a good idea or that it is secure at all.

---

### Post by mmeir0las on 2020-10-05
TheFu... thx for the reply

i don't know what you mean by "usb storage", i am not using any of that

so u mean as soon as i give rwx permission there is no way to take those back?

i came to this forum searching for a helpful soul who could tell me a short command to remove those permissions (since all tutorial online are written in greek for noobs), and now i have to do a full linux course...

well ok. let's read for a few more weeks

thx

---

### Post by TheFu on 2020-10-05
How is /media/Elements/movies connected to the computer?  Perhaps it isn't a USB connection, but then it shouldn't be located under /media/.

There are lots of simple commands, but they only work in specific situations. They can also break things when used improperly, so I'm loath to provide them without a better understanding of the setup and the file system used.  Someone may come to find this thread in 6-29 months, not understand things, and simply grab the command and running it.  Doing so could completely trash their system.  So I'd rather be just a little cautious.

What file system does /media/Elements/movies use?  In Windows, there are perhaps 4 file systems.  In Linux, there are about 50, including the Windows choices. The "easy answer" doesn't work for Windows file systems.

> i came to this forum searching for a helpful soul who could tell me a short command to remove those permissions
You really can't remove permissions when you've already allowed everyone in the world full permissions to everything. You can restrict permissions, but how to do that depends on:
[LIST]
[*]Which file system is used.
[*]What programs/daemons need access to the files.  What type of access each program/daemon needs for each file.
[*]Which userids or groups of users need access to the files. Whether none, read-only or read-write access is needed.
[/LIST]

So, in the best case, you are using a Linux file system, only 1 userid needs read-write access to the files and only 1 daemon userid needs read-only access to the files and you don't care if every other account on the system can view all the files (also read-only access). Then we have just a few commands.  But none of those will work without a Linux file system.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is a tutorial, but really just reading that isn't sufficient to understand. Hands on effort is needed. It is a really elegant solution and applies to all the popular OSes used today, except 1.

---

### Post by mmeir0las on 2020-10-05
thx for the reply again

so i'll be more specific about my setup:

my server runs a m2 nvme SSD where Ubuntu Desktop 20.04 is installed. this SSD has the ext4 file system.
the other driver where tcontent is located is just a storage drive. a 12TB WD Nas drive. File system is NTFS.

use case:

the jellyfin server is installed on the ssd and it makes it possible for me (and people i chose e to share) to acess the library over a https gui (each user has their own username and password, of course). access to other people is giver through the that user gui.
the content is placed inside a smb share on the NAS drive, in /etc/Elements/movies. i must add that for now i don't have much content. so if it's easier to just delete this smb share and start from scratch with a new one, it's not big problem
only I have of course access to the share, over my windows PC and Android smartphone. and i really need access from those clients to place content in there.

what programs need access:

this is a difficult one but smb for once: to share the files with the other clients, so that i can then access through a file manager. and for jellyfin to be able to scrape that share. 
jellyfin which scrapes the share in order to then share the content over the https user gui.

that's about it :)

i hope this helps

---

### Post by TheFu on 2020-10-06
Looks like jellyfin is a media server of some sort, similar to plex?  Does it run with a specific userid?  That userid needs access to the files.  Do you use it to manage the media as well?  Want to add files and delete files through jellyfin?  Then that userid needs read-write access to the files.

It is unclear to me what each directory already shown has to do with jellyfin.  Rather than explain, please running commands and post the command and the output here with a very short description. For example, on my plex server, 
```
drwxrwsr-x 1303 thefu   plex 61440 Oct  4 18:57 M/
```
That's a directory which contains movies and is managed by plex.  Note the permissions.  My userid is the owner, plex is the group, and the group has read-write access.  The 's' is the setgroupid permission bit. This forces any new files or directories created under the "M" directory to also use the plex group.  My userid, thefu, is a member of the plex group too. Without that, this setup doesn't work.  

None of this storage on my plex server is NTFS for many reasons, but mainly because NTFS doesn't support chown, chrgrp and chmod commands.  Those are required for a setup like this.  I've posted in these forums how-to "working together" a few times. It has the commands and examples to learn in a test directory:
[https://ubuntuforums.org/showthread.php?t=2382965](https://ubuntuforums.org/showthread.php?t=2382965)
None of this works on NTFS.  That is a different problem.

Anyways, if I wanted to go from 
```
a: drwxrwxrwx 1303 root    root 61440 Oct  4 18:57 M/
```
to
```
b: drwxrwsr-x 1303 thefu   plex 61440 Oct  4 18:57 M/
```

I would use these exact commands:
```

# Change ownership to myself for all files and directories recursively
sudo chown -R thefu M

# Change the group to plex for all files and directories recursively
chgrp -R plex M

#  Keep execute permissions only if they already exist; fix other permissions 
chmod -R u=rwX,g=rwX,o=rX M    

# to force all subdirectories to get the setgid permission, but not files.
find M -type d -exec chmod  g+s {} \;   

```
These are very dangerous and assume that M is a subdirectory of the current directory where I am running these commands. If I run these in the wrong directory, I can break a working Unix/Linux system so it will not boot again. DO NOT RUN if you do not understand these risks and aren't 100% positive it is safe for the CWD/PWD.  The command with sudo is the most dangerous.

Having 'root' be the owner is not optimal for data files.  We shouldn't need to use root or sudo very often in the daily operation of our systems.  That should only be needed when doing administrative tasks, like installing or removing software or when setting up new storage mounts.

You may note that I didn't mention samba at all.  I don't use it very often and not at all on my plex server. I only have 1 Windows machine and never use it with Plex. It just isn't the way that I work, but we are different people and if you need samba, then you need samba.

For NTFS permissions, those can only be controlled through mount options. All files, all directories within the same file system get the same permissions. You can control the owner and group too, but only through file system mount options. These are lost when the storage is disconnected.  IMHO, the best answer is to change from NTFS to EXT4. If you have backups, this isn't a big deal. There is no "conversion" tool.  It is a wipe and format then mount problem. The good news is that ext4 storage is about 30% faster than NTFS on a Linux system.  The bad news is that if your backup storage is also NTFS, then all the permissions will be lost. Not much we can do about that, besides suggest switching to ext4 for the backup storage too.

BTW, I scanned some info about Jellyfin and like what I see so far.  I may switch. Thanks!

If you need more background about users, groups, permissions, then this free book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has explanations.  Permissions on files and directories are central to all Unix security. 1 tiny mistake with those and things break or hackers have complete control over the system.

I truly hope this is useful and helpful. I fear it is not.

---

