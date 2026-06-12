---
title: "USB not booting on startup"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by coldcoffee on 2008-10-31
I have searched the forums, and if an answer is there I can't find it.

My problem is my computer will not boot from a usb pendrive. I have my computer BIOS to boot from usb before the hard drive. I have checked out my fstab file and there is no listing for sdc which would be the usb drive in question.

Do I need to add this to my fstab file for it to boot, or is there something else wrong here.

Thanks

---

### Post by Peter09 on 2008-10-31
Are you sure that the USB drive is bootable, if not your computer will ignore it.

---

### Post by Patb on 2008-10-31
Coldcoffee, the way you describe it, this has nothing to do with your fstab. The usb drive should at least try to boot before it reads (or creates in memory) a fstab file. 

I am presuming you are actually trying to boot from the usb drive and not just mount it so that its contents are visible. 

You might consider a couple of obvious checks:
[LIST]
[*]Does the usb drive have a bootable operating system on it?
[*]Does the usb drive boot okay in another computer?
[*]Does your computer satisfactorily boot from another bootable usb drive?
[*]How was the usb drive made?  
[*]Is the usb drive truly bootable?
[/LIST]
(Please bear with me if some of these questions are blindingly obvious :)).

For a guide on how to create a bootable usb drive, I would suggest you use Unetbootin. There is a guide here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I have used Unetbootin to create bootable usb drives for a variety of OS's. 
 
Hope this helps. Cheers, Pat.

---

### Post by coldcoffee on 2008-10-31
Thanks for the reply. I have considered all the questions you have asked and they are perfectly reasonable questions. I don't have easy access to another computer to see if it will boot on another computer. I will try today to see if I can get it to boot on another computer. I have installed different 7.10 and 8.04 on it and to the best of my knowledge should boot. I used the tutorials at [http://www.pendrivelinux.com](http://www.pendrivelinux.com).

I don't guess there is much need for anyone to reply till I can at least test it on another machine or two just on the off chance it just doesn't work with my computer.

Thank you very much for the suggestions and help.

---

### Post by C.S.Cameron on 2008-10-31
Often the flash drive shows up in BIOS as a hard drive.
To boot this, make it first in hard drive order, and do not tell bios to boot USB first.

---

### Post by coldcoffee on 2008-10-31
That makes sense to me. It shows up as sdg sometimes sdc, haven't quite figured that out yet, but that does make since since it is showing up sdsomething as opposed to scx or something else. Where as my primary ATA drive is sda and slave ATA drive is sdb. I will give that a go before going out of the way to find another computer.

I think the sdg sdc delima may have something to do with my making a /mnt/pendrive directory and a few other things though. I will look further into that when I get the chance later today.

---

