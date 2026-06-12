---
title: "Size mismatch"
date: 2008-01-04
forum: Packaging and Compiling Programs
---

### Post by ChameleonDave on 2008-01-04
This must surely have been covered before, but I can't find it.

I've decided to make some tentative steps into the world of programming, and I've started by packaging a pre-existing program.  I did that yesterday, and it went fine.  The next stage was to learn how to put this DEB on to a repository so that it can be retrieved and installed with the appropriate tools.

I created the repository by copying the structure from other people's repos, and entered the address into my */etc/apt/sources.list* file.  It was all recognised correctly, and I was able to use Synaptic to download the package.

That's where I hit a brick wall.  Synaptic returned the following error message: *Size mismatch*

I believe that there is no size mismatch, so I don't understand why this error occurs.

Perhaps someone could give this a quick look and tell me what mistake I have made.

Use the following code to add and test my repo:

```

sudo echo "deb http://linux.pro-reason.info gutsy partner" >>  /etc/apt/sources.list
apt-get update
apt-get install lrzip-doc

```

---

### Post by dholbach on 2008-01-07
You can use PPA ([https://help.launchpad.net/PPAQuickStart](https://help.launchpad.net/PPAQuickStart)) easily.

Or (and I'd encourage you to do that) you can get it included in Ubuntu, so all users can benefit from it: [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

---

### Post by ChameleonDave on 2008-01-07
> **dholbach said:**
> You can use PPA ([https://help.launchpad.net/PPAQuickStart](https://help.launchpad.net/PPAQuickStart)) easily.

Or (and I'd encourage you to do that) you can get it included in Ubuntu, so all users can benefit from it: [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

OK, thanks for that.  It's a workaround rather than an actual answer, but never mind.

Unfortunately those instructions for PPA are out of date.  It tells me to click on "Activate PPA" in the left-hand menu, but there is no such menu.  There's no obvious way of activating one's PPA.

I'll look into it more, but I'd really appreciate someone having a look at my repo and telling me what the source of this "size mismatch" thing is.

---

### Post by dholbach on 2008-01-08
No link on the left hand-side portlet saying "PPA" or "Personal Package Archive"?

How do you generate your Sources.gz or Packages.gz for your repository?

---

### Post by ChameleonDave on 2008-01-08
> **dholbach said:**
> No link on the left hand-side portlet saying "PPA" or "Personal Package Archive"?

How do you generate your Sources.gz or Packages.gz for your repository?

[del]Not that I can see.[/del]  Ah yes.  The site claimed (and even had a screenshot) that it would say "Activate PPA", but it says "Activate Personal Package Archive".  I searched (both with my eyes and with Ctrl+F) for the string "PPA" on the page.

I followed the example of repos like [http://www.virtualbox.org/debian/dists/gutsy/](http://www.virtualbox.org/debian/dists/gutsy/) to infer what the proper contents of all the files should be.

---

### Post by ChameleonDave on 2008-01-13
Looking at the PPA thing, it's so user-unfriendly that I can't bring myself to persevere and work out how to use it.

Does anyone know how I can fix the size mismatch?

---

