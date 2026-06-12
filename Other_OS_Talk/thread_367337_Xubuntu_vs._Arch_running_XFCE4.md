---
title: "Xubuntu vs. Arch running XFCE4"
date: 2007-02-22
forum: Other OS Talk
---

### Post by Slychilde on 2007-02-22
I recently took the plunge and put Arch on my laptop.  I put it on my test box, which consists of an old 750mhz Gateway, and it would open apps almost instantly.  My laptop, which is a dual 1.6 running Ubuntu takes anywhere from 2 to 10 depending on the app, and I'm talking amaroK, firefox, etc. nothing big.  That's crazy.

Well, I found out it's faster, but not necessarily *better*.  Stuff that should just work doesn't, such as cd's auto-mounting to desktop when inserted, dvd's auto-playing on insert, and wine seems to be a mess.  Right now, warcraft 3 is unplayable in Arch; with Ubuntu I installed both wine (ran winecfg) and Wc3 and it just 'worked'.

I also like the way Ubuntu does updates - apt-get and synaptic are fantastic.  It's also easier to find 'how-to' type information for Ubuntu; either it's harder to find for Arch or non-existent.

So, I'm wondering if Xubuntu would run as fast (or almost) as Arch running XFCE?  What differences can I expect, those of you who have used both Arch and Ubuntu?  Any tips?

Sort of a side question, but does it affect performance if you also put KDE or Gnome on your box, or is XFCE standalone faster?  Thinking Ubuntu with XFCE installed here. :)

---

### Post by Strider on 2007-02-22
From what I remember, ARCH was compiled with optimization so it runs faster.  Ubuntu on the other is compiled with more generic options to work with a wider range of hardware.  You will also see a difference with distros like Gentoo and Mepis.

ARCH uses "pacman" as the package manager ([http://www.archlinux.org/pacman/)](http://www.archlinux.org/pacman/)).  You can find tutorials on using it on ARCH's website.

XFCE may be a little faster but not sure by how much.  The hardware requirements are less compared to KDE or GNOME.  You'll have to decide for yourself.  I mentioned Mepis and I've used it in the past.  Compared to Ubuntu, Mepis runs a faster (this is by no means done with actual benchmark, just user experience on how the system respond).  Again, Mepis has some optimization that runs faster.

If you have KDE, GNOME and XFCE on your system, it doesn't make one run faster/slower than the other.  You can't use all 3 at the same time, only one.  Again, I recommend you try XFCE on Ubuntu to see if it responds better.

FWIW, you'll probably end up compromising when using any given linux distro -- you may give up package management for faster performance or vice versa.  Unless you want to get into compiling your own kernel and really need that extra speed, it's not worth the hassle in my opinion.  I can deal with a 2-5 sec delay instead of having it open instantly. :)

Anyway, hope that helps.  Best way to find out what works for you is to try it.  Each of the distro has a live CD so grab the xubuntu distro if you don't want to install it on your system.

-Mike

---

### Post by mips on 2007-02-22
> **Slychilde said:**
> 
So, I'm wondering if Xubuntu would run as fast (or almost) as Arch running XFCE?  What differences can I expect, those of you who have used both Arch and Ubuntu?  Any tips?

Arch will smoke ubuntu. I have not used arch but I'm willing to place a bet on it ;)

---

### Post by antenna on 2007-02-22
Indeed, Arch is optimised for 686, which probably accounts for little speed increase overall in fact.  More likely, it's due to the minimal amount of services and such that will typically be running on a machine since you don't tend to run things you wont be needing.  Admittedly, many people are at a loss as to explain why it's just so fast.

When you say stuff should 'just work', i'm unsure if you mean things are actually broken or if it's just because these things are usually done for you by other distros.  Nevertheless, i'll give that mounting is something that if often broken in one way or another on Arch, typically in Gnome. Such breakage forces me to Debian. 

Not sure what you mean about apt-get, as mentioned Arch uses Pacman which is of equal standing in my opinion. 

What I would do, if you're brave enough & since you managed to get Arch up and running you must have a clue, is install a base Ubuntu (or Debian..) system and go from there (install xorg, xfce4, etc (not xubuntu-desktop)). I do this with all my installs, you end up with everything you need and without excess services/bloat such as Ubuntu/Xubuntu provide.

It's not going to slow you down just having Gnome and/or KDE on your machine, but Gnome and KDE apps (that use libraries of their respective desktop) will typically be slower to load in Xfce or whatever than lighter alternatives since they have to load these libraries.  Usually for best performance on slower machines it's worth finding lighter alternatives, and thankfully there are usually lots of good GTK apps around that use neither Gnome/KDE libraries.

---

### Post by ynnhoj on 2007-02-22
> **antenna said:**
> What I would do, if you're brave enough & since you managed to get Arch up and running you must have a clue, is install a base Ubuntu (or Debian..) system and go from there (install xorg, xfce4, etc (not xubuntu-desktop)). I do this with all my installs, you end up with everything you need and without excess services/bloat such as Ubuntu/Xubuntu provide.i would probably recommend the same thing; i find it considerably easier to build up a system from the base, rather than have to trim the fat off of a typical install.  it's pretty simple to do with ubuntu, so if you got arch up and running (more or less), starting from an ubuntu base and adding the things that you want shouldn't be too tough since you'll probably find that most things just work--less editing of configuration files will be in order, when compared to the arch setup.

---

### Post by Slychilde on 2007-02-23
Thanks for your responses!

> Arch will smoke ubuntu. I have not used arch but I'm willing to place a bet on it 

It does in terms of speed.

> What I would do, if you're brave enough & since you managed to get Arch up and running you must have a clue, is install a base Ubuntu (or Debian..) system and go from there (install xorg, xfce4, etc (not xubuntu-desktop)). I do this with all my installs, you end up with everything you need and without excess services/bloat such as Ubuntu/Xubuntu provide.

First, thank you for the compliment. :)  It wasn't too hard, definitely not as bad as Gentoo (never could get a gui compiled without crashing), just took a lot of research and file editing.  It made me really appreciate how easy Ubuntu is....at one point I wanted to give out a Charlie Brown, "AUUUGGH!"  

But, I think I have everything working now, and holy crap is it fast.  Warcraft 3 is now running smoother than it was on Windows, even!  I guess I didn't have the ATI driver installed completely as direct rendering wasn't working.  I had to add this to my xorg.conf file (maybe it will help ubuntu'ers).

```
Section "DRI"
    Mode 0666
EndSection
```

Thank you for saving me the headache of reinstalling again.  I really didn't want to wipe my drive clean just to try Xubuntu out and possibly be disappointed by it's speed.  However, I may just take your suggestion and do a base install of Ubuntu and add XFCE after I get done playing with Arch - that sounds like fun.  ....I think I understand what's going on within both of these distro's much more now.

There is one question I do have: When you say do a base install of Ubuntu and install Xorg + XFCE - not Xubuntu-desktop - does that mean compile it from binaries or apt-get it?

> When you say stuff should 'just work', i'm unsure if you mean things are actually broken or if it's just because these things are usually done for you by other distros. Nevertheless, i'll give that mounting is something that if often broken in one way or another on Arch, typically in Gnome. Such breakage forces me to Debian.

Not sure what you mean about apt-get, as mentioned Arch uses Pacman which is of equal standing in my opinion. 

What I meant is that I can apt-get most things and they install + work without a hitch.  I have the option of tweaking it, or just having it work.  Which, also leads to me installing something in Arch, having issues configuring it or misconfiguring it, then searching for over an hour on how to get it to work properly; it gets frustrating.

Apt-get has been faster for me than pacman, and I really like how synaptic tells you when updates are available, rather than doing 'pacman -Syu' manually.  I know there are some community addons that add something similiar for Arch, but again, it's nice to have it  built right in. :)

---

### Post by ynnhoj on 2007-02-23
> **Slychilde said:**
> There is one question I do have: When you say do a base install of Ubuntu and install Xorg + XFCE - not Xubuntu-desktop - does that mean compile it from binaries or apt-get it?nah, aptitude/apt-get the [xfce4 package](http://packages.ubuntu.com/edgy/x11/xfce4) (it's in the universe repository, i think).

i think after doing your base install, something along the lines of "sudo aptitude install x-window-system-core xfce4" would be enough to get you started.  but you'd probably also want to install a display manager?  if you're aiming for light weight, you might prefer xdm over gdm.

---

### Post by Slychilde on 2007-02-23
Ah ok, thanks!  I was looking into SLiM; I wasn't even aware of XDM. :)

---

### Post by ynnhoj on 2007-02-23
i actually really like slim (and am using it currently).  it's considerably easier to configure, in comparison to xdm.  the one drawback i've been able to identify with slim so far: it seems to generate really big log files.  and i'm not quite sure why.  if you do end up using slim, check on its log file after a week or two and you'll probably see what i mean.

i guess the log file isn't hurting anything--but still, it seems excessively large to me.

---

