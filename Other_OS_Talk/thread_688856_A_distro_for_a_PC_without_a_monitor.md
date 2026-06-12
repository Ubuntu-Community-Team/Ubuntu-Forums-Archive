---
title: "A distro for a PC without a monitor"
date: 2008-02-05
forum: Other OS Talk
---

### Post by Amorphous_Snake on 2008-02-05
I am getting a new PC!!! My ancient Celeron 1.2 GHz, 512 MB RAM, Geforce 4 MX440 and 40GB HDD has no place now! I want to use it without a monitor through VNC to access it through the other 2 PCs and 1 laptop in the house.

It's running Ubuntu 7.10 now, but I have a problem with Ubuntu, whenever I start the PC without connecting a monitor (and powering it up), Ubuntu will start in 640x480 (my monitor can do 1024x768) but if it's connected, no problem. This doesn't happen in any other distro I have used.

So now I am looking for a good lightweight distro that won't be technically demanding from me (I am busy). XFCE will do. But I want it to start a VNC server on startup and create a Samba server also on startup. I want it to have an easy firewall to configure because this PC will be on 24/7. I will be using this PC mainly for downloading stuff or storing unneeded things.

---

### Post by mips on 2008-02-06
> **Amorphous_Snake said:**
> 
So now I am looking for a good lightweight distro that won't be technically demanding from me (I am busy). XFCE will do. But I want it to start a VNC server on startup and create a Samba server also on startup. I want it to have an easy firewall to configure because this PC will be on 24/7. I will be using this PC mainly for downloading stuff or storing unneeded things.


Try Arch linux, should be very light as you are only going to install what you need. Pacman is a breeze to use.
Why not use FreeNX instead of VNC?
To make IP tables configuration easier use a application called Firewall Builder

---

### Post by dca on 2008-02-06
Install the ubuntu server edition along w/ samba package & vnc & x & whatever?  If it's going to sit there.  My 6.06 box that I back-up my music catalogs from mine and my wife's workstation is sitting next to the outside refirgerator w/ no keyboard or monitor.  The only problem with it is the bios won't allow starting the box w/o a keyboard connected so after verifying it's at a login prompt I remove them all...  Oh, instead of VNC'ing into it, I either shell into it or use gFTP (when I'm lazy) for bulk moves....

---

### Post by lespaul_rentals on 2008-02-06
I'd use either Arch or Ubuntu Server 6.06.  Both are great server distros and will serve you well.  Do not run a desktop enviroment on it unless you are going to start a VNC session, as that will slow it down greatly.

---

### Post by Amorphous_Snake on 2008-03-02
I guess Arch is too difficult for me.

As for the Ubuntu 6.06 server install, how difficult is that?

I don't have the time to try! So please help me.

One more question: will using Zenwalk, Wolvix, Vector or other Slackware-based distros be easier?

---

### Post by K.Mandla on 2008-03-04
Command-line Ubuntu isn't too far from a basic Arch setup; the Ubuntu version will more or less set itself up, while Arch will require you to configure more things.

If you're used to Ubuntu, a command-line system might be a good starting system for you. Linux is Linux, but other distros might behave a little differently, or omit things you're accustomed to. You'll have to experiment and see.

---

