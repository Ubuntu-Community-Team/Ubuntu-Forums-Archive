---
title: "Live CD video problems NVidia GeForce2"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by tkman26 on 2008-07-17
Hello all.
I am new to Ubuntu however I am not new to Linux.
I have installed Mandrake, and installed and used Suse, and Centos.
Mandrake had some hardware issues and I never really used it.
I did not have any problems with Suse or Centos on other older systems.  Thus I had assumed Linux distributions had matured and recognized the value of including lots of drivers. 

Most of my experience has been with Microsoft.

I offer IT support to some businesses and am wanting to see if they would consider replacing their windows boxes with a Linux flavor.  I am experimenting with Ubuntu hoping it will be even better than Suse or Centos.

The buzz around Ubuntu and it's ease of use had my expectations high.
I have not used the live versions before but I expected them to look and feel like a regular Linux distro.


Unfortunately my expectations were too high.
The first time I tried to run I ended up with a black screen.
After surfing and experimenting I managed to get to a very distorted screen where I can tell there is something there but can't quite read it.
There appear to be many other people encountering hardware incompatibility issues as well.

I can see various posts related to loading new or other drivers.
If someone could point me to a workaround that will help me load drivers that are compatible with a NVidia GeForce2 MX video card I would greatly appreciate it.
Specifically where will I find a compatible driver?
I assume I would load this driver on a CD so when I am prompted to "insert a driver CD" I would be able to have the required driver on the CD.

The system I am experimenting with is is a Dell Dimension 4100 with 512 M ram, P3 933 cpu, Maxtor 120 G hard drive. 

Thanks in advance.

---

### Post by tuxxy on 2008-07-17
You need to fuly install Ubuntu, then enable the driver from the restricted hardware driver tool in the administration menu to enable desktop effects.

As you can see here [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia) your card is supported.  Please try a full install instead of live mode.

---

### Post by RomeReactor on 2008-07-17
Hi. After installation, you can find the driver in the repositories using Synaptic (System->Administration->Synaptic), or as tuxxy points out, in 'System->Administration->Hardware Drivers' (this option is actually the easier one).

However, seeing as this is a Live CD session, try this: After you log in (if you can log in), press CTRL+ALT+F1 to switch to a console, then stop the display:
```
sudo /etc/init.d/gdm stop
```
Then try to reconfigure the display:
```
sudo dpkg-reconfigure xserver-xorg
```
The display should start automatically after that. Note that the new version of X server does more autoconfiguration at boot time, so this procedure may not fix the problem.

This situation happens in some cases using the Live CD; once the system is installed, the problem should probably be fixed, or if it's not, it would be easier to fix. If you are unable to install using the Live CD, I believe there's an option in the initial menu to skip straight to installing instead of going to the desktop.

There's also an Alternate CD which performs a text-based installation, and is unlikely to exhibit this problem.

* Ubuntu 8.04, 32 bit ([BitTorrent]("http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso.torrent"), [direct download]("http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso"))

* Ubuntu 8.04, 64 bit ([BitTorrent]("http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-amd64.iso.torrent"), [direct download]("http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-amd64.iso"))

---

### Post by tkman26 on 2008-07-17
Solved.
Thanks for all the help.
The solution was actually much simpler.
I was using an old monitor.
When I switched to a Dell monitor that came with the system Ubuntu Live came up crisp and clear.

It was not a video card issue or a video driver issue.

Thanks again for your help.

---

