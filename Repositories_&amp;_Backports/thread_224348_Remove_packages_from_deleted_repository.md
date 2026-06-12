---
title: "Remove packages from deleted repository"
date: 2006-07-27
forum: Repositories &amp; Backports
---

### Post by Paerez on 2006-07-27
I recently removed the compiz repository in order to clean out the packages before I add it and try again.

Is there a command that could list all the packages that are now no longer linked to a repository in my sources list? I want to downgrade what was upgraded, and remove what was added.

---

### Post by J0Sb31R on 2006-08-16
*bump*

---

### Post by myha on 2006-08-22
hehe, same here.... Found anything out?


regards

---

### Post by mmcmonster on 2006-08-22
Not a direct answer, but why not just:
[INDENT]apt-get remove *package-name*
apt-get update
apt-get install *package-name*
[/INDENT]

---

### Post by andb on 2006-08-22
try gtkorphan. Its a graphic interface to the orphan command, which looks for uneeded packages.

---

### Post by VirtuAlex on 2006-08-22
> **mmcmonster said:**
> Not a direct answer, but why not just:
[INDENT]apt-get remove *package-name*
apt-get update
apt-get install *package-name*
[/INDENT]
the problem is in figuring out what *package-name*s are

---

### Post by VirtuAlex on 2006-08-22
> **andb said:**
> try gtkorphan. Its a graphic interface to the orphan command, which looks for uneeded packages.
This also won't catch everything - some packages are not orphaned, they just upgraded to "newer" versions

---

### Post by Paerez on 2006-08-22
My problem, as VirtuAlex said, is finding out which packages to uninstall. They are not orphans because I manually installed them. Consider the package "compiz". I installed it with "apt-get install compiz", so it will not show up as an orphan. But not that the repository has been removed, there is no available version.

I was hoping to get a list of all packages that currently have no available version in the repository. I use aptitude always, so I don't have any orphaned packages.

---

### Post by Gathers on 2006-08-24
Could this be what you are looking for?
[INDENT]apt-show-versions | grep 'No available'[/INDENT]

---

### Post by berteh on 2006-09-01
> **Gathers said:**
> Could this be what you are looking for?
[INDENT]apt-show-versions | grep 'No available'[/INDENT]

YEEES ! wonderful, thanks a thousand times, this will finally allow me to get rid of the mess in my packages after trying glx.

---

### Post by Paerez on 2006-09-01
thanks! that went into my "handy commands" tomboy note for safekeeping!

---

### Post by raykroeker on 2011-07-27
Another option I discovered.  I re-added the repository, then used synaptic to filter packages by "Origin" which gave me the ones I wanted to remove.  Then later removed the repo.

---

