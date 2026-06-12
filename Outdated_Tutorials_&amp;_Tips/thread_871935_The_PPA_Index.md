---
title: "The PPA Index"
date: 2008-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by picpak on 2008-07-27
[size=5]**Updates**[/size]

[size=3]03/10/09:[/size] Added PPAs and extra sections.
[size=3]01/29/09:[/size] Changed the address to every PPA.
[size=3]11/10/08:[/size] Updated to Intrepid 8.10.
[size=3]09/27/08:[/size] Added Alexander Sack's PPAs.
[size=3]08/29/08:[/size] Added PPAs for Ubuntulite, WebKit, SMPlayer, Pidgin, mupen64plus, infobash, gnome-hdaps-applet, ipager, and netconfig.
[size=3]08/21/08:[/size] Added PPAs for Galaxium, gwibber and Hamster.
[size=3]08/19/08:[/size] Added loell's and my PPA.
[size=3]08/13/08:[/size] Added PPAs for gnome-wallpaper and epiphany-webkit.
[size=3]07/31/08:[/size] Added PPAs for Mozilla Team, Amarok 2, PlayOnLinux, aMule, Audacious, Ubuntu 8.10 theme, Claws-Mail and Terminator.
[size=3]07/29/08:[/size] Added PPAs for Cairo Composite Manager, Deluge, Flash 10, Midori, Compiz Fusion, Cairo Dock, Gnome Do, Banshee, Google Gadgets, chmsee, and Screenlets

[size=6]**Introduction**[/size]

As inspired by [this post](http://ubuntuforums.org/showpost.php?p=5463235&postcount=14) here, I have begun work on an index of the most useful PPAs out there. If you know of any, please let me know!

P.S: If you can't find the software you want through this index, I suggest using Launchpad's own [PPA Search](https://launchpad.net/ubuntu/+ppas). It is constantly updated and includes every PPA. Enjoy!

[size=5]What are PPAs?[/size]

As described by [https://help.launchpad.net/PPAQuickStart:](https://help.launchpad.net/PPAQuickStart:)

> With Launchpad's Personal Package Archives (PPA), you can build and publish binary Ubuntu packages for multiple architectures simply by uploading an Ubuntu source package to Launchpad.

In short, PPAs (short for Personal Package Archives) make it easier for developers and package maintainers to upload and share packages of their programs. They can provide software not found in Ubuntu's repositories, or they can provide updated packages of outdated software. PPAs, along with [Launchpad](https://launchpad.net/ppa/ubuntu/+ppas), make it easier to provide safe and reliable package repositories for everyday use.

[size=5]How do I use PPAs?[/size]

There are two ways of going about this:

[size=3]**Method 1**[/size]

[LIST=5]
[*]In Ubuntu, go to **System** > **Administration** > **Software Sources**.
[*]Click on the **Third Party Software** tab, and click **Add...**.
[*]Under **APT line**, copy and paste in the APT line as provided by the PPA. The APT line should look something similar to this:

```
deb http://archive.ubuntu.com/ppa/ubuntu/ hardy main
```

Once it is copied and pasted in, click **Add Source**.
[*]Click **Close**. A pop-up will ask you to reload the package information. Click **Reload**.
[*]Now, you can go to **System** > **Administration** > **Synaptic Package Manager**, and search for and install your software through there.
[/LIST]

[size=3]**Method 2**[/size]

[LIST=4]
[*]Open up a terminal through **Applications** > **Accessories** > **Terminal**, and enter in the following:
```
gksudo gedit /etc/apt/sources.list
```
[*]At the bottom of the file, on a new line, copy and paste in the APT line as provided by the PPA. The APT line should look something similar to this:

```
deb http://archive.ubuntu.com/ppa/ubuntu/ hardy main
```

Once it is copied and pasted in, save the file and exit.
[*]Reload the package information by entering in the following:
```
sudo apt-get update
```
[*]Install your software either through **System** > **Administration** > **Synaptic Package Manager**, or via this command:
```
sudo apt-get install name-of-program
```
[/LIST]

Now you're good to go!

[size=6]**The List**[/size]

[size=5]**Categories:**[/size]

[size=3][LIST=2]
[*]PPAs of official projects
[*]Personal PPAs
[*]PPAs for Hardy (8.04)
[/LIST][/size]

[size=6]**1. PPAs of official projects**[/size]

[size=3]**Ubuntu Tweak**[/size]
**Website:** [https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)
**Description:** A PPA for Ubuntu Tweak, a program designed to tweak the hidden configuration settings of GNOME.
**APT line:**
```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu intrepid main
```

[size=3]**Avant Window Navigator**[/size]
**Website:** [https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)
**Description:** A testing PPA for the popular dock Avant Window Navigator.
**APT line:**
```
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu intrepid main
```

[size=3]**Shutter**[/size]
**Website:** [https://launchpad.net/~shutter/+archive/ppa](https://launchpad.net/~shutter/+archive/ppa)
**Description:** A PPA for Shutter, an advanced screenshot taking program for GNOME.
**APT line:**
```
deb http://ppa.launchpad.net/shutter/ppa/ubuntu intrepid main
```

[size=3]**Exaile**[/size]
**Website:** [https://launchpad.net/~exaile-devel/+archive/ppa](https://launchpad.net/~exaile-devel/+archive/ppa)
**Description:** A PPA for Exaile, a full-featured music player for GNOME.
**APT line:**
```
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu intrepid main
```

[size=3]**GNOME Do**[/size]
**Website:** [https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)
**Description:** A PPA for GNOME Do, an application that lets you do things as quickly as possible.
**APT line:**
```
deb http://ppa.launchpad.net/do-core/ppa/ubuntu intrepid main
```

[size=3]**Banshee**[/size]
**Website:** [https://launchpad.net/~banshee-team/+archive/ppa](https://launchpad.net/~banshee-team/+archive/ppa)
**Description:** A PPA for the latest version of Banshee, a GNOME audio management and playback application.
**APT line:**
```
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu intrepid main
```

[size=3]**Deluge**[/size]
**Website:** [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)
**Description:** A PPA for the latest stable version of Deluge, a GNOME BitTorrent client.
**APT line:**
```
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu intrepid main
```

[size=3]**WebKit**[/size]
**Website:** [https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)
**Description:** A PPA for Webkit-related programs, such as Webkit and Midori.
**APT line:**
```
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu intrepid main
```

[size=3]**Mozilla Team**[/size]
**Website:** [https://launchpad.net/~mozillateam/+archive/ppa](https://launchpad.net/~mozillateam/+archive/ppa)
**Description:** A PPA for bleeding-edge packages of Firefox and other Mozilla programs.
**APT line:**
```
deb http://ppa.launchpad.net/mozillateam/ppa/ubuntu intrepid main
```

[size=3]**gwibber**[/size]
**Website:** [https://launchpad.net/~gwibber-team/+archive/ppa](https://launchpad.net/~gwibber-team/+archive/ppa)
**Description:** A PPA for gwibber, a micro-blogging client that supports Twitter, Jaiku, Identi.ca, Facebook, and Digg.
**APT line:**
```
deb http://ppa.launchpad.net/gwibber-team/ppa/ubuntu intrepid main
```

[size=3]**Amarok Project Neon**[/size]
**Website:** [https://launchpad.net/~project-neon/+archive/ppa](https://launchpad.net/~project-neon/+archive/ppa)
**Description:** A PPA for the nightly builds of the upcoming Amarok 2.
**APT line:**
```
deb http://ppa.launchpad.net/project-neon/ppa/ubuntu intrepid main
```

[size=3]**Terminator**[/size]
**Website:** [https://launchpad.net/~gnome-terminator/+archive/ppa](https://launchpad.net/~gnome-terminator/+archive/ppa)
**Description:** A PPA for Terminator, a program that lets you run multiple GNOME terminals in one window.
**APT line:**
```
deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu intrepid main
```

[size=3]**Claws-Mail**[/size]
**Website:** [https://launchpad.net/~claws-mail/+archive/ppa](https://launchpad.net/~claws-mail/+archive/ppa)
**Description:** A PPA for Claws Mail, a lightweight GTK mail client.
**APT line:**
```
deb http://ppa.launchpad.net/claws-mail/ppa/ubuntu intrepid main
```

[size=3]**gnome-wallpaper**[/size]
**Website:** [https://launchpad.net/~doctormo/+archive/ppa](https://launchpad.net/~doctormo/+archive/ppa)
**Description:** A PPA for gnome-wallpaper, an auto-changing wallpaper program for GNOME.
**APT line:**
```
deb http://ppa.launchpad.net/doctormo/ppa/ubuntu intrepid main
```

[size=3]**OpenOffice 3**[/size]
**Website:** [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
**Description:** A PPA to install the latest version of OpenOffice.
**APT line:**
```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
```

[size=3]**Globalmenu**[/size]
**Website:** [https://launchpad.net/~globalmenu-team/+archive/ppa](https://launchpad.net/~globalmenu-team/+archive/ppa)
**Description:** A PPA for gnome-globalmenu, a Mac-like menu bar for your panel.
**APT line:**
```
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu intrepid main
```

[size=6]**2. Personal PPAs**[/size]

[size=3]**Fabien Tassin's PPA**[/size]
**Website:** [https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)
**Description:** Includes Mozilla projects such as Firefox, Seamonkey and Thunderbird.
**APT line:**
```
deb http://ppa.launchpad.net/fta/ppa/ubuntu intrepid main
```

[size=3]**My PPA**[/size]
**Website:** [https://launchpad.net/~k-belding/+archive/ppa](https://launchpad.net/~k-belding/+archive/ppa)
**Description:** Includes the latest release of Openbox, as well as sakura and Nitrogen.
**APT line:**
```
deb http://ppa.launchpad.net/k-belding/ppa/ubuntu intrepid main
```

[size=3]**Bruce Cowans' PPA**[/size]
**Website:** [https://launchpad.net/~bruce89/+archive/ppa](https://launchpad.net/~bruce89/+archive/ppa)
**Description:** Includes packages for programs such as Audacity, Empathy and Telepathy.
**APT line:**
```
deb http://ppa.launchpad.net/bruce89/ppa/ubuntu intepid main
```

[size=3]**Reacocard's PPA**[/size]
**Website:** [https://launchpad.net/~reacocard-awn/+archive/ppa](https://launchpad.net/~reacocard-awn/+archive/ppa)
**Description:** Similar to Avant Window Navigator's PPA; includes personal packages of AWN.
**APT line:**
```
deb http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu intrepid main
```

[size=3]**Stéphane Marguet's PPA**[/size]
**Website:** [https://launchpad.net/~stemp/+archive/ppa](https://launchpad.net/~stemp/+archive/ppa)
**Description:** A PPA for Midori, a Webkit-based lightweight web browser.
**APT line:**
```
deb http://ppa.launchpad.net/stemp/ppa/ubuntu intrepid main
```

[size=3]**Michael Vogt's PPA**[/size]
**Website:** [https://launchpad.net/~mvo/+archive/ppa](https://launchpad.net/~mvo/+archive/ppa)
**Description:** A PPA for the development version of Compiz Fusion.
**APT line:**
```
deb http://ppa.launchpad.net/mvo/ppa/ubuntu intrepid main
```

[size=3]**Julien Lavergne's PPA**[/size]
**Website:** [https://launchpad.net/~gilir/+archive/ppa](https://launchpad.net/~gilir/+archive/ppa)
**Description:** A PPA for Screenlets and Cairo Dock.
**APT line:**
```
deb http://ppa.launchpad.net/gilir/ppa/ubuntu intrepid main
```

[size=3]**LI Daobing's PPA**[/size]
**Website:** [https://launchpad.net/~lidaobing/+archive/ppa](https://launchpad.net/~lidaobing/+archive/ppa)
**Description:** A PPA for chmsee, a CHM file viewer for GNOME.
**APT line:**
```
deb http://ppa.launchpad.net/lidaobing/ppa/ubuntu intrepid main
```

[size=3]**Kenneth Wimer's PPA**[/size]
**Website:** [https://launchpad.net/~kwwii/+archive/ppa](https://launchpad.net/~kwwii/+archive/ppa)
**Description:** A PPA for the Ubuntu 8.10 theme.
**APT line:**
```
deb http://ppa.launchpad.net/kwwii/ppa/ubuntu intrepid main
```

[size=3]**Alexander Sack's PPA**[/size]
**Website:** [https://launchpad.net/~asac/+archive/ppa](https://launchpad.net/~asac/+archive/ppa)
**Description:** A PPA for beta versions of Mozilla software, as well as miscellaneous networking programs.
**APT line:**
```
deb http://ppa.launchpad.net/asac/ppa/ubuntu intrepid main
```

[size=3]**network-manager**[/size]
**Website:** [https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa)
**Description:** Alex also has one for network-manager 0.7.
**APT line:**
```
deb http://ppa.launchpad.net/network-manager/ppa/ubuntu intrepid main
```

[size=3]**festor90's PPA**[/size]
**Website:** [http://ppa.launchpad.net/festor90/ppa/ubuntu](http://ppa.launchpad.net/festor90/ppa/ubuntu)
**Description:** A PPA for the latest release of aMule, a GTK P2P client.
**APT line:**
```
deb http://ppa.launchpad.net/festor90/ppa/ubuntu intrepid main
```

[size=3]**Michele Costantino Soccio's PPA**[/size]
**Website:** [https://launchpad.net/~michelinux/+archive/ppa](https://launchpad.net/~michelinux/+archive/ppa)
**Description:** A PPA for the Webkit version of the Epiphany web browser.
**APT line:**
```
deb http://ppa.launchpad.net/michelinux/ppa/ubuntu intrepid main
```

[size=3]**loell's PPA**[/size]
**Website:** [https://launchpad.net/~loell/+archive/ppa](https://launchpad.net/~loell/+archive/ppa)
**Description:** A PPA for the newest versions of Cheese, nted and consanance.
**APT line:**
```
deb http://ppa.launchpad.net/loell/ppa/ubuntu intrepid main
```

[size=3]**TheMono's PPA**[/size]
**Website:** [https://launchpad.net/~themono/+archive/ppa](https://launchpad.net/~themono/+archive/ppa)
**Description:** A PPA for the SVN releases of SMPlayer.
**APT line:**
```
deb http://ppa.launchpad.net/themono/ppa/ubuntu intrepid main
```

[size=6]**3. PPAs for Hardy (8.04)**[/size]

[size=3]**LXDE**[/size]
**Website:** [https://launchpad.net/~lxde/+archive/ppa](https://launchpad.net/~lxde/+archive/ppa)
**Description:** A PPA for the LXDE, a lightweight stable desktop environment.
**APT line:**
```
deb http://ppa.launchpad.net/lxde/ppa/ubuntu hardy main
```

[size=3]**Ubuntulite**[/size]
**Website:** [https://launchpad.net/~ubuntulite/+archive/ppa](https://launchpad.net/~ubuntulite/+archive/ppa)
**Description:** A PPA for Ubuntulite, a lightweight Ubuntu-based distribution that uses the LXDE desktop environment.
**APT line:**
```
deb http://ppa.launchpad.net/ppa/ubuntulite/ppa/ubuntu hardy main
```

[size=3]**Telepathy**[/size]
**Website:** [https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa)
**Description:** A PPA for Telepathy, Empathy and Farsight, a set of frameworks for instant messaging clients.
**APT line:**
```
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu hardy main
```

[size=3]**Galaxium**[/size]
**Website:** [https://launchpad.net/~galaxium/+archive/ppa](https://launchpad.net/~galaxium/+archive/ppa)
**Description:** A PPA for Galaxium, a multi-protocol instant messager for GNOME.
**APT line:**
```
deb http://ppa.launchpad.net/galaxium/ppa/ubuntu hardy main
```

[size=3]**Google Gadgets**[/size]
**Website:** [https://launchpad.net/~googlegadgets/+archive/ppa](https://launchpad.net/~googlegadgets/+archive/ppa)
**Description:** A PPA for the Google Gadgets, a platform for running Google Gadgets on Linux.
**APT line:**
```
deb http://ppa.launchpad.net/googlegadgets/ppa/ubuntu hardy main
```

[size=3]**KDE 4**[/size]
**Website:** [http://www.kubuntu.org/news/kde-4.1rc1](http://www.kubuntu.org/news/kde-4.1rc1)
**Description:** A PPA to get KDE4 installed on Kubuntu Hardy.
**APT line:**
```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ppa/ubuntu hardy main
```

[size=3]**Hamster**[/size]
**Website:** [https://launchpad.net/~hamster.support/+archive/ppa](https://launchpad.net/~hamster.support/+archive/ppa)
**Description:** A PPA for Hamster, an activity tracking app for GNOME.
**APT line:**
```
deb http://ppa.launchpad.net/hamster.support/ppa/ubuntu hardy main
```

[size=3]**Cairo Composite Manager**[/size]
**Website:** [https://launchpad.net/~gandalfn/+archive/ppa](https://launchpad.net/~gandalfn/+archive/ppa)
**Description:** A PPA for Cairo Composite Manager.
**APT line:**
```
deb http://ppa.launchpad.net/gandalfn/ppa/ubuntu hardy main
```

[size=3]**Pidgin**[/size]
**Website:** [https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)
**Description:** A PPA for the latest releases of Pidgin.
**APT line:**
```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu hardy main
```

[size=3]**Markus Thielmann's PPA**[/size]
**Website:** [https://launchpad.net/~thielmann/+archive/ppa](https://launchpad.net/~thielmann/+archive/ppa)
**Description:** A PPA for the Flash Player 10 beta plugin.
**APT line:**
```
deb http://ppa.launchpad.net/thielmann/ppa/ubuntu hardy main
```

[size=3]**Daniel Moerner's PPA**[/size]
**Website:** [https://launchpad.net/~dmoerner/+archive/ppa](https://launchpad.net/~dmoerner/+archive/ppa)
**Description:** A PPA for mupen64plus, infobash, gnome-hdaps-applet, ipager, and netconfig.
**APT line:**
```
deb http://ppa.launchpad.net/dmoerner/ppa/ubuntu hardy main
```

[size=6]**Troubleshooting**[/size]

[LIST=1]
[*]When I update my software sources, I get an error message saying "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available". How can I fix this?
[/LIST]

You're getting this message because your system can't find the public key of the PPA. A public way is a way of authenticating your PPA and ensuring that it is safe to use. The easiest way to fix this is by [this script](http://ubuntuforums.org/showthread.php?t=1056099), which will automatically find and install the public keys to your PPA. You can also do it manually, [as per this guide](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories).

[size=6]**Resources**[/size]

Ubuntu Tweak provides an easy way to enable many of the PPAs listed in this article and more. You can download it at [http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads) .

Use this link to search for PPAs:

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

You can also try this tool here:

[http://ppa-search.appspot.com/](http://ppa-search.appspot.com/)

This site is in Italian, but it provides you with a /etc/apt/sources.list full of many PPAs.

**PLEASE NOTE THAT THE PPAS IN THEIR SOURCES.LIST MAY CONFLICT BETWEEN EACH OTHER AND POTENTIALLY BREAK YOUR PACKAGES!**

[http://www.sourceslist.netsons.org/](http://www.sourceslist.netsons.org/)

If you know of any useful PPAs, please let me know. :) Thanks!

---

### Post by tamoneya on 2008-07-28
ive only got one PPA but it has the flash player 10 beta plugin.  i managed to get it to work with 64 bit:

```
deb http://ppa.launchpad.net/thielmann/ubuntu hardy main
```

---

### Post by picpak on 2008-07-28
Thanks, added :)

---

### Post by tamoneya on 2008-07-28
are you going to make some website or wiki or is the PPA index just going to be kept as a thread?
> tamoneya@tamoneyat61:~$ whois theppaindex.com

Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to [http://www.internic.net](http://www.internic.net)
for detailed information.

No match for "THEPPAINDEX.COM".


---

### Post by picpak on 2008-07-28
I was thinking of just keeping it in the thread, but a wiki would be an awesome idea.

---

### Post by tamoneya on 2008-07-28
from the looks of the ultimate edition website your skills are greater than mine when it comes to web design.  I get all the coding and such but lack the ability to make it look nice.

---

### Post by picpak on 2008-07-28
It's a wiki; its looks are universal. :)

---

### Post by picpak on 2008-07-29
Updated, there are now 18 PPAs :)

---

### Post by kostkon on 2008-07-29
Nice and useful thread!

Here is the PPA for *Deluge* that offers the latest stable version (thus you will not find the 1.0RC). Very useful repository in my opinion:
[https://launchpad.net/~deluge-team/+archive](https://launchpad.net/~deluge-team/+archive)
```
deb http://ppa.launchpad.net/deluge-team/ubuntu hardy main
```

---

### Post by picpak on 2008-07-29
You can find all the PPAs here:

[http://ppa.launchpad.net/](http://ppa.launchpad.net/)

But no way am I going through all that! :lolflag:

---

### Post by loell on 2008-08-19
howdy, just adding mine:)

```
deb http://ppa.launchpad.net/loell/ubuntu hardy main

```

so far i only have three, all for hardy

**cheese** (webcam application) - development version
**nted** (music notation) - updated version
**consonance** (lightweight music manager)

---

### Post by picpak on 2008-08-19
> **loell said:**
> howdy, just adding mine:)

```
deb http://ppa.launchpad.net/loell/ubuntu hardy main

```

so far i only have three, all for hardy

**cheese** (webcam application) - development version
**nted** (music notation) - updated version
**consonance** (lightweight music manager)

Thank you :) Added.

I've been thinking about starting my own PPA. Is it any hard?

---

### Post by loell on 2008-08-19
thanks for adding it in the first post :)

depending on the software package you would like to host, if its just a newer version of the software thats already in ubuntu or debian repo, then its fruitcake, you just have to copy the previous control file and change the changelog then more or less thats it. :)

for me the difficult part was about the pgp keys.

---

### Post by picpak on 2008-08-19
> **loell said:**
> thanks for adding it in the first post :)

depending on the software package you would like to host, if its just a newer version of the software thats already in ubuntu or debian repo, then its fruitcake, you just have to copy the previous control file and change the changelog then more or less thats it. :)

for me the difficult part was about the pgp keys.

I want to host software like sakura and Nitrogen. That'd be easy enough? I know setting up an Arch repo is super easy, I did it once :)

---

### Post by loell on 2008-08-19
i see and there are no previous debianized package of sakura and nitrogen? 
then you'll be creating from scratch, if you already created some deb packages with these software before,then much better.

---

### Post by picpak on 2008-08-19
> **loell said:**
> i see and there are no previous debianized package of sakura and nitrogen? 
then you'll be creating from scratch, if you already created some deb packages with these software before,then much better.

Can I just upload the debs? It'd be much easier. :)

---

### Post by loell on 2008-08-19
> **picpak said:**
> Can I just upload the debs? It'd be much easier. :)

heheh :D, at first I also thought it was just like that, but you are never permitted to just submit  binaries. you only got to submit the debianize sources, it scan for common errors then build it in three architectures, if it gets rejected, accepted, failure to build due to errors, or succesfull builds. you will be notified through your launchpad mail.

i was just following this

[https://help.launchpad.net/PPA?action=show&redirect=PPAQuickStart]("https://help.launchpad.net/PPA?action=show&redirect=PPAQuickStart")

---

### Post by picpak on 2008-08-19
The PGP thing was confusing, but I've got it :)

What now?

---

### Post by loell on 2008-08-19
have you setup dput already?

---

### Post by picpak on 2008-08-19
I have it all set up:

[https://launchpad.net/~k-belding/+archive](https://launchpad.net/~k-belding/+archive)

---

### Post by loell on 2008-08-19
ah, great! you already got it up and running. :)

---

### Post by picpak on 2008-08-19
A working version of tint2 should be on its way :D

---

### Post by picpak on 2008-08-19
UGH! No matter what I do, I can't get tint2 to build. Yet, I have a working deb installed on my machine. The same thing happened to sakura. It's very frustrating. ](*,)

---

### Post by loell on 2008-08-19
but i'm seeing sakura as successfully built?

---

### Post by picpak on 2008-08-19
> **loell said:**
> but i'm seeing sakura as successfully built?

That's because I fixed it.

Still trying with tint...

---

### Post by Stemp on 2008-08-23
Hi picpak, great post, nice idea.
Just a little update. My personnal PPA is still on and I'm still using it for midori and webkit (and others sofwares) but with michelinux we've created a webkit-team with a PPA where you could find webkit related stuffs (webkit, midori and soon epiphany-webkit).
[https://launchpad.net/~webkit-team/+archive](https://launchpad.net/~webkit-team/+archive)

---

### Post by Gourgi on 2008-08-24
picpac thanks for the list
my sources list is getting bigger now LOL

---

### Post by Hire on 2008-08-24
Very useful, nice :D

---

### Post by TheMono on 2008-08-24
If it is any use to anyone, I put Smplayer SVN debs in my PPA semi-regularly.

deb [http://ppa.launchpad.net/themono/ubuntu](http://ppa.launchpad.net/themono/ubuntu) hardy main universe
deb [http://ppa.launchpad.net/themono/ubuntu](http://ppa.launchpad.net/themono/ubuntu) intrepid main universe

---

### Post by Gourgi on 2008-08-26
you may want to add pidgin's PPA 
[https://launchpad.net/~pidgin-developers/+archive](https://launchpad.net/~pidgin-developers/+archive)

> 
This PPA contains packages of Pidgin for already released versions of Ubuntu. This allows you to stay current with Pidgin while using a stable release of Ubuntu.


---

### Post by InfinityCircuit on 2008-08-28
My PPA has everything currently in my signature.  This includes:

gnome-hdaps-applet for those who use hdaps-protect patches.
mupen64plus
infobash (simple script to display machine information written by a Sidux dev)
ipager (updated fluxbox pager)
netconfig (the redhat classic)

Backports:
tor 0.2.0.30 for hardy
rdiff-backup 1.2.0 for hardy

Fixes:
gnome-panel for hardy without arrow on "Main Menu" button.

---

### Post by picpak on 2008-08-29
Thanks everyone; I've added them all. :)

---

### Post by zim2dive on 2009-01-05
New to Ubuntu (1 month now) and still learning my way around...

Been having big troubles with the nvidia drivers on my 8200 (full-screen Flash makes it cry like a small child on drivers newer than 173)... so I've been hand installing some of the nvidia betas, but found that some appear in PPA and might make my life simpler to do that way..

what I was wondering is that under Intrepid, the "easy" way to do nvidia drivers is under the "Hardware Drivers" install panel, which by default offers 173.xx and 177.80... 

If I install a newer driver via PPA (180.18 for example), will it end up as one of my choices in the hardware driver panel?  ie. I've had fairly lousy luck reverting from my hand-installed drivers to the Intrepid default set, but I was thinking my odds would be improved of being able to downgrade if the driver was installed via the same mechanism.

Hopefully that makes any sense... as I said I'm still learning all the lingo.

thanks,
Mike

---

### Post by venator260 on 2009-01-07
Since this thread is ressurected anyway, I use this one to get OpenOffice. org version 3 in Intrepid.

[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

---

### Post by theApokalypsis on 2009-02-28
thanks for the great post. added some good repos to my list :D

would this be a decent one to add? its for the global menu applet from Gnome for a mac like menu on your panel. 

#Global Menu
deb [http://ppa.launchpad.net/globalmenu-team/ubuntu](http://ppa.launchpad.net/globalmenu-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/globalmenu-team/ubuntu](http://ppa.launchpad.net/globalmenu-team/ubuntu) intrepid main

---

### Post by forger on 2009-02-28
You could include a link to all the ppas search:
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

### Post by ingalex on 2009-03-02
On this site you can find more sources.list for Ubuntu, Mint, Debian and a Repo-finder to search repository that contain searched packages.
[http://www.sourceslist.netsons.org]("http://www.sourceslist.netsons.org")
Very good for me!

---

### Post by picpak on 2009-03-10
Alright guys, I've updated the list with all your suggestions.:)

---

### Post by novafluxx on 2009-03-11
This is excellent!! This is EXACTLY what I've been searching for!!!

---

### Post by kevdog on 2009-03-12
I guess I don't understand the ppa.  Say I add the ppa repository to my list (like a personal repository).  How do I know the name of the packages within the particular repository I want to add.  Take firefox nightly build. How would I be able to install this package?

---

### Post by loell on 2009-03-12
> **kevdog said:**
> I guess I don't understand the ppa.  Say I add the ppa repository to my list (like a personal repository).  How do I know the name of the packages within the particular repository I want to add.  Take firefox nightly build. How would I be able to install this package?



you can view package names in say (awn-testing's PPA) at

**[https://launchpad.net/~](https://launchpad.net/~)[COLOR="Red"]awn-testing[/COLOR]/+archive**

---

### Post by kevdog on 2009-03-12
Is there a way to perform what packages are available at a specific archive at the command line?

---

### Post by unutbu on 2009-03-12
Here is a way to find out what packages are available from a specific archive:
The idea is to copy the directory structure that apt uses to /tmp/apt, generate an apt.conf file, and then edit it so apt uses /tmp/apt instead of /. 

Save this as ~/bin/tmp-apt-setup
[PHP]
#!/bin/bash
# Usage:
# tmp-apt-setup "deb http://ppa.launchpad.net/gscrot/ppa/ubuntu intrepid main"
#
mkdir -p /tmp/apt
cd /tmp/apt
apt-config dump > /tmp/apt/apt.conf
sed -i 's|"/"|"/tmp/apt/"|' apt.conf
sed -i 's|/var|/tmp/apt/var|' apt.conf
mkdir -p /tmp/apt/var/lib/apt/lists/partial
mkdir -p /tmp/apt/var/cache/apt/archives/partial
mkdir -p /tmp/apt/var/lib/dpkg
touch /tmp/apt/var/lib/dpkg/status
mkdir -p /tmp/apt/etc/apt
echo "$1" > /tmp/apt/etc/apt/sources.list
apt-get --config-file apt.conf update
[/PHP]
Make it executable, and run it like this:
```

tmp-apt-setup "deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu intrepid main"
apt-cache --config-file /tmp/apt/apt.conf search .

```

The output looks like this:
```

banshee - Media Management and Playback application
banshee-1 - Transitional package
monodoc-banshee-1-manual - Transitional package
monodoc-banshee-manual - Media Management and Playback application (developer documentation)
banshee-extension-mirage - Automatic Playlist Generation Extension for Banshee
libtaglib2.0-cil - CLI library for accessing audio and video files metadata
monodoc-taglib-manual - compiled XML documentation for taglib-sharp
libipod-cil - CLI library for accessing iPods
libipodui-cil - CLI library for accessing iPods (GUI helpers)
monodoc-ipod-manual - compiled XML documentation for ipod-sharp
podsleuth - Tool to discover detailed information about Apple iPods
banshee-extension-lyrics - Lyrics extension for Banshee
libmono-zeroconf1.0-cil - CLI library for multicast DNS service discovery
monodoc-mono-zeroconf-manual - compiled XML documentation for mono-zeroconf
mzclient - CLI library for multicast DNS service discovery (commandline tool)

```

---

### Post by Vadi on 2009-03-16
Please update GScrot for Shutter: [http://shutter-project.org/2009/02/gscrot-is-now-shutter/](http://shutter-project.org/2009/02/gscrot-is-now-shutter/)

---

### Post by kevdog on 2009-03-17
unutbu

Nice script -- I like that alot!

---

### Post by coldmack on 2009-03-18
Thank you. The only thing I notice is, the version of pidgin on there is still slightly old. It is 2.5.1 while 2.5.5 is out, which I hear adds a good amount of updates to MSN which is a bonus for me. And the other things I notice is that the adobe flash one did not show flash 10 for me? Is there another repo for flash 10 or something? Maybe an adobe repo or something? Thanks....

---

### Post by ingalex on 2011-03-29
[CENTER][[IMG]http://wstaw.org/m/2011/03/29/plasma-desktopQS2269.jpg[/IMG]]("http://www.sourceslist.eu/repofinder/")[/CENTER]

[SIZE="3"]Here [/SIZE]**[SIZE="3"][SIZE="4"][[COLOR="Red"] http://www.sourceslist.eu/repofinder/ [/COLOR]]("http://www.sourceslist.eu/repofinder/")[/SIZE][/SIZE]** [SIZE="3"]there is a search engine to find repository that contain packages/programs you are looking for.
With Repo-Finder you can search repository for Linux Mint, Ubuntu, Android and Cydia.
There is a desktop version and a mobile version.
If you want you can collaborate with Repo-Finder project to improve search engine, to add new repositories.
I've indexed all launchpad repositories and much others.
I execute more bash script to index launchpad repositories and to index all contained packages.[/SIZE]

Here there are 2 demonstration video:

[LIST]
DESKTOP VERSION[/LIST]
[http://www.youtube.com/watch?v=ZGCTZLk5vts&feature=player_embedded]("http://www.youtube.com/watch?v=ZGCTZLk5vts&feature=player_embedded")

[LIST]
[*]MOBILE VERSION
[/LIST]
[http://www.youtube.com/watch?v=LKGOkCLPV3M&feature=player_embedded]("http://www.youtube.com/watch?v=LKGOkCLPV3M&feature=player_embedded")

---

