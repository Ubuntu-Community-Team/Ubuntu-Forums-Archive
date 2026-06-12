---
title: "HOWTO: Install Quod Libet Media Player"
date: 2005-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by mird on 2005-06-14
[color=red]***** UPDATED *****[/color] 
* - 17/Jun/2005*
I noticed this morning that mandb was complaining about a bung manpage, so I fixed it (I hope!).  See [font=fixed]quodlibet_0.11-2ubuntu1~mird_all.deb[/font].
* - 15/Jun/2005*
I decided to try out some of the plugins and realised plugin support wasn't introduced until version 0.11, and the version I flogged from Debian Sid is 0.10.1.  No matter, I built 0.11 and packaged it up for all :)

---

I've been using Ubuntu's default "Music Player" or Rhythmbox for some time now and even though I do really like it there have been a number of small annoyances/limitations that have been slowly wearing at my tolerance.  The upcoming 0.9 release of Rhythmbox looks promising as a cure for many of my frustrations but it's just not getting here fast enough ;) - props to the Rhythmbox dev team all the same!  \\:D//

Anyway, recently I was reading through some old posts on this humble forum and I noticed some comments about another media player which has taken the crown as my current favourite.

Quod Libet is a media player very similar to Rhythmbox, but with a number of features and improvements which enhance the user experience. It comes bundled with Ex Falso, a simple yet powerful file tagger.  See the [Quod Libet Website](http://www.sacredchao.net/quodlibet) for more tantalising information.

Luck would have it Quod Libet is written in Python, so it theoretically shouldn't even really need 'installing' as such, but there are some dependancies that need resolving and at the end of the day we all really wish for nice tidy packages! AM I RITE?!?  Thankfully some dear soul packaged Quod Libet for Debian Sid, however there was a dependancy issue regarding Python versions - apparently 2.3 is great, but 2.4 it hate!  I haxxed the package to exclude to <2.4 dependancy and it appears to work perfectly on my system running Python 2.4.

So, here goes:

**INSTALL**

1. Make sure you have all the dependacy packages installed.

```
sudo apt-get install python python-gtk2 python-pymad python-pyvorbis python-id3lib libgtk2.0-0
```
2. Fetch the Quod Libet packages.

```
wget http://newstuff.orcon.net.nz/ubuntu/quodlibet/quodlibet_0.11-2ubuntu1~mird_all.deb
wget http://newstuff.orcon.net.nz/ubuntu/quodlibet/quodlibet-ext_0.11-1ubuntu1~mird_i386.deb
```
3. Install the packages.

```

sudo dpkg -i quodlibet-ext_0.11-1ubuntu1~mird_i386.deb
sudo dpkg -i quodlibet_0.11-2ubuntu1~mird_all.deb

```

There should now be new icons under Applications -> Sound & Video.  Enjoy :)


**OPTIONAL - Install FLAC/Musepack/MOD Support**

If (like me) you have any MOD, FLAC or MPC files in your audio collection, then you'll also want to install support for them.  I've haxxed together some packages which provide the neccessary Python bindings for Quod Libet.

1. Install libflac and libmodplug.

```
sudo apt-get install libflac6 libmodplug0
```
2. Install libmpc as described in [this thread](http://www.ubuntuforums.org/showthread.php?t=38085) (note the updated instructions in the lower part of the first post).


3. Fetch the python binding packages.

```
wget http://newstuff.orcon.net.nz/ubuntu/quodlibet/python-flac_0.0.3-1ubuntu1~mird_i386.deb
wget http://newstuff.orcon.net.nz/ubuntu/quodlibet/python-modplug_1.1-1ubuntu1~mird_i386.deb
wget http://newstuff.orcon.net.nz/ubuntu/quodlibet/python-musepack_0.3-1ubuntu1~mird_i386.deb
```
4. Install the packages.

```
sudo dpkg -i python-flac_0.0.3-1ubuntu1~mird_i386.deb
sudo dpkg -i python-modplug_1.1-1ubuntu1~mird_i386.deb
sudo dpkg -i python-musepack_0.3-1ubuntu1~mird_i386.deb
```
Enjoy :)

---

### Post by jonny on 2005-06-15
Odd.  A couple of months back I downloaded Quod Libet and Ex Falso from the official site, and it worked just fine out of the box.  I guess the dependency problems you outline are a recent thing.

I don't use it, though, as I can't figure out how to get songs on an album to play in the right order - it always adds them to the playlist alphabetically by song title.  Perhaps it's because most of music doesn't seem to have the track number tag populated.

It's a shame, because otherwise Quod Libet looks good.  Has this issue been resolved in the latest version (I'm on 0.10)?  Or am I just to dumb to use a simple music player?

Ex Falso's great, though.

---

### Post by jonny on 2005-06-15
I've answered my own question.  Quod Libet allows you to choose which fields are displayed when you create a playlist, so all I needed to do was display the filename and sort on that.

It might now become my music player of choice.  Excellent.

---

### Post by Evoreth on 2005-06-15
Well, I compiled it two or three days ago and it wasn't that hard, either. Quod Libet is nice, fast and the tagging tools are way better than EasyTag, in my opinion.

Make sure to grab the OSD-Plugin: [http://www.sacredchao.net/quodlibet/wiki/Plugins](http://www.sacredchao.net/quodlibet/wiki/Plugins)

---

### Post by jonny on 2005-06-15
If anyone else goes down the source code route, make sure you install the python2.4-dev package.  Without it, everything seems to work OK, but you won't get the panel applet.

---

### Post by escobar on 2005-06-18
I installed this and decided I didn't like it, but thanks a lot for the tutorial, very helpful to newbies like myself. Question is when "uninstalling" it, how do I remove all the dependencies? If I use "aptitude purge" then paste the depedency packages you listed in step 1, it wants to remove over 200 some-odd packages. Some of which I'm either using, don't know what they do, or sound really important:

root@TREADSTONE:/home/bsanks # aptitude purge python python-gtk2 python-pymad python-pyvorbis python-id3lib libgtk2.0-0
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following packages are unused and will be REMOVED:
  gcc-4.0-base libcairo1 libpixman1 libstdc++6
The following packages will be automatically REMOVED:
  bicyclerepair bittorrent bug-buddy capplets capplets-data
  contact-lookup-applet eog evolution evolution-data-server
  evolution-exchange evolution-webcal file-roller gaim gcalctool
  gconf-editor gconf2 gdm gedit gedit-common gimp gimp-python gksu
  gnome-about gnome-app-install gnome-applets gnome-applets-data
  gnome-control-center gnome-cups-manager gnome-games gnome-gv
  gnome-keyring gnome-media gnome-menus gnome-netstatus-applet
  gnome-nettool gnome-panel gnome-panel-data gnome-pilot
  gnome-pilot-conduits gnome-session gnome-spell gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-themes gnome-utils
  gnome-volume-manager gnomemeeting gstreamer0.8-gnomevfs gstreamer0.8-misc
  gstreamer0.8-vorbis gthumb gtk2-engines-clearlooks
  gtk2-engines-industrial gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  gtkhtml3.6 gucharmap hal-device-manager hwdb-client libbonoboui2-0
  libcamel1.2-3 libebook1.2-3 libecal1.2-2 libedata-book1.2-2
  libedata-cal1.2-1 libedataserver1.2-4 libedataserverui1.2-4 libeel2-2
  libegroupwise1.2-5 libgail-common libgail17 libgal2.4-0 libgal2.4-common
  libgconf2-4 libgimp2.0 libgksuui1.0-0 libglade2-0 libgnome-desktop-2
  libgnome-keyring0 libgnome-menu0 libgnome2-0 libgnome2-canvas-perl
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0
  libgnomecupsui1.0-1 libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-common libgstreamer-gconf0.8-0 libgtk2-perl libgtk2.0-bin
  libgtk2.0-common libgtkhtml3.6-18 libgtksourceview1.0-0 libgtkspell0
  libgucharmap4 libmetacity0 libnautilus-burn1 libnautilus-extension1
  libpanel-applet2-0 librsvg2-2 librsvg2-common libvte4 libwnck16 lsb
  metacity mozilla-firefox nautilus nautilus-cd-burner nautilus-sendto
  openoffice.org-gtk-gnome python-adns python-apt python-cddb
  python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-eunuchs python-examples python-gadfly python-gd python-gdbm
  python-gdchart python-genetic python-geoip python-glade2 python-gnome2
  python-gnupginterface python-gst python-htmlgen python-htmltmpl
  python-imaging python-imaging-sane python-jabber python-kjbuckets
  python-ldap python-musicbrainz python-mysqldb python-netcdf python-newt
  python-numarray python-numeric python-opengl python-osd python-pam
  python-parted python-pexpect python-pgsql python-pisock python-pqueue
  python-pyao python-pylibacl python-pyogg python-pyopenssl python-pyorbit
  python-pyxattr python-reportlab python-simpletal python-soappy
  python-sqlite python-stats python-syck python-tk python-unit python-xdg
  python-xml python-xmpp python2.4-gd python2.4-glade2 python2.4-gnome2
  python2.4-gtk2 rhythmbox sound-juicer synaptic tsclient ubuntu-artwork
  update-manager update-notifier vino xchat xchat-common xsane xscreensaver
  xscreensaver-gl zenity
The following packages will be REMOVED:
  bicyclerepair bittorrent bug-buddy capplets capplets-data
  contact-lookup-applet eog evolution evolution-data-server
  evolution-exchange evolution-webcal file-roller firefox gaim gcalctool
  gconf-editor gconf2 gdesklets gdm gedit gedit-common gimp gimp-python
  gksu gnome-about gnome-app-install gnome-applets gnome-applets-data
  gnome-control-center gnome-cups-manager gnome-games gnome-gv
  gnome-keyring gnome-media gnome-menus gnome-netstatus-applet
  gnome-nettool gnome-panel gnome-panel-data gnome-pilot
  gnome-pilot-conduits gnome-session gnome-spell gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-themes gnome-utils
  gnome-volume-manager gnomemeeting gstreamer0.8-gnomevfs gstreamer0.8-misc
  gstreamer0.8-vorbis gthumb gtk2-engines-clearlooks
  gtk2-engines-industrial gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  gtkhtml3.6 gucharmap gxine hal-device-manager hwdb-client libbonoboui2-0
  libcamel1.2-3 libebook1.2-3 libecal1.2-2 libedata-book1.2-2
  libedata-cal1.2-1 libedataserver1.2-4 libedataserverui1.2-4 libeel2-2
  libegroupwise1.2-5 libgail-common libgail17 libgal2.4-0 libgal2.4-common
  libgconf2-4 libgimp2.0 libgksuui1.0-0 libglade2-0 libgnome-desktop-2
  libgnome-keyring0 libgnome-menu0 libgnome2-0 libgnome2-canvas-perl
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0
  libgnomecupsui1.0-1 libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-common libgstreamer-gconf0.8-0 libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtkhtml3.6-18
  libgtksourceview1.0-0 libgtkspell0 libgucharmap4 libmetacity0
  libnautilus-burn1 libnautilus-extension1 libpanel-applet2-0 librsvg2-2
  librsvg2-common libvte4 libwnck16 libwxgtk2.5.3 liferea liferea-gtkhtml
  lsb metacity mozilla-firefox nautilus nautilus-cd-burner nautilus-sendto
  openoffice.org-gtk-gnome python python-adns python-apt python-cddb
  python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-eunuchs python-examples python-gadfly python-gd python-gdbm
  python-gdchart python-genetic python-geoip python-glade2 python-gnome2
  python-gnome2-extras python-gnupginterface python-gst python-gtk2
  python-htmlgen python-htmltmpl python-id3lib python-imaging
  python-imaging-sane python-jabber python-kjbuckets python-ldap
  python-musicbrainz python-mysqldb python-netcdf python-newt
  python-numarray python-numeric python-opengl python-osd python-pam
  python-parted python-pexpect python-pgsql python-pisock python-pqueue
  python-pyao python-pylibacl python-pymad python-pyogg python-pyopenssl
  python-pyorbit python-pyvorbis python-pyxattr python-reportlab
  python-simpletal python-soappy python-sqlite python-stats python-syck
  python-tk python-unit python-xdg python-xml python-xmpp python2.4-gd
  python2.4-glade2 python2.4-gnome2 python2.4-gnome2-extras python2.4-gtk2
  rhythmbox sound-juicer synaptic tsclient ubuntu-artwork update-manager
  update-notifier vino vlc wxvlc xchat xchat-common xsane xscreensaver
  xscreensaver-gl zenity
0 packages upgraded, 0 newly installed, 216 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 414MB will be freed.

I'm sure you can understand how this makes me a little uncomfortable. I would like to remove any extra dependencies I no longer need, but don't want to blow up Ubuntu in the process. Any insight would be appreciated. Thanks.

---

### Post by mird on 2005-06-19
Most of the dependancy packages are required for other packages which explains why aptitude wants to remove so much more than just the packages you specified.  Because of this it is difficult to reverse the procedure as it will differ from system to system depending upon which packages are installed.

However if you wish to remove 'orphaned' packages (such as there would be in your situation), you can try using [font=fixed]deborphan[/font].  Here is a good article detailing it's usage and although it's written with Debian in mind it'll work in exactly the same way on Ubuntu:

[Removing unnecessary packages with deborphan](http://www.debian-administration.org/articles/134)

---

### Post by escobar on 2005-06-20
Thanks alot everyone.

---

### Post by vaskark on 2005-06-28
I've been using quodlibet for a while now and really like it. But all of the sudden it won't open. At the command line I get:
 > Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 333, in ?
    import gtk
ImportError: No module named gtk
I haven't uninstalled anything related (AFAIK). Anyone else experiencing this?

---

### Post by mird on 2005-06-28
I know you said you haven't uninstalled anything, but try this and see if it fixes the problem:

```
sudo apt-get install python-gtk2
```

---

### Post by vaskark on 2005-06-28
I've got python-gtk2 :(

---

### Post by mird on 2005-06-28
The only thing I can suggest is try reinstalling python-gtk2 and python itself.
```
sudo apt-get --reinstall install python python-gtk2
```

---

### Post by vaskark on 2005-06-28
Didn't work, either. I'm getting the same error with every python app i have: quodlibet, smeg, ...

*tear*

---

### Post by Hamman on 2005-07-22
Thanks for a great guide! Worked perfectly! :smile:

---

### Post by rwabel on 2005-07-23
I think that the problem is that python-gtk2 conflicts with these packages: python-gdk-imlib, python-glade, python-gnome, python-gtk

I really don't know why the name doesn't match, have you guys the same output when doing the status check of python-gtk2?
```
rwabel@RALPH:~/compiling $ dpkg --status python-gtk2
Package: python-gtk2
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 104
Maintainer: Sebastien Bacher <seb128@debian.org>
Architecture: all
Source: pygtk
Version: 2.6.1-0ubuntu2
Depends: python (<< 2.5), python2.4-gtk2, python (>= 2.4)
Conflicts: python-gdk-imlib, python-glade, python-gnome, python-gtk
Description: Python bindings for the GTK+ widget set
 This archive contains modules that allow you to use GTK+ in Python
 programs. This package contains the bindings for the new version 2.0
 of that toolkit.
 .
 This package is a dependency package, which select the right package
 for the default Python version (currently v2.4).
 .
  Author:   James Henstridge <james@daa.com.au>
  Homepage: http://www.daa.com.au/~james/software/pygtk/
```

---

### Post by npaladin2000 on 2005-08-11
Incidentally, the program doesn't work.  It sticks on "opening audio device."  When I CTRL-C the sucker, then I see that it failed ot open ALSA, falling back to ESD, and then a window saying it couldn't open the audio device.

Of COURSE it couldn't open the audio device, ESOUND has it open!!!  This proggie only works through direct soundcard access?  That's just wrong.

---

### Post by mird on 2005-08-12
Yes, I believe you're correct.  IIRC it's something the author is unhappy about also, and is intending to address the issue with the next release.

Incidentally, it works fine for me ;)

---

### Post by Mallin on 2005-08-29
I tried to install quodlibet. First i went to quodlibet's [homepage](http://www.sacredchao.net/quodlibet), downloaded quodlibet-0.12.tar.gz and installed it with make/make install. Everything seemed to to be ok, i got quodlibet icon under Applications --> Sound & Video. But when i try to run it, nothing happens. I just see "python /usr/local/bin/quodlibet" process and no quodlibet.

I tried to uninstall quodlibet, but i don't know how, make uninstall and make deinstall won't work.

I tried to install quodlibet again with instructions from this topic, but it didn't make any difference, there's still only that process, no quodlibet. Any ideas what should i do?

---

### Post by ddragos on 2005-09-12
[QUOTE=npaladin2000]Incidentally, the program doesn't work.  It sticks on "opening audio device."  When I CTRL-C the sucker, then I see that it failed ot open ALSA, falling back to ESD, and then a window saying it couldn't open the audio device.

Of COURSE it couldn't open the audio device, ESOUND has it open!!!  This proggie only works through direct soundcard access?  That's just wrong.[/QUOTE]

I just ran into this myself.  I went to ~/.quodlibet/config and changed the last line under settings to:

backend = ao:esd

Seems to work fine for me now.

---

### Post by manicka on 2005-09-12
>  The upcoming 0.9 release of Rhythmbox looks promising as a cure for many of my frustrations but it's just not getting here fast enough ;) - props to the Rhythmbox dev team all the same!  \\:D//


Rhythmbox 0.9 is in breezy

---

### Post by rwabel on 2005-09-12
quodlibet is also in breezy! But in my case the album cover is never displayed :-)

---

### Post by fer_ref on 2005-10-17
Where can i wget amd64 packages of quodlibet ?

---

