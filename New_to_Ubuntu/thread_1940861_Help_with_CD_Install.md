---
title: "Help with CD Install"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by davidmgf on 2012-03-14
Hi,

I am new to Ubuntu, but not to Linux. I have made a CD of 11.10 and tested the installation on the CD before using it to install from. The CD properly recognized my monitors but the installation made from the installation did not.

I have tried to edit the X config files but they are not used in the exact manner i am familiar with and i don't appear to be finding the display drivers i need even though the CD worked fine and I would have been happy to at least start with what is on the CD.

Is there a way to get THAT install put on my hard drive instead of whatever it is putting there or is that just the current state of 11.10 and i need to go back to an older version?

Thank you,

David

---

### Post by tbhatia4 on 2012-03-14
> **davidmgf said:**
> Hi,

I am new to Ubuntu, but not to Linux. I have made a CD of 11.10 and tested the installation on the CD before using it to install from. The CD properly recognized my monitors but the installation made from the installation did not.

I have tried to edit the X config files but they are not used in the exact manner i am familiar with and i don't appear to be finding the display drivers i need even though the CD worked fine and I would have been happy to at least start with what is on the CD.

Is there a way to get THAT install put on my hard drive instead of whatever it is putting there or is that just the current state of 11.10 and i need to go back to an older version?

Thank you,

David

there is no way rather than a fresh install to go ack to a previous version

---

### Post by adstri on 2012-03-14
Hi David 

What GPU do you have, you maybe missing a driver which is leaving its output undetected when you have finished the install? When you try booting without the live CD do you get any output? 

Adam

---

### Post by Holdolin on 2012-03-14
Do you get an image at all from the install?  What video card are you using?  You may need to get a driver for your card.

---

### Post by sudodus on 2012-03-14
Welcome to the Ubuntu Forums!

- Please describe your computer, and in particular, your graphics card or chip!

- What is working and what is not right now in the installed system? 
- Are you getting any graphics mode at all, or only text mode?
- Have you tried boot options?
- What graphics driver is running?

---

### Post by davidmgf on 2012-03-14
Computer: Shuttle SN26P
GPU        : NVidia GeForce 7950 GX2 (dual cards in sli)
Monitor1  : Dell 15in
Monitor2  : Dell 30 in (3007 WFP)

Both the CD & HD Installations see Monitor1

The CD installation sees both monitors and lets me configure them at least partially (I need to reset the resolution on the 3007 WFP but the default of 1280x800 is acceptable to start with - i can fix it later)

The real problem is that the HD install doesn't match the CD install and the CD install is close enough to what i need that I would prefer starting with it.

The HD install doesn't seem to recognize my gpu and doesn't see the 3007 WFP at all and I have enough new to learn about Ubuntu's implementation of X that i need to have a monitor i can easily see to work on. I did attempt to install a driver for the nvidia board and it did install and activate one that did not fix the problem (likely due to all the X file changes that need to be made. 

So, really.. if I could just get the CD install on the HD, I would consider that to be an acceptable starting point.. i can use the computer with the larger monitor.. the smaller one is very hard for me to read because i do not have good vision (not correctable with glasses) which is why i have a large 30 in monitor.. I only use the 15 in monitor for images.

David

---

### Post by sudodus on 2012-03-14
You can make a small partition (for example 5 GB) with FAT32 on the hard drive, and use Unetbootin to make it like a live USB drive. I suggest 5 GB, because you can add a 4 GB casper-rw file for persistence. [s]Of course you can also make a swap partition, if you don't have one already. but don't add an extra swap partition.[/s]

See for example the last post in this thread
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")
or boot directly from the iso file as described in the following link
[[COLOR="red"]_http://ubuntuforums.org/showpost.php?p=11227153&postcount=349_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11227153&postcount=349")

*Edit: But I think that your problem is the graphics driver, and when you get that working, you should be better off with a regular install.*

---

### Post by Holdolin on 2012-03-14
Have you installed the Nvidia drivers?

---

### Post by davidmgf on 2012-03-14
Yes, it has the the "current" nvidia driver, 173.14.30

---

