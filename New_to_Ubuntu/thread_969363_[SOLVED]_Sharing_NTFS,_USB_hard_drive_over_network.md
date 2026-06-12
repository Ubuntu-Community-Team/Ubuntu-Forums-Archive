---
title: "[SOLVED] Sharing NTFS, USB hard drive over network."
date: 2008-11-03
forum: New to Ubuntu
---

### Post by toolfan2k4 on 2008-11-03
I have a USB hard drive hooked into my dual boot PC. Its formatted as NTFS and basically I use it to store all my files for the family's Windows PCs. Backups for pictures mostly, anyway how do I share this? Do I need samba? Can samba be run on desktop version of Hardy or is it server only? I already have it shared in Windows fine but I want the other Windows PCs to be able to access it even while I'm using Ubuntu on my dual boot PC. Is there a simple GUI to allow read and write access from any PC in my network workgroup? Kinda like how in Windows all you have to do is check a couple of boxes...lol. Spoken like someone whoes family forces him to be attached to Windows. I love this forum everyone is top notch and I like how people are not verbally abused for being a noob. Thanks in advance.

---

### Post by dustman on 2008-11-04
Hi!

Yes, to achieve this you'll need samba. If you have Ubuntu 8.04 or later, you can just right click the folders you want to be shared over the network and then click "Share" (I don't know it's exactly that option since I don't have access to an Ubuntu machine right now, but you get the point - I hope :D). Since you already can share data when your computer has windows started, you won't have to make any other modifications to the other computers.

Btw, Ubuntu server is just the same as Ubuntu desktop, only that is some different packages installed by default (like apache2, php5, mysql etc - and all these are already configured). If you are to get a list of all the packages from Ubuntu server, you can install a desktop version and then just install the packages from the servers' list - this way having them both :D.

Cheers!

Radu

---

### Post by superprash2003 on 2008-11-04
here's a samba tutorial [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by toolfan2k4 on 2008-11-04
OK thanks to both of you. I was afraid I would have to use samba. I can't get it configured to work correctly. But I guess thats another thread entirely. And yeah I tried a bunch of different samba tutorials. I have not tried that tutorial I guess I will give that one a try. Anyway, thanks again.

---

