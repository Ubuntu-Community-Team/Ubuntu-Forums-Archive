---
title: "apt &amp; dpkg"
date: 2010-10-19
forum: Packaging and Compiling Programs
---

### Post by J05HYYY on 2010-10-19
Hello,

I am trying to get deb files using apt and install them using dpkg.

For instance when I do:
```
sudo apt-get -d install xyz
```
...  it installs the debs for package xyz in "/var/cache/apt/archives".

The problem comes when using dpkg. If there is more than one deb file, how do I know what order to install them in? Can apt tell me what order to install the debs or am I supposed to just guess?

Any help much appreciated.

---

### Post by MadCow108 on 2010-10-21
why not install them directly with apt?

dpkg is the low level program used e.g. for the installing.
The dependency resolving is done by the higher level programs like apt, aptitude, gdebi, dselect ... which then call dpkg in the right order.

if you want to install local packages probably gdebi is one of the easiest solutions.
But you can also set up apt and the others to do it with a little more effort (+manpages/google).

---

### Post by J05HYYY on 2010-10-27
I want to install on computers which don't have an internet connection. 
I'm trying to download online, copy across, then install offline.
Problem is that when I use dpkg, it doesn't install in the correct order, resulting in missing dependencies.

---

### Post by StephenDavison on 2010-10-27
Have you tried using the --ignore-depends or --force-depends options to dpkg?

---

### Post by MadCow108 on 2010-10-28
I think that could be dangerous on certain packages.
A package may require one if its dependencies to configure itself.
If that does not exist you may create problems.

Better stick to the local alternatives I posted before.
(or permutate your dpkg installation list until they install correctly ;) )

---

### Post by CharlesA on 2010-10-28
What happens if you throw whatever packages into /var/cache/apt/archives/ ?

It'll pull them from there if you use apt-get.

---

### Post by mcduck on 2010-10-28
> **J05HYYY said:**
> Hello,

I am trying to get deb files using apt and install them using dpkg.

For instance when I do:
```
sudo apt-get -d install xyz
```
...  it installs the debs for package xyz in "/var/cache/apt/archives".

The problem comes when using dpkg. If there is more than one deb file, how do I know what order to install them in? Can apt tell me what order to install the debs or am I supposed to just guess?

Any help much appreciated.

If you have all the dependencies, simple "sudo dpkg -i *.deb" (in same directory where the packages are, of course) should work just fine to install them all in correct order.

If you get an error about missing dependency with that command then the problem is not the order but that you really *are* missing some dependency package.

---

### Post by SevenMachines on 2010-10-28
i think gdebi from the command line does what you looking for? i think it might anyway.. :)

---

### Post by J05HYYY on 2010-10-28
Nope,

```
dpkg -i *.deb
```

doesn't seem to do it. I am getting a lot of

```
xyz package depends on abc but is not installed
```

Here's the command I'm using to download the debs:

```
sudo apt-get -d install pulseaudio pavucontrol xorg wicd fvwm-crystal gnome-menus pcmanfm tango-icon-theme wmbattery leafpad firefox vlc amsn openoffice.org xdm arandr htop kolourpaint4 linphone isomaster brasero --install-recommends --reinstall -y

```

After running this command, I am copying /var/cache/apt/archives to a CD. Note the host is using ubuntu netbook remix and the slave is running cli version of ubuntu.

Any help, much appreciated.

---

### Post by CharlesA on 2010-10-28
Is the slave running a different architecure? 64-bit vs 32-bit, netbook remix is 32-bit.

To fix the dependancy problems you'd need to run this:

```
sudo apt-get install -f
```

Also check here: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by mcduck on 2010-10-29
> **J05HYYY said:**
> Nope,

```
dpkg -i *.deb
```

doesn't seem to do it. I am getting a lot of

```
xyz package depends on abc but is not installed
```

Here's the command I'm using to download the debs:

```
sudo apt-get -d install pulseaudio pavucontrol xorg wicd fvwm-crystal gnome-menus pcmanfm tango-icon-theme wmbattery leafpad firefox vlc amsn openoffice.org xdm arandr htop kolourpaint4 linphone isomaster brasero --install-recommends --reinstall -y

```

After running this command, I am copying /var/cache/apt/archives to a CD. Note the host is using ubuntu netbook remix and the slave is running cli version of ubuntu.

Any help, much appreciated.
That sounds like your missing deps are something that is installed by default on the Netbook version, but not on your minimal install.

Like I said, dpkg will easily sort out the correct install order if you just throw all the packages at it at the same time, so any dependency error would really mean that you *are* missing some dependency.

---

