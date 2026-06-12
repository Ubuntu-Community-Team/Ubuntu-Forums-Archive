---
title: "[SOLVED] HELP, setting up a Samba Share"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by BassKozz on 2008-10-17
I am trying to setup a samba share on my Ubuntu machine so that I can share with my WinXP machines, and when I right click the folder I want to setup the share for and select "Sharing Options" and try and setup a share I get the following error:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/Screenshot-FileManager.png[/IMG]


What am I doing wrong?

---

### Post by Nxion on 2008-10-17
Try theses guides. I found them most helpful.
[URL="https://help.ubuntu.com/community/SettingUpSamba"]
https://help.ubuntu.com/community/SettingUpSamba[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=202605"]
http://ubuntuforums.org/showthread.php?t=202605[/URL]

Hope it helps :)

---

### Post by bodhi.zazen on 2008-10-17
Suggestions / questions.

First , with samba, you need to log out and back in after installing the samba server.

Second, what directory are you sharing ? You need to have the proper ownership and permissions on a directory before you can share it.

Third, do you have a firewall on any of your boxes ?

---

### Post by Nxion on 2008-10-17
> **bodhi.zazen said:**
> Suggestions / questions.

First , with samba, you need to log out and back in after installing the samba server.

Second, what directory are you sharing ? You need to have the proper ownership and permissions on a directory before you can share it.

Third, do you have a firewall on any of your boxes ?

I can't believe I for got about the permission part. I feel stupid now :(

---

### Post by BassKozz on 2008-10-17
> **bodhi.zazen said:**
> First , with samba, you need to log out and back in after installing the samba server.

That fixed my 1st problem, now my 2nd problem is that the share isn't showing up on my XP machines under networking?

---

### Post by bodhi.zazen on 2008-10-17
> **BassKozz said:**
> That fixed my 1st problem, now my 2nd problem is that the share isn't showing up on my XP machines under networking?

That seems to be somewhat inconsistent.

First it may take a few minutes for the share to show (there is a delay or latency sometimes for the samba server). In my experience this "problem" is more common.

If it does not show you may need to manually mount it (ie map a network drive).

[http://www.cs.umd.edu/faq/pc/map_network_drive/map_network_drive.html](http://www.cs.umd.edu/faq/pc/map_network_drive/map_network_drive.html)

Less common, on a home network, you need to add your Samba server to a windows domain.

---

### Post by BassKozz on 2008-10-18
i figured it out;
Thanks to your help (everyone)...
The problem was that it didn't show up in the network neighborhoods on the XP machines, but when I manually mounted the share it worked. :D
Thanks
-BassKozz

---

### Post by nixforme on 2008-10-27
> **bodhi.zazen said:**
> Suggestions / questions.

First , with samba, you need to log out and back in after installing the samba server.

Second, what directory are you sharing ? You need to have the proper ownership and permissions on a directory before you can share it.

Third, do you have a firewall on any of your boxes ?

> **Nxion said:**
> Try theses guides. I found them most helpful.
[URL="https://help.ubuntu.com/community/SettingUpSamba"]
https://help.ubuntu.com/community/SettingUpSamba[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=202605"]
http://ubuntuforums.org/showthread.php?t=202605[/URL]

Hope it helps :)

Both of you guys rock!!!!!!!

---

### Post by BassKozz on 2008-10-27
I experienced alot of odd behaviors (file locks, etc...) when I setup the share via right clicking on the folder and sharing it, so I ended up just setting up the share manually via ***/etc/samba/smb.conf*** instead and all is well :D

I am curious thou, how come the behavior is different?
Isn't right clicking a folder and selecting 'share' the same as setting up a samba share, or is there something else going on there?
TiA,
-BassKozz

---

