---
title: "Held packages?"
date: 2011-07-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-07-10
My system has gradually built up to 21 upgradeable packages being held back. Is this normal?

The last time this happened (during Natty development), I finally broke down and did a fresh install from a fresh download. No packages were held from then on. Do I need to do that again? I hope not, because it is such a pain to get my networking drivers installed, again.

Tim

---

### Post by buzzmandt on 2011-07-10
well, you could take a chance and do a 
```
sudo apt-get dist-upgrade
```
make sure it's not removing something important and go for it.  especially if the alternative is to do a fresh install anyway. have your install cd handy as a back up.

---

### Post by Bucky Ball on 2011-07-10
Have you tried just a regular:

```
sudo apt-get update
sudo apt-get upgrade
```

?

---

### Post by WRDN on 2011-07-10
It is normal. There is currently a migration to a new set of indicator libraries. Do **not** upgrade the packages, as it will break Unity and will prevent you from logging in (from experience).

In a few days, all dependencies should be sorted and you will be able to do a full upgrade.

---

### Post by Bowmore on 2011-07-10
I guess it's about those 17 indicator and 4 unity packages.

The two packages *libindicator3* and *libindicator3-3* is going to be replaced by *libindicator6* and *libindicator3-6*. At the moment unity-2d still depends on libindicator3 so that's why all dependencies are not yet met.

So either wait for an updated version of *unity-2d* (beginning next week) or upgrade now and reinstall *unity-2d* manually later when its dependency to be libindicator6 is updated. Easiest way then is to reinstall *ubuntu-desktop*.

If upgrading now then the following packages will be removed
```
libindicator3
libindicator3-3
libunity-2d-private0
ubuntu-desktop
unity-2d
unity-2d-launcher
unity-2d-panel
unity-2d-places
unity-2d-spread
```
and these will be installed replacing libindicator3/libindicator3-3
```
libindicator3-6
libindicator6
```

---

### Post by ratcheer on 2011-07-10
Thanks, WRDN and Bowmore. Yes, my held packages are those you mention. I just wanted to make sure it was not just me. I will wait for the dependencies to resolve themselves.

Tim

---

### Post by ratcheer on 2011-07-15
I've waited five more days and these packages are still held. In fact, they are up to 24 held, now.

```
evolution-data-server-common 3.1.2-0ubuntu1 -> 3.1.3.1-0ubuntu3

You can only view changelogs of official Debian packages; evolution-data-server-common is from "Ubuntu".

indicator-application 0.3.90-0ubuntu2 -> 0.3.91-0ubuntu2

You can only view changelogs of official Debian packages; indicator-application is from "Ubuntu".

indicator-application-gtk2 0.3.90-0ubuntu2 -> 0.3.91-0ubuntu2

You can only view changelogs of official Debian packages; indicator-application-gtk2 is from "Ubuntu".

indicator-appmenu 0.2.90-0ubuntu3 -> 0.2.91-0ubuntu1

You can only view changelogs of official Debian packages; indicator-appmenu is from "Ubuntu".

indicator-appmenu-gtk2 0.2.90-0ubuntu3 -> 0.2.91-0ubuntu1

You can only view changelogs of official Debian packages; indicator-appmenu-gtk2 is from "Ubuntu".

indicator-datetime 0.2.90-0ubuntu4 -> 0.2.91-0ubuntu2

You can only view changelogs of official Debian packages; indicator-datetime is from "Ubuntu".

indicator-datetime-gtk2 0.2.90-0ubuntu4 -> 0.2.91-0ubuntu2

You can only view changelogs of official Debian packages; indicator-datetime-gtk2 is from "Ubuntu".

indicator-me 0.2.91-0ubuntu1 -> 0.2.92-0ubuntu1

You can only view changelogs of official Debian packages; indicator-me is from "Ubuntu".

indicator-me-gtk2 0.2.91-0ubuntu1 -> 0.2.92-0ubuntu1

You can only view changelogs of official Debian packages; indicator-me-gtk2 is from "Ubuntu".

indicator-messages 0.4.90-0ubuntu2 -> 0.4.91-0ubuntu1

You can only view changelogs of official Debian packages; indicator-messages is from "Ubuntu".

indicator-messages-gtk2 0.4.90-0ubuntu2 -> 0.4.91-0ubuntu1

You can only view changelogs of official Debian packages; indicator-messages-gtk2 is from "Ubuntu".

indicator-session 0.2.90-0ubuntu3 -> 0.2.92-0ubuntu2

You can only view changelogs of official Debian packages; indicator-session is from "Ubuntu".

indicator-session-gtk2 0.2.90-0ubuntu3 -> 0.2.92-0ubuntu2

You can only view changelogs of official Debian packages; indicator-session-gtk2 is from "Ubuntu".

indicator-sound 0.7.2-0ubuntu1 -> 0.7.3-0ubuntu1

You can only view changelogs of official Debian packages; indicator-sound is from "Ubuntu".

indicator-sound-gtk2 0.7.2-0ubuntu1 -> 0.7.3-0ubuntu1

You can only view changelogs of official Debian packages; indicator-sound-gtk2 is from "Ubuntu".

libappindicator1 0.3.0-0ubuntu3 -> 0.3.90-0ubuntu1

You can only view changelogs of official Debian packages; libappindicator1 is from "Ubuntu".

libappindicator3-1 0.3.0-0ubuntu3 -> 0.3.90-0ubuntu1

You can only view changelogs of official Debian packages; libappindicator3-1 is from "Ubuntu".

libunity-2d-private0 3.8.10-0ubuntu1 -> 3.8.10-0ubuntu2

You can only view changelogs of official Debian packages; libunity-2d-private0 is from "Ubuntu".

libunity-core-4.0-4 4.2.0-0ubuntu1 -> 4.2.0-0ubuntu3

You can only view changelogs of official Debian packages; libunity-core-4.0-4 is from "Ubuntu".

python-appindicator 0.3.0-0ubuntu3 -> 0.3.90-0ubuntu1

You can only view changelogs of official Debian packages; python-appindicator is from "Ubuntu".

unity 4.2.0-0ubuntu1 -> 4.2.0-0ubuntu3

You can only view changelogs of official Debian packages; unity is from "Ubuntu".

unity-2d-panel 3.8.10-0ubuntu1 -> 3.8.10-0ubuntu2

You can only view changelogs of official Debian packages; unity-2d-panel is from "Ubuntu".

unity-common 4.2.0-0ubuntu1 -> 4.2.0-0ubuntu3

You can only view changelogs of official Debian packages; unity-common is from "Ubuntu".

unity-services 4.2.0-0ubuntu1 -> 4.2.0-0ubuntu3

You can only view changelogs of official Debian packages; unity-services is from "Ubuntu".


```Do those of you doing a fresh install from a CD image have this status? Or, does it come with the current versions of these packages already installed?

Thanks,
Tim

---

### Post by CaptainMark on 2011-07-15
ive got 35 held back packages now, the list seems to grow each day, i know most are know about, but im not sure about all of them```
The following packages have been kept back:
  evolution-data-server-common gnome-keyring gnome-system-monitor
  indicator-application indicator-application-gtk2 indicator-appmenu
  indicator-appmenu-gtk2 indicator-datetime indicator-datetime-gtk2
  indicator-me indicator-me-gtk2 indicator-messages indicator-messages-gtk2
  indicator-session indicator-session-gtk2 indicator-sound
  indicator-sound-gtk2 jockey-common jockey-gtk libappindicator1
  libappindicator3-1 libebook1.2-11 libgtk2.0-cil libunity-2d-private0
  libunity-core-4.0-4 linux-generic linux-headers-generic linux-image-generic
  python-appindicator seahorse unity unity-2d-panel unity-common
  unity-services yelp

```thats if use apt-get, if i got to synaptic i get different answers, these 35 will be sorted but remove others

---

### Post by mc4man on 2011-07-15
> **ratcheer said:**
> I've waited five more days and these packages are still held. In fact, they are up to 24 held, now.]Do those of you doing a fresh install from a CD image have this status? Or, does it come with the current versions of these packages already installed?

Thanks,
Tim
A fresh install with todays iso wouldn't be the worst thing - otherwise you should be able to get all of those installed thru synaptic.
If trying I'd click the reload button in synaptic after opening and possibly once again if you remove anything to jumpstart getting up to date (there's something funny about that in synaptic

If may depend on how you select the packages to upgrade (order), otherwise just remove evolution, reload and then try adding back
If anything else is marked for removal you think you need then add back...

---

### Post by Bowmore on 2011-07-15
@ratcheer, which packages will be removed by synaptic if you mark them all for upgrade?
Basically libindicator3, libindicator3-3 and libedataserverui-3.0-0 will be removed or actually replaced by libindicator6, libindicator3-6 and libedataserverui-3.0-1.

@CaptainMark, the only strange thing here is that indicator-me is removed. Did you use Mark all upgrades in synaptic?

**Edit**: Just noticed that the current upgrade of *indicator-session* (0.2.93-0ubuntu1) replaces *indicator-me* so that one will be removed too.
[https://lists.ubuntu.com/archives/oneiric-changes/2011-July/005006.html](https://lists.ubuntu.com/archives/oneiric-changes/2011-July/005006.html)

---

### Post by ratcheer on 2011-07-15
Everyone is talking about Synaptic. I use aptitude, so I don't really know the in's and out's of Synaptic.

Tim

---

### Post by CaptainMark on 2011-07-15
@bowmore yes this screenshot is synaptic right after i click mark all upgrades, i have done it yet though

---

### Post by sgage on 2011-07-15
I've been updating at least once every day with Synaptic since A2, and don't have any packages held back. 

Maybe it's time for you to do a reinstall - you might have worked yourself into some sort of dependency pickle.

---

### Post by ratcheer on 2011-07-15
> **sgage said:**
> I've been updating at least once every day with Synaptic since A2, and don't have any packages held back. 

Maybe it's time for you to do a reinstall - you might have worked yourself into some sort of dependency pickle.

That is exactly what I am thinking.

My problem with just going and doing that is that Ubuntu installs the wrong drivers for both my NIC and my wireless card, leaving me with no network access. I have to compile the correct drivers from source and force the kernel to load them. I know how to do it, but it is really a pain.

Tim

---

### Post by Bowmore on 2011-07-15
> **CaptainMark said:**
> @bowmore yes this screenshot is synaptic right after i click mark all upgrades, i have done it yet thoughYou've made the upgrades? It's ok anyway to do so in your case.

The me menu is replaced by a user menu that only show up if there are more than one user registered. However this new menu does not work atm.

---

### Post by sgage on 2011-07-15
> **ratcheer said:**
> That is exactly what I am thinking.

My problem with just going and doing that is that Ubuntu installs the wrong drivers for both my NIC and my wireless card, leaving me with no network access. I have to compile the correct drivers from source and force the kernel to load them. I know how to do it, but it is really a pain.

Tim

Sounds like a pain, but you may just have to bite ye olde bullet.

Ah, development releases!  :KS

---

### Post by CaptainMark on 2011-07-15
typo, i havent made the upgrades via synaptic, i will do in time but usually like to give a chance incase the dependencies get resolved im more likely to get into dependency loophole hell if i force package upgrades, we shall wait and see, im doing the apt-get only route for now, i always like to stick with one package management type in a single dev cycle

---

### Post by VinDSL on 2011-07-16
> **ratcheer said:**
> My system has gradually built up to 21 upgradeable packages being held back. [COLOR="Red"]**Is this normal?**[/COLOR]
Yes, normal... sorta.  :D

I was going to leave a reply, a few hours ago, when I had 2 upgradeable packages being held back - MY normal - albeit 1/10 YOUR normal, but...

I ran out of time.

The reason I'm posting NOW is because I just did an update and the dependencies for these 2 lingering packages were finally met.

Put another way, my new stautus is:
```

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

... which is actually abnormal.

Anyway, I would judge that 2-21 packages being held back is rather normal - FOR A DEV RELEASE.  ;)

---

### Post by ratcheer on 2011-07-16
Thanks, VinDSL. I am going to continue waiting, mainly due to my networking driver problems.

I do not blame the driver problems on Oneiric nor even Ubuntu. I believe the problems are at the Linux kernel level, as I can see that people have been posting the same problems against several distributions over a period of at least five years. I do not understand why they cannot be fixed. I even found one bug on Launchpad where the status is "will not fix". What a load of...

Tim

---

### Post by drs305 on 2011-07-16
I installed the 15 July daily build and still have a couple of unity, gwibber and four indicator packages being held back.

---

### Post by mc4man on 2011-07-16
> **drs305 said:**
> I installed the 15 July daily build and still have a couple of unity, gwibber and four indicator packages being held back.
At least on a 32 bit install (07/15 iso) all those sources upgraded fully

unity - 4.2.0-0ubuntu4
gwibber (3.1.2-0ubuntu1
indicator-messages (0.4.92-0ubuntu1)
indicator-session (0.2.93-0ubuntu1
ect.

---

### Post by drs305 on 2011-07-16
> **mc4man said:**
> At least on a 32 bit install (07/15 iso) all those sources upgraded fully

unity - 4.2.0-0ubuntu4
gwibber (3.1.2-0ubuntu1
indicator-messages (0.4.92-0ubuntu1)
indicator-session (0.2.93-0ubuntu1
ect.

I didn't mention it, but I'm using a 64-bit image.

---

### Post by mc4man on 2011-07-16
They all show as built for i386 and amd64, but not having 64 bit can't say for sure
synaptic usually will do or say why not - lately when using synaptic I always reload the sources from synaptic itself - there's is something odd going on there occasionally

(just noticed the new unity may have changed the default scale function from l.click on icon, (window picker on window group from ALL workspaces) -  will have to ck. further

---

### Post by ratcheer on 2011-07-18
I worked around the problems by doing a fresh install from an iso image (Jul 17 daily Live). I did have to reinstall the wireless driver. But, I am now fully updated with no held upgrades.

Tim

---

### Post by VinDSL on 2011-07-19
> **ratcheer said:**
> I worked around the problems by doing a fresh install from an iso image (Jul 17 daily Live). I did have to reinstall the wireless driver. But, I am now fully updated with no held upgrades.
Yep, this usually works wonders - fresh installs.  Fresh installs serve the purpose of being a sanity check, of sorts, in our second-guessing.

If everybody would leave dev releases alone - and rely solely  on updates - they wouldn't have to do this, but...

Who (amongst us) can leave dev releases alone?!?!?  Workarounds are the name of the game, and often they conflict with the direction that the devs ultimately take.

Even though (in our mind's eye) our fresh installs remain fresh - they are indeed corrupt, because we've typically made changes, that we forgot about a few minutes later.

Soooo, many times, it easier to just do another fresh install, than to rack our brains, trying to remember what we changed, and figure ways to reverse-engineer said changes.

This is where having a separate /home partition saves your bacon - and even then - sometimes deleting things in your /home directory is necessary, because you've corrupted the config files, as well.

LoL!  Does that make any sense?

I suppose you can chalk this up to, "ever cloud has a silver lining".

And, clouds are what testers live for...  ;)

---

### Post by ratcheer on 2011-07-19
And now, after getting everything straightened out just yesterday, a bunch of compiz and xorg updates and now my desktop will not display. Just a few rectangular patches of it.

I reviewed the update output before I restarted, and I saw no evidence of errors.

Tim

---

