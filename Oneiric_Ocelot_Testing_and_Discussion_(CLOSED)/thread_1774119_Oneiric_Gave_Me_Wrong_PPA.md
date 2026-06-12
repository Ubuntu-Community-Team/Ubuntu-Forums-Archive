---
title: "Oneiric Gave Me Wrong PPA?"
date: 2011-06-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xxhopingtearsxx on 2011-06-02
When I try to Update I get

> W: Failed to fetch ht tp://ppa.launchpad.net/vala-team/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http ://ppa.launchpad.net/vala-team/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


Those look like they were meant to be where I get my updates for Oneiric from. Should I replace them? If so, what exactly should I replace them with? (The exact repository link or whatever.)

---

### Post by Starks on 2011-06-03
change the repo to natty in gksu software-properties-gtk

---

### Post by plucky on 2011-06-03
> **xxhopingtearsxx said:**
> When I try to Update I get



Those look like they were meant to be where I get my updates for Oneiric from. Should I replace them? If so, what exactly should I replace them with? (The exact repository link or whatever.)

Why do you need the PPAs?

PPAs are used to install the latest versions of software in current releases,and should only be used when you cannot wait for the latest release of a particular piece of software.

As Oneiric is still in the development phase,you will be getting the most up to date bits of software that the devs think are stable enough to include with the system.

I would remove all your PPAs and just rely on the Main Canonical repositories for updates.

Good Luck

---

