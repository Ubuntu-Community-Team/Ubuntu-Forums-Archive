---
title: "Installing Digikam"
date: 2018-05-12
forum: New to Ubuntu
---

### Post by Dan_kesson on 2018-05-12
I just installed Ubuntu on my laptop and the installation went well.
I would like to install Digikam 5.9.0. I downloaded the file (digikam-5.9.0-01-x86-64.appimage) from their homepage. I right clicked and changed to "Allow executing file as program" but nothing happens.

I also tried running it from the terminal:


```
./digikam-5.9.0-01-x86-64.appimage
```

I got the following reply:

```
-- digiKam AppImage Bundle
-- Use 'help' as CLI argument to know all available options
digikam: error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory
 
```

I'm a newbe to Linux so I would need to a simple answer :)

---

### Post by sevendogsbsd on 2018-05-12
FYI, Digikam has a very large number of dependencies on the KDE desktop environment, none of which are installed by default on Ubuntu. Is Digikam available in the Ubuntu software "store"? I would not attempt to install software in the manner you described but only use the Ubuntu software app or synaptic.

---

### Post by cruzer001 on 2018-05-12
I think you should of installed it from Ubuntu software repositories.

```
sudo apt install digikam
```

If you feel you need the latest version and wish to persue this then check if libopenal1 is installed.

```
sudo apt install libopenal1
```

And I'm not sure how well KDE plays with Gnome these days.

[https://packages.ubuntu.com/bionic/digikam](https://packages.ubuntu.com/bionic/digikam)

---

### Post by sevendogsbsd on 2018-05-12
OP - cruzer001 makes a good point: you may end up with a large number of KDE applications installed because the dependencies on the KDE desktop are very heavy.

---

### Post by ajgreeny on 2018-05-12
As others have said you really need to install digikam from the repos; in doing do it will pull in a huge number of dependencies and only you can make the choice of whether or not it's worth it, and if you wish to continue.

I have used it in my non-KDE versions of Ubuntu for a long time now as well as kmymoney, another KDE package and I definitely feel it is worth the use of my space as I much prefer both of those applications to any others in the repos.

Don't forget that simply installing dependencies to your system does not slow it down nor add to a central registry as happens in Windows; they just use space on the disk.
As a test case I have just gone through the process using the -s option (simulate) on my VM of a vanilla install of Ubuntu 18.04; it would need downloads of 211 extra packages and 193 MB.

Your choice!  If you really want it install it.  It works the same as in KDE as far as I'm aware, though it is many years since I use KDE.

---

### Post by Dan_kesson on 2018-05-12
It helped to install libopenal1. Thanks.

---

### Post by monkeybrain20122 on 2018-05-12
Actually I would differ from others. I think an appimage is better because it is more up to date (repo version is old unless you find a ppa) and you don't need to install a ton of KDE dependencies, a lot cleaner (I use appimage for krita) As you found out all you need is to install libopenal rather than 300 MB of kde dependencies which you don't care for if you install from the repo

---

### Post by ajgreeny on 2018-05-13
> **monkeybrain20122 said:**
> Actually I would differ from others. I think an appimage is better because it is more up to date (repo version is old unless you find a ppa) and you don't need to install a ton of KDE dependencies, a lot cleaner (I use appimage for krita) As you found out all you need is to install libopenal rather than 300 MB of kde dependencies which you don't care for if you install from the repo
You may not need to install a lot of KDE dependencies if you use the appimage as I assume it is totally self-contained, but note that the appimage itself is 380MB, though I have no idea how large it is when installed, and have never used an appimage.

---

### Post by monkeybrain20122 on 2018-05-13
> **ajgreeny said:**
> You may not need to install a lot of KDE dependencies if you use the appimage as I assume it is totally self-contained, but note that the appimage itself is 380MB, though I have no idea how large it is when installed, and have never used an appimage.

The appimage doesn't need installation, it is self contained and all in one place. Don't work, just delete it. I have a big /home partition but a small /root so a huge download into /home does not have the same effect as a huge download in /usr. Also I like to keep unnecessary kde things separately from the system and don't need to update them etc.

---

### Post by ajgreeny on 2018-05-14
> **monkeybrain20122 said:**
> The appimage doesn't need installation, it is self contained and all in one place. Don't work, just delete it. I have a big /home partition but a small /root so a huge download into /home does not have the same effect as a huge download in /usr. Also I like to keep unnecessary kde things separately from the system and don't need to update them etc.
Yes, so I subsequently found!

You just make the appimage you have downloaded executable and either double click it or create a .desktop file, a launcher, pointing to it.

---

### Post by monkeybrain20122 on 2018-05-14
> **ajgreeny said:**
> Yes, so I subsequently found!

You just make the appimage you have downloaded executable and either double click it or create a .desktop file, a launcher, pointing to it.

Actually you don't need to create a .desktop file, after the first launch by double clicking it will place a .desktop file in .local/share/applications, you just need to go there and make it executable. (In 18.04 gnome shell you need to do an extra step of clicking it and then give it permission to launch as "trusted", kind of stupid. If I mark something as executable of course I want to launch it!)

---

### Post by cruzer001 on 2018-05-14
Is bintray.com the place to go for appimages?

[https://bintray.com/probono/AppImages](https://bintray.com/probono/AppImages)

---

### Post by monkeybrain20122 on 2018-05-15
> **cruzer001 said:**
> Is bintray.com the place to go for appimages?

[https://bintray.com/probono/AppImages](https://bintray.com/probono/AppImages)

I would only trust appimages published by the developers of the software. e.g digikam, krita.

---

### Post by ajgreeny on 2018-05-15
> **monkeybrain20122 said:**
> I would only trust appimages published by the developers of the software. e.g digikam, krita.
Same here.

Go to 
[https://download.kde.org/stable/digikam/digikam-5.9.0-01-x86-64.appimage](https://download.kde.org/stable/digikam/digikam-5.9.0-01-x86-64.appimage) 
for the 64bit version or
[https://download.kde.org/stable/digikam/digikam-5.9.0-01-i386.appimage](https://download.kde.org/stable/digikam/digikam-5.9.0-01-i386.appimage)
for the 32bit version

---

### Post by cruzer001 on 2018-05-15
Appimage, snap, flatpacks

Wonder whats next

---

### Post by monkeybrain20122 on 2018-05-15
> **cruzer001 said:**
> Appimage, snap, flatpacks

Wonder whats next

Flatpacks and snaps are new, supposed to be able to update. Appimages have been around for a while, it is static. To "upgrade" you download a new one and delete the old one. Also  they don't have the confinement mechanisms for Snap and Flatpak.

One use of appimages would be to distribute old software that doesn't run with new OS, e.g  Nightingale the music player, it has been dead for a while, you can't even compile it from sources for Ubuntu > 16.04 with system libs, but there is an appimage that runs in 18.04.

---

