---
title: "Encryption, Dual Boot, &amp; GRUB"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by Polypro on 2011-10-08
Greetings, First Post

I'm ready to kick Windows to the curb (for the most part, see below) but I need to figure out how to accomplish what I want with Linux. I have searched numerous forums and have seen hints that what I want to do is possible, but nothing is all in one spot, easy to follow.

I have an Asus 1215N with a 128Gig SSD, that has no problem booting off USB or SD Card. I can either his ESC and select the boot device, or set it up as first in the BIOS.

What I want to do is this:

Install Windows 7 to the first 30Gig NTFS partition on the SSD. Then I would like to install Ubuntu 11.4, using LVM and LUKS on the remaining unpartitioned space on the HD (I can also partition that with G-Parted if need be, I'm a Linux newb and don't know if I should pre-format)

At this point, I assume GRUB (2?) would be the new boot loader. I then want to encrypt the entire Windows partition with TrueCrypt. TC should now be the new boot loader. I then need to somehow get GRUB (2?) onto the SD Card and bootable. The SD Card will be kept on my person at all times. 

Windows will be the decoy OS. When I want Linux, I should either be able to hit ESC in the TC Boot Loader and it will find GRUB on the SD Card, or I can boot to the SD Card directly.

Like I said, I've seen hints that all this is possible, I just need some help being a Linux newb...any links appreciated. I did find a good tutorial on installing LVM/LUKS with the Alternate Distro manually (Guided looks like it will kill the Windows Install?), so I think I'm good there.

Thanks,

NN

---

