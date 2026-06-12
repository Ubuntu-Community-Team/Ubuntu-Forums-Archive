---
title: "Partition?"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by Devster on 2012-03-10
I just formatted an older hard drive of mine and I have a few questions about putting a linux distro on it. I want to make a dual boot with XP and Zorin Os I think, but with XP on one drive and Zorin on the other. I'm currently downloading the .iso.

Would I need to partition it, if I plan to use the entire drive for linux, or is that even necessary? (it's a 100GB drive)

Would I be able to access the files (music, pictures etc.) on my other drive, or outside the linux partition?

Just so you know, I'm an absolute beginner with linux, but I'm pretty darn computer savvy, if I do say so myself ;)

---

### Post by Frogs Hair on 2012-03-10
Hello and Welcome

If you are using the entire disk you should have the option during installation . Zorin is Ubuntu based , but you may want to check with their forum. [http://zorin-os.webs.com/apps/forums/](http://zorin-os.webs.com/apps/forums/)

---

### Post by dekom on 2012-03-10
You don't need to partition it, thought I would suggest separating the /home folder from the others onto another partition.

During the installation, make sure that you select the correct drive to install GRUB onto, otherwise, your system may not be able to find bootable partitions.

You can access files from other partitions, though some of them may be read-only.

---

### Post by Bucky Ball on 2012-03-10
If you go for letting Ubuntu format the drive you are installing onto you get what you're given and you may not be happy with that. I would manual partition when you get to that bit of the install and go for something like:

/ = 20Gb plenty
/home = as suggested by dekom - contains your data; large as you like
/swap = 2Gb fine

That way, if you need to reinstall the OS you just reinstall over the / partition (unticking the other partitions so they don't get formatted) and all your data stays in /home. It won't get wiped. If you don't have a separate /home a /home *folder* will be made inside / which means if you need to reinstall the OS you will kill your data too.

---

### Post by Devster on 2012-03-10
Thanks for the info and advice! 
@Frogs Hair: I checked with them, they assured me that the installer was pretty much exactly the same as Ubuntu.

@Bucky Ball, whats the point of the /swap partition?

---

### Post by SuaSwe on 2012-03-10
Hey Devster!

Have a look at [this FAQ]("https://help.ubuntu.com/community/SwapFaq"), which outlines why you want a swap partition. :)

---

