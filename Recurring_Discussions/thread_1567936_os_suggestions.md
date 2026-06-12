---
title: "os suggestions??"
date: 2010-09-04
forum: Recurring Discussions
---

### Post by ventrical on 2010-09-04
Hi All,

  I am trying to experiment with an olde Hp Pavillion 733MHz with 256 sdram. Knoppic 6.2 and Damn Small Linux (DSL) work pretty good but I wanted to try somthing a little faster and more stable.

Does anyone know of any Ubuntu, Linux or Fedora stable installs that would work with this PC.??

thanks

---

### Post by Donzieja on 2010-09-04
I'd go for Intrepid, even Jaunty. I've seen Jaunty run on a 333 mhz iMac G3 with 190 mb ram, so I don't see why it wouldn't work for you.

---

### Post by -kg- on 2010-09-04
> **Donzieja said:**
> I'd go for Intrepid, even Jaunty. I've seen Jaunty run on a 333 mhz iMac G3 with 190 mb ram, so I don't see why it wouldn't work for you.

I wouldn't suggest the above.  Intrepid is no longer supported, and Jaunty's support is ending next month.  Besides, earlier releases won't necessarily be "faster and more stable" on a machine with limited resources.

You might want to try a minimal install Ubuntu release, or maybe Puppy Linux, which is designed to load into and run from RAM.  The newest Puppy Linux release is based on Ubuntu Lucid.  If the machine is new enough that it will boot from a USB Flash drive, you might want to try putting Puppy on a Flash drive and booting from that.

A USB Flash drive will give you quicker boot time, and the fact that Puppy loads into and runs from RAM means that it will run at the maximum possible speed for the given system. It runs from between 65 and 100 MB of RAM, so you would have more than enough RAM for it to run efficiently.

If your machine won't boot from USB, it will still run from a Live CD...it will just boot up slower.  Once booted, though, it still runs from a RAM disk and will run just as fast.

You should be able to install Ubuntu, though, if you want to.  With 256 MB of RAM, you will likely have to use the Alternate Install disk, but it can be done, and it will run on your system, albeit slowly...probably more slowly than DSL.

I don't know how DSL works, but if you're looking for more speed and efficiency, I'd say Puppy is probably what you're looking for.

---

### Post by printfw on 2010-09-04
As variant you may try lubuntu based on LXDE:
[http://lubuntu.net/]("http://lubuntu.net/")

---

### Post by Frogs Hair on 2010-09-04
Linux Peppermint is worth a look.

---

### Post by ventrical on 2010-09-04
> **printfw said:**
> As variant you may try lubuntu based on LXDE:
[http://lubuntu.net/]("http://lubuntu.net/")

Thanks!!!

This was a great install on the HP. It's real snappy :)

---

### Post by Sef on 2010-09-04
Moved to Recurring Discussions.

---

### Post by zipizap on 2010-09-04
I've also installed Lubuntu in a PC with 256MB Ram, and it went just fine :)
LXDE is making good advances for low-ends :)

---

### Post by OpressedCalamity on 2010-09-04
> **ventrical said:**
> Hi All,

  I am trying to experiment with an olde Hp Pavillion 733MHz with 256 sdram. Knoppic 6.2 and Damn Small Linux (DSL) work pretty good but I wanted to try somthing a little faster and more stable.

Does anyone know of any Ubuntu, Linux or Fedora stable installs that would work with this PC.??

thanks

Freebsd. :3
Archlinux:3
GENTOO!
and ultimately, Minix.

---

### Post by ventrical on 2010-09-05
Wow!!..Thanks everybody.

The Lubuntu OS is really the trick for older PCs. Just amazing .. and so unobtrusive.

  It has this really neat little program called Osmo which is a personal organizer/calander!!

Just great stuff!!

Google Chome is a little choppy.

 How do I remove Google Chrome and put in Firefox?

Thanks again for the Lubuntu Link.!!

---

### Post by printfw on 2010-09-05
Don't mention it, man :)

---

### Post by -kg- on 2010-09-14
> **ventrical said:**
> Google Chome is a little choppy.

 How do I remove Google Chrome and put in Firefox?

If you don't already found out or know about it, you can uninstall Chromium from Synaptic Package Manager and install Firefox from same.

It's very unlikely that you'll have any better luck with Firefox, though, as far as performance goes.  I would assume that the included Chromium browser was pre-configured to run as efficiently as possible with Lubuntu while providing as many of the most-used capabilities as possible.

You might want to try a lighter-weight browser, though some of the features you might want could be missing.  Just launch Synaptic and type "browser" in the search box.  See what you can find that you might want to check out.  You don't need to uninstall Chromium in order to try other browsers, unless HD room is a big issue.  Just install whatever browser(s) you want to try, and if you don't like them, uninstall them again.

---

### Post by MasterNetra on 2010-09-14
> **-kg- said:**
> If you don't already found out or know about it, you can uninstall Chromium from Synaptic Package Manager and install Firefox from same.

It's very unlikely that you'll have any better luck with Firefox, though, as far as performance goes.  I would assume that the included Chromium browser was pre-configured to run as efficiently as possible with Lubuntu while providing as many of the most-used capabilities as possible.

You might want to try a lighter-weight browser, though some of the features you might want could be missing.  Just launch Synaptic and type "browser" in the search box.  See what you can find that you might want to check out.  You don't need to uninstall Chromium in order to try other browsers, unless HD room is a big issue.  Just install whatever browser(s) you want to try, and if you don't like them, uninstall them again.

+1

Personally, Chrome preforms better then Firefox at least for me. I use Firefox with noscript+adblock+betterprivacy for when I need to preform sensitive activities, (access bank account & purchase things, etc)

---

### Post by Legendary_Bibo on 2010-09-15
Xubuntu 9.10

I have a machine with just a slightly faster processor, but it was snappy with Xubuntu 9.10, It's a bit slower with 10.04 and it can't detect the graphics card now so no wobbly windows. :(

---

### Post by kenwong on 2010-09-18
Lubuntu has come to my attention just recently.  Right now, I am using Crunchbanglinux on my old Thinkpad 600E with Pentium II 300MHz, 226M Ram.

I am considering reinstalling the OS and am wondering which linux distro may suit my old machine better.

Anyone can please give me some advice/info?

I also noticed some discussion about chromium vs firefox.  How about swiftfox?

Thank you.

---

### Post by Dragynn on 2010-09-18
Slitaz rocks on old machines, soooo fast. Choose the xvesa version for extra compatibility with older video hardware (xvesa is lighter and faster too, just not quite as pretty as xorg can be).

Puppy Linux is cool, but the latest distro is seriously bloated, too much for low ram. There is a version called Turbodog Xtreme that's lightweight and as fast as Slitaz. These are the 2 that I use on my old PIII laptop.

---

### Post by Dragynn on 2010-09-18
> **MasterNetra said:**
> +1

Personally, Chrome preforms better then Firefox at least for me. I use Firefox with noscript+adblock+betterprivacy for when I need to preform sensitive activities, (access bank account & purchase things, etc)

Ditto that, but I use Iron, same as Chrome, but without Google spyware. It can use adblock lists too. Fast as lightning, waaaaaaay faster than FF.

---

### Post by murderslastcrow on 2010-09-18
Doesn't get much faster than DSL. I ran Gnome with compiz comfortably on a system like that, with full-screen Flash playback (no stutters). So it all depends on your hardware, but if you want something incredibly light and incredibly good looking, go with an e17 ppa. If you want something stable and fast, I'm afraid that Fluxbox or Openbox are about as slim as you can get. JoeWM or IceWM are the only ones that might KIND OF be a bit slimmer than that.

IceWM is prettier than JoeWM, in my experience. So really, if you're going for super-minimal, anything IceWM based should suit you.

---

### Post by smellyman on 2010-09-19
another to try:
 
AntiX

---

