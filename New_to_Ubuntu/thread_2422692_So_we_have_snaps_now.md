---
title: "So we have snaps now?"
date: 2019-07-11
forum: New to Ubuntu
---

### Post by bunny9000 on 2019-07-11
Hi All.

Just been reading up on snaps because I've re-entered the land of the Linux.

when I do ```
apt-get install application
``` does that install the application the normal way or using the snap now.

I usually know several of the applications I want to install so just copy the install command from a text file to list off all the applications.

So I guess I need to run the ```
snap install application
``` command according to [https://tutorials.ubuntu.com/tutorial/basic-snap-usage#0](https://tutorials.ubuntu.com/tutorial/basic-snap-usage#0) to install those same applications or is there a divide. Are all applications snap applications now or does the snap version of e.g. libreoffice live alongside the .deb package version?

The software centre exclusivly appears to deal with snaps now? Does synaptic pull apps from the same source.

I'm going to think that snaps are just another version of the same application, such as having a .tar release of an app.

I'm running ubuntu - mate and I think I answered most of my own questions as I wrote the thread. :P

---

### Post by deadflowr on 2019-07-11
>  Are all applications snap applications now or does the snap version of e.g. libreoffice live alongside the .deb package version?
It's both deb and snap, currently.
snaps and debs can be installed at the same time.

The only package I can think of off the top which is moving from deb to snap only is chromium, and that has quite few users up in arms.
(Here's a link to a on-going thread on the transition: 
[https://community.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179]("https://community.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179")
> The software centre exclusivly appears to deal with snaps now? Does synaptic pull apps from the same source.
Software store deals with all, deb, snap, and flatpak (if flatpak utilities are installed on the system.)

Synaptic only deals with debs.
And I doubt that will change any time soon.

---

### Post by Impavidus on 2019-07-12
deb and snap live side by side now. The software store (or whatever it's called now) deals with both snap and deb, so you have to be careful which version of a package you install. apt-get (or apt, which is preferred these days) deals with deb only, as does synaptic. I've got no snaps on my system at the moment.

---

### Post by again? on 2019-07-12
If you you use the software store to install applications, check the details section and it will show
the source.
At this stage I don't think there is a lot of snaps.
eg vlc has a deb and a snap.
[ATTACH=CONFIG]283615[/ATTACH] [ATTACH=CONFIG]283616[/ATTACH]

I can see the point of snap packages for third party applications but don't see why some 
snaps are being used in the default install.
Snap packages are relatively large and are noticeably slow to initiate but may be a more up to date version than default debs.
I remove snapd and the software store and only use apt and synaptic.

---

### Post by grahammechanical on 2019-07-13
I have not found Ubuntu Software all that useful for finding snaps. Ubuntu now has a snap only software store. It is not installed by default

[https://snapcraft.io/snap-store](https://snapcraft.io/snap-store)

Regards.

---

### Post by TheFu on 2019-07-13
There are reasons to use snaps.
There are reasons to avoid snaps.

Snaps are self-contained virtual sandboxes.  That means they include dependencies normally that would be installed already on the system.  This means they use more RAM, more disk, and are slower to start.  If you have fast NVMe storage and 64G of RAM, that probably doesn't matter to you.  But, if you are on a 2GB netbook from 2010, snaps are your enemy.  You don't want them. EVER.  
That sandbox brings additional issues with programs designed to work with other programs as "helpers", so if your email thick client is Thunderbird and you want to automatically open attachment documents, the snap sandbox will prevent that.  This is good from a security standpoint, but bad from a convenience standpoint.

I wanted to use a video editor.  The Snap for it was almost 900MB in size.  The program alone was 32MB in size.  So, would you rather load 32MB of program into RAM or almost 1GB into RAM to perform video editing?

Some teams have gone snap-happy for reasons that don't make sense to me.  A clock app or a calculator app have no need to be "contained" in a sandbox and bring 500MB of dependencies into RAM just to run a 3 MB application that doesn't do high-risk behaviors.  When was the last time **anyone** got hacked running a calculator?  OTOH, an email program and web browser ARE definitely high risk applications.  As painful as it might be, having a snap for those even if they don't work with helper tools, is something I'd agree makes sense.  But you and I have different needs, different security comforts, and different mitigations for our security.  Having the choice is what I'd like and I'd much prefer if snaps weren't the default, rather they should be the 2nd option.  

Everyone has different needs. Canonical has repeatedly decided that "the default" is right well before it is.  I think this is another one of those mistakes.

IMHO.

So, to avoid the issues, like VLC addons not always working because VLC is in a snap sandbox, I've decided to remove the snap infrastructure from my systems and use a different sandboxing tool for my high-risk needs.

YMMV.

---

### Post by VMC on 2019-07-13
If I lose *apt* ability then I will loose Ubuntu. I realize its a ways off, so I need to start looking for alternatives. I dislike snaps and its the first to be removed. I hear Chromium can only be installed using snaps.

---

### Post by TheFu on 2019-07-13
> **VMC said:**
> If I lose *apt* ability then I will loose Ubuntu. I realize its a ways off, so I need to start looking for alternatives. I dislike snaps and its the first to be removed. I hear Chromium can only be installed using snaps.

```
$ dpkg -l |grep chromi
ii  chromium-browser                            74.0.3729.169-0ubuntu0.16.04.1        
```

Appears not to be true, at least for 16.04.  If you remove all the snap infra, I bet there is still a chromium-browser package.

---

### Post by cruzer001 on 2019-07-13
> **TheFu said:**
> Appears not to be true, at least for 16.04.  If you remove all the snap infra, I bet there is still a chromium-browser package.
And even if it was true

[https://pkgs.org/download/chromium-browser](https://pkgs.org/download/chromium-browser)

---

### Post by PaulW2U on 2019-07-13
> **VMC said:**
> I hear Chromium can only be installed using snaps.
In the current development release (19.10), yes that is true. Other releases to follow once a few minor issues have been resolved.

Quoting from: [Call for testing: chromium-browser deb to snap transition]("https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179")
> In a first step, the transition will be happening exclusively for Ubuntu 19.10 (Eoan Ermine) users, and once I’m confident it is rock-solid it will be rolled out to stable releases, starting with disco and then the LTSes.

---

### Post by bunny9000 on 2019-07-14
Hi folks.

Thanks for the fantastic replies.This clears a lot of things up. I guess for now I'll carry on as normal :(

---

