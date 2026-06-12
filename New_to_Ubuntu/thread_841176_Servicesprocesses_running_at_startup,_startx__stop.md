---
title: "Services/processes running at startup, startx / stopx"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by batfastad on 2008-06-26
Hi everyone
I'm using Ubuntu server 8.04 as a test server at the moment to get my head round things.
I installed gnome-core to make things a bit easier (to run firefox so I can ask questions!)

I've been messing around with various Samba configurations. And shortly I will move on to Netatalk to share files to Macs using AFP. Then I will be able to roll out these configurations to a new RAID NAS I'll build at work (15 users)

My questions:

1) What file/files in Ubuntu server control which processes/services get loaded on startup?
Samba seems to be running, but I think I'll have to add Netatalk manually.

2) At which point are services like Samba started? Before login?
Or are they started once I've logged in to the terminal screen and started x?

3) Even though I have basic gnome-core installed, it still dumps me to the command prompt at startup... this is how I want it.
I then type startx to load Gnome, then quit in Gnome to take me back to the command prompt.
I guess Gnome loads up quite a few processes when it starts... but do they all stop again once I quit Gnome?

99% of the time my server will just be hovering at the terminal login screen, but sometimes I have to startx to check something out. I want to make sure that there's nothing extra and not required that lingers in memory after I've quit Gnome and logged out

Thanks, B

---

### Post by HalPomeranz on 2008-06-26
> 1) What file/files in Ubuntu server control which processes/services get loaded on startup?
Samba seems to be running, but I think I'll have to add Netatalk manually.

This is way more detail than you asked for, but let me be complete about this:

1) The first process started once the kernel is running is a process called init, which is responsible for starting everything else on the machine.  init uses the scripts in /etc/event.d to figure out what happens through the rest of the boot process.

2) Specifically, the /etc/event.d/rc-default script helps init figure out what default "run level" your system is going to boot to.  The default run level on Ubuntu is run level 2.

3) init then starts running the scripts out of /etc/rc?.d, where ? is the run level your system is booting towards-- so in a default Ubuntu install init will run the scripts out of /etc/rc2.d.

4) Each script in the /etc/rc?.d directory is generally responsible for starting/stopping a particular service (or closely related group of services).  You'll notice that the scripts in the rc?.d directory have a funny naming convention-- either S??scriptname or K??scriptname.  The 'S' means to run the script to "start" a particular service, and the K means to stop ("kill") the service.  The numbers after the S or K are used so that the scripts run in the correct dependency order.

Most people just use the GUI interface for managing services (System -> Administration -> Services).  There's also a command-line program for managing boot services called update-rc.d.

But at the lowest level these programs are simply managing the scripts in the /etc/rc?.d directories.  Actually the things in the /etc/rc?.d directories are really just links (pointers) to the real scripts that live in the /etc/init.d directory.  So if you wanted to add a completely new service, you'd put a script to start the service into /etc/init.d and make the appropriate links in the /etc/rc?.d directories.

> 2) At which point are services like Samba started? Before login?
Or are they started once I've logged in to the terminal screen and started x?

```

$ ls /etc/rc2.d
K08vmware		     S19mysql	       S25pulseaudio
README			     S20apport	       S30gdm
S01policykit		     S20cupsys	       S50ntp
S05vbesave		     S20hotkey-setup   S89anacron
S10acpid		     S20makedev        S89atd
S10powernowd.early	     S20nvidia-kernel  S89cron
S10sysklogd		     S20powernowd      S90binfmt-support
S10xserver-xorg-input-wacom  S20rsync	       S90vmware
S11klogd		     S20samba	       S91apache2
S12dbus			     S20smartmontools  S98usplash
S15bind9		     S20xinetd	       S99acpi-support
S16ssh			     S21sendmail       S99laptop-mode
S17mysql-ndb-mgm	     S24dhcdbd	       S99rc.local
S18avahi-daemon		     S24hal	       S99rmnologin
S18mysql-ndb		     S25bluetooth      S99stop-readahead

```

See the "S20samba" link in the middle of the output?  That's where Samba gets started.

> 3) Even though I have basic gnome-core installed, it still dumps me to the command prompt at startup... this is how I want it.
I then type startx to load Gnome, then quit in Gnome to take me back to the command prompt.
I guess Gnome loads up quite a few processes when it starts... but do they all stop again once I quit Gnome?


Yes, everything that gets fired up when you run startx should shut down again when you exit Gnome.  Note that the processes that run when you startx have nothing to do with the processes started at boot time that we were discussing above.

---

