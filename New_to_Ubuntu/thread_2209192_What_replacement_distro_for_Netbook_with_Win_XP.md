---
title: "What replacement distro for Netbook with Win XP?"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-03-04
I have a Netbook which came with XP. Since that OS is not supported after April 4th, I want to convert it to Linux.

It has only 1GB RAM, but more importantly has a low powered processor ("System" describes as a N270 1.60 Ghz).

Among the possible distros, I have only had experience with Ubuntu in the past and run 12.04 on our computers. I do not like Unity and have gone to Gnome Classic as my IF.

I find the multiple workspace switching to be one of the best things to ever happen to the desktop environment. (I run 8 for different purposes)

So I am asking for recommendations on an appropriate distro for this computer. 12.04 would be ideal so that I only need to know one, but I think it is too heavy for this little device. How does Lubuntu compare, will it run OK on this computer, and what is the interface? If Unity, is Gnome Classic available to Lubunutu? Are multiple workspaces available (though not crucial as the Netbook is just a lighter weight alternative travel tool, mainly for checking gmail, maps. weather, lookups, etc,) 

Others? Maybe Linux Mint Xfce or Mate?  Or???? The closer it can look to 12.04 with Gnome Classic, the better. Again, not critical as the normal use for this Netbook is not demanding.

TIA

---

### Post by phidia on 2014-03-04
I'm sure you'll get many responses/opinions. You could check on Puppy linux. That distro is meant for older less powerful hardware.
Search at distrowatch too perhaps and good luck.

---

### Post by David_Wright on 2014-03-04
I have recently installed Lubuntu on a near-identical netbook (Advent 4211 = MSI Wind clone) and it runs flawlessly so far.

I had no setup issues with wireless, graphics etc, just booted and it worked - although I'd recommend running it from a USB stick first just to see.

So far the CPU seems to be more of a limit than the 1GB ram, although I will max that to 2Gb at some point.

I recommended Puppy to someone else earlier today, but that was on much older hardware and I'd recommend Lubuntu for an Atom-cpu netbook.

I'm a *buntu newbie, so can't comment on Gnome Classic etc.

---

### Post by endlessinstant on 2014-03-04
Lubuntu ships with the LXDE desktop environment.  LXDE is extremely lightweight and doesn't take very many system resources.   There is nothing to stop you from installing Gnome on Lubuntu and all the relevant packages you would need are available on the repos.  The various flavors of Ubuntu (kubuntu, lubuntu, xubuntu, etc.) are all basically the same system just with certain preconfigured options out of the box (namely what desktop environment they ship with).   

At any rate, both Lubuntu and Xubuntu would be good fits for your system as their respective desktop environments (LXDE and Xfce respectively) are both very lightweight.

---

### Post by sudodus on 2014-03-04
I would recommend either Lubuntu 13.10, or if you want a little more bells and whistles, Xubuntu 12.04 LTS or 13.10. But since you like 12.04 Gnome, I would also suggest ***Precise Gnome Classic Tweaks***, that you can install via the One Button Installer

[http://ubuntuforums.org/showthread.php?t=2172971](http://ubuntuforums.org/showthread.php?t=2172971)

or do the tweaks yourself from a regular Ubuntu installation

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by mastablasta on 2014-03-04
so many options.... Mate is old gnome and look like classig gnome in 12.04.
XFCE is like light gnome
LXDE (in lubuntu) is again very ligth

if screen is small perhaps Netbook plasma in Kubuntu might be worth having a look.

then there are various windows managers and such who will be even lighter. IceWM - you will feel like running windows 98 with latest programs :-)

---

### Post by Impavidus on 2014-03-04
I think all common Linux window managers have multiple workspaces nowadays. It was already pretty standard when I first used Unix, 11 years ago. No idea why it was never added as a standard feature in Windows.

---

### Post by ibjsb4 on 2014-03-04
> is Gnome Classic available to Lubunutu?

I have not tried this, but I think adding the classic desktop to lubuntu will bloat your lubuntu install thus defeating the purpose of lubuntu.  I think you will find that the classic desktop will add a couple of 100M to your install, if not more.  Once you have lubuntu installed you could verify this with the -s switch option (in terminal "man apt-get").  This will allow you to do a simulation of the install to see just what will be downloaded.

```
sudo apt-get install -s gnome-session-fallback
```

If your machine will run Xubuntu, I think you would find that it to be much more like the classic environment out of the box and would save you a few headaches as opposed to installing fallback.  One being Nautilus (it gets installed with fallback).  Nautilus likes to take over and probably would have to be dealt with.

So what to do?

Squeeze out a couple of 10G partitions and try both Lu and Xubuntu in their natural environment.

Also Lubuntu does not have a LTS, you would need to load 13.10.

---

### Post by Rob Sayer on 2014-03-04
I have some experience with different distros/desktops on my Atom 2600/gma500 netbook.  I don't use it at home very much, where I use kubuntu.  The 12.04 lts doesn't work as well on it so I've been hopping desktops & distros until 14.04 comes out.

Your netbook uses the integrated intel gma945 gpu for graphics.  It's not as bad in linux as the gma500 (cedarview) in the 1Gb netbook I'm typing this on.  But the linux performance isn't much good either.

Basically the first thing I think you need to do is avoid desktops that require 3D hardware acceleration like the plague.  This would include unity and cinnamon or any gnome 3 based desktop.  I've run unity on my 4Gb i3 laptop, and the 2D version wasn't really all that much faster.  No bloody way would I install it on my netbook.

I've actually run KDE (kubuntu) on it for probably the longest time.  Many will say you shouldn't run it in 1Gb but I'm surprised how well it runs after you configure it for speed.  There's some latency but the desktop itself has a lot of features that speed *me* up.  Which compensates a lot.

I've installed linux mint MATE on it, both 13 and 16.  Frankly, it wasn't that much faster than KDE, which is kind of ridiculous.  Plus their forum support is a joke.  It's just pitiful.  It's not that I think mint per se is a bad distro.  It isn't.  But the support is so weak I couldn't recommend it to inexperienced users.  At all.

XFCE is a good choice for a netbook.  I used to run it on this one and it's pretty zippy.  I always found it a bit clunky though.  Not my taste.  Plus, when I tried xubuntu 12.10, when I plugged in an external drive, the icon would appear on the desktop TWICE.  This was totally a known bug, and you just couldn't help ask yourself how the frak it got released like that.  I never really liked it after that, but I'm not NOT recommending it.

I've been lubuntu 13.10 on this netbook for about a month, and it's just stupid fast.  Very impressive.  The 14.04 lubuntu release is supposedly going to be a 3 year lts.  Otherwise I wouldn't have bothered trying it.  Haven't found any serious problems with it, except the config program that's supposed to run dolphin as default file manager doesn't work, and I've has no luck here or on askubuntu.  Frankly I don't think lubuntu has the support level the other desktop flavors do, and I've definitely researched this.  Which is kind of a vote for xubuntu, I guess.

However, lxde (lubuntu) is so fast I'm willing to forgive some rough edges.  Just don't expect eye candy.  There's a *reason* it works so well in 1Gb with a gpu that doesn't have proper linux 3D support.

I'd probably recommend ubuntu with xfce or lxde over the above mentioned really lightweight distros.  If you has 512Mb or less, well, yeah.  But if you don't have a lot of experience in linux ubuntu is just a no brainer to me if your computer will run it.  The really light ones don't have very many GUI config tools.

Myself, I think I may up the netbook ram from 1Gb to 2 and go back to kde when kubuntu 14.04 comes out.  Like I said, it ran surprisingly well in 1Gb when tweaked.  And I've always found that less memory needed = less features built into the GUI, which slow me down.

---

### Post by david98 on 2014-03-04
If it were me I would use lubuntu it's extremely well on an old advent netbook of mine with an intel atom 1.2 ghz It also has 1gb of ram it runs extremelly well for basic web browsing and watching youtube videos.

---

### Post by phidia on 2014-03-04
You might also consider [zevenos]("http://www.zevenos.com") since it's targeted towards older/lesser powered machines.

---

### Post by windowsfree on 2014-04-21
I installed Xubuntu 14.04 on Lenovo ideapad netbook s10-2.  Runs great, although I did add another gig of ram.  (2 gigs total).

---

