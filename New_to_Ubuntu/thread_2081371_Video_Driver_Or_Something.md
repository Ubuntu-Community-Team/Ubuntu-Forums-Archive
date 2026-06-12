---
title: "Video Driver? Or Something?"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by kenizl86 on 2012-11-06
For some reason, my laptop (Dell Latitude D600) has lines on the screen. Not very noticeable lines, but enough to mess me up when I'm using Gimp. On startup when it shows the boot logo (Dell, with "F12 for Boot Menu" and whatnot), it has all these crazy lines and stuff going on. I know it's mainly not like this because when I booted it from the Xubuntu 12.04 CD (which I installed and am running currently) it has no video issued whatsoever and even the boot screen is fine. But after the second reboot (boot out of CD, then restart again) it goes back to blinking-line-madness. Does anyone know what's happening? Do I need some sort of Video Display Adapter Driver thing?

Thanks for any input!

---

### Post by papibe on 2012-11-06
Hi kenizl86.

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the link here.

Regards.

---

### Post by kenizl86 on 2012-11-06
All it said was:

```
bash: /var/log/Xorg.0.log: Permission denied

```


EDIT: Ohhh... Nevermind. I will post the contents of the file. I accidentally ran it instead.

---

### Post by kenizl86 on 2012-11-06
Here's the link:

[http://paste.ubuntu.com/1338540/](http://paste.ubuntu.com/1338540/)


Thanks for the reply!

---

### Post by papibe on 2012-11-06
Unfortunately, I won't be much help, as I don't have much experience with ATI cards.

I see that you have a ATI Radeon Mobility 9000, and you are using radeon, the open source driver (as the proprietary one no longer supports it). Beyond that, there's no mayor error or warning on the log.

Let's hope someone else will pitch in and provide a better diagnostic of what's going on. 

Best Regards.

---

### Post by kenizl86 on 2012-11-08
Okay. Well, if anyone has any ideas, it would be most appreciated.

---

### Post by mastablasta on 2012-11-08
what is your actual graphics card? do you knwo maybe? because mine gets detected as mobility eventhough it is not. it owuld be interesting to see what card it recognises during live boot.
 
in any case you are going to be using opensource drivers. 
 
have you tried any of the boot parameters? Use boot repair and grub options to change these: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
final option would be to use PPA for beta drivers, but cosidering it all works fine in live version i owuld say that corect drivers are already included but maybe not used.

---

### Post by kenizl86 on 2012-11-09
Okay, well is there anyway to detect what drivers are being used during a CD Live boot? And if so, would I be able to copy those drivers from the CD files and into my filesystem? Like downloading it into my computer?

When I had windows running on here, the Dell website insisted that the driver I needed was a Mobility Raedon 9000 (or something like that) driver. Well, it did the exact same thing when I had Windows after I installed the driver. Same annoying lines.

I'm new to Linux in general, so I'm not to Linux savvy. If you could explain how something is done besides just telling me it needs to be done, that would be great. Thanks for the input!    :)

---

### Post by MoebusNet on 2012-11-09
OK, I'm not running Xubuntu so this will be for Ubuntu 12.04.

To find which video card you have, in the upper-left corner of the desktop, the uppermost icon is called Dash Home. If you left-click on it you should be able to search for an application called Terminal. Typing ```
lspci | grep VGA
``` in the Terminal window should list hardware including your video card. That will return something similar to:```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
```

If you want to experiment with the default video driver *radeon* without changing your system, boot up from a Live-CD or Live-USB with changes to the boot options:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

My 2002 Dell D800 laptop needs a *nomodeset* boot option to boot without vertical lines and pointer corruption when booted using the *nouveau* video driver.

Our computers are old enough that the video card manufacturers no longer want to support the cards in these machines with the restricted drivers:

[https://help.ubuntu.com/community/RestrictedDrivers](https://help.ubuntu.com/community/RestrictedDrivers)

Xubuntu 11.10, 11.04 or even 10.04 may be the newest version giving you the ability to use the restricted drivers. I'm running Lubuntu 12.04 with xorg xserver pinned back to 11.10's version for that very reason. This is what I had to do:

[http://ubuntuforums.org/showthread.php?p=11909048#post11909048](http://ubuntuforums.org/showthread.php?p=11909048#post11909048)

---

### Post by MoebusNet on 2012-11-09
@kenizl86, I dug out my Dell Latitude D800 and traveled to a place where I can get a strong wireless signal, so let's see what I can do:

Booting Xubuntu 12.04.1 from a Live-CD, when the boot screen comes up I press any key to enter the boot option menu, choose my language and press F6 to choose a boot option. I need *nomodeset* so I use the up/down arrow keys to scroll to *nomodeset* then press ENTER to choose it. I then use the ESCAPE key to return to the menu to choose TRY XUBUNTU to boot from the Live-CD. This uses the nouveau video driver without some kernel options so that my desktop and pointer are not corrupted.

Note that I am running a D800 with an Nvidia card, and you are using a D600 with an ATI  card, so what works for my card won't work for yours as far as the restricted driver. However, I think you can experiment with the boot options for radeon from the Live-CD/Live-USB to see what works for you or doesn't without changing your installed system. Once you find a boot option that works, then you can see about making changes to your installed Xubuntu system.

Worth a try, anyway. :)

---

### Post by kenizl86 on 2012-11-11
I ran

```
sudo lshw -class display
```

And I got this:

```
*-display               
       description: VGA compatible controller
       product: Radeon RV250 [Mobility FireGL 9000]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master vga_palette cap_list rom
       configuration: driver=radeon latency=32 mingnt=8
       resources: irq:11 memory:e8000000-efffffff ioport:c000(size=256) memory:fcff0000-fcffffff memory:fc000000-fc01ffff

```

Is there a driver for this harware for Xubuntu? I know that before I used (when I had Windows XP on it) a Mobility Raedon 9000 driver, but it still made the screen all screwy.

I also ran:

```
lspci | grep VGA
```

And I got this:

```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Radeon RV250 [Mobility FireGL 9000] (rev 02)

```

By the way, I don't know how to change a driver on linux (I'm used to windows).

---

### Post by Mark Phelps on 2012-11-11
The only driver for that now is the default open-source Radeon driver -- and it is installed by default during setup.

---

### Post by kenizl86 on 2012-11-11
So then what is used during live-CD as a driver?

---

### Post by kenizl86 on 2012-11-12
Would I run:

```
sudo lshw -class display
```

To show what driver is being used? How would I see the driver being currently used in a Live-CD boot?

---

### Post by audiomick on 2012-11-12
> **kenizl86 said:**
> So then what is used during live-CD as a driver?

> **kenizl86 said:**
> Would I run:

```
sudo lshw -class display
```

To show what driver is being used? How would I see the driver being currently used in a Live-CD boot?

Same command for the live CD boot, and the Live environment will be using the default driver unless you have taken steps in the current boot to get something else going.

---

### Post by kenizl86 on 2012-11-21
Alright. I figured out how to fix it.
While trying to remember the keyboard shortcut for running a program, I accidentally pressed Ctrl-Alt-F2 and it brought me to this black screen and asked for my user and sign-in. I did so and promptly ran "sudo reboot".
After reboot, like magic, the lines in my screen disappeared!

After several shutdowns and whatnot, the lines have since remained obliterated.

Like I said, it was accidental, so does anybody have an idea of what happened? Just curious.

---

### Post by kenizl86 on 2012-11-21
No... Nevermind, it's broken again. I have no idea what happened. I'm going to look over this post and other places again and see if I can fix it.

---

### Post by MoebusNet on 2012-11-22
I don't have any solid answers for you, but this may give you some more information:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Note that this was written with Oneiric in mind and has not been updated for Precise. Nevertheless, it may give you some ideas on a direction to pursue.

---

