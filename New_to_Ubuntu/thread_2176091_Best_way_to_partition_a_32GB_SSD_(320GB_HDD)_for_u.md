---
title: "Best way to partition a 32GB SSD (320GB HDD) for ubuntu"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by WJMRfYt on 2013-09-22
I've got a laptop with [THESE SPECS]("http://www.amazon.com/gp/product/B00863L2MI/ref=oh_details_o05_s00_i00?ie=UTF8&psc=1"), and I plan to use only ubuntu on it. I'm wondering the best way to maximize my boot time and the speed with which I run applications. I only run half a dozen applications (chrome, eclipse, Evernote, etc.) frequently, and I was told that the best thing to do for this was to install these programs on the SSD and have all the other files (music, etc) put in the HDD. However, I'm a bit lost because I'm brand new to ubuntu and I can barely grasp intalling with tarballs and where programs are saved on the hard drive, plus I still don't quite get the purpose of a "swap" partition.

I played around with it a bit and found that 12.04 doesn't install on my system for EFI-related reasons, but 13.04 works just fine (so I have to use this). I'm at the point where I'd like to start from scratch because I've had nothing but trouble trying to install things and make sure it boots quickly. Would anyone be willing to provide step-by-step instructions to make sure I install it correctly and partition it effectively (as well as a guide or reference on how to make sure programs are installed on the SSD and not HDD)?



For reference, my level of experience: I know how to access the BiOS, change the boot order, run terminal with basic commands (cd, ls, sudo), and follow well-delineated instructions I find online (for the most part). However, I don't know much about how the ubuntu/linux file system works, the purpose of partitions, how SSDs can be used to their fullest capacity, etc. Just something to keep in mind.

Thank you.

---

### Post by oldfred on 2013-09-22
Have you turned off fast boot in Windows. I would also turn off secure boot in UEFI/BIOS. But you still should install in UEFI mode if you have a computer that will boot Ubuntu. A few only boot Windows (not really confirmed, but users have posted that).

Review this as it was the same.
I do not totally agree with all details as with 30GB, you should not need a separate /var. I prefer separate /mnt/data for most data which I have on my rotating drive. I have a separate 64GB SSD, with two 27GB / partitions, but do not have UEFI.
 Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

         lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

 Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

I would fully back up Windows so if in the future you want to sell system you can reinstall Windows.
See info in link in my signature also.

---

