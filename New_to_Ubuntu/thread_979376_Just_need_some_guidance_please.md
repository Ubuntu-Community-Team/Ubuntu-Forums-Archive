---
title: "Just need some guidance please"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Ricorich196 on 2008-11-11
Okay so I'll try to break this down so that I can get some guidance while helping you all helping me =)

[B]System Specs:
Dell Dimension 4600
WinXP Home
Intel 865PE Chipset
1GB Ram
2.66 GHz P4
Nvidia 5200FX AGP Video card
120 GB IDE HDD[/B]

Now here's a quick run down of what's currently going on
I have a weird combination of virus/trojan/spyware that's completely dismantaling my system as we speak (please don't mention running any programs to fix this, I've tried everything in safe mode including 2 different antivirius (avast/Avira), Adaware, Spybot, Malwarebyte's Antimalware ect.)

My plan is to buy a 500 GB SATA drive (my mobo has 2 sata ports) and cleanly install Ubuntu Intrepid Ibex. I'm done with windows and viruses and it being so bloated, I've been put on to Linux and while I know it might be rough but I'm willing to go for the long haul.

Now for the questions (yeah you knew they were coming lol)

Can Ubuntu natively recognize SATA HDDs? I know WinXP when installing doesn't without having the SATA drivers on a Floppy during the initial install. 

Next what I wanted to do was put the old 120 GB IDE HDD in an external enclosure and connect it to my computer that hopefully will be running Ubuntu and using NTFS Config (I think that's the name of the program) copy over all the Media that I need onto the 500 Giger.

Also as a side note I plan I installing a SATA DVD burner, will Ubuntu automatically recognize it? If not what will I need to do for it to?

I've searched in regards to Ubuntu automatically picking up SATA drives but none of the threads I found involved CLEAN installing Ubuntu, instead the SATA drives were either a secondary drive or partitioned with a different OS on the separate partition.

Any help would greatly be appreciated!

---

### Post by handydan918 on 2008-11-11
> **Ricorich196 said:**
> Okay so I'll try to break this down so that I can get some guidance while helping you all helping me =)

[B]System Specs:
Dell Dimension 4600
WinXP Home
Intel 865PE Chipset
1GB Ram
2.66 GHz P4
Nvidia 5200FX AGP Video card
120 GB IDE HDD[/B]

Now here's a quick run down of what's currently going on
I have a weird combination of virus/trojan/spyware that's completely dismantaling my system as we speak (please don't mention running any programs to fix this, I've tried everything in safe mode including 2 different antivirius (avast/Avira), Adaware, Spybot, Malwarebyte's Antimalware ect.)

My plan is to buy a 500 GB SATA drive (my mobo has 2 sata ports) and cleanly install Ubuntu Intrepid Ibex. I'm done with windows and viruses and it being so bloated, I've been put on to Linux and while I know it might be rough but I'm willing to go for the long haul.

Now for the questions (yeah you knew they were coming lol)

Can Ubuntu natively recognize SATA HDDs? I know WinXP when installing doesn't without having the SATA drivers on a Floppy during the initial install. 

Next what I wanted to do was put the old 120 GB IDE HDD in an external enclosure and connect it to my computer that hopefully will be running Ubuntu and using NTFS Config (I think that's the name of the program) copy over all the Media that I need onto the 500 Giger.

Also as a side note I plan I installing a SATA DVD burner, will Ubuntu automatically recognize it? If not what will I need to do for it to?

I've searched in regards to Ubuntu automatically picking up SATA drives but none of the threads I found involved CLEAN installing Ubuntu, instead the SATA drives were either a secondary drive or partitioned with a different OS on the separate partition.

Any help would greatly be appreciated!

Can't give too many definitve answers here, but I am post from a system with SATA drives, no probs. 
The thing that struck me is "Why replace your IDE drive?"

After you install Ubu, any remnants of the virus code left on the disk will be WISHING they could find enough Windows code left to survive....

---

### Post by bumanie on 2008-11-11
In short, ubuntu should recognize all your hardware - everything you have listed should have drivers available in the kernel - and you should be able to enable the nvidia gpu via hardware drivers. ubuntu should work fine.

---

### Post by Ricorich196 on 2008-11-11
> **handydan918 said:**
> Can't give too many definitve answers here, but I am post from a system with SATA drives, no probs. 
The thing that struck me is "Why replace your IDE drive?"

After you install Ubu, any remnants of the virus code left on the disk will be WISHING they could find enough Windows code left to survive....

I want to replace my IDE drive with a SATA for the better performance for the same/less cost. The 500 GB Seagate I want to buy is $70 on Newegg and on back order in IDE for $84.99 so I figured SATA would be a better look.

And if any of that virus/spyware makes its way off of my old HDD (which I doubt but you never know) onto my new one running Ubuntu I'm happy to know it couldn't find it's own rear with two hands and a map.

Quick question, did you do a clean install of Ubu onto your SATA drives? Or were you running a different OS prior? I'm basically going to have a OS-less PC when it comes time to install Ubu. I want to know if it'll be as simple as install SATA HDD> Insert Ubuntu CD> Install.

---

### Post by Ricorich196 on 2008-11-11
> **bumanie said:**
> In short, ubuntu should recognize all your hardware - everything you have listed should have drivers available in the kernel - and you should be able to enable the nvidia gpu via hardware drivers. ubuntu should work fine.

Sounds great! The only reason I'm being so cautious is if something goes wrong I'm screwed, this is my ONLY computer in the house so in order for me to get help I'd have to return here via friends house/my PDA/Library ect. So I want to be absolutely sure I can do this without running into ANY issues.

---

### Post by blackened on 2008-11-11
> **Ricorich196 said:**
> Sounds great! The only reason I'm being so cautious is if something goes wrong I'm screwed, this is my ONLY computer in the house so in order for me to get help I'd have to return here via friends house/my PDA/Library ect. So I want to be absolutely sure I can do this without running into ANY issues.

You're in luck then. The install CD has a "Live" feature that lets you run a (somewhat slower) version of Ubuntu without having it installed to the harddrive. So, if you run into problems during the install, then you can always pop in the live cd to search for answers on the web. Take my advice though: before you install Ubuntu from burned media make sure you check the media from the startup menu provided by the livecd. If you have a bad burn you will run into problems during the installation and the livecd will likely not work.

---

### Post by Crafty Kisses on 2008-11-11
Sounds like a solid machine, don't worry the HD's will get detected. From the looks of it, everything should work out for you.

---

### Post by handydan918 on 2008-11-12
> **Ricorich196 said:**
> 
Quick question, did you do a clean install of Ubu onto your SATA drives? Or were you running a different OS prior? I'm basically going to have a OS-less PC when it comes time to install Ubu. I want to know if it'll be as simple as install SATA HDD> Insert Ubuntu CD> Install.

Clean install, actually across two SATA drives, 160 each.

---

