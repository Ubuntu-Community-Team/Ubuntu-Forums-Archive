---
title: "Trouble installing Ubuntu 8.04"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by stromgald on 2008-05-07
I recently built three identical machines (hardware-wise, and almost identical in software) with XP Pro installed.  I'm trying to add Ubuntu 8.04 to them in a dual boot configuration.  I was successful with the first computer, but I'm on the second one and I'm getting a blank screen during install.

I've tried checking the system memory for errors and checking the disk for errors (using the LiveCD options), but I've come up with nothing.  When the screen is blank, the keyboard (NumLock, CapsLock) still responds, so I don't think it's hanging completely.  If it's a resolution issue, why didn't it show up with the first computer?

I've looked online and tried taking off the quiet, added in some things about framebuffers and such, but none of that worked.

Should I get the alternate/text-based install?  Does that really help if there's issues with boot up?  Won't it just do the same thing after the install is done through the command prompt?

Also, I read that Ctrl+Alt+F1 would bring up a terminal, but I'm not sure what I could do there since I'm very much a Linux novice.

I'm not at the computers now, so any advice on how to proceed when I get in tomorrow would be greatly appreciated.

Here's the computer configurations:
ASUS P5N-E SLI motherboard
Intel Core2Quad Q6600
4 GB OCZ RAM
XFX nVidia 9600GT graphics card (only one, no SLI)
Western Digital 250GB SATA HDD
Samsung 22" widescreen monitor

---

### Post by angelillo on 2008-05-07
I had a similar problem with a previous version (7.04). In that version, in the boot menu of the live CD, I was able to select the resolution pressing F4. In 8.04, maybe you can try pressing F4 and selecting "Safe graphics mode".
If it doesn't work, you can try the alternate CD instead the live CD. The alternate CD follows a text-only installation, so you shouldn't have resolution problems with your monitor.

---

### Post by stromgald on 2008-05-07
I read elsewhere that there's a difference in the live CD and alternate CD installations.  I don't mind the text based install, but I'd rather not try and figure out which packages are missing from the alternate CD install and have to install them manually.  

Is there a quick way to go from an alternate CD installation to what the LiveCD would do?

---

### Post by stromgald on 2008-05-07
OK, I've successfully installed on the other two computers.  They both required the "safe graphics mode" option.  

Now, I'm having the problem of poor resolutions.  The first one works fine from the beginning at 1680x1050.  The other two machines have max resolution of 1280x1024, which isn't so great for a 22" widescreen.  Will installing updates fix it?

---

### Post by angelillo on 2008-05-07
Maybe this post can help: 
[http://ubuntuforums.org/showpost.php?p=4903255&postcount=2]("http://ubuntuforums.org/showpost.php?p=4903255&postcount=2")

---

### Post by stromgald on 2008-05-09
Thanks for the help.:)

I couldn't get the resolution right even with the information in that thread, but I found a friend that's somewhat of a Linux expert and he did it from the command line.

---

