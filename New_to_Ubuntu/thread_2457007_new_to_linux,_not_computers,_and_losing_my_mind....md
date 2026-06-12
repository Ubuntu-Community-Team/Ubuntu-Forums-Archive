---
title: "new to linux, not computers, and losing my mind..."
date: 2021-01-24
forum: New to Ubuntu
---

### Post by flybynight-187 on 2021-01-24
So, a windows 10 update broke my sound,...again.. So i did some reading, and linux supports all the programs i use often, as well as games.
Ubuntu came recommended after a day of reading, managed the install, and to get the Nvidia drivers working using the updater.  Cant get my realtek sound to make so much as a beep. 
have tried various commands i found hunting online, and it seems that the hdmi of the 2080Ti is what is trying to be used.  Cannot for the life of me figure out how to install and configure the alsa-driver-RTv5.18rc8.tar i downloaded from the realtek website.
Ive worked in windows platforms for 2+decades doing cad/cam and 3ds work,...THIS is making me feel dumb.
Can someone please point me in the proper steps??

---

### Post by ActionParsnip on 2021-01-24
It's a new OS for you so you need to learn. You'll learn just the same way you learned Windows, by using the OS.

---

### Post by ActionParsnip on 2021-01-24
Please follow this guide
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Please give the link created in step 3. Also make sure you have the latest BIOS and that sound is enabled there. You may want to reset settings and reconfigure the BIOS from scratch as well. Make a note if you have used secure boot as well, you'll need to set this to the same setting if the OS is to boot

---

### Post by rsteinmetz70112 on 2021-01-24
I think your biggest problem is trying to use Linux like you used Windows.

For example you said you downloaded drivers from the Realtek site. That is almost never a good idea in Linux. With Ubuntu most drivers are automatically installed and loaded on installation and boot.
The file you downloaded from the Realtek site alsa-driver-RTv5.18rc8.tar is a Tape ARchive and needs to be extracted to be useful. Usually those files are actually delivered as alsa-driver-RTv5.18rc8.tar.bz2 the bz2 is a bzip compression which also need to be decompressed.

To Review:

How did you install Ubuntu? 
[LIST]
[*]Is it on the raw hardware? 
[*]Is it a dual boot?
[*]Is it in a hypervisor?

[/LIST]
What is your hardware?

What version of Ubuntu did you install?  
[LIST]
[*]Most people here will recommend 20.04 LTS for new users unless you have brand new hardware which may not be supported yet.
[/LIST]
 
Please be very specific.

People here are knowledgeable who are willing to help someone who works at getting answers, but we cannot know what you've already done unless you tell us.

**Good luck and welcome to Linux.**

P. S. Since you were having trouble with this in Windows are your sure your hardware is functioning correctly?

---

