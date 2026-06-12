---
title: "Unmet Dependencies while intsalling python3.2"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by touches on 2012-10-24
I had 2 versions of python (i.e) python 2.7 installed by the OS and python 3.2 which i installed from the python site. The python 3.2 version somehow caused problems with modules and following suggestion posted here about installing python 3.2 from the Ubuntu repo's i removed python 3.2.

Now when i do a 
```
sudo apt-get install python3.2
```I get the following unmet dependenncies
```

The following packages have unmet dependencies:
 apt-xapian-index : Depends: python (< 2.8) but 3.2-1 is to be installed
 apturl : Depends: python (< 2.8) but 3.2-1 is to be installed
 apturl-common : Depends: python (< 2.8) but 3.2-1 is to be installed
 checkbox : Depends: python (< 2.8) but 3.2-1 is to be installed
 command-not-found : Depends: python (< 2.8) but 3.2-1 is to be installed
 duplicity : Depends: python (< 2.8) but 3.2-1 is to be installed
 gnome-codec-install : Depends: python (< 2.8) but 3.2-1 is to be installed
 gnome-orca : Depends: python (< 2.8) but 3.2-1 is to be installed
 gnome-sudoku : Depends: python (< 2.8) but 3.2-1 is to be installed
 hplip : Depends: python (< 2.8) but 3.2-1 is to be installed
 jockey-common : Depends: python (< 2.8) but 3.2-1 is to be installed
 language-selector-common : Depends: python (< 2.8) but 3.2-1 is to be installed
 language-selector-gnome : Depends: python (< 2.8) but 3.2-1 is to be installed
 lsb-release : Depends: python (< 2.8) but 3.2-1 is to be installed
 nvidia-common : Depends: python (< 2.8) but 3.2-1 is to be installed
 onboard : Depends: python (< 2.8) but 3.2-1 is to be installed
 oneconf : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-appindicator : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-apport : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-apt : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-aptdaemon : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-aptdaemon.gtk3widgets : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-aptdaemon.gtkwidgets : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-brlapi : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-cairo : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-chardet : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-configglue : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-crypto : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-cups : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-cupshelpers : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-dateutil : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-dbus : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-debian : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-defer : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-egenix-mxdatetime : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-egenix-mxtools : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-farsight : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-gconf : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-gdbm : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-gnomekeyring : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-gnupginterface : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-gobject : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-gobject-2 : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-gobject-cairo : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-gst0.10 : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-gtk2 : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-httplib2 : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-ibus : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-imaging : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-indicate : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-keyring : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-launchpadlib : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-lazr.restfulclient : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-lazr.uri : Breaks: python (>= 2.8) but 3.2-1 is to be installed
 python-libproxy : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-libxml2 : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-louis : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-notify : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-numpy : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-oauth : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-openssl : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-pam : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-papyon : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-pexpect : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-piston-mini-client : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-pkg-resources : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-problem-report : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-protobuf : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-pyatspi2 : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-pycurl : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-pygame : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-pyinotify : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-serial : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-simplejson : Breaks: python (>= 2.8) but 3.2-1 is to be installed
 python-smbc : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-software-properties : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-speechd : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-telepathy : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-twisted-bin : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-twisted-core : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-twisted-names : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-twisted-web : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-ubuntuone-client : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-ubuntuone-control-panel : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-ubuntuone-storageprotocol : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-uno : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-virtkey : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-vte : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-wadllib : Breaks: python (>= 2.8) but 3.2-1 is to be installed
 python-webkit : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-wnck : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-xapian : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-xdg : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-xkit : Depends: python (< 2.8) but 3.2-1 is to be installed
 python-zope.interface : Depends: python (< 2.8) but 3.2-1 is to be installed
 python3.2 : Depends: python3.2-minimal (= 3.2.2-0ubuntu1.1) but it is not going to be installed
 sessioninstaller : Depends: python (< 2.8) but 3.2-1 is to be installed
 software-properties-common : Depends: python (< 2.8) but 3.2-1 is to be installed
 software-properties-gtk : Depends: python (< 2.8) but 3.2-1 is to be installed
 telepathy-butterfly : Depends: python (< 2.8) but 3.2-1 is to be installed
 ubuntu-sso-client : Depends: python (< 2.8) but 3.2-1 is to be installed
 ubuntu-system-service : Depends: python (< 2.8) but 3.2-1 is to be installed
 ubuntuone-control-panel-gtk : Depends: python (< 2.8) but 3.2-1 is to be installed
 ubuntuone-couch : Depends: python (< 2.8) but 3.2-1 is to be installed
 ubuntuone-installer : Depends: python (< 2.8) but 3.2-1 is to be installed
 ufw : Depends: python (< 2.8) but 3.2-1 is to be installed
 update-manager : Depends: python (< 2.8) but 3.2-1 is to be installed
 update-manager-core : Depends: python (< 2.8) but 3.2-1 is to be installed
 usb-creator-common : Depends: python (< 2.8) but 3.2-1 is to be installed
 usb-creator-gtk : Depends: python (< 2.8) but 3.2-1 is to be installed
 xdiagnose : Depends: python (< 2.8) but 3.2-1 is to be installed
 zeitgeist-core : Depends: python (< 2.8) but 3.2-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```I am trying hard to learn python but with one or the other errors keep popping out. Am new to Ubuntu so anybody please help me out

---

### Post by NikTh on 2012-10-24
Hi , 

please open a terminal and post the full results of bellow command 

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```

Please put the results between the brackets **[noparse]```
Here
```[/noparse]** so can be easy to read.
Thanks

---

### Post by touches on 2012-10-24
The dependency errors got fixed after i typed the command:
```
apt-get -f install
```After this i was able to install python 3.2 without any errors

Now i am unable to import pygame in either of my python versions (i.e) python2.7 and python 3.2 when i try i get the **"Import error: No module name pygame"**
Should i start a new thread for this? I am really getting tired of trying to setup python and pygame and start learning

@NikTh

The output i get is
```
/etc/apt/sources.list

     1    #deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://in.archive.ubuntu.com/ubuntu/ oneiric main restricted
     6    deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://in.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
    11    deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://in.archive.ubuntu.com/ubuntu/ oneiric universe
    17    deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric universe
    18    deb http://in.archive.ubuntu.com/ubuntu/ oneiric-updates universe
    19    deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://in.archive.ubuntu.com/ubuntu/ oneiric multiverse
    27    deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric multiverse
    28    deb http://in.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
    29    deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://in.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
    37    deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
    41    deb http://security.ubuntu.com/ubuntu oneiric-security universe
    42    deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
    43    deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu oneiric partner
    51    # deb-src http://archive.canonical.com/ubuntu oneiric partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu oneiric main
    56    deb-src http://extras.ubuntu.com/ubuntu oneiric main

/etc/apt/sources.list.d/google-talkplugin.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb http://dl.google.com/linux/talkplugin/deb/ stable main

/etc/apt/sources.list.d/google-chrome.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb http://dl.google.com/linux/chrome/deb/ stable main

```

In this list we can comment out the deb http lines right? I had read it in one of the forum posts and it seems to be commented out. Anyways for the pygame error i think i have to start a new thread.

---

### Post by NikTh on 2012-10-24
> **touches said:**
> The dependency errors got fixed after i typed the command:
```
apt-get -f install
```After this i was able to install python 3.2 without any errors
Yes, you did well. You fixed the error with the -f switch. 
> **touches said:**
> In this list we can comment out the deb http  lines right? I had read it in one of the forum posts and it seems to be  commented out. Anyways for the pygame error i think i have to start a  new thread.

Yes you can comment out anything you don't want , but I asked for this list cuz I thought you've added an external PPA (repository) for the python and thought maybe breakage your system.

You can mark this thread as solved and open a new thread to the appropriate section for the python module error. 

Thanks

---

