---
title: "So I shrunk my ext3 partition"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by boxxy27 on 2008-08-14
Actually what I did was copy my ubuntu partition to a unallocated space and then shrunk the filesystem from 50gb to 30gb to give me some space for my windows partition cause I end up using a lot more space on windows compared to linux. Anyways I used gparted to shrink it, all worked fine, I can boot into the partition but when its booted the computer still thinks that it has 29gb free space left when it really has like 5gb.

That and when i go into gparted it says that it can not read the filesystem?

But everything works fine as far as i can see...so how do i fix this?

---

### Post by boxxy27 on 2008-08-14
oh yeah forgot to say that when i go into the filesystem from computer and right click on it...

its says

volume: unknown instead of the total size

---

### Post by ercferret18 on 2008-08-14
i think you have to edit something in /etc/fstab... not sure what

---

### Post by S.A.A on 2008-08-14
could you post the output of /etc/fstab..

---

### Post by prshah on 2008-08-14
> **boxxy27 said:**
> Actually what I did was copy my ubuntu partition to a unallocated space and then shrunk the filesystem 

Next time, shrink it using a live CD rather than copy back and forth.

For this particular situation, run the command```
sudo resize2fs /dev/sdxx
``` replace "sdxx" with the actual partition id of your troublesome filesystem. This will "fix" the new size. It should not harm your data in any way, but

a) Take a backup
b) Use a live CD and unmount the filesystem first.

Note: Neither of the above two are essential, but it is good practice; if you're impatient and willing to take a minimal risk, just proceed with the resize command.

The fstab has nothing to do with filesystem size.

---

### Post by boxxy27 on 2008-08-14
so little did you know...I did use gparted from the ubuntu hardy live cd....

at first i tried downsizing my real filesystem but it wouldnt let me so i just copied the partition

anyway i followed your steps and it didnt do a thing...
it only said that the filesystem is already 74894621 and something blocks and there isnt anything else to do...but thanks anyway

---

### Post by caljohnsmith on 2008-08-14
Have you tried running fsck on the partition from a Live CD?
```
sudo fsck /dev/sdXY
```
Make sure the partition you use fsck on is not mounted.

---

