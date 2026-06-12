---
title: "Flashing the bios etc."
date: 2012-04-25
forum: New to Ubuntu
---

### Post by rollerworld on 2012-04-25
Hello, I am using Lubuntu 11.10 on a temperamental 32 bit machine.
Would updated drivers help, and how do you install them? Also there must be a program for flashing the bios? Thanks in advance, Rollerworld

---

### Post by Bartender on 2012-04-25
We were just talking about [BIOS]("http://ubuntuforums.org/showthread.php?t=1963160") in another thread.  Your questions seem to be very similar (?)

I don't know anything about Lubuntu, so the following is generic:

For most of the devices, Linux drivers are in the kernel and there's nothing more to be done.  In some cases (mostly video AFAIK) you can use the Hardware Drivers utility to search for drivers.

In other cases (wi-fi) there are some methods for making the Windows drivers work.  I've only messed with that once and the results weren't spectacular. 

I think you'd need to specify what device you're having trouble with before anyone can offer much help.

Flashing the BIOS is a very manufacturer-specific function.  I'd suggest going to your laptop's support pages and looking for BIOS directions.  Some manufacturers are better than others with this sort of thing.  Hewlett Packard is pretty good.  I was able to find directions for updating the BIOS on an 8 year old laptop a few weeks ago. 

If you find some directions but they're confusing, post back here with a link.  I'm sure folks would be willing to lend a hand.

Why is it exactly that you want to flash the BIOS?  In general, flashing the BIOS without a specific reason isn't a great idea.  If the laptop still has the original BIOS, and there have been several revisions, and some of those revisions fixed known problems, sure.

---

### Post by corrytonapple on 2012-04-25
I too, advise against flashing the BIOS unless it brings in bug fixes that are critical to you.  Or, but rarely, brings in new features.
Post your laptop/desktop model and brand, that way we can help you better.

Also, if you do have a reason, like drivers that control your video card or sound or something, as Bartender said, they are built into the kernel.  You can always make your own kernel, and it is a great experience.  But, I would advise against doing this until you have some more Linux experience.

---

### Post by grahammechanical on 2012-04-25
Motherboard makers often supply utilities for flashing the BIOS. My ASUS came with BIOS utilities that work in Windows. But they are useless to me as I do not have Windows. But there is a utility that I could use. It works from a floppy.

It is up to the motherboard maker to supply utilities that flash the BIOS within Linux. I have given up going to the ASUS web site expecting to find Linux equivalents to the Windows utilities provided by ASUS.

This is the situation all over I am sure.

Regards.

---

### Post by jerome1232 on 2012-04-25
I second not flashing your bios unless you know you need the newest version for a critical bug fix or feature. I suggest you describe exactly what you mean by temperamental so we can figure out what the issue is.




With that being said, If all you can find are windows/dos utilities for bios flashing, you can always create a boot disk with freedos on it. Freedos aims to be 100% compatible with msdos and should work in all cases.

---

### Post by Mark Phelps on 2012-04-25
From experience, I can tell you that flashing a BIOS, even when it works, is not necessarily a good thing.  I did that on a Gigabyte board and lost the ability to run my 1600 speed memory at 1600.  Reflashed back to an older BIOS version and got the memory speed back.

So, unless there is a SPECIFIC problem that an upgraded BIOS fixes, you should really leave the BIOS alone.  It's not a miracle cure.

---

### Post by Bartender on 2012-04-25
Whoops, I don't know why I assumed the OP was talking about a laptop.  rollerworld PM'ed me.  It's a 6 year old Acer desktop.

I suggested replacing the CMOS battery for starters.  6 or 7 years is about all you'll get out of those batteries and a dying CMOS battery can certainly cause weird behavior.

Oh, yeah, open the case and look for capacitors that are swelling or leaking.  Millions of bad capacitors were installed on motherboards several years back.  Google 'bad caps' to see some pictures.  I know from personal experience that bad capacitors can cause a PC to act sickly and weird, functioning fine one day, then acting like its brains are spilling out the next.  If you have any bulged, swelling, or leaking capacitors, there's little you can do except begin preparing for the inevitable.  Replacing them requires skills and equipment that most of us do not possess.

---

### Post by corrytonapple on 2012-04-25
Thanks for the update.  What did he say the machine was doing?  Also, remind him to post in the threads and not PM this stuff.  
The iMac G5s, with iSight, were one of the infected machines of the bad capacitor incident.  Those boards you can desolder the capacitors, and it isn't to the extreme difficultly.  You do need electronic skills to do it though.

---

### Post by jerome1232 on 2012-04-25
This could be so many things, I would give a wary eye to the PSU before anything else, they are the first thing to fail in my experience, and can cause "weird" behavior if it's just barely providing enough power.

---

