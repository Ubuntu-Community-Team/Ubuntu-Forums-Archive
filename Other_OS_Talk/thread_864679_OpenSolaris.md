---
title: "OpenSolaris"
date: 2008-07-19
forum: Other OS Talk
---

### Post by Le-Froid on 2008-07-19
I just got my live CD in the mail today, and was extremely confused when running it. I made it boot from the GRUB menu, and after it started I had no Desktop Environment, or an entirely functional shell. When trying to find out how to do any commands to install it onto my computer or get their desktop environment running, nothing would work.

I searched everywhere to find out if there were any tutorials, assuming that the desktop may not come with the live cd. Everywhere I looked said that the CD i ordered came with a GNOME DE, and I had no clue what was happening with my disk. I sort of gave up using it, as of now.

So here's my question for you:
   How many people here have tried OpenSolaris (successfully), and what do you think of it? is it worth trying to get to work?

---

### Post by kk0sse54 on 2008-07-19
I've tried the liveCD before and it was a mostly pleasant experience except for the fact that it didn't recognize half my hardware. At least the default themes and wallpapers looked good :)

---

### Post by cardinals_fan on 2008-07-20
It worked almost flawlessly for me, and I would use it as my main OS if it were 1) faster and 2) had better package management.

---

### Post by DeadSuperHero on 2008-07-20
Same for me, CardinalsFan. I happen to really like it, I just hope they improve the IPS manager by 2008.11 Codename "Jericho".

The artwork and main functionality is there, though.

I personally can't wait to see KDE 4.1's build running on top of it. That makes me really stoked about seeing it...

Also, for some odd reason Flash ran way better on there for me than Linux Flash ever did.

---

### Post by cardinals_fan on 2008-07-20
> **Mr. Psychopath said:**
> Same for me, CardinalsFan. I happen to really like it, I just hope they improve the IPS manager by 2008.11 Codename "Jericho".

The artwork and main functionality is there, though.

I personally can't wait to see KDE 4.1's build running on top of it. That makes me really stoked about seeing it...

Also, for some odd reason Flash ran way better on there for me than Linux Flash ever did.
My main issue is the package management.  The command-line system for handling packages is a total disaster.  I could, after a considerable amount of research, figure out how to install a local package, but I couldn't get pkg, pkgadd, or any of the other package commands to work from the repos.  And the graphical package manager is an unmentionable atrocity.  It has a horrific combination of slowness and bugginess.  Add the tiny repos, and you've got an authentic abomination.  (Think I'm overstating it?  I couldn't get ANY packages installed with that abuse of a GUI.)  It also reported that I had three GIGABYTES worth of updates to download.  What the...?

On the plus side, OpenSolaris was stable, usable, and had awesome support for Java, Flash, NVIDIA drivers, and most of my hardware.  Once they get package management sorted out, I could see switching.

BTW, how does OpenSolaris number drives?  I keep all my data on a separate partition (a lesson learned from chronic distro hopping), and I would need to mount it in order to use Solaris on a day-to-day basis.

---

### Post by 67GTA on 2008-07-20
I really liked the Driver Utility idea. Everything worked except for ethernet. I could have probably gotten it working if I had tried. The one thing that bothers me is the sound of my CD/DVD drive. It sounds like it is going to take flight with the Solaris CD. I think it will be a decent OS once the hardware compatibility gets better.

---

### Post by tact on 2008-07-20
> **Le-Froid said:**
> I just got my live CD in the mail today, and was extremely confused when running it. I made it boot from the GRUB menu, and after it started I had no Desktop Environment, or an entirely functional shell. When trying to find out how to do any commands to install it onto my computer or get their desktop environment running, nothing would work.

I searched everywhere to find out if there were any tutorials, assuming that the desktop may not come with the live cd. Everywhere I looked said that the CD i ordered came with a GNOME DE, and I had no clue what was happening with my disk. I sort of gave up using it, as of now.

So here's my question for you:
   How many people here have tried OpenSolaris (successfully), and what do you think of it? is it worth trying to get to work?

I downloaded the ISO and booted that in a VM (presumably the result would be the same as booting a liveCD).

When you booted up the liveCD did you get to the gnome desktop?  Or did that fail too?

I found that it seemed to sit at a ("unusable") terminal prompt for some time before it kicked into the gnome environment.   I guess there was just a (longish) delay getting x started.

What do you mean you "...made it boot with grub"?   The standard linux grub cannot start opensolaris (or any solaris).  But the solaris grub can start linux installs.

Try booting directly from the liveCD again and go for a coffee when you see the "terminal" screen that seems unusable.  When you come back you should have a familiar GDM login prompt.

If the liveCD works reasonably well with your hardware then only you face the decision whether to install to HDD or not.  

I have not gone that far (installing to HDD).  I very much enjoy using it in a VM but agree with others that it is a bit limited in the packages available and usability of the package manager.  The gnome desktop is very familiar and would make it a fairly easy transition for someone used to gnome on linux.

---

### Post by Le-Froid on 2008-07-20
> **tact said:**
> I downloaded the ISO and booted that in a VM (presumably the result would be the same as booting a liveCD).

When you booted up the liveCD did you get to the gnome desktop?  Or did that fail too?

I found that it seemed to sit at a ("unusable") terminal prompt for some time before it kicked into the gnome environment.   I guess there was just a (longish) delay getting x started.

What do you mean you "...made it boot with grub"?   The standard linux grub cannot start opensolaris (or any solaris).  But the solaris grub can start linux installs.

Try booting directly from the liveCD again and go for a coffee when you see the "terminal" screen that seems unusable.  When you come back you should have a familiar GDM login prompt.

If the liveCD works reasonably well with your hardware then only you face the decision whether to install to HDD or not.  

I have not gone that far (installing to HDD).  I very much enjoy using it in a VM but agree with others that it is a bit limited in the packages available and usability of the package manager.  The gnome desktop is very familiar and would make it a fairly easy transition for someone used to gnome on linux.

I've waited a long time with the liveCD, but when I boot it, the regular version and the text console listed both go to the same shell.

Meh, I'll give it 30 minutes to see if it ever boots to the GNOME desktop

---

### Post by tact on 2008-07-20
Shouldn't take quite THAT long ...  hehehe    Try booting the CD in a totally different PC (different video card) to be sure that the CD is not corrupt.   

If the CD will boot on another machine (different video card) then you will need to suspect that perhaps your video card is not supported in opensolaris' x implementation yet.

It does work on my laptop in a VM (as mentioned previously) but there was a delay between seeing what looked like a terminal screen and actually kicking into X.  It was such a delay that the first few times I booted I...:
-  thought it had hung at that point ...  so restarted.
-  waited longer and thought this was all you get and need to manually start X (not so - failed)
-  waited a bit longer and saw that terminal finally replaced with a GDM prompt,

Even when you get to the GDM prompt on the liveCD (wondering what the heck is the username/password you are supposed to use and why its not auto-logging on)... just wait.  It will eventually logon itself.   

Keep itchy fingers away from the keyboard til you get to a gnome desktop.  hehehe.



Cheers

---

### Post by Sorivenul on 2008-07-20
Love it, love it, love it, despite the default Gnome.  Works like a champ on my Sony VAIO VGN FS-980.

---

### Post by Le-Froid on 2008-07-20
> **tact said:**
> Shouldn't take quite THAT long ...  hehehe    Try booting the CD in a totally different PC (different video card) to be sure that the CD is not corrupt.   

If the CD will boot on another machine (different video card) then you will need to suspect that perhaps your video card is not supported in opensolaris' x implementation yet.

It does work on my laptop in a VM (as mentioned previously) but there was a delay between seeing what looked like a terminal screen and actually kicking into X.  It was such a delay that the first few times I booted I...:
-  thought it had hung at that point ...  so restarted.
-  waited longer and thought this was all you get and need to manually start X (not so - failed)
-  waited a bit longer and saw that terminal finally replaced with a GDM prompt,

Even when you get to the GDM prompt on the liveCD (wondering what the heck is the username/password you are supposed to use and why its not auto-logging on)... just wait.  It will eventually logon itself.   

Keep itchy fingers away from the keyboard til you get to a gnome desktop.  hehehe.



Cheers

Meh, still didn't work

---

### Post by tact on 2008-07-20
Just revisited the opensolaris liveCD in a VM.   The delay wasn't more than a few minutes really.  

Only then realised that I had already done an install to a VM.  Fired that up too and played again for a bit.  

It is a nice system to use.  Very familiar with the gnome DE.   But still leaves me feeling like i am very restricted... All the basics are there and could replace my work desktop as it has all I'd need (openoffice (I installed OOo3 beta), email, etc).  But the huge breadth of software available to linux is not there yet.  So it feels a little lacking...

Maybe I will install to a USB HDD and copy all my work folders across and try to use it for a few weeks as my work desktop.  Just as an experiment.  :)

---

### Post by Sef on 2008-07-21
I've tried Open Solaris and worked well.  I just have to figure out how to download the codecs, so I can play some music.

---

### Post by tact on 2008-07-21
Yer... it deserves more of my attention.  It really is nice.  Installing to an external HDD as I type  :)

---

### Post by cardinals_fan on 2008-07-21
> **Sef said:**
> I've tried Open Solaris and worked well.  I just have to figure out how to download the codecs, so I can play some music.
Use RealPlayer :)

(The *other* codecs are available from the Blastwave repos)

---

### Post by dca on 2008-07-21
Encountered the same package issue(s) other have.  Wouldn't been that big a deal but my Acer laptop and clone (P4) PC both req'd drivers for all the network devices (both wired and wireless) and other items.  The driver utility is nice but areas on Sun's site that point to the necessary driver(s) were dead links...  I'll have to revisit that at a later time. 
 
I'm still stuck on purpose, though.  They went to all the trouble to get Ian Murdock on board and here with the SCO debacle, Sun may owe Novell money because of the Unix copyrights/licensing. I can only think that is why the OS, FS, etc weren't released under the GPL because of possible litigation.
 
Solaris10 on SPARC is solid as a rock, but adding a bunch of packages on top of it and throwing it out as open source just seems to me like a day late and a dollar short.

---

