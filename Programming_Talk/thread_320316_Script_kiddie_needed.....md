---
title: "Script kiddie needed...."
date: 2006-12-17
forum: Programming Talk
---

### Post by John E on 2006-12-17
Although I've been programming for longer than I can remember, I've somehow managed to avoid scripting languages. I'm trying to install a new graphics driver for my Ubuntu PC but it keeps throwing up this error:- **" Could not find X server driver install path "**. I looked in **install.sh** where i found the function that throws up the error.....
```
function SetXInstallPath
{
    if [ "$XPRESENT"=="1" ]; then
        export XINSTALLDIR=$XPATH/$LIBPATH/modules/drivers
        if ! test -e $XINSTALLDIR ; then
           ** echo -e "$RED\033[1mERROR\033[0m: \033[1mCould not find X server driver install path.\033[0m"**
            echo ""
            exit 1
        fi
    else
        echo -e "$RED\033[1mERROR\033[0m: \033[1mX server not present.\033[0m"
        echo ""
        exit 1
    fi
}
```
Obviously, $XINSTALLDIR isn't being set up (or found). But I don't understand the line:- **export XINSTALLDIR=$XPATH/$LIBPATH/modules/drivers**. What exactly is the program trying to find (or set up) here? I'm just wondering if there might be something I could set up manually to get me past this error?

---

### Post by po0f on 2006-12-17
John E,

You could try changing the export line to the following:
```
[FONT="Courier New"]export XINSTALLDIR="$XPATH/$LIBPATH/modules/drivers"[/FONT]
```

The script is trying to combine the variables XPATH and LIBPATH ( and modules/drivers) into XINSTALLDIR, where, presumably, X is installed in.  Maybe set up an `echo "$XINSTALLDIR"` right before the if statement to see if anything looks fishy with where the script thinks you have X installed to.

BTW, there are probably easier ways to install a video card driver than using some script you found on the forums.  What kinda card is it?

---

### Post by John E on 2006-12-17
It's a Matrox Millennium G400. I downloaded the driver (as a tarball) and unpacked it. According to the instructions, I now need to run this script file. But if there's another way, I'll happily try it...!

[Edit...]
I tried that modification but it didn't make a difference However, adding the** echo** line produced:-  **/usr/X11R6/lib/modules/drivers**

**/usr/X11R6/lib** seems to exist on my system - but not **modules/drivers**. I'll try creating them manually and see what happens.

---

### Post by po0f on 2006-12-17
John E,

I thought it might have been a quoting problem; guess not.

Have you tried installing [this](http://packages.ubuntu.com/edgy/x11/xserver-xorg-video-mga)?

---

### Post by John E on 2006-12-17
I downloaded it and unpacked the tar file - but there are no instructions for what to do with the files. I've tried a couple of obvious things such as 'make' and 'sh install-sh' but nothing seems to work.... :(

---

### Post by po0f on 2006-12-17
John E,

Install it via Apt.  Use `aptitude` from the command line, or Synaptic for a GUI.

---

### Post by John E on 2006-12-17
I haven't got much experience of apt and Synaptic doesn't seem to list it as an installable package. I tried typing this:-

**sudo apt-get install xserver-xorg-video-mga**

but it returned these messages:-

[B]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xserver-xorg-video-mga[/B]

Am I doing something obviously wrong?

---

### Post by po0f on 2006-12-17
John E,

No, I just thought you were using Edgy.  Try this one:
```
[FONT="Courier New"]$ sudo aptitude install xserver-xorg-driver-mga[/FONT]
```

---

### Post by John E on 2006-12-17
That seemed a bit more positive but I'm still not sure if anything got installed. Here's the output I got:-

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  acpi-support app-install-data app-install-data-commercial base-files
  bind9-host binutils binutils-static capplets-data cpio cupsys cupsys-bsd
  cupsys-client deskbar-applet desktop-file-utils dnsutils dpkg dpkg-dev
  dselect eog evince file-roller firefox firefox-gnome-support gdb gdm
  gedit gedit-common gimp gimp-data gimp-python gnome-about
  gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-control-center gnome-desktop-data
  gnome-doc-utils gnome-games gnome-games-data gnome-media gnome-menus
  gnome-panel gnome-panel-data gnome-screensaver gnome-session
  gnome-terminal gnome-terminal-data gnome-themes gnupg gstreamer0.10-alsa
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-x gtk2-engines-clearlooks
  gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  gtkhtml3.8 gzip hal hal-device-manager info language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector language-selector-common libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-glib1 libbind9-0
  libcupsimage2 libcupsys2 libdns21 libeel2-2 libeel2-data libfreetype6
  libgd2-noxpm libgimp2.0 libglib2.0-0 libglib2.0-data libgnome-desktop-2
  libgnome-menu2 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgnutls12 libgsf-1-113
  libgsf-1-common libgstreamer-plugins-base0.10-0 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtkhtml3.8-15 libgtksourceview-common
  libgtksourceview1.0-0 libhal-storage1 libhal1 libisc11 libisccc0
  libisccfg1 libkrb53 liblwres9 libmagick9 libmetacity0 libmusicbrainz4c2a
  libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libnspr4
  libnss3 libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpng12-0
  libpq4 libsmbclient libsoup2.2-8 libssl0.9.8 libtiff4 libtotem-plparser1
  libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libxfont1
  linux-386 linux-image-386 linux-restricted-modules-386
  linux-restricted-modules-common login lvm2 metacity mysql-common nautilus
  nautilus-cd-burner nautilus-data openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  openssh-client openssl passwd pcmcia-cs pmount ppp python-gmenu
  python-pyorbit python-uno python-vte python2.4 python2.4-examples
  python2.4-gdbm python2.4-minimal python2.4-pyorbit python2.4-tk
  samba-common screen smbclient sound-juicer ssh-askpass-gnome tar totem
  totem-gstreamer ttf-opensymbol ubuntu-base ubuntu-desktop ubuntu-docs
  ubuntu-minimal ubuntu-standard wpasupplicant xinit xserver-xorg-core
  xserver-xorg-input-mouse yelp zenity
0 packages upgraded, 0 newly installed, 0 to remove and 204 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

---

### Post by po0f on 2006-12-18
John E,

Looks like it is already installed.  Are you having problems configuring it?

---

### Post by John E on 2006-12-18
To my amazement, I eventually managed to get this working this morning. I came across [this install script](http://tuxx-home.at/archives/2006/10/24/T11_52_15/) and found that I needed to install the drivers with the **--overwrite** option (note the double '-' sign). The problem seems to be caused by the installer. If you don't specifiy that particular option, it tells you that the drivers are up-to-date - even if they're not.

It's taken me 5 whole weeks to install this driver and I must say that I'm still bitterly disappointed that driver installation, in general, is so massively difficult under Linux. There seems to be no unified installation procedure and even the most experienced of users seem to be fumbling around in the dark. This really is a _very_ weak area that needs tightening up considerably.

---

### Post by clubsoda on 2006-12-19
Hi John E,
I'm right there with you, battling the same problems with my Matrox G550 and the official scripts which only support up to Xorg 7.0.0.  I tried hacking the script, replacing 7.0.0 with 7.1.1 and renaming the directory, however I got errors running the script.  The tuxx-home.at link looked very promising but it throws out similar errors then deletes itself, so it's kind of hard to debug!

Someone please help with this error:-```
Verifying archive integrity... All good.
Uncompressing Unofficial Matrox G-Series Driver by tuxx-home.at..............................................
./install.sh: 42: function: not found
./install.sh: 54: function: not found
./install.sh: 63: function: not found
./install.sh: 80: function: not found
./install.sh: 128: function: not found
[: 173: ==: unexpected operator
```Looks like Xubuntu uses **dash** instead of **bash**.  Does dash not support inline function definitions?  The code probably looks something like this:-```
function IsRoot
{
    # check for superuser mode
    if ! test -r /proc/kmsg ; then
        echo "---------------------------------------------------------"
        echo -e "$RED\033[1mERROR\033[0m: \033[1mYou must be logged in as Root to run this program.\033[0m"
        echo "---------------------------------------------------------"
        echo ""
        exit 1
    fi
}
```Cheers.

---

### Post by clubsoda on 2006-12-19
Solved.  Looks like it is indeed a dash problem.  [This page](http://www.tuxx-home.at/cmt.php?article=/2006/10/24/T11_52_15/index.html) helped.```
sh matroxdriver_mga-x86_32-4.4.1-installer.run --extract-only
sudo bash install.sh -overwrite
```Have to reboot now and see if my graphics are fixed...

---

### Post by John E on 2006-12-20
**clubsoda** - you're right about the dash/bash issue. If you still have problems, join [this thread]("http://forum.matrox.com/mga/viewtopic.php?p=113424#113424") on the Matrox user forum.

---

