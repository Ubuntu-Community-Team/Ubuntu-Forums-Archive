---
title: "Brand New user to the Linux world re wireless problem"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by marvuk on 2008-06-14
Hi all,

Today is my very 1st day into the world of Linux & have chosen to install Ubuntu 8.04 onto A Dell Vostro 1400 laptop.

Install went well and now have a dual boot machine Vista/Ubuntu 8.04 The first problem I have encountered is that I'm unable to connect to the internet wirelessly. 

I use a Linksys WAG54GS wireless G model router and am able to connect the Dell Vostro to it wirelessly via Vista. I've spent couple hours browsing forum for this problem but I'm afraid I really am out of my depth at the moment and do not understand what is written.

If any of you guys & girls can help me out with this I'd very much appreciate that as I'm very keen to persue Linux computing world and refuse to be put off by the learning curve that lies ahead.

Big thanks to those of you answering this prob.

marvuk.

---

### Post by nkri on 2008-06-14
First off, welcome to Ubuntu!  You, unlike so many, are embracing the initial hurtles and problems instead of cowering away from them, and this is a very good attitude to have as a beginner!

So, wireless, eh?  Have you tried clicking on the wireless applet?  It is the icon showing two computers and a caution sign in the top bar (panel) of your desktop.  If you click on it, a list of the available wireless networks will pop up.  If yours doesn't show, click on the icon again and go to "Connect to Other Wireless Network."  Now you can type in the name of the router (and that's the name you gave it, not model), type of security, and password, if needed.  If you're not sure about the security, try them all with your password and write down the one that works.

Good luck!

---

### Post by wormser on 2008-06-14
I looked at your other thread and it appears you have a Broadcom 4311 wireless card.  Have you enabled it under System> Administration> Hardware Drivers (Restricted Drivers Manager) and enable the Broadcom card.  Can you also confirm that is the correct model number by posting the results of lspc.

```
lspci
```

---

### Post by jimrz on 2008-06-14
WELCOME !

First thing please post which wifi card, make / model / chipset) your laptop is attempting to use. This will allow others here who have the same card and have been able to get it working to help you through the required steps. 

If you do not know this info, you can:

1- go to Dell.com and look it up

              or

2- open a terminal (Applications > Accessories > Terminal) and enter
```
lspci
```
which will list info on all the pci devices on your system, scroll down until you find your card. If you are not certain which line, simply post the output here on this thread.

Hang in there, nearly all wifi devices can be made to work with ubuntu. Some just require a little more effort than others.

---

### Post by marvuk on 2008-06-15
Hi guys & thanks for your replies, the result of lspci lists:

*Network controller:Broadcom Corporation BCM94311MCG wlan mini-pc (rev01)*

After trying System> Administration> Hardware Drivers (Restricted Drivers Manager)the box states '*No propriety drivers are in use on this system*'

When I try to connect via the two monitors & enter my network details an exclamation mark appears next to the two monitors icon.

Thanks once again & I look forward to working with you soon.

marvuk

---

### Post by fade2gray on 2008-06-15
Hi guys, as you can see by my join date that I first tried Ubuntu almost 2yrs ago - I fell at the wireless hurdle and never got back on the horse until just over 3wks ago.

If marvuks's experience is going to be anything like mine (old BT Voyager 1040 w/l adapter with BCM4306 chip), he's going to need an initial wired connection in order to use fwcutter to download and install firmware for his adapter.

I tried all the alternative methods and suggestions I could find without using the initial wired connection without luck - with an initial wired connection it's a breeze to set up wireless.

Good luck marvuk.\\:D/

---

### Post by drs305 on 2008-06-15
> **marvuk said:**
> 
*Network controller:Broadcom Corporation BCM94311MCG wlan mini-pc (rev01)*

After trying System> Administration> Hardware Drivers (Restricted Drivers Manager)the box states '*No propriety drivers are in use on this system*'

marvuk

Marvuk,

Welcome to ubuntu. I have the Broadcom 4311 Rev 1 and found the instructions in the following post an excellent method to get the card working. (I also didn't have anything listed in the Proprietary Drivers section.)

While following the instructions, I believe you have to temporarily go to another page to complete step 2. For me, step **2a** was the one I needed to use before returning to the link and completing steps 3-9.

[http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")

---

