---
title: "Getting Chromium updates properly?"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by blackbird34 on 2011-12-17
Hi
My Chromium browser is still on the version from the Natty repos (Chromium 14.xxxx). Are they frozen to one version like the Firefox repo used to be? Because Chromium dev versions are now on version *_**18**_* and even Google Chrome stable is on version 16 ?
How can i get the current updates from the repo? or anyone got a PPA?

---

### Post by Paqman on 2011-12-17
I'm not trying to be a smartarse, but googling "chromium ppa" threw up the following links as the top three:

[Chromium Daily]("https://launchpad.net/~chromium-daily/+archive/ppa")
[Chromium Stable]("https://launchpad.net/~chromium-daily/+archive/stable")
[Chromium Dev]("https://launchpad.net/~chromium-daily/+archive/dev")

Generally speaking, the Ubuntu repos are frozen and only security updates or critical bugfixes find their way in. There is a backports repo that will contain some updated packages, this is especially useful on older LTS releases. Google do maintain their own repo of Chrome that is constantly updated, but because Chromium is shipped by the distros it gets left behind on Ubuntu.

---

### Post by *^kyfds( on 2011-12-17
Ubuntu repos should be designed to make updating easier.


right now, for most software at least, repos are useless.

---

### Post by Paqman on 2011-12-17
> **Thehumorouscheese said:**
> Ubuntu repos should be designed to make updating easier.


right now, for most software at least, repos are useless.

That's why we have backports and PPAs. The standard repos are designed to be stable, if you want to stay on the edge then there are other methods provided for you.

If you want repos that are constantly updated, then you choose a distro that has a rolling release model like Arch or Gentoo. It's no coincidence that these distros are considered more technical to use than Ubuntu, so you can see why maybe Ubuntu's choice of repo is a good fit for its objectives.

---

### Post by *^kyfds( on 2011-12-17
> **Paqman said:**
> That's why we have backports and PPAs. The standard repos are designed to be stable, if you want to stay on the edge then there are other methods provided for you.

If you want repos that are constantly updated, then you choose a distro that has a rolling release model like Arch or Gentoo. It's no coincidence that these distros are considered more technical to use than Ubuntu, so you can see why maybe Ubuntu's choice of repo is a good fit for its objectives.

true, but i still think it would be a useful tool to have the ability to update all of your software(s) at once (optionally, of course)

i love ubuntu, so i'm sticking with it anyways :3

---

### Post by Paqman on 2011-12-17
> **Thehumorouscheese said:**
> true, but i still think it would be a useful tool to have the ability to update all of your software(s) at once (optionally, of course)


There is, and you can use it every April and October ;)

---

### Post by blackbird34 on 2011-12-17
thanks for the replies everyone. Bit of a dumb post... 
At least i've managed to read the PPA page and spot the command     
sudo add-apt-repository ppa:chromium-daily/stable
Not really ready to move to Arch yet, thanks, no time, though it sounds educational:P

---

### Post by malspa on 2011-12-17
Thanks blackbird34, and thanks Paqman. I should have thought to check for a Chromium PPA, but I didn't until I saw this thread.

> **blackbird34 said:**
> Bit of a dumb post...

Your "dumb post" ended up helping me.

---

