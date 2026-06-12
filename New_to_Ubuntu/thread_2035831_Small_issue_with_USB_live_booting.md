---
title: "Small issue with USB live booting"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by saturdaysequalyouth on 2012-07-31
Hi everyone, I'm having what I hope is a small issue with Try Ubuntu without installing. I'm trying to run Ubuntu live simply to see if my Win7 install has corrupted itself to the point it thinks it has (as in, having lost all photos and documents), but I can't get the live boot to work. When I boot up the computer (ASUS G73), a message quickly flashes up - 'error: "prefix" not set' and then it proceeds to a text based 3 option menu. When I hit try without installing, the screen disappears, the USB stick's activity light flashes for a few seconds, but then nothing happens. In one instance I left the computer for a few minutes to see if it loaded, but it never did. I should mention also that my house mate had tried it just before me, with the same USB stick, and everything worked perfectly for him.

If anyone has any ideas, they would be greatly appreciated. Thanks!

---

### Post by critin on 2012-07-31
Since you're getting to the 'Try' screen, and your friend used it successfully, I suspect the contents have become corrupted somehow.  I would reload the usb stick from the beginning.

It could be an ntfs corruption.  Can you get into Windows?  If so, run *chkdsk -- to *check and repair disk.  And always shut the machine down properly, no pushing the power button.

---

### Post by saturdaysequalyouth on 2012-07-31
Thanks for your suggestions! Unfortunately, it would seem that there is no corruption and it still works fine on my friend's system. I am unable to boot Windows, and so I'm super worried that you're probably correct in your NTFS corruption idea. I have one friend in town with a desktop computer (I'm currently in South America.. Not the best time for this to be happening..), so maybe I'll take the hard drive out and run it as a slave disc through their SATA

Also, I have been hitting the power button to switch off - unfortunately the GRUB that's being displayed has no other options

---

### Post by critin on 2012-07-31
> Also, I have been hitting the power button to switch off - unfortunately the GRUB that's being displayed has no other optionsThat's the quickest way to corruption.  Windows didn't have a shut off/restart option at the Start button?  Odd... If you can get a hold of a windows cd of the same type as yours, you could repair with it.  A real copy though, not an OEM.

Good luck!

---

### Post by oldfred on 2012-07-31
What video card/chip do you have. That is often an issue or it could be some other boot option is required.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'.

---

