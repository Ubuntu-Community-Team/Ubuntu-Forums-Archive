---
title: "Two drives: how to install with proper partitions?"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by KSvkWtDO on 2012-09-26
I have an eee pc 900, which has a 4GB drive and a 16 GB drive. I am installing 12.04 and want to get the partitions right. It seems like the right thing to do to install the operating system on the small drive and then leave it be, so I set the bootloader to install on the 4GB drive and mounted it to / with the ext4 filesystem and labeled it Primary. Then I made a 2 GB swap partition on the 16 GB drive. Then I made an 8 GB /home partition on the 16 GB drive, again with ext4 and Primary selected. I want to use the rest of the space on the 16 GB drive to hold extra system files and program installation files and whatnot, so I selected ext4 and Primary yet again and tried to mount it to /, but I am being told that I can't mount two drives to /.

My question is, what are the proper settings for installing the OS to the small drive, and then having swap, /home, and space for system and program files on the large drive?

Thank you in advance! :p

---

### Post by wheeze on 2012-09-26
You'd have to make partitions on your 16 GB drive to mount anything you want to pull out of the root, such as /usr or /lib, etc. You can only have one partition per mount point, as you found out already.

It's a pretty dicey setup, you run the chance of running out of space in the partitions you set up. You only have 6 GB left to play with on the big drive.

Any particular reason for wanting to set it up this way? If it were me, I'd install everything on the 16 GB drive, use half the 4 GB for your swap partition and the other half for perhaps /var and /tmp or something.

---

### Post by KSvkWtDO on 2012-09-26
> **wheeze said:**
> You'd have to make partitions on your 16 GB drive to mount anything you want to pull out of the root, such as /usr or /lib, etc. You can only have one partition per mount point, as you found out already.

It's a pretty dicey setup, you run the chance of running out of space in the partitions you set up. You only have 6 GB left to play with on the big drive.

Any particular reason for wanting to set it up this way? If it were me, I'd install everything on the 16 GB drive, use half the 4 GB for your swap partition and the other half for perhaps /var and /tmp or something.

Your suggestion does sound a lot better, actually. I had no particular reason other than that I thought it was "proper" to have the OS be installed on a small drive and all other files on a larger drive. I also wasn't sure what mount point was needed for the OS installation.

Anyway, thank you!!

---

### Post by KSvkWtDO on 2012-09-26
Success! At first I was having boot errors after installation, but then I realized that I needed to change my boot order so that the large hard drive would boot insetad of the smaller one. Thanks again!

---

### Post by wheeze on 2012-09-26
Glad to hear you've got it going. Fun, huh? :)

---

### Post by KSvkWtDO on 2012-09-26
> **wheeze said:**
> Glad to hear you've got it going. Fun, huh? :)

You know it! :KS

---

