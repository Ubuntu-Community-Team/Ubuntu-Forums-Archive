---
title: "No mount NAS share in fstab. Did I do something wrong?"
date: 2021-10-09
forum: New to Ubuntu
---

### Post by katana-9988 on 2021-10-09
Hi guys. I am have a Synology NAS and want to open the share mount using fstab. I followed  the documentation of Ubuntu for fstab and I cant seem to get it right.

```

//greenpy.local/Ahmed /home/ahmed/Desktop/NAS_Ahmed cifs credentials=/etc/samba/nas_credentials, uid=1026,gid=100  0  0
# //greenpy.local/Download
//greenpy.local/Download /home/ahmed/Desktop/NAS_Download cifs credentials=/etc/samba/nas_credentials, uid=1026,gid=100  0  0
# //greenpy.local/Media
//greenpy.local/Media /home/ahmed/Desktop/NAS_Media cifs credentials=/etc/samba/nas_credentials, uid=1026,gid=100  0  0

```

But I got the following error when I try to open dolphin.

An  error occurred while accessing '/home/ahmed/Desktop/NAS_Media', the  system responded: mount: /etc/fstab: parse error at line 15 -- ignored
mount: /etc/fstab: parse error at line 17 -- ignored
mount: /etc/fstab: parse error at line 19 -- ignored
mount: /home/ahmed/Desktop/NAS_Media: can't find in /etc/fstab.

Please advise me and thank you. 						  						  						  						 					  					 						 							 									[ 										]("https://forum.kde.org/posting.php?mode=quote&f=225&p=449463")

---

### Post by TheFu on 2021-10-09
Some tips:
a) do not mount storage directly under any Userid's HOME.  Trust me. This is a terrible idea.
b) use NFS, not CIFS, if the NAS supports NFS.
c) mount options cannot have any spaces.  None. Zero.  The only allowed separator is a , (comma), not a space.

That should be enough to get started.  If course, you CAN do anything you like, but then you'll learn the hard way, instead of from the experience of others.

If you use snaps, then you'll probably want to mount the NFS shares under /media/nfs/.... somewhere.

---

### Post by Morbius1 on 2021-10-09
> //greenpy.local/Ahmed /home/ahmed/Desktop/NAS_Ahmed cifs credentials=/etc/samba/nas_credentials, uid=1026,gid=100  0  0

There is a space between [highlight]credentials=/etc/samba/nas_credentials,[/highlight] and [highlight]uid=1026[/highlight]. I'm fairly certain that is the "parse" error. Remove the space.

Speaking of spaces there should be no spaces in your credentials file either although you would get a different error. So this is good:
```
username=xxxxx
password=yyyyy
```
This is bad:
```
username = xxxxx
pasword = yyyyy
```

One more thing about cifs: It automatically negotiates with the server ( NAS in this case ) the best smb dialect to use between the values of SMB2.1 and SMB3.x. Depending on how up to date your synology software is it may need to be told to allow SMB2/3 for this to work:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289255&stc=1[/IMG]

[COLOR=#0000ff][I]One more thing - and this is more of a gee-whiz thing - but right below that setting is a reference to WS-Discovery. I would suggest enabling that as well:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289256&stc=1[/IMG]

That allows the nas to be discoverable to Win10 using Windows replacement for NetBIOS. It has nothing to do with this question but since you are using Dolphin it has a ws-discovery client built in which you might find interesting. Someday Gnome might have such a thing but it needs to understand the whole samba thing first.[/I][/COLOR]

---

### Post by Tadaen_Sylvermane on 2021-10-09
You have a space at the uid. No spaces.

---

### Post by katana-9988 on 2021-10-10
I copied this from ubuntu documentation 

```

# NFS
Server:/share  /media/nfs  nfs  rsize=8192 and wsize=8192,noexec,nosuid
# "Server" = Samba server (by IP or name if you have an entry for the server in your hosts file
# "share" = name of the shared directory

```

If I translate this for my need. But not sure from the rest of the information?

Server:/greenpy.local/Ahmed /home/ahmed/Desktop/NAS_Ahmed nfs rsize=???? and wsize=????,noexec,nosuid

And for my Synology. I got DS22+ with update DSM 7 and the NFS that I have is NFSv3, NFSv4 and NFS4.1.

Please advise me and thank you.

---

### Post by TheFu on 2021-10-10
Appears the manual you referenced was old.
rsize and wsize haven't been needed for 15 yrs.  They've been self optimized since NFSv4 was released long, long, long, ago.

Here's what I use in my NFS mounts.
```
istar:/d/D1     /d/D1 nfs  nconnect=4,proto=tcp,intr,rw,async   0    0
```
My nfs server is "istar", but that could be an IP address if you don't have an internal DNS.

For data only (i.e. no programs), then the noexec is ok as an option. nosuid shouldn't be required, since root on a client machine isn't root on the server in default NFS servers and hasn't been since at least the early 1990s.  The client "root" account should be translated to "nobody" automatically, but perhaps on the Synology NAS they don't do that?  It wouldn't hurt to add the nosuid option.

So if we put it all together, this should work:
```
greenpy.local[COLOR="#FF0000"]:/[/COLOR]Ahmed [COLOR="#FF0000"]/media[/COLOR]/NAS_Ahmed    [COLOR="#FF0000"]nfs[/COLOR]      nconnect=4,proto=tcp,intr,rw,async,noexec,nosuid    0     0
```

Assuming the Synology is already running NFS, make the change, restart the NFS server daemon to pick up the new change, then put that line into your fstab and run 
```
sudo mkdir -p /media/NAS_Ahmed
sudo systemctl daemon-reload
sudo mount -a

```
If you have **nfs-common** APT package installed, that should mount any non-mounted storage in the /etc/fstab.  Try **cd /media/NAS_Ahmed** - does it work?  Does **df -Th** show the nfs mount? Something like this?
```
 Filesystem                      Type      Size  Used Avail Use% Mounted on
istar:/d/D1                     [COLOR="#FF0000"]nfs4[/COLOR]      3.5T  3.5T   19G 100% /d/D1
```

At each reboot, the NFS line(s) will automatically be mounted. No commands needed, but the NFS server must be up and available.  If it isn't it will complain in the logs. There are options to let the boot continue.  I use a subsystem called autofs - this uses the Unix automounterd under the covers and mounts selected storage when it is requested and umounts NFS storage when it isn't used any more. The mounts are there only when needed.  I use it for USB storage too. autofs is a little weird. There is a systemd version that mostly works. I played with it about a year ago, but it didn't behave the same, so I ran back to autofs. [Https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](Https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156) has an example for NFS and cifs. The CIFS options get pretty long.

From that point on, the NFS storage is managed exactly like native, local, attached, storage, with chown. chgrp and chmod.  The only caveat is that root doesn't have control. To change ownership under NFS, we have to do that from the NFS server itself.  With NFS, it is all about the uid and gid - the numbers.  Use 'id' command to see the numbers for any user.  When you have multiple clients, ensure the uid/gid numbers match across each client for the files controlled by users.
With Linux, the first user created during install almost always has a uid=1000 and a gid=1000, so if you have 2 or 50 or 500 NFS clients, whatever userid on a client system maps to uid=1000 and gid=1000 will see those files as owned by their user from their client.  As more users are added, uids 1001, 1002, 1003, .... get added.  Keep those mapped 1-for-1 on each system if they will have NFS access on the system.  NFS is system-to-system access, not like CIFS which users a credentials file (user-to-system).

---

