---
title: "Setting up Ubuntu"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by will_s54 on 2008-07-13
Am having major probs with my main computer so I am going to change the way things are set up. At the moment I have a dual boot system with Vista and they both share the same hard disk. Now I want to make that hard disc just Vista and install Ubuntu on another hard drive, actally that drive will be only for Ubuntu and my 3rd Hard drive will be or both to share.

Now I dont want Ubuntu to be able to access my Vista hard drive and I dont want Vista to be able to access the Ubuntu drive .

I am going to totally clean installations of both systems as all my data is on the 3rd drive. Will Ubunti give me a choise as to what drive I can install it on ?  Will the Grub boot loader still be on my C: drive ( Vista) ?  Any suggestions ?

---

### Post by davbren on 2008-07-13
OK first off there is no reason for you to stop Ubuntu accessing you windows drive. As far as I know, Vista won't do it anyway without a patch.

If you have two drives then its easy. You say you're reinstalling both anyway so install vista first on the necessary drive. Then install Ubuntu on the other drive. It should be as easy as that. I personally would suggest doing a live cd install rather than using wubi through vista. 

If vista doesn't turn up on the grub menu, (its happened before) there is this tutorial that will take you through it from the beginning.

During the Ubuntu setup there will be an option for which drive to install it to. In here just make sure you pick the empty drive...

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

---

### Post by Dedoimedo on 2008-07-13
Hello,

The GRUB bootloader won't be on your C: partition. It will be installed to MBR of whatever hard disk you use / assign, and the configuration files for GRUB will most likely be located on the same partition as /root (or at most, a dedicated /boot partition).

Cheers,
Dedoimedo

---

