---
title: "Random freezing of different apps"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Sydius on 2008-07-10
I've installed Ubuntu on three (very different) laptops and two (also very different) desktops.  On all these systems, in addition to my coworker's system (another desktop running Ubuntu), the system kind of freezes after a while.

I can still have conversations in Pidgin, but all shells freeze (and go dark gray), and if I open a new shell, it never loads the GUI properly and never becomes usable.  Also, if I try to shut down the system, Gnome seems to stop responding.  I can continue to talk in Pidgin and do a few other things (I can't remember exactly what right now), but the system effectively becomes unusable until I hard boot it.

This has happened more than once on all of the systems I have installed Ubuntu (8.04), and all updates have been installed (and it just happened again on my desktop).  It seems to happen most often when I leave it running for several days, but it has also happened within minutes of turning it on after a fresh boot.

I don't know what to look for, as I don't know what program is causing this.  My only guess is that it is Gnome, but I really don't know.

Anyone else having this problem?  I'm not running anything terribly unusual, either... just Pidgin, gVim, and shells--sometimes Evolution Mail (but only on one of the systems).

---

### Post by dracayr on 2008-07-10
six different systems and you suspect gnome? not very likely...

How much RAM do these computers have? how much swap? If they have enough of both, I can only suspect irregular power supply...

EDIT: do you have desktop effects enabled? try disabling them

dracayr

---

### Post by Sydius on 2008-07-10
One desktop is a 64-bit system (with the 64 bit version of Ubuntu) with 4 GB of RAM on a UPS battery system.  The other desktop has less memory (I don't know how much, how do I tell?), is not on a UPS, but is in a different building (my workplace), along with my coworker's machine (which, I was mistaken to say is a desktop--is actually a new Dell laptop, I don't know the specs).  My three laptops and my coworker's are all very different (different brands, different architectures (one is 32-bit), etc.).  I manually set the swap on one of the laptops to 4 GB (it has 2 GB of RAM), but the others I did the automatic do-it-for-you thing, where it chose how to partition the system.  Of note is that all systems dual-boot with XP (64-bit XP Pro on two, 32-bit XP Pro on the the rest).

---

### Post by Sydius on 2008-07-10
> **dracayr said:**
> EDIT: do you have desktop effects enabled? try disabling them

Yes, all systems have this enabled.  I will disable it and see if that helps, thanks.

---

### Post by Sydius on 2008-07-11
I disabled all effects by going to System->Preferences->Appearance, but it just froze again.  Firefox and Pidgin are still working (it's doing the "frozen" thing right now), and this time shells are still working, but the Archive Manager and system settings things (like the Appearance window above) and gVim do not load (they start up, but quickly "stop responding" and never draw the GUI properly).

System monitor works, and I'm using 29% of 1.9GB of RAM, 0% swap, and 5% CPU. :confused:

Also, clicking the button in the top-right to go to the shutdown menu did nothing (didn't even try to load anything).  I had to hard boot it.

---

### Post by aktiwers on 2008-07-11
What other apps are freezing? Maybe you could run one from Terminal and wait for it too freeze. Then we could get the error. Maybe you are missing some libs or something.. ?

---

### Post by Sydius on 2008-07-11
> **aktiwers said:**
> What other apps are freezing? Maybe you could run one from Terminal and wait for it too freeze. Then we could get the error. Maybe you are missing some libs or something.. ?

I will try that, but I do generally run gVim from the terminal, and when it freezes, there hasn't been any errors there.  Quite often, I cannot even open a new terminal once this happens (it loads the window, but never finishes displaying the interface and won't let me type into it).

What confuses me most is that I don't think I'm doing anything unusual on these machines, and they're all having the problem, and they all have wildly different hardware.  My work desktop, by far, has the problem the most (maybe once every other day), but I also use it the most.  But I do the least on it... gVim, ssh, sshfs, scp, Pidgin, Evolution mail, and Firefox 3.

---

### Post by Sydius on 2008-07-15
I'm not entirely sure if I'm on to something, but this seems to happen when I am talking in Pidgin... though, Pidgin does not freeze.  It crashes sometimes, but I think that might be unrelated.

---

### Post by Sydius on 2008-07-17
Is it possible that a single user application could cause other things to lock up like this? Like, say I have an app with a bug that is doing something bad, could it theoretically be causing other programs (but not all) to become unresponsive (like Gnome and gVim)?

---

### Post by Sydius on 2008-07-29
Either updates fixed it, or it may be a Skype plugin for Pidgin that I have been using (and subsequently stopped using, as a test).  Hasn't happened in a while.

---

### Post by gjoellee on 2008-07-29
maybe kernel 2.6.26-20.38 fixed it....

---

### Post by stap on 2008-08-06
Hi!

I have exactly the same problem. I also have the impression that it is caused by pidgin, but that's really just my impression.
Well, I have installed all update, too, but the problem still exists... Did you install kernel 2.6.26-20.38 manually? I don't think that it is in any of the official Ubuntu repositories...

Andreas

---

### Post by Sydius on 2008-08-06
> **stap said:**
> Hi!

I have exactly the same problem. I also have the impression that it is caused by pidgin, but that's really just my impression.
Well, I have installed all update, too, but the problem still exists... Did you install kernel 2.6.26-20.38 manually? I don't think that it is in any of the official Ubuntu repositories...

Andreas

No, I just did the normal updates.  I don't know what fixed it for me... it just stopped happening after a while.  Maybe it's still an issue, and I just haven't done the right combination of key presses to make it spring back to life yet.

You aren't using the Skype plugin for Pidgin, by chance? I thought that might be the problem for me, since it hasn't happened since I stopped using Skype with Pidgin.  Are you using any Pidgin plugins?

---

### Post by Vorian Grey on 2008-08-06
If you find a fix for this you need to market it because a lot of people would like to have the answer.

---

### Post by Sydius on 2008-08-06
At least now I know it's not just me that was having the issue.  I think we should find something in common with all of us that are having the issue.

Is everyone running Pidgin?

---

