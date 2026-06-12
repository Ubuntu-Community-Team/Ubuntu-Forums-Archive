---
title: "Apt --purge autoremove fails to remove some things."
date: 2021-08-17
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2021-08-17
I was fiddling about with Xfce the other day and ended up removing it. Running focal vanilla otherwise.

```
sudo apt --purge autoremove xubuntu-desktop
```

Problem was it left stuff behind. In this case the plymouth theme was still set to Xubuntu. Not a hard fix of course. If it pulled it in then why didn't it remove it? Had to manually go and figure it out, download the original and then purge the Xubuntu ones?

---

### Post by ActionParsnip on 2021-08-17
Removing the metapackage doesn't remove it's contents. If you want to get rid of Xubuntu (XFCE) then run:
```

sudo apt --purge remove xfce4
sudo apt --purge autoremove

```
This will pull all packages relating to XFCE. You can remove the other packages you don't need as you see fit but this will remove the most part for you

---

### Post by Tadaen_Sylvermane on 2021-08-18
Meta packages aren't supposed to remove packages. I get the concept. Does not equal reality, at least on this installation.

Example.

```
sudo apt --purge autoremove xubuntu-desktop
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  blueman* catfish* engrampa* engrampa-common* fonts-noto-hinted*
  fonts-symbola* gigolo* gimp* gimp-data* gir1.2-appindicator3-0.1*
  gir1.2-cheese-3.0* gir1.2-clutter-1.0* gir1.2-cogl-1.0*
  gir1.2-coglpango-1.0* gir1.2-gst-plugins-base-1.0* gir1.2-gtkclutter-1.0*
  gstreamer1.0-nice* gucharmap* hddtemp* inxi* libamd2* libbabl-0.1-0*
  libblas3* libburn4* libcamd2* libccolamd2* libcholmod3* libexo-1-0*
  libfarstream-0.2-5* libgadu3* libgegl-0.4-0* libgegl-common* libgfortran5*
  libgimp2.0* libgtksourceview-3.0-1* libgtksourceview-3.0-common*
  libgtkspell0* libgucharmap-2-90-7* libheif1* libisofs6* libjte2*
  libkeybinder-3.0-0* liblapack3* libmeanwhile1* libmetis5* libmng2*
  libmypaint-1.5-1* libmypaint-common* libprotobuf-c1* libpurple-bin*
  libpurple0* libraw19* libtagc0* libumfpack5* libunique-1.0-0*
  libxfce4ui-utils* libzephyr4* lightdm-gtk-greeter-settings* mate-calc*
  mate-calc-common* menulibre* mousepad* mugshot* numix-gtk-theme* numlockx*
  onboard* onboard-common* onboard-data* parole* pastebinit* pidgin*
  pidgin-data* pidgin-otr* python3-xcffib* ristretto* sgt-launcher*
  sgt-puzzles* shimmer-themes* thunar* thunar-archive-plugin*
  thunar-media-tags-plugin* thunar-volman* tree* xfburn* xfce4-appfinder*
  xfce4-cpugraph-plugin* xfce4-dict* xfce4-mailwatch-plugin*
  xfce4-netload-plugin* xfce4-notes* xfce4-notes-plugin* xfce4-panel*
  xfce4-panel-profiles* xfce4-places-plugin* xfce4-pulseaudio-plugin*
  xfce4-screenshooter* xfce4-systemload-plugin* xfce4-taskmanager*
  xfce4-verve-plugin* xfce4-weather-plugin* xfce4-whiskermenu-plugin*
  xfce4-xkb-plugin* xfpanel-switch* xubuntu-artwork*
  xubuntu-community-wallpapers* xubuntu-community-wallpapers-focal*
  xubuntu-core* xubuntu-default-settings* xubuntu-desktop* xubuntu-docs*
  xubuntu-wallpapers*
```

Looks like it's removing a ton of stuff.

Also while I'm hardly in a position to say something is wrong it seems meta packages should meta remove what they install else you have left overs as in my situation. As it is now the only way to clean it is to manually chase down whatever was in the apt log on that install. Seems an oversight to me. Just a thought.

---

### Post by ActionParsnip on 2021-08-19
Yes because XFCE is a lot of stuff. I assume you have an alternative desktop environment to use and is installed. A desktop environment is not a trivial piece of software. If you don't want XFCE then those packages can be removed. If you have other desktop environments then those will stand.

---

### Post by Tadaen_Sylvermane on 2021-08-19
Which is it?

I ask why it doesn't remove everything it installed you say this.

> [COLOR=#000000][FONT=Ubuntubeta]Removing the metapackage doesn't remove it's contents[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR]
I show that it removes packages and you say this.

> [COLOR=#000000][FONT=Ubuntubeta]Yes because XFCE is a lot of stuff.[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR]
So if it removes some packages that it installed (yet it's not suppose to?), _**why not all of what it installed?**_ In this case the Xubuntu plymouth was not the original plymouth screen. It was changed after the Xubuntu-desktop package installation. It is clearly a Xubuntu package and came with the meta, not a regular package included on the stock Ubuntu installation. It did not revert after purging the package. Why?

---

### Post by Impavidus on 2021-08-19
I can't make much sense of that output for simulater removal of xubuntu-desktop. Lots of packages and I won't track down which are direct or indirect dependencies of xubuntu-desktop. I don't see plymouth-theme-xubuntu-logo listed as one of the packages for removal, which is the package containing the xubuntu logo for plymouth.

One other idea: Purging the package removes all files from the package, but may not undo all actions done by the installation script. I don't know the internals of plymouth. When removing a theme, does it revert to some other installed theme or does it copy the logo from the old theme somewhere and continue using it until some other default is set by the install script of a different theme?

---

### Post by ActionParsnip on 2021-08-19
Might explain better
[https://askubuntu.com/questions/1111491/why-does-removing-a-metapackage-not-remove-the-dependencies-which-it-installed](https://askubuntu.com/questions/1111491/why-does-removing-a-metapackage-not-remove-the-dependencies-which-it-installed)

---

### Post by tea for one on 2021-08-19
> **Tadaen_Sylvermane said:**
> In this case the plymouth theme was still set to Xubuntu. Not a hard fix of course. If it pulled it in then why didn't it remove it? Had to manually go and figure it out, download the original and then purge the Xubuntu ones?

> Plymouth is the application which provides the graphical "splash" screen when booting and shutting down an Ubuntu system.
Note that on Ubuntu, Plymouth is considered to be the "owner" of the console device (/dev/console) so no application should attempt to modify terminal attributes for this device at boot or shutdown. 

Text extracted from [https://wiki.ubuntu.com/Plymouth](https://wiki.ubuntu.com/Plymouth)

During the removal of a meta-package, I wonder if [COLOR="#0000FF"]purge autoremove[/COLOR] is acting sensibly by ignoring anything to do with the boot process.

If the background image for plymouth is forcibly removed, does the PC boot?

I'm just guessing - I was just interested if some commands are more judicious in certain circumstances?

---

### Post by Dennis N on 2021-08-19
> Also while I'm hardly in a position to say something is wrong it seems meta packages should meta remove what they install else you have left overs as in my situation.
The "leftovers" are possibly still dependencies of other packages so won't be autoremoved.

---

### Post by Tadaen_Sylvermane on 2021-08-20
> [COLOR=#000000] When removing a theme, does it revert to some other installed theme or does it copy the logo from the old theme somewhere and continue using it until some other default is set by the install script of a different theme?

Is only reason I posted. I'd have never known if I didn't reboot and see the Xubuntu splash.[/COLOR]

---

