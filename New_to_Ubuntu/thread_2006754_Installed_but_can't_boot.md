---
title: "Installed but can't boot"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by Nanur on 2012-06-19
Hey all, so I just installed Ubuntu onto my D: (this drive does not have Windows on it, but my C: does) I used a USB plugged it in, and chose the "run" option and from there I clicked the Installation icon and off I went.
So once I got into the setup, I setup three separate partitions: one 15Gb for /, one 80Gb for /home, and one 2Gb for /swap. The installation did it thing and before I knew it, it was done, so I restarted. The screen came up and showed "Windows and Ubuntu" so I pressed Ubuntu and it gave me an error message:



Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

     1. Insert your Windows Installation disc and restart your computer.
     2. Choose your language setting, and then click "Next."
     3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

     File: \ubuntu\winboot\wubildr.wbr

     Status: 0xc0000000f

     Info: The selected entry could not be loaded because the application is missing or corrupt.



Although I believe this happened because I had a wubi install of Ubuntu on my C:, but just deleted it, and made a permanent install on my D:, which is not appearing. This especially could not be the D: Ubuntu since it also had Windows on the option menu.

I went into my boot setup to see if there was a problem with the order the hard drives boot from. All I saw was onboard SATA (my C: for Windows) and USB Device. I booted into Windows and found that my D: didn't show up. (it wasn't on the list of hard drives)
If it helps, my D: is internal.
Any help would be great!

---

### Post by wilee-nilee on 2012-06-19
Run this tool to use the bootinfo summary using the ubuntu live cd and post the HTTP address.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Sounds like grub was put in the wrong discs mbr, the bootinfo summary will give us a better look at the setup.

---

### Post by Nanur on 2012-06-19
> **wilee-nilee said:**
> Run this tool to use the bootinfo summary using the ubuntu live cd and post the HTTP address.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Sounds like grub was put in the wrong discs mbr, the bootinfo summary will give us a better look at the setup.

So I boot into my live CD, and then run that tool?

---

### Post by wilee-nilee on 2012-06-19
> **Nanur said:**
> So I boot into my live CD, and then run that tool?

Yes, use the tool to generate the bootinfo summary only at this point, and post the http address to it.

---

### Post by Nanur on 2012-06-19
Here is the URL:
[http://paste.ubuntu.com/1049962/](http://paste.ubuntu.com/1049962/)

---

### Post by nipunshakya on 2012-06-19
> **Nanur said:**
> 
Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

     1. Insert your Windows Installation disc and restart your computer.
     2. Choose your language setting, and then click "Next."
     3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

     File: \ubuntu\winboot\wubildr.wbr

     Status: 0xc0000000f

     Info: The selected entry could not be loaded because the application is missing or corrupt.



Hello Nanur, i guess you have a Dell laptop because i have had similar problem when i was trying to install a 32-bit Win XP on my machine after removing Windows VIsta 64-bit(long ago). 

Searching a bit led me to a result that the AHCI was enabled in the BIOS under my hardware configuration. Turns out that i simply have to disable AHCI in order to install a 32-bit os in dell laptops of x86_64 architecture and enable the other SATA mode...(i forgot the exact name of other mode,sorry). It worked for me a long time ago(2.5 years back)...but its worth checking it once in your BIOS options about your hardware configurations too... Goodluck

---

### Post by wilee-nilee on 2012-06-19
So that we are on the same page partitions do not go by letters here, but buy there names sda1....etc.

This is a perfect example why, what you call D is actually a whole other HD, it could of been another partition on the sda disc, very confusing at the least.

If you cannot see the sdb drive in the bios it sounds like you have a master and slave set up the slave the sdb drive is not bootable then.

You are best having both OS's on the sda drive, if this is the case. It could be the 320 gig HD if you wanted, depending on the data you have altogether, and whether you want to do a copy and paste of the windows Partition.,

You can go into the windows setup using the ubuntu live cd and remove all wubi stuff with a search.

Might just need a cable change, that is out of my area, for the sdb to show up though so lets see what others have to say.

---

### Post by Nanur on 2012-06-19
The Boot-Repair tool fixed everything up nicely, I can boot into both Windows, and Ubuntu. Everything works perfectly now! Thanks wilee-nilee for telling me about that tool. :)
-Nanur

---

### Post by wilee-nilee on 2012-06-19
> **Nanur said:**
> The Boot-Repair tool fixed everything up nicely, I can boot into both Windows, and Ubuntu. Everything works perfectly now! Thanks wilee-nilee for telling me about that tool. :)
-Nanur

It is a good tool glad you were able to use it to get fixed up. ;)

---

### Post by Nanur on 2012-06-19
Yeah, all I had to do is plug my live-USB in and run the tool, and problem fixed!

---

