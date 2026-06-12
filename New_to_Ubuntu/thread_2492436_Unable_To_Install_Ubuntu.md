---
title: "Unable To Install Ubuntu"
date: 2023-11-10
forum: New to Ubuntu
---

### Post by raviheima on 2023-11-10
I'm trying to make a full installation of Ubuntu ubuntu-22.04.3-desktop-amd64 for the first time on my PC but I keep getting this error

---

### Post by Rubi1200 on 2023-11-10
Hi and welcome to the forums :-)

We need some more information to help you.

Please try and answer the following questions:

1. what version of Ubuntu are you trying to install?

2. are you using a USB or a CD/DVD?

3. did you verify the checksum for the ISO?

4. what is currently installed on the PC?

5. what are your specifications, especially RAM and graphics card?

---

### Post by raviheima on 2023-11-11
The Pc Specs
Dell Latitude E6440
8GB RAM
300GB HDD
CPU Core i5 2.5GHz
i'm using a usb disk
and i've verified the checksum for the ISO file they both match
I tried to make a full installation so windows was wiped out and the installation still failed so currently there's no operating system on the PC

---

### Post by MAFoElffen on 2023-11-11
How did you write the image to the USB Flash Drive? Using what?

---

### Post by raviheima on 2023-11-11
I used rufus, i was able to test and run ubuntu i even browsed with it but the installation just keep failing

---

### Post by raviheima on 2023-11-11
> **raviheima said:**
> I used rufus, i was able to test and run ubuntu i even browsed with it but the installation just keep failing

and i just tried using ventoy and the same error occured again

---

### Post by raviheima on 2023-11-11
The harddrive was working fine with windows so i don't think it could be the problem

---

### Post by guiverc on 2023-11-11
The error shows installation media error(s), ie. the CD/DVD drive refers to whatever media your ISO was written to.

First reason for this is an invalid ISO, corrupted download etc. detected by ISO validation after download ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0) or other checksum check).

Next the write of ISO to media was incorrectly handled; which can include using *outdated* programs for the release of Ubuntu being written, which really matters if you're talking about Ubuntu 20.10 or later (ie. 22.04, 23.04, 23.10). 

`rufus` of any version should write correctly if you clone (*I think this is called dd-mode*) the ISO to your installation media; but if using any other option the software needs capable of writing that release of Ubuntu if your release of Ubuntu is 20.10 or later.  You didn't give release details; but release & rufus version matter (ie. if your rufus version was older than the Ubuntu ISO you can experience this if you didn't clone/dd-mode write)

If you can boot the installation media in *live* mode, you can check it, however how you do this will vary on Ubuntu release too, so I'll provide a link to a answer I've written elsewhere - [https://askubuntu.com/questions/1311183/do-i-need-to-check-the-integrity-of-a-ubuntu-install](https://askubuntu.com/questions/1311183/do-i-need-to-check-the-integrity-of-a-ubuntu-install) where you can scroll to my answer & use the method most appropriate for your *unstated* Ubuntu release... ie. I'll scan looking for the message which will look like (*varying on release somewhat*)

```

May 11 08:37:47 ubuntu casper-md5check[3924]: Check finished: no errors found.
```

If you don't see this, errors like you are asking about are to be expected due to invalid installation media.  

Also note, if you're using *optical media* and installing a release newer than 20.04, you can also experience issues relating to *timeouts* that can result in this or other invalid messages (*the timeout will be obvious only in system logs as the cause*); reboot & re-trying will work usually (*may take up to 3 tries in my experience*) as USB flash media is expected for modern Ubuntu releases (ie. *anything newer than 20.04*)

My experience/2c worth anyway.

---

### Post by MAFoElffen on 2023-11-11
> **MAFoElffen said:**
> How did you write the image to the USB Flash Drive? Using what?
You said you verified the checksum that you downloaded. So next would be to determine if it was written to the USB, in a maaner that made it bootable.

So... Let me ask in another manner...

How did you prepare the USB Flash drive with the installer image?

---

### Post by kc1di on 2023-11-12
I would recommend burning the .iso using Etcher found here.
[https://etcher.balena.io]("https://etcher.balena.io")
rufus has been problematic for some reason. 

Give Etcher a try.

---

### Post by adamking999 on 2023-11-22
[COLOR=#000000][FONT=&quot]To install Ubuntu Desktop, you need to write your downloaded ISO to a USB stick to create the installation media. This is not the same as copying the ISO, and requires to use [balenaEtcher]("https://etcher.balena.io/"), as it runs on Linux, Windows and Mac OS. Choose the version that corresponds to your current operating system, download and install the tool.
please create the bootable USB stick again and see whether problems gone or not[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-11-25
+1 -- With quiverc

I have kept somewhat quiet... He said all that needed to be said. 

I do IT Support. I use Rufus and it works for me. I have in the past used 'dd' on both Linux and MAC OSX terminal, sudodus'es mkusb, Windows Tools, UltraISO, Yumi, Ventoy, Balena Etcher, RMPrepUSB, UNetbootin, XBoot, Universal USB Installer, PowerISO, usb-creator-gtk, usb-creator-kde, WonderISO, and more. Some that are not around any more. 

I do about 3-5 installs a day. 'Some', I don't use anymore because they had some problems. As an IT professional, I don't use what doesn't work for me, nor recommend them to my customers. 

The two biggest things I see is to verify that you have a good image downloaded by checking the 256-SHA checksum, before burning it to a USB. Then checking the filesystem after it is burned to the USB. The 22.04 LTS image has that file system and file checker in startup of the image... If you <Arrow-Down> during the Splash, it will toggle the screen to the boot messages that are usually hidden under the splash screen.

---

