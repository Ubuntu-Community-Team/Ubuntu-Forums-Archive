---
title: "Can't run 12.04 live CD on Pana CF-52"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by acrosome on 2012-09-25
Ok, I'm ready to revisit a problem I already discussed a bit here:

[http://ubuntuforums.org/showthread.php?t=2010700](http://ubuntuforums.org/showthread.php?t=2010700)

I'm trying to install 12.04LTS on my laptop.  It is a Panasonic Toughbook that I bought from EmperorLinux in 2010.  It looks like my graphics device is an ATI Mobility Radeon HD 5650.  I know that there are issues with Ubuntu and some ATI accelerators...

Before I install, though, I want to be sure all works well so I'm trying to run 12.04 from a live CD.  My machine is 64-bit, and I have downloaded and tried both the i386 and amd64 versions to no avail.

When I boot from the CD I can get as far as choosing a language and then selecting to run Ubuntu from a CD.  Then the computer thinks a while and the screen whites out.

If I choose *nomodeset* I'll get farther- after selecting to run from the CD I'll see a screen with "Ubuntu 12.02" and four dots that cycle colors for quite a while while the machine thinks, but eventually an error shows up:

**[ 125.792748] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled**

...after which the screen again whites out.  If it means anything, every time I do this the numbers in brackets are different.  I know that a i915 error has something to do with deep magic in the chipset that is far beyond by humble abilities.

I have also tried with *acpi=off*, and this gets me a little farther yet: I get the same error but after that I get a "Welcome to Ubuntu" message before the screen yet again whites out.

So, any wisdom?

---

### Post by newb85 on 2012-09-25
I've had this problem with ATI Radeon in the past, and here's how I got through it:

When the little man and keyboard appear, hit Esc.  This will drop you to the old-school LiveCD startup.
You should see a list of languages.  Select yours and hit Esc. again.  This will drop you to a "boot:" prompt.  Enter 
```
live-install xforcevesa
```
and hit Enter.

With any luck, you'll be up and running.  (If you only want to run the live environment and not install, just hit Cancel in the installer.)

---

### Post by acrosome on 2012-09-29
Well, I was just trying to run it from the CD, not do the full install yet.  But, what the hell, right?

So I tried what you said and nothing happened.  But then I tried:

> live-install acpi=off nomodeset xforcevesa

And it started installing.  I figured in for a penny in for a pound so I just had it clobber my whole hard drive so I'd only have Ubuntu on it, because I wanted to remove as many other variables as possible.  Installation completed without problem (except that my mouse didn't work so I navigated through all the choices with the keyboard).

And it won't boot- the same thing happens.  The screen just grays out and seems to sort of fade.

Oddly I **can** get Mint 13 to run from the CD, but only in compatability mode.  If I try to run it from a HD install (which also seems to go without  ahitch) I get the exact same grayed out screen.  Even if I run it in compatability mode I still get that error about "failed to get i915 symbols" but eventually it does boot from the CD into a fully functioning system- that's how I'm typing this.  So I installed Mint to the hard drive but it won't boot and I get the same grayed out screen.

(I mention this because Ubuntu 12.04 and Mint 13 are related.)

So, now I have a nonfunctioning computer, until I can get this worked out.

So, any more ideas?  I'd be happy with either Ubuntu or Mint, frankly.

---

### Post by mips on 2012-09-30
> **acrosome said:**
> Well, I was just trying to run it from the CD, not do the full install yet.  But, what the hell, right?

So I tried what you said and nothing happened.  But then I tried:



And it started installing.  I figured in for a penny in for a pound so I just had it clobber my whole hard drive so I'd only have Ubuntu on it, because I wanted to remove as many other variables as possible.  Installation completed without problem (except that my mouse didn't work so I navigated through all the choices with the keyboard).

And it won't boot- the same thing happens.  The screen just grays out and seems to sort of fade.

Oddly I **can** get Mint 13 to run from the CD, but only in compatability mode.  If I try to run it normally I get the exact same grayed out screen.  Even if I run it in compatability mode I still get that error about "failed to get i915 symbols" but eventually it does boot from the CD into a fully functioning system- that's how I'm typing this.  So I installed Mint to the hard drive but it won't boot and I get the same grayed out screen.

(I mention this because Ubuntu 12.04 and Mint 13 are related.)

So, now I have a nonfunctioning computer, until I can get this worked out.

So, any more ideas?  I'd be happy with either Ubuntu or Mint, frankly.

This individual [http://ubuntuforums.org/showthread.php?p=12070623](http://ubuntuforums.org/showthread.php?p=12070623) booted to a shell and installed new ati drivers.

Dunno what's in the repos but these PPA contain the latest fglrx drivers,
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by acrosome on 2012-09-30
> **mips said:**
> This individual [http://ubuntuforums.org/showthread.php?p=12070623](http://ubuntuforums.org/showthread.php?p=12070623) booted to a shell and installed new ati drivers.

You're kidding, right?  That was me.  :D  (On 10.04LTS.)  As I mentioned in that thread, I'm now revisiting the matter, because I wasn't happy with all the issues I was having with my EmperorLinux install.

Right now I'm trying to *install* 12.04LTS, and I'm willing to defenstrate completely and reformat my whole drive.

But I can't even get the damned liveCD to run.  As mentioned above I went ahead and tried an install anyway, but no dice.

I've got all my files backed up and I'm starting with a clean slate, here.  So even if you have an idea that reformats my hard drive I'm game.  But I can't get anything to boot.  Is there a way to edit GRUB to force a boot to a shell?  Because that's the only thing I can get into right now, GRUB.  I tried pressing e and adding **init=/bin/bash** to the line that starts with linux... then ctrl-x to boot, but I STILL get that same damned greyed out screen

---

