---
title: "Need help picking a new Distro"
date: 2009-01-10
forum: Other OS Talk
---

### Post by transmition on 2009-01-10
OK, before anyone gets mad, I still like Ubuntu. It works like a dream on my dell desktop, but on my macbook, it leaves some things to be desired (kernel panics, low battery life, low performance, slow program loading times)

So I would like to pick a new distro for my laptop. Primarily, I would be using it for basic internet usage such web browsing, instant messaging, multimedia viewing, and the occasional photo edit under wine.

Here is a list of Priorities I would like to see in the distro:

1. Performance - I want to be able to launch programs quickly, while using only a few resources. I suppose this would also include a superior battery life (I only get about 3 hours, regardless of whether or not wireless is turned on)

2. Multimedia support - I should be able to view a very large amount of media that requires proprietary codecs and packages like dvds, mp3's, Divx, etc. It would be preferred if I did not have to go fetching this packages myself, but that would not be that bad if I had to.

3. Stability - pretty self explanatory.

I guess I should say that wifi *must* work. Maybe not without some fiddling, but I must be able to get it working.

So far I have been looking at zenwalk, slackware and pclinuxos. Zenwalk seems like the best fit.

Any thoughts?

---

### Post by namegame on 2009-01-10
Zenwalk is definitely in my top 3 distributions. It's very good at what it does. It's got a few differences from Ubuntu though. It is based on Slackware. The installer is ncurses based. (Not %100 graphical). The package management is handled by netpkg. On a sidenote, it is intended to be compatible with Slackware packages, so if it works on Slackware it should work on Zenwalk. If my memory holds true, Zenwalk used to be called Minislack. 

I would also suggest that you look into Linux Mint. For performance, I would look into either the XFCE or Fluxbox editions. The multimedia support is installed by default. It's stability is on par with Ubuntu, because at it's core Linux Mint is Ubuntu.

---

### Post by cardinals_fan on 2009-01-10
I recommend Vector or Zenwalk.  Both are Slackware based, both include support for most multimedia out of the box, and both are very well made.  Vector has older software in the repos, but that gives it greater stability.  Zenwalk has a better package manager, but they can sometimes be a bit cavalier about security updates.  Vector is a touch lighter.  Both use Xfce.  Both have good communities, but Zenwalk's is larger.

Slackware is a superb distro, but it is intended for someone who wants total control over their OS from start to finish.  If that describes you, enjoy it.  Otherwise, stick with the two above.

SliTaz may fit the bill soon (with 2.0 in March, perhaps?), but it's still a bit new.

If you've had trouble with Ubuntu, I wouldn't advise Mint, because it IS Ubuntu under the hood.

---

### Post by transmition on 2009-01-10
Thanks! A couple more questions:

What are the differences between netpkg and apt-get? I believe that in slackware, everything had to be compiled, so is this the same in zenwalk, or can I do something like

```
netpkg install firefox
```

to install firefox?

As well, does anyone know anything about the hardware support for a macbook concerning these distros?

---

### Post by cardinals_fan on 2009-01-10
> **transmition said:**
> Thanks! A couple more questions:

What are the differences between netpkg and apt-get? I believe that in slackware, everything had to be compiled, so is this the same in zenwalk, or can I do something like

```
netpkg install firefox
```

to install firefox?

Fact: Slackware uses binary packages.  Traditionally, it requires the user to manage dependencies themselves.  This provides a tremendous amount of power, but also takes more work.  Tools such as slapt-get (used by Vector) and Slackpkg have evolved to fill this niche and handle dependencies.

Netpkg is another of these package managers, and it will resolve dependencies and install binary packages just fine.  The Zenwalk repos are smaller than those of Ubuntu and Debian, but the package manager is very similar (but with better output).

---

### Post by transmition on 2009-01-10
OK, things are shaping up pretty well, and I think I am going to try out zenwalk. Only two more questions:

1. In ubuntu I customized my touchpad to work like that in OS X, using a customized fdi file, with the following contents:

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
   <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
   <merge key="input.x11_options.TapButton1" type="string">1</merge>
   <merge key="input.x11_options.TapButton2" type="string">3</merge>
   <merge key="input.x11_options.TapButton3" type="string">2</merge>
   <merge key="input.x11_options.FingerLow" type="string">10</merge>
   <merge key="input.x11_options.FingerHigh" type="string">20</merge>
   <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
   <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
   <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
   <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
  </match>
 </device>
</deviceinfo>

```

Could this be ported over to zenwalk?

Second, would this tutorial for slackware carry over to my macbook?
[http://macbook.mared.com/linux/](http://macbook.mared.com/linux/)

---

### Post by cardinals_fan on 2009-01-10
You might like this thread: [http://support.zenwalk.org/viewtopic.php?f=18&t=16380](http://support.zenwalk.org/viewtopic.php?f=18&t=16380)

---

### Post by transmition on 2009-01-10
I suppose I should have said that I had a standard 4,1 Macbook. Not a Macbook Pro.

---

### Post by defri on 2009-01-10
> **namegame said:**
> Zenwalk is definitely in my top 3 distributions. It's very good at what it does. It's got a few differences from Ubuntu though. It is based on Slackware. The installer is ncurses based. (Not %100 graphical). The package management is handled by netpkg. On a sidenote, it is intended to be compatible with Slackware packages, so if it works on Slackware it should work on Zenwalk. If my memory holds true, Zenwalk used to be called Minislack. 

I would also suggest that you look into Linux Mint. For performance, I would look into either the XFCE or Fluxbox editions. The multimedia support is installed by default. It's stability is on par with Ubuntu, because at it's core Linux Mint is Ubuntu.

+1.:P:P:P:P 

Zenwalk was stable and have good performance without to much resources.
It have good package manager although the package not as many as debian.
I would like to recommended it.

:guitar::guitar:

---

### Post by transmition on 2009-01-10
Can anyone point me towards an installation guide for a standard macbook 4,1? My googling skills don't seem to helping, and after trying to boot the install cd (I assume it can act like a live cd, not sure) it hangs on a screen with two dolphins at the top and some text readout about my hardware.

---

