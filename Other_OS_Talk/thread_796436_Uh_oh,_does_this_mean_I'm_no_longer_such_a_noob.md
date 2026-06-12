---
title: "Uh oh, does this mean I'm no longer such a noob?"
date: 2008-05-16
forum: Other OS Talk
---

### Post by Lucho on 2008-05-16
I've been away from this forum for a while (thanks to work and whatnot) so I thought I'd remedy 
 that with a recent story. Before I begin, let me point out that while
 I work hard to be open-minded and objective with all OS/ software
 in general (with emphasis on objective) I admit to being a debian fanboy.
 So last weekend I suddenly got an inexplicable urge to give Slackware a
 try. I'd avoided it in the past because of bad experiences with some of its
 spinoffs like GoblinX and Arch. But, ok said I, into the fire we go.
 
 I downloaded BlueWhite64 12.1 because I prefer to go with 64-bit
 distros (yeah, I know about the real 32-bit vs. 64-bit performance difference
 but dammit, I like my placebo effect  ) and BW64 seems to be the "purest"
 64-bit Slackware. 
 
 So, what happened? Well, everything installed without a hitch; the
 installer reminds me an awful lot of the Sarge installer: ncurses, long-winded
 (well, not as much as Sarge) and tedious. But not difficult, just tedious. After
 installation I rebooted, and cheated, just a little. I rebooted into Debian and
 copied over some config files ( fstab, resolv.conf, etc. ) instead of configuring
 them. I had told the installer not to install a bootloader, so it installed LILO
 in /boot/lilo  . After editing Debian's GRUB I rebooted into BW64.
 
 I probably shouldn't have used KPackage to remove things I know 
 I won't need, but it got the job done. I compiled a new kernel using the
 2.6.25.3 source and the 2.6.25-dark1 patch and and couple of other apps
 (namely Swaret, MPlayer, Xine, and FFmpeg), along with installing the Nvidia
 driver. The result was a system I could work on.
 
 So to make a long story short, here are my observations:
 - All of the guides and tips that I pulled off the Slackware site worked without
 a hitch on BW64. 
 - Performance is very similar to Debian Sid, with a slight edge going to BW64.
 - I admit it: I'm lazy. Apt-Get has thouroughly spoiled me WRT package man-
 agement / installation. I had no difficulty compiling things (even the kernel
 was straightfoward), but it's more work than I care for. 
 
 Slackware is supposed to be difficult, a distro for advanced users. I'm
 not in IT, nor have I studied computers. I'm just a shadetree mechanic with
 a keyboard, but BW64/ Slackware turned out to be easier than some "User-
 Friendly" distros. So, my question is two-fold: not "What do you think of
 Slackware," but "How do compare Slackware to more mainstream distros?"
 
 My second question is just this: does anybody else have stories to tell
 about BlueWhite64 ? Do you all think it's "pure" Slackware?

---

### Post by Barrucadu on 2008-05-16
I haven't tried Slack yet, but it's been high on my todo list since I tried Zenwalk.

---

### Post by kerry_s on 2008-05-16
i never thought slackware was difficult. :confused:

i'm so debian entwined i don't think i'll ever leave it, i use to distro hop all the time looking for that little edge 1 distro has over the next, in the end i go back to debian. now i don't even bother with anything else, debian is what i know, anything else is just a toy.

---

### Post by Half-Left on 2008-05-16
Slackware is pure. everything else is based off it, even slamd64. I've used it for a few years been there done that, I just want a easy live now. :)

---

### Post by Lucho on 2008-05-16
> i never thought slackware was difficult. 
 
 i'm so debian entwined i don't think i'll ever leave it, i use to distro hop all the time looking for that little edge 1 distro has over the next, in the end i go back to debian. now i don't even bother with anything else, debian is what i know, anything else is just a toy.

         The sums up most of my sentiment too. I experiment with
other distros, but I've yet to come across anything I couldn't
do in Debian. 

> Slackware is pure. everything else is based off it, even slamd64. I've used it for a few years been there done that, I just want a easy live now. 

       True, and BlueWhite64 is pure Slackware, no ifs, and, or
buts about it. I admit to being impressed with Slackware/BW64
even if it's not really my cup of tea. 

    Here's some food for thought:
  Who else here finds it odd that Slackware doesn't have more of
a presence in education? It's do-it-yourself nature makes the OS
particularly well-suited for educational purposes. 

    Another thought:
  If you take the Slackware philosophy to its logical conclusion
you could make a netinstall verson, like Debian does. No bigger
than a business card, with just enough to get a bootable system.
From there the user builds the system to according to his needs.

---

