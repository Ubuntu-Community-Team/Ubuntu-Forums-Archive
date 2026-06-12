---
title: "broken pipe"
date: 2011-06-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-06-11
is this just one of those things i gotta wait longer for builds and dependencies to meet?

```
sudo apt-get upgrade
[sudo] password for buzzmandt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 kdebase-workspace-bin : Depends: libkscreensaver5 (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is installed
                         Depends: libplasmagenericshell4 (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is installed
                         Depends: libprocessui4a (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is installed
                         Depends: kdebase-workspace-data (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is installed
 libplasmagenericshell4 : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is installed
 libtaskmanager4abi1 : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is installed
 plasma-desktop : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is installed
 plasma-widgets-workspace : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is installed
E: Unmet dependencies. Try using -f.

```


```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgnomekbd4 libnm-glib-vpn1 libgladeui-1-11 gstreamer0.10-packagekit libxcb-event1 libppl7 libgnome-media0 lzma linux-headers-2.6.38-8 linux-headers-2.6.39-1
  python-gtksourceview2 libevview3 evince-common linux-headers-2.6.39-1-generic linux-headers-2.6.35-28 gnome-media-common libprocesscore4b libgweather1 libelfg0 gnome-about
  libgtksourceview2.0-common libppl-c2 libkpathsea5 libt1-5 libgtksourceview2.0-0 libevdocument3 linux-headers-2.6.35-28-generic linux-headers-2.6.38-8-generic
  indicator-applet-session libedata-cal1.2-10 libgnome-window-settings1 gnome-panel-bonobo libedata-book1.2-8 libsolidcontrolifaces4a cpp-4.5 gir1.2-panelapplet-3.0
  libpoppler-glib6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kde-window-manager kdebase-workspace-bin kdebase-workspace-kgreet-plugins kdm libkdecorations4 libkwineffects1abi1 libkworkspace4 libsolidcontrolifaces4abi1
Suggested packages:
  plasma-scriptengines
The following packages will be REMOVED:
  libpowerdevilcore0 libtaskmanager4b
The following NEW packages will be installed:
  libkwineffects1abi1 libsolidcontrolifaces4abi1
The following packages will be upgraded:
  kde-window-manager kdebase-workspace-bin kdebase-workspace-kgreet-plugins kdm libkdecorations4 libkworkspace4
6 upgraded, 2 newly installed, 2 to remove and 169 not upgraded.
194 not fully installed or removed.
Need to get 0 B/5,120 kB of archives.                                                                                                                                               
After this operation, 1,864 kB of additional disk space will be used.                                                                                                               
Do you want to continue [Y/n]? y                                                                                                                                                    
Preconfiguring packages ...                                                                                                                                                         
(Reading database ... 253314 files and directories currently installed.)                                                                                                            
Preparing to replace kdebase-workspace-bin 4:4.6.2a-0ubuntu5.1 (using .../kdebase-workspace-bin_4%3a4.6.3-1ubuntu3_i386.deb) ...                                                    
Unpacking replacement kdebase-workspace-bin ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.6.3-1ubuntu3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libpowerdevilcore.so.0.1.0', which is also in package libpowerdevilcore0 4:4.6.2a-0ubuntu5.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.6.3-1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


```
 sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  libpowerdevilcore0 libtaskmanager4b
The following NEW packages will be installed:
  libkwineffects1abi1 libsolidcontrolifaces4abi1
The following packages have been kept back:
  aptdaemon banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-main empathy empathy-common
  gnome-bluetooth gnome-orca gnupg-agent gnupg2 gpgsm grub-common grub-pc ktorrent ktorrent-data kubuntu-konqueror-shortcuts language-selector-common language-selector-gnome
  language-selector-kde libcompizconfig0 libdecoration0 libktorrent-l10n libmono-corlib2.0-cil libmono-posix2.0-cil libmono-system2.0-cil libnotify0.4-cil libtunepimp5
  libwww-perl linux-generic linux-headers-generic linux-image-generic lsb-release mono-2.0-gac mono-csharp-shell mono-gac mono-gmcs mono-runtime nautilus-sendto-empathy
  protobuf-compiler python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-gconf python-glade2 python-gnome2 python-gtk2
  python-protobuf totem totem-common totem-mozilla totem-plugins unity unity-common vinagre yelp
The following packages will be upgraded:
  apport apport-gtk apport-kde apt apt-transport-https apt-utils apt-xapian-index aptdaemon-data bsdmainutils busybox-initramfs busybox-static cli-common command-not-found
  command-not-found-data cups cups-bsd cups-client cups-common cups-ppdc dictionaries-common dosfstools eog evince-common evolution-plugins fakeroot firefox firefox-globalmenu
  firefox-gnome-support foo2zjs gbrainy gconf-defaults-service gnome-codec-install gnome-session gnome-session-bin gnome-session-common gucharmap hpijs hplip hplip-cups
  hplip-data initscripts kde-window-manager kdebase-workspace kdebase-workspace-bin kdebase-workspace-kgreet-plugins kdm kinfocenter klipper konsole launchpad-integration
  libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libfaac0 libgnomevfs2-0 libgnomevfs2-common libgucharmap7 libhpmud0 libkdecorations4 libkworkspace4
  liblaunchpad-integration1 liblaunchpad-integration1.0-cil liblouis-data liblouis2 libmono-cairo2.0-cil libmono-i18n-west2.0-cil libmono-management2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libnm-glib-vpn1 libsane-hpaio libv4l-0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libxcb-xv0 linux-libc-dev modemmanager
  module-init-tools mountall multiarch-support network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome notification-daemon pitivi
  plasma-dataengines-addons plasma-widgets-addons procps python-apport python-launchpad-integration python-louis python-problem-report python-software-properties python-webkit
  sessioninstaller software-properties-gtk software-properties-kde systemsettings sysv-rc sysvinit-utils ubuntu-minimal ubuntu-standard update-manager update-manager-core
  update-manager-kde update-notifier update-notifier-common xscreensaver-data xscreensaver-gl xserver-xorg-input-synaptics zip
114 upgraded, 2 newly installed, 2 to remove and 61 not upgraded.
194 not fully installed or removed.
Need to get 0 B/62.4 MB of archives.
After this operation, 10.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 253314 files and directories currently installed.)
Preparing to replace kdebase-workspace-bin 4:4.6.2a-0ubuntu5.1 (using .../kdebase-workspace-bin_4%3a4.6.3-1ubuntu3_i386.deb) ...
Unpacking replacement kdebase-workspace-bin ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.6.3-1ubuntu3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libpowerdevilcore.so.0.1.0', which is also in package libpowerdevilcore0 4:4.6.2a-0ubuntu5.1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.6.3-1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by 23dornot23d on 2011-06-11
I have not tried it on my 32 bit version yet ..... but on the 64 bit using 

**aptitude safe-upgrade**

I got a similar report back but aptitude seems to deal with it a bit better and it
gave me enough options to get by this similar problem and install everything ok.

[IMG]http://img18.imageshack.us/img18/5936/kdebase.jpg[/IMG]

Will have a look at the 32 bit version later today ..... but seems like the same
packages were mentioned on my upgrade.

---

### Post by buzzmandt on 2011-06-11
thanks, tried to install aptitude, it's borked too
```
sudo apt-get install aptitude
[sudo] password for buzzmandt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude : Depends: libboost-iostreams1.42.0 (>= 1.42.0-1) but it is not going to be installed
            Depends: libcwidget3 but it is not going to be installed
 kdebase-workspace-bin : Depends: libkscreensaver5 (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
                         Depends: libplasmagenericshell4 (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
                         Depends: libprocessui4a (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
                         Depends: kdebase-workspace-data (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
 libplasmagenericshell4 : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
 libtaskmanager4abi1 : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
 plasma-desktop : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
 plasma-widgets-workspace : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by 23dornot23d on 2011-06-11
( One reason I run aptitude all the time .... have never borked my dependencies using it )

Have you tried this first ...... ( to try to fix it from apt ) .... if so what was the output ....

apt-get -f install

---

### Post by buzzmandt on 2011-06-11
> **23dornot23d said:**
> ( One reason I run aptitude all the time .... have never borked my dependencies using it )

Have you tried this first ...... ( to try to fix it from apt ) .... if so what was the output ....

apt-get -f install

in the OP, second code box
Reposted here:
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgnomekbd4 libnm-glib-vpn1 libgladeui-1-11 gstreamer0.10-packagekit libxcb-event1 libppl7 libgnome-media0 lzma linux-headers-2.6.38-8 linux-headers-2.6.39-1
  python-gtksourceview2 libevview3 evince-common linux-headers-2.6.39-1-generic linux-headers-2.6.35-28 gnome-media-common libprocesscore4b libgweather1 libelfg0 gnome-about
  libgtksourceview2.0-common libppl-c2 libkpathsea5 libt1-5 libgtksourceview2.0-0 libevdocument3 linux-headers-2.6.35-28-generic linux-headers-2.6.38-8-generic
  indicator-applet-session libedata-cal1.2-10 libgnome-window-settings1 gnome-panel-bonobo libedata-book1.2-8 libsolidcontrolifaces4a cpp-4.5 gir1.2-panelapplet-3.0
  libpoppler-glib6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kde-window-manager kdebase-workspace-bin kdebase-workspace-kgreet-plugins kdm libkdecorations4 libkwineffects1abi1 libkworkspace4 libsolidcontrolifaces4abi1
Suggested packages:
  plasma-scriptengines
The following packages will be REMOVED:
  libpowerdevilcore0 libtaskmanager4b
The following NEW packages will be installed:
  libkwineffects1abi1 libsolidcontrolifaces4abi1
The following packages will be upgraded:
  kde-window-manager kdebase-workspace-bin kdebase-workspace-kgreet-plugins kdm libkdecorations4 libkworkspace4
6 upgraded, 2 newly installed, 2 to remove and 169 not upgraded.
194 not fully installed or removed.
Need to get 0 B/5,120 kB of archives.                                                                                                                                               
After this operation, 1,864 kB of additional disk space will be used.                                                                                                               
Do you want to continue [Y/n]? y                                                                                                                                                    
Preconfiguring packages ...                                                                                                                                                         
(Reading database ... 253314 files and directories currently installed.)                                                                                                            
Preparing to replace kdebase-workspace-bin 4:4.6.2a-0ubuntu5.1 (using .../kdebase-workspace-bin_4%3a4.6.3-1ubuntu3_i386.deb) ...                                                    
Unpacking replacement kdebase-workspace-bin ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.6.3-1ubuntu3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libpowerdevilcore.so.0.1.0', which is also in package libpowerdevilcore0 4:4.6.2a-0ubuntu5.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.6.3-1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by 23dornot23d on 2011-06-11
If this is just your test system I would try this ..... 

apt-get remove libpowerdevilcore0


as its failing on

trying to overwrite '/usr/lib/libpowerdevilcore.so.0.1.0' and then try it again ..... 

and it wants to remove this anyway ...... (reading the start of the apt-get sequence).
**The following packages will be REMOVED:   libpowerdevilcore0 libtaskmanager4b**


Check that it adds it back in after the install too ..... only advice I can give at the moment 
to solve it.

---

### Post by buzzmandt on 2011-06-11
wow, this really is a catch 22.

```
sudo apt-get remove libpowerdevilcore0
[sudo] password for buzzmandt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kdebase-workspace-bin : Depends: libkscreensaver5 (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
                         Depends: libplasmagenericshell4 (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
                         Depends: libpowerdevilcore0 (= 4:4.6.2a-0ubuntu5.1) but it is not going to be installed
                         Depends: libprocessui4a (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
                         Depends: kdebase-workspace-data (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
 libplasmagenericshell4 : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
 libtaskmanager4abi1 : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
 plasma-desktop : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
 plasma-widgets-workspace : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```
sudo apt-get remove libpowerdevilcore0 -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kdebase-workspace-bin : Depends: libkscreensaver5 (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
                         Depends: libplasmagenericshell4 (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
                         Depends: libpowerdevilcore0 (= 4:4.6.2a-0ubuntu5.1) but it is not going to be installed
                         Depends: libprocessui4a (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
                         Depends: kdebase-workspace-data (= 4:4.6.2a-0ubuntu5.1) but 4:4.6.3-1ubuntu3 is to be installed
 libplasmagenericshell4 : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
 libtaskmanager4abi1 : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
 plasma-desktop : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
 plasma-widgets-workspace : Depends: libkworkspace4 (= 4:4.6.3-1ubuntu3) but 4:4.6.2a-0ubuntu5.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by 23dornot23d on 2011-06-11
Yep its a dependency nightmare and it can get a lot worse before it gets better .....

sometimes easier to bite the bullet re-install ..... and next time use **aptitude safe-upgrade**

Trust me it does all the hard work for you .........

___________________________________

I have done this before ...... today ..... but I run 2 or 3 desktops alongside one another
and can always get back into one of them

apt-get remove kde-full
apt-get install aptitude
aptitude update
aptitude install kde-full
aptitude safe-upgrade

---

### Post by seeker5528 on 2011-06-11
If you still need to get rid of these packages libpowerdevilcore0, libtaskmanager4b, use dpkg....

```
sudo dpkg --purge --force-depends libpowerdevilcore0 libtaskmanager4b
```

Then try 'apt-get -f install' again.

Sometimes it may be necessary to clean older packages that are not currently available in the repositories out of the cache```
sudo apt-get autoclean
``` then use dpkg to install from the cache directory. ```
sudo dpkg -i /var/cache/apt/archives/*.deb
```

Or if there is still a lot of stuff in the cache you can always make a list of the packages you think you need, then specify those, probably easier in this case.

The ones you need should be the ones from this list from the second code box of your first post ```
The following extra packages will be installed:
  kde-window-manager kdebase-workspace-bin kdebase-workspace-kgreet-plugins kdm libkdecorations4 libkwineffects1abi1 libkworkspace4 libsolidcontrolifaces4abi1
```

dpkg needs the full file names so if you cd to the apt cache directory then copy the list and paste it in at the command line 

```
cd /var/cache/apt/archives
sudo dpkg -i kde-window-manager kdebase-workspace-bin kdebase-workspace-kgreet-plugins kdm libkdecorations4 libkwineffects1abi1 libkworkspace4 libsolidcontrolifaces4abi1
```

Then before you hit 'Enter' on the dpkg command, for each package name if you position the cursor at the end of the package name, then hit the 'Tab' key, it should fill in the rest of the file name. If you get complaints about additional packages being needed, assuming they were previously downloaded and in the cache, hit the up arrow and add that package to the list. 

Later, Seeker

---

### Post by buzzmandt on 2011-06-11
> **seeker5528 said:**
> If you still need to get rid of these packages libpowerdevilcore0, libtaskmanager4b, use dpkg....

```
sudo dpkg --purge --force-depends libpowerdevilcore0 libtaskmanager4b
```

Then try 'apt-get -f install' again.


Thanks seeker, that did it, apt-get -f install worked and fixed the rest, updating as normal now.

---

### Post by ranch hand on 2011-06-11
You may want to have this.  It is a very handy doc to give you some real basic commands and a good place to start from in learning more.  It should be in the repo with several different formats for the same document.

Your pdf reader should (does under Debian) read this as is.  You may have to extract it.  I use it this way just fine.

---

### Post by buzzmandt on 2011-06-11
Thanks ranch hand.  very nice

---

### Post by ronacc on 2011-06-11
if thats not already in tutorials&tips it should be .

---

### Post by ranch hand on 2011-06-11
Well it is in the repo here so I suspect it is in the repo for Ubuntu.   I see no reason why it would not be.

"apt-dpkg-ref" is what it is called here and I suppose it would be there too.

 I never looked for it.  Have to have my son (moved here recently) look on his box.  I am sure he is running 10.10.

I really am an idiot.  I just went and checked the wifes box (10.04).  It is in there.

---

### Post by ronacc on 2011-06-11
Yes I checked 10.10 on my "work" box , its there.

---

