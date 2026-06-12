---
title: "wayland 0.1"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-07-12
I've seen there is a new update for Wayland

wayland (0.1~git20110214.e4762a6a-0ubuntu2) oneiric; urgency=low

  * Simplify debian/rules code
  * Fix almost all lintian complaints (LP: #724608 )
  * Switch to dpkg-source 3.0 (quilt) format


Anyone tried it? Does it already work?

---

### Post by alphacrucis2 on 2011-07-12
> **lucazade said:**
> I've seen there is a new update for Wayland

wayland (0.1~git20110214.e4762a6a-0ubuntu2) oneiric; urgency=low

  * Simplify debian/rules code
  * Fix almost all lintian complaints (LP: #724608 )
  * Switch to dpkg-source 3.0 (quilt) format


Anyone tried it? Does it already work?

Not really game to try it yet but IMO this is a very logical and efficient way of handling graphics. X is well past its use by date so the more quality devs working on Wayland the better.

---

### Post by teh603 on 2011-07-12
> **alphacrucis2 said:**
> Not really game to try it yet but IMO this is a very logical and efficient way of handling graphics. X is well past its use by date so the more quality devs working on Wayland the better.If it needs fixing or replacing, how is X broken? From what I've seen its working fine and uses very few system resources compared to more "modern" software.

---

### Post by philinux on 2011-07-12
> **teh603 said:**
> If it needs fixing or replacing, how is X broken? From what I've seen its working fine and uses very few system resources compared to more "modern" software.

This is a good read.

[http://arstechnica.com/open-source/guides/2011/03/the-linux-graphics-stack-from-x-to-wayland.ars](http://arstechnica.com/open-source/guides/2011/03/the-linux-graphics-stack-from-x-to-wayland.ars)

---

### Post by sanderd17 on 2011-07-12
> **philinux said:**
> This is a good read.

[http://arstechnica.com/open-source/guides/2011/03/the-linux-graphics-stack-from-x-to-wayland.ars](http://arstechnica.com/open-source/guides/2011/03/the-linux-graphics-stack-from-x-to-wayland.ars)

Thanks, a great article. I had read about wayland before, but I have never understood how it would be better than X.

---

### Post by cpatrick08 on 2011-07-12
> **alphacrucis2 said:**
> Not really game to try it yet but IMO this is a very logical and efficient way of handling graphics. X is well past its use by date so the more quality devs working on Wayland the better.
do you know how to switch from x to wayland do you install the package or install it from ppa

---

### Post by CaptainMark on 2011-07-12
good read, damn nvidia for being so anti-open source, i like the way my card performs but theyre just not very 'linux' as a company

---

### Post by teh603 on 2011-07-12
> **CaptainMark said:**
> good read, damn nvidia for being so anti-open source, i like the way my card performs but theyre just not very 'linux' as a companyFrom what I saw, they weren't anti-linux until a certain Mark Shuttleworth decided to use Plymouth as a sledgehammer to try to force them to "improve" their open-source driver. That made them go from dragging their feet, to outright lack of support.

There wasn't anything broken with the old bootsplash either; sure there were a few complaints that theming it was hard, but its not like I've heard about anyone putting theme packages into Plymouth either. Hell, I don't think I've even seen instructions for making them.

> **philinux said:**
> This is a good read.

[http://arstechnica.com/open-source/guides/2011/03/the-linux-graphics-stack-from-x-to-wayland.ars](http://arstechnica.com/open-source/guides/2011/03/the-linux-graphics-stack-from-x-to-wayland.ars)All it says to me is "We need need a more bloated stack so we can have flashier graphics and waste more resources."

---

### Post by buzzmandt on 2011-07-12
> **teh603 said:**
> From what I saw, they weren't anti-linux until a certain Mark Shuttleworth decided to use Plymouth as a sledgehammer to try to force them to "improve" their open-source driver. That made them go from dragging their feet, to outright lack of support.

There wasn't anything broken with the old bootsplash either; sure there were a few complaints that theming it was hard, but its not like I've heard about anyone putting theme packages into Plymouth either. Hell, I don't think I've even seen instructions for making them.

All it says to me is "We need need a more bloated stack so we can have flashier graphics and waste more resources."

I could be wrong but didn't fedora use plymouth before ubuntu?

---

### Post by sgage on 2011-07-12
> **buzzmandt said:**
> I could be wrong but didn't fedora use plymouth before ubuntu?

That was my understanding. Sounds like some revisionist history going on...

---

### Post by EgoGratis on 2011-07-12
>  			 		 	 	 From what I saw, they weren't anti-linux until a certain Mark  Shuttleworth decided to use Plymouth as a sledgehammer to try to force  them to "improve" their open-source driver. That made them go from  dragging their feet, to outright lack of support.

Nvidia doesn't produce open source drivers because of Mark Shuttleworth and Plymouth? I didn't hear about this theory before.

> All it says to me is "We need need a more bloated stack so we can have flashier graphics and waste more resources." 	

Flashier is better then tearing?

Bloated? Wayland is (will be) slimmer than Xorg in amount of code and both will use the same drivers?

Waste of resources or mange it better? More direct access to 3D capabilities of the hardware isn't wasting but improving resource usage?


> Anyone tried it? Does it already work? 	

I would like to know more about Wayland too. I tried to find a blog or something like that from people working on it with updated information and status, but didn't find much.

---

### Post by Starks on 2011-07-12
X defenders are the ones who are in the way of permanent, low-level open-source solutions for Nvidia Optimus, Nvidia Synergy, and AMD Bacon.

It's never going to happen without X Hotplugging or Wayland.

---

### Post by alphacrucis2 on 2011-07-12
I read that "Wayland" versions of GTK and QT are already in progress. Once available, apps using these can bypass X without any changes, so no need to run X as a Wayland client. Intel are behind it big time. The open source AMD and NVidia drivers shouldn't be a problem but getting these guys to make changes to their blobs might be harder. AMD will probably do it then NVidia will follow.

---

### Post by teh603 on 2011-07-12
> **EgoGratis said:**
> Nvidia doesn't produce open source drivers because of Mark Shuttleworth and Plymouth? I didn't hear about this theory before.Lessee, he makes a big announcement about Nvidia's drivers not being up to some standard that he didn't explain (aside from them not being open source, that much I got) at the same time he announces the switch to Plymouth, and then nVidia cans the FOSS driver a few weeks later. Looks like they're connected to me.

> Flashier is better then tearing?Never had issues with that, on any hardware. Not even on some stuff that isn't even supposed to be able to run Linux anymore.
> Bloated? Wayland is (will be) slimmer than Xorg in amount of code and both will use the same drivers?

Waste of resources or mange it better? More direct access to 3D capabilities of the hardware isn't wasting but improving resource usage?The last software that I've seen that wasn't written to overtax existing hardware was GEOS on a C64. Every new release I've seen since then has been more and more bloated, and requires more and more system resources. Which then drives obselescence of older but still-functional hardware. I'll believe Wayland is smaller than X when I see it.

As for anything to do with 3D, point fingers when Nouveau has out-of-the-box 3D support and works as well as the nVidia binary.

---

### Post by buzzmandt on 2011-07-12
I've read the wiki before:
[http://en.wikipedia.org/wiki/Wayland_(display_server_protocol](http://en.wikipedia.org/wiki/Wayland_(display_server_protocol))

> Planned adoption



Wayland demonstration
MeeGo (2010-09-08)
Intel is working on moving MeeGo to Wayland.[13]
Ubuntu (2010-11-04)
Mark Shuttleworth announced plans to eventually replace X with Wayland as the primary Ubuntu display server with their Unity desktop.[14]
Fedora (2010-11-09)
Adam Jackson (ajax) said that Fedora is likely to eventually use Wayland by default, “…because it's a serious win for a lot of things, and the downsides are pretty negligible despite the fear from the peanut gallery.”[15]
KDE
KWin, the KDE window manager, added support for OpenGL ES output.[16] It will ship with KDE SC 4.7. [17] So far KWin has received its initial port to Wayland.[18]
Compiz
Canonical Ltd., owner of Ubuntu, hired Sam Spilsbury,[19] primary Compiz developer. He has been moving Compiz dependencies on X into a plugin. This will make it easier to enable Compiz to become a Wayland display server.[20] Canonical is planning to help port Compiz to OpenGL ES, currently a requirement for Wayland display servers.[21]

---

### Post by buzzmandt on 2011-07-12
and oooohhh but wow, just came across this one  :)  :)
[http://www.markshuttleworth.com/archives/551](http://www.markshuttleworth.com/archives/551)

> The next major transition for Unity will be to deliver it on Wayland, the OpenGL-based display management system. We’d like to embrace Wayland early, as much of the work we’re doing on uTouch and other input systems will be relevant for Wayland and it’s an area we can make a useful contribution to the project.

---

### Post by cariboo on 2011-07-12
> **teh603 said:**
> Lessee, he makes a big announcement about Nvidia's drivers not being up to some standard that he didn't explain (aside from them not being open source, that much I got) at the same time he announces the switch to Plymouth, and then nVidia cans the FOSS driver a few weeks later. Looks like they're connected to me.



Citation please.

---

### Post by inportb on 2011-07-13
> **teh603 said:**
> Lessee, he makes a big announcement about Nvidia's drivers not being up to some standard that he didn't explain (aside from them not being open source, that much I got) at the same time he announces the switch to Plymouth, and then nVidia cans the FOSS driver a few weeks later. Looks like they're connected to me.

Looks like a *post hoc* fallacy to me.

---

### Post by lucazade on 2011-07-13
From what I read also Nvidia binary blob *could* work with Wayland, even without the KMS feature present in opensource drivers, employing instead OpenWF: 

[http://groups.google.com/group/wayland-display-server/browse_thread/thread/c20af3f41244617c](http://groups.google.com/group/wayland-display-server/browse_thread/thread/c20af3f41244617c)

---

### Post by NightwishFan on 2011-07-13
> From what I saw, they weren't anti-linux until a certain Mark Shuttleworth decided to use Plymouth as a sledgehammer to try to force them to "improve" their open-source driver. That made them go from dragging their feet, to outright lack of support.
I am too tempted to jump on the bandwagon and add my :confused: to the list.

---

### Post by CaptainMark on 2011-07-13
Urm were diverging slightly from the original point but i may aswell get my piece in, i cant wait for the day if it ever arrives that nvidia decide theyve been silly and give full support to the open source community but theres not a lot that complaining on forums can do, perhaps we should look into campaigning/petitioning to nvidia. If wayland can improve upon the overcoded behemoth that is X then im game, its in dire need of being updated but its had a good life so cant complain. Theming with plymouth, urrrgh, i used the plymouth manager to change the boot theme a few weeks ago and it added about 30secs to boot time, i dont want to wait that long just so i have a pretty picture to look at, once i used it though there was no way i could find to restore my boot time, even returning to the original theme and removing plymouth manager, a complete reinstall may have been overkill but it prompted my move to 11.10

---

### Post by EgoGratis on 2011-07-13
> From what I read also Nvidia binary blob *could* work with Wayland, even  without the KMS feature present in opensource drivers, employing  instead OpenWF:I did hear on some occasions that close source drivers could work with Wayland, but it is just too technical and i will not try to explain it. As i understand it is possible.

> Lessee, he makes a big announcement about Nvidia's drivers not being up  to some standard that he didn't explain (aside from them not being open  source, that much I got) at the same time he announces the switch to  Plymouth, and then nVidia cans the FOSS driver a few weeks later. Looks  like they're connected to me.I think Nvidia didn't have up to the average user expectation FOSS drivers. This is open source software and i imagine open source drivers are expected by users?

> Never had issues with that, on any hardware. Not even on some stuff that isn't even supposed to be able to run Linux anymore.Issues with tearing are common for Ubuntu users.

> As for anything to do with 3D, point fingers when Nouveau has out-of-the-box 3D support and works as well as the nVidia binary.You can have out-of-the-box 3D support with nouveau graphic driver in OO on some hardware. It only makes sense to have it on all in the future.


And Xorg and Wayland will share the same open source drivers. So there really isn't much of debate if quality FOSS graphic drivers are needed in the future?

---

### Post by smellyman on 2011-07-13
X is keeping DE's from really developing further right now.

[this guy]("http://www.youtube.com/watch?v=9R3n7W_wfzM&feature=related") compiled it back it november or December judging from his comments.  Shows its future potential.  It certainly isn't much now but with all the big players looking into developing it I think it will mature quickly.

---

