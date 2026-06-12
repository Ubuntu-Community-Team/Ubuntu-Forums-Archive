---
title: "Finally got Ubuntu installed, now nothing works"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by Erik The Pope on 2012-12-12
Started a new thread because this is a new problem. I was having trouble installing Ubuntu from a CD/DVD so I installed Wubi on the Windows XP installation. Downloaded 12.04 (64 bit), took over an hour to D/L, started up fine. Then I installed a driver for my Nvidia video card & rebooted again. Came up fine; HOWEVER, the mouse will not do anything but move around. No names with hovering, nothing will run at all. I don't think this is what is supposed to happen! So now, I can boot up & then do nothing. Any ideas on how to fix this annoying problem w/o installing Ubuntu again?

Erik The Pope

---

### Post by mastablasta on 2012-12-12
did you check the md5sum of the downloaded image to make sure it is the same as the one on server?
 
how did you install the GPU drivers?

---

### Post by asifnaz on 2012-12-12
I think you should download ISO and burn it to a CD and try Live Cd first

---

### Post by Erik The Pope on 2012-12-12
I have 5 or 6 Live CDs, none of which would install; they would just stop working while installing. I will try them again & also try installing from a flash drive. It seems to me that it's a video problem (Nvidia card) but since it's not responding to mouse clicks, I have no idea how to go back to the "stock" video driver. Sigh...

Erik The Pope

---

### Post by oldfred on 2012-12-12
What nVidia card. 

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

            I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by Erik The Pope on 2012-12-12
Well, I thought it was a video problem but (at least so far) it was a mouse problem. With the Nvidia driver loaded, the mouse would move around but nothing would come up when I hovered over a program nor would anything happen when I clicked on anything. This was a Logitech mouse with a charger that plugged in a USB port. I replaced it with a MS mouse that has a Bluetooth adaptor, also with a USB plug. Then I got out a 12.04 CD & ran it to check on if it would work as a Live CD; however, I thought it would be quicker to see if it installed since that was the whole point. Lo & behold, it did & the mouse (BT) works fine. The video driver is still what it put on, I haven't updated the driver at all.

Now I will turn it on again to see if it boots up correctly. I did install it to my SSD (80 GB Intel), now I will see if it will upgrade some of my programs. Wish me luck...

Erik The Pope

---

