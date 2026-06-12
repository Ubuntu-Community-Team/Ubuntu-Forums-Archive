---
title: "changing low screen resolution"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by dynacrylic on 2008-11-01
I just upgraded to 8.10, how do I change my resolution to something other than 800x600?

I tried adding the restricted drivers, but it seems the nvidia software and drivers are not working properly.

Can someone please direct me to a solution for this.

thanks in advance

---

### Post by acm321 on 2008-11-02
Did you go to System>Preferences>Screen Resolution or something else?

---

### Post by mingle on 2008-11-02
Hi,

I have a similar issue, as do a few others it seems!

Previously (7.10) it was possible to get around missing/not installed GFX drivers using the quick and handy displayconfig-gtk utility, however the developers (in their wisdom!) appear to have left this out of 8.10 and not provided (as far as I can see) an alternative...

The gnome-display-properties util is of no help, since it is just for changing display resolutions that are currently available. Our issue is that the correct GFX drivers are not available/have not been installed by the installer...

Hopefully someone can help us out or it's going to be back to XP (again!) for me, as I'm stuck at 800x600 too!

Cheers,

Mike.

---

### Post by bscbrit on 2008-11-02
When you try to change the screen resolution, does it offer any other setting than 800x600?  If so, try selecting a different one and see if that helps.  If your problem, however, is that the maximum resolution offered is only 800x600 then you are experiencing the same problem as others, myself included.  The software behind xserver has changed fundamentally and, where it was once a case of changing the odd line in xorg.conf or, better still, running displayconfig-gtk, neither of these options is now possible.  

I had to take a very long route to solve my problem.  Firstly, I had to go back to 8.04.  When I had that working I copied /etc/X11/xorg.conf to a thumb drive.  Next, I reinstalled 8.10 and then, as sudo, copied the xorg.conf onto the new installation.  You might want to wait a little while longer to see if anyone comes up with a more efficient/effective solution.

The new changes seem to please people once they are working correctly, but are causing difficulties for many others who are experiencing problems with no easy or obvious way to resolve them.

---

### Post by bscbrit on 2008-11-02
I've just made a little experiment.  I downloaded guidance-backends and displayconfig-gtk from the Hardy repos and installed them under Intrepid.  This returns the missing displayconfig-gtk which allows me to configure my display again!

HOWEVER - use this at your own risk.  It might cause other problems behind the scenes but, if you haven't got a working computer, that might not be too much of a problem for you.

I stress, USE THIS AT YOUR OWN RISK.  If you don't know how to download the debs from the Hardy repos, please come back and ask.

---

### Post by mingle on 2008-11-02
Hi bscbrit,

Could you please let a relative newbie know how to access and install displayconfig-gtk? I'm willing to take the risk! :-)

Cheers,

Mike

---

### Post by SunnyRabbiera on 2008-11-02
yeh this is why removing the display config tool was a stupid idea.
I dont care if it broke xorg, hey a hapless newbie who has no idea how to work the xorg.conf file can break it just as easy.

---

### Post by bscbrit on 2008-11-02
THIS IS NOT SUPPORTED BY Intrepid - but it worked for me.  USE AT YOUR OWN RISK.

**EDIT - This has only been successful with a small number of people.  I do not recommend it as a first option, but rather as something to try when all else fails. - END EDIT**

First of all, you need to download the packages. Go to the following 2 links.  At the bottom of each page is a link to allow the package to be downloaded.  Make sure that, for guidance-backends you select the correct architecture for your computer.  For displayconfig-gtk there is only one possible download for all architectures. You will have to select a mirror near to you before each download will begin.

[http://packages.ubuntu.com/hardy/admin/displayconfig-gtk](http://packages.ubuntu.com/hardy/admin/displayconfig-gtk)

[http://packages.ubuntu.com/hardy/guidance-backends](http://packages.ubuntu.com/hardy/guidance-backends)

Once downloaded, click on the guidance-backends first, and you should be presented with the option 'Open with GDebi' or something similar.  This program installs the package on your system.  It will ask for your password.

Do the same for the displayconfig-gtk package.

Once they are both successfully installed (< 30 seconds ) open a terminal and type:

gksudo displayconfig-gtk

That's it.  It will let you install your screen from manufacturers' data, or you can simply select a Generic display that has the correct resolution for your screen.

I STRESS, THIS WORKED FOR ME BUT USE AT YOUR OWN RISK.

---

### Post by mingle on 2008-11-04
Hi,

It sort o worked for me - I could call up the correct GFX card and monitor for my setup, but after a reboot I got a warning about graphics configuration and gnome would prompt me to go into a safe GFX mode, which then resulted in a black screen...

No big deal, since I'm currently just mucking around with 8.10 and since I've hit quite a number of glitches related to GFX I might have to stick with 8.04 (which was fine!).

My system uses an Intel 82845G GFX chipset, which is known to be a bit buggy and the cause of most of my initial problems seemed to be compiz, so I removed that. It's still not 100% though - I've now come acros some graphical bugs in Google earth which weren't there on 8.04...

I get the impression that 8.10 was either rushed or not tested very well - I know it's damn hard to cover all possible hardware configs, but it seesm that a lot of people are hitting the same issues as me...

Thanks again for everyone's suggestions and help!

Cheers,

Mike,

---

### Post by bscbrit on 2008-11-04
mingle

Sorry to hear that it didn't solve all of your problems.

I think the devs have, on the whole, done a very good job with Intrepid but I think that they have been concentrating so much on the latest technology and wanting 'bling', that they have forgotten that the vast majority of people just want an OS that works with the average run-of-the-mill hardware and remains stable.  I agree, they cannot check every combination of hardware, but hardware that was working perfectly well under 8.04 is now not working at all.  Linux used to boast that 'older' systems would always work with linux, and often better than it would with a certain other OS.  I suspect that problems are a lot to do with xorg7.4 which is, in software terms, a big departure from what went before.  I think it should have been released rather more slowly than it has i.e. with considerably more testing during the beta phases.  A solid Intrepid using the previous xorg, issued at the same time as an xorg7.4 beta would have fitted the bill.  I know that this is a massive task, but it is important if you put your existing user base before having the latest compiz cubes doing fancy acrobatics. Networking problems and CD drives that won't stay open also feature quite prominently.

Couple this with the fact that, at the same time as xorg7.4, they removed any configuration options from the user has left many people struggling to keep their systems usable.

Still, it would appear that you and I are certainly in the minority - there are many on this thread and elsewhere proclaiming how good Intrepid is for everyone.  Either they are in denial or we are just a handful and statistically insignificant.

---

### Post by mingle on 2008-11-04
Hi again,

Yep... I know quite a few people that run Linux on older HP and Compaq PCs (which are cheap and reliable) and 8.10 is going to cause a few headaches...

It would be good if there was some sort of hardware survey that could capture data on the type/spec of PCs people are using and then direct testing towards those systems.

I used to work in IT Quality and was involved in a lot of software testing, so I know what a task it can be!

Ha! Yeah, the CD drive thing - I've noticed that!

I'm assuming that you mean when the system ejects/opens the drive tray, it shuts it almost immediately?

And here I was thinking my DVD drive was buggered! 

It's almost had me fingers off a couple of times! :-)

Cheers,

Mike.

---

### Post by dynacrylic on 2008-11-07
I resolved this problem by simply re-installing 8.10.

This was the FIRST TIME EVER that I just upgraded (from 7.10 to 8.04). I don't know what caused the problem, but a complete fresh install resolved my problem.

---

### Post by taiter on 2008-11-16
I have been looking for a solution for THREE WEEKS.  I tried EVERY suggestion I came across with the exception of modifying the monitors.xml file.  This worked!!

My problem: Monitor and graphics card not detected, "Detect Displays" in Screen Resolution GUI tool did not function at all, as a new ubuntu user it was nice to find out that xorg.conf is deprecated and my changes there were useless, dpkg xorg-xserver whatever did not work

My hardware: Campaq Presario 1700t, 700MHz 256MB w/ 14.1" TFT display and ATI Rage Mobility M3 graphics card.

I was VERY patient and waited three weeks so I would not get a RTFF, or RTFM demerits.  I am very pleased to have FINALLY found a solution.  THANK YOU THANK YOU THANK YOU!!!:KS:KS:KS:KS:KS

---

### Post by tense eye man on 2008-11-16
hi,

i think i'm having similar issues, with xubuntu 8.10, fresh install and stuck at 800x600 with a black rectangle round the outside of the desktop.  

any chance you can explain your 'monitors' solution in simple terms so i can try it? I'm afraid i' a brand noob, this is the first time i've installed an OS or done anything outside XP, so i will need idiot-proof instructions....:confused:

alternatively, should i try installing xubuntu 8.4 instead? from the replies in this thread it seems the problems are 8.10 related. 

thanks for any help anyone can offer.

---

