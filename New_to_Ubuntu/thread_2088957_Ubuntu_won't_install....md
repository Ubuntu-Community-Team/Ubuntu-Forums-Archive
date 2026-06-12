---
title: "Ubuntu won't install..."
date: 2012-11-27
forum: New to Ubuntu
---

### Post by Erik The Pope on 2012-11-27
Hi. I'm trying to install Ubuntu 12.04 or 12.10 or Dream Studio (superset of Unbuntu). On any of these, it will read the CD & proceed on but eventually stops reading the CD with a blinking cursor @ the top left of the screen. It is a home-built with an ASUS P5E3 Premium mb, 4 BG ram & an EVGA Force 8800 GTX (Invidia clone) video card. This computer worked fine with Windows & will boot correctly with a Boot It NG disk. It seem I've heard that Invidia cards have problems with Unbuntu. If so, how do I fix it if it won't install the OS? Thanks!

Erik The Pope

---

### Post by Bashing-om on 2012-11-27
Erik The Pope; Hi ! Welcome to the forum.

Try this and advise results:
from "try" ubuntu mode ::
Boot the installCD, soon as bios screen clears depress the shift key -> language screen -> escape to accept the default English -> menu options screen;
At this options screen press f6 -> boot options;
arrow down to the "nomodeset" option; enter to activate
press f10 to continue to boot to the desk top.

Play with ubuntu, insuring all devices operate. If so will advise on how to make the change permanent with a better graphics driver.

[INDENT][INDENT]just try'n to help
 
[/INDENT][/INDENT]

---

### Post by Erik The Pope on 2012-11-27
Thanks for responding. I tried the shift key & all that came up was boot:

No  other menu came up. When I tried it this time, it got a lot farther. It  quit when the colored screen was on and a msg that read "Wireless  networks available" came up; then it froze. The shift key thing sounds  promising (booting from an Unbuntu 12.04 disc). There are a couple  screens that come up with this mb: one that is a choice between

Never mind. This time when I held the shift key, the language menu came up, picked nomodeset, pushed the enter key but F10 was not a choice. It started to boot & got to the colored screen then froze (mouse as well). I'm going to try a different disk this time just for yuks. Let you know...

Erik The Pope

---

### Post by Erik The Pope on 2012-11-28
Tried 12.10 this time. The shift key thing did nothing but the "boot:" msg did come up. I wonder if I can type nomodeset then? Probably not...

Tried 12.04 again, this time the shift key worked. I picked nomodeset but hitting the enter key just removed the check mark that had appeared when I picked it. Maybe escape? Anyway, it froze up again with the Ubuntu dots picture.

Any other ideas? This is probably why Linux has a "difficult to use reputation", even tho Ubuntu is supposed to be one of the easiest Linux distros.  :)

I will try tomorrow...

Erik The Pope

---

### Post by varunendra on 2012-11-28
> **Erik The Pope said:**
> Tried 12.04 again, this time the shift key worked. I picked nomodeset but hitting the enter key just removed the check mark that had appeared when I picked it. Maybe escape? Anyway, it froze up again with the Ubuntu dots picture.
You may find these useful -
Various boot options, their details and how to use them (community wiki) : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some useful comments from P4man on using boot options : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I would suggest to stick with 12.04, as it is an LTS (supported until April 2017) and is supposed to be more stable.

---

### Post by mansonfan78 on 2012-11-28
Does your mb have onboard video?  If so, you could try switching to that in bios and then installing Ubuntu.  If it works we can get the nvidia card working later.

---

### Post by audiomick on 2012-11-28
> **varunendra said:**
> 
I would suggest to stick with 12.04, as it is an LTS (supported until April 2017) and is supposed to be more stable.

That wont give the OP the media creation applications, but Ubuntu Studio might be an option.
[http://ubuntustudio.org/]("http://ubuntustudio.org/")

I don't know about now, but they used to use the alternate installer which I think is the one that Debian uses. It is text based and a little more robust that the GUI one, or at least it was a couple of years back.

Anyway, I think if the suggestions to get around the video driver problem during the install work, all will be fine with dream studio.

---

### Post by varunendra on 2012-11-28
> **audiomick said:**
> That wont give the OP the media creation applications, but Ubuntu Studio might be an option.
Ah.., sorry, I forgot Erik is using a non-default distro. Although I believe installing the required apps shouldn't be an issue once the OS is installed. Of-course unless the mentioned distro uses some of its own, non-supported packages.

I myself started with Ubuntu-Studio (9.10), and unless there is any radical change since then, it contains nothing that is not available in default Ubuntu repos. But yes, it definitely saves you the (big) hassle of fine-tuning the system.

---

### Post by Erik The Pope on 2012-11-28
I am using the regular Ubuntu 12.04 D/L. Do you think that trying to use the 64 bit version might be causing me these problems? Also trying the vga= parameter. I did check the disk I was using & it was OK. I thought it was my video (BTW, the mb doesn't have built-in video so I can't try using that) but since it has progressed to the regular screen, maybe not. Gotta go to band practice now but will try some other stuff tomorrow. Been reading the links you have provided. Thanks!

Erik The Pope

---

### Post by varunendra on 2012-11-28
> **Erik The Pope said:**
> I am using the regular Ubuntu 12.04 D/L. Do you think that trying to use the 64 bit version might be causing me these problems? Also trying the vga= parameter. I did check the disk I was using & it was OK. I thought it was my video (BTW, the mb doesn't have built-in video so I can't try using that) but since it has progressed to the regular screen, maybe not. Gotta go to band practice now but will try some other stuff tomorrow. Been reading the links you have provided. Thanks!

Erik The Pope
You're welcome !

And I don't think it can be a 64 vs 32 bit issue. If your system supports 64 bit (which it obviously does in your case), there is not a single reason to prefer 32-bit over it.

The 'nomodeset' option is supposed to bypass the graphics related issues by using the basic graphics mode. But there may be other issues as well which it can't address. That's why reading those short guides about boot parameters may help you advance further.

Also, how did you check the disk integrity? There are two popular methods -
1) Checking the MD5Sum : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2) Using the "Check disk for defects.." option in live cd boot menu.

I'd suggest to check it both ways.

As a different approach, you may try the "Alternae" cd to install. Once installed, it is same as the regular "Desktop" version. It is an 'install-only' cd that runs the installation in text-only mode, thus requiring much less resources and avoiding issues that are inherent to the heavy GUI that the regular cd provides for 'live session'.

If you need or wish to download again, I'd strongly recommend to download via torrents. It downloads faster and ensures the integrity of downloaded stuff. Official link for torrent downloads : [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

.

---

### Post by mastablasta on 2012-11-29
to add to that, you should be able to hit esc when you have ubuntu dots on to see if there are any error "hidden" messages underneath the splash screen.

---

### Post by Erik The Pope on 2012-11-30
I did the check on the F6 screen. Also checked the memory with memtest. Both OK. I have only the SSD (Intel) connected. I was thinking about connecting only the Raptor to find out if the SSD has anything to do with this, which I don't think it is. Also, gonna try some other vga=xxx parameters. Sigh...

---

### Post by Erik The Pope on 2012-12-04
I tried the "alternate" version of Ubuntu & I thought it was going to work, but nnnooooooo!
It got to where it was partitioning the drive. Turned out that was the Raptor drive & it quit in the middle (33% done). I've got a BootIt NG disk in there now & apparently it doesn't see the SSD so I've got to check that. Aarrgghh!  :confused:

---

