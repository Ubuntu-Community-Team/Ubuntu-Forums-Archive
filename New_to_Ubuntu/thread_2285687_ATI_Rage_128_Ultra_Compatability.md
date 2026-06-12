---
title: "ATI Rage 128 Ultra Compatability"
date: 2015-07-07
forum: New to Ubuntu
---

### Post by wyvern3 on 2015-07-07
I was given two Dell Dimension 4500 computers both running XP. I had been wanting to try Linux for some time now, but I didn't want to risk doing anything to my laptop since I'm a beginner. One of these computers ran fine with xp so I've left it alone mostly for now. The other however had had some of the files deleted when they tried to "wipe" the hard drive. I used PLoP and and USB to install Xubuntu 14.04 after trying to install 15.04 and it not being compatable with the video card. After I installed 14.04 I installed the updates, then restarted and everything worked fine. The next day there were more updates so I went ahead and installed them and tried to reboot it. I then had the same problem as I had had with 15.04 with the loading screen going black then compressing to a bar across the top of the screen repeating horizontally like a strip of film. The computer will still run the OS as it came, but once the updates are installed it won't work. It appears to be an issue with the ATI Rage 128 Ultra video card. Both computers have them. Is there anything I can do to run Linux on these computers as is or would I need to replace the video card?

---

### Post by mastablasta on 2015-07-08
replace it if you can.

card will work with software acceleration. the CPu will be used to draw the picture rather than GPU (which is more efficient for these kind of tasks). it will be good enough ot do some internet browsing, maybe some simple 2D games but not much more than that.

try to boot it with nomodeset boot parameter & see if it get's you to the desktop. if so we can help you make the "fix" permanent.: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by mörgæs on 2015-07-08
It's a very weak card. If you find a replacement which does not eat more power than the powersupply is able to deal with you could try swapping. 

Another option is Vesa drivers. See the link in my signature for details.

---

### Post by wyvern3 on 2015-07-09
Do you have any graphics cards you would recommend? I'm not really sure about the compatability issues, but I'm trying to learn. I'm having trouble getting the boot options to load. I've tried pressing the F6 key, but nothing appears to happen, nor with any of the other Fn keys.

---

### Post by mörgæs on 2015-07-10
Did you try booting both with the standard and the alternate Lubuntu ISO? 

I don't have enough overview to recommend a particular card, sorry. It's a matter of what fits to the slot.

---

### Post by mastablasta on 2015-07-10
128 is likely AGP. there aren't many new ones around (In fact I found only 1). 2nd hand ones are floating around though. you would need to check the motherboard documentation to see which are compatible. even then....

boot options - try holding shift on boot to get the grub up and then add nomodeset to the boot line.: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by wyvern3 on 2015-07-10
Okay I went into the grub and I had a little bit of trouble trying to figure out exactly what you're talking about so I may not have done it right. I went to the command line and entered ```
GRUB_CMDLINE_LINUX_DEFAULT= nomodeset
``` I then went back and clicked on Ubuntu which started the boot sequence. It got stuck on a black page with two rows of red spots on the top of the page. No I haven't tried Lubuntu yet, just Xubuntu.

---

### Post by Geoffrey_Arndt on 2015-07-10
That doesn't look right . . . . please read masta's link a couple posts above . . . the instructions are clear but you have to scroll down a way to see the section on nomodeset entry

---

### Post by wyvern3 on 2015-07-10
Sorry, I didn't read down far enough the first time. I added the nomodeset entry and booted. It stopped on the screen with the same red spots as before, but with some jumbled up white text near the middle of the screen.

---

### Post by Geoffrey_Arndt on 2015-07-10
Xubuntu should run well on your hardware, but, do you know what was updated "the next day" ?    It's unusual the pc would run fine one day and not the next.    Might want to try a reinstall . . . I've had good results with Ubuntu Mate on similar hardware.

---

### Post by wyvern3 on 2015-07-10
I did try a reinstall, and as soon as I installed the system updates it did the exact same thing. I guess I should try different flavors and see if any of the others work, but I don't want to have to worry about my hardware not being compatible with an update with this computer or any other.

---

### Post by mörgæs on 2015-07-11
If the other flavours use the same kernel and xorg you are not likely to gain anything by switching. Again, Vesa drivers are a good option.

---

### Post by Brian_Huggins on 2015-12-16
Ever have any luck with r128?  I have one computer with the AGP ATI Rage 128 Ultra 32MB (was the top of that line back then lol).  I tried live cd's of different flavors of Ubuntu 14.04.  I'm pretty sure even Lubuntu but I might try again because I'm not 100% sure.  Ended up trying 12.04 Kubuntu and I decided to use it.  During the time I had it I installed the various DE's (onto the 12.04 core of course) and now I'm deciding to go to Xubuntu (but I'm having to use 12.04) because Kubuntu is too much for it even on 12.04.  It works but gets laggy.  I'm wondering if anyone has gotten anything to work on any *buntu 14.04.

---

### Post by mörgæs on 2015-12-17
X/Lubuntu 12.04 is out of support and should not be used.

Though it might not be able to run a live boot it could still be capable of installing a [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") 14.04 or 15.10.

---

