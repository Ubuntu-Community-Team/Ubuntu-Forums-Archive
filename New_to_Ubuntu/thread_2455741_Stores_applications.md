---
title: "Stores applications"
date: 2020-12-26
forum: New to Ubuntu
---

### Post by raisen on 2020-12-26
I am trying to understand all these store apps available:
- Ubuntu Software
- snap-store
- gnome store

I assume Ubuntu Software is the same (alias) as snap-store, and gnome store is an application developed by the gnome team that isn't related to Canonical - right?

We also have the Synaptic Package manager.

I wish the Synaptic package manager was built into one of those store applications so I can do searches in one place.

---

### Post by TheFu on 2020-12-26
There are
 [LIST]
[*] APT repos
[*]snap store
[*]flatpak store
[/LIST] 

APT is the ecosystem used by synaptic, apt, apt-get, aptitude, and other apt-based tools. To search, use **sudo apt search {search term}**.  'd assme whatever the gnome-store is, would tie into the apt-ecosystem on debian-based systems and whatever RH uses for those systems.

snap can search the Canonical snap-store.

Canonical decided to muddy the water by mixing the snap-store and normal canonical repos the last few releases. I find that unfortunate. There are good and bad parts to the choice.

I haven't used any GUI for software install, searching, or management in a very long time.  For me, this makes getting the software I want, from the correct type of package for my needs, possible.

---

### Post by grahammechanical on 2020-12-26
I guess it depends on which version of Ubuntu you are using. A fresh install of Ubuntu 20.04 should have something called Software. (icon a white shopping bag) This is Gnome Software branded as a Ubuntu app. It will have extensions to offer Flatpack and Snap apps.

My main OS has been upgrade over the years through 16.04 to 18.04 and on to 20.04. I have Gnome Software (Called Software), Ubuntu Software (orange icon of a shopping bag) that looks like the Software app and also the Snap Store. Which is the only one I do not have an icon for. I can launch it from the Software app and it uses the old orange Ubuntu Software icon.

The last few years have been confusing and messy.

Regards

---

### Post by raisen on 2020-12-28
Thank you all for your feedback.

---

### Post by raisen on 2020-12-30
Yeah, the app store world is a bit messy now, but I guess this is happening to other OSes too. Windows and Apple desktop stores are quite confusing for users too.
I have been using Linux on and off since I was 11 (Slackware being my first distro). I have been spending my last ten years or so working on an Apple laptop, but I couldn't deal with the lack of kernel space support for Docker containers so I am trying to make a transition to use Linux as my main OS now *again*.
PS: I just found out there is a flatpak store too.

---

