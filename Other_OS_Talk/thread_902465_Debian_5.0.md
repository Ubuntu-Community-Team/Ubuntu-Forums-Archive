---
title: "Debian 5.0"
date: 2008-08-27
forum: Other OS Talk
---

### Post by phidia on 2008-08-27
It's out now (beta) and it's live now too.
I'm downloading it right now. Has anyone tried this and if so how is it?
I'm sort of excited to find out!

[Here's]("http://cdimage.debian.org/cdimage/lenny_live_beta1/") a link to the isos.

---

### Post by Bachstelze on 2008-08-27
Okay, now we can expect a release for Christmas (2009) :p

---

### Post by phidia on 2008-08-27
Without Debian doing the heavy lifting we'd all be using stone tablets, or ok windows. :lolflag:

---

### Post by jwaiwit on 2008-08-27
I confuse something about Ubuntu is base on debian. Once Debian is updated Ubuntu will or not? Or it's completely seperate from each other.

---

### Post by phidia on 2008-08-27
> **jwaiwit said:**
> I confuse something about Ubuntu is base on debian. Once Debian is updated Ubuntu will or not? Or it's completely seperate from each other.

As I understand it Ubuntu is a mix of debian testing and unstable. 
They are separate, ubuntu and debian, from one another.

---

### Post by NullHead on 2008-08-27
[quote=Distrowatch.com]Daniel Baumann has announced the availability of the first set of live CD images for Debian GNU/Linux 5.0 "Lenny", complete with a hard disk installer and available in three desktop variants (GNOME, KDE and Xfce): "The Debian Live team is pleased to announce the first beta of Debian Lenny's Live images. This is the first official release of Debian Live and the whole team has been working hard during the past **2.5 years** to make Debian's own live systems become a reality. Main features: 100% Debian; Live Magic - an GUI front-end around the live-helper scripts, offering a subset of the features of live-helper in an easy-to-use graphical user interface; Live Installer - a special udeb for the Debian Installer that installs the system from the live image." Read the full release announcement for more details and known issues. Download (MD5): debian-live-lenny-i386-gnome-desktop.iso (733MB), debian-live-lenny-i386-kde-desktop.iso (702MB), debian-live-lenny-i386-xfce-desktop.iso (503MB). ISO images for the amd64 architecture are also available.[/quote]

I'm not sure if their development cycle is a good thing or a bad one ... these people take unnaturally long periods of time to develop. 

Anyways, the Debian team needs one big "YAY" from us and we all should download the isos and install 'em into virtual machines.

---

### Post by Antman on 2008-08-27
> **HymnToLife said:**
> Okay, now we can expect a release for Christmas (2009) :p
:lolflag:

---

### Post by ezsit on 2008-08-27
> Originally Posted by jwaiwit View Post
I confuse something about Ubuntu is base on debian. Once Debian is updated Ubuntu will or not? Or it's completely seperate from each other.

> As I understand it Ubuntu is a mix of debian testing and unstable. They are separate, ubuntu and debian, from one another.

Ubuntu is built from the Debian unstable repositories (Sid). So a release of Debian Stable (what the testing repository will become once Debian releases Lenny) is not directly affecting Ubuntu development.

However, the Debian community builds and maintains 98% of the  codebase that Ubuntu relies upon, so to say that Debian and Ubuntu are separate is a bit misleading. The release of Debian Stable does not affect Ubuntu, but the work of the Debian community is what makes Ubuntu possible. If it were not for the hundreds (maybe thousands) of Debian contributors doing their mostly thankless jobs, Ubuntu would not exist.

The Debian community and project value stability above almost anything else, so Debian developers will take the open source code from around the world and compile, package, and test the code for a couple of years. As the code is tested and confirmed to be stable, it is moved from the unstable branch (Sid) to the testing branch (now Lenny), and finally, when all the code is deemed stable and the installer is finalized, a snapshot is taken and that snapshot becomes the stable release. 

The unstable branch sees changes hour to hour, the testing branch sees changes every few days or weeks sometimes, and the stable branch only gets security updates so it changes only when completely necessary. This is where the branches get their names, unstable changes frequently, so hence it is unstable. The testing branch changes less frequently and serves as the testing bed for the next stable release. The stable branch stays pretty stable since it does not change that often.

The Ubuntu folks take a look at the unstable repository and take code from that branch primarily. Over the course of six months, Ubuntu will take code from unstable and test the the code until they come up with a mix that meets their standards and goals. Ubuntu will test packages, add and remove as necessary, until they arrive at the next Ubuntu release.

I hope this makes the relationship a bit clearer.

---

### Post by mthei on 2008-08-27
I've been using Lenny for two weeks now. Coming from Fedora, it's a bit of a change. Most of the software is the same for now. I'm very surprised at how much lighter it is compared to Fedora, OpenSUSE and Ubuntu (the only other Gnome distros I've tried), all of which I'd remove unwanted apps and disabling services. Fedora and Ubuntu would get down to 140mb, while Debian ranges from 100 - 120mb, which for a full Gnome desktop, is pretty impressive.
It runs very well, and is as fast and quiet as Fedora was for me. It took a while for me to get it to resume properly (it used to stretch my resolution) but once that was done, I was very pleased.

---

### Post by cmay on 2008-08-27
thanks for the good news.
i am gonna download this right away.
i use debian testing but i cant quit figure out what is stable testing and unstable.
 thanks for the tip; :)

---

### Post by SunnyRabbiera on 2008-08-27
So debian finally has a live installer then?
Awesome!

---

### Post by tdrusk on 2008-08-27
> **mthei said:**
> I've been using Lenny for two weeks now. Coming from Fedora, it's a bit of a change. Most of the software is the same for now. I'm very surprised at how much lighter it is compared to Fedora, OpenSUSE and Ubuntu (the only other Gnome distros I've tried), all of which I'd remove unwanted apps and disabling services. Fedora and Ubuntu would get down to 140mb, while Debian ranges from 100 - 120mb, which for a full Gnome desktop, is pretty impressive.
It runs very well, and is as fast and quiet as Fedora was for me. It took a while for me to get it to resume properly (it used to stretch my resolution) but once that was done, I was very pleased.
How did you fix the resolution problem?

---

### Post by swoll1980 on 2008-08-27
> **phidia said:**
> It's out now (beta) and it's live now too.
I'm downloading it right now. Has anyone tried this and if so how is it?
I'm sort of excited to find out!

[Here's]("http://cdimage.debian.org/cdimage/lenny_live_beta1/") a link to the isos.

If you plan on 3d acceleration with a NVIDIA card there seems to be a huge issue with Debian's kernels, and the NVIDIA drivers not installing properly. The drivers are not compatible with xen kernels, and although Debian provides non xen kernels they put code in them that makes them xen like in some way, and difficult to deal with.

---

### Post by mthei on 2008-08-27
> **tdrusk said:**
> How did you fix the resolution problem?

It's only a temporary fix for now (although there was an ACPI-Support update today, so maybe the problem as been taken care of?), you have to edit the file at /usr/lib/pm-utils/module.d/uswsusp and make the following changes:
The section that says 
> OPTS=""
becomes
> OPTS="-f -p -m"

And
> do_suspend()
{
	get_quirks
	s2ram --force $OPTS
}
becomes
> do_suspend()
{
	get_quirks
	s2ram $OPTS
}

I had found the above somewhere on the Debian forums. It's only temporary, as apparently an update to pm-utils can overwrite this, in which case you'd have to make the changes again.

---

### Post by kerry_s on 2008-08-27
i'll just wait till it moves to stable, i'm running etch right now, i've already changed all "etch" to "stable" in my /etc/apt/sources.list so it should be a easy upgrade. :)

---

### Post by phidia on 2008-08-27
> **swoll1980 said:**
> If you plan on 3d acceleration with a NVIDIA card there seems to be a huge issue with Debian's kernels, and the NVIDIA drivers not installing properly. The drivers are not compatible with xen kernels, and although Debian provides non xen kernels they put code in them that makes them xen like in some way, and difficult to deal with.

I agree that debian isn't proprietary driver friendly-that's sort of a given with debian's software philosophy. 

There actually is a deb way to install the drivers which I did once on my desktop but that installs a really old version. I found I like to just grab the latest nvidia driver and use their installer-that method works fine for me, or it did with 4.0. 

Maybe I'm not understanding all the ramifications of the xen kernel though and I haven't had time to try the iso-just burned it.

---

### Post by karellen on 2008-08-27
that's good news. finally Debian has a live cd

---

### Post by swoll1980 on 2008-08-27
> **phidia said:**
> that method works fine for me, or it did with 4.0. 



yes this is a 5.0 problem, and because of the philosophy as you stated earlier they have no intentions of fixing it. From what I have learned of it so far it would seem the only way to install nvidia's drivers would be to  compile a new kernel from source

---

### Post by tel93 on 2008-08-27
> **phidia said:**
> It's out now (beta) and it's live now too.
I'm downloading it right now. Has anyone tried this and if so how is it?
I'm sort of excited to find out!

[Here's]("http://cdimage.debian.org/cdimage/lenny_live_beta1/") a link to the isos.

I've been using lenny for a long time. It's sweet!

---

### Post by Seventh Reign on 2008-08-27
Anyone else having issues with 5.0 erroring out at the "Press F1 For Help or ENTER to" .. and thats all it shows before it reboots .. over and over and over again.

2 DVD's for Gnome and 2 CD's for xfce wasted :-(

---

### Post by swoll1980 on 2008-08-27
> **Seventh Reign said:**
> Anyone else having issues with 5.0 erroring out at the "Press F1 For Help or ENTER to" .. and thats all it shows before it reboots .. over and over and over again.

2 DVD's for Gnome and 2 CD's for xfce wasted :-(

not to mention the countless hours of download time :( this is how I felt when I had the NVIDIA issue.

---

### Post by cardinals_fan on 2008-08-27
> **phidia said:**
> Without Debian doing the heavy lifting we'd all be using stone tablets, or ok windows. :lolflag:
Eh?

---

### Post by Seventh Reign on 2008-08-27
Oh I have cable, it takes like 10 minutes to download em LOL.

Only problem is it basically freezes my browsers while they're downloading.

---

### Post by exploder on 2008-08-27
Seventh Reign, I also get, "Press F1 For Help or ENTER to" and then a snowy looking screen...

---

### Post by Seventh Reign on 2008-08-27
I get the Snowy screen on Gnome.  but not on xfce.  Sometimes I can see part of the error message through the snow, and sometimes I cant.

---

### Post by phidia on 2008-08-27
> Linux debian 2.6.25-2-amd64 #1 SMP Mon Jul 14 11:05:23 UTC 2008 x86_64 GNU/Linux

I'm running it live right now. You do not need to use a dvd for the 715MB iso just use the overburn flag with wodim (see man wodim) from CLI.
It looks good too!

---

### Post by Mizzou_Engineer on 2008-08-27
> **phidia said:**
> It's out now (beta) and it's live now too.
I'm downloading it right now. Has anyone tried this and if so how is it?
I'm sort of excited to find out!

[Here's]("http://cdimage.debian.org/cdimage/lenny_live_beta1/") a link to the isos.

I'm running Debian 5.0 on all of my machines. It's about as good of a release as I've used.

---

### Post by kagashe on 2008-08-28
> **phidia said:**
> It's out now (beta) and it's live now too.
I'm downloading it right now. Has anyone tried this and if so how is it?
I'm sort of excited to find out!

[Here's]("http://cdimage.debian.org/cdimage/lenny_live_beta1/") a link to the isos.[Debian 5.0 beta2]("http://www.debian.org/devel/debian-installer/") was released on 9th June.

Debian Live is a separate project in Debian and they have released this beta1 on Aug 27. This beta1 is only a Live CD and does not include Live Installer which might be included in next beta (beta2) expected in about two weeks. There may be a third beta before RC.

kagashe

---

### Post by Seventh Reign on 2008-08-28
32bit Gnome is 732mbs not 716.  This Motherboard maxes out at 2gigs of RAM so there's no point in trying a 64bit system here.

---

### Post by phidia on 2008-08-28
From Distrowatch:
> "The Debian Live team is pleased to announce the first beta of Debian Lenny's Live images. This is the first official release of Debian Live and the whole team has been working hard during the past 2.5 years to make Debian's own live systems become a reality. Main features: 100% Debian; Live Magic - a GUI front-end around the live-helper scripts, offering a subset of the features of live-helper in an easy-to-use graphical user interface; Live Installer - _a special udeb for the Debian Installer that installs the system from the live image._" Read the full release announcement for more details and known issues. 

> No live-installer included yet (if you wish to test live-installer earlier, please build it yourself). 

---

### Post by phidia on 2008-08-28
Maybe the "Know issues & Plans" sections from [here]("http://blog.daniel-baumann.ch/2008/08/27#20080827_debian-live-lenny-beta1") will be helpful?

> Known issues in this release

    * The prebuilt images for gnome-desktop and kde-desktop are a bit too big to fit on a CD. Although the automatic installation of Recommends was disabled to build the images, they are still too big. This will need further tweaking as they are supposed to fit with the next beta.

    * The rescue flavour, containing system rescue and forensic related packages, is missing in this beta release.

    * There will be a DVD image with the next beta that includes all three desktop environments so that you can choose at boot time which system you would like to start.

    * Due to time constraints, the prebuilt images for Beta1 are only covering i386 and amd64; with the next beta, powerpc and sparc will follow (if you wish to test these architectures earlier, please build them yourself).

    * The new desktop artwork is not yet included.

    * The syslinux menu is still the old, prompt-based one. A freshly made new syslinux vgamenu using the official lenny desktop artwork is on the way (the same as d-i media will use in Lenny).

    * No live-installer included yet (if you wish to test live-installer earlier, please build it yourself).

    * No win32-loader included yet.

    * Sid packages used - At the time of building the live images, both live-helper 1.0.0-1 and live-initramfs 1.139.1-1 from sid were used. Since the latter has not yet migrated to testing, it was included manually as a local package. This is undesirable, as the release is supposed to be self-contained - however, it is just a convenient workaround as both were granted freeze exception and will migrate soon.

Plans for next Beta release

We are looking forward to upload Beta2 in about two weeks from now (maybefollowed by a third beta) with one final RC after that which should be identical to the final release.

Some more details about the open things we would like to address in Beta2 and later can be found at the wiki page.

The Debian Live team is still looking for more contributors for new features (post-lenny, though) as well as documentation writers for the manual (always). If you care about live systems, please join and help! 

---

### Post by tdrusk on 2008-08-28
I did not want to make a new thread for this, although the final will deserve one, but there is a Mepis beta out also.

[http://www.mepis.org/node/14194](http://www.mepis.org/node/14194)

---

### Post by Antman on 2008-08-28
> **Seventh Reign said:**
> Oh I have cable, it takes like 10 minutes to download em LOL.

Only problem is it basically freezes my browsers while they're downloading.
From a termial, just use [WGET]("http://en.wikipedia.org/wiki/Wget"). It's better for downloading large isos than a browser.
```
wget http://www.example.com/Debian.iso

```

---

### Post by Antman on 2008-08-28
Duplicate post

---

### Post by init1 on 2008-08-28
> **NullHead said:**
> I'm not sure if their development cycle is a good thing or a bad one ... these people take unnaturally long periods of time to develop. 

Anyways, the Debian team needs one big "YAY" from us and we all should download the isos and install 'em into virtual machines.
Yeah, but when a release does come, it tends to be extremely stable.

---

### Post by NullHead on 2008-08-29
> **init1 said:**
> Yeah, but when a release does come, it tends to be extremely stable.

You're very correct, my server has never once crashed or had any reason for me to restart it after I installed debian on it. 

I restarted it once in a wile just for goo measure and I did it once to boot into my new custom kernel, but other than that it's really stable. 

I remember when I had ubuntu server on there, my IRC bot would crash every 20 minuets, I run the same exact IRC bot on debain etch and it's never ever crashed .. not once.

---

### Post by wolfen69 on 2008-08-29
the live cd would not load on my pc. i can get to the initial boot screen, but it would just reboot my computer. only cd that's ever done that. strange. i guess i'll wait until it's finished.

---

