---
title: "Best Current way of getting Oneiric?"
date: 2011-05-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by RJ12 on 2011-05-30
What is the best current way of getting Oneiric? Is it better to install Natty then use the sources and upgrade, or install a daily build?

---

### Post by zika on 2011-05-30
> **RJ12 said:**
> What is the best current way of getting Oneiric? Is it better to install Natty then use the sources and upgrade, or install a daily build?Third way: Terminal:**update-manager -d**...
Beware: [http://ubuntuforums.org/showthread.php?t=1769822](http://ubuntuforums.org/showthread.php?t=1769822)

---

### Post by sparker256 on 2011-05-30
> **RJ12 said:**
> What is the best current way of getting Oneiric? Is it better to install Natty then use the sources and upgrade, or install a daily build?
The advantage of daily live build is you can try it before installing. It is how I have installed my 32 and 64 bit installs.

Bill

---

### Post by donniezazen on 2011-05-30
> **zika said:**
> Third way: Terminal:**update-manager -d**...
Beware: [http://ubuntuforums.org/showthread.php?t=1769822](http://ubuntuforums.org/showthread.php?t=1769822)

Upgrade gave me lots of error like doc-base broken, etc and aborted itself without cleaning. I have a working system but Unity and theme are not fully functional and i also have /run problem being discussed in other thread.

I might go with ISO.

---

### Post by Squonk07 on 2011-05-30
Alternately, if you're not dying to get on board right away, the first alpha is due on June 2nd. Granted it's just a snapshot in time (like the dailies), but I imagine some effort will be put into making sure it works before going bravely forward into more breakage/progress. The dailies...not so much.

---

### Post by sisco311 on 2011-05-30
I usually use debootstrap... What do you think about it?

---

### Post by jerrylamos on 2011-05-31
> **RJ12 said:**
> What is the best current way of getting Oneiric? Is it better to install Natty then use the sources and upgrade, or install a daily build?

I've been running pre-Alpha, Alpha, Beta, RC, ... since Dapper Drake.  Sooner or later the "dread update" will crash the installation irreparably.

So I frequently do a re-install from daily build.  

That's been working pretty well until Natty Narwhal where for almost 2 months daily build "install" was broken on my test pc's, but I did have Alpha's updated that worked until they eventually got around to fixing "install" which kept hanging where it was trying to determine the partition structure.

Usually daily builds won't fit on a CD so that means install from a USB stick or USB hard drive or a second hard drive.  Lately I've been booting the .iso directly which is a good bit easier than going through the "make startup disk".  Put the .iso someplace easy like /boot/iso folder, do a "zsync" to refresh to the latest daily build, then reboot selecting the .iso from a 40_custom entry.  See the oneiric forums for how.

I'm learning a lot about linux by coping with various breakages, plus reporting bugs to development.

Good luck, 

Jerry

---

### Post by seeker5528 on 2011-06-02
> **soham_1207 said:**
> Upgrade gave me lots of error like doc-base broken, etc and aborted itself without cleaning. I have a working system but Unity and theme are not fully functional and i also have /run problem being discussed in other thread.

I wouldn't suggest 'update-manager -d' at this point, I'm a little surprised it would even give you the option before the first alpha, but then again I did see some comments about that being soon. 

Don't know what's up with that '/run/' thing, it hasn't been created on any of my machines. 

Due to a hard drive starting to fail and having an installation on another system that ran out of space a while back that I copied to another hard drive and got working on the system where the hard drive was failing, I started with Lucid (I said it was a while back right) and went from Lucid --> Maverick --> Natty --> Oneiric' all by editing my sources.list then using Synaptic to pull stuff in. 

I removed a bunch of stuff first so I wouldn't have so much to upgrade through the multiple versions of Ubuntu, Mythbuntu stuff, open office, etc.

Grub was a little bit of a PITA, but once I got the other stuff sorted purging grub and re-installing sorted that out. 

What was on there at the start was mostly all Kubuntu/Mythbuntu stuff so once I got to Natty I pulled in metacity and unity and some of the gnome stuff that would have been part of the stock Ubuntu install. 

I don't have most of the Oneric stuff on that machine yet, I just pulled in some of the low hanging fruit so far, base-files, gcc, cron, and some of the other base stuff that mostly were small and didn't require pulling in a lot of other stuff. 

In Synaptic if you go to 'Settings --> preferences --> general' and make sure 'System upgrade:' is set to 'Default upgrade' which is equivalent to 'apt-get safe-upgrade', then you can use the 'Mark All Upgrades' button on the toolbar to mark all the safe upgrades and do those first. 

After that you can individually select things, cancel them if the changes look to drastic. Once you get some stuff selected that clears the way for you to hit the 'Mark All Upgrades' button again and have it find another group of packages that it will consider safe choices. 

At some points it may be easier to go through the list of 'installed (local or obsolete)' packages choosing things to remove and see what that triggers, you want to get rid of most if not all of the obsolete stuff eventually any way.

The key is to always watch what will be removed and cancel if you don't like it.

Later, Seeker

---

### Post by jerrylamos on 2011-06-02
Oneiric Ocelot Alpha is running for me now:

[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha1](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha1)

I'm using Live mode.  Install with early flaky Alpha's can bork hard drives.....

Enjoy,  Jerry

BTW I use zsync which is good for keeping your .iso current without doing a whole .iso download once you have a copy.

---

### Post by donniezazen on 2011-06-02
How does debootstrap works? Is it like wubi installed on Ubuntu system?

---

### Post by sisco311 on 2011-06-03
> **soham_1207 said:**
> How does debootstrap works? Is it like wubi installed on Ubuntu system?

It downloads and extracts the essential packages needed for a minimal chroot environment in a directory. Then you can chroot into the directory and install the rest of the system (grub, the kernel, a desktop environment...).

The community documentation is a little bit outdated, but still useful:
[uhelp]community/Installation/FromLinux#Without CD[/uhelp]

I'm working on a HOWTO, but it's far from being finished... :)

---

