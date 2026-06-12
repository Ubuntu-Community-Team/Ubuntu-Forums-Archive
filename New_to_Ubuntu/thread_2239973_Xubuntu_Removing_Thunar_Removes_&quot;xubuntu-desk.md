---
title: "Xubuntu: Removing Thunar Removes &quot;xubuntu-desktop&quot;"
date: 2014-08-16
forum: New to Ubuntu
---

### Post by Sanctimonious_Ape on 2014-08-16
I have no use for a file manager that doesn't tell me the *real* size of a file (Thunar shows base-10, when anyone who's been around since the days before Gigabyte-sized hard drives knows the truth lies in using base-2, what is now called GiB), so I want to replace Thunar because it doesn't have an option to display in base-2 (although I came across an old thread that said it used to be the other way around years ago **sigh**).

I installed PCmanFM and want to wipe Thunar off the map, but when I tell Ubuntu Software Center to remove it I am told several other packages will also have to be removed -- including one called "xubuntu-desktop"!  That's kinda scary.  I don't want my whole DE removed.  Should I be concerned about this?

[ATTACH=CONFIG]255541[/ATTACH]

---

### Post by vasa1 on 2014-08-16
> **Sanctimonious_Ape said:**
> ... several other packages will also have to be removed -- including one called "xubuntu-desktop"!  That's kinda scary.  I don't want my whole DE removed.  Should I be concerned about this?

ubuntu-desktop is a metapackage. After installation, it can safely be removed. If you plan to **upgrade** to 14.10, you'll probably want to re-install it then for the upgrade to be successful.

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)
[www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html](www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html)

---

### Post by Sanctimonious_Ape on 2014-08-16
Interesting - I kinda already knew the basic concept of metapackages, but it appears you're saying uninstalling said metapackage won't remove all the dependencies it's responsible for having brought in?  Seems counterintuitive to me, but if it works then so be it.  Thanks for the info and quick response, vasa1.

---

### Post by vasa1 on 2014-08-17
> **Sanctimonious_Ape said:**
> Interesting - I kinda already knew the basic concept of metapackages, but it appears you're saying uninstalling said metapackage won't remove all the dependencies it's responsible for having brought in?  Seems counterintuitive to me, but if it works then so be it.  Thanks for the info and quick response, vasa1.
On my system, lubuntu-desktop is one of the first things that gets removed after a clean installation. Its removal doesn't affect me in any perceptible way because I move to the new release via a clean install. I provided just two links but there are several on the issue.

---

### Post by Sanctimonious_Ape on 2014-08-17
Went ahead and removed it - thanks!

(If I have to come back here using elinks, you'll know what happened... ;))

---

### Post by Dennis N on 2014-08-17
Just wondering...Now that Thunar is gone, can you still delete items from your Desktop without using the file manager?

---

### Post by mörgæs on 2014-08-17
Good that it works. Please mark the thread 'solved'.

---

### Post by newb85 on 2014-08-17
> **vasa1 said:**
> On my system, lubuntu-desktop is one of the first things that gets removed after a clean installation. Its removal doesn't affect me in any perceptible way because I move to the new release via a clean install. I provided just two links but there are several on the issue.

That's what makes metapackages special.  When normal packages are installed, their dependencies are marked as automatically installed, so that when they're no longer required as dependencies, they can automatically be removed.  When metapackages are installed, their dependencies are marked as manually installed.

---

### Post by JKyleOKC on 2014-08-17
> **newb85 said:**
> That's what makes metapackages special.  When normal packages are installed, their dependencies are marked as automatically installed, so that when they're no longer required as dependencies, they can automatically be removed.  When metapackages are installed, their dependencies are marked as manually installed.I'm glad you posted this message! Although I've used various flavors of Linux since starting with Slackware 2.0 back in the previous century, I never knew what made this tiny difference before. Old dogs **can** learn new tricks! Many thanks for making my day!

I've wondered for years why most of my system packages show up as "manually installed" when using Synaptic's filters; now I know.

---

### Post by mcduck on 2014-08-18
> **newb85 said:**
> That's what makes metapackages special.  When normal packages are installed, their dependencies are marked as automatically installed, so that when they're no longer required as dependencies, they can automatically be removed.  When metapackages are installed, their dependencies are marked as manually installed.

It also helps to remember that package dependencies are one-way mechanism.

If package *A* depends on package *B*, that doesn't mean that package *B* would depend on package *A*. So installing *A* will bring *B* with it, and if you the remove package *B*, *A* will also need to be removed since it's dependencies can't be fulfilled any more. However since package *B* doesn't depend on package *A*, you can install *B* without *A*, or if both are already installed, remove package *A* without affecting package *B* at all.


(so actually you *could* safely uninstall the metapackages even if the system for marking things as manually/automatically installed wasn't there, but that mechanism allows you to run commands like "apt-get autoremove" that cleans unused dependencies from the system. )

---

