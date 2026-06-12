---
title: "[SOLVED] ubuntu hardy failed to install"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by timo_01 on 2008-05-14
hi everyone

I wanted to dual boot,win xp which is already install,but a fresh ubuntu hardy 8.04 install,all seemed fine until 98 % and i get this error "executing grub install (hd0)failed".

does anyone have an idea?
Maybe windows is causing this?
thanks

---

### Post by Sef on 2008-05-14
1) Put in the disk and 'Check disk for errors', make sure your version of ubuntu is good.

2) Did you md5sum the download or use a torrent?

---

### Post by aquavitae on 2008-05-14
Could be a problem related to grub and linux seeing the boot disk differently - I've known it to happen although it probably shouldn't.  How many physical drives do you have? 
Do you know what your new partition layout is?

---

### Post by timo_01 on 2008-05-14
> **Sef said:**
> 1) Put in the disk and 'Check disk for errors', make sure your version of ubuntu is good.

2) Did you md5sum the download or use a torrent?

how do i check for errors?
i didn't use torrent

thanks

> **aquavitae said:**
> Could be a problem related to grub and linux seeing the boot disk differently - I've known it to happen although it probably shouldn't.  How many physical drives do you have? 
Do you know what your new partition layout is?

i have one hard disk of 120 gb which i partitioned one for win xp 40 gb and the other 80gb for ubuntu.

---

### Post by billgoldberg on 2008-05-14
> **timo_01 said:**
> how do i check for errors?
i didn't use torrent

thanks



i have one hard disk of 120 gb which i partitioned one for win xp 40 gb and the other 80gb for ubuntu.

Check the md5sum (google it), if and check the disk for errors (you can pick this option before you choose "install to harddrive").

If everything should check out fine, try installing it again.

If it doesn't work, try the alternate cd to install.

---

### Post by steve-shinn on 2008-05-14
Does the pc run ok in live from the CD ?

---

### Post by wpshooter on 2008-05-14
> **billgoldberg said:**
> Check the md5sum (google it), if and check the disk for errors (you can pick this option before you choose "install to harddrive").

If everything should check out fine, try installing it again.

If it doesn't work, try the alternate cd to install.

I had made all of the integrity checks, etc. on the Alternate CD that I had burned, yet I still got the error that the poster of this thread mentioned.

Me thinks this version of Ubuntu has many, many bugs remaining in it !!!

---

### Post by baddnady23 on 2008-05-14
Bugs remaining, yes.  But nothing to the point that has prevented myself or thousands of other users from upgrading yet.  Maybe try downloading the installer directly from ubuntu.com itself??

---

### Post by timo_01 on 2008-05-14
> **steve-shinn said:**
> Does the pc run ok in live from the CD ?

it does run ok.

i solved it.i booted from win xp cd and saw the partition marked as fault tolerance,formatted it and now hardy works out of the box.no more grub problems.

thanks to you all..

---

### Post by wpshooter on 2008-05-14
> **baddnady23 said:**
> Bugs remaining, yes.  But nothing to the point that has prevented myself or thousands of other users from upgrading yet.  Maybe try downloading the installer directly from ubuntu.com itself??

That IS where I downloaded it from !!!

Thanks.

---

