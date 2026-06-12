---
title: "Nothing happens after installation"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by IGGt on 2012-08-11
HI, I just installed a copy of Ubuntu 12.04 to a PC I had (no OS on it previously), installation went through fine. It said I needed to restart so I pressed enter, and now when the PC boots, nothing happens, just a blank screen.

I'm new to Linux so though this (Ubuntu) would be a good place to start, but it looks like I've been beaten at the first hurdle.

Is it something I've done, or is there an Ubuntu problem at work here? Any ideas would be apprecia[LEFT][/LEFT]ted.

---

### Post by TheFu on 2012-08-11
How did Ubuntu run directly from the LiveCD?  Where all your devices properly recognized?

That's the first test **before** installing any Linux-based OS.
If that works well, then you shouldn't have any issues after an install, but if you do, the next thing to do is watch the boot screen - just press the <esc> key until you see it at boot time.  Look for errors and write them down exactly.

Issues generally don't prevent a login screen, since most are due to vendors not providing Linux/Ubuntu drivers for their hardware.  Early in the boot, the main issues are around disk controllers, strange partitioning, hardware failures or a little later in the boot process, video drivers.

The best advice I can give is to post the exact vendor and model of your PC here - googling for "{vendor} {model} ubuntu install" can help too. Some laptops need special boot instructions, for example.  If your PC is home-built, posting the chipsets and MB model might get you more help.

---

### Post by Sidewinder1 on 2012-08-11
Also, make sure to md5sum the ISO that you've downloaded; even if you've acquired  it (the Ubuntu ISO), through peer to peer protocol (torrent) which has error checking, it's best to be absolutely certain that you have a perfect copy. If unfamiliar, here's a link:
[https://en.wikipedia.org/wiki/Md5sum](https://en.wikipedia.org/wiki/Md5sum)
Once you've verified that both hashes match exactly then burn the ISO (at the slowest speed) and test (Try Ubuntu) it from the LiveCd environment. Once that's accomplished then follow TheFu's excellent advice above. Good luck!
And, BTW, Welcome to Ubuntu and Ubuntuforums.org.

Side

---

### Post by IGGt on 2012-08-12
Hi, I just tried running it from the CD, and it worked fine (except that it wouldn't connect to my WPA wireless network - but I'm not to worried about that).

So I clicked the icon to 'install' Ubuntu, and ran through the process again. As before it appeared to go through fine, and as before I restarted it and nothing happens.

I notice that there is a slight red cast to the screen just after  I hit the power button, but then that disappears. Strangely though, I don't even get to the Bios screen any more (F2 for settings / F12 for setup etc.).

After a few moments there is a 'bongo' type sound, and then the hard drive light stops flashing, and that is it.

I tried pressing esc at various points but nothing happenned.

The PC is a DELL Optiplex SX270 and the monitor is a HP 1702.

---

### Post by IGGt on 2012-08-12
OK, now I am really confused????

The bios page is back. So I pressed F12 "Boot Menu", for here I chose option 6 "Boot to Utility Partition". After this, it loaded Ubuntu desktop and appeared to be running fine!!

So to check it wasn't a one-off I repeated the process, and now it doesn't work. Selecting these options, I now go the GRUB menu.

I select option 1 "Ubuntu with Linux 3.2.0-23-generic-pae", and then I get the blank screen and start again.

I tried going past the bios screen and pressing escape, and that puts me in the GRUB menu again, with the same result.

So I tried option 2 in the GRUB menu "Ubuntu with Linux 3.2.0-23-generic-pae with recovery console", from here I got the message
"Running in Low Graphics Mode. Screen, Graphics card, input Device could not be detected" You will need to configure these yourself."

then there was options for "low Graphics Mode" which basically booted to a command line, where I rebooted from.

I tried the option to reconfigure the graphics, and the only seemingly relevant option was to use failsafex mode, which was seemingly a default screen resolution etc. but still failed to boot into a desktop.

So now I am trying to figure out why it would work once, and not again (and yes, I did take this CD out).

---

### Post by TheFu on 2012-08-12
It sounds, but I do not **KNOW** that this model uses a strange graphics setup.

I googled "Optiplex SX270 ubuntu 12.04 install" and found this thread:
[https://www.linuxquestions.org/questions/linux-server-73/after-installation-of-ubuntu-10-4-server-edition-screen-shuts-off-809546/](https://www.linuxquestions.org/questions/linux-server-73/after-installation-of-ubuntu-10-4-server-edition-screen-shuts-off-809546/) which seemed to a boot option that worked.

---

### Post by IGGt on 2012-08-12
Cheers, I had a read through that, but from what I can tell the solution was to reinstall, then apply 'nomodeset', but I can't see how or where they applied this.

---

