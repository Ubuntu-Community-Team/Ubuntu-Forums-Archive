---
title: "Need help configuring grub for additional op system"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by phread59 on 2008-07-27
I just repartitioned my main Ubuntu drive and installed 64 bit Ubuntu on the same drive as my 32 bit installation.  According to Gparted it is on SDC3.  I have 2 IDE drives and 1 SATA drive.  Currently the 1 IDE has Windows and the second is partitioned but empty. 

For now I just want to add the 64 bit to my original 32 bit grub settings.  I am not sure how to configure the root portion of the chain loader option.  Chainloading would probably be the easiest.  I don't want to reconfig each time a kernel update is done.  

I hope I'm not being too obtuse.  I just need some help setting up the   Root(hd_,_) portion.  Any help would be appreciated.  BTW I believe I installed grub to the new partition with the 64 bit using manual install.

Oh yea a stupid question.  Would I install the whole commands for chainloading above the end of debian kernels list or after with windows?

Mark Shuman

---

### Post by mikewhatever on 2008-07-27
Can you post the outputs of the following:
> sudo fdisk -l
cat /boot/grub/device.map

---

### Post by caljohnsmith on 2008-07-28
Since your new 64-bit Ubuntu is on the same drive as your 32-bit Ubuntu, and you can boot the 32-bit fine, in your menu.lst you should use root (hdX,Y) where X will be the same what you use for your 32-bit Ubuntu (maybe 2 since sdc is your 3rd HDD), and the Y will be 2 since you said the 64-bit Ubuntu is on /dev/sdc3.

But if you want to load the 64-bit Ubuntu using the chainloader notation, you must have an additional Grub installed into the boot sector of the sdc3 partition. That is an option when you install Ubuntu, to install Grub to a partition's boot sector vs. the MBR; when you go through the part about installing Grub (and I think you have to hit the "advanced" button if I remember correctly), you can install Grub to (hdX,2) which is sdc3, and not to just (hdX) which would be the MBR. 

If you need more details let me know.

---

