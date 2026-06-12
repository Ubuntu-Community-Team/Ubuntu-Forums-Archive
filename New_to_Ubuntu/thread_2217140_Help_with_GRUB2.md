---
title: "Help with GRUB2"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by DXXPublic on 2014-04-15
Hi all,

So im pretty new to Linux and im playing around with some of the distributions of it.  Currently i managed to install Ubuntu 12.04 and Kali Linux.

I want to edit the Grub menu because as i get updates the list keep getting bigger and bigger.   My noob question will be, how can i determine which grub/grub.cfg file to edit?  The one in Ubuntu, or the one in Kali?  Or it doesnt matter.

Anyways, thank you for your time

J

---

### Post by Double.J on 2014-04-15
Hi there!

Glad to hear you're experimenting!

typically the last linux installed will be the one configuring the boot menu. Short answer it's the one at the top of the list ;)

this is because unless you change it, an installer installs the first part of the bootloader to the first sector of the disk. Only one can fit there, so the next install writes over it.

They can be arranged differently - i choose to have my main ubuntu install always on /dev/sda and then each subsequent bootloader on that installs root or boot partition. It creates a chain loading situation where any option other than ubuntu goes to another grub screen, but it means that every time there's a kernel update on any of my systems, i willaytomatically load the latest kernel.

if you install one bootloader to the mbr and then write ovef it, the second one controls the boot list, so if you installed ubuntu first, and kali second, not only is kali in charge of the boot order, but it may not even boot the latest kernel for ubuntu - you have to update ubuntu, boot into kali and update grub.

Best tool to remove ubuntu kernels - [ubuntu tweak]("http://ubuntu-tweak.com")
best tool to organise grub how you want - [grub customizer]("http://www.ubuntugeek.com/how-to-install-grub-customizer-in-ubuntu-13-04.html")

Jj

---

### Post by DXXPublic on 2014-04-15
Thank you very much  :D 

Its all clear now.  I will go ahead and play with those new tools you pointed out.

Thanks again

---

### Post by Mark Phelps on 2014-04-15
Also, do NOT edit grub.cfg -- either of them.  Whenever you do an update that affects GRUB, that file gets automatically regenerated.  If you want default changes, you can make them using Grub-Customizer, as it will edit the Defaults file, instead.

---

