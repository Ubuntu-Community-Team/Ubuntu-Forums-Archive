---
title: "Hardy net problems"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by hello_emo_boy on 2008-04-28
So I just installed Hardy and now my internet won't work.
I've read in a few places how to do it, but I only have wireless internet so I can't go through synaptics.

Any ideas?

I have a linksys wireless G with speedbooster pci card.

Cheers!

---

### Post by dokdoom on 2008-04-28
Synaptics has nothing to do your internet. You won't be able to install or update any packages without a net conenction. On one of your panels should be a network manager. When you left click on it it should show you the avilable wireless networks. Do you not see the network manager?

---

### Post by hello_emo_boy on 2008-04-28
Yes I clicked the network manager but there are no wireless networks listed. I know the card is working but when I go to activate the restricted driver, it says it can download anything.

---

### Post by dokdoom on 2008-04-28
You are correct, without an internet connection you are not going to download anything. Is your wireless switch turned on? If so find out which wireless card you have and google to see if anyone else is experience similar issues.

---

### Post by hello_emo_boy on 2008-04-28
Tried that, no luck. I do have a laptop so if there is somewhere I can download something, yay.

---

### Post by sam_delta on 2008-04-28
do you have a wired connection?, try pluggin in a cable and enable hardware drivers

sam

---

### Post by hello_emo_boy on 2008-04-29
No, I only have wireless and I'm a good 200 feet from a wired connection. All I have is 2 other laptops running wireless.

---

### Post by sam_delta on 2008-04-29
could you post the output of the following 2 commands, just to make sure which chipset your card has, and try to research on it.

```
lspci
lshw -C network
```

sam

---

### Post by hello_emo_boy on 2008-05-06
Ok, so here's what I got after those commands:

00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
07:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)

and here's for the second command

*-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:1d:7e:95:3a:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Does this mean anything? Am I going to die? I can't go to long without new episodes of Supernatural. I DON'T HAVE CABLE!!! *Tears*

---

### Post by sam_delta on 2008-05-06
the easiest way is to just plugg in a cable connection and download whatever the "hardware drivers" says you need to update.

if you definetly dont have a wired connection you can follow steps on post # 9 of the following link
[http://ubuntuforums.org/showthread.php?t=766800](http://ubuntuforums.org/showthread.php?t=766800)

NOTE:
make sure you uninstall b43-fwcutter before attempting installing it again (above link) by typing before starting the above link
```
sudo apt-get remove b43-fwcutter
```


tell us how it goes
sam

---

### Post by 85fb on 2008-05-07
i have a vostro 1500 with hardy 8.04. anyone know how to get ndiswrapper working properly without destroying my wired connection?

or at least cutter, it doesnt do anything when i try to install it. it finishes and dissapears. please help!

---

### Post by sam_delta on 2008-05-07
what chipset do you have? , if you dont know, post the output of :
```
lspci
```

you might consider starting your own thread so you grab more people's attention

sam

---

### Post by hello_emo_boy on 2008-05-08
Well I don't have b43 fwcutter installed at the moment and I downloaded all the packages is step 9 like you said.

However, when I tried to install the build-essential, it gives me an error saying it can't install libc6-dev.

---

### Post by hello_emo_boy on 2008-05-08
How do I start my own thread? I'm pretty new at this

---

### Post by hello_emo_boy on 2008-05-08
Here's the output for lspci:

00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
07:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)

---

### Post by sam_delta on 2008-05-08
@hello emo
this is your own thread, i was refering to 85fb that was asking for help in here.


alright, itll be usefull if you copy the error you got while trying to install build essentials. are you installing it from the .deb package downloaded from ubuntu archives?

lets try to see why it cant install, hopefully ,if we find a solution, we'll get b43-fwcutter up and running, if not, we'll move to ndsiwrapper route

sam

---

### Post by hello_emo_boy on 2008-05-08
@sam_delta

I am trying to install from a .deb file considering I don't have a wired net connection. When I tried to install the build-essential, it gives me an error saying it can't install libc6-dev.

That's the only error I get.

---

### Post by Tecra_8100 on 2008-05-08
I had the same problem you have and I'm online use a linksys gn card to.

---

### Post by hello_emo_boy on 2008-05-08
So you fixed the problem? How?

---

### Post by Tecra_8100 on 2008-05-08
sudo lshw -C network

if you see ssb anywhere in that then i had the same problem.

---

### Post by hello_emo_boy on 2008-05-08
Nope, no ssb anywhere.

---

### Post by hello_emo_boy on 2008-05-08
Nope, no ssb listed anywhere.

---

### Post by Tecra_8100 on 2008-05-08
try this. It might work if you haven't try it.

sudo modprobe -r b43
sudo modprobe -r b44
sudo modprobe -r b43legacy
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44

if it work then let me know.

---

### Post by hello_emo_boy on 2008-05-08
Tried, no dice. Still no wireless and still will not install the essential build file.

---

### Post by Tecra_8100 on 2008-05-08
Ok what have you try bcuz that work if me until I installed the fwcutter.

---

### Post by hello_emo_boy on 2008-05-09
What are the steps you did, I followed a suggestion previously from this thread.

---

### Post by Tecra_8100 on 2008-05-09
The way that I post did work for me. Did you use ndiswrapper for the driver. What does "ndiswrapper -l" say

---

### Post by sam_delta on 2008-05-09
@hello_emo

if you want to use ndiswrapper, i think tecta can help you better than me since i dont use ndiswrapper. 

to install build essentials:
open a terminal, insert the ubuntu 8.04 hardy CD
and then type 
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

if it works and install build essentials, preceed with the next instructions as if you installed build essentials correctly

sam

---

### Post by Tecra_8100 on 2008-05-09
I just used ndiswrapper to get online then installed b43-fwcutter. Work fine with linksys wi-fi cards.

---

### Post by hello_emo_boy on 2008-05-10
For some reason, my cdrom will not mount. It updates in the package manager, but then it won't find the CD.

Any idea?

---

### Post by sam_delta on 2008-05-10
do you have ubuntu i386/32bit or AMD/64bit?

if you have ubuntu AMD/64bit, tell me cuz the package "build essential.deb" i pointed out in previouis post was for i386/32bit

if you have ubuntu i386/32bit then 
you might need to go to the ndiswrapper route

follow VERY CAREFULLY the steps on the following link:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

there are 2 instructions that you wont be able to follow since you do not have a wired connection, instead, youll need to download those files and install them manually on your pc

FOR STEP 1 on "sudo apt-get install ndiswrapper-utils-1.9"
      for this instruction you will have to download the following .deb file and install it in your ubuntu machine:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb)

FOR THE WHOLE STEP 2
       you can skip this steb by just downloading/copying your microsoft windows wireless drivers for your card and placing them on your working directory, which will be "~/bcm43xx" as made in the first step (in your home directory and filder called bcm43xx) (you made this folder on step one)

FOR STEP 3 on "sudo ndiswrapper -i bcmwl5.inf"
       replace the <bcmw15.inf> with the name of the microsoft windows driver you copied into your computer/working directory.

you should be good to go with everything else

if you get stucked in any step, post here, ill help you out

sam

---

