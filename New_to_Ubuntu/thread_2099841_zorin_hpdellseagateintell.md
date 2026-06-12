---
title: "zorin hp/dell/seagate/intell"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by gerrman97 on 2012-12-30
I just recently bought a computer. It was orinally all hp and seagate. I installed 3 PCI  cards a hard drive and a cd-rom drive. One was a d-link modem card. The other was a generic sound card. Hd is a seagate. Cd is an hp cd writer plus. Problems: cd drive doesnt even say that its there. Hd freezes. Internal sound card doesnt work. External doesnt work either. Btw the computer will not boot into bios so i can install ubuntu. I have Zorin 6.1 lite. The only key that works is the esc key when booting. None of the function keys or numeric keys work during boot stages. Neither do the  arrow keys. Obviously a lot of problems please help

---

### Post by Bashing-om on 2012-12-30
gerrman97;

In a situation as described, back up five yards and punt !
1. Download the manual from the mainboards web site. Check all wiring. Old style ide drive ? Are they pinned correctly for the cable positions ?
2. Strip out all from the box down to the barest of necessities, now will it boot a known good cd ?
3. Power supply good 'nuff to run all the additional hardware added --say 400 watts ?
4. Any pins bent on the connectors ? How do the seats look for the cards ? How bout the cards themselves ?

The list can go on and on ...but these are good places to begin with.
Then when re-assembling do it one component at a time, testing the system as you go !

[INDENT][INDENT][INDENT]Know what I Mean, Vern <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by gerrman97 on 2012-12-30
Thank you for your suggestion. I have tried reseating everythin! I replaced the power supply cuz the first one burnt out in the testing stage. I think the problem with the keys is not the computer or the keyboard. I think its the bios or the drivers on the hard drive. I will pull it apart tonight all the way and test the parts. Hd is old style. How many kinds of hard drives are there.

---

### Post by Bashing-om on 2012-12-30
gerrman97;

Sounds like you have a plan. 
Hard drive, old style; two that were common. both ribbon cable and "ide" type. 

Very cheap systems ran the hard drive on the same ribbon as the cd drives (yuk). Best of my poor memory the cd was master as it was first component on the ribbon and the hardrive was pinned as slave.

Then there is the "ide" ribbon supporting two drives, the first drive pinned as master, the second positioned drive as slave.

Alternate "ide" drives with differing ribbon cable had to be pinned as "cable select"

Consult the manuals for the mainboard and the drives to determine the cable and pinning requirements. The pinning arrangements are often printed (smally) on the back of the hard drive.
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by gerrman97 on 2012-12-30
I have 1 hd connected. I is on its own line.  1 cd drive connected on its own line. For some unknown reason, the floppy drive has to be connected to boot the hd. Idk why. I tried to remove the floppy so i could install an extra hd (mines only a ten gig). I have a 1 tb but its SATA  and not meant for a desktop. Will that work if i get sata cables? I can email u the pictures of FRANK (my computer) so u can tell me what u think.

---

### Post by squakie on 2012-12-31
If you don't have SATA on the mainboard or no SATA adapter card, you can't use the SATA drive - they are physically very different from an IDE drive.

Again, as has already been recommended a couple of times, download the manual for your motherboard and look it over for what is supported and what isn't.  

IDE interfaces use a master/slave configuration - 1 drive on the cable needs to be configured as master using a jumper on the back of the drive.  If there are 2 drives on the cable, the 2nd needs to be set to slave via the same set of jumpers on the back of that drive.  You also won't have any luck if you have a "cable select" IDE cable but don't set the jumpers on the drives to cable select (this could be why your CD drive doesn't show).

Since you are using 2 different cables, that means you have 2 IDE controllers on the motherboard.  Normally the boot disk needs to be the master disk on the first controller, usually denoted as IDE0.  The CD drive, being on it's own cable, should be set to master as well.  You also need to check the BIOS setup to be sure the 2nd IDE controller (usually denoted as IDE1) is enabled.

You should also make sure your CD drive is a true IDE drive.  If this is an old drive from an old PC, it's possible it's one of the old old drives that actually interfaced to one of the old old old controller cards.

Download and look through the motherboard manual - you'll need it to get started.

---

### Post by gerrman97 on 2012-12-31
Motherboard is super old like windows 3.1 old. It barely works with windows 98. Also it WONT boot into bios so i can change my boot order. Not gonna be able to change anything. I will work on it later. I will upload some pics of it on facebook. If ufeel like it look me up. Grant Lee. My pic is a black background. Has word but i cant remember what they r.

---

### Post by squakie on 2012-12-31
I hate to be the bearer of bad news, but if your motherboard is that old, I wouldn't count on getting anywhere.  The board itself is going to be extremely slow, no matter what the processor (and you'll be very limited there as well).  You probably can't put much memory in it.  It may even be made for the old MFM and RFM drives, not true IDE.  You would be much better off buying one that is new to you - there are lots of much much better motherboards with cpu, heatsink and fan for very low prices.  People have been dumping their old ones (but MUCH newer than yours) for very low prices for quite a while.  I would imagine that now that it's after the holiday there may be even more.

---

### Post by gerrman97 on 2013-03-30
@squakie: thanks for your help. that pc has actually burnt itself out, running the bare minimum. I have recieved a new(er) desktop, which i customized and all that good stuff. i moved all the components into a bigger( but older) case for more room, had to hot glue some parts in place, due to lack of mounts. i am actually able to run win7 on this, and it flies. 2.4 ghz processor and 2 gigs ram work wonderfully. though, no cd/dvd device. will buy one soon. this one uses SATA. i was excited to dig into it. i also got a new(er) laptop and it is running Ubuntu 12.04.2 instead of windows 7. (had to format hdd, due to virus infection:( )

---

