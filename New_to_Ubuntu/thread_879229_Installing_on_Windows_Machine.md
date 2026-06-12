---
title: "Installing on Windows Machine"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by utgalois4234 on 2008-08-03
I'm currently downloading Ubuntu on a Windows machine with XP Professional, and I was wondering if it would be possible (and if so, how), once I complete my download, to completely uninstall windows and everything else that was done in Windows, including all saved files, programs, and so on. Thanks a lot.

---

### Post by PCessna on 2008-08-03
> **utgalois4234 said:**
> I'm currently downloading Ubuntu on a Windows machine with XP Professional, and I was wondering if it would be possible (and if so, how), once I complete my download, to completely uninstall windows and everything else that was done in Windows, including all saved files, programs, and so on. Thanks a lot.

You can't uninstall windows, when installing ubuntu, tell it to use the whole drive

Cheers
-PCessna

Edit: It will write over everything and windows will be completely lost, hope this helps

---

### Post by Paqman on 2008-08-03
Sure, when you install Ubuntu you'll be asked how much of the disk you want to give to Ubuntu. If you select "Use entire disk" then Windows will be completely overwritten. Easy as that.

Make sure everything is working fine in Ubuntu when you run the LiveCD first though. Making sure you can get an internet connection is especially important.

---

### Post by utgalois4234 on 2008-08-03
Thanks a lot; that is exactly what I was hoping. I do have one question though, regarding connecting to my wireless network. I have a Netgear router and a USB receiver that I use, and I imagine I will consequently need to install the driver in Ubuntu to connect; should I just be able to install it as usual (I apologize for my ignorance; I am a Ph.D. student in mathematics who incidentally knows very little about computers, and my computer at school has Ubuntu with all the necessary software installed, and I just wanted to set up my home PC to mirror it more or less). Thanks again.

---

### Post by OutOfReach on 2008-08-03
Well you should try out the LiveCD and see if the wireless works.

---

### Post by bwainscott on 2008-08-03
Glad to hear you are kicking windoze.  I am about to buy a preloaded Dell with 8.04.  The wireless really depends on which one it is.  

Also, there is some funky stuff sometimes that you need to do to get ubuntu to see the usb wireless as a wireless device.  Holler back if the livcd give you no love.

Here is a trick I read to add USB devices in Hardy
In a terminal:

Code:
sudo gedit /etc/init.d/mountdevsubfs.sh2.
Now remove " # " symbols from the front of following lines of code :

Code:
        #mkdir -p /dev/bus/usb/.usbfs
	#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700         ,devmode=0600,listmode=0644
	#ln -s .usbfs/devices /dev/bus/usb/devices
	#mount --rbind /dev/bus/usb /proc/bus/usb
code:

---

