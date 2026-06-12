---
title: "Pre-Installation Questions Dell GX1"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by harpoonz on 2008-10-21
Hi, I wanted to ask a few bios and hardware related questions regarding a Dell GX1 on which I'll be installing Xubuntu. I read a related post on these forums but still have some unanswered questions. 

My current specs on the Dell are PII 400mhz/256MB RAM/20GB hard drive.  According to this page:

 [http://docs.us.dell.com/support/edocs/systems/ban_gx1/specs.htm]("http://docs.us.dell.com/support/edocs/systems/ban_gx1/specs.htm") 

I can upgrade to a PIII 600 which conflicts with other items I've read stating the GX1 can take up to a Slot1 1Ghz Coppermine chip or perhaps higher with a slocket. I know these are pretty popular machines so can someone experienced with the GX1/GX1P help me out? On a related note, I know I'll have to flash the bios. Currently, the machine is running the A04 version but I would like to know which version is the most stable. It looks as if most of you are running either A07 or A09. I'm assuming the updated bios will allow for faster procs and as much as I'd like to pop a 1Ghz in there, I'd like to know if it will work before I scavenge one off of Ebay. 

Does the bios update allow for 256MB double sided modules to be used and recognized as such? I ask because I popped two non-ecc 256MB modules in and the OS and bios only recognize the pair as 256MB total. I seem to remember having a socket 7 board that didn't recognize double sided RAM, although it was so long ago I really can't remember. I hope this isn't the case with the GX1, big difference between 384 and 768 max. I've read a few other threads with people using half a gig o' ram in these machines so I'm hoping I can max out at 768. If worse comes to worse, I'm sure 384MB will suffice for web browsing, word processing, online videos etc but I was hoping I could get this thing to play DVDS as well. Is it possible with the onboard video or will I need to buy a PCI video card? 

Sorry for all the questions but it can be hard correct info on legacy equipment.  I figured there would be a lot of people here familiar with the GX1 so hopefully some of you can help a guy out. :)

Thanks in advance!

---

### Post by ronnielsen1 on 2008-10-21
> I ask because I popped two non-ecc 256MB modules in and the OS and bios only recognize the pair as 256MB total.
It sounds like it's recognizing 128MB off of each one and according to the specs that dell gave you
> [FONT=Times New Roman]DIMM capacities[/FONT]     [FONT=Times New Roman]32-, 64-, and 128-MB non-ECC     SDRAM ("PC100" 100 MHz);
    32-, 64-, 128-, and 256-MB ECC SDRAM ("PC100" 100 MHz)[/FONT]
the box will only see a max of 128 MB on non-ECC - you will need ECC ram to go to 256 MB on this mobo
> I was hoping I could get this thing to play DVDS as well. Is it possible with the onboard video or will I need to buy a PCI video card? 
Dvd's shouldn't be a problem. Beryl would be a problem

---

### Post by harpoonz on 2008-10-21
Good to hear about DVD playback.  I'm not concerned about Beryl so no biggie there. 

I did see the RAM specs but am still wondering if the bios update will rectify the RAM issue.  I've read other people saying they have a GX1 with 512MB or more RAM installed.  

Looks like I'll have some spare time later today to update the BIOS (going to try version A07 first) so I guess I'll find out first hand.

---

