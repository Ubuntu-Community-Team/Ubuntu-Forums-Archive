---
title: "Where is the xserver-xorg?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by johanang on 2008-10-14
I have downloaded, loaded the newest Ubuntu server addition.

If i Type 'sudo aptitude' to open aptitude (a text-based package manager)

And Search for the package "xserver-xorg. This package is not found. As far as i understand to use fluxbox you first have to have this installed?

---

### Post by Nxion on 2008-10-14
What you could do is this:

```
sudo apt-get install fluxbox fbconf fbmenu
```

This should pick up ALL the dependencies that you need to run it.

Hope that helps,
Nx

---

### Post by johanang on 2008-10-14
Reading package list... DOne
Building dependency tree
reading state information ... done
E: Couldn't find package fluxbox

I dont believe i have any of the packages.. maybe it is because i have the lastest version???

---

### Post by DGortze380 on 2008-10-14
> **johanang said:**
> Reading package list... DOne
Building dependency tree
reading state information ... done
E: Couldn't find package fluxbox

I dont believe i have any of the packages.. maybe it is because i have the lastest version???

are you connected to the internet? Have all the correct repositories active (ie uncommented).

---

### Post by jerome1232 on 2008-10-14
Well make sure universe is enabled, just edit your sources.list and uncomment the sections the end with the word 'universe'

```
sudo nano /etc/apt/sources.list
```

then update the list, and try and download it.

```
sudo apt-get update
sudo apt-get install fluxbox fluxconf
```

by the way when I search for fluxbox these are the packages that come up.
You might want fbpager as well.

```
apt-cache search fluxbox
alltray - Dock any program into the system tray
backstep - Draws icons for minimized windows on your desktop
bbmail - Mail notifier for Blackbox/Fluxbox
bbpager - Pager for the blackbox and fluxbox window managers
bbrun - A tool for the blackbox/fluxbox window managers that runs commands
bbtime - Time tool for the blackbox/fluxbox window managers
fbpager - a pager application for the Fluxbox window manager
fluxbox - Highly configurable and low resource X11 Window manager
fluxconf - FluxBox configuration utility
gsetroot - a C/Gtk-based front-end for Esetroot
kdocker - minimize all applications to system tray
pekwm - Fast & Light WindowManager
```

---

### Post by johanang on 2008-10-14
I did as you said. when i did the apt-get update it said it failed to download. Funny thing is i can ping the ip address 91.189.88.37 or any of them that show up.

---

### Post by jerome1232 on 2008-10-14
That is odd, Can you show us your sources.list file?
```
cat /etc/apt/sources.list
```

Also can you ping out by name (us.archive.ubuntu.com for example?) could be a simple dns issue.

---

### Post by johanang on 2008-10-14
Sweet how do i use/access flux box.. I installed it and fbpager.

It was a proxy. Apps updated and installed now im installed fluxbox.. Thank you so so much jerome123! And also thank you for teaching me to use teh nano editor.

---

### Post by johanang on 2008-10-14
Cannot connect to Xserver when i type fluxbox

---

### Post by phidia on 2008-10-14
Try > startx

---

### Post by johanang on 2008-10-14
Keep in mind this is the server addition.
I installed startx and it gives me a fatal server error no valid fontpath could be found giving up.
/usr/bin/startx line 166 xauth command not found

---

### Post by johanang on 2008-10-14
startx did not work after i installed it. This is the newest and lastest server im running.

---

### Post by phidia on 2008-10-14
> **johanang said:**
> startx did not work after i installed it. This is the newest and lastest server im running.

Maybe you need to create your xorg.conf? Note: I didn't see post #11 when I 1st responded

You may need to pull in all the packages for an xserver-it seems like installing a DE would have done that but it may not have.

> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by RedSquirrel on 2008-10-15
> **johanang said:**
> startx did not work after i installed it. This is the newest and lastest server im running.
If you haven't done so already, you need to install the package named **xorg**.

```
sudo apt-get install xorg
```

Fluxbox doesn't pull in the xorg package. ;)

---

### Post by jerome1232 on 2008-10-15
I find it odd that fluxbox doesn't have xorg as a dependency, worth a bug report maybe?

---

### Post by RedSquirrel on 2008-10-15
> **jerome1232 said:**
> I find it odd that fluxbox doesn't have xorg as a dependency, worth a bug report maybe?
Yeah, I suppose it would be nice if installing fluxbox pulled in xorg. I think there is a bug report for it, but my memory is fuzzy on this.

---

