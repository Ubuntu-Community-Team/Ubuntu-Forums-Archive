---
title: "Thinkpad T40, T41, T42 -- Complete Feisty Install Guide"
date: 2007-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Lil on 2007-08-13
Hello,

I compiled a very thorough (I believe guide) of my experiences of installing Ubuntu 7.04 on my Thinkpad T40. It's the XGA Radeon 7500 based model; but it should be more or less applicable to any T4x series ThinkPad. (I cannot vouch for some of the info on the Radeon 9000, 9600, X300, GMA and FireGL T4x's.)

I wrote it if anything as a reinstall guide for myself :)

I have been using Ubuntu now for about a month although I'm not a complete UNIX alike system newbie having used FreeBSD/NetBSD/MacOS  X and a few other systems in my time; so I had a little bit of knowledge to start with.

The guide will help you suss out pretty much all the hardware except for the modem which I never use but it would appear if I did sort it, it would work. I think that's the only piece of hardware I haven't 'covered' fully in my guide.

The guide might in some aspects to a pro not come across as the best advice in some instances but what I have detailed works, and very well too. For what it's worth I don't dual boot, and I am using Windows when the need arises (not often!) in VMware Player.

I have covered:

[LIST]
[*]TV output over Svideo for DVD playing
[*]Dual screen support for extended desktop
[*]Dual screen support for mirrored display
[*]Auto detection of external display and asking whether to mirror or extend on boot
[*]Web fonts
[*]Media Codecs
[*]WINE
[*]and more!
[/LIST]

As you can tell some of the info is generic. I have tried to be absolutely thorough, and not to assume pre-existing knowledge. It should be of use to anyone in parts, but if you own a Pentium M based laptop that uses a Radeon GPU; it should be of use if not in verbatim!

You can download the PDF (32 pages) from my blog:

[http://lilserenity.wordpress.com/2007/07/31/installing-ubuntu-feisty-fawn-704-on-a-thinkpad-t40/](http://lilserenity.wordpress.com/2007/07/31/installing-ubuntu-feisty-fawn-704-on-a-thinkpad-t40/)

Also valid for systems like the ThinkPad X31, X32, some R40, some R50 series and I think even the A31p.

I'll keep revising and updating it! Hope it's of use to someone :)

Thanks,

Vicky

---

### Post by Vadi on 2007-08-14
Thank you, that's a very useful guide.

A quick question though - did you manage to set the Super (Windows key which the T40 doens't get) key? If you did, hoiw?

---

### Post by Lil on 2007-08-15
Hiya,

I'm glad you have found it of use :)

As for the latter I have not configured it as I don't really ever use the Windows key, even when I am using Windows as I am now. What purpose do you need the Windows key for?

If you want keyboard access to the Application menu, you can use Alt + F1 and then navigate using the cursor keys + return key. And Alt+F2 gives you a run command window. This is superficially similar to hitting the Windows key for the start menu and Win + R for run. Not sure if this helps.

Vicky

---

### Post by Vadi on 2007-08-15
I need the Windows key for the fancy compiz-fusion effects, which seem to rely on it a lot.

I read some tips on setting it before, but I can't find any of them now... and I've messed up my xmodmap quite a bit (if there is a way to reset it to how it was by default, I'd gladly use it).

here's what the xmodmap command gives me:

```
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock      
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_R (0x71),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x73),  Super_R (0x75),  Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)
```

---

### Post by yoel.koenka on 2008-12-06
Though it's not the exact same system, I tried getting S-video to work on my T41p (Ubuntu 8.10).
The script for doing that simply makes my screen black but doesn't show anything on the connected TV.
Help anyone?

---

