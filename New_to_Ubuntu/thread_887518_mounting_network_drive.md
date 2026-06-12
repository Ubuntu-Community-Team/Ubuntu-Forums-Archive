---
title: "mounting network drive"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2008-08-12
Hi,
I have a networked file server on my LAN that I want to mount with Ubuntu.
I have managed to do this in Places>Connect to server> then filling out the info here. Though I am not sure how it happens or it does not work every time. Hard to say.
Also I can say that after a restart, connection to the server is gone.

How can I do this and keep these settings. Can someone please help me?

INFO
File server is a Synology 106e
HDD in file server is one NTFS partition.

---

### Post by cmnorton on 2008-08-12
How are you mounting this network drive?

My nfs connection survives reboots, because I have a line in /etc/fstab like this

backupm:/data/dbexport  /drserver nfs     rsize=8192,wsize=8192,timeo=14,intr

and /etc/exports on the server (backupm) hosting the share needs to have

/data/dbexport           remote_server(rw,sync,no_root_squash)

---

### Post by mlentink on 2008-08-12
> **steinzeitmensch said:**
> INFO
File server is a Synology 106e
HDD in file server is one NTFS partition.

I'm assuming this is some NAS drive?
You should be able to permanently mount such a drive with an entry in /etc/fstab, like:
```
//server_name/share_name /path_to/mount_point cifs username=server_user,password=server_password,_netdev,uid=client_username,gid=users 0 0
```
You might have to change the server_name for the IP-adress

seea also: [http://www.thelinuxvault.net/wiki/Mount_CIFS_shares](http://www.thelinuxvault.net/wiki/Mount_CIFS_shares) and [http://ubuntuforums.org/showthread.php?t=288534&page=25](http://ubuntuforums.org/showthread.php?t=288534&page=25)

---

### Post by steinzeitmensch on 2008-08-12
can you please tell me what each of the elements of this string are. I am not sure about some of them and i know this much that if I have just one tiny mistake here it simply will not work and I will chase my tail for hours trying all sorts of combinations.

```
//server_name/[COLOR="Red"]share_name[/COLOR] /[COLOR="Red"]path_to[/COLOR]/[COLOR="Red"]mount_point[/COLOR] cifs username=server_user,password=server_password,_netdev,uid=client_[COLOR="Red"]username[/COLOR],gid=users 0 0
```

So I assume server_name is the IP address on the LAN of the file server
share_ name ?
path_to ?
Mount point ?  (is this a folder that exists on the server? If so how do I write the path for this?)
username (i assume this is my local user account (not root)

---

### Post by mlentink on 2008-08-12
> **steinzeitmensch said:**
> 

```
//server_name/[COLOR="Red"]share_name[/COLOR] /[COLOR="Red"]path_to[/COLOR]/[COLOR="Red"]mount_point[/COLOR] cifs username=server_user,password=server_password,_netdev,uid=client_[COLOR="Red"]username[/COLOR],gid=users 0 0
```

So I assume server_name is the IP address on the LAN of the file serverCorrect
> **steinzeitmensch said:**
> share_ name ?Is the name of the windows share on that machine, a directory on that disk
> **steinzeitmensch said:**
> path_to ?
Mount point ?  (is this a folder that exists on the server? If so how do I write the path for this?)This is the path to the mountpoint (a directory which you create in /mnt, as you have been shown in an earlier question, e.g. '/mnt/mymusic')> **steinzeitmensch said:**
> 
username (i assume this is my local user account (not root)Yes. This gives your local user access rights to the share


Hope this clarifies a bit. Please note that this is very similar to permanently mounting local drives/partitions, which you asked about earlier. And I guess you also see the difference with windows. In linux, you add drives to your filesystem, as many as you want, whether they are local or networked. Neat, huh?

---

### Post by steinzeitmensch on 2008-08-12
This is what I have entered into the fstab, but it does not work at the moment. Can you see anything wrong here:

```

//192.168.1.25/music /mnt/music cifs username=alex2,password=**********,_netdev,uid=alex,gid=users 0 0
```

alex2 is the user on the server
****** is the password on the server for the user

When I do a mount -a as root in termainal this is what I get:

```
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
mount error: can not change directory into mount target /mnt/netBackup
```

please note that I have 5 entries in the fstab file hence the 5 errors. I just give one of the entries above as an example of what I entered.

any hints?

---

### Post by mlentink on 2008-08-12
I'll check how I did it when I get back home (I'm at work at the moment) so bear with me...

Edit: Just a quick question: share_name is really that. In the administration of your NAS-drive, you were probably able to designate a sharename to a specific directory on that drive. Did you use the share-name or the name of the directory? (in windows too, you can share a directory under a descriptive name of sorts.)

---

### Post by steinzeitmensch on 2008-08-12
Not sure how to interpret your answer.
> administration of your NAS-drive
What exactly are you talking about here? :confused:

---

### Post by steinzeitmensch on 2008-08-14
Hi,
Is there anyone who could help me out on this problem please. I know I am close, but I seem to be stumbling over the same mistake(s) again and again.

please help someone:-

---

### Post by mlentink on 2008-08-19
Last time I did it, I followed this:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

Sorry, I should have checked, but got caught up in quite a few other things...

---

### Post by steinzeitmensch on 2008-08-22
I am working abroad and will not have a chance to try this out until I get back home.
Thanks for the link. I hope it helps

---

### Post by steinzeitmensch on 2008-09-22
I seem to have made some progress in my quest toward mounting a NAS drive, but I am still not quite there.

At the moment my fstab.conf looks like this:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=32cd1a76-a146-4f6a-af1c-f29d4c99b85e / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=90757b6e-79c4-410d-b439-1e3cb23f083e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# Entry for /dev/sda4 :
UUID=2b63b6fb-c4d1-41a0-a3ca-da869a845c06 /mnt/disk1 ext3 relatime 0 2
# Entry for /dev/sda3 :
UUID=4ab5846c-fb01-47b5-99f5-608835af5178 /mnt/disk2 ext3 relatime 0 2
[COLOR="Blue"][COLOR="RoyalBlue"]# Entry for NAS Video foler:
//192.168.1.25/video /mnt/video cifs username=*****,password=*****[/COLOR]
# Entry for NAS Music foler:
//192.168.1.25/music /mnt/music cifs username=*****,password=*****
# Entry for NAS public foler:
//192.168.1.25/public /mnt/public cifs username=*****,password=*****
# Entry for NAS photo foler:
//192.168.1.25/photo /mnt/photo cifs username=*****,password=*****[/COLOR]
```

The highlighted part is my attempt to mount the various locations on the NAS. After a restart, seems that Video is now shown in my 'Places' menu and when I click on it, it opens the NAS at the Video folder. But the others do not work.
BTW These different folders (video, music, etc...)are preset in the NAS, and they seem to act as partitions, but I a pretty sure they are not actually partitions but there seems to be not 'root' folder.

I also tried the following fstab but strangely got the same reaction as I do with the above configuration.
(Note that the location on the NAS is [COLOR="RoyalBlue"]//192.168.1.25[/COLOR] insead of [COLOR="RoyalBlue"]//192.168.1.25/video[/COLOR])

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=32cd1a76-a146-4f6a-af1c-f29d4c99b85e / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=90757b6e-79c4-410d-b439-1e3cb23f083e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# Entry for /dev/sda4 :
UUID=2b63b6fb-c4d1-41a0-a3ca-da869a845c06 /mnt/disk1 ext3 relatime 0 2
# Entry for /dev/sda3 :
UUID=4ab5846c-fb01-47b5-99f5-608835af5178 /mnt/disk2 ext3 relatime 0 2
[COLOR="RoyalBlue"]# Entry for NAS Video foler:
//192.168.1.25 /mnt/video cifs username=****,password=****
```[/COLOR]

More bizarre is that when I change the fstab to this
(Note: no more video entry at all!)

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=32cd1a76-a146-4f6a-af1c-f29d4c99b85e / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=90757b6e-79c4-410d-b439-1e3cb23f083e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# Entry for /dev/sda4 :
UUID=2b63b6fb-c4d1-41a0-a3ca-da869a845c06 /mnt/disk1 ext3 relatime 0 2
# Entry for /dev/sda3 :
UUID=4ab5846c-fb01-47b5-99f5-608835af5178 /mnt/disk2 ext3 relatime 0 2[COLOR="Blue"]
# Entry for NAS Music foler:
//192.168.1.25/music /mnt/music cifs username=****,password=****
# Entry for NAS public foler:
//192.168.1.25/public /mnt/public cifs username=****,password=****
# Entry for NAS photo foler:
//192.168.1.25/photo /mnt/photo cifs username=****,password=****[/COLOR]
```

and then restart Ubuntu (Note the video entry in fstab is now gone)
the video entry in 'places' is still there and still works!

What is happening here?

---

### Post by kellemes on 2008-09-24
Just bought a ds207+ (pretty cool stuff) but haven't started using it from Linux yet, so I can't give the ultimate answer.. Next week I'll be wrestling with it. ;-)
But have you searched the [Synology forum]("http://www.synology.com/enu/forum/index.php")? Search for "fstab"or "ubuntu" or something.

---

### Post by steinzeitmensch on 2008-09-24
Yeh thanks for the tip. There are some posts refering to Ubuntu and fstab.
See if I can make some progress with this. If I crack this nut, I will share my fstab setup in this tread.

thanks again

---

### Post by kellemes on 2008-11-09
For those interested, ds207+ permanently mounted like so..
/etc/fstab..

```
//<ip_of_nas>/<dir> /mnt/nas cifs user,uid=500,rw,suid,username=****,password=**** 0 0
```

As I understand it the syn's don't support mounting root, like "//ip-address/volume1" too bad. So I simply mount every shared directory I want separately.
If anyone has a better idea, I'd like to hear..

---

### Post by steinzeitmensch on 2008-11-09
Hi and thanks for the tip. I had pulled out almost all my hair trying to mount this NAS. I recently discovered some strange things that lead me now to believe that the NAS is the problem.
I noticed that on a Windows (XP) machine on my LAN, the NAS is not shown in the network places, even though the folders on the drive are mounted OK.
Additionally I noticed that a media player that I recently purchased could not see the NAS on the network either.  Frustrating.

I just tried your string (above) in the terminal and got back ```
No such file or directory
```
This could mean that cifs cannot see this NAS on the network.

Strangely, I have permenantly mounted on of the folders on the DS106e (my flavour of NAS at the moment) using the >Places>Connect to Server in Ubuntu main menu. I am not even sure myself how I did this and cannot recreate it for the other folders on the NAS!

I have posted this information on the Synology support forum but I have not heard back from them yet.

Thanks for the info

---

### Post by kellemes on 2008-11-09
I can assume you've create your mount directory right?
In my example /mnt/nas

---

### Post by steinzeitmensch on 2008-11-09
Yes I did.

I am not sure to what location the message ```
No such file or directory
``` is referring to. The network location or the local location which is to act as the link

---

### Post by kellemes on 2008-11-09
Well, I'm not the brightest with thing like this..
So I've installed [Smb4K]("http://smb4k.berlios.de/") (sorry, I'm on KDE) at some point just to check cifs is finding my nas. It did find my nas indeed, so at least I knew it had to be something else.

---

