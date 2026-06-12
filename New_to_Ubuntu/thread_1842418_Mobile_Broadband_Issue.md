---
title: "Mobile Broadband Issue"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by fardy0 on 2011-09-11
I have recently decided to try Ubuntu out. I am having trouble getting my mobile broadband dongle to work. It is being recognized as a pen drive but not as an internet dongle. The dongle is Huawei E1752c

I have no experiance using this OS so maybe there is an obvious solution 

The dongle does work as i am using it with my PC running XP

Cheers

---

### Post by Wim Sturkenboom on 2011-09-11
You need something called usb-modeswitch; it's in the repositories. I hope you have a different means (e.g. wired connection) to get it.

Somebody else might be able to tell you how to get it using a different computer.

---

### Post by fardy0 on 2011-09-11
I have usb-modeswitch it must have installed with the OS. I am a bit of a loss as what to do now though

---

### Post by gandaran on 2011-09-11
> **fardy0 said:**
> I have recently decided to try Ubuntu out. I am having trouble getting my mobile broadband dongle to work. It is being recognized as a pen drive but not as an internet dongle. The dongle is Huawei E1752c

I have no experiance using this OS so maybe there is an obvious solution 

The dongle does work as i am using it with my PC running XP

Cheers
have you tried the network manager mobile broadband setup wizard?
you just select country and internet provider then the modem should connect.
and which ubuntu release do you have?

---

### Post by fardy0 on 2011-09-11
Yes i have that done. I have version 11 04

---

### Post by gandaran on 2011-09-11
> **fardy0 said:**
> Yes i have that done. I have version 11 04
does it try to connect when you click the setup in the panel icon or doesn't do anything at all?
try a reboot after the setup.
also check the login details like the APN for your internet provider are correct.

---

### Post by fardy0 on 2011-09-11
Nothing happens at all, its as if the laptop only recognizes the dongle as a pen drive and not as a modem

---

### Post by gandaran on 2011-09-11
> **fardy0 said:**
> Nothing happens at all, its as if the laptop only recognizes the dongle as a pen drive and not as a modem
that shouldn't be the problem, mine worked as a mounted cd drive in ubuntu 10.04 and still connected fine.
have you installed all ubuntu updates on 11.04? using wired internet? if you haven't do it, there is some updates for the usb-modeswitch and internet providers info packages, maybe the new usb-modeswitch package supports your dongle.

---

### Post by westie457 on 2011-09-11
Believe this or not. Even when using a USB dongle you need to have the on-board wireless turned on, usually a switch or key combination and you also need the correct drivers installed otherwise it will not work.

Could you open a terminal (Ctrl+Alt+t) and run ```
lsusb
```and ```
lspci
```
and ```
rfkill list all
```
Then highlight all the output, copy and paste into a new reply between [CODE] tags by clicking the # in the menu bar. This will make things easier to read and also give us a clue to what is needed to help you.

Thank you.

---

### Post by sujitrjadhav on 2011-09-11
Have you installed appropriate drivers for the dongle? In my case I have usb dongle from zte company which has a CDFS partition where from I can install required .deb driver. Check if your usb dongle too have CDFS partition and if yes install appropriate package (may be .deb package.)

---

### Post by gandaran on 2011-09-11
> **westie457 said:**
> Believe this or not. Even when using a USB dongle you need to have the on-board wireless turned on, usually a switch or key combination and you also need the correct drivers installed otherwise it will not work.

Could you open a terminal (Ctrl+Alt+t) and run ```
lsusb
```and ```
lspci
```
and ```
rfkill list all
```
Then highlight all the output, copy and paste into a new reply between [CODE] tags by clicking the # in the menu bar. This will make things easier to read and also give us a clue to what is needed to help you.

Thank you.
really? I use the Huawei E1550 dongle on my netbook with the wireless switch off every-time and haven't seen any problem

---

### Post by ironic.demise on 2011-09-11
Out of the box, my HUAWIEE(or whatever) worked fine.
Top left corner, clicked the network applet, new mobile broadband connection.
Followed on-screen prompts, without needing to download any updates either.

to learn how to use modeswitch, as I haven;t used it myself, try looking at the modeswitch manpage ```
man modeswitch
``` or find the manpage on the ubuntu site.

---

### Post by westie457 on 2011-09-11
> **gandaran said:**
> really? I use the Huawei E1550 dongle on my netbook with the wireless switch off every-time and haven't seen any problem

You are correct. I got myself confused and thought we were talking about an ordinary wireless dongle. Of course a Mobile Broadband dongle works differently.

---

