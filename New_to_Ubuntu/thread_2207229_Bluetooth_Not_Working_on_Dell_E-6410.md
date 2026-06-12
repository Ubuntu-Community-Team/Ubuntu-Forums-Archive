---
title: "Bluetooth Not Working on Dell E-6410"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by GUZZLR on 2014-02-22
Hello All,
I'm trying to get my Bluetooth working, but I honestly don't know if this computer even has a Bluetooth module.  I did look at the wifi module inside, it is intel with two antenna leads to it (black & white) with an unused third antenna lead which is grey.  The exact model number of the wifi card I cant read.
is there a code I can run to see if the computer is Bluetooth capable and simply needs a driver?
Thanks for the help
  
Computer: Dell E-6410, original software was Vista Business Class, manufactured in 2010
Ubuntu 13.10

---

### Post by Vladlenin5000 on 2014-02-22
> **GUZZLR said:**
> I'm trying to get my Bluetooth working, but I honestly don't know if this computer even has a Bluetooth module.

Don't you think is better to know for sure before anything else? Really... Is it so hard to remember whether or not you had it when using Vista? Ubuntu does a lot of things better than Windows but conjure new hardware out of thin air isn't one of them, well, not yet anyway...

---

### Post by GUZZLR on 2014-02-22
```
Is it so hard to remember whether or not you had it when using Vista?
```

Actually yes...
I'll better describe the condition of the computer....
I received the computer with no hard drive, and no O/S from ebay.  So, I never owned/used the machine while it was working with Windows.  I know it most likely had Vista Business Class installed as it says so on the machine bottom software sticker.
So I don't really know if it was originally purchased with the option of Bluetooth.  I do see an area where the Bluetooth icon will light up though.  

Does anybody know how to run code to scan if there is Bluetooth functionality in this computer?
Thanks for the help

---

### Post by IvoGuerreiro on 2014-02-22
Hi, 
sudo lsusb |grep Bluetooth
Should give an output similar to:   
  Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) 
attention, i'm really new on this ubuntu things, so i just searched, i suggest for your own safety to do the same.
Or wait for someone more experient.
more information: [URL="http://askubuntu.com/questions/301458/how-can-i-tell-if-my-computer-has-bluetooth"]http://askubuntu.com/questions/301458/how-can-i-tell-if-my-computer-has-bluetooth


[/URL]

---

### Post by Vladlenin5000 on 2014-02-22
The command is correct indeed. The results vary according to the hardware detected (if any). Here's another example ```
Bus 002 Device 002: ID 0a5c:2121 Broadcom Corp. BCM2210 Bluetooth
```

There are however many other ways to know whether or not it come originally with the optional *Dell Wireless 375 Bluetooth[SUP]®[/SUP] 3.0* the easiest being Dell's website itself. There's a section where you enter the "service tag" (Dell's fancy name for "serial number") and it returns the complete original hardware configuration and OS version shipped with it plus warranty information. Now, WiFi and Bluetooth are two different things. Except the odd hybrid chips from 3DSP from some years ago and currently discontinued all the others are managed by two different chips often from different and unrelated manufacturers.

PS - BTW, the correct brand/model is Dell Latitude E6410.

---

### Post by GUZZLR on 2014-02-22
Yep...tried the Dell Website Service Tag. What's odd is the only place the service tag is recognized so far is  in the parts area. where are you talking about. do you have an address?

---

### Post by Vladlenin5000 on 2014-02-23
[http://www.dell.com/support/my-support/us/en/04?c=us&s=bsd&cs=&l=en](http://www.dell.com/support/my-support/us/en/04?c=us&s=bsd&cs=&l=en)

---

### Post by GUZZLR on 2014-02-23
Thank you...solves that mystery.  Apparently this machine did not have a bluetooth module installed at build time.  I'll need to see if I can find a used one somewhere.
Thanks for the help

---

### Post by Vladlenin5000 on 2014-02-23
You're welcome.

Parts for your Latitude should be easy to find and if having one less USB port isn't a problem for you there are many USB ones which are really cheap, certainly cheaper than any "original" part from Dell.

---

