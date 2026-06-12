---
title: "Nmap 4.00 for Ubuntu 5.10 (Breezy)"
date: 2006-02-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2006-02-01
I have made an updated package for the new version of NMAP.

1. Get files
```
wget -c http://mikesplanet.net/deb/nmap_4.00-1~dmb_i386.deb
wget -c http://mikesplanet.net/deb/nmapfe_4.00-1~dmb_i386.deb
wget -c http://mikesplanet.net/deb/nmap-logo-64.png

```

2. Install Extra Libraries
```
sudo apt-get install libpcre3
```

3. Install Files
```
sudo dpkg -i nmap_4.00-1~dmb_i386.deb nmapfe_4.00-1~dmb_i386.deb
```

4. Copy Icon Pixmap
```
sudo cp nmap-logo-64.png /usr/share/pixmaps
```

5. Restart Gnome Panel
```
killall gnome-panel
```

The source can be found here:
```
wget -c http://mikesplanet.net/deb/nmap-4.00~dmb.tar.gz
```

---

### Post by RaptorRaider on 2006-02-01
It's always nice to give a bit more information about what the effect of a certain customization is.
Screenshots are always appreciated.

> Nmap ("Network Mapper") is a free open source utility for network exploration or security auditing. It was designed to rapidly scan large networks, although it works fine against single hosts. Nmap uses raw IP packets in novel ways to determine what hosts are available on the network, what services (application name and version) those hosts are offering, what operating systems (and OS versions) they are running, what type of packet filters/firewalls are in use, and dozens of other characteristics. Nmap runs on most types of computers and both console and graphical versions are available.

[Here]("http://images.insecure.org/nmap/images/nmap-349-demovscan.gif")'s a screenshot, though I'm sure you can come up with better ones.


Looks interesting for network admins. Will play a bit with it in the future.

---

### Post by i3dmaster on 2006-02-01
That's cool! Thanks for sharing.

---

### Post by Technoviking on 2006-02-01
[QUOTE=RaptorRaider]It's always nice to give a bit more information about what the effect of a certain customization is.
[/QUOTE]
It should not effect your Ubuntu install, since the Ubuntu Base System does not depend on NMAP.

The source is direct from insecure.org and not Dapper, so YMMV.

I included a link to my source files, so you can see the changes I made yourself.

Mike

---

### Post by straylight on 2006-02-01
I didnt really see a good spot to post this question so when a search turned up an active topic on nmap 4.0 i figured i would just ask my question here.

I'm trying to install from source and i seem to be having some issues, when i run a ./configure i get the following error:

[B]configure: error: C compiler cannot create executables
See `config.log' for more details.[/B]

When i check config.log i see the following:

[B]/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1714: $? = 1
configure: failed program was:
| /* confdefs.h.  */[/B]


so it seems like it is bombing out on confdefs.h, anyone know how to fix that?

I guess I should also mention that before i was getting the "cannot create executables" error i was getting this:

**configure: error: no acceptable C compiler found in $PATH**

So i fired up synaptic and marked gcc for install. 

Any help would be appreciated....

Thanks,
straylight

MODS: feel free to move this post if need.

---

### Post by straylight on 2006-02-01
nvm, got it working.....needed to "apt-get install build-essential", that fixed the problem!

-straylight

---

### Post by majikstreet on 2006-02-01
I think you should also make a guide (or someone should) on how to have fun exploring your network with nmap... It's always been interesting, and I'd like to have a look around my network (2 windows machines, 2 linux machines, and a tivo).. should be neat :)

EDIT: I just opened nmapfe and looked on my network.. neat..

---

### Post by straylight on 2006-02-01
majikstreet:

check out the man page for nmap, as it has been completely rewritten for version 4.0.  It contains tons of awesome info!  IMHO, its the best documentation available on the program, at least until fyodor's nmap book gets published.

BTW:

How were you guys able to get nmapfe working?  I almost never use the GUI but since it too has been revamped i figured i would check it out.  But when i compiled nmap it told me that nmapfe wouldnt be installed because gtk is missing.  I tried "apt-get install gtk" but no package was found.  Any ideas?

Thanks,
straylight

---

