---
title: "low resolution, ubuntu 11.04"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by bluesix on 2011-09-25
It is probably user error because I am really new to computers (the beyond playing wow and watching porn side of computers)


when I boot off of my flash drive and run Ubuntu, the resolution is set at the atrocious 640x480 or something and I can't even see to click the Install button or move the window far enough up to be able to click it. I dont know how to open command window. But the most peculiar and irritating part is that I read all the threads and found the one where it told me to Settings->hardware->monitors and I was stoked. However it doesnt detect my monitors after I click detect monitors. They remain unknown. Also, when I try to click the button to bring up the different resolutions it just turns red and does nothing. Arrows dont work nothing. It just turns red. 

wathafidun.jpg

---

### Post by bluesix on 2011-09-25
I just tried to run the wubi and I got this error:

Windows - No Disk

   Exception Processing Message 0xc0000013 Parameters...

then its 4 hella long numbers but it wont let me copy paste. Ill edit with them as soon as I type it all out.


Edit: full error numbers

after the first line ends with parameters the 4 numbers follow 3 on one line 1 on last line if that matters. 

0x000007FEFD827249 0x000000000000004 0x000007FEFD827240
0x000007FEFD827240

---

### Post by Mark Phelps on 2011-09-25
The resolution could be because you have an older video card or chip that is not supported anymore.

To see the make and model card/chip, open a terminal and enter "lspci".  Then, look for the line containing "VGA" -- and post that information back here.

---

### Post by bluesix on 2011-09-25
I'm on windows vista right now. Ubuntu is unmanageable at that resolution unuseable really. Also how do I open the command window in Ubuntu? Really stupid I know. Can I get you that info from windows somehow? I Have an ASUS 21 or something monitor DVI and a westinghouse 720 tv through HDMI thats like extra monitor for videos when im playing a game. just bought XFX Radeon HD6770 vid card.

---

### Post by MG&amp;TL on 2011-09-25
Ctrl-Alt-T brings up a terminal emulator, but if you can't see/read that, use Ctrl-Alt-F1, which will drop intoo a command prompt. Ctrl-Alt-F7 restores the GUI. Or at least it should.

---

### Post by bluesix on 2011-09-25
ok im going to run in ubuntu and try to do this give me a min to reboots.

---

### Post by bluesix on 2011-09-25
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
[COLOR=Sienna]01:00.0 VGA compatible controller: ATI Technologies Inc Device 68ba
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)[/COLOR]
ubuntu@ubuntu:~$

---

### Post by bcbc on 2011-09-25
> **bluesix said:**
> I just tried to run the wubi and I got this error:

Windows - No Disk

   Exception Processing Message 0xc0000013 Parameters...

then its 4 hella long numbers but it wont let me copy paste. Ill edit with them as soon as I type it all out.


Edit: full error numbers

after the first line ends with parameters the 4 numbers follow 3 on one line 1 on last line if that matters. 

0x000007FEFD827249 0x000000000000004 0x000007FEFD827240
0x000007FEFD827240
See [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

---

### Post by bluesix on 2011-09-25
OK running full scans with Norton. Comcast gave it to me for free. Will that be good enough?

---

### Post by bluesix on 2011-09-25
The more pressing issue for me is my lack of ability to change my resolution and do this all from ubuntu. It sucks rebooting constantly from OS to OS.

Edit : I wish I could give rep on these forums. Thank you so much for the responses!

Edit 2: Alright. So the problem could be caused by a worm, Norton itslef, or simply clicking through the error messages. Windows error seems to be WIP now.

Edit 3: Clicked through and now currently installing inside windows to have workable for resolution problem. Virus scan still running.


resolution and sound still not working though :(

---

### Post by Captain Smiley Pants on 2011-09-25
You may want to try running [EnvyNG](http://albertomilone.com/nvidia_scripts1.html) to see if it will install the proper video drivers, that is if Ubuntu is not prompting you to install propriety drivers already.

---

### Post by alegomaster on 2011-09-25
Did you build the computer, or did you buy it.

If you bought it can you tell me what company you bought it from.


Edit: Do you know if it uses crossfire x

---

### Post by wildmanne39 on 2011-09-25
Hi, captain smiley I clicked on the link you gave, it look interesting but it is not supported as of 10.04, so it is out dated.
Thank you

---

### Post by Captain Smiley Pants on 2011-09-25
Oh... Yes, it's been a while since I've had to use that and it appears to be outdated. Sorry. That used to be my go-to app for video drivers. :(

---

### Post by mörgæs on 2011-09-25
Changed the title to a more descriptive one.

---

### Post by bluesix on 2011-09-26
> **alegomaster said:**
> Did you build the computer, or did you buy it.

If you bought it can you tell me what company you bought it from.


Edit: Do you know if it uses crossfire x

I bought the computer built if that makes any sense. My friend who is computer smart compiled a list of parts and I ordered it from ibuypower.com a few years ago. I dont think it USES crossfire but I have no idea.

---

### Post by wildmanne39 on 2011-09-26
Hi, can you hit alt+f2 that will open dash then type additional drivers and it will show them, then click on additional drivers and there should be a driver for your video card in there, you need to be connected to the internet then click to install the driver, then restart ubuntu.
Thank you

---

### Post by bluesix on 2011-09-26
When I press alt+f2 it brings up the "Run Application" window. I can Run with file or Run in terminal. Neither option worked with Additional Driver typed into the box. I did however access the Additional Drivers through System Settings. No Proprietary Drivers are in use on this system and there are no options to select...

---

### Post by bluesix on 2011-09-26
I am moving in a day or two, and will no longer be using my TV as a second monitor. So after exhausting all of your suggestions and failing on my own, I wondered if the TV was ******* the system up somehow because it had previously given me problems with dual resolutions and the like. I shut down the computer and unplugged the HDMI that led to the TV. 

Upon restarting my computer for the first time I did not mash f12 to boot from my flash and had the option instead to boot Ubuntu or Microsoft. I chose Ubuntu and everything Installed, then updated and installed. I restarted to finish the update and everything works flawlessly so far out of the box. I activated the Proprietary Drive for my vid card anyhow because I figured the probably wrote a pretty good one :) 

My only question now is a really simple one. How much HD space do I have? When I inspect the properties of my "File System" its 12.2GB available. Previously in my jacked up version it had 320GB available. Did I somehow create some small section on my HD that is just Ubuntu? Can I access more if I need to?

_[IMG]http://s3.amazonaws.com/kym-assets/entries/icons/original/000/006/581/lonely-computer-guy-is-the-millionth-visitor-photo-u1.jpg?1312631863[/IMG]_

---

### Post by alegomaster on 2011-09-26
> **bluesix said:**
> I am moving in a day or two, and will no longer be using my TV as a second monitor. So after exhausting all of your suggestions and failing on my own, I wondered if the TV was ******* the system up somehow because it had previously given me problems with dual resolutions and the like. I shut down the computer and unplugged the HDMI that led to the TV. 
 
Upon restarting my computer for the first time I did not mash f12 to boot from my flash and had the option instead to boot Ubuntu or Microsoft. I chose Ubuntu and everything Installed, then updated and installed. I restarted to finish the update and everything works flawlessly so far out of the box. I activated the Proprietary Drive for my vid card anyhow because I figured the probably wrote a pretty good one :) 
 
My only question now is a really simple one. How much HD space do I have? When I inspect the properties of my "File System" its 12.2GB available. Previously in my jacked up version it had 320GB available. Did I somehow create some small section on my HD that is just Ubuntu? Can I access more if I need to?
 
_[IMG]http://s3.amazonaws.com/kym-assets/entries/icons/original/000/006/581/lonely-computer-guy-is-the-millionth-visitor-photo-u1.jpg?1312631863[/IMG]_
 
Great to hear. Now can you please mark the thread as solved. that is what you do when the thread question is answered.

---

