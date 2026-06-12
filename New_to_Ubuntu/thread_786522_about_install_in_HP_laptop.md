---
title: "about install in HP laptop"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by kjman83 on 2008-05-08
Model:Compaq 6515b
Processor:Mobile AMD Sempron(tm) Processor 3600+
Wireless Card:BCM94311MCG wlan mini-PCI
Graphics Card:: ATI Radeon Xpress 1250
Tribe (Version):8.04 BETA (Release 8.04(hardy))
32 bit or 64 bit:32
Boot Parameters (if any): <---What is it?


I'm using 8.04 BETA version.
I just tried booting by 8.04 LTS by try without anychange...mode.
in Beta case , I installed with noapic nolapic acip=off.
After typing that line, I can see the interface of 8.04.
So today I tried booting by LTS version, but any cases didn't show me
the interface.
When I typed 'acip=off'
I saw this message 'mp-bios bug : 8254 timer not connected to IO-APIC
When I typed 'nolapic'
I saw this message 'Loading, please wait...
                    Usb 3-1 :device not accepting address 2, error -62'
When I typed 'noapic nolapic'
I saw this message 'Loading, please wait...'
When I typed 'noapic nolapic acip=off'
I saw this message 'Loading, please wait...'
...when I booted without typing, laptop didn't work as well.

Actually I don't know the meaning of 'noapic nolapic acip=off'.
I just want to install LTS version and use power manager of my laptap, wireless.
Is there anyone who successed to install in HP perfectly?

---

### Post by gn2 on 2008-05-08
Try using the "Alternate CD" to install from instead of the normal CD.

---

### Post by kjman83 on 2008-05-08
Do you think It can be a good method to install?
Do you think I can use wireless and powermanager with my laptop in 8.04?
I just wonder .. so.. 
Now I have lot of things in my laptop , so I wanna be careful.

---

### Post by gn2 on 2008-05-08
Wireless will depend on whether there are working drivers for the adapter, it would appear from a quick search on the net that it will work OK.

Power management can be difficult, often suspend and hibernation will not work.
The only certain way to know if it will work is to try it once it's installed.

If you have data you wish to keep on the hard drive, you must make copies on removable media before continuing to install Ubuntu, or risk losing all your data.

---

### Post by kjman83 on 2008-05-08
Thank you for your reply.
I'm worried about alternative install.
I 've never done it. 
What should I do when I do it with alternative CD.
Should I also type something like noapic.... etc.?
If the CD can't be installed, Could I return to 8.04 Beta?

---

### Post by gn2 on 2008-05-08
The Alternative install is very simple.

Boot with the CD in the drive and select the first option, Install Ubuntu.

It's fairly straightforward and very similar to the normal installer.

If you overwrite an existing 8.04 Beta installation, you will not be able to return to it.

---

### Post by kjman83 on 2008-05-08
why I'm worried about it is that I installed 7.10 alternative CD before.
but I couldn't install. I don't know why ..
I Just installed 8.04 Beta. 
So., The worst situation is After installing and then fail to install, and then install Beta, but fail as well..
this is a big problem to me.
How do you think?

---

### Post by AlanB66 on 2008-05-08
Read this post ([http://ubuntuforums.org/showthread.php?t=749481](http://ubuntuforums.org/showthread.php?t=749481)) and see if this might apply for you. I have a Compaq and they're one and the same with HP now.

---

### Post by gn2 on 2008-05-08
The Alternate install procedure for 8.04 has been changed from the procedure for 7.10.

In 8.04 the Alternate installer is much simpler and installs the GUI automatically without having to make any text commands.

---

### Post by ubuntozack on 2008-05-08
I found it helpful to restart your computer then spin around your chair and yell hotsause!:popcorn:

---

### Post by kjman83 on 2008-05-08
To Alan 
Do you use Beta or LTS?
If you use LTS ,, Did you install LTS easily?

---

