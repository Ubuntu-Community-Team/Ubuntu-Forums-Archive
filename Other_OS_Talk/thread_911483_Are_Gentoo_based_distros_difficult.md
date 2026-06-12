---
title: "Are Gentoo based distros difficult?"
date: 2008-09-05
forum: Other OS Talk
---

### Post by global citizen on 2008-09-05
I have found a lot of user friendly Debian based distros, a lot of RPM based ones though not on the scale of Debian and some others based on others but I only found Sabayon as a user friendly Gentoo based distro. The reason I concluded after reading about Gentoo is that it is very difficult to install softwares in Gentoo and update the system. Also its a little unstable. Is that true? Is Gentoo some unique distro very very different from others like Debian and RPM etc. etc. that it is at such a disadvantage that there is only one distro based on it? Please inform I am very curious to know about the reality.:KS

---

### Post by TheKid965 on 2008-09-05
Gentoo is not for beginners, period.  Even if you use its graphical installer it can take a long time, and unless you're already *quite* familiar with your computer and its constituent components it can still throw you off.

The "thing" about Gentoo is that its packages are actually (unless you specify otherwise) compiled from source as you "emerge" them from the Portage tree, based on settings you predefine (the "USE=" variable).  While this goes a long way toward creating leaner, meaner packages based on your specific system, it does tend to make package installation a much longer, more CPU-intensive process than it is in a Debian/Ubuntu environment, or even RPM.  (Trust me, you *don't* want to try something like "emerge openoffice" unless you have a *very* fast CPU, a lot of free memory, and the lion's share of a day to spare.)  Luckily, most popular "big" packages have binary-install options.

Sabayon seems to be a good jumping-off point for the distro; it appears to be for Gentoo what Ubuntu is for Debian, meaning it's a "frendlier," easier-to-install variant with a lot of extras.  Better still, unlike Ubuntu (which retains some important differences from Debian in structure), once installed Sabayon is basically Gentoo with a bunch of extra packages already installed.

---

### Post by handy on 2008-09-05
A Sabayon installation is so quick & (provided you don't have some strange hardware incompatibility) easy, compared to that of the time consuming Gentoo install.

Using Sabayon you get to learn about the Gentoo portage software installation system, which is not too hard to use, though it is slow due to everything being compiled.  The Arch pacman system, which runs on binaries is lightning fast by comparison.

I agree, Sabayon is an easy introduction to Gentoo.

---

### Post by nrs on 2008-09-05
If you consider yourself an advanced user your not going to find it difficult, just time consuming. I used Gentoo before I switched to Ubuntu, I've actually switched back to it. 

In a perfect world I would rate Gentoo easy for a beginner, it is most of the time, but you do run into problems, at least I do, often during particularly long chains of package upgrades / installs, etc. The solutions are usually trivial, but I can see a "newbie" smashing their head against the desk.

---

### Post by init1 on 2008-09-06
Gentoo is difficult, but not all distros based on it are. Knopperdisk is relatively easy (even though there's no X).

---

### Post by molom on 2008-09-09
Thats really not a proper question, because it depends. Gentoo itself is not easy, but other Gentoo distros can be super easy to use (Eg. Sabayon is pretty user-friendly).

An example:
Ubuntu is one of the most known distros for being user friendly and its based on Debian. Debian isn't user friendly compared to Ubuntu though.

It really depends on the distro, not the base.

---

