---
title: "Herp derp (Live disc not booting)"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by Dubslow on 2012-01-16
Hey guys. 
Just got a new laptop, and after fighting with the BIOS for a while (the screen doesn't even tell you what key to press to get to the BIOS) I finally got it to boot to the live disc made of 11.10 with the pendrivelinux.com installer recommended on the Ubuntu website (live disc made in Windows). After getting to GRUB, choosing either "Install Ubuntu" or "Try without installing" just lead to a black screen with nothing happening. The light on the USB flashes for around 10 seconds before stopping completely. Any ideas?

Edit: The 10.10 live disc I've kept for a while has worked just fine.

---

### Post by benpack101 on 2012-01-16
After creating the flashdrive with Ubuntu, did if give you an option to check to make sure it was installed correctly (if so, run that)

I would suggest downloading the iso first and then using pendrive (and choosing the iso)

Try these things and let us know how it goes!

---

### Post by wolfen69 on 2012-01-16
Installing from a usb drive has been hit or miss for me over the years. Sometimes you will need to re-image the usb drive and try again.

---

### Post by sudodus on 2012-01-16
It is hard from your description to know what is the error. So I suggest a few things to try.

0. If you have a CD drive, make a boot CD.

1. Try another tool for making the USB boot drive. I have good experience with Unetbootin.
[http://ubuntuforums.org/showpost.php?p=11546560&postcount=5](http://ubuntuforums.org/showpost.php?p=11546560&postcount=5)

2. Try another version of Ubuntu for example 10.04 LTS or 11.04, or another flavour, for example Lubuntu.

3. Try Linux Mint 11 or 9. It is based on Ubuntu and uses the same repositories.

If you still have no success, please post data about your computer  (motherboard, graphics chip, ...). Often a particular computer  co-operates better with one particular version and flavour of linux or a  particular boot configuration. And someone here may know what works  with your computer, and can share his/her experience.

---

### Post by Dubslow on 2012-01-17
Okay, now having retried with Startup Disk Creator on another Ubuntu comp that I have running, that produced exactly the same results. I downloaded the 11.10 iso, and used Startup Disk Creator to make the Live Disc on my flashdrive.

Of note, there is now a bootloader in the 11.10 startup disk, with 
```
Try Ubuntu without installing it
Install Ubuntu
Check disc for errors
```
as the options. On previous versions it just booted the Live Disc without asking you for anything.

All three options lead to a blank screen with nothing happening. This is an ASUS X54C laptop.

---

### Post by sudodus on 2012-01-17
Now we know more and I think you can get more specific help :-)

I suggest that you make a boot CD. Sometimes it is hard to make a full-featured boot USB drive. For example, often some options are lost compared to a boot CD. At the menu, press F6 to select boot options, that might solve your problem. See the following link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

There may be some (minor?) differences in the newest version compared to the pictures.

---

### Post by Dubslow on 2012-01-17
This is the first computer (out of at least 10) where a flash drive hasn't worked. As for F6, I don't really know what those options are or how to use them. (And I don't think I have a CD anywhere at the moment.)

Edit: Just tried this in another computer, and that one didn't have a boot menu, but had the little symbols at the bottom with a keyboard and a little stick figure inside a circle (the picture [here](https://help.ubuntu.com/community/Installation/FromUSBStickQuick) but nothing appears after that. No bootmenu appears. Why wouldn't the picture in the link appear in my own computer, and why would it have a bootmenu instead?

Edit2: My desktop does successfully boot to the live disc, unlike my laptop or my roommate's (though as I said his laptop gets further than mine). (Also did not go through a boot menu screen.)

Edit3: The reason this is so frustrating is that the 10.10 live disc booted and installed just fine, but 11.10 won't, and Ubuntu froze halfway through trying to update 11.04 to 11.10, which is why I was trying to do a fresh install anyways. Why would 10.10 live disc work but not 11.10? (I'm now trying to fix the install that's there now, unless someone can fix this live disc issue.)

Edit4: Well the borked-current-install is mostly unborked, except I don't have a GUI. I can access F[1-6] command lines, but the F7 GUI doesn't get passed the ```
* Checking battery state...                [ OK ]
```line. Any ideas there? EditWhatever: Google sort of fixed it, it works now if I start gdm manually.

---

