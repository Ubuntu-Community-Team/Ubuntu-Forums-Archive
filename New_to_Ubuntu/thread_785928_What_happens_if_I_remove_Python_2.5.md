---
title: "What happens if I remove Python 2.5?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-05-07
I've got a weird itch to remove it, maybe because I don't like the name? Would it do anything if I removed it?


.

---

### Post by Nxion on 2008-05-07
To be honest, I don't believe it would hurt anything. Maybe somewhere down the line you may run across a application that need python. Maybe not. If so then just reload it.

---

### Post by tamoneya on 2008-05-07
you dont want to do that.  It depends exactly what you have installed but some programs have python dependencies.  These programs will all become non-functional.  Also it is very useful jsut by itself.  If you every want to learn a programming langauge I would recommend python.  It is very simple but at the same time VERY powerful.

---

### Post by Zorael on 2008-05-07
If you tag it for removal in Synaptic, a box should pop up if that action would imply removing more packages. It should also pop up once you hit Apply.

If the list only includes library packages (basically those that start with **lib**), it's likely safe to do. But if it seems to want to remove all kinds of stuff that you use, then you'd be better off bringing Python 2.5 to counseling and make up.

---

### Post by quelx on 2008-05-07
Try it in Synaptic, search for Python and remove it, you will see a huge list of applications that have python as their dependency.  It is likely most if not all of them will break, rendering your system mostly useless.

```
$ sudo apt-get remove python
The following packages will be REMOVED:
alacarte alsa-utils apport apport-gtk apturl avant-window-navigator
  awn-manager blender bluez-gnome brasero bug-buddy capplets-data
  command-not-found compiz compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compiz-gnome compizconfig-settings-manager
  contact-lookup-applet deskbar-applet displayconfig-gtk ekiga eog evince
  evolution evolution-data-server evolution-exchange evolution-plugins
  evolution-webcal f-spot fast-user-switch-applet file-roller
  firefox-3.0-gnome-support firefox-gnome-support foomatic-db-hpijs gcalctool
  gconf-editor gconf2 gdebi gdebi-core gdm gedit gimp-gnomevfs gimp-python
  gksu gnome-app-install gnome-applets gnome-applets-data gnome-control-center
  gnome-doc-utils gnome-games gnome-games-data gnome-keyring gnome-media
  gnome-media-common gnome-menus gnome-mount gnome-netstatus-applet gnome-orca
  gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits
  gnome-power-manager gnome-raw-thumbnailer gnome-screensaver gnome-session
  gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils
  gnome-volume-manager gstreamer0.10-gnomevfs gstreamer0.10-plugins-good
  gtkhtml3.14 guidance-backends hal-cups-utils hpijs hplip hwtest hwtest-gtk
  jockey-common jockey-gtk language-selector language-selector-common
  launchpad-integration libawn0 libbonoboui2-0 libbonoboui2-dev libcamel1.2-11
  libdeskbar-tracker libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libexchange-storage1.2-3
  libgail-gnome-module libgconf2-dev libgdl-1-0 libgdl-gnome-1-0 libgksu2-0
  libglade2-dev libgnome-desktop-2 libgnome-media0 libgnome-vfs2.0-cil
  libgnome-window-settings1 libgnome2-0 libgnome2-common libgnome2-dev
  libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomekbd-common
  libgnomekbd2 libgnomekbdui2 libgnomeui-0 libgnomeui-dev libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-dev libgnomevfs2-extra
  libgtkhtml3.14-19 libgtkhtml3.16-cil libgweather-common libgweather1
  liblpint-bonobo0 libmetacity0 libpanel-applet2-0 libtotem-plparser10
  lsb-release metacity metacity-common mousetweaks nautilus nautilus-cd-burner
  nautilus-data nautilus-sendto nautilus-share network-manager-gnome
  notification-daemon onboard openoffice.org-gnome openoffice.org-writer
  pidgin pidgin-otr policykit-gnome python python-apport python-apt
  python-brlapi python-cairo python-central python-compizconfig python-crypto
  python-cups python-dbus python-dev python-gconf python-gdata python-gdbm
  python-glade2 python-gmenu python-gnome2 python-gnome2-desktop
  python-gnome2-extras python-gnomecanvas python-gnupginterface python-gobject
  python-gobject-dev python-gst0.10 python-gtk2 python-gtk2-dev
  python-gtkhtml2 python-gtksourceview2 python-imaging python-launchpad-bugs
  python-launchpad-integration python-libxml2 python-notify python-numeric
  python-problem-report python-pyatspi python-pyorbit python-sexy
  python-software-properties python-support python-uno python-virtkey
  python-vte python-xdg revelation rhythmbox sbackup seahorse
  software-properties-gtk sound-juicer system-config-printer-common
  system-config-printer-gnome tomboy totem totem-common totem-gstreamer
  totem-mozilla totem-plugins tracker-search-tool tsclient ubufox
  ubuntu-desktop ubuntu-docs ubuntu-minimal ubuntu-standard ufraw ufw
  unattended-upgrades update-manager update-manager-core update-notifier
  vinagre vino xulrunner-1.9-gnome-support yelp
```

removing it can't be recommended to say the least.

---

### Post by zaussome on 2008-05-07
I don't see what bad could happen from removing it other than the obvious fact that some applications might be written in it. I don't see them including it by default and not including PHP, Ruby etc unless a packaged application was written in Python.

---

### Post by piratesmack on 2008-05-07
why would you want to get rid of python? it's so fun

```

steven@steven-desktop:~$ python
Python 2.5.2 (r252:60911, Apr 21 2008, 11:17:30) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print 'hey sexy'
hey sexy
>>> print 'haha python, you so funny'
haha python, you so funny
>>> x=4
>>> y=5
>>> z=7
>>> print x+y-z
2
>>> print 'you so smart, python'
you so smart, python
>>> 

```

---

### Post by Sealbhach on 2008-05-07
Yeah, it did just that so I'm downloading a fresh ISO, lost the other disk I had. You live and learn.:)

I won't be doing that again.


> **quelx said:**
> Try it in Synaptic, search for Python and remove it, you will see a huge list of applications that have python as their dependency.  It is likely most if not all of them will break, rendering your system mostly useless.

```
$ sudo apt-get remove python
The following packages will be REMOVED:
alacarte alsa-utils apport apport-gtk apturl avant-window-navigator
  awn-manager blender bluez-gnome brasero bug-buddy capplets-data
  command-not-found compiz compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compiz-gnome compizconfig-settings-manager
  contact-lookup-applet deskbar-applet displayconfig-gtk ekiga eog evince
  evolution evolution-data-server evolution-exchange evolution-plugins
  evolution-webcal f-spot fast-user-switch-applet file-roller
  firefox-3.0-gnome-support firefox-gnome-support foomatic-db-hpijs gcalctool
  gconf-editor gconf2 gdebi gdebi-core gdm gedit gimp-gnomevfs gimp-python
  gksu gnome-app-install gnome-applets gnome-applets-data gnome-control-center
  gnome-doc-utils gnome-games gnome-games-data gnome-keyring gnome-media
  gnome-media-common gnome-menus gnome-mount gnome-netstatus-applet gnome-orca
  gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits
  gnome-power-manager gnome-raw-thumbnailer gnome-screensaver gnome-session
  gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils
  gnome-volume-manager gstreamer0.10-gnomevfs gstreamer0.10-plugins-good
  gtkhtml3.14 guidance-backends hal-cups-utils hpijs hplip hwtest hwtest-gtk
  jockey-common jockey-gtk language-selector language-selector-common
  launchpad-integration libawn0 libbonoboui2-0 libbonoboui2-dev libcamel1.2-11
  libdeskbar-tracker libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libexchange-storage1.2-3
  libgail-gnome-module libgconf2-dev libgdl-1-0 libgdl-gnome-1-0 libgksu2-0
  libglade2-dev libgnome-desktop-2 libgnome-media0 libgnome-vfs2.0-cil
  libgnome-window-settings1 libgnome2-0 libgnome2-common libgnome2-dev
  libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomekbd-common
  libgnomekbd2 libgnomekbdui2 libgnomeui-0 libgnomeui-dev libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-dev libgnomevfs2-extra
  libgtkhtml3.14-19 libgtkhtml3.16-cil libgweather-common libgweather1
  liblpint-bonobo0 libmetacity0 libpanel-applet2-0 libtotem-plparser10
  lsb-release metacity metacity-common mousetweaks nautilus nautilus-cd-burner
  nautilus-data nautilus-sendto nautilus-share network-manager-gnome
  notification-daemon onboard openoffice.org-gnome openoffice.org-writer
  pidgin pidgin-otr policykit-gnome python python-apport python-apt
  python-brlapi python-cairo python-central python-compizconfig python-crypto
  python-cups python-dbus python-dev python-gconf python-gdata python-gdbm
  python-glade2 python-gmenu python-gnome2 python-gnome2-desktop
  python-gnome2-extras python-gnomecanvas python-gnupginterface python-gobject
  python-gobject-dev python-gst0.10 python-gtk2 python-gtk2-dev
  python-gtkhtml2 python-gtksourceview2 python-imaging python-launchpad-bugs
  python-launchpad-integration python-libxml2 python-notify python-numeric
  python-problem-report python-pyatspi python-pyorbit python-sexy
  python-software-properties python-support python-uno python-virtkey
  python-vte python-xdg revelation rhythmbox sbackup seahorse
  software-properties-gtk sound-juicer system-config-printer-common
  system-config-printer-gnome tomboy totem totem-common totem-gstreamer
  totem-mozilla totem-plugins tracker-search-tool tsclient ubufox
  ubuntu-desktop ubuntu-docs ubuntu-minimal ubuntu-standard ufraw ufw
  unattended-upgrades update-manager update-manager-core update-notifier
  vinagre vino xulrunner-1.9-gnome-support yelp
```

removing it can't be recommended to say the least.

---

### Post by lamalex on 2008-05-07
Yeah, python is a huge part of the Ubuntu desktop. *Many* apps are written in python, some of the best! Why don't you like the name? Afraid of snakes?

---

### Post by Sealbhach on 2008-05-07
> **Iamalex said:**
> Yeah, python is a huge part of the Ubuntu desktop. *Many* apps are written in python, some of the best! Why don't you like the name? Afraid of snakes?


I guess I don't like how pythons kill their prey - it was a nightmare of mine to be caught by one.


.

---

### Post by Delever on 2008-05-07
Well, it just happens to remove ubuntu desktop too. Not so much fun without it :D

---

### Post by Morpholinux on 2009-03-15
well....I guess I am a bit late....

ummm I am learning about python..want to learn version 3.0 but the default in Ubuntu 8.10 (I think) it's version 2.5.x...or 2.4?

big problem...was (and its) I think that may be uninstalling v2.5.x while having installed the libs docs and all the right stuff of v3.0 would be perfectly fine...well that was not the case ..


.after uninstalling was complete a bunch of apps disappeared...though I still could move the mouse over the Desktop ..no terminal and everything else stop functioning opera, firefox, the .pfds I was reading ........then I restart and now I have no GUI....
there's a magical command to undo last things in synaptic package manager???...
or there's a way to reinstall python AND EVERYTHING THAT DEPEND ON PYTHON??
..--
thanks in advance

---

### Post by Sealbhach on 2009-03-15
When you boot up do you get a login screen? If so, log in.

If not, press Ctrl+Alt+F2 which shold bring you to a new login screen.

Log in.

Then type

```
sudo apt-get install ubuntu-desktop python
```

This should fix it for you.

.

---

### Post by snova on 2009-03-15
> **Morpholinux said:**
> ummm I am learning about python..want to learn version 3.0 but the default in Ubuntu 8.10 (I think) it's version 2.5.x...or 2.4?

The default version in Ubuntu 8.10 is 2.5, which you would be well-recommended to learn. Py3K has some nice new features, and does away with some old, deprecated things, but it is **not** ready to be widely used.

2.6 will be the default in Ubuntu 9.04, which is something like a transition version between 2.x and 3.0.

> big problem...was (and its) I think that may be uninstalling v2.5.x while having installed the libs docs and all the right stuff of v3.0 would be perfectly fine...well that was not the case ..

No. Py3K is incompatible with 2.x code. Even if you could remove 2.5 and swap 3.0 in, you'd break everything written in Python.

> .after uninstalling was complete a bunch of apps disappeared...though I still could move the mouse over the Desktop ..no terminal and everything else stop functioning opera, firefox, the .pfds I was reading ........then I restart and now I have no GUI....
there's a magical command to undo last things in synaptic package manager???...
or there's a way to reinstall python AND EVERYTHING THAT DEPEND ON PYTHON??
..--
thanks in advance

Try Sealbhach's instructions. Also, how did you install Py3K? From the repos? From source?

---

### Post by Morpholinux on 2009-03-15
Sealbhach...I just try what you suggest...

"sudo apt-get install ubuntu-desktop python"
..
reads and asks for 698Mb will be used yes or no?
I said yes

 and appears..well a lot of lines...the last ones are:->
-------------------------------------------------------
t_0.150_1ubuntu3_i386.deb Could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-0.93.34_all.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-0.93.34_all.deb) Could not resolve 'mx.archive.ubunutu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier-0.71.8_i386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier-0.71.8_i386.deb) Could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.124_386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.124_386.deb) Could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vinagre/vinagre_2.24.1-0ubuntu.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vinagre/vinagre_2.24.1-0ubuntu.1_i386.deb) Could not resolve 'security.ubuntu.com' failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/v/vino/vino_2.24.1-0ubuntu1_i386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/v/vino/vino_2.24.1-0ubuntu1_i386.deb) could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/g/gnome-pilot/gnome-pilot_2.0.15-2ubuntu4_i386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/g/gnome-pilot/gnome-pilot_2.0.15-2ubuntu4_i386.deb) Could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/g/gnome-pilot-conduits/gnome-pilot-conduits_2.0.15-1-2_i386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/g/gnome-pilot-conduits/gnome-pilot-conduits_2.0.15-1-2_i386.deb) Could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/libin/libmca/libmbca0_0.0.3~bzr42-ubuntu2.i386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/libin/libmca/libmbca0_0.0.3~bzr42-ubuntu2.i386.deb) Could not resolve 'mx.archive.ubuntu.com' E:unable to fetch some archives, maybe run apt-get update or try with--fix-missing?
-----------------------------------------------------

(well maybe are a few mistakes...but..I hope this can help)..

and to

snova...
i did all the install and uninstall from spm...
but got problems when tryin' to install for example IDLE 3.0


HOPE IS THE LAST THING THAT DIES...


thanks..

---

### Post by Sealbhach on 2009-03-15
> **Morpholinux said:**
> Sealbhach...I just try what you suggest...

"sudo apt-get install ubuntu-desktop python"
..
reads and asks for 698Mb will be used yes or no?
I said yes

 and appears..well a lot of lines...the last ones are:->
-------------------------------------------------------
t_0.150_1ubuntu3_i386.deb Could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-0.93.34_all.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-0.93.34_all.deb) Could not resolve 'mx.archive.ubunutu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier-0.71.8_i386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier-0.71.8_i386.deb) Could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.124_386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.124_386.deb) Could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vinagre/vinagre_2.24.1-0ubuntu.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vinagre/vinagre_2.24.1-0ubuntu.1_i386.deb) Could not resolve 'security.ubuntu.com' failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/v/vino/vino_2.24.1-0ubuntu1_i386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/v/vino/vino_2.24.1-0ubuntu1_i386.deb) could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/g/gnome-pilot/gnome-pilot_2.0.15-2ubuntu4_i386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/g/gnome-pilot/gnome-pilot_2.0.15-2ubuntu4_i386.deb) Could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/g/gnome-pilot-conduits/gnome-pilot-conduits_2.0.15-1-2_i386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/g/gnome-pilot-conduits/gnome-pilot-conduits_2.0.15-1-2_i386.deb) Could not resolve 'mx.archive.ubuntu.com' Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/main/libin/libmca/libmbca0_0.0.3~bzr42-ubuntu2.i386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/main/libin/libmca/libmbca0_0.0.3~bzr42-ubuntu2.i386.deb) Could not resolve 'mx.archive.ubuntu.com' E:unable to fetch some archives, maybe run apt-get update or try with--fix-missing?
-----------------------------------------------------
.


Hi, try all these commands first:

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove
```

Then try:

```
sudo apt-get install ubuntu-desktop python
```


.

---

### Post by Morpholinux on 2009-03-16
hi Sealbhach..
Try whay U said...
umm   (still dunno how to put what u said in gray background..)

1:- sudo dpkg --configure -a
2:- sudo apt-get -f install
3:- sudo apt-get --fix-missing install
4:- sudo apt-get clean all
5:- sudo apt-get update
6:- sudo apt-get upgrade
7:- sudo apt-get dist-upgrade
8:- sudo apt-get clean all
9:- sudo apt-get autoremove
10:- sudo apt-get install ubuntu-desktop python


1 nothing happened
2 o upgrade 0 newly installed 0 to remove...
3 same as 2
4 nothin'
5 
W: Failed to fetch [http://archive.canonical.com/ubuntu/dist/intrepid/Release.gpg](http://archive.canonical.com/ubuntu/dist/intrepid/Release.gpg) Could not resolve 'archive.canonical.com'
W: Failed to fetch [http://archive.canonical.com/ubuntu/dist/intrepid/partner/i8n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dist/intrepid/partner/i8n/Translation-en_US.bz2) Could not resolve 'archive.canonical.com' 
W: Failed to fetch [http://archive.canonical.com/ubuntu/dist/intrepid/security/Release.gpg](http://archive.canonical.com/ubuntu/dist/intrepid/security/Release.gpg) Could not resolve 'security.ubuntu.com' 
W: Failed to fetch [http://archive.canonical.com/ubuntu/dist/intrepid-security/main/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dist/intrepid-security/main/i18n/Translation-en_US.bz2) Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dist/intrepid.security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dist/intrepid.security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release.gpg](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release.gpg) Could not resolve 'ppa.launchpad.net'
W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2) Could not resolve 'ppa.launchpad.net'
W: Some index files failed to download they have been ignored or old ones used instead
W:tou may want to run apt'get to correct these problems

6,7,8,9,10 sometimes nothing..sometimes same as 2...
..
...
...
really thanks for helping...

---

### Post by Torkiliuz on 2009-03-16
try sudo dpkg --reconfigure -a, instead of sudo dpkg --configure -a...:)

---

### Post by Morpholinux on 2009-03-16
do not recognise --reconfigure...
a list of available options appears..
(like V version...h help..etc)
.
thanks Torkiliuz

---

### Post by Tony Flury on 2009-03-16
> **Morpholinux said:**
> hi Sealbhach..
Try whay U said...
umm   (still dunno how to put what u said in gray background..)

1:- sudo dpkg --configure -a
2:- sudo apt-get -f install
3:- sudo apt-get --fix-missing install
4:- sudo apt-get clean all
5:- sudo apt-get update
6:- sudo apt-get upgrade
7:- sudo apt-get dist-upgrade
8:- sudo apt-get clean all
9:- sudo apt-get autoremove
10:- sudo apt-get install ubuntu-desktop python


1 nothing happened
2 o upgrade 0 newly installed 0 to remove...
3 same as 2
4 nothin'
5 
W: Failed to fetch [http://archive.canonical.com/ubuntu/dist/intrepid/Release.gpg](http://archive.canonical.com/ubuntu/dist/intrepid/Release.gpg) Could not resolve 'archive.canonical.com'
W: Failed to fetch [http://archive.canonical.com/ubuntu/dist/intrepid/partner/i8n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dist/intrepid/partner/i8n/Translation-en_US.bz2) Could not resolve 'archive.canonical.com' 
W: Failed to fetch [http://archive.canonical.com/ubuntu/dist/intrepid/security/Release.gpg](http://archive.canonical.com/ubuntu/dist/intrepid/security/Release.gpg) Could not resolve 'security.ubuntu.com' 
W: Failed to fetch [http://archive.canonical.com/ubuntu/dist/intrepid-security/main/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dist/intrepid-security/main/i18n/Translation-en_US.bz2) Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dist/intrepid.security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dist/intrepid.security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release.gpg](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release.gpg) Could not resolve 'ppa.launchpad.net'
W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2) Could not resolve 'ppa.launchpad.net'
W: Some index files failed to download they have been ignored or old ones used instead
W:tou may want to run apt'get to correct these problems

6,7,8,9,10 sometimes nothing..sometimes same as 2...
..
...
...
really thanks for helping...

These errors look like you are not actually online, so you wont be able to download the packages.

---

### Post by orethrius on 2009-03-16
> **Tony Flury said:**
> These errors look like you are not actually online, so you wont be able to download the packages.
You noticed that, too?  Here's something to try (hold Alt and hit F2 to bring up the Run prompt, then do this):

```
xterm -e 'ifconfig > ~/Desktop/lanconn.log'
```

Please post the contents of the lanconn.log file just created on your desktop.

---

### Post by Morpholinux on 2009-03-16
hi everybody..
.ahmmm yup...
I was thinking the same as Tony...
ammm somebody told me to install lynx...but i dunno how to do it and how to manage it....besides...my computer is a sony vaio vgn-nr220fe....few months ago with Hardy heron I had problems with my wireless card LAN Express AS IEEE 802.11g PCI-E Adapter..so I have to uninstall and install Intrepid and do some of my first commands to have at that time internet wireless..thing is...at the blankscreen no GUI, no apps...no python ( I think maybe I have python a minimal version) can I have internet wireless ???how?
..thanks to everybody...

ps sorry if i didnt realize before about the internet...
ps 2.....internet at home is free of password ..

---

### Post by orethrius on 2009-03-16
Okay, what is displayed if you open a Terminal and type in:
```
ifconfig | grep "inet addr"
```

(The | is the bar achieved by holding Shift and hitting backslash '\' on a QWERTY keyboard; ignore the 127.0.0.1 line, the important part here is that you get a result *besides* that one.)

From the sounds of what you're describing (no GUI, that is to say CLI only) you can just directly type that code at the top of this post.

---

### Post by Tony Flury on 2009-03-16
Can't help thinking that a complete re-install is the way to go here.

I do hope you backed up everything of value (or you have a seperate /home partition).

---

### Post by orethrius on 2009-03-16
> **Tony Flury said:**
> Can't help thinking that a complete re-install is the way to go here.

I do hope you backed up everything of value (or you have a seperate /home partition).
Yeah, but if we can get that system back up, he won't *have* to worry about the logistics of offloading any files not on a separate partition. :)

---

### Post by 3rdalbum on 2009-03-16
Plug your ADSL router into your computer through an Ethernet cable. The Network Manager program that connects your wireless card runs on Python.

---

### Post by orethrius on 2009-03-16
...or iwconfig might work...

---

### Post by billgoldberg on 2009-03-16
Don't remove python.

You can do so, but a ******** of programs won't work any more.

---

### Post by Morpholinux on 2009-03-16
once again :D HI everybody !!....

I do what 3rdalbum comment...
then follow Sealhbach instructions...
and after some 20 minutes...I am at my ubuntu desktop....
everything seems to be working just fine...internet wireless, spm, allgnome...my programs installed and all
thanks...its so nice having great help.. 
..

---

### Post by Simi23 on 2009-11-06
Hi, I just like to add thanks, this forum helped me with my problem ;) I have older computer as a file and web server with Ubuntu 9.10 and I always had a problem with CPU usage (60% all the time) since ver. 8.10 ... and now since I reinstall Python (with your guys help) CPU dropped to 2-5% when idle ;-) ... don't know why but it works, so thank you, ... Ubuntu rocks  :guitar:

---

### Post by LostAndDelerious on 2010-10-24
Try this..

[http://shibuvarkala.blogspot.com/2008/08/connect-to-wireless-lan-in-ubuntu.html](http://shibuvarkala.blogspot.com/2008/08/connect-to-wireless-lan-in-ubuntu.html)

if you need a key replace the line

sudo iwconfig wlan0 essid "ESSID_IN_QUOTES"
with
sudo iwconfig wlan0 essid "ESSID_IN_QUOTES" key "KEY_IN_QUOTES"

that should get you networking and you can reinstall ubuntu-desktop from there..

Good Luck!
:P

---

### Post by kako13 on 2010-12-05
Oh many thanks! My girlfriend deleted python from her Laptop...

---

### Post by Sef on 2010-12-05
Necromancing. Locked.

---

