---
title: "install natty from knoppix"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-09-29
I was 95% DONE ON AN UPGRADE TO NATTY AT THE LIBRARY AND IT CAME UNPLUGGED AND MAJOR DIDASTER, i CAN'T BOOT TO CD OR uSb. Sorry about the caps. I can boot into knoppix but the only directions I could find on installing ubuntu from Knoppix is real old and does't work.I believe I have the correct partitioins set up. I have 18GB for/ ext4 446GB ext4 for/home and 4 GB swap. I was tired after doing 9 upgrades and now have a mess,I just need to know how to make it boot then I can fix it from here I hope.

---

### Post by oldfred on 2011-09-30
If it was 95% can you chroot into it and repair it. Often the last part is the install of grub2's boot loader.

What boot loader does Knoppix use? If grub2 you can directly boot the ISO from the hard drive, but should not reinstall to the same partition.

---

### Post by cmcanulty on 2011-09-30
I reformatted the partitions so now I have 18GB/, 450GB/Home and 4 GB swap but still no OS. So how do I get ubuntu reinstalled. Both the flash drive and the CD freeze at splash screen forever.

---

### Post by oldfred on 2011-09-30
Often video issues. What video card do you have.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

---

