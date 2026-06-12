---
title: "Frugal Install Experiment"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-09-16
Hi,


  I just installed Oneiric Beta 1 on a 4GB hdd/Acer Aspire -3620.

  It was a seamless install.

  I would like some pointers on what programs to remove and how to remove them , ie; Libre Office .. etc becaus it has very low disk space reporting.

  I am sure I can do this from synpatic.
  
 I have 220 MBs of updates waiting and not enough space. The warning screen told me I can use an external storage but did not tell me how to do it.

 Any pointers would be great.

Thanks

*note*

  I just want to use this system to beta test Unity/Gnome 3 desktops and other smaller programs in the repsitories. I am just testing to see how Oneiric works in a frugal environment.

---

### Post by cariboo on 2011-09-16
Have you run:

```
sudo apt-get clean
```

to remove any archived packages. I just did it on a fresh install, and gained and extra 300MiB of space in /, not that I really need it, but I was curious to see how much space was taken up after updates and package installations.

---

### Post by ventrical on 2011-09-17
> **cariboo907 said:**
> Have you run:

```
sudo apt-get clean
```to remove any archived packages. I just did it on a fresh install, and gained and extra 300MiB of space in /, not that I really need it, but I was curious to see how much space was taken up after updates and package installations.


Thanks Caribou. 

 I am about to try that now.

---

### Post by ventrical on 2011-09-17
Yes ... this worked to a point where I now have about 250MBs left on my 4.2GB hdd. It was really tough to do this as I had to update first and broke the linux 3.0.0-11 generic file .. but it repaired itself quite well.

 Certainly there is a lot of garbage from the clean install  and I would like to clean more. I know that teh recovery option in GRUB can do this but is prone to breaking packages and depends.. so I will check into that option .. but any other suggestions are welcome .. and thanks again Caribou.

---

### Post by ranch hand on 2011-09-17
While I really like LibreOffice it is a huge install.
```

sudo apt-get remove libreoffice

```
should get rid of it.  I use Debian so you may want to check synaptic for the correct package name.

Synaptic is a good place to remove stuff too.  Just click on "installed" and the installed packages will be shown.  Scroll through and find what you don't want.

---

### Post by paul_in_london on 2011-09-17
A better way (IMHO) would be to download the **mini.iso** from here (or the corresponding 386 directory):

[http://archive.ubuntu.com/ubuntu/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/)

and reinstall using that. Or you could create a separate install on another partition.

Once you've got your bare-bones system installed, build it up from there with something like:

```
aptitude install --without-recommends xorg xserver-xorg-core \
xserver-input-all xserver-utils x11-xserver-utils \
xorg-input-all xserver-xorg-input-all lightdm lightdm-gtk-greeter \
gnome-session gnome-panel gnome-terminal gnome-themes \
gnome-themes-selected gnome-themes-ubuntu ubuntu-artwork \
light-themes
```

```
aptitude install --without-recommends synaptic \
flashplugin-downloader app-install-data gnome-applets gnome-panel-bonobo \
gvfs-backends indicator-applet-appmenu indicator-applet-complete \
indicator-application libasound-plugins libgtk2-perl libpam-ck-connector \
notification-daemon notify-osd nvidia-settings pulseaudio python-gconf \
software-properties-gtk python-software-properties gnome-keyring \
indicator-appmenu indicator-me indicator-messages indicator-session \
indicator-sound notify-osd-icons pulseaudio-esound-compat \
pulseaudio-module-x11 appmenu-gtk indicator-applet-session \
libpam-gnome-keyring python-indicate
```

---

### Post by ventrical on 2011-09-17
Thanks Ranchand and Paul_in_London!!  Thats great !! :) And I will try those things.

---

### Post by ranch hand on 2011-09-18
That netboot install is really fun to do.  Be sure you have everything you want to add written down as you will boot to a test login and then get a cli prompt to install the rest.

I recommend 2 additional packages;
package "mc" is midnight commander a file browser you can use from the cli in case you want to check some files.

package "elinks" is an internet browser you can use from the cli.  You can imagine that might be handy to have.

They are both lightweight and very useful.  In testing OS' there are times when nothing but your tty prompts may work.  This gives you a file browser and internet access from there.  They may not be real slick and shiny but they work.

Remember that you have nano, a text editor, as part of that netboot base install incase you need to edit any files.

Have FUN.

---

