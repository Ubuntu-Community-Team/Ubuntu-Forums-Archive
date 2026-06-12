---
title: "problem with python in hardy"
date: 2008-05-02
forum: Programming Talk
---

### Post by keisangi on 2008-05-02
i have a problem with python in hardy, i cannot import random, 
i get an exception about "randint" tat cannot be imported..
(i'm beginning python.. be kind)
why do i get an exception about randint ?
please have a look at the following:

```

keisangi@kanzume:~/TEMPO/bpwpapcode/Chapter04$ python
Python 2.5.2 (r252:60911, Apr 21 2008, 11:12:42) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import random
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/random.py", line 4, in <module>
    --------
ImportError: cannot import name randint
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 37, in apport_excepthook
    import re, tempfile, traceback
  File "/usr/lib/python2.5/tempfile.py", line 33, in <module>
    from random import Random as _Random
  File "/usr/lib/python2.5/random.py", line 4, in <module>
    --------
ImportError: cannot import name randint

Original exception was:
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/random.py", line 4, in <module>
    --------
ImportError: cannot import name randint
>>> 

```

---

### Post by samjh on 2008-05-02
How very strange!

"import random" works fine on my Hardy installation.  Perhaps your Python installation is broken.  Try re-installing it.```
sudo apt-get purge python2.5 && sudo apt-get install python2.5
```

---

### Post by keisangi on 2008-05-02
> **samjh said:**
> How very strange!

"import random" works fine on my Hardy installation.  Perhaps your Python installation is broken.  Try re-installing it.```
sudo apt-get purge python2.5 && sudo apt-get install python2.5
```

i'm not sure this is a good idea ;)

looking at what it want to remove, it seems it will uninstall almost everything:

```

keisangi@kanzume:~$ sudo apt-get purge python2.5 && sudo apt-get install python2.5
[sudo] password for keisangi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-x libxine1-misc-plugins libxcb-xv0 libxine1-bin libxine1-ffmpeg libsdl-ttf2.0-0 libgnomecanvasmm-2.6-1c2a libxcb-shape0 tcl8.4 libsdl-mixer1.2 libxine1-plugins
  libmodplug0c2 libgconfmm-2.6-1c2 libxcb-shm0 libglademm-2.4-1c2a libsdl-image1.2 libxine1-console libxine1 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alacarte* alsa-utils* apport* apport-gtk* apturl* bluez-gnome* brasero* bug-buddy* capplets-data* command-not-found* compiz* compiz-fusion-plugins-extra*
  compiz-fusion-plugins-main* compiz-gnome* compizconfig-settings-manager* contact-lookup-applet* deskbar-applet* displayconfig-gtk* ekiga* eog* evince* evolution*
  evolution-data-server* evolution-exchange* evolution-plugins* evolution-webcal* f-spot* fast-user-switch-applet* file-roller* firefox* firefox-3.0* firefox-3.0-gnome-support*
  firefox-gnome-support* foomatic-db-hpijs* fusion-icon* gcalctool* gconf-editor* gconf2* gdebi* gdebi-core* gdm* gedit* gimp-gnomevfs* gimp-python* gksu* gnome-app-install*
  gnome-applets* gnome-applets-data* gnome-control-center* gnome-doc-utils* gnome-games* gnome-games-data* gnome-keyring* gnome-media* gnome-media-common* gnome-menus*
  gnome-mount* gnome-netstatus-applet* gnome-orca* gnome-panel* gnome-panel-data* gnome-pilot* gnome-pilot-conduits* gnome-power-manager* gnome-screensaver* gnome-session*
  gnome-settings-daemon* gnome-spell* gnome-system-monitor* gnome-system-tools* gnome-terminal* gnome-terminal-data* gnome-user-guide* gnome-utils* gnome-volume-manager*
  gstreamer0.10-gnomevfs* gstreamer0.10-plugins-good* gtkhtml3.14* guidance-backends* hal-cups-utils* hardware-monitor* hpijs* hplip* hwtest* hwtest-gtk* jockey-common*
  jockey-gtk* language-selector* language-selector-common* launchpad-integration* libbonoboui2-0* libcamel1.2-11* libdeskbar-tracker* libebook1.2-9* libecal1.2-7*
  libedata-book1.2-2* libedata-cal1.2-6* libedataserverui1.2-8* libeel2-2* libexchange-storage1.2-3* libgail-gnome-module* libgksu2-0* libgnome-desktop-2* libgnome-media0*
  libgnome-vfs2.0-cil* libgnome-window-settings1* libgnome2-0* libgnome2-common* libgnome2-perl* libgnome2-vfs-perl* libgnome2.0-cil* libgnomekbd-common* libgnomekbd2*
  libgnomekbdui2* libgnomeui-0* libgnomevfs2-0* libgnomevfs2-bin* libgnomevfs2-common* libgnomevfs2-extra* libgtkhtml3.14-19* libgtkhtml3.16-cil* libgweather-common*
  libgweather1* liblpint-bonobo0* libmetacity0* libpanel-applet2-0* libtotem-plparser10* lsb-release* metacity* metacity-common* mousetweaks* nautilus* nautilus-cd-burner*
  nautilus-data* nautilus-sendto* nautilus-share* network-manager-gnome* notification-daemon* onboard* openoffice.org-gnome* openoffice.org-writer* pidgin* pidgin-otr*
  policykit-gnome* python* python-apport* python-apt* python-brlapi* python-cairo* python-central* python-compizconfig* python-cups* python-dbus* python-gconf* python-gdata*
  python-gdbm* python-glade2* python-gmenu* python-gnome2* python-gnome2-desktop* python-gnomecanvas* python-gnupginterface* python-gobject* python-gst0.10* python-gtk2*
  python-gtkhtml2* python-gtksourceview2* python-imaging* python-launchpad-bugs* python-launchpad-integration* python-libxml2* python-notify* python-numeric*
  python-problem-report* python-pyatspi* python-pygame* python-pyorbit* python-sexy* python-software-properties* python-sqlite* python-support* python-uno* python-virtkey*
  python-vte* python-xdg* python2.5* rhythmbox* seahorse* simple-ccsm* software-properties-gtk* sound-juicer* system-config-printer-common* system-config-printer-gnome* tomboy*
  totem* totem-common* totem-gstreamer* totem-mozilla* totem-plugins* totem-xine* tracker-search-tool* tsclient* ubufox* ubuntu-desktop* ubuntu-docs* ubuntu-minimal*
  ubuntu-standard* ufw* unattended-upgrades* update-manager* update-manager-core* update-notifier* vinagre* vino* xchat* xchat-common* xulrunner-1.9* xulrunner-1.9-gnome-support*
  yelp*
0 upgraded, 0 newly installed, 219 to remove and 0 not upgraded.
After this operation, 667MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
keisangi@kanzume:~$ 


```

i did tryed to mark python for reinstallation in synaptic.. it went fine .. but the problem is stll here,
it didn't solve a thing..

---

### Post by Jessehk on 2008-05-02
> 
```

ImportError: cannot import name randint

```


The module is called **random**, NOT **randint**.

EDIT: You would want the function **random.randint()**

---

### Post by samjh on 2008-05-02
[quote=keisangi]i'm not sure this is a good idea

looking at what it want to remove, it seems it will uninstall almost everything:[/quote]Oops, I'd forgotten how much depends on Python!  If re-install didn't solve the problem, I'm stumped.

[quote=Jessehk]The module is called random, NOT randint.

EDIT: You would want the function random.randint()[/quote]He's just typing in **import random** and nothing else.  So it should work without a fuss.

---

### Post by Siph0n on 2008-05-02
He is trying to import random...

> 
>>> import random
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/random.py", line 4, in <module>
    --------
ImportError: cannot import name randint


---

### Post by Jessehk on 2008-05-02
Oops. My mistake.

---

### Post by keisangi on 2008-05-03
thank you for the help
i don't know why or how but after a reboot it's working now
i can import random without errors

tnx

---

### Post by days_of_ruin on 2008-05-03
Check for any files named random in your home directory or subdirectories.They may be hidden.If that is the case
it will likely be only happening in a certain directory.

---

