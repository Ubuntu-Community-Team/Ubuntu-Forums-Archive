---
title: "Newbie looking for gimp"
date: 2020-07-01
forum: New to Ubuntu
---

### Post by nikaron66 on 2020-07-01
Trying to download gimp and got messege "/usr/share/app data" no such file I know what this means but afraid to put wrong thing in command, just need to know what to type

---

### Post by SeijiSensei on 2020-07-01
```
sudo apt install gimp
```
You'll be prompted to enter your login password.

That will run the apt program which manages "packages" like gimp.  Running with sudo grants the program administrative privileges.  Without them, apt would not be able to write into the directories it needs to access.

As a general rule, use apt or the graphical package manager in your version of Ubuntu to handle all installation and removal tasks. It is exceedingly rare that you would need to download a package and install it manually outside the apt system.

---

### Post by TheFu on 2020-07-01
With most linux distros, you don't directly download software. Use the package manager:
```
sudo apt  install gimp
```

Learn about APT, the package management system that Ubuntu uses, so you understand why it is superior to other software management systems.  Basically, something installed through APT (apt, apt-get, synaptic, aptitude) will automatically get bug and security fixes through the normal OS patching provided.

The slight negative for APT is that the current package in a distro should only get security and major bug fixes, not new releases. For those, we need to add a PPA into our APT install.  Then the PPA version will need to be maintained by that PPA team. PPAs expand the normal patching to external, non-Canonical, teams. This brings a little risk, so be certain the team/person running the PPA is trustworthy. 

There are other ways to install newer versions of software using flatpak, snaps and AppImages, but these each bring some issues.  For me, the issues they bring outweigh having slightly older versions of the software that is stable. But we are all different.  If you want the snap, use:
```
sudo snap install gimp
```

For The Gimp, 
the APT version in 20.04 is: 2.10.18-1
the snap version is 2.10.20.

Does that slight difference matter?

For 16.04, the APT version is: 2.8.16 which could definitely matter for features to some. It doesn't to me.

A warning about using "Software Center" to install programs.  More and more, Canonical has been pushing snap packages, so the Software Center will show snaps to be installed. I've never used *Software Center* because of my technical issues with snaps. If there is a way to tell that a package is a snap or Debian package in that GUI, I don't know.  Snaps include mandatory constraints which means access to any files outside your HOME is prevented.

---

### Post by SeijiSensei on 2020-07-01
Personally, I think snaps are the work of the devil and would never recommend installing them.

---

### Post by monkeybrain20122 on 2020-07-01
Gimp is also available as a flatpak (2.10.20) [https://flathub.org/apps/details/org.gimp.GIMP](https://flathub.org/apps/details/org.gimp.GIMP)
flatpak is similar to snap but in my experience works better, it doesn't mount a lot of volumes like snap. A problem of these sandboxed apps is access to file system and external devices, in flatpak you can control it through an easy gui called flatseal (also installed via flatpak) In snap there is no unify way for this kind of control.

If you have Ubuntu 20.04 (18.04?) you can install the package gnome-software-plugin-flatpak via apt then just go to the site above and click install, gnome-software will pop up and install it for you. You may have to restart the computer to find the app though.

However, sandboxed apps (like snap and flatpak) have issues integrating with some external plugins e.g gimp flatpak (and snap) can't find [darktable]("https://gitlab.gnome.org/GNOME/gimp/-/issues/4666").

There is a [ppa]("https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp") that gives you the best of both worlds, you get the latest and it is well integrated with the system, but the maintainer hasn't upgraded his version for a while. Now its version for focal is older than the official repo's (though it may resume updating later)

---

### Post by monkeybrain20122 on 2020-07-01
> **TheFu said:**
> 

If there is a way to tell that a package is a snap or Debian package in that GUI, I don't know.  Snaps include mandatory constraints which means access to any files outside your HOME is prevented.

Yes. You can click the application's name and read the descriptions, it shows you the publisher, if it is something like ubuntu focal then it is deb, if it says snapcraft than it is a snap.

---

### Post by nikaron66 on 2020-07-01
Thank you, job done with "sudo apt install" I am just still overly cautious

---

### Post by TheFu on 2020-07-01
> **nikaron66 said:**
> Thank you, job done with "sudo apt install" I am just still overly cautious

This question means you could read a primer about using Linux distros for basic stuff.  On most desktops there in an introduction for how to do things which would have clearly said how to install software using the package manager for that specific desktop.  There's also the Ubuntu Desktop Guide - [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)
or [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)

---

### Post by SeijiSensei on 2020-07-02
The Ubuntu repositories are the safest source of packages.  Third-party "repositories" are more problematic, but if they're supported by the projects themselves (e.g., Oracle/VirtualBox or Google Chrome), I don't have a problem trusting them.  Downloading and installing software from random sources is much more dicey.  For one thing, programs on *nix systems typically rely on existing "libraries" for many of their functions. Software from the repositories is pretty much guaranteed to work together with the libraries on the system; programs from other sources may not and may instead throw "dependency" errors.

---

