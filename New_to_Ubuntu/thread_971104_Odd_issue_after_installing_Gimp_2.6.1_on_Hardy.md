---
title: "Odd issue after installing Gimp 2.6.1 on Hardy"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Katerine on 2008-11-04
Hi,

I have Ubuntu Hardy running on my new Asus 1000HA. I've been playing with Ubuntu for about a week. Before that, I had 0 experience with Ubuntu, and very little with Linux. I do have some experience with Gimp 2.6.1 on Windows, though. Nothing that would tell me what's wrong here, though. And Google returns nothing. Please help...

I've been trying to install Gimp 2.6.1 using the 5 files in getdeb. There are 5, btw, not 6 - users in a different thread that I can no longer find have referred to their being 6...

I've tried several times. Each time, the same issue occurs.

I download the files. I install the files in "babl (1st) - gegl (2nd) - libgimp (3rd) - gimp-data (4th) - gimp (5th)" order. I have done this both through the package installation manager (not Synaptic - the other one) and through "sudo dpkg -i" in the command line. (I uninstall everything completely in Synaptic after each failed attempt).

Each time, the installation goes through completely without a hitch.

Each time, I open Gimp through the menu. Each time, it loads everything, and opens completely without a hitch. I have done this from the command line as well, and there are no complaints.

Each time, everything looks great... except...

The "Layers/Channels/Paths/Undo" dock doesn't work. At all. It's *there*, but it doesn't work. If I create a new image, nothing appears in the layers tab. If I add a new layer, nothing appears in the layers tab. If I paint something, nothing appears in the undo tab. If I try to open a different tab (say, "Navigation,") in the same dock... that tab works. But if I try to remove one of the malfunctioning tabs and then add them again, the docks won't open.

I have reinstalled the version from the standard Ubuntu repository (2.4.5) a few times (after completely removing 2.6.1), and 2.4.5 seems to work just fine. Except once, my desktop went away. But only until I restarted the OS. I could just give up and reinstall 2.4.5 for good... but I really want 2.6.1. I *like* 2.6.1...

Possible culprits:
The first time I tried this, I missed the instruction to uninstall the old version of Gimp first. I then tried to uninstall it afterwards, and completely uninstalled the new version of Gimp, and started over.

It's not the download, unless it's corrupted on the server - I downloaded all of the deb's twice.

It's not the installation order, unless everyone's instructions are wrong.

Please help...

---

### Post by keplerspeed on 2008-11-04
Gimp 2.6.1 is the the repositories, but you may have to enable universe or restricted sources, system/administration/software sources.

Cheers

---

### Post by gali98 on 2008-11-04
Well, is there any reason not to move to intrepid? (it has 2.6 default)
Also where did you download the packages. I used the ones from Getdeb
[www.getdeb.net](www.getdeb.net)
and they worked great on Hardy...
Kory

---

### Post by Katerine on 2008-11-04
Thanks for the replies. :) Still having the same issues though.

> **keplerspeed said:**
> Gimp 2.6.1 is the the repositories, but you may have to enable universe or restricted sources, system/administration/software sources.

Not... really...

These are the options I have in the Software Sources:
"Canonical" etc. is checked.
"Community-maintained" etc. is checked.
"Proprietary" etc. is checked.
"Software restricted" etc. is checked.
"Source Code" is unchecked.
Download from "Server for United States."
Installable from CD-Rom - "CD-Rom with Ubuntu 8.04 'Hardy Heron'" is unchecked.

Third-Party Software - these are the checked ones:
apt.wicd.net hardy extras
ppa.launchpad.net/mishd/ubuntu hardy main
ppa.launchpad.net/mishd/ubuntu hardy main (Source Code)
[www.array.org/ubuntu](www.array.org/ubuntu) hardy eeepc

Updates tab:
Important Security Updates and Recommended Updates are checked. Pre-released Updates and Unsupported updates are unchecked. I'm really hesitant to check either of them, as I would wind up with far more updates than just Gimp, and most of those would probably be unwanted.

Show new distribution releases = Normal releases.

I've reloaded the package info twice, just to be sure, and the latest version is still 2.4.5-1ubuntu2.

I also have a sneaking suspicion that, since the installation went without a hitch and opening the program goes without a hitch, that the problem isn't with the install itself, but with some gimp setting somewhere... and that setting is not getting removed even when I do "Mark for Complete Removal." So the first thing I'd like to know is, how do I do a removal of Gimp that's *truly* complete?

> **gali98 said:**
> Well, is there any reason not to move to intrepid? (it has 2.6 default)
Also where did you download the packages. I used the ones from Getdeb
[www.getdeb.net](www.getdeb.net)
and they worked great on Hardy...
Kory

Thanks. :) That... *is* where I got the install files... :(

Can't move to Intrepid yet, because Ubuntu EEE Intrepid isn't out yet, and I'm not even remotely familiar enough with Linux yet to try to do an installation that's not already configured for the EEE... :lolflag:

---

### Post by gali98 on 2008-11-04
Oh.....
Do you like the EEE? I want one!

Anyway, I suggest you go on Ubuntu packages (just type that in the address bar of firefox)
and download the gimp packages for intrepid there and try to install them.
Kory

---

