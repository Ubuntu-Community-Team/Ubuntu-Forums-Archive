---
title: "Boot fail 12.04"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by ironrosefarms on 2012-09-26
Attempting to run Ubuntu 12.04 from dvd. boot begins from the dvd drive however then it shuts off the monitor and keyboard. If I manually turn on the monitor all I have is horizontal gray static lines.

HP Pavilion a1440n, pentium D two cores, 2gig memory, NVidia Geforce 7300LE graphics card.

Trying to assure that I have a working copy so I can then move to a different machine...

---

### Post by ajgreeny on 2012-09-26
When you boot from the DVD and get to the purple screen with the figure of a man and a keyboard at the bottom, hit any key, choose language, then use F6 to show many boot options.  Start by choosing **nomodeset** and see if that gets you a working desktop; if not try each option one by one.

It sounds as if this is a graphic card/driver problem, so once installed properly it will probably be possible to figure out a solution.

---

### Post by ironrosefarms on 2012-09-26
I'm not getting a purple screen. It starts with a black screen with a set of linux boot lines and a series of dots that builds as it progress' then goes black and the monitor and keyboard both shut off.

and thank you for your quick response!

---

### Post by critin on 2012-09-27
It does sound like a graphic issue, but can you try the cd on another computer to see if it does the same?  It may be a bad download or burn.

---

### Post by ironrosefarms on 2012-10-01
Not easily... Ummmm, have to see what I can make happen...

One thing that I question is I am having to use Sonic to burn the disc (it is what is on this borrowed unit). I tried to copy into the burn folder using the XP utility, but it will not allow the copy any ideas that way?

---

### Post by AndyOpie150 on 2012-10-01
Have you tried using the Penndrive Linux utility to configure a USB device bootable and install your .iso of choice from a list of close to 200 distros. It will auto pick the best mirror for the fastest download to help prevent the download from becoming corrupt. 
I think you might need to insure you have a clean download and try again.
You can use a MD5 sum utility to verify if it's a clean download (if the download site list the MD5 sum).

I like the USB drive install better than a CD. The USB drive is a little easier to tote around and every computer has a USB port (unless it an Android device or Tablet, then a SD card will work)

This worked great on my old 2003 Windows machine with sub-par graphics driver.

It can't hurt to make a CD of this as well (just in case): [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
I'm pretty sure the boot repair .iso wont work on a USB device.

---

### Post by Bufeu on 2012-10-01
Linux + nVidia drivers = [IMG]http://png-5.findicons.com/files/icons/438/dating/48/broken_heart.png[/IMG]

 It may just be a bad download or burn, but if fails after trying re-burn the disc with the lowest speed possible, I'm almost sure it's about drivers. Ubuntu doesn't come with all drivers pre-installed, it comes with open source drivers, written by the Ubuntu developers.
There's also *proprietary drivers*. Proprietary drivers can be installed manually or using jockey. This drivers is written by the hardware manufacture, and the source code is closed. The Ubuntu developers can, therefore, not fix bugs and problems. It's all up to the hardware manufactures to keep their own Linux drivers up-to-date.

Installing a proprietary driver for certain graphics cards may allow you   to use more advanced visual effects, but they may have limited functionality   or may not work at all, depending on the hardware manufacture.

AMD have been quite good at write good drivers to graphics cards, unlike nVidia. nVidia's drivers for Linux are know to be buggy, have several security holes or just don't work at all. I do not recommend to buy a nVidia graphic card if you are going to use Linux. In that case, go for an AMD/ATI instead. Moreover, nVidia has not been so willing to give out such information that is required to make open-source drivers, and that is the reason why the open-source drivers do not work so well you could wish.

My theory is that there's no drivers for your card at the moment, neither open source ones or closed source ones.

You can always try the text based installer and see if that works. If the installation works, install the drivers from that point.

---

### Post by Favux on 2012-10-02
Hi ironrosefarms,

Welcome to Ubuntu forums!


Is that a HP laptop from around 2005?  With an Nvidia video chipset:
```
lspci |grep VGA
```
the default video driver used by Ubuntu is the OSS nouveau driver.  It sounds like it does not support your chipset out of the box.

When you boot, arrow to the latest linux kernel line and press the e key.  Than will allow you to edit the kernel boot options for the current boot.  Find the part that says "quiet splash" and add 'nomodeset'.  So it looks like "quiet splash nomodeset".

What that will do is turn off the nouveau driver and force Ubuntu to use the VESA video driver.  See if that gets you to a gui.  If you are able to boot into the Desktop then click on the Ubuntu icon at the top of the taskbar (on the left) and enter "Additional Drivers".  It should recommend a proprietary Nvidia video driver for your chipset.  Make that active and when you reboot you should be OK.

The keyboard issue may or may not be related.  That might require another kernel boot parameter option.

---

### Post by ironrosefarms on 2012-10-02
Favux, not sure of the direction you are suggesting as I don't seem to be getting that far into the boot process. I get as far as white dots progressing then it shuts off the monitor and keyboard. Is there a key set I can use to enter into the area you are talking about?

---

### Post by Favux on 2012-10-02
Are you dual booting?  It sounded like you were because you said:
> It starts with a black screen with a set of linux boot lines
That sounds like the Grub splash screen and is what I'm talking about.  It should appear before the screen with the dots appears.

If you're not dual booting the Grub splash screen with the kernel lines and the Recovery Mode option won't show.  You should be able to get it by holding down the left shift key or maybe by repeatedly tapping it during boot.

---

### Post by ironrosefarms on 2012-10-02
left shift key, gotcha. Gonna give it a try.

---

