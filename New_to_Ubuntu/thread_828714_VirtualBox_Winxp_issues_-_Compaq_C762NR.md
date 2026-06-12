---
title: "VirtualBox Winxp issues - Compaq C762NR"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by julianna on 2008-06-14
OK Gang, here's the scoop.  Laptop less than 2 months old, came with Vista.  After 4 crashes and 1 wipeout, I switched.  A friend gave me Ubuntu Hardy.  A little research and I was able to install WinXP via VirtualBox, which allows me access to certain things currently unsupported.  The biggie, is, of course iTunes.  In the meantime, certain issues have come up, and maybe I'm not looking in the right spot.  They are:

1.  USB accessories currently not recognized.
2.  No sound from conexent sound card.

Both of these situations DO NOT exist in Ubuntu.  So, if anyone has an idea, I'm game to try it.

My one Ubuntu issue is keeping my WiFi working, but since it sees my usb adaptor with no problem, its' no big.

Thanks to all of you for Ubuntu and in advance for any advice you can offer.

---

### Post by Troll_the_Great on 2008-06-14
I don't know about the sound problem, but I think I can help with USB support.You installed virtual box from the repos, right?Via synaptic?You have to download a .deb file from Sun Microsystems and use that. I heard that has USB support.
Use this link, and from there choose the one that best suits your needs:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)  
 
I hope this helps.

---

### Post by julianna on 2008-06-14
My VB download was direct from SunMicro. The strange thing is, I have a USB wireless adaptor plugged in and can connect to the internet from XP - but it just doesn't want to see my external hard-drive.  Perhaps I missed something in the setup?

---

### Post by Troll_the_Great on 2008-06-14
This is strange...I'll look and if I find something I'll tell you.

---

### Post by julianna on 2008-06-15
Greetings from the west shore of Lake Michigan...

For what it is worth, this i d 10 T machine originally had vista installed. I cannot find compaq or hp drivers for XP.  When I can run iTunes under Ubuntu, i'll drop windows like a hot potato.

---

### Post by Lord Xeb on 2008-06-15
When you install WinXP under a virtual machine, you actually using virtual hardware and virtual drivers to trick XP into thinking it is actually on the host machine. You cannot get drivers for in a virtual machine because there would be a huge conflict. Trust me... I did it and it wasn't cool e_e.

Also, if want USB support in Virtualbox, DO NOT get the OSE version. Get the lastest one you can get. Then once things are done, just go to settings on on the virual machine and click USB Device so that it will be supported in the virutal machine. Next you have to mount it yourself... Well at least I had to so I dropped a virtual machine of WinXP and did a Virtial of Hardy to keep tabs on its progress. So far it is doing good >_>

---

### Post by hopelessone on 2008-06-15
Check this thread:

How To: Install VirtualBox on Ubuntu 8.04LTS (Hardy Heron) [Tutorial]
[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

There are 2 versions on their website...Download the ->Binaries (all platforms)
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Not the VirtualBox Open Source Edition (OSE) <- No USB...

Hope that helps ya..

---

### Post by julianna on 2008-06-15
OK - downloaded the Ubuntu 8.04 edition, x86.  The amd 64 does not want to work, which is strange consideing this pc is an amd64 Athlonx2...rotten vista core...checking out your how-to link in the meantime.

---

### Post by bumanie on 2008-06-15
You need the binary version of virtualbox to get usb support. Follow this [guide]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html") When I did it, my external hard drive was not recognised until I rebooted the virtual xp about 5 times - other usb devices seemed to be recognised straight away.

---

### Post by julianna on 2008-06-20
One problem solved one to go.  The latest release of Banshee syncs with IPODs, Wine doesn't yet, so the only thing left is being unable to "see" anything connected to a USB port.  The truth is out there...Thanks for all the advice, things are really coming together.

---

### Post by agentphish on 2008-06-21
Greetings. I have spent many hours compiling a complete driver set for XP for the C762NR after purchasing one 48 hours ago. I almost threw this machine out the window 2 times while doing it. Which I know would have solved nothing! :)

Please feel free to download and use it. My email is in the readme if you have any questions.

Thanks, and I hope it helps. I don't know much about linux, but i hope these drivers help you since you're trying to use windows.

Here's the link: [http://www.mediafire.com/?ona9rjhyn0d](http://www.mediafire.com/?ona9rjhyn0d) 

Good Luck!

---

### Post by julianna on 2008-06-23
Worked through this step by step.  I get the following error:
Failed to access the usb subsystem. Could not load the USB Proxy Service (VERR_FILE_NOT_FOUND).  The service might be not installed on the host computer.

Component:              Host
Interface:              Lhost
Callee:                 LMachine

Frankly, I cannot find a usb proxy service anywhere.  Any ideas you have will be greatly appreciated.  Thank you for the input.

---

### Post by agentphish on 2008-06-23
Updated Windows XP Installation instructions:

1. Open the bios and disable SATA
2. Change bios to start from CD Drive
3. IMPORTANT: Insert a Windows XP CD w/SP3 integrated....if you do not have SP3 this method will not work.
4. Proceed installing a fresh copy of xp
5. Download all the drivers with step-by-step installation instructions from here: [http://www.mediafire.com/?ona9rjhyn0d](http://www.mediafire.com/?ona9rjhyn0d)
6. You are done. Enjoy!

[http://www.xaqdesign.com/c762nr.html](http://www.xaqdesign.com/c762nr.html) full instructions there as well. 

Will be updated as more comes. I think I have the fix for the quicklaunch volume controls and overall audio issues.

You can check my thread w/ HP [here]("http://forums12.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1242782")... I haven't had a chance to test Cheryl G's recommendations for the audio/quicklaunch fix. 

Good luck, again hope this helps you somehow. I don't know anything about linux.

---

