---
title: "screen goes black during boot"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by funcify on 2011-12-22
So I have been having video performance issues lately, and decided to remove the proprietary fglrx drivers, and go back to the open-source ati drivers.  I followed the instructions given [HERE](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch).  So now I am losing video output while booting.  I am seeing the BIOS bootsplash, but the screen goes black before I make it to the lubuntu splashscreen. The hard-drive light is blinking, and I can hear it spinning.

Hmmmm :confused:

---

### Post by amjjawad on 2011-12-22
> **funcify said:**
> So I have been having video performance issues lately, and decided to remove the proprietary fglrx drivers, and go back to the open-source ati drivers.  I followed the instructions given [HERE]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch").  So now I am losing video output while booting.  I am seeing the BIOS bootsplash, but the screen goes black before I make it to the lubuntu splashscreen. The hard-drive light is blinking, and I can hear it spinning.

Hmmmm :confused:

Hello and Welcome to Ubuntu Forum :)

What is your OS? what release?

You need to include more information so we can help. Check this: [http://ubuntuforums.org/showpost.php?p=11532952&postcount=349](http://ubuntuforums.org/showpost.php?p=11532952&postcount=349)

---

### Post by MG&amp;TL on 2011-12-22
I'm not entirely sure what causes it, but I get this regardless of the driver with an NVIDIA card. I think it's something like an excessively low resolution. (so I guess you only see one pixel?)

---

### Post by funcify on 2011-12-22
> **amjjawad said:**
> Hello and Welcome to Ubuntu Forum :)

What is your OS? what release?

You need to include more information so we can help. Check this: [http://ubuntuforums.org/showpost.php?p=11532952&postcount=349](http://ubuntuforums.org/showpost.php?p=11532952&postcount=349)
Thanks for your response.

I am using a normal installation of 32-bit lubuntu 11.10 on my notebook.  However, I'm running off of the live usb at the moment due to the problem I described in my first post.

The specs of my notebook are:
Toshiba Satellite T135D-S1320
Processor: AMD Athlon Neo MV-40
Video: ATI Radeon 3200
RAM: 3GB DDR2 800MHz

---

### Post by garyhibdon on 2011-12-23
welcome to the forums.

first off, youre entire computer is overheating, which MAY be keeping the graphics cards from functioning properly.

secondly i would make sure that your bios is up to date with the newest release. 

finally, i would recomend enabling the built in graphics of your system in your bios just to get the system stable, and then mess with options as far as the video card. 

i personally was not able to get my nvidia properly working on 11.10, therefore i switched back to 10.10.

i know its not much help, but its a start. good luck man

---

### Post by funcify on 2011-12-23
> **garyhibdon said:**
> welcome to the forums.

first off, youre entire computer is overheating, which MAY be keeping the graphics cards from functioning properly.

secondly i would make sure that your bios is up to date with the newest release. 

finally, i would recomend enabling the built in graphics of your system in your bios just to get the system stable, and then mess with options as far as the video card. 

i personally was not able to get my nvidia properly working on 11.10, therefore i switched back to 10.10.

i know its not much help, but its a start. good luck man

It is getting warmer than I would like, but I don't think it is overheating.  I just did a fresh install of lubuntu 11.10, and everything seems fine now.  After updating, however, I am getting an error message - "cannot write bytes: broken pipe" - that appears after the lubuntu splash screen and before the desktop loads.  Doesn't appear to be affecting anything; just kind of annoying.

---

### Post by amjjawad on 2011-12-23
> **funcify said:**
> "cannot write bytes: broken pipe"

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/521298](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/521298)

Also, use this for more results: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by amjjawad on 2011-12-23
> **garyhibdon said:**
> secondly i would make sure that your bios is up to date with the newest release. 


+1
This is VERY important but honestly I did not mention it because I have no idea how to do that from Linux.

We have HP Pavilion DV6 Laptop. It was overheating. I contacted HP Customer Care and they send me the update for BIOS. After updating the BIOS, everything is ok. When I asked them about Linux, they said they can't support it unless the Laptop has pre-installed Linux which didn't make any sense to me.

Last night, I slept while that laptop was ON and when I woke up, it's was SO MUCH HOT and thank God it did not set a fire or something. It was on bed but on a stand so it's not fully covered but I guess my blanket was covering it. I pressed the Power Button and put it on the floor to cool down.
I must buy a cooling fan for it (it's not my laptop though but I use it).

If this is new machine, check with the vendor and see if they can provide some updates or perhaps you need to call the customer care?

Take it as an advice, don't ignore that, overheating is NOT good at all.

**Edit:**
I'm sorry, I got confused with your other thread: [http://ubuntuforums.org/showthread.php?t=1897815](http://ubuntuforums.org/showthread.php?t=1897815)

The above reply is for overheating issue.

---

### Post by garyhibdon on 2011-12-23
let the laptop stay on for about 10 mins, log into your bios, and check out the hardware manager. if it says that your cpu is >70 degrees C, then its too hot. to put it into perspective, 71*C is around 160*F. thats overheating temp. the heat that you are feeling is not necessarily how hot the internals are. Just a word for the wise

---

### Post by amjjawad on 2011-12-24
> **garyhibdon said:**
> let the laptop stay on for about 10 mins, log into your bios, and check out the hardware manager. if it says that your cpu is >70 degrees C, then its too hot. to put it into perspective, 71*C is around 160*F. thats overheating temp. the heat that you are feeling is not necessarily how hot the internals are. Just a word for the wise

Some BIOS don't really have that. I have two PCs, one with Gigabyte MB and the other with Intel MB. The one with Gigabyte does have that but the other does not.

:)

---

