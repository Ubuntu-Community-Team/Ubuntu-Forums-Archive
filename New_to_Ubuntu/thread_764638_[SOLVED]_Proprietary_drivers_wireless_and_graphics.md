---
title: "[SOLVED] Proprietary drivers/ wireless and graphics"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by NeuB27 on 2008-04-24
Ok, so I have a nvidia 8600 GT, and Zonet wireless card. 
1. The display drivers contained on the LiveCD (which I used to install) work, but they cannot provide the enhanced desktop features, or 3d graphics. I cannot seem to figure out how to install the drivers from the CD, if that is even possible. The help guide that comes inherently on ubuntu doesn't seem to help.
2. The wireless card that I have does not seem to be functioning correctly, as I have no wireless option under the network manager. Following the troubleshooting guide (which refers to 'Device Manager under " System > Administration > Device Manager " doesn't seem to be there...? ) doesn't have any information thats helpful. Under the ' System > Preferences > Hardware Manager ' I see something that calls itself a wireless card, but from a different company. I also have the drivers CD for that card.

So in short, if there is some way to get drivers off of a CD I would love to know. As you can probably tell I am completely new to any Linux based system, and have only really used Windows in the past. So I apologize if these questions are completely inane, I've looked around the forums but could find this information elsewhere. Thanks for any help you can offer.

---

### Post by SunnyRabbiera on 2008-04-24
what version did you install?

---

### Post by Tatty on 2008-04-24
Go to the Hardware Manager and install that wireless card you see.  It probably is the right driver for your card, otherwise it wouldnt appear.

If that fails then please go to a terminal and type ```
lspci
``` then post the output on here.  (i assume this is a pci wireless card from how your describe it?)

Can you be more specific about the make / model of youre wireless card?

Lets get that working first before the graphics card.  Can you connect via a wired connection for the time being or are you dependant on the wireless?

---

### Post by DezSP on 2008-04-24
Correct me if I'm wrong, but I think the restricted drivers for nvidia aren't included on the Ubuntu CD? So to get that working, you really want an Internet connection to make use of restricted-manager...

So it's best to get the wifi working first. If you could post up the make/model of your card, we can go from there. :)

---

### Post by NeuB27 on 2008-04-24
I installed Gutsy Gibbon 7.10 The wireless card is a Zonet ZEW1602A.
 >>Tatty: How do I install something from the Hardware Manager, the only functions of the HM that I understood were to look at what is attached, I didn't see anything like an installation option or button, just information on what it was.
 > and yes it is a PCI card.
 > Wireless is my preferred option for now, is the only way to get the wireless card to work through an internet connection?

>>>results of lspci (the important part? its kind of a pain to list it all, nothing else mentioned a wireless anything, it was all PCI bus and USB/1394 and general stuff)

05.02.0 Ethernet Controller: Marvell Technology Group Ltd. 88w8335  [Libertas] 802.11b/g Wireless (rev 03)

---

### Post by twright on 2008-04-24
run update manager (in the administration menu) select check then it might appear in restricted drivers manager :)

---

### Post by nicedude on 2008-04-24
He needs to use Ndiswrapper for that PCI wifi card in question I do believe. Could someone else help him do that. I use madwi drivers so I'm not too good at Ndiswrapper help.

---

### Post by NeuB27 on 2008-04-24
>> twright: When I run update manager it cannot connect to the update website and fails, is there another way to run that utility so that it doesn't connect to the internet, and/or searches amongst hidden or batched/compressed files already installed?

---

### Post by twright on 2008-04-24
i think you will need internet to get this working (though you might be able to work around it)

if your router has an eithernet port you could connect via that

---

### Post by nicedude on 2008-04-24
Here's the manufacturers specs for his card, It uses a Marvel chipset. Someone should know what driver he needs to either try natively or Ndiswrapper 

Specifications
IEEE Stardards
	
IEEE 802.11g, IEEE802.11b
PCI Bus Power
	
3.3v
Chipset
	
Marvell 88W8335+88W8010
Frequency Range
	
2.4GHz - 2.462GHz, ISM Band
Data Transfer Rate
	
IEEE802.11g: 54/45/36/24/28/12/6 Mbps
IEEE802.11b: 11/5.5/2/1 Mbps
(with auto-fallback)
Modulation
	
IEEE802.11g: OFDM
IEEE802.11b: CCK
Encryption
	
64/128bit WEP, WPA, WPA2
Transmit Output Power
	
IEEE802.11g: 15dBm +/- 2dBm
IEEE802.11b: 16-18dBm
LEDs
	
Power, Link/Activity
Antenna
	
2dBi SMA
Operation Range
	
Indoor: Up to 100M (328.8FT)
Outdoor: Up to 300M (98.4FT)
*Environmental factors may adversely affect operation range
Support OS
	
Windows 2000, XP and Vista

---

### Post by twright on 2008-04-24
ok, to set it up with ndiswrapper you will need the windows driver and ndisgtk package installed. you can get that using nonetdebs.homeip.net.

---

### Post by NeuB27 on 2008-04-24
Ok, I've downloaded the ndisgtk package and installed it, so now what is ndiswrapper and how do I use that to enable my wireless card? Also is the 'windows driver' a separate thing I need to install, and if so do I get that from nonetdebs also?

---

### Post by twright on 2008-04-24
you can get it from google or your pc manufacturers website, just the normal driver you use in windows. right click on the .exe and select extract here

---

### Post by NeuB27 on 2008-04-24
I assembled the computer, when you say 'windows driver' do you mean the driver for the wireless card? If so then I have the driver disk from the retail purchase of the card... Which .exe is it that I need to extract? the autorun.exe? something that is called setup.exe? or is there a driver file (.exe?) Sorry for all of the questions, I am really new to this all, but thanks a lot for the continuing help.

---

### Post by Mazza558 on 2008-04-24
> **NeuB27 said:**
> I assembled the computer, when you say 'windows driver' do you mean the driver for the wireless card? If so then I have the driver disk from the retail purchase of the card... Which .exe is it that I need to extract? the autorun.exe? something that is called setup.exe? or is there a driver file (.exe?) Sorry for all of the questions, I am really new to this all, but thanks a lot for the continuing help.

Tell us what .exes you have on the disc - this'll tell us which you need.

---

### Post by NeuB27 on 2008-04-24
On the driver disk for the wireless card, I have three .exe files: autorun under the main directory and invokesetup under two seperate directories, one directory is called drivers PCI/CARDBUS the other is drivers USB, so I'm assuming that the windows driver is referring to the invokesetup.exe under the PCI/Cardbus directory?

---

### Post by Mazza558 on 2008-04-24
> **NeuB27 said:**
> On the driver disk for the wireless card, I have three .exe files: autorun under the main directory and invokesetup under two seperate directories, one directory is called drivers PCI/CARDBUS the other is drivers USB, so I'm assuming that the windows driver is referring to the invokesetup.exe under the PCI/Cardbus directory?

I recommend trying that - after you've extracted, if you see an .inf file or two, you're on the right lines.

---

### Post by NeuB27 on 2008-04-24
The extract to.. option seem to be the only available, but its on a disk so i guess that makes sense, however it does not work, it comes back with an error. The error seems to indicate that it expected a zip file. I copied the driver PCI/CARDBUS folder to the desktop, and tried to extract it there, still no good. Noticed a driver.zip file, and extracted that, it contains more .exe's which also do not extract, but also has folders for win 98, me, xp64, xp2k all of which have a .inf and .sys files. What do I do from here?

PS. Thanks for the patience.

---

### Post by Mazza558 on 2008-04-24
> **NeuB27 said:**
> The extract to.. option seem to be the only available, but its on a disk so i guess that makes sense, however it does not work, it comes back with an error. The error seems to indicate that it expected a zip file. I copied the driver PCI/CARDBUS folder to the desktop, and tried to extract it there, still no good. Noticed a driver.zip file, and extracted that, it contains more .exe's which also do not extract, but also has folders for win 98, me, xp, xp2 all of which have a .inf and .sys files. What do I do from here?

PS. Thanks for the patience.

Okay, so you have the inf files now - use the "xp2" files as they're probably the most advanced. I haven't been following the thread, so I'm not sure whether you want to install these manually (e.g via the terminal) or not.

---

### Post by NeuB27 on 2008-04-24
> **Mazza558 said:**
> Okay, so you have the inf files now - use the "xp2" files as they're probably the most advanced. I haven't been following the thread, so I'm not sure whether you want to install these manually (e.g via the terminal) or not.

Oops, I meant to say xp64 and xp2k for the folders, perhaps I should use the xp64, i'm using gutsy 7.10 amd64

I would love to use the terminal, but I don't know how to install them with it. I also don't know how to install them with out it, so .. using the .inf file ( do I need the .sys or .cat files, they are the only other files in the folder)

---

### Post by Mazza558 on 2008-04-24
> **NeuB27 said:**
> Oops, I meant to say xp64 and xp2k for the folders, perhaps I should use the xp64, i'm using gutsy 7.10 amd64

I would love to use the terminal, but I don't know how to install them with it. I also don't know how to install them with out it, so .. using the .inf file ( do I need the .sys or .cat files)

When I did it, it was the inf and sys files you needed (one of both).

(This is copied from a guide:

Step 2: Get Needed Packages
To install ndiswrapper
In a terminal type:
```
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```

**(Then move the inf and sys file from the folder you talked about to your Desktop)**

```
cd ~/Desktop
```

Then

```
sudo ndiswrapper -i (whatever the name of the inf file is)
```

```
sudo ndiswrapper -l (that is a lowercase L)
```

You should see a message that says driver present, hardware detected.

Now finish installing the driver
In a terminal type:
```
sudo ndiswrapper -m
```
Then:
```
sudo modprobe ndiswrapper
```

**Reboot now!**

```
sudo iwlist scanning
```

...and then choose your Network from the icon in the corner.

---

### Post by NeuB27 on 2008-04-24
Thanks a lot, I haven't tried this yet, but I really appreciate it. Could you link to the guide you referenced?

---

### Post by Mazza558 on 2008-04-24
> **NeuB27 said:**
> Thanks a lot, I haven't tried this yet, but I really appreciate it. Could you link to the guide you referenced?

It was a guide specifically for my Laptop and won't apply to you, but I cut out the bits that won't work (especially since you have a different driver and are on Gutsy). The full guide is here:

[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html]("http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html")

---

### Post by NeuB27 on 2008-04-25
Well darn, so I setup the driver, and that all seemed to go well, but I still have no wireless option inside the network manager.... Any suggestions on how to proceed?

---

### Post by NeuB27 on 2008-04-25
This thread was helpful, I finally got the wireless option to show up in network settings, but now I'm having other problems. I'd ask that you look over at my new post[ (here)]("http://ubuntuforums.org/showthread.php?t=766295") if you have any helpful suggestions. Thank you again to everyone who replied and helped me out.

---

### Post by NeuB27 on 2008-06-17
Nothing actually worked. If you have a Zonet ZEW1602A use hardy 8.04 and it all works fine. 7.10 will never work. I don't know why.

---

