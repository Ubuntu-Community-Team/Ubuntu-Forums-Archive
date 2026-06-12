---
title: "apt-build - how to make it works?"
date: 2005-04-16
forum: Programming Talk
---

### Post by Molot on 2005-04-16
I've just apt-get'ed apt-build... On test run, I've decided to recompile links and mc - not so big, not so complicated... Ideal for testing purposes.

All seems to be fine - source downloading, dependiences installing...

In links, when it is time to run gcc, compiler is called in the broken manner: gcc treats options as a filename - of course "-pipe" file does not exist.

When trying to apt-build mc, mc directory don't even appears in source dir.

**solved... partialy**
Ok, links part seems to be solved - default config file was broken - unneeded "" signs in "other options".

It still ignores my march, mcpu and my optimization level...

---

### Post by Molot on 2005-04-17
Ok, maybe simplier question... Did anyone make apt-build works on Ubuntu?...

---

### Post by Daniel G. Taylor on 2005-04-17
I'm not sure about apt-build but I have been able to successfully rebuild debian packages using:
```
apt-get build-dep packagename
apt-get source packagename
cd packagename
dpkg -rfakeroot -b
```
That will basically download a source debian package and make sure you have all the dependencies required to build it, and then you use dpkg to actually build it in a fakeroot (make sure you have fakeroot installed).

I've been able to successfully rebuild Debian unstable packages that aren't in Ubuntu repositories that way (like cegui and ogre) by adding the deb-src for the debian unstable repository to my sources.list and doing the above. So far I've only done it on amd64, but it works the same everywhere (I wanted amd64 packages, which is why I had to build from source).

[Edit] Forgot to mention, you can add/change/remove whatever you want before you rebuild the package with dpkg. It's probably a good idea to update the changelog and info files in the debian folder (maybe set yourself as the maintainer of this version).

---

### Post by Molot on 2005-04-18
[QUOTE=Daniel G. Taylor]I'm not sure about apt-build but I have been able to successfully rebuild debian packages using:
```
apt-get build-dep packagename
apt-get source packagename
cd packagename
dpkg -rfakeroot -b
```
That will basically download a source debian package and make sure you have all the dependencies required to build it, and then you use dpkg to actually build it in a fakeroot (make sure you have fakeroot installed).

I've been able to successfully rebuild Debian unstable packages that aren't in Ubuntu repositories that way (like cegui and ogre) by adding the deb-src for the debian unstable repository to my sources.list and doing the above. So far I've only done it on amd64, but it works the same everywhere (I wanted amd64 packages, which is why I had to build from source).

[Edit] Forgot to mention, you can add/change/remove whatever you want before you rebuild the package with dpkg. It's probably a good idea to update the changelog and info files in the debian folder (maybe set yourself as the maintainer of this version).[/QUOTE]
 I have fakeroot of course ;)

Way you wrote is good and workable.

Apt-build has few additional nice things I need:
- Removing unneeded packages previously automatically installed for the build dependiences
- Keeping the repository and automaticaly adding newly compiled packages

All this with only one command that download source & build-deps, compiles, builds package, adds it into repository and (if I want to) clearing system...

If I'll use Your way (and now it looks like I have to), I'll be made to write my own program for all "additional" tasks that apt-build should do. As all you know, it's not nice :]

Anyway, thanks... You were trurly helpfull.

---

### Post by SkyNet2029 on 2006-05-08
Does anyone know of a more insightful readme for this ? When I am wanting to remove the references to kernel from the /etc/apt/apt-build.list file am I supposed to comment the entries out or delete in its (the entry, not the file) entirety?

---

