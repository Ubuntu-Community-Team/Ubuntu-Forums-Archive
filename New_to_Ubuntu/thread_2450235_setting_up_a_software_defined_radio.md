---
title: "setting up a software defined radio"
date: 2020-09-09
forum: New to Ubuntu
---

### Post by matthewpartrick on 2020-09-09
I bought a kit from NooElec to try this software defined radio idea out.  I have built two or three Pi units in the past as Roon endpoints.  I know almost nothing about Linux, FWIW.

I've successfully flashed Ubuntu onto the SD card, transferred the SD card, booted up the Pi, and went through the boot instructions uneventfully.  I have the IP address and am at the page that says:

to login:

ssh myname@192.000.0.000

personalize your acct at login.ubuntu.com

So, I go to the Mac OS terminal and ssh onto the Pi (although I have no idea why this is necessary when the Pi is connected to a monitor, ethernet, and USB keyboard and mouse.)  Anyhoo I successfully changed the username and password the first time around.  Now, when I ssh onto the Pi, I cannot get any of the following commands to work:

sudo apt update
sudo apt-get update

sudo apt upgrade 
sudo apt-get upgrade

sudo apt install xubuntu-desktop
sudo apt-install xubuntu-desktop

sudo apt install lubuntu-desktop
sudo apt-install lubuntu-desktop

So, I'm stuck.  I can't really seem to move on from this position.  The NooElec instructions don't specifically demand installing a desktop platform, but when I plug in the USB radio stick and run "lusb" it says

-bash: lusb: command not found

So I cannot complete the instructions from the manufacturer, and they said they can't help with Ubuntu issues.    

I know this is like Linux 101, but until some nitwit accidentally knocked the tip of the Rosetta Stone off none of us could speak Heiroglyphic etc, so there's that.  Any help would be appreciated.

Thanks in advance!
Matthew

---

### Post by CelticWarrior on 2020-09-09
The command is **lsusb**&#8203;.

---

### Post by matthewpartrick on 2020-09-10
yes, lsusb, that was a mistype.  I have been using lsusb.  that one is also listed as "command not found."

---

### Post by deadflowr on 2020-09-10
Sounds like you've installed Ubuntu Core which should be snap-centric not apt-centric.
Could you link to which image of Ubuntu you installed?

---

