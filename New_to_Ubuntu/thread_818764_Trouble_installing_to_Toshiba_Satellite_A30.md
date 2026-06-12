---
title: "Trouble installing to Toshiba Satellite A30"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Evil Garden Gnome on 2008-06-04
Hello all.

I'm fairly new to linux and need some help with an install.

I am attempting to install Xubuntu 7.10 (from a burnt disc) onto a stock [Toshiba Satellite A30]("http://www.toshiba.ca/web/product.grp?section=1&group=223&product=2331").

I have tried 3 times and each time has resulted in the computer locking up and crashing at 82% of the final install ("Installing the kernel - retrieving and installing linux-generic").

I have tested the disc to make sure it is working properly and it installed perfectly onto a desktop.

For options I go with my local choices, UTC time, skip networking, and for the partition I chose "Guided - use the whole disc".

I can no longer access Windows XP (as it was wiped on the first install attempt) and wouldn't know how to recover it if I could. The bios works fine.

Any help is greatly appreciated.

---

### Post by wpshooter on 2008-06-04
First may I ask why are you choosing to skip networking ?

Do you not have internet connection ?

---

### Post by Evil Garden Gnome on 2008-06-04
I skipped networking because the computer is not online. I'm using my landlord's connection and he has mac filtering on. I can not find out my mac address as I don't have an OS.

I did the same with my desktop and had no problem.

---

### Post by avtolle on 2008-06-04
As much as I dislike saying this, the fact that the disk installed perfectly on another computer doesn't mean it will install on the Toshiba. There are several variables which might get involved, such as the CD drive, etc. For example, in my instance, to install Ubuntu on two of my computers, use of a CD-R is required for the media; but on another, the iso burnt to a CD-RW works every time, but neither of the other two will handle a CD-RW. Thus, it is always my recommendation to burn at a slow speed on a "name brand" CD-R for best hopes of success. Similarly, I recommend use of the alternate install disk rather than the Live Desktop CD for installs, as the Live CD installs quite well on one computer, and due to (sometimes) subtle differences, will not install on another although of similar specs.

Your difficulty with the Toshiba leads me to the conjecture that there is a problem with the CD for *that computer*. I suggest burning a new CD, etc., and trying it again on the Toshiba.

---

### Post by wpshooter on 2008-06-04
Yes, I agree, different drives sometimes prefer different types/brands of media.  My best results seem to comes from the use of either Sony or Imation CD-RWs.

One other thing you might consider is if your CD drive has the latest and greatest firmware installed.

And also, one other thing, since you have already basically taken everything off of the hard drive, I would suggest that you get [www.killdisk.com](www.killdisk.com) and WIPE the drive completely clean before you attempting installing again.  I would suggest using the manual partition process, the ALTERNATE CD installation and make sure you make a separate root partition, home partition and SWAP partition.

Good luck.

---

### Post by Evil Garden Gnome on 2008-06-04
Alright. I will download killdisk and the alt cd for xubuntu. Thank you both for the help. Hopefully it will work.

---

### Post by Evil Garden Gnome on 2008-06-04
Hello. I am happy to say that the results were much better.

I grabbed the alt cd of the latest version of xubuntu and killdisk. I wiped the drive and proceeded to install xubuntu.

Unfortunately the computer crashed at around 70 or 80% of "select and install programs". I didn't see the descriptor though.

Does this mean another round of killdisk and reinstall? Can I recover the work I've already done?

I used 20gb for root, 6 for home, and 4 for swap (likely overkill). Could that have caused a problem?

---

### Post by lisati on 2008-06-05
There is hope. 

It might not be related but I had trouble installing from a Live CD onto a Toshiba Satellite A100, it seemed to take "forever" without achieving much more than sound effects from the disk drive. I eventually used an "alternate" disk. There were still a couple of "tweaks" that needed to be done to get the sound to work and to keep the USB mouse & keyboard alive for more than a few minutes.

---

### Post by Evil Garden Gnome on 2008-06-05
avetolle, wpshooter and lisati, thank you all.

I've got xubuntu running now. I pulled the swap to 1gb (a little more reasonable).

Runs great. Thank you all so very much.

---

