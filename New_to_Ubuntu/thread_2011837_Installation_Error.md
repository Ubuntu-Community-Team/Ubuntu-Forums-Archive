---
title: "Installation Error?"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by Joshuabouffard on 2012-06-27
Hey, JoshuaBouffard here, And today I was going to install Ubuntu 12. 04

I reached the screen where It asks if i Want to Test Ubuntu Or install, so on and so forth.

So i Clicked install, After this My Screen Went Flashing with a black underscore IT doesn't change basically i cant do anything.

Any ideas on how to fix?

~Joshua Bouffard

Photo of Error: [http://s1092.photobucket.com/albums/i413/JoshuaBouffard/?action=view&current=UBUNTU.png](http://s1092.photobucket.com/albums/i413/JoshuaBouffard/?action=view&current=UBUNTU.png)

---

### Post by oldfred on 2012-06-27
It will sometimes show that for a few seconds before doing anything, but if after a bit nothing happens it is often a video issue. So you get little icons at bottom or just a few seconds first? That is keyboard & accessiblity meaning hit any key if issues.

What video card/chip do you have. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

