---
title: "hdmi sound and ati hd radeon 6000 graphics card"
date: 2013-11-03
forum: New to Ubuntu
---

### Post by jayclev on 2013-11-03
I'm trying out the live CD version of Ubuntu 12.04.3 LTS 64 bit and I noticed that the sound doesn't work.  I have the HDMI cable plugged into the back of the monitor going to my ATI HD radeon 6000 series card (the monitor has built in speakers).  When I open the sound menu, HDMI isn't listed as an option, just built in audio.  I went to AMD's website and tried to download the file called 'amd-catalyst-13.11-beta6-linux-x86.x86_64.run'.  It looks like a script file.  It tried to open/install it with the program gedit, but it is really slow.  Am I doing everything correct, or do I need to copy/paste the script file somewhere else?  I hope downloading this driver works.  The sound works fine when I boot back into Win 7 64 bit.

---

### Post by hg-knight on 2013-11-03
unsure if hdmi is supported as yet

---

### Post by coffeecat on 2013-11-03
First thing to remember is that if you are running a live session of Ubuntu from a CD, you can't install the proprietary catalyst driver. Well - you can, it will be installed to volatile memory, but it requires a reboot which means that you lose it as soon as you do so. Also, if you do ever install Ubuntu permanently and you want the proprietary driver, it is better to install it from the package manager rather than download an installer from the AMD website, particularly a beta one. You are also going about installing a run file the wrong way, but that's all a bit moot at the moment. If you do install Ubuntu permanently, people here will be able to tell you how to install the proprietary driver with a couple of mouse clicks.

HDMI output is disabled by default in the open source radeon driver, which is what the live CD uses.

[https://help.ubuntu.com/community/RadeonDriver#HDMI_Audio](https://help.ubuntu.com/community/RadeonDriver#HDMI_Audio)

Don't try the fix that is documented in the linked launchpad bug, the one that requires "radeon.audio=1" added to the boot options. That won't work with a live CD either. There is a different way of adding that boot option when you boot from a live CD, but it has to be done every time you boot. If you want to try that I can give you further details, but you might want to rethink what you want to achieve before I do. Running a live Ubuntu CD is only intended as a tryout or for using the live session for such things as maintenance/repair of installed operating systems, data rescue, temporary internet access, and the like. Using a live session for video output with hdmi is going to be clunky however you do it.

Have a think about all that and then get back to us to see what we can help you with.

---

### Post by jayclev on 2013-11-03
I downloaded Lubuntu, newest version and now I need to figure out how to get the sound from HDMI AMD ATI Radeon HD 6x series graphics card to work.  Is there a software package I should download, or maybe download the linux catalyst driver from AMD's website?  

Here is a generated report of my system it doesn't show the ATI Raedon HD graphics card for some reason, but it is a 6850, I think:

Processor	4x Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz
Memory	8141MB (598MB used)
Operating System	Ubuntu 13.10
User Name	jay (jay)
Date/Time	Sun 03 Nov 2013 01:49:16 PM PST
Display
Resolution	1920x1080 pixels
OpenGL Renderer	Unknown
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	HDA-Intel - HDA Intel PCH
Audio Adapter	HDA-Intel - HD-Audio Generic
Input Devices
Power Button	
Power Button	
HID 04b4:0033	
Microsoft Microsoft® SiderWinderTM X6 Keyboard	
HDA Intel PCH Front Headphone	
HDA Intel PCH Line Out	
HDA Intel PCH Line	
HDA Intel PCH Rear Mic	
HDA Intel PCH Front Mic	
HD-Audio Generic HDMI/DP,pcm	3=
Printers
No printers found	
SCSI Disks
HL-DT-ST BD-RE WH12LS38	
ATA ST500DM002-1BD14	
Operating System
Version
Kernel	Linux 3.11.0-12-generic (x86_64)
Compiled	#19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013
C Library	Unknown
Default C Compiler	Unknown
Distribution	Ubuntu 13.10

---

### Post by coffeecat on 2013-11-03
> **jayclev said:**
> I downloaded Lubuntu, newest version and now I need to figure out how to get the sound from HDMI AMD ATI Radeon HD 6x series graphics card to work.  Is there a software package I should download, or maybe download the linux catalyst driver from AMD's website?  

Did you read my post? Are you running Lubuntu live from a CD, or have you installed it? What applies to Ubuntu applies to Lubuntu in this regard.

---

### Post by jayclev on 2013-11-03
Yes, I pulled the trigger and I'm now running Lubuntu from my HDD.  I did try downloading from AMD's support site.  Here is the file:
 
 amd-driver-installer-catalyst-13-4-x86.x86_64.run

Under properties, the file is a shell script and the default program to run it is leafpad.  When I try to install by double-clicking, it asks to execute or execute in terminal.  When I choose execute, there is a pause, then a pop-up message says 'you need to run this installer as the super-user'.  If I choose execute in terminal, another 'DOS'-like black and white pop-up window brings up the path of file with a flashing cursor.  I guess that is where you would copy and paste the contents of the script?  Not sure.

---

### Post by coffeecat on 2013-11-03
Since you've now settled on Lubuntu, I've added the Lubuntu prefix to this thread.

As I said before, you're better off installing the AMD proprietary driver from the Ubuntu repository, where it is ready packaged for the system. All it takes is a few mouse clicks. I'm not familiar with the Lubuntu desktop, and you don't say which version of Lubuntu, so here's a link which describes where you might find the GUI utility for installing proprietary drivers.

[http://askubuntu.com/questions/197110/enable-drivers-on-lubuntu](http://askubuntu.com/questions/197110/enable-drivers-on-lubuntu)

Ignore the B43 driver at the beginning - that's a wireless driver - the additional drivers utility is for all types of proprietary driver. The latest entry there refers to the Other Software tab in Software and Updates, but I think that's wrong. Look for the Additional Drivers tab.

---

### Post by jayclev on 2013-11-03
I'm using Lubuntu 13.10, but after some research, I think the problem is that I need to upgrade the linux kernel to 3.5 or higher.  I've tried the other drivers but they didn't work.

---

### Post by walterorlin on 2013-11-05
Actually lubuntu 13.10 uses kernal 3.11 by defualt so I don't think that would solve the problem.

---

