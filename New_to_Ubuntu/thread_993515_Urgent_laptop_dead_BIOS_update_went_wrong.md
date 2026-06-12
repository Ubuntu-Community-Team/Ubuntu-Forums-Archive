---
title: "Urgent: laptop dead BIOS update went wrong"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by dileepdinesh on 2008-11-25
Hi guys,
    I have a dell inspiron 1420. I was having problems with fan.
I read in some threads here that i should upgrade my bios. I tried a update from dell support site. and now nothing boots up when i switch on the laptop, when i press the power button , it just stays in a blank screen. and goes off after 4 or 5 secs, help is needed urgently. thanx

---

### Post by diablo75 on 2008-11-25
This sounds very bad.

How exactly did the BIOS update work?  Did you have to create a bootable floppy/CD?  Or was there some utility that you're supposed to run in Windows?  Or some other method?

---

### Post by dileepdinesh on 2008-11-25
I read it here in the threads,it said to download a file called bios.hdr from dell site and run it as root,i think it went successfully and showed that package was installed successfully,but when i press power button just the light flashes for 4 or 5 sec and goes dead,,,,the screen is just dead.

---

### Post by DGortze380 on 2008-11-25
I hate to be the bearer of bad news but if you've botched a BIOS upgrade your motherboard is now a paperweight.

The BIOS are stored in CMOS and perform all the very first, very basic start up functions for you motherboard. There's no way to start the board to fix the BIOS... short of soldering on a new chip.

---

### Post by diablo75 on 2008-11-25
Can you provide a link to the thread where you were instructed to do this?

---

### Post by dileepdinesh on 2008-11-25
After the completion of installation,,it showed that i should set up some CMOS bits,will that do any help? I didnt do any? will that do any help

---

### Post by gpsmikey on 2008-11-25
> **DGortze380 said:**
> I hate to be the bearer of bad news but if you've botched a BIOS upgrade your motherboard is now a paperweight.

The BIOS are stored in CMOS and perform all the very first, very basic start up functions for you motherboard. There's no way to start the board to fix the BIOS... short of soldering on a new chip.


Actually, the BIOS is stored in FLASH memory - the CMOS memory is a small segment of special battery backed up memory that holds various settings for the BIOS etc, but the BIOS itself is in FLASH memory and is upgraded to a new version by typically running a utility in main memory that erases the flash memory then programs it with the new version of the BIOS.  If that process is aborted, you don't have a valid BIOS and as said, often no way to recover.  You MAY have some options - check with Dell support and see if they have answers (also Google for ideas).  Sometimes, on desktop motherboards, you can buy a new pre-programmed BIOS chip if it is socketed and replace it.  Laptops MAY have that feature, I have not looked, but it is another idea to check out.  Typically, a corrupted flash is bad news, but there may be some recovery methods.  Worth talking to Dell and Google.

I notice that the Dell site shows that A09 looks like the latest BIOS.
These guys may be able to help you too (they indicate that they have a problem with DELL, but it sounds like they can work with you on it)
[http://www.biosman.com/replacement.htm](http://www.biosman.com/replacement.htm) (never used them myself)

I see there are also a number of articles out there on new BIOS versions for fan issues causing Nvidia cards to overheat.  One of the articles is here:
[http://www.gizmodo.com.au/2008/07/dell_issues_bios_update_to_keep_nvidia_geforce_cards_from_frying-2.html](http://www.gizmodo.com.au/2008/07/dell_issues_bios_update_to_keep_nvidia_geforce_cards_from_frying-2.html)


mikey

---

### Post by diablo75 on 2008-11-25
> **dileepdinesh said:**
> After the completion of installation,,it showed that i should set up some CMOS bits,will that do any help? I didnt do any? will that do any help

I'm not sure what it means by "CMOS bits"...

Can you post a link to the page/forum that instructed you to do what you did?

---

