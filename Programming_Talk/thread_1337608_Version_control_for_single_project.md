---
title: "Version control for single project"
date: 2009-11-25
forum: Programming Talk
---

### Post by juli2005an on 2009-11-25
Hi,
After posting it in the general forum, I've figured that this one here is a better place to ask a "stupid" question. This is rather something about recommendations/suggestions than asking for technical support.
The problem:
I've been working on a number of files (c-codes) in a project. As the project grows the code alters and to keep track of changes I would like to have something similar to CVS... basically a way of telling, "okay this is a new release" but keeping the old one - organized... preferably with a note i can attach to tell (myself) later what I've been working on and what I've changed so far. I thought about SVN or CVS but that seems a bit "overkill" for my purposes since it would be only for a single user and I would like not have to set up a server...
Any suggestions/ideas????
Cheers,

p.s. I don't think it would matter which distro I use but that's the current situation:
Ubuntu 9.10 / RedHat 4.x (if i recall correctly)
However, the Ubuntu would be the system i'm mostly working with.

---

### Post by wmcbrine on 2009-11-25
git is perfect for this. Any directory can become a repository.

---

### Post by Cardale on 2009-11-25
How difficult is git to install and use on a ubuntu setup?  How is performance?  Git has version control?

Thanks.

---

### Post by juli2005an on 2009-11-25
thanks... i've just starting playing around... and yes git has version control plus it has some implementations to various other programs with several GUIs. To install do the following as superuser:
apt-get install git-core git-doc gitk
(the last will install a GUI toolkit)
and then follow this tutorial
[http://www.kernel.org/pub/software/scm/git/docs/gittutorial.html](http://www.kernel.org/pub/software/scm/git/docs/gittutorial.html)

Cheers,

---

### Post by wmcbrine on 2009-11-25
> **Cardale said:**
> How difficult is git to install and use on a ubuntu setup?Trivial.

> *How is performance?*Aside from pushing to/pulling from remote repositories, I have yet to do an operation that wasn't essentially instantaneous. Since git isn't server-based, it's convenient to use offline. You can do as many commits as you want to your local repository, and then push them all to a remote repo in one batch.

> *Git has version control?*No, git *is* version control. But perhaps I'm not understanding you.

---

### Post by Tibuda on 2009-11-25
> **Cardale said:**
> How difficult is git to install and use on a ubuntu setup?  How is performance?  Git has version control?

Thanks.

[click here to install git on ubuntu]("apt:git-core") (if you got apturl working, if not, install the git-core package using synaptic or another package manager)

[click here to see why git is better]("http://whygitisbetterthanx.com/")

---

