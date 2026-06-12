---
title: "How to install Video card driver for intel?????HELP"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by gullfounder on 2008-07-19
[FONT=Courier New]Hi. 
     I have problem in Linux Ubuntu that is how to install driver for Intel Video card.
I have downloaded the driver file form Intel website but don't know how to install it.

Note: I am new user from Windows OS. So, I don't know much about the Ubuntu so reply briefly.

I am havening a Laptop 
Fujitsu Siemens 
Amilo-Pro-3405   

                                                                                                      Thanks in Advance
[/FONT]

---

### Post by phidia on 2008-07-19
Are you using the 8.04 release and what specfic intel card do you have?
The community documents for setting up video are [here]("https://help.ubuntu.com/community/Video#Intel").

---

### Post by coffeecat on 2008-07-19
You shouldn't need to install the Intel video driver. It should have been set up when you installed Ubuntu. Can you tell us what the problem is or why you think you need to download the driver?

---

### Post by gullfounder on 2008-07-20
Yes i am using 8.04LTS.

i don't know weather the driver installed or not.
And i think i need the driver because when in Advance desktop option i turn on the 3D effect's it does  not apply or don't work.

i am having intel  945GMA mobile  video card !!!!!

---

### Post by gullfounder on 2008-07-20
by the way my friend have Nvidia GT8400 video card how do we install the driver for that video card he also have the Ubuntu 8.04LTS

---

### Post by Sef on 2008-07-20
For the driver, have you tried System > Administration > Hardware Drivers?

---

### Post by coffeecat on 2008-07-20
As far as the Intel machine is concerned, **gullfounder**, look in the file /etc/X11/xorg.conf; don't edit it. Find the section "Device". In that section there is a line starting 'Driver'. What is next to 'Driver'. Is it "i810" or "intel". If it's one of those, then you have the Intel driver installed. If it's something else, then post what it is and someone will be able to help.

The Intel graphics chipset can display some of the 3D effects, but it isn't as capable as a Nvidia card, say, with the proprietary driver. Maybe you've hit the limitation of Intel graphics. Can you get anything to work in Advanced Settings, or nothing at all?

---

### Post by gullfounder on 2008-07-27
Well i have went to that file this is what i have found??
"
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Synaptics Touchpad"
EndSection"

---

### Post by nikeairj on 2008-07-28
I have the exact same problem except that I'm using Intel Corporation 82845G/GL (according to lspci),

---

### Post by freebird54 on 2008-07-28
I am not an expert on this - but I suggest that you go to the ***Desktop Effects & Customization*** forum here, and search for ***compiz-check***.  This is a script that someone wrote for testing your setup for compiz (special effects) compatability - and it might well point you to a solution...

Unless, of course, your particular chipset is blacklisted!

I have an integrated Intel video chipset on my desktop, and compiz works MUCH better than it seems that it should!  Good luck!

---

### Post by eightmillion on 2008-07-28
gullfounder, 

Please type this in a terminal window.
> sudo apt-get install xserver-xorg-video-intel
After that finishes, do this.
> sudo dpkg-reconfigure -phigh xserver-xorg
This will ask you several questions about your setup. If you don't know the answers, leave them default.

---

### Post by gullfounder on 2008-07-28
> **eightmillion said:**
> gullfounder, 

Please type this in a terminal window.

After that finishes, do this.

This will ask you several questions about your setup. If you don't know the answers, leave them default.

Man i tried that command but the second command did not work.................!
Pleas check again the commands

---

