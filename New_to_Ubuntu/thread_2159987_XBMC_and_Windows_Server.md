---
title: "XBMC and Windows Server"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by elninouk on 2013-07-05
[SIZE=2]hi guys i've just moved away from microsoft after being a slave for many many many years.. :)

i've just installed 
[/SIZE][h=1][SIZE=2]Lubuntu 13.04 and from the first install on my previous slow laptop a new lease on life has occured. every thing installs very very quickly... my only issue is this ( probably very easy to ask) 
[/SIZE][/h][SIZE=2]i need to access my window server ( HP Proliant) which sits in my home office.. holds all my media on my windows machine is appears as network drive ... how do i  get my new machine to reconize this..  its sat on a assigned IP address in my 192.168.0.10 which is fixed.. and my login for my windows server  would 

User Name elninouk 
Password elninouk 
its not but you get the picture so what would i need to do to make my server talk to my new machine :)
[/SIZE]

---

### Post by Paqman on 2013-07-05
[XBMC can find and connect to Windows shares]("http://wiki.xbmc.org/index.php?title=Video_library/Adding_media_sources") (which may be called Samba shares) without any special configuration. If the folders are shared n the Windows machine you should be able to find them ok in XBMC.

If you want access to those files in other applications it might be sensible to mount the shares locally on your machine through a file called [/etc/fstab]("https://help.ubuntu.com/community/Fstab"), which will automatically mount them at boot time. Then all your applications can just point to the same local mount point (which could be something like /mnt/stuff). Doing this is IMO a more robust and straightforward way to set up your machine, but if you're predominantly using XBMC then doing it through that application makes sense.

---

### Post by TheFu on 2013-07-05
Well said @Paqman.

I would point out that many Linux file browsers support mounting (temporary or permanent) remote CIFS file systems with credentials. Nautilus does, but I don't think those shares are available unless the specific user logs in.

---

### Post by dannyboy79 on 2013-07-05
what OS and software does the HP Proliant run? When you say all your media is there, does that mean it's just sitting in folders or are you running Windows Media Center or something like Plex media Server? These questions need to be answered so that we can provide the best solution.

Anotehr question that may arise, is the username the same on the HP Proliant as it is on your newly installed Lubuntu machine?

---

