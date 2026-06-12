---
title: "NVidea Bad Driver, Slows PC - Should I Replace Graphics card?"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Teasdale on 2008-08-31
I posted a few weeks ago because every time I used GIMP or viewed photos, my computer would slow to a crawl. I installed Mirage, which seemed better - but now the slowness seems to be getting worse. I assume it's the NVidea card. When I first installed Ubuntu, my son spent hours researching different ways to try and get a driver for the video card that Ubuntu would work with. Everything he tried was even worse than using whatever default Linux started with, so we went back to that and I just have to live with the oddness resulting from that (strange lines when closing programs, inability to use a screensaver, etc).

But I want to work more with photos, and it only takes a few photos before the computer is so slow that it locks up and I have to reboot. 

Would it be a good idea to just buy a new graphics card, or would that be a bad idea because a new card wouldn't sync with my 5-yr old computer/motherboard?

And, if a new graphics card would solve my problem, are there certain brand names I should look for? I already know that NVidea is a bad match for Ubuntu.

---

### Post by pi.boy.travis on 2008-08-31
Did you try looking in System-Administration-Hardware Drivers?

As for a new graphics card, I would recommend Intel.

---

### Post by ARhere on 2008-08-31
> **Teasdale said:**
> ...but now the slowness seems to be getting worse. I assume it's the NVidea card ... But I want to work more with photos, and it only takes a few photos before the computer is so slow that it locks up and I have to reboot ... 
Viewing pictures requires more system memory and not necessarily video card memory.  You said it is 5 years old so I would guess you have only 256 or 512 MB of RAM.  Your first step should be to get more RAM.

> Would it be a good idea to just buy a new graphics card, or would that be a bad idea because a new card wouldn't sync with my 5-yr old computer/motherboard?
You might have problems.  An old AGP NVidia Ti 4200 could be picked up at EBay for dirt cheap now and would be perfect.  My guess is you are fine with the video card.

> And, if a new graphics card would solve my problem, are there certain brand names I should look for? I already know that NVidea is a bad match for Ubuntu.
Actaully, NVidia is the best bet for Linux IMO.  Others say ATI is, but the point is NVidia and ATI are well supported.  If you want to upgrade an ATI or NVidia driver, you best bet is to use the ENVY software to automatically do this for you.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
It is a one-click solution.  Remember to read his instructions on the web page as you probably have a legacy video card.

-AR

**[i]EDIT: **Post your video card information.  In a terminal, type "lspci" and copy+paste the line that says "NVidia" something.
Example... ```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
```[/i]

---

### Post by Teasdale on 2008-08-31
*There were LOTS of lines that said nVidea something, but this is the only one that looked like a video card. There was also memory controller, audio controller, audio, ethernet controller, USB, bridges . . .*

02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)

-----------------------

I don't know whether any of the following makes a difference, but I have this info as well:

Motherboard: ASUSTeK A7N266VM
version: REV 1.xx

BIOS: ASUS A7N266-VM ACPI BIOS Rev 1004/AA 
size: 64KB   capacity: 192KB

CPU: AMD Athlon(tm) Processor 6.8.1
size: 1666MHz
capacity: 2GHz
width: 32 bits
clock: 133MHz

slot: L1 Cache
size: 128KB
capacity: 128KB

slot: L2 Cache
size: 256KB
capacity: 8MB

System Memory
size: 256MB
capacity: 512MB

---

### Post by ARhere on 2008-09-01
Found your MB here -->[http://www.mikeshardware.com/reviews/review_a7n266-vm/review_a7n266-vm_review.html](http://www.mikeshardware.com/reviews/review_a7n266-vm/review_a7n266-vm_review.html)

I am assuming you are using the on-board graphics as it shares your main RAM.  I am not sure what...
"System Memory
size: 256MB
capacity: 512MB" 
...means.  I am guessing you have 512 MB RAM and have half of it shared as video RAM.  Check this in your BIOS.

You have three options,
1.  Upgrade to a newer motherboard + CPU + RAM.  Against all belief this can be easily done without much money or knowledge, unless you are a hard core gamer.

2.  Get more RAM for your current system.  Unfortunately PC2100/1600 DRAM (*the memory your system takes*) is getting hard to find.

3.  You could get a newer AGP video card and disable on the on-board graphics in the BIOS, this will free up more memory for your pictures.

If you choose for option #2 I will help you.  Let me know.
-AR

[i]**EDIT:** If I am correct that you have 512MB RAM and are dedicating 256 of it to your video card, then simply reducing the memory to your video card to 32MB will help a LOT with viewing pictures.  This will increase the available RAM form 256MB's to 480MB's and should help.
Please check your BIOS settings.[/i]

---

### Post by nhasian on 2008-09-01
agreed.  sounds like not having enough ram is your main problem but adding more memory to such an old system is just a bandaid solution to the problem.  I strongly recommend a new motherboard/cpu/ram/video card.  If you dont want to buy new (like a quad core intel processor) then i'm sure you can find a 2 year old dual 3.2Ghz system for cheap on ebay or craig's list.

---

### Post by ARhere on 2008-09-01
> **nhasian said:**
> agreed.  sounds like not having enough ram is your main problem but adding more memory to such an old system is just a bandaid solution to the problem.  I strongly recommend a new motherboard/cpu/ram/video card.  If you dont want to buy new (like a quad core intel processor) then i'm sure you can find a 2 year old dual 3.2Ghz system for cheap on ebay or craig's list.

BAH!  I can put a new screaming system togeather for him on newegg.com for less then $500.  If just a MB + Processor + Memory, you can find deal for as little as $180.

-AR

---

