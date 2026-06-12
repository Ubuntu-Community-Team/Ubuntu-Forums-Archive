---
title: "make deb or not make deb?"
date: 2011-05-12
forum: Programming Talk
---

### Post by johnny3k on 2011-05-12
I sometimes install apps with ./configure make make installl but maybe this is bad idea? maybe need make deb 1st and install it after?  
how make deb?

---

### Post by simeon87 on 2011-05-12
deb is for distributing a program to others. If you already have the deb (with the program's code), then there's no need to create a deb while installing the program. You can use configure, make and make install just fine.

---

### Post by arsenic23 on 2011-05-12
> **simeon87 said:**
> deb is for distributing a program to others. If you already have the deb (with the program's code), then there's no need to create a deb while installing the program. You can use configure, make and make install just fine.

Creating the deb package makes updating and uninstalling the package easier in the future.  I used to do it back when I had to compile things more often.

---

### Post by MadCow108 on 2011-05-12
I prefer creating a deb as I can easily uninstall that again, only very few makefiles have an uninstall target.

checkinstall makes it very easy to create debs for personal use

---

### Post by Lars Noodén on 2011-05-12
> **arsenic23 said:**
> Creating the deb package makes updating and uninstalling the package easier in the future.  I used to do it back when I had to compile things more often.

+1 it makes it much easier to manage, 
   I would strongly recommend making a deb

---

### Post by cgroza on 2011-05-12
Make a deb. Let dpkg and apt do the work for you.

---

### Post by nvteighen on 2011-05-13
I'll be the advocate's devil.

No, don't make a deb unless you're distributing software targetting a specific distro.

While creating a deb is easy, creating one that works smoothly can become really hard. I'm thinking on stuff like Python modules (python-support vs. python-central vs. dh_python...) or even just configuring the deb in the right way when something more than a simple executable is going to be installed (system-wide data, whatever... distros may have different criteria for this).

FYI, Debian mantainers always create the official deb by their own, even when the project released an upstream deb. This means that all the hassle you might have been through is worth nothing if you're interested on having your software included in that OS. IIRC, Ubuntu uses a similar approach.

For distribution, the most universal way is a source tarball with a Makefile. If you're going to create a deb, do always distribute a source tarball too.

If what you want is just a way to keep track of different versions of some application you're writing, being able to revert to an older one if the newer breaks, use some VCS system.

---

### Post by -=hazard=- on 2011-05-13
> **johnny3k said:**
> I sometimes install apps with ./configure make make installl but maybe this is bad idea? maybe need make deb 1st and install it after?  
how make deb?

Well thats not very bad idea by compiling stuff your self. Anyway by installing from .deb packages you save your self some time for future management of your installed programs.
This is the simpliest way to make a .deb package from source files, but remember that this way the .deb package may only work on the computer that was created, because sometimes it need dependencies that are not included.

First install checkinstall:
```
sudo apt-get install checkinstall
```
then
```
cd /path to your source folder
./configure
sudo make
sudo checkinstall
```

Now the .deb package should be on the source folder.
If you want a more complicated but better way you can consult this guide [COLOR="Red"][here]("https://wiki.ubuntu.com/PackagingGuide/Basic?action=show&redirect=HowToBuildDebianPackagesFromScratch")[/COLOR]

Cheers

---

