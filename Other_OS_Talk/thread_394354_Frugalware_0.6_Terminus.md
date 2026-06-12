---
title: "Frugalware 0.6 Terminus"
date: 2007-03-26
forum: Other OS Talk
---

### Post by Rumor on 2007-03-26
I read a comment posted somewhere that Slackware + Arch = Frugalware. So I visited Frugalware's website to see what it was all about. Three things caught my eye. 

[http://frugalware.org/](http://frugalware.org/)

1. Frugalware uses pacman as its package manager
2. Frugalware has a pygtk gui front end for pacman
3. Frugalware 0.6 has Gnome 2.18 in it

I downloaded both DVD images and burned them. I put the first disc in a spare P2/400 512 RAM machine and booted into a text based installer that looks sort of like the Debian Etch text installer.

I only needed the first DVD for the packages I selected during the install process. After rebooting, I was brought to the Gnome 2.18 desktop:

[[IMG]http://img145.imageshack.us/img145/3076/desktophi9.th.jpg[/IMG]](http://img145.imageshack.us/my.php?image=desktophi9.jpg)

I was mostly interested in the front end for pacman. I fired it up: 

[[IMG]http://img141.imageshack.us/img141/9418/packagemanageraw9.th.png[/IMG]](http://img141.imageshack.us/my.php?image=packagemanageraw9.png)

Selected the new packages:

[[IMG]http://img143.imageshack.us/img143/1664/selectedim1.th.png[/IMG]](http://img143.imageshack.us/my.php?image=selectedim1.png)

and installed them.

[[IMG]http://img143.imageshack.us/img143/6374/executingnv5.th.png[/IMG]](http://img143.imageshack.us/my.php?image=executingnv5.png)

It worked, sort of. There was no option to select all the packages, each had to be clicked individually. There was no evidence that it was downloading anything, and the installation itself was rather anticlimactic. It was a lot more work than simply typing "pacman -Syu" in a root terminal

I don't know enough about Slackware to say how much like Slack it is. So far as comparing with Arch, it seems like a sluggish Arch, but I have not gotten into the .conf files to take them apart and see what is in them yet.

I like Gnome 2.18 but think that I will wait for it in Arch and the next Ubuntu.

---

### Post by pelle.k on 2007-03-27
Frugalware is certainly not sluggish. It's actually a bit faster in some areas. (it's i686 just like arch linux, using DT_GNU_HASH)
The pacman gtk frontend is nothing but a placeholder for the "real thing" planned for 0.7 release.

If you're used to arch linux, it might take a while to adjust to frugal. It might even be awkward.
It helps to think of it as a mix between arch and ubuntu, but using slackware of course.

I would say there's really no apparent flaw in this distro, other than the lack of a "pretty" and organized forum. The current forum isn't very active i'm afraid. To me, a good community/forum is important as i like to search for answers to common problems (yes, people, i actually use the search function instead of spawning threads that could have easily avoided), instead of bothering the devs on the irc channel with the same question they have probably have heard a thousand times before!

---

### Post by Rumor on 2007-03-27
I think that most of the "sluggishness" I noticed comes more from the computer being rather slow than from the OS. I've run Arch on that particular box from some time and am used to how it responds. It is likely more of a feeling that Frugalware was slower than any realy decrease in performance.

I know the package manager is not in its final form as of yet, what with all the work that has been going on with getting pacman 3 ready and all. When I ran it from the terminal, it responded every bit as quickly as Arch, as I would expect it to.

On a somewhat related note, both pacman 3 and Gnome 2.18 are now available in Arch's testing repository.

---

### Post by pelle.k on 2007-03-27
For me, one of the reasons i'd choose frugal instead of arch (i run both though...) is the 6 month release cycle. This would be a bad thing though, if you're into that rolling release system thingy ;)
Arch has got several more system level applications in their repos such as powersave, cpufreq-utils and firehol (firehol is in the aur btw), but i managed to do all that was missing with pure bash and iptables etc...
You could always create (or port from a pkgbuild) a frugalbuild and make the packages yourself though... (aah! the beauty of pacman and makepkg :) )

yeah, pacman3 in arch is going to be sweet! I'm going to write my own personal GUI frontend just to celebrate the "libification" of pacman. yay!

---

### Post by unbuntu on 2007-03-27
I installed Frugalware over the weekend.  I believe the installer is adapted from Slackware, rather than Debian.  However, the installer is quite buggy and crashed a lot on my laptop.  (Toshiba TE2100, P4 1.6, 256M)  Somehow I managed to install just the base system, and then use the dvd as frugalware repository.

They use a modified version of pacman, although the pacman basics still apply.  The difference in speed isn't quite noticeable, if any.  Being based off Slackware, it should be a stable enough system.

---

### Post by bonzodog on 2007-03-28
ooh...I might just get this..it looks interesting.

/me starts the download of the net installer.

---

### Post by .aku on 2007-03-29
I found out that if you choose not to do the 'expert' package selection in the install process (with the CD / DVD version), you'll end up having a system with too much stuff.
And what I've heard, the selection process is cumbersome. (I chose not to do the expert install, as I was just trying out.)
I don't have any experience with the net installer, but I think the package selection is the same.
I wanted to have a base system with only Fluxbox, but ended up having stuff I don't want.

For example Wine, I don't need it, and I don't want it installed on my system. Still, I end up with seeing Wine started up at boot. Hmm.
Next, ACPI install was partial, so if you need ACPI, you'll have to reinstall it and kill & restart the daemons.

Otherwise it's pretty damn good, it's for sure in my top 3.
I even removed Arch & Zenwalk, and installed Frugal on a clean HDD. (I regret it now.)
If you don't care about the 'bloat', go for it.
If you're anything like me who likes to have control of everything, go for Arch.
Or Zenwalk, still my favourite.

//aku

---

### Post by pelle.k on 2007-03-29
It's pretty much what is says in the installer. If you choose to install all groups, your going to end up with all the groups...
This is _not_ about bloat. It's about you not selecting only the groups you want. I went for base, X11 and gnome. That's what i got. Just like in arch! It still possible to have xapps installed, and you'll get your wine and whatnot without lifting a finger after the installation is done.

The expert package selection is not recommended unless you want to hurt your brain.

---

### Post by .aku on 2007-03-29
Okay then, I gave it another chance.
I chose to run the 'expert' package selection.
Everything was going nice, I got thru base groups, devel groups, gnome groups, and BOOM.
Segfault.
Crap.
Reboot. Another try.
base. ok.
devel ok.
gnome ok.
Segfault. Again.
It's not about the discs, md5 checked, burnt slow as fcuk, and they run perfectly without the expert selection.
I prefer Arch over Frugal now, just because I don't want stuff installed, which I still have to install in the end.

I'd rather install just the stuff I need. Arch or Zenwalk Core. <3


So that's about it.

//aku

---

### Post by unbuntu on 2007-03-29
> **.aku said:**
> Okay then, I gave it another chance.
I chose to run the 'expert' package selection.
Everything was going nice, I got thru base groups, devel groups, gnome groups, and BOOM.
Segfault.
Crap.
Reboot. Another try.
base. ok.
devel ok.
gnome ok.
Segfault. Again.
It's not about the discs, md5 checked, burnt slow as fcuk, and they run perfectly without the expert selection.
I prefer Arch over Frugal now, just because I don't want stuff installed, which I still have to install in the end.

I'd rather install just the stuff I need. Arch or Zenwalk Core. <3


So that's about it.

//aku

Segfault...That's exactly what happened to me.  I got it around with choosing just the base packages during installation and use the frugalware DVD as pacman source afterwards to install other packages.

---

### Post by pelle.k on 2007-03-29
omg. i don't want to sound harsh, but frugals base = arch base (more or less). frugals gnome = arch gnome (more or less). frugals x11 = arch xorg (more or less).
I can appreciate the fact that the installer screwed your installation, but _why_ do you then insist of using it then? Frugal can be installed in the same way you add stuff to arch. Install base _only_ and do what you normally would do in arch, and you'll get more or less the same result.

---

### Post by .aku on 2007-03-30
> **pelle.k said:**
> omg. i don't want to sound harsh, but frugals base = arch base (more or less). frugals gnome = arch gnome (more or less). frugals x11 = arch xorg (more or less).
I can appreciate the fact that the installer screwed your installation, but _why_ do you then insist of using it then? Frugal can be installed in the same way you add stuff to arch. Install base _only_ and do what you normally would do in arch, and you'll get more or less the same result.

Ok, again we go.
Only the **base**, nothing else but the **base** (just like I do in Arch).
Segfault.
It's not about what I choose to install, it is segfaulting **after** the package selection part,
it is not segfaulting **in** the package selection. (So only when it should start installing the packages I already chose.).
You know I got thru the selection process, but not further than that.
Then again, I *could* run the 'non-expert' install and live happy with it, but I can't.

so *no go* hombre. it just wont run.
But hey, I'm happy w/ Arch & ZW.
I still like Frugalware a lot, it's really sweet.
And for shizzle when the installer is fixed I will install 'Sayshell'

//aku

---

### Post by pelle.k on 2007-03-30
> so no go hombre. it just wont run.
OK. I apologize for my rudeness then.

---

### Post by .aku on 2007-03-30
> **pelle.k said:**
> OK. I apologize for my rudeness then.

Mate, what rudeness ? :confused:
Probably I also explained the situation kinda badly.
(English is _not_ my native language, I'm from your neighbour country. )
We're not that good in English.. :lolflag:


//aku

---

### Post by AlexExtreme on 2007-03-30
The installer is quite bad right now, although for 0.7 we'll really, really try to make the installer better.

---

### Post by Amorphous_Snake on 2007-04-05
So, as a Linux beginner, how is the Frugalware installer in comparison to that of Arch? I have to say that I failed to install Arch twice (v 0.7.2 and 0.8) although I really tried. But I guess I am a noob!

---

