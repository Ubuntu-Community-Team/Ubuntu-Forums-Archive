---
title: "Install X on server?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by tstack77 on 2008-10-15
I have a simple NAS setup that I would like to get X loaded up on to get a graphical user interface for the times I want one.

I don't want to install the full ubuntu-desktop, just the base.

Is this possible?

---

### Post by Sorivenul on 2008-10-16
As far as I know
```
sudo apt-get install xorg
```
should do the trick.

---

### Post by niteshifter on 2008-10-16
Hi,

Installing xorg will get you the base - the very basic base. Xorg can do window management, but it ain't pretty. If you want a lightweight window manager for GUI use that looks better look into Xcfe or Fluxbox.

---

### Post by stephanvaningen on 2008-10-16
like
```
sudo apt-get install gnome
```
or
```
sudo apt-get install kde
```

---

### Post by tstack77 on 2008-10-16
Thanks guys, close to what I'm looking for. I should have been more clear that I want to add the standard ubuntu-desktop, but only with the necessary dependencies (the red dependencies [HERE]("http://packages.ubuntu.com/hardy/ubuntu-desktop"))

If I apt-get ubuntu-desktop I get everything and space on my 4gb cf card is somewhat at a premium.

---

### Post by LowSky on 2008-10-16
sudo apt-get install ubuntu-minimum

then install xfce or ICEwm or Fluxbox

sudo aptitude install xfce4 

sudo aptitude install icewm iceconf icepref iceme icewm-themes 

sudo aptitude install fluxbox fluxconf

---

### Post by tstack77 on 2008-10-16
Lowsky, I'm pretty sure you mean "ubuntu-minimal" but I already have that installed with server. I'm starting to think that there isn't a "clean" gnome-desktop option. I guess the best bet is to install gnome and add the tools I deem necessary.

---

### Post by RedSquirrel on 2008-10-16
tstack77,

```
sudo apt-get install --no-install-recommends ubuntu-desktop
```should do what you want. Personally, I prefer to install the [gnome-core]("http://packages.ubuntu.com/hardy/gnome-core") package and build up from there (not on a server though, just for a desktop ;)).

---

### Post by tstack77 on 2008-10-16
Thanks! Trying your method of installing gnome-core first then working up from there. Great to learn this route!

EDIT: Looking over the packages of gnome-core and I see the suggestion for the gnome-desktop-environment. Will this be installed with apt-get install gnome-core?

---

### Post by RedSquirrel on 2008-10-17
> **tstack77 said:**
> Thanks! Trying your method of installing gnome-core first then working up from there. Great to learn this route!

EDIT: Looking over the packages of gnome-core and I see the suggestion for the gnome-desktop-environment. Will this be installed with apt-get install gnome-core?

Suggested packages are not installed by default.

apt-get will tell you the packages it wants to install, so you will be able to see what is to be included.

To be extra safe, you can verify before you install anything with, for example, the --simulate option:

```
 sudo apt-get --simulate --no-install-recommends install gnome-core
```


Have a look at the man page for apt-get (or aptitude if you prefer that).

```
man apt-get
``````
man aptitude
```


Note that the gnome-core package is fairly basic, but that seems to be what you are looking for. You'll have to install the fancy Ubuntu artwork and so on yourself. :)

---

### Post by tstack77 on 2008-10-17
Thanks for the info, but of course nothing comes easy!

I have installed gnome-core but now cannot switch to the gui. I have tried alt+F7 (and ctrl+Alt+F7) without luck. After a quick google search I found that I should install xinit and then run the startx command...again no love with 'cannot stat /etc/X11/X (No such file or directory)'.

RedSquirrel, what are the steps you take on a fresh install? I tried to start from scratch with the alternate cd and simply install only the command line interface. I then tried the gnome-core but I couldn't connect to the internet (not even able to ping my router). 

I'd be lying if I said I wasn't enjoying this simply because I've learned so much by trying this already, but I really need to get something working soon or I'll go nuts :)

---

### Post by RedSquirrel on 2008-10-18
> **tstack77 said:**
> Thanks for the info, but of course nothing comes easy!

I have installed gnome-core but now cannot switch to the gui. I have tried alt+F7 (and ctrl+Alt+F7) without luck. After a quick google search I found that I should install xinit and then run the startx command...again no love with 'cannot stat /etc/X11/X (No such file or directory)'.

RedSquirrel, what are the steps you take on a fresh install? I tried to start from scratch with the alternate cd and simply install only the command line interface. I then tried the gnome-core but I couldn't connect to the internet (not even able to ping my router). 

I'd be lying if I said I wasn't enjoying this simply because I've learned so much by trying this already, but I really need to get something working soon or I'll go nuts :)

For the graphical part of your problems, you need to install xorg.

```
sudo apt-get install xorg
```Your X *may* work without the file /etc/X11/xorg.conf, but you can generate a basic one with:

```
sudo dpkg-reconfigure xserver-xorg
```After that, you should be able to get GNOME started by running:

```
startx
```


When I install Ubuntu:

1. Install the command-line system using the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") (which should be equivalent to installing the command-line system using the alternate CD + upgrading to the latest packages).

2. 
```
sudo apt-get update
sudo apt-get upgrade 
```(There probably won't be any upgrades since the minimal CD installer pulls in the latest packages, but it's nice to be sure.)

3. Install the xorg package.

4. Install a nice window manager, for example, openbox.

```
sudo apt-get install openbox
```5.
```
startx
```6. Make sure things are working as expected.

7. Fire up a terminal and install more packages for my desktop (e.g., gnome-core, xfce4, kde-core, fluxbox, firefox,...).



For the networking problem you are experiencing, you should probably start another thread. I have a router and I have never had any networking issues. While I'm in the Ubuntu installer, I allow it to setup the network using DHCP. Once the installation is complete, DHCP is setup automatically in the installed system.

---

