---
title: "Install from distro disk"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by Tom_Temple on 2014-07-26
[COLOR=#3F4549][FONT=Helvetica Neue]Hi all I have a few distro disk but never been able to in stall them to my Hard drive...theey look like this on the cd......   gnucash-2.4.4.tarbz2[/FONT][/COLOR]

---

### Post by Tom_Temple on 2014-07-26
[COLOR=#3F4549][FONT=Helvetica Neue]Hi all I have a few distro disk but never been able to in stall them to my Hard drive...theey look like this on the cd......   gnucash-2.4.4.tarbz2[/FONT][/COLOR]

---

### Post by Bashing-om on 2014-07-26
Tom_Temple; Hi !

And the question is ?

Is it your desire to install "buntu ?
For recommendations, supply your hardware specifications please.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all things a re possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by justin-c-hawkins92 on 2014-07-26
I don't understand what you are asking, because the [COLOR=#3F4549][FONT=Helvetica Neue]gnucash-2.4.4.tarbz2 is a package.....unless you burn a .iso img to a cd or dvd and boot it in the bios you won't be able to install the distro. 
[/FONT][/COLOR]

---

### Post by ian-weisser on 2014-07-27
What is a 'distro disk' ?

A *.tar.bz file, sometimes called called a *tarball*, is compressed archive containing multiple files that make up most of a package.
Tarballs come with a README or INSTALL file included that tells you how to install/uninstall the software.

In the Debian / Ubuntu worlds, a .deb file (which is a slightly different compressed archive) is called a *package*.
We don't consider tarballs to be a package here, since Ubuntu's package manager does not handle tarballs.

Packages in Debian / Ubuntu are different from random tarballs you find in the wild. They contain a lot of metadata about the package, it's version, it's dependencies.
Packages in the Ubuntu repositories are built and tested to work with a specific release of Ubuntu. A new version of the package is released with each new version of Ubuntu. These *distro releases* are generally unrelated to the *upstream releases*.

If you are new to Ubuntu, you should be installing proper packages from the Ubuntu repositories (Software Center) using your package manager instead of random tarballs.
You should only manually install software that is unavailable from the Ubuntu repositories.
Unskilled manual installs of random tarballs from the internet is a great way to break your system quickly.

---

### Post by oldos2er on 2014-07-27
> **Tom_Temple said:**
> [COLOR=#3F4549][FONT=Helvetica Neue]Hi all I have a few distro disk but never been able to in stall them to my Hard drive...theey look like this on the cd......   gnucash-2.4.4.tarbz2[/FONT][/COLOR]

Gnucash should be in the repositories. If you're attempting to use APT for cdrom, there are instructions here: [https://help.ubuntu.com/community/AptCdrom](https://help.ubuntu.com/community/AptCdrom)

A little more detail on what exactly you're asking would help.

---

### Post by oldos2er on 2014-07-27
Threads merged. Please don't create more than one thread for the same or similar questions; it's confusing and it dilutes the community's ability to help.

---

