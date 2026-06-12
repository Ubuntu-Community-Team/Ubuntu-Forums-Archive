---
title: "Howto : Ricoh  (R5C592) Card reader with MMC cards"
date: 2008-03-22
forum: Outdated Tutorials &amp; Tips
---

### Post by aashay on 2008-03-22
I was having a hard time finding a solution to the the  Ricoh Co Ltd R5C592 to work on my Lenovo Laptop. From what I gathered, SD cards worked out of the box with the reader. However, it absolutely refused to recognize MMC cards. Today while searching around, I landed onto this Polish(?) blog which mentions the fix for the problem: [http://osnews.pl/ricoh-r5c822-i-linux-obsluga-mmc](http://osnews.pl/ricoh-r5c822-i-linux-obsluga-mmc) 
This is what I could understand

1. Make sure you have this card reader
```
lspci | grep Ricoh
```
```
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

I'm not too sure, but the 05:06.2 line read differently (something with a 'MMC' in it before the fix)

2. modprobe the required modules in case they arent already loaded
```
sudo modprobe mmc_core mmc_block sdhci
```
I'm not sure if the hdhci is required for MMC cards

3. Here's the crucial part. You need to configure the PCI device using setpci.
Note that the MMC controller in the lspci is preceeded by 05:06.2 . It may be xx:yy.2 on your machine.
Assuming it is 05:06.2 on your machine too, run
```
sudo setpci -s 05:06.2 0xCA=57
sudo setpci -s 05:06.2 0xCB=02
sudo setpci -s 05:06.2 0xCA=00
```
I already had the card in the reader when I was trying the fix. As soon as I executed the second setpci, the card mounted right up. I'm not too sure what exactly is happening here, maybe someone wiser can fill me in, but I sure am glad the reader is finally working

---

### Post by octesian on 2008-04-05
I have the same device but that solution doesn't work for me.  I don't know how to tell if the card is detected.  It doesnt mount or anything.

Heres my lspci

```

octesian@Graveyboat:~$ lspci | grep Ricoh
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


```

---

### Post by aashay on 2008-04-09
You should get the following two files under /dev
mmcblk0
mmcblk0p1
Just to make sure, did you setpci -s 03:01.2 instead of 05:06.2 as in my post?

---

### Post by octesian on 2008-04-11
Yeah, nevermind.  I think I was using the wrong type of card.

---

### Post by ryanleo on 2008-04-12
Hi, I am quite a newbie here and Ubuntu, but I totally like Ubuntu. I have the Lenovo F40M laptop, and with lspci, I got this information before:

05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C592 MMC Bus Host Adapter (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd Memory Stick Bus Host Adapter  (rev 05)

I can not remember clearly, but surely 05:06.2 is MMC and 05:06.3 is Memory Stick.

According to your guide, I successfully mounted my current MMC card, but then I want to mount my Sony Memory stick card, so I tried that three command with 05:06.3 and then My MMC does not word, neither do my Memory Stick.

Now my lspci shows:

05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)

I can not find the info of my MMC now, how can I make my MMC work again? and is there any way to make my memory stick work? ( My old Sony DSC-S70 can not be mounted automatically)

Thanks a lot in advance.

---

### Post by octesian on 2008-04-12
I think Memory Sticks aren't supported yet which was my problem.  Did you try rebooting and then following the instructions again?

---

### Post by aashay on 2008-04-12
I'm sorry, I do not have a memory stick and I did not make that tutorial either. I just kind of translated it off the site I mentioned. 
As octesian mentioned, rebooting the computer and applying the setpci again will make your MMC work. 
As for the memory stick, i doubt running the same commands for 5:06.3 will work.

---

### Post by ryanleo on 2008-04-12
Well, after I rebooted, and executed the lspci | grep Ricoh, and I got this:

05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)

So I executed that modprobe and setpci again, and not as the first time I executed that the MMC was mounted automatically, this time, nothing happened.


And as for the memory stick, I think I have to turn to XP to get the photos in my camera.

Anyway, thanks.

---

### Post by aashay on 2008-04-13
The MMC should automount once you execute the setpci. Rebooting seems to reset the setpcis, so if it doesnt work, try again after rebooting. If everything is working fine, create a new file 'setpci' or whatever you want to name it in /etc/init.d
Add this to it```
#!/bin/sh
# Setpci for MMC Cards

setpci -s 05:06.2 0xCA=57
setpci -s 05:06.2 0xCB=02
setpci -s 05:06.2 0xCA=00
```

---

### Post by xodeus on 2009-06-16
> **aashay said:**
> 
2. modprobe the required modules in case they arent already loaded
```
sudo modprobe mmc_core mmc_block sdhci
```
I'm not sure if the hdhci is required for MMC cards

thank you very much for this small guide. But when I execute this I get this error message. How do I get this module? 
```
FATAL: Module mmc_core not found.
```

> **aashay said:**
> ```
#!/bin/sh
# Setpci for MMC Cards

setpci -s 05:06.2 0xCA=57
setpci -s 05:06.2 0xCB=02
setpci -s 05:06.2 0xCA=00
```
Thank you for this script.

---

