---
title: "Upgrading to 12.04 LTS Failed"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by missmable on 2012-05-04
I tried to upgrade from Oneiric Ocelot to Precise Pangolin yesterday and my system froze during installation. I left it overnight, hoping it would fix itself but it didn't so I had to force a restart. 

My computer is partitioned, with the majority allocated to Windows 7, and when I chose to restart in Ubuntu, the computer froze again at the blank purple screen before you even get to the user accounts to log in. 

How do I fix this?? Please help! :confused:

---

### Post by oldfred on 2012-05-04
If you are past the grub menu, then it probably is a video issue. Often nomodeset added to the linux line in grub as you boot will fix it.

Do you get grub menu? And what video card do you have?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by missmable on 2012-05-04
I went to Device Manager --> Display Adapters and it says "Intel(R) 4 Series Internal Chipset"

I'm not sure which one is the grub menu. Upon restart, I'm asked to choose between Windows and Linux and when I choose Linux, it just goes to a blank, purple screen and stays there.

The Linux upgrade never finished. It froze while saying it was doing something like "Preparing libc6" - or something having to do with lib6.

Sorry, I'm quite bad at this.

---

### Post by growingneeds on 2012-05-04
Froze at purple screen? It is possible that the upgrading process broke the system. Personally, I would backup important files in my home folder on Oneiric by booting into a Live CD. After that I would do a new installation of Precise. In all this, I would not edit the partition tables in any way, choosing only to reformat the partition that housed Oneiric.

---

### Post by missmable on 2012-05-04
How do I get/make a Live CD? And how do I boot into it? Sorry, again, not very good at this!

And if the Precise installation failed the first time, how do I avoid it on the second go round?

---

### Post by oldfred on 2012-05-04
Have you tried recovery mode, since grub loads and you get menu?

You can run several updates and get to command line.

Generally Intel video just works?

You should have an Ubuntu liveCd or USB  and a Windows repair CD or USB for the current version so you can make repairs. With Ubuntu then you can also boot and get online with the liveCD,if need be.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by rillerille on 2012-05-04
I have similar problem....
 
I upgraded and all went well, after entering my password desktop go brown and i can see blank icons to the left. I guess it is a graphics issue, going into recoverymode gives me the same result.
 
I cant see my desktop, nor do anything but shutdown or restart.
 
Advice please..
 
Best regards 
Richard

---

### Post by fooman on 2012-05-04
> **missmable said:**
> 
The Linux upgrade never finished. It froze while saying it was doing something like "Preparing libc6" - or something having to do with lib6.


sorry this is too late as you have already abandoned the update, but...

i had the exact same thing happen to me on 3 different updates in the last 2 days!  the fix was actually quite simple:

when you get to the point where it says "Preparing libc6" (after only about a minute or 2 into the installation), look  in the bottom of the update window and  there you will see it says *terminal* with an arrow next to it....click the arrow to reveal the terminal window below, and you will see that the update/install is actually prompting you to give it the "ok" to *configure libc6*,  you need to reply by saying "ok"....you do that by pressing the "tab" key.  that should highlight the word "ok" in the terminal,  then press "enter" on your keyboard to complete and continue. 

the update *will not* continue unless you reply with the ok.  it will sit,  apparently frozen waiting for you open the terminal, say ok and continue...

after that,  don't go away  because there will be 2 or 3 more such prompts before the update completes.  the good news is....the upgrades went flawlessly after that on all 3 computers:  a lenovo T61 thinkpad,  a lenovo t410 thinkpad,  and a lenovo k330 ideacentre desktop.

...i think the update should open that terminal window automatically when it gets to that point (Preparing libc6?),  as a new user will not know enough to open the terminal window and reveal the prompt to continue.

hope that helps others out there.

---

### Post by oleink on 2012-05-07
> **missmable said:**
> I went to Device Manager --> Display Adapters and it says "Intel(R) 4 Series Internal Chipset"

I'm not sure which one is the grub menu. Upon restart, I'm asked to choose between Windows and Linux and when I choose Linux, it just goes to a blank, purple screen and stays there.

The Linux upgrade never finished. It froze while saying it was doing something like "Preparing libc6" - or something having to do with lib6.

Sorry, I'm quite bad at this.


This is why ubuntu upgrades are worse than they used to be.  Does anyone remember when the terminal showed up by itself?  All you have to do is click the little arrow while upgrading and hit enter to the prompts (only a few) and the install will continue on its way

---

