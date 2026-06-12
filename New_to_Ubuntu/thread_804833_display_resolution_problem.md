---
title: "display resolution problem"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by caver on 2008-05-23
display resolution problem

I had a windows crash, redid hard drive, installed XP than Hardy thru Windows

I had a 800x600 display resolution after install 
I can’t get a higher display resolution. When I had 7.1 on this computer I had higher resolution with no problems. I download a Nvidia driver and got only 640x320. I used add/remove to use the driver that said for older cards Geforce 2- tv out ect. I unchecked it and then went back to 800x600. did this four times. I have a Geforce 2 MX-400 Pro-T64s AGP card. What am I doing wrong?

---

### Post by Dave Otter on 2008-05-23
alt + F2 >> displayconfig-gtk
click on Model then chose your screan model >> ok

---

### Post by wpshooter on 2008-05-23
Does this video card share system memory ?  If so, do you have the amount of shared RAM set in the BIOS to the maximum amount allowed ?

---

### Post by caver on 2008-05-23
> **Dave Otter said:**
> alt + F2 >> displayconfig-gtk
click on Model then chose your screan model >> ok
Thanks for reply
When I run displayconfig-gtk, screen pops up saying need administrative rights to change all screen setting. So I guess the ? Is how do I get  administrative rights for this?
Model has plug & play ghosted 
 graphics card tab is all ghosted. 
Has graphics card (nvidia geforce2 ddr (generic))
Drive > none
Video Memory> Automatic

---

### Post by Dave Otter on 2008-05-23
Sorry should read alt + F2 >> alt + F2 >> sudo displayconfig-gtk

---

### Post by caver on 2008-05-23
You wrote "Sorry should read alt + F2 >> alt + F2 >> sudo displayconfig-gtk"

 when I used  alt + F2 window opened I put in "sudo displayconfig-gtk" I pushed run and window closed nothing else happen.
I tryed using terminal to run it. got " [sudo] password for sp:" When I tryed to type in password, password would not type on screen.

I have seen other replies, I want to stay with one thing at a time
I quess I have been in Windowa to long :) .

---

### Post by alienexplorers on 2008-05-23
When you loaded ubuntu did you select install Restriced Driver.  If so it may have loaded the nvidia-glx-new driver.  You may have to unload Restricted Drivers and install nvidia-glx-legacy driver instead.

---

### Post by caver on 2008-05-23
Thanks for replay
As far as I know I have done this.  Each time I had to uninstall last one to put in a new one. I have tryed all I could find before I put post up. Each time went back and checked the Display, after unistalling, it was back to defaut 800x600

The post before with "Sorry should read alt + F2 >> alt + F2 >> sudo displayconfig-gtk" I still can't get it to run. Did he mean alt + F2 twice? I tryed it both ways. As I said I am new at ubuntu and may have to much "windows in my head"

---

### Post by caver on 2008-05-23
I have problem fixed I changed hardware driver to the one below. Then what other person posted worked for me. I have a large number of options now

Thanks to everyone

Hardware Drivers

KDE user interface and desktop integration for driver management 

Jockey provides a user interface for configuring third-party drivers, such as the Nvidia and ATI fglrx X.org and various Wireless LAN kernel modules.

This package contains the KDE frontend.

This is what was installed before

 Hardware Drivers

GNOME user interface and desktop integration for driver management 

Jockey provides a user interface for configuring third-party drivers, such as the Nvidia and ATI fglrx X.org and various Wireless LAN kernel modules.

This package contains the GNOME frontend.

---

### Post by Dave Otter on 2008-05-23
When you type in your password it will not appear to type on the screen but should open when u press enter

---

