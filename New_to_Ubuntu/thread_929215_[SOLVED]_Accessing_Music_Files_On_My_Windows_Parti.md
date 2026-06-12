---
title: "[SOLVED] Accessing Music Files On My Windows Partition"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by StunnerAlpha on 2008-09-24
Ey guys, I am trying to get Amarok to read my music files from my Windows partition, but it won't let me see the mounted drives or let me go up past the root to the computer level. In the file browser I am able to access the music perfectly fine, but the Amarok add media browser doesn't let me select a partition. Any help is greatly appreciated. Thanks!

---

### Post by eternalnewbee on 2008-09-24
I don't know much about amarok, but with vlc I have no troubles opening files from a mounted partition.. maybe you could give it a try

---

### Post by jemate18 on 2008-09-24
You can also try banshee.....

it can access my music on my windows partition..


sudo apt-get install banshee

---

### Post by angelsguitar on 2008-09-24
> **StunnerAlpha said:**
> Ey guys, I am trying to get Amarok to read my music files from my Windows partition, but it won't let me see the mounted drives or let me go up past the root to the computer level. In the file browser I am able to access the music perfectly fine, but the Amarok add media browser doesn't let me select a partition. Any help is greatly appreciated. Thanks!

All the NTFS (Windows) partitions are mounted by default on the /media folder.  From Amarok, try searching the /media folder; there you should find your Windows partition.

---

### Post by StunnerAlpha on 2008-09-25
> **angelsguitar said:**
> All the NTFS (Windows) partitions are mounted by default on the /media folder.  From Amarok, try searching the /media folder; there you should find your Windows partition.

Yeah, that seemed to work. Had to type it in for it to show up. Thanks.

---

### Post by jemate18 on 2008-09-25
please mark this thread as SOLVED

---

### Post by StunnerAlpha on 2008-09-25
> **jemate18 said:**
> please mark this thread as SOLVED

How do I do that?

Edit: nevermind, got it.

---

