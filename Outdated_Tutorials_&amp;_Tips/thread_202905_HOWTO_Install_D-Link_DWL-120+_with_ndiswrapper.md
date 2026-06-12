---
title: "HOWTO: Install D-Link DWL-120+ with ndiswrapper"
date: 2006-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by henrikfromnorway on 2006-06-24
Yes, I know this sounds stupid. I was going to install the MA111, but I couldn't find it. So, just for trying, I tried with the D-Link DWL-120+.


First, you need the Netgear MA111 v1 (!!!) drivers.

Download them at netgear.com. in the 2.5Beta-zip, it's a couple of files.

you need the four NETMA111.INF-files, and the MA111nd5.sys-files.

i used winzip to zip them over to an USB-jumpdrive, and i got them in folders called /Drivers/Win98, /Drivers/WinNT, /Drivers/Win2000, /Drivers/WinXP.

Unpack them to your home folder. Let them stay in /Drivers/WinVERSION, but rename the root-folder of the files to something easy.

Then install ndiswrapper. 
```
sudo apt-get install ndiswrapper-utils
```

When that's done, type ```
sudo -s
```

```
ndiswrapper -i /folder/with/netgear/ma111/Drivers/Win98/NETMA111.INF
```
Install the Windows98-drivers. You can also try with the XP, but it worked for me with 98. (I didn't try the others)

```
ndiswrapper -l
```
Then you should see somthing like this:
```
root@westbeach:~# ndiswrapper -l
installed ndis drivers
NETMA111.INF                driver present, hardware present

```
(i don't have the box accessible right now, so i'm not 110% sure)

If not, remove the NETMA111-driver, and try again with another Windows-version.
```
ndiswrapper -e NETMA111.INF
```

Then
```
sudo ifdown wlan0
sudo ifup wlan0
```

Reboot, and configure it the way you want to!
I like to use Gnome Network Tools.

ENJOY!

---

### Post by hilander on 2007-05-11
how do I remove the drive it it does not work??
It is probably stupid,,but is the fist time I am using linux...hope you guys understand

---

### Post by boxall on 2007-05-25
Henriks instructions are for Ubuntu 6.06.  Has anyone managed to use a D-Link DWL-120+ with Ubuntu 7.04 yet???

I only installed Ubuntu this week as my first go with Linux so please keep the instructions simple :-)

Thanks

---

### Post by Ouoertheo on 2007-09-10
No luck with this method in 7.07

---

