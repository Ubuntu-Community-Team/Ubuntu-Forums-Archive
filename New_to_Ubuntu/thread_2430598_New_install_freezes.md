---
title: "New install freezes"
date: 2019-11-04
forum: New to Ubuntu
---

### Post by jellicus on 2019-11-04
I'm running it on an Asrock integrated Intel J1900 fanless board, and it seems to freeze randomly. It can be up for days, or hours. The system is more stable running W10, but I have experienced freezes there too. Should I be focusing on hardware? It's only the MB, an SSD, a HD, and 2 USB dongles for BT and wireless keyboard/pointer.

---

### Post by Autodave on 2019-11-04
Definitely focus on hardware.  My first thought is overheating.  Get some cooling going over, through, around that machine.  Put a little desk fan or something else to move air.  If that helps or eliminates the problem, you will then know.  Can you post the model and specs/pictures of this unit?  I tried a search, but not really sure what you have there.

---

### Post by jellicus on 2019-11-04
Thanks for your response. It's an ASRock Q1900B-ITX Intel Celeron J1900 2.0GHz Mini ITX Motherboard. It's specs are still up on Newegg. I use a similar board for my desktop running W10 and have had no issues at all.  I have not noticed temp problems, but one of the reasons I want to ditch W10 is the damn security apps that peg my CPU cycles to 100% for no obvious reason. Not good when you're trying to run low power and silent. FWIW, the DIY case is barely a case, there's no impairment of convection, and at this point the top is off and the board is in open air. Is there a good temp logger where the file would not be destroyed by a freeze and hard reboot?

[https://c1.neweggimages.com/NeweggImage/ProductImageCompressAll1280/13-157-497_R01.jpg](https://c1.neweggimages.com/NeweggImage/ProductImageCompressAll1280/13-157-497_R01.jpg)

---

### Post by oldfred on 2019-11-04
Please attach photos or screenshots.If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

If not in a case that could be part of issue as then you do not have a fan moving air?

---

### Post by jellicus on 2019-11-04
> **oldfred said:**
> Please attach photos or screenshots.If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

If not in a case that could be part of issue as then you do not have a fan moving air?

Did I break a rule with the inline link? Sorry. So no inline, only attachments?  As for the board, it's designed to be very low wattage and fanless using passive convection. I *shouldn't* have to use a fan, but I guess when you dance close to the edge sometimes you fall off. I'm going to watch the heat levels and see if it's suspect.

---

### Post by jellicus on 2019-11-05
Well, last night while streaming (this is an HTPC) it hit 65c. This processor is rated to 105c according to mfr, so I'd say it's within spec. Keep in mind this board is explicitly designed to be fanless, I'm not hacking it in any way.

But it froze while I was messing around trying to get my BT keyboard to connect, I wonder if there's some driver issue with the dongle?

---

### Post by hk42 on 2019-11-07
I only had problems with blue tooth keyboards:
No way to access BIOS
Pairing required each time you change OS on a multi-boot system.

Multi boot Linux/W10 on the same system is a very good way to diagnose between software and hardware problems.

---

