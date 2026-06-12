---
title: "How to get edgy's neat usplash in dapper"
date: 2006-09-25
forum: Outdated Tutorials &amp; Tips
---

### Post by jamadagni on 2006-09-25
[color="red"]**Warning:** 

You follow this howto at your own risk. It worked on my system, but may not do so on yours.

This procedure may also cause shutdown/reboot to hang, though this is not confirmed. Only the courageous proceed![/color]

**Preliminary:**

You will need to have installed the packages dpkg-dev and fakeroot and of course all the dev files required to compile the source packages used here, which you will have to install using sudo apt-get install when you get an error message saying that such-and-such a package is needed.

**Working procedure:**

Download to an empty working directory, the dsc and tar.gz files from:

[http://packages.ubuntu.com/edgy/source/usplash](http://packages.ubuntu.com/edgy/source/usplash)

and from one of the following four pages as per your variant of Ubuntu:

Ubuntu: [http://packages.ubuntu.com/edgy/source/usplash-theme-ubuntu](http://packages.ubuntu.com/edgy/source/usplash-theme-ubuntu)
Kubuntu:  [http://packages.ubuntu.com/edgy/source/kubuntu-default-settings](http://packages.ubuntu.com/edgy/source/kubuntu-default-settings)
Xubuntu: [http://packages.ubuntu.com/edgy/source/xubuntu-artwork](http://packages.ubuntu.com/edgy/source/xubuntu-artwork)
Edubuntu: [http://packages.ubuntu.com/edgy/source/edubuntu-artwork](http://packages.ubuntu.com/edgy/source/edubuntu-artwork)

Now do:

```
dpkg-source -x usplash_0.4-29.dsc
```

and do the same for the other dsc file which corresponds to your distro. Now do:

```
cd usplash-0.4
dpkg-buildpackage -rfakeroot
```

You will get an error about a key not being available. Ignore it. Then do:

```
cd ..
sudo dpkg -i usplash*.deb
```

Then descend to the other subdirectory of your working directory and again do:

```
dpkg-buildpackage -rfakeroot
```

Again ignore the error about the key. Then do cd .. and use sudo dpkg -i to install the appropriate deb which should have been created:

Ubuntu: usplash-theme-ubuntu
Kubuntu: kubuntu-artwork-usplash
Xubuntu: xubuntu-artwork-usplash
Edubuntu: edubuntu-artwork-usplash

**Known bugs:**

During shutdown/reboot, the usplash may not appear except briefly at the end. [This bug]("https://launchpad.net/distros/ubuntu/+source/usplash/+bug/62302") has been reported.

---

### Post by paulrobert_a on 2006-11-06
I had done as described ran into a wee problem, usplash didn't actually work once installed, but I figured it out.  You need to specify a vga code within your grub config.

For best results I'd recommend you simply follow this [guide]("http://ubuntuforums.org/showthread.php?t=289335") to make sure the vga code isn't overwritten because of a kernel upgrade 


**VGA Code Table**
[HTML]Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795[/HTML]

---

