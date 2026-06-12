---
title: "HELP: accidentally deleted packages"
date: 2018-11-21
forum: New to Ubuntu
---

### Post by imgeka on 2018-11-21
Hello,

I accidentally deleted the GTK-pixbuf packages on my  Xubuntu 18.04 via Synaptics. I have enclosed screenshots of the packages  I deleted. 

The problem I now have is that I only have the Xterm  terminal at my disposal and I have no idea how to install the packages  via Xterm.

Being completely illiterate with regard to the Linux world, I am need guidance: how can I get the uninstalled packages back?

Please notify me of the exact commands to be typed in the Xterm Terminal in order to get things on track again.

Thanks in advance

---

### Post by Frogs Hair on 2018-11-21
You can install or reinstall with synaptic . Right click on the line including the desired package,  mark for installation, and select apply .

---

### Post by imgeka on 2018-11-21
Synaptics vanished with the packages. Synaptics is no longer there. I only have Xterm.

--

UPDATE: I managed to reinstall Synaptics via Xterm. Will update this post in the next 30 minutes.

---

### Post by Frogs Hair on 2018-11-21
I can't tell from the screen-shots what packages have been removed or are supposed to be installed.

---

### Post by imgeka on 2018-11-21
I have a 4 pages long list of uninstalled packages; they were in my Synaptic Pacage manager history.

Is there a way to reinstall them all at the same time via the terminal?

--

In Synaptic I also get the error message: Could not apply Changes. Fix Broken Packages first.

How can these be fixed? It doesn't work via Synaptic package manager.

---

### Post by imgeka on 2018-11-21
Hello, I can't enter xubuntu now after restart. It does not make it to the log in  screen. The Xubuntu 18.04 Logo is stuck in a loop. What can I do?

---

### Post by MSGone on 2018-11-21
> **imgeka said:**
> Hello, I can't enter xubuntu now after restart. It does not make it to the log in  screen. The Xubuntu 18.04 Logo is stuck in a loop. What can I do?

I'm no expert like some of these guys, but it sounds to me like time for a clean install to start over. I wish I would have been able to help you.

---

### Post by wildmanne39 on 2018-11-22
> **MSGone said:**
> I'm no expert like some of these guys, but it sounds to me like time for a clean install to start over. I wish I would have been able to help you.

Hello, reinstalling the OS is almost never required, please do not suggest this as a fix lightly.

Thanks

---

### Post by The Cog on 2018-11-22
To install packages from the command line (assuming that you can figure out the required package names) just do **sudo apt install** followed by a list of the package names (space separated), e.g.
```
sudo apt install eog gir1.2-gdkpixbuf-2.0
```
Installing a package will also install its dependencies, so if you can find a top-level package (eog perhaps, I don't know) this will save naming lots of other libraries etc. Actually, **sudo apt install ubuntu-desktop** might be all you need if you have not been removing packages since the original install.

---

### Post by Impavidus on 2018-11-22
From these screenshots we can't tell which packages exactly were removed, but as so many packages directly or indirectly depend on libgdk-pixbuf I can tell it must be many packages.

Can you use the grub menu to boot into recovery mode? Then drop to a root shell and mount the filesystem read-write:```
mount -o rw,remount /
```
Now you can examine the log files to find out which packages were removed:```
grep remove /var/log/dpkg.log
```For example, on my system I get```
$ grep remove /var/log/dpkg.log
2018-11-14 10:33:50 startup packages remove
2018-11-14 10:33:50 remove flashplugin-installer:amd64 31.0.0.148ubuntu0.18.04.1 <geen>
2018-11-14 10:38:38 startup packages remove
2018-11-14 10:38:47 remove linux-headers-4.15.0-36-generic:amd64 4.15.0-36.39 <geen>
2018-11-14 10:38:52 remove linux-headers-4.15.0-36:all 4.15.0-36.39 <geen>
2018-11-14 10:38:56 remove linux-modules-extra-4.15.0-36-generic:amd64 4.15.0-36.39 <geen>
2018-11-14 10:39:01 remove linux-image-4.15.0-36-generic:amd64 4.15.0-36.39 <geen>
2018-11-14 10:39:34 remove linux-modules-4.15.0-36-generic:amd64 4.15.0-36.39 <geen>
```telling me that this month the packages flashplugin-installer, linux-headers-4.15.0-36-generic, linux-headers-4.15.0-36, linux-modules-extra-4.15.0-36-generic, linux-image-4.15.0-36-generic and linux-modules-4.15.0-36-generic were removed. Then you can use apt to reinstall those packages:```
apt install package1 package2
```You can list multiple packages on the command line simultaneously or run the command multiple times with different packages. Just install all the packages that were recently removed and hope the package system is in a consistent state.

There is a shortcut though. I suspect that one of the packages that was automatically removed along with libgdk-pixbuf, was xubuntu-desktop. If you reinstall that, you should get a working system back with just one command:```
apt install xubuntu-desktop
```Any packages you added after install that were removed along with libgdk-pixbuf will have to be reinstalled separately.

When you have installed those packages succesfully, you can reboot:```
reboot
```

---

### Post by imgeka on 2018-11-22
I finally managed to access my desktop, so I should be be able to rescue my files. The only problem is that I cannot move to the USB my own files that I had saved in two folders on the desktop. The system says they are read only files. What package could be missing that is preventing me from moving my own files, i.e., what causes the system to identify them as read only files?

---

### Post by imgeka on 2018-11-22
I couldn't follow any of the instructions you gave: terminal says 'unable to correct problems, you held broken packages'

---

### Post by imgeka on 2018-11-22
OK, I finally managed to rescue all my files; thanks to everyone who helped.

---

