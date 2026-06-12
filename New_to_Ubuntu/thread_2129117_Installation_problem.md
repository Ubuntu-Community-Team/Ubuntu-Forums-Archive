---
title: "Installation problem"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by maikendaalman on 2013-03-25
Well hello everybody.
A friend told me too install Ubuntu, and i tried. 
I came into the demo version and installed the full version, and restarted my computer.
But when it opened again it was stuck by the part of turing on youre computer and it just blinks with this symbol: _ 
I just thought it was normal but now it is like 2 hours ago it started doing that.. And i have no idea what to do now.
And i was hoping somebody here could help me out. 

And sorry if this thread is placed wrong, but i had no idea where to put it.

---

### Post by mörgæs on 2013-03-25
Hi, welcome to the fora.
Please begin with a complete hardware description.
Do you want to have only Buntu installed or should it work side by side with Windows?

---

### Post by fantab on 2013-03-25
Firstly, you have to tell us more about your computer: for instance,
Laptop/Desktop: Model, Make and Specifications, especially Graphics. What OS was it running before you installed Ubuntu? How did you Install Ubuntu? Default Install, where you just kept saying "Continue" until it finished install or Did you "Manually" guide the installation?

---

### Post by maikendaalman on 2013-03-25
I've found some informations about my computer. 
Here they come.
CPU Typy: AMD Athlon(tm) II p340 dual-core processer
CPU speed: 2.20 GHz
IDEO Model name: Toshiba MK6465GSX - (s1)
IDEO Seriel numer: 119EF2XQS
Atapi model name: HL-DT-STDVDRAAM
KBC Bios version: 01.08
Asset tag: No asset tag
Product name: eMachines G640
Manufacturer name: eMachines

I have no idea if that it usefull but i hope so. And to get those information i pressed f2 when you start the computer up.

And i was running Windows 7 before this but windows did stop working so my friend told me too use ubunte like i said. 

I dont know so mcuh about computers and all that but i put the disc with ubuntu on it(that i godt from another computer) and i got to the demo version. And i bgan the installation just did what it told me too and nothing else. But one problem i had was that i use a wireless usb adapter but that didnt work. So it was installed without internet. And at last it a window popped up and said: "Installation completed and you have too restart the computer." And i just pressed the restart button, and then all this happened with that symbol: _
And thats all i can say.

---

### Post by maikendaalman on 2013-03-25
And the last thing, i needed just too have ubuntu cause my windows doesnt work at all.

---

### Post by fantab on 2013-03-25
> **maikendaalman said:**
> And the last thing, i needed just too have ubuntu cause my windows doesnt work at all.

The simplest solution will be to reinstall UBUNTU.

But before you do that, Boot with your Ubuntu USB/DVD. I hope you have Ubuntu 12.04 or 12.10 (You can also install Ubuntu 13.04 Beta, which is quite stable and it is due for release at the end of April). 12.04 is a LTS (Long Term Support) version, supported until 2017.

Boot with you ubuntu usb/dvd and choose to "Try Ubuntu" at the appropriate screen. Wait until you are presented with the full desktop, then open the application called TERMINAL and there you type;

```
sudo fdisk -l
```

and post the output here...

```
lspci | grep vga
```

and post the output here...

---

### Post by maikendaalman on 2013-03-25
it is ubuntu 12.10. But the main problem is that it doesnt start up my computer. I have the disc in my computer. I cant choose anything it just goes too that screen. The only thing i can get into is when you press f2 right before the computer "starts up"..

---

### Post by fantab on 2013-03-25
That is BIOS. Ok.. You press F12 or F10 depending on your BIOS to be able to boot from your disc. can you do that?

---

### Post by grahammechanical on 2013-03-25
Is Windows still on that machine? I am still not clear about that. If Windows is still on that machine and you choose the Install Alongside option, then when you reboot you will see a boot menu (Grub) from which you can choose between Windows and Ubuntu.

If you chose to install Ubuntu with the Use the Whole Disk option then only Ubuntu will be on the hard disk and you will not see a boot menu. But it is there non-the-less. As the boot process starts hold down the Shift key. That should bring up the boot menu. You do not tell us the version of Ubuntu that you are using. This is useful information that we need in order to give you accurate directions.

If you have installed Ubuntu 12.04 then the boot menu will show you an option to boot Ubuntu Recovery Mode. Select Recovery Mode and boot it. At the Recovery Mode menu select Resume. That may get you to a working desktop and from there you need to activate a video driver but first you need to get an internet connection.

If you have installed 12.10 then select the Advanced Options for Ubuntu. That will open a sub-menu where you will find Ubuntu Recovery mode. You can also try the Recovery Mode option of FailsafeX mode.

Regards.

---

### Post by maikendaalman on 2013-03-25
Yes. But if you can be nice and give me a link with the ubuntu i have too download on my disc. So i can be sure that it is the right one for installing without an operating system.

---

### Post by maikendaalman on 2013-03-25
No my computer does not have an operating system at all. And that is my problem bacuse i thought i had installed Ubuntu 12.10 but apperantly not. Because my computer is stuck, where it just shows a blinking symbol: _

---

### Post by grahammechanical on 2013-03-25
Perhaps we should start from the beginning. Your CPU is 64bit so it will run a 64bit Ubuntu. Although 32 bit Ubuntu will run on a 64 bit CPU. But 64 bit Ubuntu will not run on a 32 bit CPU. This is why I checked the CPU.

[http://www.notebookcheck.net/AMD-Athlon-II-P340-Notebook-Processor.37883.0.html](http://www.notebookcheck.net/AMD-Athlon-II-P340-Notebook-Processor.37883.0.html)

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

I have built my own machine and I did not get a flashing white line when I first switched on the machine. I got a message telling me that the BIOS could not find an operating system to load. The hard disk was blank, you see.

The Basic Input Output System (BIOS) holds information about the hardware that the computer uses when it boots. It also looks for an operating system in a certain order that can be changed. In the past it was customary for the BIOS to look for an operating system first on a floppy disk then on a hard disk. All this took time. So, it became customary for the BIOS to simply look first at the hard disk. If it cannot find an operating system the BIOS will test us that this is the problem. You are not getting that message, are you? 

To run/load the Ubuntu live session whether to try Ubuntu or install Ubuntu we need the BIOS to look for an operating system on a DVD or USB memory stick before it looks for an operating system on the hard disk. Because your machine is not finding the operating system on the DVD/USB it suggests that it is going straight to the hard disk and finding something there and loading it and it is braking.

We need to go into the BIOS settings and change the boot priority. You may find that you have legacy floppy support enabled. If that is the case then you may not be able to set a USB stick as the first in boot priority. Disable legacy floppy and you will find that you then have options for USB.

So, you have 2 choices. 1) Accept that Ubuntu is on the hard disk and try to get to a desktop through Recovery Mode options. 2) Re-install Ubuntu by first setting the boot priority in the BIOS.

By the way, if you try to re-install Ubuntu and you run a live session try to get that USB wireless adapter working in the live session. Or get hold of an ethernet cable and use that to get an internet connection.

Regards.

---

### Post by Tony Flury on 2013-03-25
Don't assume you don't have an OS - you may well have one installed which for some reason is not starting correctly  - hence the flashing _.

I think if you had no OS at all your PC would refuse to boot and would generate an error saying "No Boot disc" or similar.

Follow the commands that fantab gave you - what results do you get ?

---

### Post by maikendaalman on 2013-03-25
I have dowlaoded the iso file on a dvd-r disc. Just following this link: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto).
The first step for windows 7. 
Now the last step is too download it on my computer by using the boot thing. 
The last thing i dont understand...

---

### Post by grahammechanical on 2013-03-25
I always use the last step Burning from Ubuntu because I only have Ubuntu on my machine. Once we have an image we follow this

[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)

Regards.

---

### Post by maikendaalman on 2013-03-25
I did what you said with the boot thing and.. thank you alot. My screen is now purple with the text ubuntu. But im going to stay in this thread cause well maybe things will happen again. 
but i cant make the adapter work because it is a netgear thing that says: Compatible with Windows 7. So my first guess is that it doesnt work with ubuntu. But im hoping that it will work now :)

Adn now my last question: How can i make my internet work because i that adapter is my only way too get internet cause i cant get an ethernet cable. Doesnt work where i live.

---

### Post by maikendaalman on 2013-03-25
I got this message: 
This computer currently has no detected operating system. What would you like to do ?

1: Erase disk and istall ubuntu
2: Encrypt the new Ubuntu istallation for security
3: use LVM with new Ubuntu installation

i have no idea what to choose....

---

### Post by fantab on 2013-03-25
> **maikendaalman said:**
> I got this message: 
This computer currently has no detected operating system. What would you like to do ?

1: Erase disk and istall ubuntu
2: Encrypt the new Ubuntu istallation for security
3: use LVM with new Ubuntu installation

i have no idea what to choose....

Choose 1. Erase disk and install Ubuntu....

---

### Post by maikendaalman on 2013-03-25
> **fantab said:**
> Choose 1. Erase disk and install Ubuntu....
 Thank you.
Evrything worked untill almost at the end of the installation where it pops up a window that says:
"Installation crashed.
If you press close you would get in and we will try to report the bug" or something like that. 
what to do. I tried twice....

---

### Post by fantab on 2013-03-25
Well, Try again. 12.10 is, in my opinion, one of those Ubuntu versions that didn't work for me as well as the previous ones. If you have patience try [13.04 Daily]("http://cdimage.ubuntu.com/daily-live/current/"), its in BETA and quite stable and fast. If you install this you will have to update it everyday until its final release in about less than 30 days.

Ok, with your existing Ubuntu, do this:
Boot your machine with Ubuntu and at the appropriate screen say "TRY Ubuntu". It will boot to a working desktop. Play around for a while and set up your Internet connection. Then from desktop install "Ubuntu to Hard Disk".

Hope it works...

---

### Post by alphacrucis2 on 2013-03-26
The fact that Windows failed on this machine may indicate some sort of hardware issue. I would at least run memtest on it before going too much further.

---

