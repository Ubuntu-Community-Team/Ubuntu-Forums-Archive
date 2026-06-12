---
title: "9 June daily build no gdm black screen"
date: 2011-06-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2011-06-09
09 June daily build Live - no "gnome", no "gdm", no "desktop".

It will boot in rescue mode but
sudo service gdm start
reveals no "gdm".

sudo startx
doesn't.  Message says "no gnome".

"repair broken packages" ran but no help.

Acer Aspire one netbook runs Unity 3D fine, runs 08 June daily build.

Where did "gnome" go?

Any ideas?

Jerry

---

### Post by kansasnoob on 2011-06-09
Ubuntu is now using lightdm so try:

```
sudo /etc/init.d/lightdm restart
```

Or:

```
sudo service lightdm start
```

Some of the installed files are different:

> /.
/etc
/etc/dbus-1
/etc/dbus-1/system.d
/etc/dbus-1/system.d/org.lightdm.LightDisplayManager.conf
/etc/init
/etc/init.d
/etc/init.d/lightdm
/etc/init/lightdm.conf
/etc/lightdm.conf
/etc/pam.d
/etc/pam.d/lightdm
/usr
/usr/bin
/usr/bin/lightdm
/usr/share
/usr/share/doc
/usr/share/doc/lightdm
/usr/share/doc/lightdm/changelog.Debian.gz
/usr/share/doc/lightdm/copyright
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/lightdm.1.gz
/var
/var/cache
/var/cache/lightdm
/var/log
/var/log/lightdm


---

### Post by jerrylamos on 2011-06-09
Thanks.  I had been booting "persistent" which fouled up with 9 June so I rebooted without "persistent" and I can get it up to a degree.

I had to do sudo service lightdm start

then login using lightdm with Unity 2D

at which point Unity 2D came up, using lightdm.

Shortly thereafter lightdm crashed but still stayed up, did I want to report the problem?  Sure, but

Wireless is busted.  Can't get it up nohow.  The applet shows the network but won't connect.  The applications for network and network tools won't work for wireless. sudo dhclient doesn't get network up, and ifconfig doesn't show any active network.

Had to boot Narwhal (wireless of course) to make this entry.

Let me try 9 June daily build on another pc which uses wired network to see how lightdm works/crashes ...

Thanks, Jerry

---

### Post by ronacc on 2011-06-09
Your wireless problem may not be lightdm , see this thread ```
http://ubuntuforums.org/showthread.php?t=1778061
``` check your glib version

---

### Post by jerrylamos on 2011-06-09
> **ronacc said:**
> Your wireless problem may not be lightdm , see this thread ```
http://ubuntuforums.org/showthread.php?t=1778061
``` check your glib version

Thanks, I'll check that thread after lunch.  Gotta go do my daily exercise.

The glib version is whatever shipped on daily build today 9 June.

The lightdm crash also happened on IBM Thinkpad T40, bug #795047, and on IBM ThinkCentre A30.  That's three different video cards so video not likely the difficulty.

The latter two use wired network so they could report the crash.

Thanks, Jerry

---

### Post by jerrylamos on 2011-06-09
With 9 June default lightdm plugged in a wired connection ran fine.  Tried to activate wireless with "Network" and it wouldn't connect so I did ubuntu-bug lightdm and created bug report #795205.

Rebooted with 8 June default gdm, activated wireless with "Network" just fine.

I don't know enough about glib versions to know which one/ones are loaded?

Jerry

---

### Post by bmbaker on 2011-06-10
the new glib update solved this :-)

---

### Post by fjgaude on 2011-06-10
Hi, Jerry and all! Well, using grub boot .iso (not persistent) the 9 and 10 June build didn't work on my system.

I thought it might be my wireless kyb and mouse, but no. I get to the log-in screen and there is then no mouse or keyboard. So I have to reset to get out of it.

Will wait until the next build comes out and see...

---

### Post by 23dornot23d on 2011-06-10
> 
I don't know enough about glib versions to know which one/ones are loaded?

Jerry

Just open up Synaptic package manager and search for glib ..... look down the list

It shows what is installed and also if the next version is available it will show that alongside it .......
in this format

Package ..... Installled Version ..... Latest Version

---

### Post by jerrylamos on 2011-06-11
> **23dornot23d said:**
> Just open up Synaptic package manager and search for glib ..... look down the list

It shows what is installed and also if the next version is available it will show that alongside it .......
in this format

Package ..... Installled Version ..... Latest Version

Since wireless isn't working, synaptic can't load an update to glib.  Anyone know how to activate wireless from the command line?  dhclient only gets wired up.

On daily build 10 June I did plug in a wired connection, and in rescue mmode did:

sudo dhclient
sudo apt-get update lightdm
unplugged the wire
sudo service lightdm start

Then the application Network got wireless up.  The nm applet disappeared.

11 June no daily build update.

Jerry

---

