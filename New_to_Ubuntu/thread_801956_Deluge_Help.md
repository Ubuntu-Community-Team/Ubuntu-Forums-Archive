---
title: "Deluge Help"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Skeet on 2008-05-21
I have just installed Deluge Bittorrent Client, and I want to be able to save my downloads to my NTFS formatted Storage partition. Is it possible to do this or must I save it on my Ubuntu partition and transfer it over?

---

### Post by Xiong Chiamiov on 2008-05-21
Why don't you just try it?

AFAIK you should be fine, unless there is an inherent limitation built into libtorrent that prevents that.

---

### Post by iaculallad on 2008-05-21
Its possible to save all your downloads to your NTFS formatted partition. Just be sure that its (NTFS formatted drive) auto/mounted when you activate your deluge-torrent.

---

### Post by prshah on 2008-05-21
> **Skeet said:**
> I have just installed Deluge Bittorrent Client, and I want to be able to save my downloads to my NTFS formatted Storage partition. Is it possible to do this or must I save it on my Ubuntu partition and transfer it over?

Yes possible, but not recommended (by me). Reasons: 

a) If by chance you go to windows, but fail to shutdown properly, the ntfs partition will not be accessible in ubuntu until chkdsk (windows) is run. That means that ubuntu will start downloading the entire torrent from scratch into the mount directory of your ntfs partition.

b) An improper shutdown in ubuntu as well will not (auto) load the ntfs partition

c) It's better to download to your ext2/3 partition as usual, then use Deluge move torrent plugin to move the completed download to your storage partition in one shot.

---

