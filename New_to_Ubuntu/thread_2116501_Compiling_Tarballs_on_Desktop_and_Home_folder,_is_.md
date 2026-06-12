---
title: "Compiling Tarballs on Desktop and Home folder, is this bad?"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by Wiking on 2013-02-16
Hi, sometimes I just download a tarball and extract the folder to my desktop or my home folder, and I then compile the program for there. Is that bad?

Does it really matter where I extract the folder? Or where I compile the program?

Can I delete the extracted folder after installing?

---

### Post by HermanAB on 2013-02-16
Howdy,

If the program has a proper Makefile, then nothing happens to your system until you run 'make install', so whichever way you experiment is fine.

However, if you are using your computer for something important besides software R&D work and you are worried about breaking it, then you should install Virtualbox and create a virtual machine for software development work.  That way, your base system remains safe.  This is what most serious developers do.

---

### Post by fdrake on 2013-02-16
> **Wiking said:**
> Hi, sometimes I just download a tarball and extract the folder to my desktop or my home folder, and I then compile the program for there. Is that bad?

Does it really matter where I extract the folder? Or where I compile the program?

Can I delete the extracted folder after installing?
pretty soon you'll have software in the desktop, you documents' folder, your home dir, downloads dir  and so on.... A mess to find what you need

usually users should compile they software in /usr/loacal/<specific subfolder> (if it's a lib in /lib, if it's a code into src etc..)
when you compile a software is always a good ide to save the tar archive and the source code(the config/make file , in order to make uninstall easier in the future)

I usually choose /usr/local/share
that way other users can see it and use it without touching the system tools.

---

### Post by oldos2er on 2013-02-16
> **Wiking said:**
> Hi, sometimes I just download a tarball and extract the folder to my desktop or my home folder, and I then compile the program for there. Is that bad?

No, assuming you trust the source code.

> **Wiking said:**
> Does it really matter where I extract the folder? Or where I compile the program?

I create folders below my ~/Downloads/ for this purpose.

> **Wiking said:**
> Can I delete the extracted folder after installing?

I usually keep these folders in case I want to uninstall the software later on with **sudo make uninstall**

---

### Post by andrew.46 on 2013-02-19
Perhaps you could emulate a customary Slackware practice and perform the actual compilation in /tmp. Not normally done in Ubuntu but it might be a sound practice to at least experiment with?

---

### Post by Paqman on 2013-02-19
> **Wiking said:**
> Hi, sometimes I just download a tarball and extract the folder to my desktop or my home folder, and I then compile the program for there. Is that bad?


If you're doing it a lot, probably yes.

Linux distros like Ubuntu have a sophisticated package manager built in. The package manager constantly juggles a complex web of dependencies between all the software on your machine and keeps everything running stably. Downloading tarballs and compiling them circumvents that package management system, and can cause the dependency system to break.

That's not going to cause any catastrophic damage, things will just not work properly. But if you want a stable system it's always best to use the package manager to install software. If you need a package that's not in the repos, try to find a .deb or a PPA for it rather than a tarball.

---

### Post by Zill on 2013-02-19
> **Paqman said:**
> ...If you need a package that's not in the repos, try to find a .deb or a PPA for it rather than a tarball.
+1
For a "typical" home user the compilation of tarballs is both unnecessary *and* undesirable.  It is far better to use a package from the repos as this ensures that all the necessary dependencies are available or will be installed as required.  Personally, I haven't compiled software for many years as I prefer to avoid hassle and keep my systems stable!

---

### Post by Kov3nant on 2013-02-19
I always compile mine in ~/builds/app_name a habit I picked up using other distros. Keeps everything nice and organized.

---

### Post by andrew.46 on 2013-02-19
I have to mildly disagree with those who advocate against compiling at all. It can be done safely and can be integrated easily enough with the Ubuntu package manager. Times to consider compiling would include:

[LIST=1]
[*]A newer version of your favourite software is not included with your current flavour of Ubuntu.
[*]....and you are not keen on PPAs...
[*]You want to add in an option that has not been compiled into the repository version
[*]You want to experiment a little :)
[/LIST]

My own MPlayer guide is an example of all of these features rolled into one and I give it some advertising here:

[https://help.ubuntu.com/community/Compiling%20MPlayer](https://help.ubuntu.com/community/Compiling%20MPlayer)

---

### Post by Zill on 2013-02-19
> **andrew.46 said:**
> I have to mildly disagree with those who advocate against compiling at all. It can be done safely and can be integrated easily enough with the Ubuntu package manager...
I'm sorry but I fail to see *how* compiled software integrates with the package manager.  Packages automatically receive security updates whereas compiled software remains outside this system and can only be updated manually.  Keeping track of manually installed software is a nightmare!

I agree that if a user really *needs* the "latest and greatest" then compiling may be appropriate as PPAs *can* be from dubious sources.  However, if a stable system is required then I advise always keeping well behind the "latest and greatest" software to avoid problems.

Experimentation is fine but, I suggest, not on a critical system.  Either use a Virtual Machine or, ideally, a totally different "play" system.

---

### Post by andrew.46 on 2013-02-19
> **Zill said:**
> I'm sorry but I fail to see *how* compiled software integrates with the package manager.  Packages automatically receive security updates whereas compiled software remains outside this system and can only be updated manually.  Keeping track of manually installed software is a nightmare!

In the example I gave you can see that a judicious use of checkinstall and a close attention to the version numbering can integrate quite nicely with the package manager.

---

### Post by Zill on 2013-02-19
andrew.46:  I agree that checkinstall can make a "pretend" version of a deb package but it still has the disadvantage of not being able to automatically update along with "real" deb packages that are from an Ubuntu repository.

I am unsure of exactly how a checkinstall deb package handles dependencies.  Installing from source can quickly get you in "dependency hell" so does checkinstall have the same problem?

---

### Post by andrew.46 on 2013-02-19
> **Zill said:**
> andrew.46:  I agree that checkinstall can make a "pretend" version of a deb package but it still has the disadvantage of not being able to automatically update along with "real" deb packages that are from an Ubuntu repository.

If the version numbers given by checkinstall are done properly the repository version will upgrade the checkinstall version if the repository package has a more recent version number.


> I am unsure of exactly how a checkinstall deb package handles dependencies.  Installing from source can quickly get you in "dependency hell" so does checkinstall have the same problem?

Checkinstall does negligible dependency tracking hence the packages produced with checkinstall are not really portable. It is a great tool but a little limited...

One trick with dependencies when you are compiling, if you do not wish to replace or upgrade a system library, is to manipulate the PKG_CONFIG_PATH path. I have used this technique here for example:

[https://help.ubuntu.com/community/CompilingTransmission](https://help.ubuntu.com/community/CompilingTransmission)

to avoid any possible problems with the *system* libevent. So it can all be done with a degree of caution and preferably with the aid of a decent guide :)

---

### Post by Zill on 2013-02-20
andrew.46:  Thank you for the clarification re checkinstall and I agree that there is a (limited) place for compiling from source, with or without the aid of checkinstall.

However, for newbies in particular, I do suggest that they will have far fewer problems if they avoid this until they have considerable experience.  Sticking to the standard package manager tools should cause far less hassle. ;-)

---

### Post by andrew.46 on 2013-02-20
> **Zill said:**
> However, for newbies in particular, I do suggest that they will have far fewer problems if they avoid this until they have considerable experience.  Sticking to the standard package manager tools should cause far less hassle. ;-)

I would certainly agree with this :)

---

