---
title: "correct login screen resolution"
date: 2008-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by mättu on 2008-08-31
first of all, I don't know if it works for you, I just describe what I did in the hope that it might help one of the many threads about wrong xorg.conf's

I learned that I have to learn again. For years, xorg.conf was *the* place for anything with screens, mice and so on. No more, it seems..

Good things first: My fresh install of xubuntu today was as easy as never before. It even imported all my settings and files without any problem. whow!

But:
The resolution of my 1500x1050 laptop screen was not recognized by gdm(?), xorg.conf didn't mention a word about my screens resolution. Manual corrections didn't help, not even back upping my old xorg from my older xubuntu which absolutely definitely worked for years.

The ubiquitous dpkg-reconfigure to the rescue! Thats what you know and read a lot about in the forums, even today. No avail. 

Even worse, it always set my keyboard to "us" which would be fine for programming but is quite incompatible to what I see on all computers around me.

Hint 1:
When installing with the graphical installer I had to be careful to set the correct resolution before installing. Otherwise I would never get the splash screen positioned correctly. And I tried quite a lot.

A friend of mine then knew about the "virtual" line to be set into the "screen" section of xorg.conf:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
        virtual         "1400x1050"

Then logout and wait for some time. gdm complains about "low resolution" etc. and needs some time to recover from that. In the little window it presented me I choose "always use low resolution" and "ok" and then had to wait again.

Then reboot - well I rebooted many times until I found out what to tick in the little "low resolution window" - and even considered to upgrade to Windows 95.

Now I had the correct resolution in gdm and the wrong keyboard layout again. So I looked at xorg.conf and what had I to see?!

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "800x600"
	EndSubSection
EndSection

My friends beautiful virtual-line had disappeared and was replaced by some nonsense about 800x600. I can confirm that *no* screen on my computer uses 800x600, neither the "f1"-"f6"-terminals, nor X nor gdm. I even don't have any old-fashioned video-beamer using this resolution.

Anyway, everything is perfect now.
Nonsense + Nonsense = Sense
it seems.

Hint 2: 
Try what I did, perhaps you want to try something even weirder, and post back what you found out. I would really be happy to find out, what goes on behind the scenes.

You think this is not a howto? Well. As written in [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)
"Once upon a time, long long ago, Linux users had to manually configure their X Window System in order to use graphical programs."

While I have very much sympathy for ubuntu and know not to expect the impossible from a system which is given to me for free (in all means), this is perhaps not what I expect from a "stable" "long time support" version.

And it's definitely still a log way to correct bug #1.

If you can direct me to a real, straight fix, please don't hesitate. I will immediately delete my rant. I have received much help in these forums, and I'm willig to share as well. I hope my post didn't upset too many of you.

cheers as always
:m)

---

