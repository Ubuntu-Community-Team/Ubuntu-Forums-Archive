---
title: "Trouble Updating via the Software Updater in 14.04"
date: 2016-01-29
forum: New to Ubuntu
---

### Post by bijaydeyp on 2016-01-29
I am new to ubuntu(14.04 lts) & Linux world.I set dual boot pc with windows and made two mistakes.  1.  in update settings, I checked all updates incluiding trusty-proposed & trusty-backports.after few weeks I unchecked the two mentioned. 2.  during regular update checking,one day I run the'software updater' and found 'not all updates can be installed, run a partial update' dialog box.I clicked 'partial update'.but it was incomplete & auto-stopped . later on whenever I check for the updates,it shows that dialog box each time.even after perform a fully update it shows that.I don't know whether the pc is taking updates at all or not.how can I get rid of it? can anyone help me please?

---

### Post by oldos2er on 2016-01-29
Can you open a terminal (Ctrl-Alt-t), run the following command, and copy/paste all the output here? ```
sudo apt-get update && sudo apt-get upgrade -s
```

---

### Post by philinux on 2016-01-29
open a terminal and run,

```
sudo dpkg --configure -a
```

---

### Post by grahammechanical on 2016-01-29
The Partial Upgrade dialog gives 4 reasons why the partial upgrade is being offered. Which one applies to your system?
> 
1) A previous upgrade which did not complete
2) Problems with some of the installed software
3) Unofficial software packages not provided by Ubuntu
4) Normal changes of a pre-release versions of Ubuntu

I update daily & I see that partial upgrade dialog every time I update. And I know why. It is item #4. You see I am running the pre-release version of Ubuntu 16.04 (code name xenial xerus). I always click Continue and the update always takes place as normal.

Which of those 4 reasons is causing that dialog to appear in your case? Have you tried clicking Continue. It will most likely continue with the update as normal. I do not think that needed updates are being prevented. That is not what happens on my system.

Regards.

---

### Post by DougieFresh4U on 2016-01-30
Never run a 'partial' update!
Always best to go to terminal and run the commands that were posted above to sort out why
the 'partial' update.

---

### Post by bijaydeyp on 2016-01-31
Hi, oldos2er!    Thanksssssssss for the help
outputs are as follows...        is there anything wrong?

```
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [181 B]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,033 B]                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease [64.4 kB]             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease [64.4 kB]             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease                        
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg [933 B]                     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources [248 kB]           
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources [5,359 B]    
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources [147 kB]       
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources [147 kB]      
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources [5,161 B]   
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [663 kB]    
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [663 kB]    
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [663 kB]    
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [663 kB]    
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [335 kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.1 kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en [348 kB]   
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en [6,832 B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en [176 kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources [103 kB]         
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources [4,035 B]  
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources [33.1 kB]    
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Sources [2,357 B]  
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages [384 kB] 
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages [123 kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages [4,955 B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en [225 kB]  
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en [2,437 B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en [3,206 B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en [72.1 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [335 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US                
Fetched 2,360 kB in 27min 43s (1,418 B/s)                                      
Reading package lists... Done
[sudo] password for suvendu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0
  linux-generic-lts-utopic linux-headers-generic-lts-utopic
  linux-image-generic-lts-utopic oxideqt-codecs-extra
The following packages will be upgraded:
  apport apport-gtk apt apt-transport-https apt-utils bind9-host
  chromium-codecs-ffmpeg-extra coreutils cups cups-browsed cups-bsd
  cups-client cups-common cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ppdc cups-server-common curl dnsutils dpkg
  firefox firefox-locale-en flashplugin-installer fonts-opensymbol
  gcc-4.9-base gir1.2-gst-plugins-base-1.0 gir1.2-gtk-3.0
  gir1.2-networkmanager-1.0 gnome-desktop3-data google-chrome-stable
  grub-common grub-pc grub-pc-bin grub2-common gstreamer1.0-alsa
  gstreamer1.0-plugins-base gstreamer1.0-plugins-base-apps gstreamer1.0-x
  im-config indicator-session isc-dhcp-client isc-dhcp-common krb5-locales
  libapt-inst1.5 libapt-pkg4.12 libbind9-90 libcups2 libcupscgi1
  libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3
  libcurl3-gnutls libdns100 libdpkg-perl libffi6 libfontembed1 libgail-3-0
  libgbm1 libgcc1 libgnome-desktop-3-7 libgnutls-openssl27 libgnutls26
  libgssapi-krb5-2 libgstreamer-plugins-base1.0-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libido3-0.1-0 libisc95 libisccc90 libisccfg90 libk5crypto3
  libkrb5-3 libkrb5support0 libldb1 liblightdm-gobject-1-0 liblwres90
  libmbim-glib0 libmm-glib0 libnautilus-extension1a libnm-glib-vpn1
  libnm-glib4 libnm-util2 libnspr4 libnss3 libnss3-1d libnss3-nssdb libpng12-0
  libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0
  libpoppler-glib8 libpoppler44 libreoffice-avmedia-backend-gstreamer
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-human
  libreoffice-writer libsmbclient libsndfile1 libssl1.0.0
  libunity-control-center1 libunity-core-6.0-9 libwbclient0 libwhoopsie0
  libxml2 lightdm linux-firmware linux-libc-dev modemmanager nautilus
  nautilus-data network-manager notify-osd-icons ntpdate oneconf
  oneconf-common openssh-client openssl os-prober policykit-1 poppler-utils
  python-apt python-apt-common python-ldb python-libxml2 python-oneconf
  python-samba python3-apport python3-apt python3-oneconf
  python3-problem-report python3-software-properties python3-uno rsync
  samba-common samba-common-bin samba-libs smbclient
  software-properties-common software-properties-gtk ssh-askpass-gnome
  thunderbird thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-gb thunderbird-locale-en-us unattended-upgrades unity
  unity-control-center unity-services unity-settings-daemon uno-libs3 unzip
  ure whoopsie wpasupplicant
171 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Inst coreutils [8.21-1ubuntu5.1] (8.21-1ubuntu5.3 Ubuntu:14.04/trusty-updates [i386])
Conf coreutils (8.21-1ubuntu5.3 Ubuntu:14.04/trusty-updates [i386])
Inst dpkg [1.17.5ubuntu5.4] (1.17.5ubuntu5.5 Ubuntu:14.04/trusty-updates [i386])
Conf dpkg (1.17.5ubuntu5.5 Ubuntu:14.04/trusty-updates [i386])
Inst gcc-4.9-base [4.9.1-0ubuntu1] (4.9.3-0ubuntu4 Ubuntu:14.04/trusty-updates [i386]) [libgcc1:i386 ]
Conf gcc-4.9-base (4.9.3-0ubuntu4 Ubuntu:14.04/trusty-updates [i386]) [libgcc1:i386 ]
Inst libgcc1 [1:4.9.1-0ubuntu1] (1:4.9.3-0ubuntu4 Ubuntu:14.04/trusty-updates [i386])
Conf libgcc1 (1:4.9.3-0ubuntu4 Ubuntu:14.04/trusty-updates [i386])
Inst libapt-pkg4.12 [1.0.1ubuntu2.10] (1.0.1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Conf libapt-pkg4.12 (1.0.1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Inst apt [1.0.1ubuntu2.10] (1.0.1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Conf apt (1.0.1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Inst libapt-inst1.5 [1.0.1ubuntu2.10] (1.0.1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Inst libffi6 [3.1~rc1+r3.0.13-12] (3.1~rc1+r3.0.13-12ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libgnutls-openssl27 [2.12.23-12ubuntu2.2] (2.12.23-12ubuntu2.4 Ubuntu:14.04/trusty-updates [i386]) []
Inst libgnutls26 [2.12.23-12ubuntu2.2] (2.12.23-12ubuntu2.4 Ubuntu:14.04/trusty-updates [i386])
Inst libssl1.0.0 [1.0.1f-1ubuntu2.15] (1.0.1f-1ubuntu2.16 Ubuntu:14.04/trusty-updates [i386])
Inst ntpdate [1:4.2.6.p5+dfsg-3ubuntu2.14.04.5] (1:4.2.6.p5+dfsg-3ubuntu2.14.04.6 Ubuntu:14.04/trusty-updates [i386])
Inst libpng12-0 [1.2.50-1ubuntu2] (1.2.50-1ubuntu2.14.04.2 Ubuntu:14.04/trusty-updates [i386])
Inst libk5crypto3 [1.12+dfsg-2ubuntu5.1] (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [i386])
Inst libgssapi-krb5-2 [1.12+dfsg-2ubuntu5.1] (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkrb5-3 [1.12+dfsg-2ubuntu5.1] (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkrb5support0 [1.12+dfsg-2ubuntu5.1] (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [i386])
Inst libcurl3-gnutls [7.35.0-1ubuntu2.5] (7.35.0-1ubuntu2.6 Ubuntu:14.04/trusty-updates [i386])
Inst libpolkit-gobject-1-0 [0.105-4ubuntu2.14.04.1] (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst libxml2 [2.9.1+dfsg1-3ubuntu4.4] (2.9.1+dfsg1-3ubuntu4.7 Ubuntu:14.04/trusty-updates [i386])
Inst chromium-codecs-ffmpeg-extra [45.0.2454.101-0ubuntu0.14.04.1.1099] (48.0.2564.82-0ubuntu0.14.04.1.1108 Ubuntu:14.04/trusty-updates [i386])
Inst libcupsfilters1 [1.0.52-0ubuntu1.5] (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Inst libcupsimage2 [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst libpoppler44 [0.24.5-2ubuntu4.2] (0.24.5-2ubuntu4.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst poppler-utils [0.24.5-2ubuntu4.2] (0.24.5-2ubuntu4.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst cups-filters-core-drivers [1.0.52-0ubuntu1.5] (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst libfontembed1 [1.0.52-0ubuntu1.5] (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst cups-browsed [1.0.52-0ubuntu1.5] (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst cups-daemon [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst libcupsppdc1 [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst libcupscgi1 [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst libcupsmime1 [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst cups-core-drivers [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst cups-bsd [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst cups-client [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst libcups2 [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) [cups:i386 ]
Inst cups-server-common [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [all]) [cups:i386 ]
Inst cups [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst cups-filters [1.0.52-0ubuntu1.5] (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst cups-common [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [all])
Inst cups-ppdc [1.7.2-0ubuntu1.6] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Inst libnspr4 [2:4.10.7-0ubuntu0.14.04.1] (2:4.10.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst libnss3-1d [2:3.19.2-0ubuntu0.14.04.1] (2:3.19.2.1-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnss3-nssdb [2:3.19.2-0ubuntu0.14.04.1] (2:3.19.2.1-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [all]) []
Inst libnss3 [2:3.19.2-0ubuntu0.14.04.1] (2:3.19.2.1-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [i386])
Inst curl [7.35.0-1ubuntu2.5] (7.35.0-1ubuntu2.6 Ubuntu:14.04/trusty-updates [i386]) []
Inst libcurl3 [7.35.0-1ubuntu2.5] (7.35.0-1ubuntu2.6 Ubuntu:14.04/trusty-updates [i386])
Inst google-chrome-stable [46.0.2490.80-1] (48.0.2564.97-1 Google:1.0/stable [i386])
Inst libgtk-3-common [3.10.8-0ubuntu1.4] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [all])
Inst libgail-3-0 [3.10.8-0ubuntu1.4] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386]) []
Inst libgtk-3-0 [3.10.8-0ubuntu1.4] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386])
Inst libgbm1 [10.1.3-0ubuntu0.5] (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [i386])
Inst libgstreamer-plugins-base1.0-0 [1.2.4-1~ubuntu1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst libido3-0.1-0 [13.10.0+14.04.20140423-0ubuntu1] (13.10.0+14.04.20151021-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst python-ldb [1:1.1.16-1] (1:1.1.16-1ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libldb1 [1:1.1.16-1] (1:1.1.16-1ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libmbim-glib0 [1.6.0-2] (1.6.0-2ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libmm-glib0 [1.0.0-2ubuntu1] (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libpolkit-agent-1-0 [0.105-4ubuntu2.14.04.1] (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst libpolkit-backend-1-0 [0.105-4ubuntu2.14.04.1] (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst libpoppler-glib8 [0.24.5-2ubuntu4.2] (0.24.5-2ubuntu4.3 Ubuntu:14.04/trusty-updates [i386])
Inst libreoffice-calc [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libreoffice-gnome [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libreoffice-gtk [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libreoffice-impress [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libreoffice-writer [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libreoffice-common [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [all]) []
Inst libreoffice-pdfimport [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libreoffice-base-core [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libreoffice-math [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst python3-uno [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libreoffice-ogltrans [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst uno-libs3 [4.2.8-0ubuntu2] (4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) [ure:i386 ]
Inst ure [4.2.8-0ubuntu2] (4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libreoffice-draw [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libreoffice-core [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Inst fonts-opensymbol [2:102.6+LibO4.2.8-0ubuntu2] (2:102.6+LibO4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [all])
Inst libreoffice-style-human [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [all])
Inst libsndfile1 [1.0.25-7ubuntu2] (1.0.25-7ubuntu2.1 Ubuntu:14.04/trusty-updates [i386])
Inst libwbclient0 [2:4.1.6+dfsg-1ubuntu2.14.04.9] (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386])
Inst lightdm [1.10.5-0ubuntu1.1] (1.10.6-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst modemmanager [1.0.0-2ubuntu1] (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libnm-util2 [0.9.8.8-0ubuntu7.1] (0.9.8.8-0ubuntu7.2 Ubuntu:14.04/trusty-updates [i386])
Inst libnm-glib4 [0.9.8.8-0ubuntu7.1] (0.9.8.8-0ubuntu7.2 Ubuntu:14.04/trusty-updates [i386])
Inst wpasupplicant [2.1-0ubuntu1.3] (2.1-0ubuntu1.4 Ubuntu:14.04/trusty-updates [i386])
Inst isc-dhcp-client [4.2.4-7ubuntu12.3] (4.2.4-7ubuntu12.4 Ubuntu:14.04/trusty-updates [i386]) []
Inst isc-dhcp-common [4.2.4-7ubuntu12.3] (4.2.4-7ubuntu12.4 Ubuntu:14.04/trusty-updates [i386])
Inst policykit-1 [0.105-4ubuntu2.14.04.1] (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst network-manager [0.9.8.8-0ubuntu7.1] (0.9.8.8-0ubuntu7.2 Ubuntu:14.04/trusty-updates [i386])
Inst libsmbclient [2:4.1.6+dfsg-1ubuntu2.14.04.9] (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386]) []
Inst smbclient [2:4.1.6+dfsg-1ubuntu2.14.04.9] (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386]) []
Inst samba-common-bin [2:4.1.6+dfsg-1ubuntu2.14.04.9] (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386]) []
Inst python-samba [2:4.1.6+dfsg-1ubuntu2.14.04.9] (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386]) []
Inst samba-libs [2:4.1.6+dfsg-1ubuntu2.14.04.9] (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386]) []
Inst samba-common [2:4.1.6+dfsg-1ubuntu2.14.04.9] (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [all])
Inst apt-utils [1.0.1ubuntu2.10] (1.0.1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Inst apt-transport-https [1.0.1ubuntu2.10] (1.0.1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Inst bind9-host [1:9.9.5.dfsg-3ubuntu0.5] (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst dnsutils [1:9.9.5.dfsg-3ubuntu0.5] (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst libisc95 [1:9.9.5.dfsg-3ubuntu0.5] (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst libdns100 [1:9.9.5.dfsg-3ubuntu0.5] (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst libisccc90 [1:9.9.5.dfsg-3ubuntu0.5] (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst libisccfg90 [1:9.9.5.dfsg-3ubuntu0.5] (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst liblwres90 [1:9.9.5.dfsg-3ubuntu0.5] (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst libbind9-90 [1:9.9.5.dfsg-3ubuntu0.5] (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386])
Inst krb5-locales [1.12+dfsg-2ubuntu5.1] (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Inst openssh-client [1:6.6p1-2ubuntu2.3] (1:6.6p1-2ubuntu2.4 Ubuntu:14.04/trusty-updates [i386])
Inst openssl [1.0.1f-1ubuntu2.15] (1.0.1f-1ubuntu2.16 Ubuntu:14.04/trusty-updates [i386])
Inst python-apt-common [0.9.3.5ubuntu1] (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst python3-apt [0.9.3.5ubuntu1] (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst rsync [3.1.0-2ubuntu0.1] (3.1.0-2ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Inst grub-pc [2.02~beta2-9ubuntu1.3] (2.02~beta2-9ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst grub-pc-bin [2.02~beta2-9ubuntu1.3] (2.02~beta2-9ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst grub2-common [2.02~beta2-9ubuntu1.3] (2.02~beta2-9ubuntu1.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst grub-common [2.02~beta2-9ubuntu1.3] (2.02~beta2-9ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Inst python3-problem-report [2.14.1-0ubuntu3.18] (2.14.1-0ubuntu3.19 Ubuntu:14.04/trusty-updates [all])
Inst python3-apport [2.14.1-0ubuntu3.18] (2.14.1-0ubuntu3.19 Ubuntu:14.04/trusty-updates [all])
Inst apport [2.14.1-0ubuntu3.18] (2.14.1-0ubuntu3.19 Ubuntu:14.04/trusty-updates [all])
Inst gir1.2-gtk-3.0 [3.10.8-0ubuntu1.4] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386])
Inst apport-gtk [2.14.1-0ubuntu3.18] (2.14.1-0ubuntu3.19 Ubuntu:14.04/trusty-updates [all])
Inst firefox [41.0.2+build2-0ubuntu0.14.04.1] (44.0+build3-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst firefox-locale-en [41.0.2+build2-0ubuntu0.14.04.1] (44.0+build3-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst flashplugin-installer [11.2.202.540ubuntu0.14.04.2] (11.2.202.559ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-gst-plugins-base-1.0 [1.2.4-1~ubuntu1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-networkmanager-1.0 [0.9.8.8-0ubuntu7.1] (0.9.8.8-0ubuntu7.2 Ubuntu:14.04/trusty-updates [i386])
Inst gnome-desktop3-data [3.8.4-0ubuntu3.1] (3.8.4-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Inst gstreamer1.0-alsa [1.2.4-1~ubuntu1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst gstreamer1.0-plugins-base [1.2.4-1~ubuntu1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst gstreamer1.0-plugins-base-apps [1.2.4-1~ubuntu1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst gstreamer1.0-x [1.2.4-1~ubuntu1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst im-config [0.24-1ubuntu4.1] (0.24-1ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Inst indicator-session [12.10.5+14.04.20151008-0ubuntu1] (12.10.5+14.04.20151021.1-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst libdpkg-perl [1.17.5ubuntu5.4] (1.17.5ubuntu5.5 Ubuntu:14.04/trusty-updates [all])
Inst libgnome-desktop-3-7 [3.8.4-0ubuntu3.1] (3.8.4-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Inst libgtk-3-bin [3.10.8-0ubuntu1.4] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386])
Inst liblightdm-gobject-1-0 [1.10.5-0ubuntu1.1] (1.10.6-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst libnautilus-extension1a [1:3.10.1-0ubuntu9.9] (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [i386])
Inst libnm-glib-vpn1 [0.9.8.8-0ubuntu7.1] (0.9.8.8-0ubuntu7.2 Ubuntu:14.04/trusty-updates [i386])
Inst libreoffice-avmedia-backend-gstreamer [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Inst libreoffice-presentation-minimizer [1:4.2.8-0ubuntu2] (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [all])
Inst libunity-control-center1 [14.04.3+14.04.20140922-0ubuntu1.1] (14.04.3+14.04.20150916-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst nautilus-data [1:3.10.1-0ubuntu9.9] (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [all])
Inst unity-settings-daemon [14.04.0+14.04.20150825-0ubuntu2] (14.04.0+14.04.20151012-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst unity-control-center [14.04.3+14.04.20140922-0ubuntu1.1] (14.04.3+14.04.20150916-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst unity [7.2.5+14.04.20150603-0ubuntu1] (7.2.6+14.04.20151021-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libunity-core-6.0-9 [7.2.5+14.04.20150603-0ubuntu1] (7.2.6+14.04.20151021-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst unity-services [7.2.5+14.04.20150603-0ubuntu1] (7.2.6+14.04.20151021-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst whoopsie [0.2.24.6] (0.2.24.6ubuntu2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libwhoopsie0 [0.2.24.6] (0.2.24.6ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst linux-firmware [1.127.16] (1.127.20 Ubuntu:14.04/trusty-updates [all])
Inst linux-libc-dev [3.13.0-66.108] (3.13.0-76.120 Ubuntu:14.04/trusty-updates [i386])
Inst nautilus [1:3.10.1-0ubuntu9.9] (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [i386])
Inst notify-osd-icons [0.8+14.04.20131204-0ubuntu1] (0.8+14.04.20151016-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst os-prober [1.63ubuntu1] (1.63ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst python-apt [0.9.3.5ubuntu1] (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst python-libxml2 [2.9.1+dfsg1-3ubuntu4.4] (2.9.1+dfsg1-3ubuntu4.7 Ubuntu:14.04/trusty-updates [i386])
Inst software-properties-common [0.92.37.5] (0.92.37.7 Ubuntu:14.04/trusty-updates [all]) []
Inst software-properties-gtk [0.92.37.5] (0.92.37.7 Ubuntu:14.04/trusty-updates [all]) []
Inst unattended-upgrades [0.82.1ubuntu2.3] (0.82.1ubuntu2.4 Ubuntu:14.04/trusty-updates [all]) []
Inst python3-software-properties [0.92.37.5] (0.92.37.7 Ubuntu:14.04/trusty-updates [all])
Inst ssh-askpass-gnome [1:6.6p1-2ubuntu2.3] (1:6.6p1-2ubuntu2.4 Ubuntu:14.04/trusty-updates [i386])
Inst thunderbird-locale-en [1:38.3.0+build1-0ubuntu0.14.04.1] (1:38.5.1+build2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst thunderbird [1:38.3.0+build1-0ubuntu0.14.04.1] (1:38.5.1+build2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386]) [thunderbird-gnome-support:i386 ]
Inst thunderbird-gnome-support [1:38.3.0+build1-0ubuntu0.14.04.1] (1:38.5.1+build2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst thunderbird-locale-en-gb [1:38.3.0+build1-0ubuntu0.14.04.1] (1:38.5.1+build2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst thunderbird-locale-en-us [1:38.3.0+build1-0ubuntu0.14.04.1] (1:38.5.1+build2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst unzip [6.0-9ubuntu1.4] (6.0-9ubuntu1.5 Ubuntu:14.04/trusty-updates [i386])
Inst oneconf-common [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst python3-oneconf [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst oneconf [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst python-oneconf [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf libapt-inst1.5 (1.0.1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Conf libffi6 (3.1~rc1+r3.0.13-12ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgnutls26 (2.12.23-12ubuntu2.4 Ubuntu:14.04/trusty-updates [i386])
Conf libgnutls-openssl27 (2.12.23-12ubuntu2.4 Ubuntu:14.04/trusty-updates [i386])
Conf libssl1.0.0 (1.0.1f-1ubuntu2.16 Ubuntu:14.04/trusty-updates [i386])
Conf ntpdate (1:4.2.6.p5+dfsg-3ubuntu2.14.04.6 Ubuntu:14.04/trusty-updates [i386])
Conf libpng12-0 (1.2.50-1ubuntu2.14.04.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkrb5support0 (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [i386])
Conf libk5crypto3 (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkrb5-3 (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgssapi-krb5-2 (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [i386])
Conf libcurl3-gnutls (7.35.0-1ubuntu2.6 Ubuntu:14.04/trusty-updates [i386])
Conf libpolkit-gobject-1-0 (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf libxml2 (2.9.1+dfsg1-3ubuntu4.7 Ubuntu:14.04/trusty-updates [i386])
Conf chromium-codecs-ffmpeg-extra (48.0.2564.82-0ubuntu0.14.04.1.1108 Ubuntu:14.04/trusty-updates [i386])
Conf libcups2 (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf libcupsfilters1 (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf libcupsimage2 (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf libpoppler44 (0.24.5-2ubuntu4.3 Ubuntu:14.04/trusty-updates [i386])
Conf poppler-utils (0.24.5-2ubuntu4.3 Ubuntu:14.04/trusty-updates [i386])
Conf cups-filters-core-drivers (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf libfontembed1 (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf cups-browsed (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf libcupsmime1 (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf cups-daemon (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf libcupsppdc1 (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf libcupscgi1 (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf cups-core-drivers (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf cups-common (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [all])
Conf cups-client (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf cups-bsd (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf cups-server-common (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [all])
Conf cups-ppdc (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf cups-filters (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf cups (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf libnspr4 (2:4.10.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf libnss3 (2:3.19.2.1-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [i386])
Conf libnss3-nssdb (2:3.19.2.1-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [all])
Conf libnss3-1d (2:3.19.2.1-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [i386])
Conf libcurl3 (7.35.0-1ubuntu2.6 Ubuntu:14.04/trusty-updates [i386])
Conf curl (7.35.0-1ubuntu2.6 Ubuntu:14.04/trusty-updates [i386])
Conf google-chrome-stable (48.0.2564.97-1 Google:1.0/stable [i386])
Conf libgtk-3-common (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [all])
Conf libgtk-3-0 (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386])
Conf libgail-3-0 (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386])
Conf libgbm1 (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [i386])
Conf libgstreamer-plugins-base1.0-0 (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libido3-0.1-0 (13.10.0+14.04.20151021-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libldb1 (1:1.1.16-1ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf python-ldb (1:1.1.16-1ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmbim-glib0 (1.6.0-2ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmm-glib0 (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libpolkit-agent-1-0 (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf libpolkit-backend-1-0 (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf libpoppler-glib8 (0.24.5-2ubuntu4.3 Ubuntu:14.04/trusty-updates [i386])
Conf fonts-opensymbol (2:102.6+LibO4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [all])
Conf libreoffice-style-human (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [all])
Conf uno-libs3 (4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf ure (4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-common (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [all])
Conf libreoffice-core (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-base-core (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-calc (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-gtk (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-gnome (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-draw (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-impress (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-writer (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-pdfimport (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-math (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf python3-uno (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-ogltrans (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libsndfile1 (1.0.25-7ubuntu2.1 Ubuntu:14.04/trusty-updates [i386])
Conf libwbclient0 (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386])
Conf lightdm (1.10.6-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf modemmanager (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libnm-util2 (0.9.8.8-0ubuntu7.2 Ubuntu:14.04/trusty-updates [i386])
Conf libnm-glib4 (0.9.8.8-0ubuntu7.2 Ubuntu:14.04/trusty-updates [i386])
Conf wpasupplicant (2.1-0ubuntu1.4 Ubuntu:14.04/trusty-updates [i386])
Conf isc-dhcp-common (4.2.4-7ubuntu12.4 Ubuntu:14.04/trusty-updates [i386])
Conf isc-dhcp-client (4.2.4-7ubuntu12.4 Ubuntu:14.04/trusty-updates [i386])
Conf policykit-1 (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf network-manager (0.9.8.8-0ubuntu7.2 Ubuntu:14.04/trusty-updates [i386])
Conf samba-libs (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386])
Conf libsmbclient (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386])
Conf samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [all])
Conf smbclient (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386])
Conf python-samba (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386])
Conf samba-common-bin (2:4.1.6+dfsg-1ubuntu2.14.04.11 Ubuntu:14.04/trusty-updates [i386])
Conf apt-utils (1.0.1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Conf apt-transport-https (1.0.1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Conf libisc95 (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386])
Conf libdns100 (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386])
Conf libisccc90 (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386])
Conf libisccfg90 (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386])
Conf libbind9-90 (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386])
Conf liblwres90 (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386])
Conf bind9-host (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386])
Conf dnsutils (1:9.9.5.dfsg-3ubuntu0.7 Ubuntu:14.04/trusty-updates [i386])
Conf krb5-locales (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Conf openssh-client (1:6.6p1-2ubuntu2.4 Ubuntu:14.04/trusty-updates [i386])
Conf openssl (1.0.1f-1ubuntu2.16 Ubuntu:14.04/trusty-updates [i386])
Conf python-apt-common (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf python3-apt (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf rsync (3.1.0-2ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf grub-common (2.02~beta2-9ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf grub2-common (2.02~beta2-9ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf grub-pc-bin (2.02~beta2-9ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf grub-pc (2.02~beta2-9ubuntu1.7 Ubuntu:14.04/trusty-updates [i386])
Conf python3-problem-report (2.14.1-0ubuntu3.19 Ubuntu:14.04/trusty-updates [all])
Conf python3-apport (2.14.1-0ubuntu3.19 Ubuntu:14.04/trusty-updates [all])
Conf apport (2.14.1-0ubuntu3.19 Ubuntu:14.04/trusty-updates [all])
Conf gir1.2-gtk-3.0 (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386])
Conf apport-gtk (2.14.1-0ubuntu3.19 Ubuntu:14.04/trusty-updates [all])
Conf firefox (44.0+build3-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf firefox-locale-en (44.0+build3-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf flashplugin-installer (11.2.202.559ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-gst-plugins-base-1.0 (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-networkmanager-1.0 (0.9.8.8-0ubuntu7.2 Ubuntu:14.04/trusty-updates [i386])
Conf gnome-desktop3-data (3.8.4-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Conf gstreamer1.0-alsa (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf gstreamer1.0-plugins-base (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf gstreamer1.0-plugins-base-apps (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf gstreamer1.0-x (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf im-config (0.24-1ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Conf indicator-session (12.10.5+14.04.20151021.1-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libdpkg-perl (1.17.5ubuntu5.5 Ubuntu:14.04/trusty-updates [all])
Conf libgnome-desktop-3-7 (3.8.4-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgtk-3-bin (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386])
Conf liblightdm-gobject-1-0 (1.10.6-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libnautilus-extension1a (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [i386])
Conf libnm-glib-vpn1 (0.9.8.8-0ubuntu7.2 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-avmedia-backend-gstreamer (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-presentation-minimizer (1:4.2.8-0ubuntu3 Ubuntu:14.04/trusty-updates [all])
Conf libunity-control-center1 (14.04.3+14.04.20150916-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf nautilus-data (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [all])
Conf unity-settings-daemon (14.04.0+14.04.20151012-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf unity-control-center (14.04.3+14.04.20150916-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf unity-services (7.2.6+14.04.20151021-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libunity-core-6.0-9 (7.2.6+14.04.20151021-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf unity (7.2.6+14.04.20151021-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libwhoopsie0 (0.2.24.6ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf whoopsie (0.2.24.6ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf linux-firmware (1.127.20 Ubuntu:14.04/trusty-updates [all])
Conf linux-libc-dev (3.13.0-76.120 Ubuntu:14.04/trusty-updates [i386])
Conf nautilus (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [i386])
Conf notify-osd-icons (0.8+14.04.20151016-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf os-prober (1.63ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf python-apt (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf python-libxml2 (2.9.1+dfsg1-3ubuntu4.7 Ubuntu:14.04/trusty-updates [i386])
Conf unattended-upgrades (0.82.1ubuntu2.4 Ubuntu:14.04/trusty-updates [all])
Conf python3-software-properties (0.92.37.7 Ubuntu:14.04/trusty-updates [all])
Conf software-properties-common (0.92.37.7 Ubuntu:14.04/trusty-updates [all])
Conf software-properties-gtk (0.92.37.7 Ubuntu:14.04/trusty-updates [all])
Conf ssh-askpass-gnome (1:6.6p1-2ubuntu2.4 Ubuntu:14.04/trusty-updates [i386])
Conf thunderbird (1:38.5.1+build2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf thunderbird-locale-en (1:38.5.1+build2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf thunderbird-gnome-support (1:38.5.1+build2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf thunderbird-locale-en-gb (1:38.5.1+build2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf thunderbird-locale-en-us (1:38.5.1+build2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf unzip (6.0-9ubuntu1.5 Ubuntu:14.04/trusty-updates [i386])
Conf oneconf-common (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf python3-oneconf (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf oneconf (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf python-oneconf (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
suvendu@suvendu-N148-N208:~$
```

---

### Post by bijaydeyp on 2016-01-31
Hi, grahammechanical!
I do the same as you do.I click the 'continue' button. so, you are saying it is very common & there is nothing to worry?

---

### Post by bijaydeyp on 2016-01-31
Hi,DougieFresh4U!
only once I clicked the 'partial upgrade' button & it was my big mistake.

---

### Post by oldos2er on 2016-01-31
I don't see any errors in the terminal output. Go ahead and run ```
sudo apt-get update && sudo apt-get dist-upgrade
``` to get your system up-to-date.

---

