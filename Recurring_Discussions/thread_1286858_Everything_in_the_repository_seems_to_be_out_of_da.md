---
title: "Everything in the repository seems to be out of date."
date: 2009-10-09
forum: Recurring Discussions
---

### Post by Isaacgallegos on 2009-10-09
I'm very new to Ubuntu but have been doing my best to get used to it. However it seems that every time I get something from the Add/Remove installation system or Synaptic Package Manager I always end up removing it and having to manually download the newer version of what ever I just got through a website. 
Is there some way I can just add a big third party software source that will have lots updated stuff?

---

### Post by fabdango on 2009-10-09
What software do you mean? Like Firefox and that stuff? That's because of the distro's policies.

In most cases you can add PPAs from [Launchpad]("http://launchpad.net/").

---

### Post by snowpine on 2009-10-09
Hi there, it would be easier to answer your question if you gave specific examples of particular applications. :)

In general, the way things work in Ubuntu is as follows: When a new Ubuntu release comes out (twice a year, April and October), all of the applications are "frozen" at their current version. You only get minor updates like bug fixes and security patches. Major updates (for example going from Firefox 3.0 to 3.5) occur when you upgrade to the next release (next one being 9.10 Karmic at the end of this month).

Ubuntu is designed this way so your system is more stable and reliable. Every version of every application is tested to work well together. Your apps might be a few months out of date, but they will be well tested and stable.

You can of course upgrade to newer, unsupported versions of an application (for example by downloading the latest Firefox from the Mozilla site, or using a Launchpad PPA), but that is kind of a "Windows way" of doing things that compromises the stability of your system.

I hope that answers your very vague question. :)

---

### Post by Isaacgallegos on 2009-10-09
> **snowpine said:**
> Hi there, it would be easier to answer your question if you gave specific examples of particular applications. :)
Inkscape, Anki, Nexuiz (game), Audacity, Wine, and the list goes on. 
I'm not trying to be difficult but if I type **sudo apt-get install vlc** I know it's going to be an old version of the vlc player. If I go to the "add/remove applications" window the same thing will occur. The Package Manager dose the same. 

Ubuntu has a great idea when it comes to getting software. And it's easier! But it's more work when it's not the latest versions. There's got to be away to fix this from my end. Aside from going the developers websites.

---

### Post by SuperSonic4 on 2009-10-09
Yes, you can use a rolling release distro.

Arch is the most common around here but it takes patience to set up.

---

### Post by snowpine on 2009-10-09
> **Isaacgallegos said:**
> Inkscape, Anki, Nexuiz (game), Audacity, Wine, and the list goes on. 
I'm not trying to be difficult but if I type **sudo apt-get install vlc** I know it's going to be an old version of the vlc player. If I go to the "add/remove applications" window the same thing will occur. The Package Manager dose the same. 

Ubuntu has a great idea when it comes to getting software. And it's easier! But it's more work when it's not the latest versions. There's got to be away to fix this from my end. Aside from going the developers websites.

Hi Isaac, there is no "fix" because it's not broken. :) Ubuntu is designed so that every application is between zero and six months old. For example, the latest stable VLC is 1.0.2, and that's the version that will be included in 9.10 Karmic Koala (in a couple of weeks). Right now is the worst time, because it's right before the big new release. You can install Karmic right now, if you're interested in testing bugs in the beta release. ;)

---

### Post by Isaacgallegos on 2009-10-09
> **SuperSonic4 said:**
> Yes, you can use a rolling release distro.

Arch is the most common around here but it takes patience to set up.

It looks like only the OS gets constant updates and not all the software installed.

---

### Post by Isaacgallegos on 2009-10-09
> **snowpine said:**
> Hi Isaac, there is no "fix" because it's not broken. :) Ubuntu is designed so that every application is between zero and six months old. For example, the latest stable VLC is 1.0.2, and that's the version that will be included in 9.10 Karmic Koala (in a couple of weeks). Right now is the worst time, because it's right before the big new release. You can install Karmic right now, if you're interested in testing bugs in the beta release. ;)
Okie dokie. Thanks.

---

### Post by SuperSonic4 on 2009-10-09
> **Isaacgallegos said:**
> It looks like only the OS gets constant updates and not all the software installed.



Yeah that's one of the features of ubuntu. I prefer to sacrifice some stability for the latest stuff (often beta software) so to me this is a flaw in ubuntu. But to others who want 5 9's uptime this is a good thing.

---

### Post by StuartN on 2009-10-09
> **Isaacgallegos said:**
> Inkscape, Anki, Nexuiz (game), Audacity, Wine, and the list goes on.

Most of my work is done on releases from the repositories, which are stable and well supported on the forums. There are more recent versions of every package I use, but the change-lists don't mention a single feature I need.

Games and fun packages have recent releases I want to try and I have never had a problem downloading and installing them.

---

### Post by slakkie on 2009-10-09
Run Debian unstable if you want the latest and greatest :)

I agree with you when you look at LTS versions of Ubuntu. I would like to see more use of the -backports repo's with backported software from intrepid/jaunty/karmic.
Keep major compontents like the toolchain stable, but backport the rest.

---

### Post by mgol on 2009-10-09
> **slakkie said:**
> I would like to see more use of the -backports repo's with backported software from intrepid/jaunty/karmic.
Keep major compontents like the toolchain stable, but backport the rest.
I share Your opinion - stuff like Xorg, kernel version etc. should be frozen, but there is no such need for user apps (Firefox, OpenOffice.org etc.). I suppose, though, that Ubuntu is lacking in developers for such a thing.

---

### Post by Vaphell on 2009-10-09
well, that's what PPAs are for if you want newest shiniest stuff
you subscribe to the PPAs of choice and software you are interested in gets updated in a standard way.

---

### Post by snowpine on 2009-10-09
> **mgol said:**
> I share Your opinion - stuff like Xorg, kernel version etc. should be frozen, but there is no such need for user apps (Firefox, OpenOffice.org etc.). I suppose, though, that Ubuntu is lacking in developers for such a thing.

I don't think it's a lack of developers. It wouldn't really be any extra work to open the floodgates and use the "upstream" version of Firefox, OpenOffice, etc. But they choose not to do it that way for some reason. ;)

---

### Post by Vaphell on 2009-10-09
they care about the user experience - they shrink the set of possible configurations to iron the bumps out. If it was possible to have 5 different versions and we are talking about hundreds of apps here - impossible to control and squash bugs.
Majority wants seamless experience, especially when using 'entry level' linux distro. If you want bleeding edge you have to use external app sources (ppa, deb files)

---

### Post by slakkie on 2009-10-09
> **Vaphell said:**
> well, that's what PPAs are for if you want newest shiniest stuff
you subscribe to the PPAs of choice and software you are interested in gets updated in a standard way.

I'm talking about LTS releases, not regular releases. I don't run PPA's on my LTS installs because I don't trust them enough. Getting some more up to date applications from the official archives would benefit LTS users a lot (IMO). 

For example, with opencsw on Solaris, they have two repo's: stable, unstable. When a package is in unstable for 6 months and has not received critical bugs, they push it to stable. We use opencsw at work for all of our Solaris boxes (our main OS). We keep the OS at one version, but upgrade applications where needed. This is something I would like to see with LTS versions of Ubuntu. Maybe not every 6 months, but at every point release push packages from the current release to -backports in LTS versions. Although every 6 months is the same as the normal release cycle, so it could be possible..

---

### Post by Isaacgallegos on 2009-10-09
I'll say one more thing. I've almost stopped using the repository for most of my applications because of how many are downloaded and installed manually.  And a problem I'm now having is some of these programs don't have good un-install scripts. So this is major reason why I would love everything to be fed through the Add/remove manager or the Package manager.

---

### Post by aysiu on 2009-10-09
You really have only two options in this particular scenario:

1. Work with Ubuntu's release model (possibly supplemented with PPA repositories)

2. Use a rolling-release distro (PCLinuxOS, Debian, Arch)

I can't understand the need to get the absolute latest software. I can wait six months to get it all updated instead of updated one at a time. Not everyone's like me, though, which is why rolling releases are great for other people (people like you).

---

### Post by hoppipolla on 2009-10-09
> **Isaacgallegos said:**
> I'm very new to Ubuntu but have been doing my best to get used to it. However it seems that every time I get something from the Add/Remove installation system or Synaptic Package Manager I always end up removing it and having to manually download the newer version of what ever I just got through a website. 
Is there some way I can just add a big third party software source that will have lots updated stuff?

I wanted to start this myself! A new repository to give people newer versions of popular software :)

I might do it sometime!

---

### Post by SunnyRabbiera on 2009-10-09
> **Isaacgallegos said:**
> I'll say one more thing. I've almost stopped using the repository for most of my applications because of how many are downloaded and installed manually.  And a problem I'm now having is some of these programs don't have good un-install scripts. So this is major reason why I would love everything to be fed through the Add/remove manager or the Package manager.

The thing is sometimes latest isnt always the greatest, sometimes newer releases of software can be very unstable and can cause systemwide issues.
I have seen it happen
From a windows user perspective Ubuntu's software policies are silly, you are so used to updating everything in windows.
But no, its all for stability.
Stuff like firefox 3.5 has been reported to be very unstable for some folk, even if the newer version might have feature a and feature 2 it might not be all that stable.

For a more "windows" feel you might want to try openSUSE, for new users I cannot suggest arch as its complicated to set up.

---

### Post by aysiu on 2009-10-09
> **SunnyRabbiera said:**
> 
From a windows user perspective Ubuntu's software policies are silly, you are so used to updating everything in windows. It really depends on the Windows user. If you're the kind of Windows user (what I like to call a "Windows power user") other Windows users come to for help with Windows problems, then, yes, you probably like updating software individually and the minute that newer version becomes available.

If you're the kind of Windows user who doesn't want to mess with the computer because you're worried it's going to break if you change *anything*, then actually the Ubuntu model (especially an LTS release) makes far more sense.

---

