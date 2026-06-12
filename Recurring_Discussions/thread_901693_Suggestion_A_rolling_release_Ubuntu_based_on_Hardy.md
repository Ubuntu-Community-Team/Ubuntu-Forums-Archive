---
title: "Suggestion: A rolling release Ubuntu based on Hardy?"
date: 2008-08-26
forum: Recurring Discussions
---

### Post by ljpp on 2008-08-26
First of all I have to emphasize that I am not a developer and not even very competent with Linux. I know my around the Linux desktops, but don't know too much about the stuff happing under the hood. But still, I would like to present this idea, that seems to come up Ubuntu forum discussions every now and then.

With the relesae of Hardy LTS, the time is right for a community driven rolling release Ubuntu!(?)

I can't stop admiring what 'Textar' has achieved with PCLinuxOS, which is a fork of Mandriva. Especially the 2008 MiniMe edition is damn right amazing. The problem is though the small community around PCLOS, even though it has gained a nice number of members rather quickly. Also the package selection of PCLOS, or Mandriva, is somewhat smaller than with Ubuntu/Debian. But imagine what could be achieved in a similar project, using Ubuntu's recent LTS release and driven by the huge Ubuntu community?

There's exactly two things I don't like about Ubuntu. The software quality of releases has been less than great for the last few cycles - sure, the releases do mature as patches and fixes are coming in, but at the time of the release there has been quite a bit of bugs in recent Ubuntus. On the other hand the life-cycle of regular releases is too short, and there is not a good availability of upgraded packages/apps even for the LTS releases.

So wouldn't it make sense to take Hardy as a base, and start rolling upgraded packages/apps on top of that? PCLOS has maintained a rather conservative policy in package updates, which has resulted in a distro that is not bleeding edge, but reasonably up-to-date and quite stable. With the base of Hardy, patches coming from Ubuntu, key apps backported from future releases I am sure that even better results would be achieved. The Ubuntu userbase and community is huge, so I am confident that there would be a sufficient amount of contributors and testers for maintaining a high quality rolling update relase at least through the life cycle of Hardy and further. After all Ubuntu already offers a great base systems so there would not be a huge need of core changes, rather just a refreshed selection of key packages/apps.

Hopefully I am not way off here, and I am not sure if this topic has been previously covered, but in my point of view here would be an excellent opportunity come up with a distro that combines the goodies of Debian/Ubuntu base and PCLOS/conservative rolling release update policy.

What do you think?

---

### Post by Tom--d on 2008-08-26
I can see where you are coming from here.

But Backports is good, I think. Maybe the backports could be updated a bit more.
Do you want to update everyday?

---

### Post by tom66 on 2008-08-26
Could someone explain what a rolling release is to me? I too am a bit of a newbie to Linux.

---

### Post by fwojciec on 2008-08-26
[QUOTE=tom66]Could someone explain what a rolling release is to me? I too am a bit of a newbie to Linux. [/QUOTE]

In a rolling release model all packages which comprise the system are constantly updated to most recent versions.  You install it once and then you never have to update to a newer release.  Downloadable "releases" (CD ISOs) are basically just snapshots of the state of the repositories at any given moment.

Ubuntu, for example, works differently -- it uses a 6 months release cycle so a new version of Ubuntu is made available every 6 months (i.e. "Edgy Eft", "Feisty Fawn", "Hardy Heron") and so every 6 months users are asked to perform an upgrade to the current release.  Each particular release has updates (security fixes and such), but the core of the system remains essentially unchanged throughout the lifetime of a release.

Each model has its own advantages and disadvantages.

---

### Post by Lostincyberspace on 2008-08-26
I love the Idea It would be great to have a rolling update. Grumpy Groundhog actual release.


> **Tom--d said:**
> I can see where you are coming from here.

But Backports is good, I think. Maybe the backports could be updated a bit more.
Do you want to update everyday?
No, I want to update every Hour!

---

### Post by aysiu on 2008-08-26
Didn't Linux Mint (which is based on Ubuntu) recently move to a rolling release schedule?

---

### Post by _sAm_ on 2008-08-26
What is the disadvantages with a rolling release - and why didn't Canonical go for this solution?

And last; you can run sudo apt-get update and upgrade. Don't the upgrade in fact upgrade to latest version for some packages? If so, what difference this from a rolling release? 

Thanks for answers

---

### Post by bruce89 on 2008-08-26
> **_sAm_ said:**
> What is the disadvantages with a rolling release - and why didn't Canonical go for this solution?

New packages = new bugs.

> **_sAm_ said:**
> And last; you can run sudo apt-get update and upgrade. Don't the upgrade in fact upgrade to latest version for some packages? If so, what difference this from a rolling release? 

The latest packages for that version will be upgraded. New upstream versions aren't usually packaged for stable releases however (in fact, never).

---

### Post by fwojciec on 2008-08-26
From the perspective of Canonical, which is a company that makes money by providing paid support, rolling release would be disadvantageous as it tends to be, relatively speaking, more unpredictable and more difficult to provide support for.

---

### Post by bruce89 on 2008-08-26
> **fwojciec said:**
> From the perspective of Canonical, which is a company that makes money by providing paid support, rolling release would be disadvantageous as it tends to be, relatively speaking, more unpredictable and more difficult to provide support for.

Ah, but there'd be more bugs.

---

### Post by fwojciec on 2008-08-26
> **bruce89 said:**
> Ah, but there'd be more bugs.

Precisely -- especially considering the added complexity of Ubuntu which is required to achieve the "just works" effect.

---

### Post by jgrabham on 2008-08-26
> **aysiu said:**
> Didn't Linux Mint (which is based on Ubuntu) recently move to a rolling release schedule?

Possibly, but IIRC the newest version of mint is based on 7.10 (unless they've released a new version since I last checked).

---

### Post by the yawner on 2008-08-26
I just scour the PPAs nowadays.

---

### Post by Lostincyberspace on 2008-08-26
The current Linux Mint uses the hardy stack.

---

### Post by ljpp on 2008-08-27
> **bruce89 said:**
> Ah, but there'd be more bugs.

Not exactly, or at least not necessarily. For an example in Ubuntu the changes in between releases are usually so fundamental that the latest release always seem to be more or less buggy, at least on the day of the release announcement.

A rolling release distro like PCLOS can be quite conservative in releases updates. People are most interested in the most recent applications (Firefox, Pidgin, OpenOffice, GIMP...) rather than the desktop environment or the kernel. On the other hand majority of Joe Averages are not likely to notice the Gnome/KDE version updating +0.01 as the changes are usually very small.

Someone made a reference to Mint, and yes indeed they seem to have plans to offer application updates for the LTS relese Elyssa (based on Hardy). Again, Mint has a lot smaller community and userbase than Ubuntu, I am sure that it would be a lot better to have such a project running within the Ubuntu community.

---

### Post by hessiess on 2008-08-27
personaly i dont think the linux world needs more distros. why not switch to PCLOS or arch?

---

### Post by kpkeerthi on 2008-08-27
Rolling release model may not fit a distro, like Ubuntu, that adds 'custom patches' to the upstream packages. It needs too much work to keep up with the upstream and the probability of introducing more bugs (when patching often) is more.

This is the reason why Arch, despite being a rolling distro, is both up-to-date and stable. Arch keeps packages from upstream mostly vanilla. So  upstream-fixed bugs remain fixed.

Ubuntu has opted for a 6 month release cycle so the devs will have sufficient time to test and validate the patches they add.

---

### Post by JuryZ on 2008-09-26
If I wanted up-to-date kernel or dbus, I would use LFS. It is Firefox or Gajim for example, for which being up-to-date really matters. I think that better idea would be just to have a community driven repository with upstream end user applications. Then everyone could just chose to sacrifice some predictability in favor of bleeding-edge apps.

---

### Post by K.Mandla on 2008-09-26
Not to belittle the discussion thus far, but this has been a topic many times over. Moved to Recurring Discussions.

---

### Post by vishzilla on 2008-09-26
> **K.Mandla said:**
> Not to belittle the discussion thus far, but this has been a topic many times over. Moved to Recurring Discussions.

an old thread brought back to life and sent to recurring discussions. very typical! :popcorn:

---

### Post by SunnyRabbiera on 2008-09-26
> **aysiu said:**
> Didn't Linux Mint (which is based on Ubuntu) recently move to a rolling release schedule?

Sorta, I hear its going to only update major interface packages and security, but kernel updates might not be in the cards.

---

