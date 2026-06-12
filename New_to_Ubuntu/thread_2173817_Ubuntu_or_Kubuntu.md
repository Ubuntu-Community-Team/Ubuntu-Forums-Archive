---
title: "Ubuntu or Kubuntu?"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by Citta on 2013-09-11
Hi,       I bought a PC, Win7, i7,64bit, 128GB SSD, 1TB HDD. I want to install one of the mentioned OS alongside, multiboot, on the SSD.         What are the pro's and con's of these OS? Is Kubuntu as easy to install as Ubuntu-how to install it? How can I delete an OS, when not running properly? Any problem I have to consider before for  not to  crash the machine?       Thanks for taking the time to read this and for your hints, too,     Citta

---

### Post by VMC on 2013-09-11
I have both Ubuntu & Kubuntu. Different philosophy, but below is all Linux. They do have separate libraries, but its the "front end" that you will have to decide.

Deleting OS is just a matter of re-installing, with the reformat option - if we're talking about Ubuntu.

The main thing to find out is the BIOS. Is it Legacy BIOS or EFI. What is the computer model number your using.

---

### Post by deadflowr on 2013-09-11
> [COLOR=#000000]Is Kubuntu as easy to install as Ubuntu-how to install it?[/COLOR]
In general, yes.
Though the installer's design is slightly different in look, the installation process is generally the same.

---

### Post by philinux on 2013-09-11
> **Citta said:**
> Hi,       I bought a PC, Win7, i7,64bit, 128GB SSD, 1TB HDD. I want to install one of the mentioned OS alongside, multiboot, on the SSD.         What are the pro's and con's of these OS? Is Kubuntu as easy to install as Ubuntu-how to install it? How can I delete an OS, when not running properly? Any problem I have to consider before for  not to  crash the machine?       Thanks for taking the time to read this and for your hints, too,     Citta

Best answer is to try them both either via a live dvd or live usb. Instructions for creating these are here [http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

---

### Post by crazymonkey05 on 2013-09-11
from your givin specs your machine seems relatively new....so when you install ubuntu/kubuntu make sure you install properly as UEFI is a pain in the but when trying to install the OS's as most modern pc's use UEFI instead of bios now

---

### Post by Jonathan Precise on 2013-09-11
> **Citta said:**
> Hi,       I bought a PC, Win7, i7,64bit, 128GB SSD, 1TB HDD. I want to install one of the mentioned OS alongside, multiboot, on the SSD.         What are the pro's and con's of these OS? Is Kubuntu as easy to install as Ubuntu-how to install it? How can I delete an OS, when not running properly? Any problem I have to consider before for  not to  crash the machine?       Thanks for taking the time to read this and for your hints, too,     Citta

Install [Kubuntu]("http://cdimage.ubuntu.com/kubuntu/releases/raring/release/kubuntu-13.04-desktop-amd64.iso"). Once installed, run:

```
sudo apt-get install ubuntu-desktop
```

to install ubuntu (choose the one you want at the login screen). Now you have windows, ubuntu, and kubuntu!

Update: If you have UEFI (check through the BIOS setup utility), choose the 64-bit DVD.

---

### Post by Citta on 2013-09-12
Hi, VMC, 

Could you explain what library, front end(desktop?). deleting OS a matter of reinstalling/reformatting means? I took a glimpse at boot_info_script...seems it is for Linux, not for Win. Next reboot I will try to find 
out BIOS/EFI, where is this displayed? The PC is a make of the shop, if I understood your question correctly.
So U or Ku does not matter and it is just a matter of taste?

---

### Post by Citta on 2013-09-12
Hi, deadflowr, 

is it installed as Ubuntu?

---

### Post by Citta on 2013-09-12
Hi, philinux, 

I went to the first link, mentioned in your post, there is Ubuntu, for Kubuntu does not exist the same?

---

### Post by Citta on 2013-09-12
Hi, crazymonkey, 

it is Win7, without UEFI, as far as I can see, the clerk in the shop told the same...so I hope not to run in trouble.

---

### Post by Citta on 2013-09-12
Hi, Jona, 

Yes, I ask you why....No UEFI. How to install Kubuntu?

---

### Post by philinux on 2013-09-12
> **Citta said:**
> Hi, philinux, 

I went to the first link, mentioned in your post, there is Ubuntu, for Kubuntu does not exist the same?

If you go here you can get the iso [http://www.kubuntu.org/](http://www.kubuntu.org/)

You can burn it to disk or usb using the same instructions as for ubuntu.

Please remember that running a live disk or usb will be a lot slower than a hard disk installation. But it's a great way to trial an OS.

---

### Post by malspa on 2013-09-12
> **Citta said:**
> So U or Ku does not matter and it is just a matter of taste?

I use both Ubuntu and Kubuntu here. In my opinion, yes, it is just a matter of taste.

> **Citta said:**
> How to install Kubuntu?

I typed **install kubuntu** in my web browser; here's the first thing that came up: [https://help.ubuntu.com/community/GraphicalInstall/Kubuntu](https://help.ubuntu.com/community/GraphicalInstall/Kubuntu)

---

### Post by deadflowr on 2013-09-12
I'm not sure what you want.
But Kubuntu and Ubuntu use different graphical desktops.
Underneath, parts like the linux kernel are the same.
You can get Kubuntu [here]("http://www.kubuntu.org/").
And Ubuntu [here]("http://www.ubuntu.com/download").

Follow Philinux's link on how to try Ubuntu, the method of getting the downloaded iso file onto a cd/dvd or usb is the same for both.

---

### Post by craig10x on 2013-09-12
Would you like a simpler and mac-like ubuntu (unity is a dock type launcher which auto hides on the left side of the screen and also has a global menu and dash search which is similar to the mac)...or do you want something that sort of resembles windows and has tons of configuration settings (personally, i think too many settings)...

I have used both and prefer ubuntu with the unity desktop myself... personally, if i wanted something that looked like windows, i think then i would use windows instead ;)

Your choice, of course...Even when i was using kubuntu which is kde, i still found myself using more gnome programs on it then kde ones so i figured, what's the point...might as well stay on gnome...which is what the regular ubuntu is...

---

