---
title: "Upper/Lower case mixed up after 20 mins on Sony Vaio"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by Martin_Whittle on 2014-01-30
Hi - 
I already posted Garbled acps/lowercase on Sony Vaio VGN-FS485B on Ask Ubuntu but didn't get a useful reply yet.   I also put something on Hardware, but since I am a newbie at Ubuntu I'm having a go here too.  Also, since then I've tried installing Mint - which gave similar behaviour - and now come back to Ubuntu.  A reinstall hasn't helped: it is still doing the same thing.  After about 20-30 minutes of browsing, say, lower case starts to become upper case and a string of lower case a's becomes AAaaaaAAAAaaaAA etc.  Caps lock sometimes reverses it, but numbers can be completely inaccessible - I just get !"£$%^&*().  Firefox also starts throwing a new window instead of a tab - even though the preferences - are correctly chosen.  (This appears to be a symptom of the same underlying problem - but a moderator at ask Ubuntu didn't like getting what they saw as two unrelated questions in one post)

My machine never had this problem running XP, which I have sought to escape before April, so I replaced it rather than get a dual boot - rash maybe, but maybe wise as well.  

So another reason for posting again is that I think I am getting closer to a answer.  My guess is that something is overheating ( although Psensor didn't give any exceptional temperatures, ~60 max,  - it may not be measuring the temperature of the problem component) and my further guess - after reading loads of threads - is that I might need to install a proprietry driver (maybe for the graphics adapter) or two.  So, the original configuration is given as:

[h=2]Specifications[/h]Sony Vaio VGN-FS485B
:: Processor
 Intel Pentium M 740 1.73 GHz 
:: Memory
512 MB, DDR2, PC4300, max. 2048MB, 1x512MB (1 Slot free)
:: Graphics adapter
[Intel Graphics Media Accelerator (GMA) 900]("http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-900.2178.0.html")
:: Display
15.4 inch 16:10, 1280x800 pixel, WXGA X-black LC-display with one light
:: Harddisk
80 GB - 4200 rpm, 80 GB 4200 rpm Toshiba MK8025GAS 80GB ATA/ATAPI-6: 80GB, 4200rpm
:: Connections
2 USB 2.0, Firewire IEE 1394 4-Pin, earphones, MemoryStick (Pro), VGA exit (analogue)
:: Size
height x width x depth (in mm): 25.4 x 364 x 264.5
:: Weight
2.675 kg
:: Battery
, 4400 mAh lithium-ions
 					:: Price
1070 Euro
:: Additional features
Intel  915GM/GMS / ICH6-M, HDD: 80GB, 4200rpm, Toshiba MK8025GAS 80GB  ATA/ATAPI-6, Intel High Definition Audio, Sony DVD RW DW-Q58A, 

Some time ago I added another 1GB of Ram so it now has 2GB.

Anyone got any idea how I might save my old but much-loved machine?  And if it involves a driver, how do I get and install it?

Many thanks


[h=1][/h]

---

### Post by Mark Phelps on 2014-01-30
> My machine never had this problem running XP, which I have sought to escape before April,

Understand your concern about continuing with XP ...

I had a similar machine in a Fujitsu laptop and upgraded it from XP to Vista, then  to Win7 -- and was quite happy with it.

The symptoms you're describing are consistent with overheating, and in the case of that PC, if it was not overheating in XP, you should seriously consider upgrading it to Win7 -- as that should also work without overheating.  And Win7 uses an Intel 915 driver that works very well -- seeing as how MS carries over XP-era drivers into Win7.

Sorry, but unless someone has a specific fix for that machine, it looks like Windows is going to be a better choice to keep using it.

---

### Post by Bashing-om on 2014-01-30
Martin_Whittle; Hi !

Might have a greater/better experience with Lubuntu.
 A guide for getting computers with older Pentium M processors to work with the latest Lubuntu;
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

With 2 gigs of ram installed, Lubuntu will scream on that hardware.
Not to say a good general cleaning would not help the situation.

[INDENT][INDENT]where there are solutions,
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mörgæs on 2014-01-31
Thanks for referring to my guide, but the 740 is one of the later Pentium M's (a Dothan) so it supports PAE and is able to run any 32 bit Buntu without modifications. Agree that Lubuntu 13.10 would be a good choice.

Did you try an external keyboard?

---

### Post by Martin_Whittle on 2014-02-01
Thanks for replies so far: yes I did try an external keyboard - it suffered from the exact same symptoms, so not a keyboard problem.  I agree that a good clean would be a ggod idea but haven't tried that yet, mainly because I'm scared of a screw in the middle and to the right of the bottom cover that has an arrow pointing at it.  Dunno what that means; maybe something critical and irreversible would fall off if I took it out.  Anyone know?  Perhaps I'll get a can of compressed air and remove all other screws first.  Somebody else suggested Lubuntu - I actually tried Xubuntu but couldn't get it to work when I tried.  Maybe the installation went wrong and I will try again with Lubuntu 13.10.  If all else fails I'll shell out for Windows 7 - but for one thing I've been concerned that the machine spec will not really be up to it.
Thanks again - much appreciated.

---

### Post by Bashing-om on 2014-02-01
Martin_Whittle; Hey ,

I found a source for the manual for your machine, maybe of some help ?
[http://www.givemyfile.net/smanuals/notebooks/sony/vgn-fs485b.html](http://www.givemyfile.net/smanuals/notebooks/sony/vgn-fs485b.html)
[http://laptoprepair.ca/news/10900.html](http://laptoprepair.ca/news/10900.html)
when all else fails (??),
[INDENT][INDENT]read the instructions[/INDENT][/INDENT]

---

### Post by mörgæs on 2014-02-01
The screws with arrows pointing at are the ones which can (and have to) be removed in order to open the housing. 

Best is to open and remove as much dirt as possiblly first. After that compressed air is fine, but only when you blow the opposite way of the normal air stream.

---

### Post by Martin_Whittle on 2014-02-02
Hi  -  I think the problem is now SOLVED by installing lubuntu... I may yet have to eat humble pie but its been running a slide show and videos all afternoon - so its warm, but the caps problem has not yet returned.  Thanks particularly to Bashing-om as well as my colleague Matt who suggested is as a solution.  As Bashing-om suggested lubuntu is pretty quick on the sony and it should do the trick for me.  It will be interesting to survey all the software available. 

But thanks are due to everyone who replied and especially for also for the recent useful tips about opening the housing and cleaning (it will be done anyway) and also (Bashing-om again)for the manual.  Your help is much appreciated.

---

### Post by mörgæs on 2014-02-03
Good, please mark the thread 'solved'.

---

### Post by Martin_Whittle on 2014-02-04
Hi - unfortunately I did speak too soon - the problem re-appeared.  I note also that the keyboard is showing as "US" and I'm sure I opted for the uK version when installing.  I don't think the US layout should giive a caps problem but I followed a thread for changing keyboard layouts and looked at the appropriate file and it appeared set to GB.   

So now I've tried Ubuntu(twice), Mint and Lubuntu.  Interestingly they all looked stable to start with but later developed problems.  I'll have to give the machine a clean and see if that helps but I do wonder if it has anything to do with updates that get installed a bit later than the initial setup.   I might try reinstalling Lubuntu and watch more closely what happens.  I'll keep you posted how this goes - but it's a very awkward problem.  Maybe I should try Debian version (though they look less user-friendly to install) ?  I was really hoping to escape Windows; I'll hang in there for a while, but if all else fails I may have to reluctantly get a copy of 7 to try.

---

### Post by mörgæs on 2014-02-05
Distrohopping is usually a good thing, but in this case I think you should focus on hardware, especially cleaning the cooling system.

---

