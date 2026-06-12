---
title: "Please help me wireless firmware not found"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by tech over load on 2012-02-11
I have installed all drivers that it can find for my hardware on my gateway laptop but it still shows the firmware as missing what else can I do I really need my wireless Internet to work.



Please advise

---

### Post by uRock on 2012-02-11
Hello and welcome to the forums,

You had a reply in the thread you posted in last night recommending you post the output from the following command,> **chili555 said:**
> Let's also see the result of this terminal command:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.
Just copy the commend and paste it into a terminal. After the command runs copy the info and paste it here.

---

### Post by tech over load on 2012-02-11
I copied and pasted the info into the terminal and this is the response I received...
markkelly@markkelly-MX6445:~$ lspci -nn | grep 0280
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
markkelly@markkelly-MX6445:~$ 

Please advise thanks...

---

### Post by Miljet on 2012-02-11
Try taking a look at this link.

[http://ubuntuforums.org/showthread.php?t=1861669&highlight=wireless+internet](http://ubuntuforums.org/showthread.php?t=1861669&highlight=wireless+internet)

---

### Post by Mark Phelps on 2012-02-11
> **tech over load said:**
> I have installed all drivers that it can find for my hardware on my gateway laptop but it still shows the firmware as missing what else can I do I really need my wireless Internet to work.
Please advise

This makes no sense.  Firmware is supplied by the manufacturer of the device -- it's not something you have to add.  While there are firmware UPGRADES that are often made available, no device is included with a purchased PC without having the firmware already installed.

If something in Linux is saying there is no firmware, then what you are using is either faulty, or it can't see the device due to lack or, or improper, drivers.

---

### Post by tech over load on 2012-02-12
solved thanks people

---

### Post by uRock on 2012-02-12
What did you do to solve it?

---

### Post by tech over load on 2012-02-14
solved thanks

---

### Post by uRock on 2012-02-14
What did you do to solve it?

---

### Post by tech over load on 2012-02-14
solved

---

### Post by tech over load on 2012-02-14
> **uRock said:**
> What did you do to solve it?
solved

---

### Post by uRock on 2012-02-14
I get that it is solved. Can you share what you did to solve the issue?

---

### Post by varunendra on 2012-02-16
> **Mark Phelps said:**
> This makes no sense.  Firmware is supplied by the manufacturer of the device -- it's not something you have to add.  While there are firmware UPGRADES that are often made available, no device is included with a purchased PC without having the firmware already installed.
With all due respect, what you said used to be my old belief about firmware. But now having the experience (of others on this forum) with broadcom wireless chips, I know that a firmware sometimes can actually 'BE something you have to add'. But until a few minutes ago I didn't know how and why it happens. So after reading your post I thought it's time I understand it properly before saying a word about it. So I did a search, and I think I'm now satisfied with what I found. I hope these links would be sufficient to explain it to you as well.

**_Firmware in Computers/Peripherals_:**
(source: [http://en.wikipedia.org/wiki/Firmware#Personal_computers](http://en.wikipedia.org/wiki/Firmware#Personal_computers))
> Currently, devices like video cards, sound cards or modems in a modern  PC **often rely on firmware dynamically loaded by a device driver** and may  thus get transparently updated through the operating system update mechanisms.(source: [http://en.wikipedia.org/wiki/Firmware#Computer_peripherals](http://en.wikipedia.org/wiki/Firmware#Computer_peripherals))
> While external devices (printers, scanners, cameras, USB drives,...) have firmware stored internally, modern graphics cards and peripheral expansion **cards  often have parts of the firmware loaded by the host system at start-up**,  as this provides greater flexibility. Such hardware may therefore fail  to function fully until the host computer has "fed" it the requisite  firmware, typically via a specific device driver (more exactly: via a start-up subsystem within a device driver package).[B][U]
Broadcom Chips in Linux[/U]:[/B]
(source: [http://linuxwireless.org/en/users/Drivers/b43#Device_firmware_installation](http://linuxwireless.org/en/users/Drivers/b43#Device_firmware_installation))
> The Broadcom wireless chip needs proprietary software (called  "firmware") that runs on the wireless chip itself to work properly. **This  firmware is copyrighted by Broadcom and must be extracted from  Broadcom's proprietary drivers**. To get such firmware on your system, you  must download the driver from a legal distribution point, extract it,  and install it.Thanks for bringing up the question, for it inspired me to get a better understanding of the issue. I hope it'll help to add something to the knowledge of others too who come across this thread.

---

