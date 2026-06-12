---
title: "fwcutter issues now"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-04-28
how can i install it. im having issues following directions. im afraid of screwing things up and having to start all over

---

### Post by adult swim on 2008-04-28
have you ever used any fwcutter pacakges before?

---

### Post by PatrickMoore on 2008-04-28
i never really succeeded in installing. luckily this has been much less painful than my attempt to install 7.10

---

### Post by adult swim on 2008-04-28
so youve got a broadcom card?  can you connect to the internet wired?

---

### Post by PatrickMoore on 2008-04-28
no i cannot im on our desktop right now. our modem only works with windows

---

### Post by adult swim on 2008-04-28
do you have your live cd?

---

### Post by PatrickMoore on 2008-04-28
i sure do

---

### Post by adult swim on 2008-04-28
woops, ive seen where some people were able to get the b43-fwcutter package from the live cd but i cant seem to find it on mine.  do you have any removable media like a usb drive or cd that you could take a file from your windows install to your ubuntu install?

---

### Post by PatrickMoore on 2008-04-28
i do and i have fw cutter downloaded on my jump drive. do i need a specific  driver for my wireless or is there a linux specific driver that i need.

---

### Post by adult swim on 2008-04-28
have you already tried to run the b43-fwcutter.deb in ubuntu?

---

### Post by PatrickMoore on 2008-04-28
> **adult swim said:**
> have you already tried to run the b43-fwcutter.deb in ubuntu?

do i need to enter that in the terminal. i cannot install outside the terminal

---

### Post by PatrickMoore on 2008-04-28
i can install fwcutter via terminal but its stating 

the bcm43xx driver needs extracted firmware. this firmware can be automatically fetched and extracted as part of installing this package

fetch and extract firmware

yes    no

im not choosing until someone tells me what to do

---

### Post by adult swim on 2008-04-28
with no internet connection you cant fetch the firmare, dont worry about that though.
open a terminal and copy in ```
lspci | grep Broadcom\ Corporation
```
paste what you get
edit: i forgot you couldnt copy and paste!  the symbol after lspci is shift+\

---

### Post by PatrickMoore on 2008-04-28
i got nothing but if i enter "lspci" i get


00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2) 
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2) 
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2) 
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2) 
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2) 
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2) 
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) 
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) 
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2) 
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2) 
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3) 
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3) 
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3) 
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) 
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) 
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) 
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1) 
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) 
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2) 
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by adult swim on 2008-04-28
neat, 03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01), was what i was looking for.  before we get a little more complicated, is there any possible way for you to hookup your ubuntu install directly to the internet, like directly from the modem or router?

---

### Post by PatrickMoore on 2008-04-28
no unfortunately my moden is formatted for windows. thank you att.

---

### Post by adult swim on 2008-04-28
go to [http://bu3sch.de/b43/fwcutter](http://bu3sch.de/b43/fwcutter) and download b43-fwcutter-011. next go to [http://downloads.openwrt.org/sources](http://downloads.openwrt.org/sources) and download broadcom-wl-4.80.53.0.tar.bz2. save these on your jump drive.  then boot to ubuntu and move the two files to your home folder, which you can just drag and drop (the home folder is located at places/home folder).  run the following commands, one line at a time.  it would probably be easiest to save the text from this message to a .txt file on your jump drive also, that way you could open it from linux and then copy and paste.
open up a terminal, applications/accessories/terminal, and enter these commands
```
tar xjf b43-fwcutter-011.tar.bz2

cd b43-fwcutter-011

make

cd

tar xjf broadcom-wl-4.80.53.0.tar.bz2

cd broadcom-wl-4.80.53.0/kmod

sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o
```
after doing this you will need to restart your computer.  if you dont see any wireless connections available from the network applet in your taskbar, go to system/administration/network and click on the unlock button. it will ask you for your password and then select wireless network and click properties.  once you are in properties click the roaming mode button, click ok and then click close.  now go back to the network applet in your taskbar and left click it, you should see wireless networks.

---

### Post by PatrickMoore on 2008-04-28
> **adult swim said:**
> go to [http://bu3sch.de/b43/fwcutter](http://bu3sch.de/b43/fwcutter) and download b43-fwcutter-011. next go to [http://downloads.openwrt.org/sources](http://downloads.openwrt.org/sources) and download broadcom-wl-4.80.53.0.tar.bz2. save these on your jump drive.  then boot to ubuntu and move the two files to your home folder, which you can just drag and drop (the home folder is located at places/home folder).  run the following commands, one line at a time.  it would probably be easiest to save the text from this message to a .txt file on your jump drive also, that way you could open it from linux and then copy and paste.
open up a terminal, applications/accessories/terminal, and enter these commands
```
tar xjf b43-fwcutter-011.tar.bz2

cd b43-fwcutter-011

make

cd

tar xjf broadcom-wl-4.80.53.0.tar.bz2

cd broadcom-wl-4.80.53.0/kmod

sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o
```
after doing this you will need to restart your computer.  if you dont see any wireless connections available from the network applet in your taskbar, go to system/administration/network and click on the unlock button. it will ask you for your password and then select wireless network and click properties.  once you are in properties click the roaming mode button, click ok and then click close.  now go back to the network applet in your taskbar and left click it, you should see wireless networks.


when i enter the first command i get
cannot open: no such file in directory
 tar: error is not recoverable: exiting now
 tar: child returned status 2
 tar: error exit delayed from previous errors

---

### Post by PatrickMoore on 2008-04-28
i extracted the files to the desktop is that ok?

---

### Post by adult swim on 2008-04-28
whenever you moved the files from your pen drive to the hard drive, did you put them on the desktop or put them in your home folder?

---

### Post by PatrickMoore on 2008-04-28
> **adult swim said:**
> whenever you moved the files from your pen drive to the hard drive, did you put them on the desktop or put them in your home folder?

i just dragged and dropped them to the desktop

---

### Post by adult swim on 2008-04-28
have you arleady extracted both files to the desktop, did you right click them and select extract here?

---

### Post by PatrickMoore on 2008-04-28
> **adult swim said:**
> have you arleady extracted both files to the desktop, did you right click them and select extract here?

yes. should i move them to my home folder?

---

### Post by adult swim on 2008-04-28
move those files to your home folder (the ones that you extracted) and then type these in from the terminal. the reason i suggest putting them into the home folder is because you would have a couple of folders cluttering up your desktop if they were left on the desktop.
```
cd b43-fwcutter-011

make

cd

cd broadcom-wl-4.80.53.0/kmod

sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o
```

---

### Post by PatrickMoore on 2008-04-28
patrick@patrick-laptop:~/broadcom-wl-4.80.53.0/kmod$ sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o 


This file is recognised as: 
  ID         :  FW11 
  filename   :  wl_apsta.o 
  version    :  351.126 
  MD5        :  9207bc565c2fc9fa1591f6c7911d3fc0 
Extracting b43/ucode4.fw 
Extracting b43/ucode5.fw 
Extracting b43/ucode11.fw 
Extracting b43/ucode13.fw 
Extracting b43/pcm4.fw 
Extracting b43/pcm5.fw 
Extracting b43/b0g0initvals4.fw 
Extracting b43/b0g0bsinitvals4.fw 
Extracting b43/a0g0initvals4.fw 
Extracting b43/a0g0bsinitvals4.fw 
Extracting b43/b0g0initvals5.fw 
Extracting b43/b0g0bsinitvals5.fw 
Extracting b43/a0g0initvals5.fw 
Extracting b43/a0g1initvals5.fw 
Extracting b43/a0g0bsinitvals5.fw 
Extracting b43/a0g1bsinitvals5.fw 
Extracting b43/lp0initvals13.fw 
Extracting b43/lp0bsinitvals13.fw 
Extracting b43/b0g0initvals13.fw 
Extracting b43/b0g0bsinitvals13.fw 
Extracting b43/a0g1initvals13.fw 
Extracting b43/a0g1bsinitvals13.fw 

i think i may have it. does this look right

---

### Post by adult swim on 2008-04-28
it looks like it! can you see any wireless networks available?

---

### Post by PatrickMoore on 2008-04-28
i have it up now many thanks you are pretty fabulous

---

### Post by adult swim on 2008-04-28
great!  happy surfing!

---

