---
title: "[SOLVED] a quick bit of help"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-05-23
[http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation)

could somebody please explain to me how i install this driver for my webcam...i just cant seem to understand what its telling me at all :( :(

---

### Post by rich.bradshaw on 2008-05-23
Try the instructions here:

[http://wiki.mediati.org/R5u870/Packages](http://wiki.mediati.org/R5u870/Packages)

Use the Debian/Ubuntu section, and just copy paste the instructions into a terminal. Don't type the $ in front of them!

---

### Post by bwhite82 on 2008-05-23
Basically, its giving you two options to install the driver, download the *stable* tarball or if you want the absolute latest, bleeding edge idriver that they are working on, you can use the program "subversion" (available for you to install in Synaptic) to download it.

Lets go with the latest, follow these steps:

1) Goto a command line and type:
> sudo apt-get install subversion build-essential

2) Make sure you're in your home directory then create a new one:
> cd ~/
> mkdir svn
> cd svn

3) Issue the command:
> svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) r5u870
> ls (To see the directory name it has created)
> cd [created directory]

3) Compile it and install it:
> make
> sudo make install

4) Insert the kernel module:
> sudo modprobe r5u870

You should then have webcam functionality.

---

### Post by betterthanjordan79 on 2008-05-23
..almost got done...made it to the last command and i got this

> daniel@Computer:~/svn/r5u870$ sudo modprobe r5u870 
sudo: unable to resolve host Computer


---

### Post by bwhite82 on 2008-05-23
> **betterthanjordan79 said:**
> ..almost got done...made it to the last command and i got this

Hmmm..thats odd. Well see if the driver got loaded anyway:

> lsmod | grep r5u870

If you see output, its loaded.

---

### Post by betterthanjordan79 on 2008-05-23
...ah i think it loaded..ud no better here

> daniel@Computer:~$ lsmod | grep r5u870 
r5u870                 27716  0 
usbcam                 48512  1 r5u870
usbcore               146028  6 r5u870,usbcam,uvcvideo,ehci_hcd,uhci_hcd


---

### Post by bwhite82 on 2008-05-23
Yes its loaded. Is it working and plugged-in? Are you sure that is the correct driver for your webcam? Is it a USB cam? If so, post the output of:
> lsusb

---

### Post by betterthanjordan79 on 2008-05-23
well i think its the correct driver - i have a built in webcam on my hp pavilion dv6000 laptop. 

theres the output of lsusb

> Bus 005 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

edit - also i cant seem to get it to work but im only tryin it with cheese!

---

### Post by bwhite82 on 2008-05-23
Alright, we'll get there eventually. So its not a USB cam, its built in, so to find out the chipset, issue the command (and post the results here):

> lspci

---

### Post by betterthanjordan79 on 2008-05-23
> daniel@Computer:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


there ya go-thanks for this help to

---

### Post by bwhite82 on 2008-05-23
Alright, heres what I want you to do. Restart your computer, after you're back in Ubuntu, issue the command:
> dmesg | grep -i r5

All of these commands are for me to help you. I need to know whether the system is recognizing your hardware and assigning the correct driver to it.

I'm reading another thread: [http://ubuntuforums.org/showthread.php?t=617748](http://ubuntuforums.org/showthread.php?t=617748)
And not seeing much success with this webcam from other users, except one person who used Skype2. So try installing that and see if its working. Also is the light on the cam on?

BTW, webcams in linux have been notoriously difficult to get working if at all.

---

### Post by betterthanjordan79 on 2008-05-23
> daniel@Computer:~$ dmesg | grep -i r5 
[   27.076261] usbcam: registering driver r5u870 0.11.1SVN
[   27.076298] r5u870-0: Detected HP Pavilion Webcam (UVC)
[   28.119880] r5u870-0: registered as video0
[   28.119914] usbcore: registered new interface driver r5u870


ill install skype2 now and no the light doesnt turn on at all

---

### Post by bwhite82 on 2008-05-23
Alright, its registering your webcam, it should be working fine. Another program to try is Ekiga. At any rate, since you installed the latest bleeding edge driver, that may be the issue. So, if its not working. You need to uninstall that driver and install the stable release:

1) Remove driver and uninstall it:
> sudo modprobe -r r5u870
> cd [driver compile directory] (Should be in /home/yourusername/svn/foldername)
> sudo make uninstall

2) Download the latest *stable* release:
[http://mediati.org/r5u870/r5u870-0.11.0.tar.gz](http://mediati.org/r5u870/r5u870-0.11.0.tar.gz)
Right click on it whereever you saved it, and click "extract".

3) CD to that directory and install it:
> cd [extracted files directory]
> make
> [QUOTE]sudo make install
sudo modprobe r5u870[/QUOTE]

---

### Post by betterthanjordan79 on 2008-05-23
....yh webcam works with skype2 aswell...pity i dont use skype...ah well.

i wonder how it works through skype but not other programs like cheese

---

### Post by betterthanjordan79 on 2008-05-23
theres a screenshot of it workin in skype...dont think ya can tell to much from that tho...oh nd obviously the blue light is on wen the cam is mounted in skype

---

### Post by bwhite82 on 2008-05-23
> **betterthanjordan79 said:**
> theres a screenshot of it workin in skype...dont think ya can tell to much from that tho...oh nd obviously the blue light is on wen the cam is mounted in skype

Yeah, its working. Not sure why not in Cheese or other programs. Is there any settings within cheese to maybe get it working? I don't use cheese or webcams in particular so I can't check myself. You can also try Ekiga or try installing the stable driver using the steps I've posted above.

---

### Post by betterthanjordan79 on 2008-05-23
just got it working in ekiga by choosing a different video device plugin so im guessing the reason its not working in cheese and other such programs is because there using the wrong plugin. there doesnt seem to be an option to change the plugin for cheese either.

is it possible to make the computer know to use that driver by default for all programs?

---

### Post by bwhite82 on 2008-05-23
Actually, just tried my own built-in webcam w/ cheese and Ekiga for the first time ever. Its working in Ekiga but not cheese. So my guess is to try a different cam program. I didn't see any configuration files for cheese either.

Edit: Cheese is a relatively young application still, so it'll have to mature more for it to become useful.
EditEdit: There are a ton of useful cam apps out there, it only depends on what you are trying to accomplish with your cam. See here for more: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by betterthanjordan79 on 2008-05-23
i just found out that cheese uses gstreamer so i ran the command 

> gstreamer-properties

to see what i could work with and seen that there was a tester program and i tested my cam and it does work.

thats a million for all your hard work!!

---

### Post by bwhite82 on 2008-05-23
Excellent, that worked for me as well. Glad everything is sorted out for you. Please mark this thread as solved.

-Cheers

---

