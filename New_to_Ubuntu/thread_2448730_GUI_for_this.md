---
title: "GUI for this?"
date: 2020-08-12
forum: New to Ubuntu
---

### Post by ferfykins on 2020-08-12
Do you know if there's a GUI in Xubuntu to see all your installed programs (xchat, discord, etc) and if there's a GUI to uninstall apps you want to unintsall (hexchat for example)

---

### Post by TheFu on 2020-08-12
synaptic?  If it isn't installed already, install it.
Some might be snaps. Doubt any apt tool will show snap package installs.

xubuntu should have some sort of software management tool. I haven't used it in years, but there is an "xubuntu users guide" that google will easily find.

---

### Post by ferfykins on 2020-08-12
> **TheFu said:**
> synaptic?  If it isn't installed already, install it. Some might be snaps. Doubt any apt tool will show snap package installs.  xubuntu should have some sort of software management tool. I haven't used it in years, but there is an "xubuntu users guide" that google will easily find.  Yeah i've tried both..... the software manager for xubuntu doesn't show all installed apps... for example it's not showing vmware  also with synaptic i think that shows everything on linux entirely, not just apps installd.... looks more like stuff i have no idea about... hopefully this makes sense for windows i mean, it shows only the installed apps, not functions of the OS

---

### Post by Impavidus on 2020-08-13
Synaptic shows all software installed from .deb and all software installable from .deb from all repositories it knows about. It doesn't show snaps (but a fresh Xubuntu 20.04 system comes without any snaps) or manually installed stuff. .deb packages can contain user applications, tools, components of the OS or data, or any combination of those, and there's no real distinction between those anyway.

---

### Post by TheFu on 2020-08-13
> **ferfykins said:**
> Yeah i've tried both..... the software manager for xubuntu doesn't show all installed apps... for example it's not showing vmware  also with synaptic i think that shows everything on linux entirely, not just apps installd.... looks more like stuff i have no idea about... hopefully this makes sense for windows i mean, it shows only the installed apps, not functions of the OS

Which is a flaw with Windows.  Inside APT, all packages are treated equally and get updated together, provided the files weren't manually downloaded and manually installed.  But, if you stay within the package management systems, there are over 60K packages to select from and all of those are maintained for bugs and security patches.  If you install any package that way, it will be updated when/if there is any security issue while the OS is under support.  Each package/program doesn't need to have a refresh. It is built-into the OS.

But there are ways we can manually install things from outside APT and the trusted, cryptographically-signed, repos. As soon as we leave the ranch and do that, all bets are off. From that point on, you are responsible for maintaining those programs. Manually downloaded .deb files that get installed may break dependencies for APT and that can get APT into a place where nothing can be upgraded.  Stay within the approved repos and that problem doesn't happen.

Then there are snaps, flatpaks, appimages - these are newer, nearly self-contained, packages that are supposed to run on any system. In general, that happens most of the time.  Snaps and flatpaks come with additional security constraints to limit where on the system access is allowed.  Flatpaks allow some local control over those settings, Snaps do not. All of these are larger than normal APT packages (.deb files in a repo).  AppImages don't updated.  Snaps update whenever they like, without asking and keep multiple copies without asking.  Flatpaks get updated only when requested.  All include dependencies, so a 33MB program can be 900MB to get if you don't have the dependencies already on the system.  All those dependencies have to be loaded into RAM, because they are probably different from what your system already uses, effectively using 2-3x the RAM.  Loading the support libraries into RAM increases startup time for each application.  If you have a Core i7 and 32GB of RAM on a 1TB HDD, none of this probably matters.  OTOH, if, like me, you have a 2GB RAM, 16GB storage Celeron system, it is terrible.
Anyways, to see which programs are installed via snaps, use this command: 
```
snap list --all
```
It might need a sudo first.  I avoid snaps, but Canonical is pushing them in 20.04, really, really, hard.  A fresh install of Ubuntu-Mate includes 3 snaps.  A "Server" 20.04.1 install includes 4 snaps. Because snaps aren't integrated into APT or any front-ends for APT in the shell, we have 2x the package management to run in our weekly patching.

---

### Post by ActionParsnip on 2020-08-13
Why a GUI? Easier to run:
```

dpkg -l | grep ^ii | awk {'print $2'}

```
The thing you are asking for is a list of text so why a GUI? How would it look any different to what the above command gives you?

---

### Post by TheFu on 2020-08-13
People coming from Windows often don't understand the power that plain text can bring to data like this. It is a different way of thinking because they haven't been exposed to the 100+ little text handling tools that EVERY Unix system comes with out of the box
AND
they don't understand how to chain commands together to make something that seems hard, very, very, easy and fast.
It is a different way of thinking. I tried to explain it a few years ago here: 
[https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed)
That article provides a little example that at first seems easier using a GUI, but quickly becomes a hassle.

Another option to using **dpkg** is to use **apt-mark showmanual**. This only shows packages manually installed, not those installed as a dependency.  Of course, the real power comes during backup and restore processing.  For the backups, just save the list created by apt-mark, say pkgs_manual.lst is the filename.  During the restore, after data, settings, and a base OS are installed, feed that list into ... let me get the exact commands:
```
sudo apt-mark manual $(cat pkgs_manual.lst)
sudo apt-get -u dselect-upgrade
```
Basically, wiping the OS, getting all your setting back AND having all programs installed from the package manager repos is about 30 minutes.

Every time I troubleshoot any issue over 30 minutes, I have to think should I just wipe and restore from backups made last night? After all, it is about productivity, not running 50 magical commands to keep/get a system working, right?

---

