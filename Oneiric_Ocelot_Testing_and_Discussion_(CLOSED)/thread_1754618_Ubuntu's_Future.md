---
title: "Ubuntu's Future"
date: 2011-05-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-05-10
[http://www.phoronix.com/scan.php?page=news_item&px=OTQyOA](http://www.phoronix.com/scan.php?page=news_item&px=OTQyOA)

---

### Post by Harry33 on 2011-05-10
> **dino99 said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=OTQyOA](http://www.phoronix.com/scan.php?page=news_item&px=OTQyOA)

Mostly concerning X.org and Wayland.

---

### Post by dino99 on 2011-05-10
> **Harry33 said:**
> Mostly concerning X.org and Wayland.

yes, finally its means huge changes coming again with this release before next LTS, all depends on nvidia/amd drivers if they follow or not; if not Nouveau will become the main driver on nvidia side chipsets, or compiling from sources and using ppa for workaround

---

### Post by beew on 2011-05-10
> **dino99 said:**
>  if not Nouveau will become the main driver on nvidia side chipsets 

If that is the case I am switching distro.

---

### Post by Harry33 on 2011-05-10
> **beew said:**
> If that is the case I am switching distro.

Sure, but only if xorg xserver would not be available, which I doubt very much.
For the time being at least Nvidia Corp. has declared they do not follow with Wayland.

However, Wayland will take some time until ready.

---

### Post by Starks on 2011-05-10
switching distros won't help

wayland will be on the major distros by the end of 2012

---

### Post by beew on 2011-05-10
> **Starks said:**
> switching distros won't help

wayland will be on the major distros by the end of 2012

Who says that? Fedora tallks about switching but nothing is very concrete as far as I know.

But if this is the case there will likely be reasonable hardware and software support by then. I am worry that Ubuntu is going alone like it does with Unity.

---

### Post by jbicha on 2011-05-11
Wayland will definitely not be default until after 12.04 LTS. And it's uncertain even how much of a developer preview there will be. There is a wayland package is 11.04 but it wouldn't be considered by most users to do anything so it's got a long ways to go.

---

### Post by ronacc on 2011-05-11
> **Starks said:**
> switching distros won't help

wayland will be on the major distros by the end of 2012

Then it is entirely possible that they will become minor distros .

---

### Post by pressureman on 2011-05-11
Linux.conf.au graphics talks, for anyone interested:

[http://www.phoronix.com/scan.php?page=news_item&px=OTA2MA](http://www.phoronix.com/scan.php?page=news_item&px=OTA2MA)

Keith Packard gives a pretty interesting talk about Wayland, and it seems that Intel are pretty committed to it.

---

### Post by MacUntu on 2011-05-11
I'll doubt it will become default before Nouveau supports 3D officially.

---

### Post by kaldor on 2011-05-11
The switch to Wayland will be great. I can't wait. NVIDIA has, before, whined about it saying they won't produce drivers for it. 

If that's the case, I'm buying AMD from now on. They're the only graphics maker who put a huge lot of effort into making OSS drivers. Free AMD graphics drivers progress very fast; one Ubuntu release made went from laggy catalyst to smooth OSS. Go figure.

Sure, you can use Nouveau by then if the NVIDIA people still refuse. But why support a company by buying their stuff when they require reverse engineering?

Just a little rant :)

---

### Post by khelben1979 on 2011-05-11
> **Starks said:**
> switching distros won't help

wayland will be on the major distros by the end of 2012

Not in Debian.. :)

---

### Post by cariboo on 2011-05-11
> **khelben1979 said:**
> Not in Debian.. :)

I wouldn't bet against it, in Mark's keynote speech he stated that Canonical/Ubuntu would start contributing more to the upstreams, they already started working more closely with Debian. If, and when they start working on Wayland, it will more than likely end up in the Debian repositories too.

---

### Post by krapp on 2011-05-11
> **cariboo907 said:**
> I wouldn't bet against it, in Mark's keynote speech he stated that Canonical/Ubuntu would start contributing more to the upstreams, they already started working more closely with Debian. If, and when they start working on Wayland, it will more than likely end up in the Debian repositories too.

But does that mean that Debian will default to Wayland?

---

### Post by beew on 2011-05-12
> **kaldor said:**
> The switch to Wayland will be great. I can't wait.

Why would that be great if hardware and software support are not in place?


> 
If that's the case, I'm buying AMD from now on. They're the only graphics maker who put a huge lot of effort into making OSS drivers. Free AMD graphics drivers progress very fast; one Ubuntu release made went from laggy catalyst to smooth OSS. Go figure.
Do the open drivers support hardware acceleration?  The open driver may have gone a long way but they are still not up to the task for 3d performance,--so I read. AMD's closed drivers are pretty terrible from what I gather in the forum, granted, that I never really use AMD so it is all second hand info.(I am now typing from a netbook using AMD card with the open driver, but it is a pretty weak machine so I am not using in for any demanding graphic task anyway)

> 
Sure, you can use Nouveau by then if the NVIDIA people still refuse. But why support a company by buying their stuff when they require reverse engineering?
Or, why bother with paying for a Nvidia card if you cannot get any performance out of it?

---

### Post by beew on 2011-05-12
> **cariboo907 said:**
> I wouldn't bet against it, in Mark's keynote speech he stated that Canonical/Ubuntu would start contributing more to the upstreams, they already started working more closely with Debian. If, and when they start working on Wayland, it will more than likely end up in the Debian repositories too.

 With wayland on major distro doesn't mean they would default to it, and unless Wayland is so great that it manages to replace X entirely in ALL areas of applications I don't see X disappearing any time soon, it is under development with or without wayland  (so it is not like gnome2 biting the dust) so, that means even if Ubuntu is to default to Wayland it will still be ways to swap it out for X. 

 Judging from the way Canonical rushes to release Unity even while it is unfinished , unless there is a major overhaul of their philosophy and release cycle I am pretty sure that they will default Wayland prematurely as well, --with fan boyz making excuses and proclaiming "I love Wayland" while graphic supports  are breaking left and right. So yeah, when Wayland arrives at default I will be very likely to swap it out for x or switch distro if that is not possible.

---

### Post by ZarathustraDK on 2011-05-12
I, for one, am looking forward to Wayland.

I'm sure it'll have its rash of child-afflictions, but reading through its wiki-entry this seems like a necessary step. Getting a flicker/tearing/sub-refreshrate-free experience with X is something I've yet to accomplish as default, and it bugs me more than anything in regards to linux because it's such a big part of the initial impression you'd get as a new user.

If/when Wayland takes off and the drivers are up to snuff, BOOM, optimal configuration-free composited desktop without the need to go hunt for drivers, as a default.

---

### Post by dino99 on 2011-05-12
for the latest UDS decisions/comments (lot of changes decided), see phoronix 
[http://www.phoronix.com/scan.php?page=home](http://www.phoronix.com/scan.php?page=home)

---

### Post by dino99 on 2011-05-12
oops

---

### Post by el_koraco on 2011-05-12
> **beew said:**
> Do the open drivers support hardware acceleration?  The open driver may have gone a long way but they are still not up to the task for 3d performance,--so I read. 

Yes, they do support hw acceleration, via the Mesa library. It varies with GPU's, DE's and the radeon/Galium versions used, though. In general, with newer GPU's, they're much smoother than fgrlx, which has to be intensively tweaked in order to work properly with the desktop, videos and so on. Dunno about games, don't play those myself. Fglrx is also somewhat better than the OSS drivers when it comes to fan control, but not a whole lot (although this is an issue with laptops). The radeon driver in Natty is the best so far. There's a 100 page thread in the Cafe dedicated to the OSS drivers.

---

### Post by NCLI on 2011-05-12
> **beew said:**
> With wayland on major distro doesn't mean they would default to it, and unless Wayland is so great that it manages to replace X entirely in ALL areas of applications I don't see X disappearing any time soon, it is under development with or without wayland  (so it is not like gnome2 biting the dust) so, that means even if Ubuntu is to default to Wayland it will still be ways to swap it out for X. 

 Judging from the way Canonical rushes to release Unity even while it is unfinished , unless there is a major overhaul of their philosophy and release cycle I am pretty sure that they will default Wayland prematurely as well, --with fan boyz making excuses and proclaiming "I love Wayland" while graphic supports  are breaking left and right. So yeah, when Wayland arrives at default I will be very likely to swap it out for x or switch distro if that is not possible.
Wayland will probably be pretty broken when it arrives, yes. It will not, however, be in an LTS release. My money is on 12.10, or maybe 13.04. As long as they don't drop it in an LTS release, I have no problems with things breaking left and right.

---

### Post by kaldor on 2011-05-12
> **beew said:**
> Why would that be great if hardware and software support are not in place?


Do the open drivers support hardware acceleration?  The open driver may have gone a long way but they are still not up to the task for 3d performance,--so I read. AMD's closed drivers are pretty terrible from what I gather in the forum, granted, that I never really use AMD so it is all second hand info.(I am now typing from a netbook using AMD card with the open driver, but it is a pretty weak machine so I am not using in for any demanding graphic task anyway)

Or, why bother with paying for a Nvidia card if you cannot get any performance out of it?

Because, in time, hardware and software support will fall in place. I'm sure Canonical won't jump into Wayland when nothing works.

AMD open source drivers progress very fast. Someone I know is able to play Urban Terror and Minecraft with me without poor performance. They use the latest Free drivers.

Regarding NVIDIA products, I think both points are valid. Why support a company when they refuse to help people make better drivers (AMD and Intel can do it, why can't NVIDIA?) and leave them relying on unofficial stuff that doesn't work that well?

---

