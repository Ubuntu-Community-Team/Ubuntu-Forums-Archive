---
title: "Standalone Enlightenment Desktop - pulls in Gnome when installing apps"
date: 2020-06-16
forum: New to Ubuntu
---

### Post by blackpointer on 2020-06-16
Hello Folks!

I'm relatively new to Linux, have been experimenting with it since december last year.

My passion is to create minimal installations, where I can choose - piece by piece - what I can put on top. I've been doing this first with the Debian net install, and then with the minimal Ubuntu 18 iso. In the past I've gone for Xfce as the DE, but now I've had an Enlightenment Revelation! Love it!

But I've run into some problems when installing Gnome/Gtk apps on it. Some don't work, others want to pull in many gigabytes and the almost full Gnome desktop. I don't want the gnome shell, I want a lean and mean Enlightenment installation.

The steps I've taken, from the Ubuntu 20 server base install and to arrive at the basic Enlightenment desktop are these (I had to use a lot of --no-install-recommends to avoid pulling in the whole Gnome shell):


 ```
sudo apt-get install xserver-xorg xserver-xorg-core xfonts-base xinit x11-xserver-utils --no-install-recommends 
sudo apt-get install lightdm lightdm-gtk-greeter lightdm-gtk-greeter-settings --no-install-recommends
sudo apt-get install enlightenment terminology
```

This deskop seem to work perfectly fine, in fact I love it! I'm using Bodhi Linux as a model and inspiration (Moksha, the Enlightenment fork). My goal is to arrive at an equally sleek and lightweight, but fully functional, desktop, of my own making. 

I can install a few programs, such as Leafpad. But when I install Gparted (from the command line sudo apt-get install) it will not launch at all. When I install the package gnome-disk-utility from the command line, it pulls in several gigabytes of Gnome related stuff, and then I get the Gnome shell as a login option.

I want to avoid the Gnome shell. Installing Gnome disk Utility works perfectly fine in Bodhi, it just pulls in a regular amount of dependencies.

Obviously I'm missing something here. So I came here to the Ubuntu forum to ask for help, and in the hope that someone will be able to point me in the right direction in how to solve this.

---

### Post by CatKiller on 2020-06-16
Packages have other packages that they depend on - that they won't run without - and other packages that they recommend. Different package managers handle recommended packages differently. You may have better luck by excluding recommended packages.

---

### Post by blackpointer on 2020-06-16
Thanks!

I'm using the Ubuntu Package Search site a lot, to investigate the dependencies of stuff I want to install.

When I use the --no-install-recommends option with gnome-disk-utility, the Disk app won't not even appear in the menu.

I'm wondering what Bodhi (it is based on Ubuntu and use Ubuntu 18 repositories) did to avoid the whole Gnome, and if I can do something similar on an Ubuntu Server base? Maybe there is some basic gnome underlying stuff I can install first, so subsequent install of Gnome apps won't run into what sems like a version of Dependency Hell?

---

### Post by blackpointer on 2020-06-16
I should add that I've build a perfectly functional and minimal Xce  Desktop on the Ubuntu Server 20 base, which works perfectly fine with  gnome apps. When I install gnome-disk-utility there, it installs like  normal and function as normal.

The steps I took with the minimal Xfce desktop, from the server base install, where these:

 ```
 sudo apt-get install xserver-xorg xserver-xorg-core xfonts-base xinit x11-xserver-utils --no-install-recommends
 sudo apt-get install xfwm4 xfce4-panel xfce4-settings xfce4-session xfce4-terminal xfdesktop4 --no-install-recommends
 sudo apt-get install thunar xfce4-power-manager xfce4-whiskermenu-plugin xfce4-pulseaudio-plugin thunar-archive-plugin
 sudo apt-get install lightdm lightdm-gtk-greeter lightdm-gtk-greeter-settings --no-install-recommends
 sudo apt-get install gvfs-backends



```

---

### Post by Holger_Gehrke on 2020-06-17
One difference might be that XFCE is based on GTK+ - just like Gnome - so a lot of the same dependencies are installed, while Enlightenment AFAIK uses it's own set of libraries (EFL). On my XUbuntu 18.04 system (which admittedly has a lot of stuff installed) doing an 'apt --dry-run install gnome-disk-utility' says it would install exactly one package, all dependencies are already satisfied.

Holger

---

### Post by blackpointer on 2020-06-17
Thanks!

In the meantime, I've done some further experimenting. I went back to the 18.04 LTS server iso, installed it and put Enlightenment on top with the same procedure as above.

Here, the installation of gnome-disc-utility works as expected, it pulls in a normal amount of stuff, and no Gnome Shell.

Unfortunately, with the 18.04 LTS you have to add PPA repos to install enlightenment. And in any case, it is the 5 years from now Ubuntu 20 LTS support I'm really after.

So as far as I can tell, this is specific to Ubuntu 20*.* It seems quite absurd to me, it pulls in everything from wallpapers to I think Network Manager!

So it leaves me thinking what is the point in including Enlightenment in the Ubuntu 20 repos, when you can't install it and use it normally as a standalone! Is intended as a secondary DE for the Gnome folks only?

Edit:
I remembered a little bit wrong in the above. I went back to the 18 server iso and installed *Fluxbox *on top of it, to test how the gnome-disk-utility would behave, and it behaved normally. *THEN *I added the Enlightenment DE on top of that again, via the PPA's.
When I tried with Fluxbox on top othe the ***Ubuntu 20*** server base, it acted just like Enlightenment , it pulled in the whole Gnome ecosystem when installing gnome-disc-utility.

---

### Post by blackpointer on 2020-06-17
Another difference between Ubuntu 18 and Ubuntu 20, is that it was a lot easier to install a lean and mean minimal Xfce on top of the base, both the server base and the Ubuntu 18 ''minimal'' iso. 

With the Ubuntu 20 server base, I had to spend a few days experimenting in Virtualbox, to figure I had to add --no-install-recommends to almost everything, even the xserver stuff. One sloppy second installing the most insignificant package and BANG you're downloading the whole Gnome Desktop. In Ubuntu 18 it all went smoothly, with zero --no-install-recommends at all.

Strange!

---

### Post by similar2 on 2020-06-19
Long time Ubuntu/Enlightenment user here (also running E on Arch). If you are looking for a clutter-free and completely customizable distro, then Arch Linux will best suit your needs.

---

### Post by blackpointer on 2020-06-19
Thanks, that's a good tip!

Actually, I have Arch on my daily use computer. This Ubuntu base/Enlightenment (eventually Fluxbox) on top project is for a few other computers, in the workshop and in the garage. 

Arch requires a certain amount of monitoring and maintenance, especially with updates. There are also often small surprises, like, say, audio starting to act unpredictable with an update, and you have to fiddle with it. I don't want to do that on all 5 computers in the house. I'm used to doing Ubuntu and Debian 'Arch style'', from a base install, and it has worked perfectly. A Debian-based base install and then whatever I want on top, ''arch style'', is perfect for those computers. Non-drastic updates, set and forget! And Ubuntu again is perfect for that purpose, with the 5 year LTS support. Debian ony offers 2-3 years. I can have these 3 Ubuntu computers, lean and mean, installed to my exact specifications, for friggin' 5 years, just set and forget and with zero surprises, that's just perfect!

I've done this with zero problems on the Ubuntu 18 LTS base, both the server and the (now discontinued) minimal iso, and I just loved it, zero worries about --no-install-recommends! But now with the Ubuntu 20, it is no longer possible. Something has happened, Ubuntu 20 *REALLY  *loves Gnome! The most innocent little package, if you're not careful with the --no-install-recommends, and BAM you have the whole damn Gnome downloading. It is plain crazy! And, as it turns out, impossible with gnome-disc-utility, probably/possibly lots of other packages. I can do without Gnome Disks, but I want a system with zero worries, that I can install anything on, in a normal fashion, without thinking too much. This worked perfectly with Ubuntu 18, not so now with Ubuntu 20.

The reason I came here is because I did an minimal, piece-by-piece, Xfce install on the Ubuntu 20 server base. This install works as expected, with a lot of tinkering and once set up with lots of --no-install-recommends. I can install gnome-disk-utility in a normal fashion. Not so with Enlightenment. I still hope the problem is on my end, that I'm missing something. I'm just a few months in and I'm still a ''newbie'', lots of stuff I don't know.

I've been testing the Debian Buster base net install, and it works normal, also with Enlightenment. I love Debian, but I really love the Ubuntu 5 year LTS support.

Unfortunately, something has happened, Ubuntu 20 just seems glued to the Gnome shell!

---

