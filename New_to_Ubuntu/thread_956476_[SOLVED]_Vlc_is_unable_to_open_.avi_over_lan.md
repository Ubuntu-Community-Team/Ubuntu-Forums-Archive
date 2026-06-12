---
title: "[SOLVED] Vlc is unable to open .avi over lan"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by mucklas on 2008-10-23
Hi, all. Newbie here with a newly installed Ubuntu Hardy Heron. Until now I used Windows.
I'm having problems with vlc. When I double-click on an .avi from the external harddrive over the lan vlc sits quietly on the screen for twenty seconds, then gives an error message: Unable to open blablabla. Drag-and-dropping produces no result whatsoever. .avi files om my laptop work perfectly.
Totem player works fine, but is unable to play sound in my headphones, and frankly; my laptop speakers aren't that good.
If someone could help me with this I'd be grateful.
vlc version: 0.8.6e Janus

---

### Post by Bazon on 2008-10-23
How do you acces your network drive?
Over Places / Network?
Unfortunately not all applications are able to open files theis way, only the gnome applications do.

But anyway, of course you can use VLC to watch your movies on your network drive, but you have to "mount" your network drive into your local filesystem.

You do this by usinf the /etc/fstab file:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I assume, you use a windows share?
In this case you heve to mount it as a Samba-Share:
[https://help.ubuntu.com/community/SettingUpSamba#Client](https://help.ubuntu.com/community/SettingUpSamba#Client)

If it is a NFS share, see here:
[https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS Client](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS Client)

So please read the page about FSTAB and the Client-part of the appropriate network.
If you have questions left (I think so...) fell free to ask! :-)

---

### Post by mucklas on 2008-10-23
Thanx a bunch for your quick reply!
The problem was with mounting the drive properly. Your reply led me to this page:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
Following those directions I fixed the problem.

---

