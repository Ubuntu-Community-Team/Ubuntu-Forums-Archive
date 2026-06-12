---
title: "Ubuntu upgrade 13.10"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by sammy3 on 2013-10-25
My moms computer has the same program as me, and her computer wants to update and upgrade, but it won't let her. it's saying it needs 41.1 free disk space but can do with 20.8 free space. She uninstalled simple things she didn't need to get more space and it didn't seem to work. It's also asking that she remove the old version before putting the new one on. asking about '/boot.' and sudo apt-get clean (which I did to see if it would help and it did nothing in the terminal) My brother is also trying to figure it out and he's thinking because her computer is so old, and the WINDOWS 7 program may not have been removed correctly or something. also heard that 13.10 was having problems? I'd like to know a little more about that too that way when her computer gets fixed whether to install it or not if it's gonna mess up or anything. Thanks!

---

### Post by unixpcguy on 2013-10-25
You can always increase the partition size, I have 13.10 and it works fine. Are you running 7 and Ubuntu on the same partition?

---

### Post by deadflowr on 2013-10-25
I'm guessing by Windows 7 program being gone, you mean Windows 7 was removed and Ubuntu replaced it.
Is that correct?

If so, then Windows 7 is gone, it and Ubuntu can't run on the same file system, so either one or the other is there, not both.

you could post the output of
```
sudo parted -l
```
this needs root, as posted sudo
and then maybe try
```
ls /boot
```
to see what /boot looks like.

Then we can try going from there.

---

### Post by sammy3 on 2013-10-25
W7 is not on her computer, only ubuntu. How do you increase the partition size exactly?

---

### Post by sammy3 on 2013-10-25
Ubuntu replaced W7. we we're thinking that if it were removed or uninstalled incorrectly that it may have effected the computer storage somehow. I could be wrong though.

---

### Post by deadflowr on 2013-10-25
If you replaced win7 with Ubuntu, then I would guess the partition layout is going to be
sda1   /
sda2  extended
sda5  swap

and that's it.
That's the default installation layout.

---

### Post by warp99 on 2013-10-25
There's most likely not enough room to download and install the upgrade due to a lack of space. If you download and burn a 13.10 DVD or make a bootable USB on another computer you can upgrade since there's an option for this during installation.

[http://askubuntu.com/questions/290201/how-do-i-upgrade-from-ubuntu-12-04-to-ubuntu-13-04-with-an-iso-image](http://askubuntu.com/questions/290201/how-do-i-upgrade-from-ubuntu-12-04-to-ubuntu-13-04-with-an-iso-image)

---

### Post by sammy3 on 2013-10-26
I'd have to have my brother figure it out cause he's a computer nut, and I'm pretty sure that's what he's doing. From USB that is, cause the disk slot on my moms laptop won't open.

---

### Post by Impavidus on 2013-10-26
In case of lack of disk space, read this: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
It gives general advice on how to find where the disk space went and how you get it back.

First of all, post the output of the commands deadflowr gave in post #3 and the output of **df -Th**. Then we will know how big and how full your mom's partitions are.

---

### Post by Bucky Ball on 2013-10-26
We are making this complicated. Please open a terminal and post the output of this:

```
sudo blkid
```

If it is possible, open Gparted and take a screenshot of your drive and attach it to your next post.

---

