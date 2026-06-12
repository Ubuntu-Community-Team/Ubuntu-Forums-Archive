---
title: "Will Ubuntu &quot;see&quot; all my hardware on my homebuilt computer?"
date: 2020-04-25
forum: New to Ubuntu
---

### Post by rocket57 on 2020-04-25
Hi folks - newbie still here (though I am learning a lot reading posts by moderators, emeritus, and super and visiting AskUbuntu)
I am enjoying Ubuntu MATE! So I wondered about this: 
I built a computer. It ran on Win 7 ok. Then I made the mistake of clicking on upgrade to Win10, and everything went whacko with my graphics card and wi-fi card. No, I can't restore it back to Win 7. I want to install Linux Ubuntu MATE and hopefully it will get everything back together again and running. I intend to keep it Linux. What I want to ask is: will Ubuntu "see" and "use" all of my hardware if I install it?
Thanks in advance, hopefully yours,
Rocket

MyBuild: Colossus (the Warren Project)
[FONT=arial][URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16811119265"]_[COLOR=#000000]Cooler Master HAF XB EVO - High Air Flow Test Bench and LAN Box Desktop Computer Case[/COLOR]_
[/URL]
[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16813128723"][COLOR=#000000]GIGABYTE GA-Z97X-UD3H-BK (rev. 1.0) LGA 1150 Intel Z97 HDMI SATA 6Gb/s USB 3.0 ATX Intel Motherboard[/COLOR]
 [/URL]
Dell P2715Q Monitor

EVGA GeForce GTX 970 04G-P4-2974-KR 4GB 256-Bit GDDR5 PCI Express 3.0 x16 SLI Support

CORSAIR Dominator Platinum 16GB (4 x 4GB) 240-Pin DDR3 SDRAM DDR3 1866 (PC3 14900) Desktop Memory

Intel Core i7-4790K Devil’s Canyon Quad-Core 4.0 GHz LGA 1150 BX80646I74790K Desktop Processor Intel HD Graphics 4600

[[COLOR=#000000]SAMSUNG 850 PRO MZ-7KE256BW 2.5" 256GB SATA III 3-D Vertical Internal Solid State Drive (SSD) [/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820147360")[COLOR=#000000]
---and a Gigabyte Wi-Fi card, 2 hot swap 1Tb WD, and a 2 Tb WD external drive…[/COLOR][/FONT]

---

### Post by CelticWarrior on 2020-04-25
Yes, Ubuntu will "see" all your hardware.

---

### Post by rocket57 on 2020-04-25
Sorry to bother you - I just figured out (duh) that I could just boot to a live USB and see for myself!

It's so hard to get out of the Windows mindset!

I'm learning though!  

Rocket

---

### Post by Impavidus on 2020-04-25
Ubuntu should see all your hardware and use most of it, but sometimes additional drivers are needed. You don't have to search for them on the web; it all happens almost automatically.

You may have to install the proprietary nvidia drivers for your graphics card. There is an option for that in the installer. It will automatically find the best driver and download and install it. To boot the live disk (with the installer) without getting a black screen, you may need the nomodeset option. [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Wifi is sometimes a problem, but usually it works right out of the box.

Now keep in mind that Ubuntu is not Windows. Most commercial software for Windows won't run on Ubuntu.

---

### Post by TheFu on 2020-04-25
> **CelticWarrior said:**
> Yes, Ubuntu will "see" all your hardware.

Short answers seldom tell the whole story.

Mainstream hardware will be seen but that doesn't mean there are drivers. We all have some odd hardware that either works, is seen but doesn't work or isn't even seen.

The best way to figure out is to create a "Live Boot" Ubuntu install flash drive, boot that on the machine and see what works and what doesn't work.  From that flash drive, we can ask good questions about any non-working hardware and possibly get it working.

The good news is that pretty much all hardware will work.  There are a few odd webcams and fingerprint readers and slide scanners that have no drivers.  That's been my experience.  Old GPUs may not have proprietary drivers anymore but there are F/LOSS GPU drivers that work on some level for pretty much any GPU.  For example, my nvidia 7200 GS doesn't have proprietary drivers that work since 16.04. 

i vaguely remember an issue with the Samsung 850 SSDs a few years ago.  Don't recall if that was incompatibility with specific controllers or a kernel version. Probably fixed but idk.

---

### Post by Autodave on 2020-04-25
> **rocket57 said:**
> Sorry to bother you - I just figured out (duh) that I could just boot to a live USB and see for myself!

It's so hard to get out of the Windows mindset!

I'm learning though!  

Rocket

It IS hard to get out of that mindset.  I moved everything to Ubuntu or Xubuntu about 8 years ago and I still, occasionally, find myself wanting to defrag the HD. :-)

---

