---
title: "Update manager keeps failing on this"
date: 2011-10-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-10-06
> 
W:Failed to fetch [http://ppa.launchpad.net/shiki/mediainfo/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/shiki/mediainfo/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Is that an official repo or is it one i have left over from my 11.04 install does anyone know as it never seems to be available on UK or Main server.

---

### Post by soylentcola on 2011-10-06
this is just an educated guess, but it looks like an official repo.  How long has it been failing? Maybe the actual thing it's trying to grab is offline, I've had that happen before...

---

### Post by thatguruguy on 2011-10-06
> **ELD said:**
> Is that an official repo or is it one i have left over from my 11.04 install does anyone know as it never seems to be available on UK or Main server.

If by "official repo" you mean "a repo maintained by Canonical", it clearly is not.

If you go to the launchpad page for the repo, which is available at [https://launchpad.net/~shiki/+archive/mediainfo]("https://launchpad.net/%7Eshiki/+archive/mediainfo"), you will see that nothing has been set up for Oneiric yet.  That's why it's failing.

---

### Post by thatguruguy on 2011-10-06
> **soylentcola said:**
> this is just an educated guess, but it looks like an official repo.

What is that educated guess based on, exactly?

---

### Post by ELD on 2011-10-06
> **thatguruguy said:**
> If by "official repo" you mean "a repo maintained by Canonical", it clearly is not.

If you go to the launchpad page for the repo, which is available at [https://launchpad.net/~shiki/+archive/mediainfo]("https://launchpad.net/%7Eshiki/+archive/mediainfo"), you will see that nothing has been set up for Oneiric yet.  That's why it's failing.

Thank you buddy, no idea where that came from in my list since i have no idea what the packages are for, i will remove it.

---

### Post by thatguruguy on 2011-10-06
> **ELD said:**
> Thank you buddy, no idea where that came from in my list since i have no idea what the packages are for, i will remove it.

It's a package for MediaInfo, which provides metatags for videos, audio files, etc.

It may be the "official" ppa of the *developer of MediaInfo*, but it's not an official part of Ubuntu.

Happy to help.

---

### Post by philinux on 2011-10-06
> **ELD said:**
> Thank you buddy, no idea where that came from in my list since i have no idea what the packages are for, i will remove it.

I'd get rid of it with ppa purge.

---

### Post by ELD on 2011-10-06
> **philinux said:**
> I'd get rid of it with ppa purge.

I actually just deleted it from my list using the software sources GUI was that not good practice then?

---

### Post by VinDSL on 2011-10-06
> **ELD said:**
> I actually just deleted it from my list using the software sources GUI was that not good practice then?
Depends on the package(s) inside the ppa, IMO...

For instance, let's say we were talking xserver, instead of update mangler.

If you washed & rinsed xserver, all hell would break loose.  Not so much a problem with update manager, I would guess.

To be safe, I judge ppa purge to be a prudent course, in most cases of ppa removal.  ;)

---

### Post by mc4man on 2011-10-06
The ppa has all of 4 packages, none of which would have been installed under "oneiric"  because none exist yet. So no need to purge

If you had use for mediainfo the natty packages work just fine in 11.10 , both the cli & gui.

---

