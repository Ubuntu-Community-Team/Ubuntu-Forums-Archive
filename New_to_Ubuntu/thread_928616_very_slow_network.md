---
title: "very slow network"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by b0b138 on 2008-09-24
I have just installed hardy onto a second machine to backup some files to, and am getting really slow transfer speeds. I'm using samba, one window with my local files, one window of the shared folder, dragging and dropping.  I'm getting around 230 KBs (seems rather slow for 100 mbit ether considering my 3meg internet connection downloads around 370 KBs)

I've looked around a bit and found some references linking it to a bug in gvfs or nautilus or both but have yet to find a solution (if there is one).

Anyone know of a way around this or some newb friendly directions to copy folders to a network share via command line?

---

### Post by lovinglinux on 2008-09-24
I also get these slow speed transfers when using samba shares. It should be faster I guess.

---

### Post by billgoldberg on 2008-09-24
I can't help with that.

But have you tried to share files using SSH?

Installation on Ubuntu is drop dead easy. On other OS's, it's a bit harder.

---

### Post by b0b138 on 2008-09-26
So heres something interesting...

I used this command, sudo mount -t smbfs -o username=user //server/share /mnt/share, instead of clicking through places, network, yada yada, which worked. I can now access this share at /mnt/share.

I opened up one window of the files I want to backup, one window for /mnt/share, dragged and dropped, and got transfer speeds around 8 MBs

How is this different from the first way I did it, and is 8 MBs normal for 100 mbit ether?

---

