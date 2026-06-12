---
title: "hplip vs cupsys"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by brucenduane on 2008-10-17
I am using Ubuntu 7.10, 8.04 and Ubuntu Studio 8.04 on several computers here at the office.  We have only an HP PhotoSmart C5200 printer here.
We connect to the printer by plugging in its USB cable to the computer
that needs to print something.

Question:  Can we remove cupsys and all the cups associated packages
and only use hplip and its associated packages?  I don't want to break
Ubuntu.

---

### Post by saj0577 on 2008-10-17
I am no expert and dont quote me on this but a I am sure i recall reading that hplip relies on cups.

I know its not much help, but I would not suggest uninstalling it untill you find out otherwise. If i get some time I will do some research into it for you.{subscribed}

Saj

---

### Post by kansasnoob on 2008-10-17
> Question: Can we remove cupsys and all the cups associated packages
and only use hplip and its associated packages?

No. Hplip depends on cupsys.

---

### Post by oldsoundguy on 2008-10-18
I have an issue involving these same two programs.
I am running a multi platform/multi computer home network that has one it (among other printers) 4 HP printers of various configurations.
I can PRINT to every one of them from every computer in the network.  NO issue there.
The issue is the hplip utility.
I want it to be able to monitor the conditions (ink, paper, yada yada) from my MAIN Ubuntu computer.  
The program itself is installed, but when I go to do the set up, it sees NO printers .. but cups sees them all (including the non HP printers).  I cut and paste the URI of the HP printers into the set up box and I get a "can't be found" message.
Excuse me?  I can print to them from the box, cups has a URI,  why can't hplip find them?

This is just an annoyance and not a world shaking threat to my every day usage!! Just would like to get that feature enabled for convenience sake.

---

### Post by kansasnoob on 2008-10-18
I'm not sure if this will be helpful or not, but the version of HPLIP that came with Intrepid didn't work with my HP printer (odd because it worked out-of-box in Gutsy and Hardy) so I decided to try installing the current driver from the HPLIP website. It worked!

But the HPLIP toolbox was in Accessories rather than Sys > Pref and when I clicked on it there was no gui. So I booted into Hardy and checked some dependencies. After adding all of this:

> libqt4-assistant
libqt4-help
libqt4-svg
libqt4-test
libqt4-webkit
libqt4-xmlpatterns
python-qt3
python-qt4
python-qt4-common
python-reportlab
python-sip4
ttf-dustin

I had a perfect HPLIP gui!
Ink levels and all.

---

### Post by oldsoundguy on 2008-10-18
should have mentioned I am running Gutsy on three of the machines and Mint on another along with XP on two others.

---

### Post by kansasnoob on 2008-10-18
> **oldsoundguy said:**
> should have mentioned I am running Gutsy on three of the machines and Mint on another along with XP on two others.

Do you have a HPLIP gui in System > Pref?

---

### Post by oldsoundguy on 2008-10-18
yes

Once again.  I open the GUI and try and do the set up.  Run scan and it sees no printers.  
So, I open cups and copy and paste the URI(s) listed there into the box that asks for the URI One at a time) and it still can't find the printer(s).

BUT I can take a document from OO and print it to any of the printers on the network.

second edit:
In thinking .. each of the HP printers has it's own menu screen and program that monitors the status of the units.  Could it be that hplip can not bypass that to do a screen display?  (never did have a screen display in Windows other than paper problems when they occurred.)

---

### Post by kansasnoob on 2008-10-18
Well my thought is to check the list of dependencies I mentioned (I don't think it would matter what version you're running) and see if anything is missing.

I don't think you'd wreck anything if you're using Synaptic, just watch what may be removed or added for each item you "tick" for installation. That's when I break out my notebook and scribble down everything I'm doing so I can easily revert.

---

### Post by oldsoundguy on 2008-10-18
none of those library dependencies are listed in Synaptic in Gutsy, so I did not bother to check for the pythons.  As to the true type, already have the true type loaded for my OO.

And the notebook (or a note pad) is a VERY handy thing to use when installing anything.  There was a boatload of stuff added when I installed GNUCash recently .. apparently nothing got broken.

This printer thing is not all that important, just that two of them are in other rooms and it would be nice to have a monitor working on each of them when I send something that way, rather than getting up and walking across the entire place to make sure everything is kosher!! LOL (I do get a "failed" message if I get a paper jam or if I forgot to turn the power on for them .. but that is it right now!)

---

### Post by gjoellee on 2008-10-18
CUPS does not work with as many HP printers as HPLIP does...

---

### Post by oldsoundguy on 2008-10-18
Know that .. but all of the HP printers I have DO work with cups.  They are all installed and WORKING right now.  This issue is not whether they work or not, but with the ability to get the HP utility to actually SEE them so that they can be monitored on screen at the main Ubuntu computer (the one that catches the lion's share of the work here.)  It is just a convenience that I would like to have because it is an "advertised" feature.  I will not die tomorrow if I can't get it to function as advertised simply because the work can continue to get done without the feature(s). (I may die tomorrow because I have a re-manufactured heart, but that is another story!! LOL)

---

