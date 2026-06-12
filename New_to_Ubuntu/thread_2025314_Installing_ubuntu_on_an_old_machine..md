---
title: "Installing ubuntu on an old machine."
date: 2012-07-14
forum: New to Ubuntu
---

### Post by Balthazar54 on 2012-07-14
I have an old Compaq 5000 series sitting around gathering dust and am planning on installing ubuntu on it.

I plan on using this for playing around with accessing it remotely, sharing it's hard drive with other systems for storage and backup, and sharing it's cd & dvd drive.

Two questions:

Does the fact that it only has .5 gb ram and not the 1 gb in the requirements really matter for use as a server?

When I reformat the hard drive, should I set up a second partition of what is left in addition to the primary partition to use for sharing, or just plan on sharing part of the primary?

---

### Post by oldfred on 2012-07-14
I am not knowledgeable on servers but like to separate system from data. But it may depend more on how large your hard drive is. If small you want the share the unused space. If larger having a 15 to 25GB / partition with only 25% used and a data partition not fully used then may be ok.

If installing server you do not have the full desktop enviroments that add a lot to the system requirements.

For example this installs the full desktop environment including all the applications which you should not need.
lubuntu-desktop (the whole LXDE desktop environment and applications)

But if you want server you can just install the  gui or window manager:
Difference between Windows manager & desktop environment
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)

Lightweight Desktop environment
Ubuntu Server + lxde
works smooth in under 256mb ram on a p2
sudo apt-get install lxde
Or Xfce GUI without any of the associated Xubuntu applications
sudo apt-get install xfce
Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)
window managers like Icewm, Openbox, Fluxbox, and Xfwm
desktop environments are KDE, Gnome, Xfce, Enlightenment, and LXDE

---

### Post by OrangeCrate on 2012-07-14
> **Balthazar54 said:**
> I have an old Compaq 5000 series sitting around gathering dust and am planning on installing ubuntu on it.

I plan on using this for playing around with accessing it remotely, sharing it's hard drive with other systems for storage and backup, and sharing it's cd & dvd drive.

Two questions:

**Does the fact that it only has .5 gb ram and not the 1 gb in the requirements really matter for use as a server?**

When I reformat the hard drive, should I set up a second partition of what is left in addition to the primary partition to use for sharing, or just plan on sharing part of the primary?

> The minimum memory requirement for Ubuntu Server 12.04 is 128 MB of memory.

Other details here:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer)

---

### Post by m3topaz on 2012-07-14
I run Ubuntu servers on old hardware with 512MB RAM. It's possible, but you can max this out if there are lots of things for a web server to do.

I suggest that when you partition the drive, allocate a few GB of swap file. For sharing, I generally map out shares as separate partitions as well - but it's a matter of personal preference for how you like to set that sort of thing up.

---

### Post by Balthazar54 on 2012-07-17
Thanks for the info, folks! Much appreciated.

---

### Post by S2UIRR3L on 2012-07-17
I don't know ANYTHING about servers, but I know that installing Xubuntu 12.04 on my little 512-Mb RAM laptop worked fantastic... Full desktop environment and it's great!

-Leo

---

### Post by d4m1r on 2012-07-17
No, go ahead and use it for a server but I have a few recommendations:

1) Install 11.10 server on it instead (doesn't require PAE which old machines don't have and less resource intensive than 12.04).

2) Don't install a UI (uses too much resources).

3) Don't run too many things at the same time.

My old Dell PC is running 11.10 and only uses 40MB/512MB RAM to serve a static website (.html) via Apache...

---

### Post by alonesurvivor on 2012-07-18
Install Lubuntu, is great distro! Works on crap machine. 

Or Puppy Lucid

---

### Post by The Linuxist on 2012-07-18
Just install Ubuntu Server and then manage it via SSH so you can just stick it under a table somewhere without a monitor. That should run fine with only 512MB RAM. I mean, you can get cloud instances of 12.04 server with 512MB RAM and they work great so should be the same for a physical machine.

With regards to the hard disk partitioning, for server to be used as storage - maybe this?

/boot - 500M
/       - 5G
swap   1G

then make a mount point called /storage and allocate the rest of the disk to that.

---

