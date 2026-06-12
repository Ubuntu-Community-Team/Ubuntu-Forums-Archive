---
title: "Ubuntu Live set permissions to 999, cant access"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by brycestejskal on 2013-02-01
Hello everyone,

I ran in to a strange issue im not sure how to get past, tried searching to no avail. Here is what happened:

I had a windows 7 pc that had about 700gb I wanted to move from its NTFS partition to my Linkstation NAS which has a 2TB drive hooked to it's USB port formated in XFS. I hooked said USB drive to the pc directly and booted into a Ubuntu live disc to transfer the files, since windows doesnt recognize XFS but linux will read NTFS. Everything transferred over and I reinstalled windows blah blah blah.

I hooked the 2TB XFS drive back up to the NAS. Now, the two folders I coppied to it are marked as read only with an owner 999(Nobody). I am unable to access ANY of the contents of these two folders now.

I booted back into the live cd and attempted to sudo chown -hR root:root Movies/ but it just says permission denied. Windows is also unable to change the permissions to anything.

Any suggestions? THanks


I have also tried this

ubuntu@ubuntu:/run/user/ubuntu/gvfs/smb-share:server=ls-wxl176,share=usbdisk1/Movies$ sudo chmod -R u+r+w Movies/
chmod: cannot access `Movies/': Permission denied
ubuntu@ubuntu:/run/user/ubuntu/gvfs/smb-share:server=ls-wxl176,share=usbdisk1/Movies$

---

### Post by brycestejskal on 2013-02-05
Still unable to figure out a solution to this issue... nothing seems to be able to get me permissions to read or make any changes to these two folders. 700GB of files... uhg

---

