---
title: "equivalent of 'mapping a drive'"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by JeremySchubert on 2012-01-03
What is the linux equivalent of mapping a drive?  For example, if I want  an icon to show on the desktop for a connection to my mobileme or ubuntu  one files?  Can I script this through a batch file? 
Thanks, 
Jeremy

---

### Post by mikewhatever on 2012-01-03
I am afraid that you compare peaches to oranges. Usually, when 'mapping a drive', it is implied that the Windows printing and sharing protocol is in use, the equivalent of which is [Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29") in Linux.

Ubuntu One doesn't use Samba, so what about that 'my mobileme' thing? Does it use Samba?

---

### Post by I_can_see_the_light on 2012-01-03
> **JeremySchubert said:**
> What is the linux equivalent of mapping a drive?  For example, if I want  an icon to show on the desktop for a connection to my mobileme or ubuntu  one files?  Can I script this through a batch file? 
Thanks, 
Jeremy

Hmm, I'm not logged in to Ubuntu right now but you should be able to right click your Ubuntu One folder and create a link. You can then copy that link to the desktop folder.

---

### Post by yndesai on 2012-01-03
if you wish to create an icon on desktop perform some task it is called 'create a launcher '

While to "map a drive" there are different ways to do it depending where the folder is hosted smb for windows share and ftp or there is even simple mount tool which mounts the folder in a location.

---

### Post by JeremySchubert on 2012-01-07
Problem solved...turns out I was using the wrong words.  Using Google to search for "linux how to mount mobileme" took me to [http://www.chrisdanielson.com/2009/08/13/mounting-mobileme-idisk-using-webdav-and-linux/](http://www.chrisdanielson.com/2009/08/13/mounting-mobileme-idisk-using-webdav-and-linux/).  Then, to create a shortcut to the mounted folder I followed the instructions at [http://www.liberiangeek.net/2011/11/create-desktop-shortcuts-icons-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/create-desktop-shortcuts-icons-in-ubuntu-11-10-oneiric-ocelot/).

Basic Instructions

1.  Install the package, davfs2
2.  Using a command like 'sudo pico fstab' modify etc/fstab to include the following line at the bottom (replace {account_name} with your account name)
> https://idisk.mac.com/{account_name}    /mnt/idisk      davfs   rw,noauto,user  0       04.  In terminal then you can use the command sudo mount /mnt/idisk

---

### Post by Paqman on 2012-01-08
If you want that to show on the desktop you should create your mount point in /media instead of /mnt, btw.

---

