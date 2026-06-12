---
title: "networking on a LAN"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by lost4now on 2008-05-11
Please bear with me I don't know enough to know what to search for.

There seems to be several ways to access one computer from another on the same LAN. Which is best and what do I search for to find a simple tutorial or guide. 

Thanks.

oops. I'm running 8.04

---

### Post by freebeer on 2008-05-11
I guess you should define what you mean by "access".  Do you want to just share files, or are you trying to run the other machine remotely?  Is the other machine(s) running Linux, Windows, other?

---

### Post by superprash2003 on 2008-05-11
if its file sharing.. you could try samba.. there's a good guide here at [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by lost4now on 2008-05-11
Both machines are running ubuntu.  All I want is to access the files on the other machine.

---

### Post by freebeer on 2008-05-11
I'm guessing that you might want to look into NFS.  That's Network File Sharing between Linux boxes.  I've never set it up, but I found this link [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

Samba is typically used when you want to share with Windows machines.

---

### Post by Scheater5 on 2008-05-11
One that's never failed me is [this howto]("http://ubuntuforums.org/showthread.php?t=218630").  It sets up FTP in the process, (as opposed to NFS) but the main point is it makes it easier to find other computers on a network, not to mention it's OS agnostic.  May or may not be of use to me, but I run it on every box I have, and between it and hamachi my networking is as easy and fun on Linux as it is on OSX.

---

