---
title: "Corrupt backup superblocks"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by PlayfulDragon on 2012-09-26
Running Gnome as well. 

I am trying to resurrect a hard drive that is NFTS formatted. 

When I run FSCK, it says that there is a 'Bad magic number in super-block while trying to open /dev/sdb' 

So I ran e2fsck -b 8193 /dev/sdb

And I have corrupt superblocks. 

So I tried to restore the superblocks from the backups. 

I tried listing them using mke2fs -l to find out where the backups were listed.

Each one is 'corrupt'. 

What else can I try? 

Could I perhaps try to restore a good superblock from another nfts formatted drive? 

Many thanks in advance. 

Yours, 

Playful Dragon

---

### Post by shreepads on 2012-09-26
Why are you using e2fsck/ mke2fs which are ext2/3/4 specific tools on a NTFS formatted drive/ partition?

Have a look at ntfsfix, details:

[http://manpages.ubuntu.com/manpages/precise/man8/ntfsfix.8.html](http://manpages.ubuntu.com/manpages/precise/man8/ntfsfix.8.html)

---

### Post by NikTh on 2012-09-26
Hi , 

the steps you must follow are 2-3 simple commands. BUT we speak about Linux File-sytem. EXT , and not NTFS. 

First you must Unmount the partition with the problem . We assume that this partition is /dev/sdb1 

```
sudo umount /dev/sdb1
```Then you can take the list with recovered superblocks with this command 
```
sudo mke2fs -n /dev/sdb1
```We assume that one of the numbers where recovered superblocks are , is 32456 
The next command will try to fix your problems 
```
sudo e2fsck -y -b 32456 /dev/sdb1
```
Good Luck and remember ,** ALWAYS** we have a **backup** of our important files. Otherwise are not so important for us.
Thanks

---

### Post by PlayfulDragon on 2012-09-26
> **shreepads said:**
> Why are you using e2fsck/ mke2fs which are ext2/3/4 specific tools on a NTFS formatted drive/ partition?

Have a look at ntfsfix, details:

[http://manpages.ubuntu.com/manpages/precise/man8/ntfsfix.8.html](http://manpages.ubuntu.com/manpages/precise/man8/ntfsfix.8.html)

It worked! Thank you very much. It can now mount the drive. :)

---

### Post by shreepads on 2012-09-27
> **PlayfulDragon said:**
> It worked! Thank you very much. It can now mount the drive. :)

Good to hear! Although the thanks should go to the ntfs-3g devs...

---

