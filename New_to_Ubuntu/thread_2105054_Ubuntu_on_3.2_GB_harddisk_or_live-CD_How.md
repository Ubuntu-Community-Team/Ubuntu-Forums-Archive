---
title: "Ubuntu on 3.2 GB harddisk or live-CD? How?"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by Franz47 on 2013-01-15
The 40GB ATA harddisk of an old laptop with 500 MB memory of my friends has crashed. I found an old 3.2 GB ATA harddisk in my junk collection and installed it and thought I might make the machine somehow usable by installing a Linux version. Graphical desktop should start automatically, WWW-Browser and text editor which can produce files readable in Windows Office should be working, saving to USB-stick should be possible for file transfer. 

At first I thought I might just burn a DVD with the lates Ubuntu distribution and use it live. There appeared a desktop but the DVD never stopped spinning and I never could use any of the programs on the desktop although the mouse pointer moved. 

Then I tried "damn small linux" 4.4.10 which started but I could not find a suitable text editor on the desktop. DSL can be installed to the harddisk but I could not find out, how.

Then I found the mini ubuntu, which would download the program packages one wanted. I could make an installation to the harddisk, but had no idea which software packages I should add to the installation. The Ubuntu on the small harddisk started, but only with the CLI.

What should I do to make this machine work as described above? Live CD - how? Miniinstallation to HDD - how?

Thanks for any advice

---

### Post by drawkcab on 2013-01-15
Provided that the laptop has a slot for an sd card, one idea would be to simply install the OS to a 16gb-16gb sd card and boot from that every time.  Not elegant but it's cheap and it works.  From the live cd just install to the card and then set the laptop to boot from the card from the bios.

If you're going to stick with the hdd, you're going to have to go with something light and small.  Lubuntu and Bodhi would just work with those resource I believe.  If you wanted to try something other than ubuntu I'd recommend cruchbang (a great little Debian-based distro with Openbox) or even archbang (arch + openbox).  

Damn Small Linux has not been in active development.  If you wanted to go with something really small to maximize hdd space, then precise puppy (ubuntu-based) or antix (mepis + icewm) might be good choices.

Have a spin around here for some more ideas:

[http://distrowatch.com/](http://distrowatch.com/)

They provide a search at the top.

---

### Post by mörgæs on 2013-01-15
If space is a constraint then [http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689) is worth trying. Remember to run

```
sudo apt-get clean
sudo apt-get autoclean
```

once in a while to free as much space as possible.


Damn Small Linux has been dormant for a long time, but it appears to be resurrecting. 
[http://damnsmalllinux.org/forums/index.php?PHPSESSID=d43e36ffb33e2ee4df14aa30920cb597&topic=2.0](http://damnsmalllinux.org/forums/index.php?PHPSESSID=d43e36ffb33e2ee4df14aa30920cb597&topic=2.0)

---

