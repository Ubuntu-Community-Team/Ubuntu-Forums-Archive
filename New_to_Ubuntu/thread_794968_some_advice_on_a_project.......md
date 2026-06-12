---
title: "some advice on a project......"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by techno-mole on 2008-05-15
hello.
i have decided to build a small file server for the home network, i mainly want to use it as a networked storage device, it will connect to the home network via a 4 port router, and will store the files from 3 systems (mine, my other halfs, and the kids pc) 

2 of the systems run windows xp, and mine runs ubuntu (hardy) on one hard drive and xp on the another, now what i was wondering is would it be best to set up ubuntu on the server (as its os) using samba it will be easy enough to set up the networking aspect of it.
obviously i (being the administrator if you like) will need access to the server in order to do various maintenance tasks etc etc, now i could hook up a monitor to the system, which would mean i can just log in and do whats needed.

however i was thinking it might be betting to set up a remote connection between my system and the server, this way i could do various things, with out having to physically do anything to the server system.

so basically would setting up a remote connection be a better way of administrating the system ? and would it be better to install a server edition of ubuntu, rather than the desktop edition ( i dont know much about the server edition, i dont even know if its allowed to be used in the home, is it  just for companies ?)

cheers in advanced for any help.

---

### Post by Xiong Chiamiov on 2008-05-15
I have a fileserver built out of a crappy old PC sitting right next to me.
For sharing with Windows, use [Samba]("http://ubuntuforums.org/showthread.php?t=202605").
For sharing with UNIX-like machines, [use]("https://help.ubuntu.com/community/SettingUpNFSHowTo") [NFS]("http://ubuntuforums.org/showthread.php?t=249889").
Sometimes, a monitor can be very helpful, so I wouldn't go making it headless until you have to.  If it can support the load, you can try a screen-sharing program.
For most administrative tasks, you just need to [install the ssh server]("https://help.ubuntu.com/community/SettingUpNFSHowTo") on the fileserver, and a client on your computer.  Then you can access with the command:
```

ssh username@IPorName

```

---

### Post by Xiong Chiamiov on 2008-05-15
Oh, and the server edition by all means is allowed in the home.  It has several things adjusted for server performance, but it comes without a GUI prepackaged (which was bad for me, as I use it for displaying videos through the tv as well).  If you go with a GUI, I'd recommend using something as light as possible, like Xubuntu or Fluxbuntu.

---

### Post by techno-mole on 2008-05-15
cheers for the info, ive booked marked the links.
now all i have to do is build it :) which i guess will be the easy bit, although as ive found with most things in ubuntu if you do a bit of reading first its all pretty easy.
cheers again.

---

