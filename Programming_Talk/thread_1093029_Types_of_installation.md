---
title: "Types of installation"
date: 2009-03-11
forum: Programming Talk
---

### Post by adit on 2009-03-11
I am asking my question with an example.  Installation of firefox 3.0.7 manually.  It requires just extracting the file "firefox-3.0.7.tar.bz2" into one folder 24.5 MB in size.  One can run the program by just clicking the launch icon situated inside the folder.  To uninstall, all that is needed is deleting the folder.  No other part of the system is modified during installation or uninstallation.

What is the name of this type of installation?
I want to write programs that install this way.  Where can I find more information about this?

---

### Post by Krupski on 2009-03-11
> **adit said:**
> I am asking my question with an example.  Installation of firefox 3.0.7 manually.  It requires just extracting the file "firefox-3.0.7.tar.bz2" into one folder 24.5 MB in size.  One can run the program by just clicking the launch icon situated inside the folder.  To uninstall, all that is needed is deleting the folder.  No other part of the system is modified during installation or uninstallation.

What is the name of this type of installation?
I want to write programs that install this way.  Where can I find more information about this?

Firefox (and most other programs) have dependencies (other programs they need to run properly).

Simply typing to install Firefox by itself probably won't work (or else it will fail with dozens of "this depends on that" error messages).

You should use Aptitude or whatever package manager to install apps. Package managers resolve dependencies for you (i.e. they download and install the "extra" stuff your program needs).

[COLOR="Red"][B][CENTER]
_READ WARNING AT THE BOTTOM FIRST!_[/CENTER][/B][/COLOR]

(p.s. if you are trying to force KDE to install Firefox instead of Iceweasel, try this: Rename your /etc/apt/sources.list file to something else (i.e. protect it), then create a new one with this content (cut-n-paste):

```

deb http://ubuntu.media.mit.edu/ubuntu hardy main restricted universe multiverse
deb http://ubuntu.media.mit.edu/ubuntu hardy-updates main restricted universe multiverse
deb http://ubuntu.media.mit.edu/ubuntu hardy-security main restricted universe multiverse

```

Then type "apt-get -V update", then "apt-get -V install firefox".

When it's all loaded, delete your "bogus" /etc/apt/sources.list file and rename your backup to the proper name.

Then, type "apt-get autoremove" which will remove all unused packages that got downloaded in the process of getting Firefox.

You should be back to normal, but with Firefox installed.

[COLOR="Red"]**Note... before you do this, wait for a few replies here. I did the above procedure and it worked, but it *might* be the wrong thing to do and it *might* mess up your system. Get second opinions first.**[/COLOR]

Good luck.

-- Roger

---

### Post by adit on 2009-07-08
I have found answer myself.
> What is the name of this type of installation?Packages that install this way are called static packages
_[http://ubuntuforums.org/showthread.php?t=1206746](http://ubuntuforums.org/showthread.php?t=1206746)_

---

