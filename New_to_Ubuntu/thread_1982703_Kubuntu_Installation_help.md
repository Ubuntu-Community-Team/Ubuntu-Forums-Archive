---
title: "Kubuntu Installation help"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by Nato71 on 2012-05-19
Hi, I am new to Linux and this forum and wondered if anyone could please help me.

I have a 6 year old iMac G5 PPC that I want to try Linux on.
So, I chose a flavour, Kubuntu 12.10, and downloaded the Live CD (the 64bit PPC version) and tried out the environment.
I liked what I saw and clicked on the desktop icon that offers to install the OS.
After eventually getting through the partitioning stage the install began but hangs at 64% which is titled "Loading module 'usb-storage' for USB storage".
I waited for an hour or so but no progress. I could minimise the window and use the Live session as normal, no problems there.
I have to admit there was a kind of rage-quit moment and I switched the machine off and redid the process. Same result.

Could the problem be on the disc or is it more likely something else?

The machine has the following specs
2.1GHz PPC G5
1.5GB DDR2 SDRAM
ATI Radeon X600 XT

Thanks in advance!!

Nato

---

### Post by carl4926 on 2012-05-19
Did you run the Check Disk for Defects?
You may need to hit Esc as the CD boots to get to that menu

---

### Post by carl4926 on 2012-05-19
> **carl4926 said:**
> Did you run the Check Disk for Defects?
You may need to hit Esc as the CD boots to get to that menu

Just to be clear
This is checking the CD for defects, not your HD.

It's important to burn the .iso on quality media and slowly or you can use a USB flash drive if your machine supports USB booting

---

### Post by Utkarsh Ray on 2012-05-19
> **Nato71 said:**
> Hi, I am new to Linux and this forum and wondered if anyone could please help me.

I have a 6 year old iMac G5 PPC that I want to try Linux on.
.
.
.
.
The machine has the following specs
2.1GHz PPC G5
1.5GB DDR2 SDRAM


You are trying to use 12.10 which is currentlyunder development. If you want to just 'try' linux, you should rather get 12.04, I'd suggest using Lubuntu as it's less resource intensive. Also after downloading the ISO check its MD5 sum as carl4926 said.

---

### Post by Nato71 on 2012-05-19
Thanks guys, this is driving me nuts!

I just checked the disc again with OSX disk utility and it said it needed repair so that must be the problem.
What's weird is that I verified it after burning the iso which was ok at the time???

I'll download 12.04 and see how I go with that.

---

### Post by carl4926 on 2012-05-19
Darn
I just thought .10 was a typo/mistake

Crumbs mate!

---

### Post by Nato71 on 2012-05-19
Yeah, not sure how that happened! Must have downloaded that by mistake and didn`t realise.

D'oh! Told you I was new.....

---

### Post by Nato71 on 2012-05-19
Well, I downloaded 12.04, burnt the iso and installed successfully.

Then on booting it said "Error" PCI card not supported, check this website for this card.
But the card I have is not the one it detected (??) and I have no idea where to go from here.

To be honest its been so difficult to get a working Linux OS, 3 days of trying different things, I feel I'm in over my head so back to OSX I go. Ho hum :(

Thanks for your help guys, I appreciate the time you gave me.

---

### Post by Utkarsh Ray on 2012-05-21
> **Nato71 said:**
> 
Then on booting it said "Error" PCI card not supported, check this website for this card.
But the card I have is not the one it detected (??)


If it's the manufacturer's website, probably they are showing the new name of the card.
Try installing it.

---

