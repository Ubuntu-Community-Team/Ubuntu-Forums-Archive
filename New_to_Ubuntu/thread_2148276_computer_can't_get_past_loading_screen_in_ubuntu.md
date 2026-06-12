---
title: "computer can't get past loading screen in ubuntu"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by pablithemantis on 2013-05-24
Hi all. Thank you for the time. I'm a beginner to all of this.

Two computers: a 3 year old Dell Studio XPS 8100, original OS: Windows 7
                        a brand new Asus, original OS: Windows 8

A month ago, the Asus was shutting down when the power went out. It killed the computer's ability to turn on. I extracted the hard drive and put it in the Dell (opened up both computers and replaced the Dell's hard drive with the Asus'). My files were intact and I saved them.

I decided to switch to Ubuntu, and made a liveUSB. I put the hard drive back in the Asus and plugged in the liveUSB. The Asus wouldn't load Ubuntu from the liveUSB. Wouldn't install it either. I tried a liveDVD. Nothing. LiveSD. Nothing. Tested the liveUSB and liveDVD on the Dell, worked fine. Used windows disk to reformat the Asus hard drive and successfully installed Windows 7. The Asus had a functional OS, could turn on perfectly, and worked fine in every way Windows does.

With Windows 7 installed, tried to run the liveUSB to install Ubuntu. Crashed. Tried liveDVD. Crashed.

Removed Asus hard drive again and put it in the Dell. Ran the liveUSB from the Dell, and successfully ran and installed Ubuntu. Ubuntu worked perfectly when the hard drive was inside the Dell. Put the hard drive back in the Asus, and it crashed after the loading screen.

Any ideas how to have my Asus run Ubuntu? According to people in the beginners Ubuntu chatroom, because the loading screen turns on, it may be a problem with my "graphics drivers" because "after the loading screen, X should boot up, but it crashes". I don't know what that means, but I do know I can access recovery mode from inside the Asus. Maybe there's a way I can use that?

Again, thanks.

---

### Post by lethall1 on 2013-05-24
what graphical adapter?
which version of ubuntu?
can you swith to first terminal with alt+ctrl+f1, when it crashes?
too little information.

---

### Post by pablithemantis on 2013-05-24
How do i determine graphical adapter?

Ubuntu 13.04
can't access terminal through alt+ctrl+f1

---

### Post by lethall1 on 2013-05-24
```
sudo lspci
```

---

### Post by pablithemantis on 2013-05-24
how do i type the code without the ctrl shft f1

---

### Post by lethall1 on 2013-05-24
recovery mode

---

### Post by pablithemantis on 2013-05-24
don't understand the information that came up. here's what the terminal said:

host bridge: advanced micro devices (amd) family 12h processor root complex

vga compatible controller: amd nee ati sumo radeon hd 6410d

audio device: amd nee ati beavercreek hdmi audio

usb controller: amd fch usb xhci controller rev03 (also rev11)

smbus: amd fch smbus controller rev14

ide interface: amd fch ide controller

isa bridge: amd fch lpc bridge rev11

pci bridge: amd fch pci bridge rev40

usb controller: amd hudson pci to pci bridge

host bridge: amd family 12h/14h processor function 0 (also 1-7)

---

### Post by lethall1 on 2013-05-24
[http://ubuntuforums.org/showthread.php?t=1940314](http://ubuntuforums.org/showthread.php?t=1940314)

---

### Post by pablithemantis on 2013-05-26
I couldn't make sense of it. Most of those threads were about insalling Ubuntu for the first time, but this one already has it installed. Am I supposed to use liveUSB or liveCD to make it happen?

Of note, I found a way to get past the loading screen. If I let the comptuer load past the bios, it will go into the purple loading screen and then the video will turn off, the computer staying on. If I mash shift during the bios, open recovery mode, and then exit recovery mode, it will take me to the login screen. (Why does that work?)

The main issue as of now is getting the computer past the loading screen without going through the recovery mode. Since I can access the computer from having logged in, where do I go? Was there something in the thread you linked on that?

---

### Post by pablithemantis on 2013-05-27
My question was answered here:

[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

The AMD graphics driver requires a slight modification to GRUB. It can be modified through GRUB by hitting E and inserting the nomodeset at a certain spot.

To make that pervasive, the following link described how to modify GRUB, by accessing the terminal.

[http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation/38782#38782](http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation/38782#38782)

It runs a little slow, but I fixed that by installing xubuntu. Now I'm set.

---

