---
title: "After installing Nvidia driver, can no longer find the additional drivers tab"
date: 2015-07-28
forum: New to Ubuntu
---

### Post by Evil Wayz on 2015-07-28
[IMG]http://i58.tinypic.com/fwso75.jpg[/IMG]

I used to have this box.  Now I can't find it, I've tried under software, software updater, and software update but it has vanished.  I suppose i could just add repositories and keys manually but It would be nice to have this back.

EDIT:  Just discovered that screenshot no longer works, no matter what I do, full screen, current window or selection it creates a picture that shows up as solid green in image viewer.

---

### Post by oldfred on 2015-07-29
Please attach screen shots. Easy to do with Forum's Advanced Editor and paperclip icon.

With nVidia 610 you should just be able to install. Is that your model? If not we need to know model to know correct nVidia driver.
Either screen shot you show that now is not working?
Or from command line.

Are you booting with nomodeset? That often is required with nVidia.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

      [/URL]
 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

    
Purge old first, if not installed it may just show error.

 sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
To see what is in repository:
ubuntu-drivers devices

Then run 
sudo apt-get install {driver}
Where driver is correct one from ubuntu-drivers devices and nVidia site on one for your model card/chip.
example but use correct. Wrong one must be purged or issues, only install correct version.
sudo apt-get install nvidia-331-updates

---

### Post by Evil Wayz on 2015-07-29
Ok while looking for information about my video card I discovered that there is now an additional drivers  option at the top of system tools.preferences.

Ok the first link says to add nomodeset behind quiet splash, not replace it.  Which should I do?

Before you replied, I installed the 340 driver.  Now that I know my additional drivers tab isn't missing and my screen shots weren't working because for whatever reason when you take a screenshot of gnome mplayer while it's paused it shows up as all green.  All I have to do is use a different video player and I can take screenshots with gnome-screenshot or shutter. 

The geforce site recommends the 304 driver, which is three years old.  Since everything appears to be working should I keep this driver?  I think of ubuntu like  a land mine, the less I mess with it the better off I am.

---

### Post by CantankRus on 2015-07-29
The nvidia site shows you can use the latest drivers which means you don't have to stick with the legacy 304 driver.
Install the latest driver available to you.

---

### Post by Evil Wayz on 2015-07-29
I have a really old card, 7600gs.  Driver still works though.

---

### Post by oldfred on 2015-07-29
Most of the updates in the very new nVidia drivers are to support new cards that have new features. Sometimes those may interfere with an old card. So some strange issues may end up being from your current video driver.

They do some minor updates to legacy drivers.

If you reinstall the correct driver, be sure to totally purge currently installed driver and its settings.

I used to have a 7600, but one night I heard a pop. Was not sure if from computer or not. But it still worked. But next morning nothing worked. Later learned capacitors on some brands of 7600 versions would pop, noticeable open at top of capacitor. I replaced with a 9600 which worked well for years. Now have a 620, but that has same performance as 9600 per some reviews. And new Intel internal video is about same as the old 9600, or new system has decent video without add in card.

---

