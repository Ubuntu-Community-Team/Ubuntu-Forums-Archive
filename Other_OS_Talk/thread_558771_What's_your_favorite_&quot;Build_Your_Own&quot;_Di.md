---
title: "What's your favorite &quot;Build Your Own&quot; Distro?"
date: 2007-09-24
forum: Other OS Talk
---

### Post by SuperDuck on 2007-09-24
There are a number of ways that you can "build your own" distro, at least in the sense that you can install only what you want from the get go.  What I'm looking for is something that is between Linux From Scratch (which is a great side project I'm working on) and a fully featured OS.

Basically I want to start with the bare bones and only install what I want to - I don't want or need a lot of the programs and extra stuff that many distros come with!

I know about Gentoo, and will be trying that soon.  What else allows you to start the the bare minimum and grow from there?

Damn Small?
Arch?

What have you guys used?

---

### Post by Warren Watts on 2007-09-24
I have had great success with Archlinux.  From the time I put in the disk to having the windows manager up and running was less than 1 1/2 hours.  The package manager (pacman) is as easy to use as apt, and Arch's repositories grow larger every day.

---

### Post by rsambuca on 2007-09-24
You can start with a 'barebones' installation with almost any distro out there.  Gentoo is excellent for this and is actually very easy to set up since the handbook is very well written.  You just follow along step by step.  If you have partitioned your hard drive, you can just install Gentoo from within your existing distro so that you don't have any computer down time.

If you like to stick to the debian side of things, obviously debian is another alternative, or you can also just install the Ubuntu minimal installation, and then add Xorg, a Window manager or Desktop Environment, and start adding things you need one by one.  There is info on how to do that [here.]("https://help.ubuntu.com/community/Installation/LowMemorySystems").  You can then add as little as you want for a fast and lightweight system, or you can add a ton of stuff for a fully loaded desktop!

---

### Post by kellemes on 2007-09-24
> **Warren Watts said:**
> I have had great success with Archlinux.  From the time I put in the disk to having the windows manager up and running was less than 1 1/2 hours.  The package manager (pacman) is as easy to use as apt, and Arch's repositories grow larger every day.

Agree.. You have all the control you want to have **without** too much complexity (think KISS principle).
You do need to understand distro's like this (including Gentoo) can only perform when setup/managed right.
The best thing (and reason I'll never go Ubuntu permanently) is the rolling-release-system.

---

### Post by Warren Watts on 2007-09-24
> **rsambuca said:**
> You can start with a 'barebones' installation with almost any distro out there...... or you can also just install the Ubuntu minimal installation, and then add Xorg, a Window manager or Desktop Environment, and start adding things you need one by one.  There is info on how to do that [here.]("https://help.ubuntu.com/community/Installation/LowMemorySystems").  You can then add as little as you want for a fast and lightweight system, or you can add a ton of stuff for a fully loaded desktop!

I also wrote a HOW TO on doing just that with Ubuntu...

[URL="http://ubuntuforums.org/showthread.php?t=549958"]http://ubuntuforums.org/showthread.php?t=549958
[/URL]

---

### Post by qamelian on 2007-09-24
My favourite is Linux From Scratch [(http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")). You start with a live CD build environment and a big, honkin' manual/PDF file, and build literally everything from source. By the time you have everything up and running, you'll have had at least a taste of pretty much every aspect of putting together a Linux distro. Beware though: LFS has been known to make strong men weep in anguish.:)

If you though distros like Gentoo were and educational experience, LFS will take you to all new levels of geekdom!

---

### Post by SuperDuck on 2007-09-24
I was going through LFS and had the temporary environment almost done.  Then I decided to install Mint and accidentally blew away all the stuff I had been working on. :(  I'll keep workign on LFS now that I have my "main" distro squared away and working, but I also wanted something else to tinker with.

I looked at Debian, but what's the deal with it having to be installed from 27 (?!) CDs?  (Or 4-ish DVD's - that's a lot!)

---

### Post by rsambuca on 2007-09-24
> **SuperDuck said:**
> I was going through LFS and had the temporary environment almost done.  Then I decided to install Mint and accidentally blew away all the stuff I had been working on. :(  I'll keep workign on LFS now that I have my "main" distro squared away and working, but I also wanted something else to tinker with.

I looked at Debian, but what's the deal with it having to be installed from 27 (?!) CDs?  (Or 4-ish DVD's - that's a lot!)

You only need one cd for debian.

---

### Post by SuperDuck on 2007-09-25
You are correct - I was only looking at the "Full" install.  I will check out the Mini.

---

### Post by Rumor on 2007-09-25
IMO Arch bridges the gap between the extreme compile-it-yourself distros that you build from the ground up and the "do it all for you" distros that install a fully working GUI desktop environment and full suite of applications. 

Arch gives you a very basic system with its install and allows you to take it from there installing only what you want. I think that's one of the reasons there is no Live CD for Arch. The developers don't want to assume any choices for the user. Not everyone wants to use Gnome / KDE. Not everyone wants to use Firefox / Opera. So they give you what you need right up front and you take it from there.

For me Arch is ideal.

---

### Post by SuperDuck on 2007-09-25
Thanks, Rumor.  Arch is sounding better and better.  I believe I will be giving it a try!

---

### Post by igknighted on 2007-09-26
> **SuperDuck said:**
> Thanks, Rumor.  Arch is sounding better and better.  I believe I will be giving it a try!

I guess I'll be the voice of dissent here... I find Arch to make tasks difficult for no reason.  The way pacman works is just awkward and counter-intuitive.  Even the man page couldn't help me figure it out.  With Gentoo, while the initial setup is more time consuming, there are so many tools to help you that help you understand, and the whole thing just happens in a far more logical process (although sometimes sorting through blocked packages can be a pita).

I will say that KDEmod for Arch is incredibly slick, and if I ever go back and give Arch another go that will be the reason.

---

### Post by happy-and-lost on 2007-09-26
Arch and Debian base are probably the simplest.

---

### Post by epimer on 2007-09-26
> **igknighted said:**
> The way pacman works is just awkward and counter-intuitive.  Even the man page couldn't help me figure it out.  

I'm just curious - what did you find awkward about pacman? I just recently switched to Arch and am really liking the whole thing, pacman included.

---

### Post by igknighted on 2007-09-26
> **epimer said:**
> I'm just curious - what did you find awkward about pacman? I just recently switched to Arch and am really liking the whole thing, pacman included.

The biggest part was nowhere is it made clear what -S actually does.  In some cases it seems to want to update, in others it just refreshes the package list, etc.  I could go up and down the line, and most of the flags available seem to do different things in different situations.  In Fedora its very clear what "yum install ____" does, or "yum search _____".  Same with Suse and "zypper install _______" or "zypper search _______".  Same with Debian based distros, same (basically) with gentoo's portage, and same with the smart package manager.  Debian has a weird "update vs. upgrade" and "upgrade vs. dist-upgrade" thing going on (yes, I understand the differences, but I can see wh many could be confused), but overall is straightforward.

Then you get to distro's like Arch and Mandriva.  In Arch, this functionality that is distributed in a fairly standard set of options (install, update, search, etc.) is now re-arranged into a set of options that follows its own logic.  Now I am sure there are reasons for it, and I am sure that it does a great job because many like it... but it just works very differently.  The same deal with Mandriva.  In Mandriva, you have urpmi to install, but if you want to search or remove or do several other tasks, you need a different command (urpme for example).  This is a very odd setup (IMHO) and not very intuitive, and could certainly be streamlined to be more user firendly.

Basically, I am warning that if you choose Arch, expect to spend some serious time researching before you will feel comfortable working with pacman.  For me, I find portage to be easier and more intuitive, so I will stick with that.  Some may find pacman more their cup of tea.  It's not that either is bad, it's that they are different, and I much prefer how portage works.

---

### Post by init1 on 2007-09-26
> **SuperDuck said:**
> You are correct - I was only looking at the "Full" install.  I will check out the Mini.
I installed debian from the bootable business card and I am very happy with it. It is very minimal, but very easy to customize.

---

### Post by fwojciec on 2007-09-26
> **igknighted said:**
> The biggest part was nowhere is it made clear what -S actually does.  In some cases it seems to want to update, in others it just refreshes the package list, etc.  I could go up and down the line, and most of the flags available seem to do different things in different situations.  In Fedora its very clear what "yum install ____" does, or "yum search _____".  Same with Suse and "zypper install _______" or "zypper search _______".  Same with Debian based distros, same (basically) with gentoo's portage, and same with the smart package manager.  Debian has a weird "update vs. upgrade" and "upgrade vs. dist-upgrade" thing going on (yes, I understand the differences, but I can see wh many could be confused), but overall is straightforward.

Then you get to distro's like Arch and Mandriva.  In Arch, this functionality that is distributed in a fairly standard set of options (install, update, search, etc.) is now re-arranged into a set of options that follows its own logic.  Now I am sure there are reasons for it, and I am sure that it does a great job because many like it... but it just works very differently.  The same deal with Mandriva.  In Mandriva, you have urpmi to install, but if you want to search or remove or do several other tasks, you need a different command (urpme for example).  This is a very odd setup (IMHO) and not very intuitive, and could certainly be streamlined to be more user firendly.

Basically, I am warning that if you choose Arch, expect to spend some serious time researching before you will feel comfortable working with pacman.  For me, I find portage to be easier and more intuitive, so I will stick with that.  Some may find pacman more their cup of tea.  It's not that either is bad, it's that they are different, and I much prefer how portage works.

For something to become intuitive it only takes some experience with it  - it requires familiarization.  There is nothing complex or complicated about pacman, it actually seems to be designed to be maximally transparent - once you know how pacman (and makepkg) works you essentially understand the entire process by means of which source is compiled into a package and then installed in Arch - and you have an option of intervening at any point in the process of course. 

I assure you that pacman becomes second blood, just like emerge I suppose, within a couple of weeks or so...  What's more - one becomes aware and appreciative of a certain sense of ease, effortlessness and elegance with which it does what it does ;)

---

### Post by ynnhoj on 2007-09-27
> **fwojciec said:**
> For something to become intuitive it only takes some experience with it  - it requires familiarization.  There is nothing complex or complicated about pacman, it actually seems to be designed to be maximally transparent - once you know how pacman (and makepkg) works you essentially understand the entire process by means of which source is compiled into a package and then installed in Arch - and you have an option of intervening at any point in the process of course. 

I assure you that pacman becomes second blood, just like emerge I suppose, within a couple of weeks or so...  What's more - one becomes aware and appreciative of a certain sense of ease, effortlessness and elegance with which it does what it does ;)
if something requires "a couple of weeks or so" of familiarization, it's not at all intuitive ;)

don't get me wrong, i'm a happy arch user and i think pacman is okay, but i tend to agree with igknighted.  pacman works just fine, but it would be much more *usable* if the various command-line options were simplified and made more clear.

---

### Post by fwojciec on 2007-09-27
> **ynnhoj said:**
> if something requires "a couple of weeks or so" of familiarization, it's not at all intuitive ;)

don't get me wrong, i'm a happy arch user and i think pacman is okay, but i tend to agree with igknighted.  pacman works just fine, but it would be much more *usable* if the various command-line options were simplified and made more clear.

Well, I guess we have different ideas about what it is for a package manager to become intuitive or usable ;)  For me that means that I know how the source code becomes a package and then how it can be installed on the system.  Two weeks was a very conservative estimate, by the way, and purposefully so.

I have never learned apt-get/aptitude at all because I could never learn how to make Debian/Ubuntu packages properly (other than with checkinstall, but that doesn't count)  - so my use of apt-get/aptitude was limited installing/removing packages and updating the system :(  An entire aspect of Debian package management was always hidden from me or beyond my abilities...  With pacman I have no such issues.

That was just an example of what I mean.  And if someone finds doing "man pacman" or "pacman --help" every once in a while to find the necessary commands he is looking for then I guess Arch is not for them.  The KISS way of doing this, IMO, is to have minimalistic one letter per functionality commands such as pacman -Syu for example.  That way once I learn them I have an easy time typing them in the future since I don't need to type out whole words like "install" and "upgrade" or "update" again and again and again.

EDIT: Also, you could of course do "pacman --sync --refresh --sysupgrade" instead of "pacman -Syu" for example, but is it really easier that way?

---

### Post by igknighted on 2007-09-27
> **fwojciec said:**
> Well, I guess we have different ideas about what it is for a package manager to become intuitive or usable ;)  For me that means that I know how the source code becomes a package and then how it can be installed on the system.  Two weeks was a very conservative estimate, by the way, and purposefully so.

I have never learned apt-get/aptitude at all because I could never learn how to make Debian/Ubuntu packages properly (other than with checkinstall, but that doesn't count)  - so my use of apt-get/aptitude was limited installing/removing packages and updating the system :(  An entire aspect of Debian package management was always hidden from me or beyond my abilities...  With pacman I have no such issues.

That was just an example of what I mean.  And if someone finds doing "man pacman" or "pacman --help" every once in a while to find the necessary commands he is looking for then I guess Arch is not for them.  The KISS way of doing this, IMO, is to have minimalistic one letter per functionality commands such as pacman -Syu for example.  That way once I learn them I have an easy time typing them in the future since I don't need to type out whole words like "install" and "upgrade" or "update" again and again and again.

EDIT: Also, you could of course do "pacman --sync --refresh --sysupgrade" instead of "pacman -Syu" for example, but is it really easier that way?

It's not about the word "update" or "-S vs. --sync", it is the lack of a usable definition of these terms.  The man pages, the wiki at the arch site, and the --help don't really tell you what exactly pacman is doing.  To me, sync and refresh sound just about the same.  Also, theres a logic behind "this command will update packages, this one will search, this one will install, etc." that is just not there with pacman.  I am sure that pacman's way has its own logic that in some situations makes more sense, but for me and my uses, I find it distracting because I am getting extra complexity for no (to me) reason.

And really that is what it is all about.  By getting more choice out of a system you have to add complexity.  The question is, does this break from the norm lead to a better experience, even if it is more complex.  Many might say that the way pacman works, while a bit more complex, gives them something they need.  To me, it is complexity with no gain.  Compare this to portage.  I have to deal with use flags in portage.  This is ok with me because the added complexity gives me more control over what is installed on my system and what is compiled into those apps.  It's not that complexity is bad, but rather the rather (in my experience) the complexity added by pacman just doesn't add anything to my linux experience.

---

### Post by fwojciec on 2007-09-27
> **igknighted said:**
> It's not about the word "update" or "-S vs. --sync", it is the lack of a usable definition of these terms.  The man pages, the wiki at the arch site, and the --help don't really tell you what exactly pacman is doing.  To me, sync and refresh sound just about the same.  Also, theres a logic behind "this command will update packages, this one will search, this one will install, etc." that is just not there with pacman.  I am sure that pacman's way has its own logic that in some situations makes more sense, but for me and my uses, I find it distracting because I am getting extra complexity for no (to me) reason.

And really that is what it is all about.  By getting more choice out of a system you have to add complexity.  The question is, does this break from the norm lead to a better experience, even if it is more complex.  Many might say that the way pacman works, while a bit more complex, gives them something they need.  To me, it is complexity with no gain.  Compare this to portage.  I have to deal with use flags in portage.  This is ok with me because the added complexity gives me more control over what is installed on my system and what is compiled into those apps.  It's not that complexity is bad, but rather the rather (in my experience) the complexity added by pacman just doesn't add anything to my linux experience.

To some extent the complexity of pacman is a testimony to how powerful it is as a package manager.  So agreed to some extent.

Pacman is not more difficult than portage, you're just probably more familiar with portage - that's what I was trying to say earlier anyways.  I would also say that you can achieve pretty much the same overall final effect with gentoo/portage and arch/pacman (more or less of course) - in one case you'll be mostly compiling from source but with an option of installing binary packages when needed, in the other case you'll be mostly working with binary packages but you will have an option of customizing particular packages and building them from source if you want.  I personally prefer the Arch way because I have no use for the ability to customize every single package, but if there was no Arch I'd be likely using Gentoo anyways because of it's flexibility.

Just to clarify this, as one could get an impression, given what you are writing, that in portage complexity comes with a real benefit, as opposed to pacman, where it is for its own sake ;)

---

### Post by kelvin spratt on 2007-09-27
you can also use jacman in ARCH looks very much like synaptic and as easy to use i tried faurn the other day arch based live DVD, easy install very impressed with the graphics and performance, and 3 setups 1 being traditional arch 1 on pen drive and their own 2 ways that makes 4 to much windows looking for me though.

---

### Post by bonzodog on 2007-09-27
There is also Zenwalk Core, based off Slackware. 

The basic install ISO is just 200MB, and installs an operative CLI system, plus the CLI end of the package manger, netpkg. It installs almost no apps, no X, just binutils.

It took me an hour to install X and the Openbox WM, then I used SLiM for a login manager.

---

