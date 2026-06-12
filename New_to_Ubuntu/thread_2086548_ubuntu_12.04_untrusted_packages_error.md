---
title: "ubuntu 12.04 untrusted packages error"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by Flynn58 on 2012-11-21
I get an error whenever I try to update Ubuntu. These are the details in the error message:
```
accountsservice apport apport-gtk aptdaemon aptdaemon-data base-files bind9-host compiz compiz-core compiz-gnome compiz-plugins-default cups cups-bsd cups-client cups-common cups-ppdc dconf-gsettings-backend dconf-service dnsutils empathy empathy-common eog evince evince-common firefox firefox-globalmenu firefox-gnome-support firefox-locale-en flashplugin-installer fontconfig fontconfig-config fonts-liberation fonts-opensymbol foomatic-filters gcalctool ghostscript ghostscript-cups ghostscript-x ginn gir1.2-gst-plugins-base-0.10 gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-launchpad-integration-3.0 gir1.2-pango-1.0 gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-webkit-3.0 glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes gnome-control-center gnome-control-center-data gnome-desktop3-data gnome-games-data gnome-icon-theme gnome-media gnome-settings-daemon gnome-sudoku gnomine gnupg gpgv gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-x gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter hplip hplip-data initscripts isc-dhcp-client isc-dhcp-common jockey-common jockey-gtk krb5-locales landscape-client-ui-install language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base launchpad-integration libaccountsservice0 libart-2.0-2 libbind9-80 libcrystalhd3 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdconf-dbus-1-0 libdconf0 libdecoration0 libdns81 libevince3-3 libexif12 libexpat1 libfontconfig1 libframe6 libfreerdp-plugins-standard libfreerdp1 libgail-3-0 libgeis1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa libgnome-control-center1 libgnome-desktop-3-2 libgphoto2-2 libgphoto2-l10n libgphoto2-port0 libgrail5 libgrip0 libgs9 libgs9-common libgssapi-krb5-2 libgstreamer-plugins-base0.10-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgudev-1.0-0 libgwibber-gtk2 libgwibber2 libhpmud0 libisc83 libisccc80 libisccfg82 libjavascriptcoregtk-3.0-0 libjpeg-turbo8 libk5crypto3 libkrb5-3 libkrb5support0 liblaunchpad-integration-3.0-1 liblaunchpad-integration-common libldap-2.4-2 liblightdm-gobject-1-0 liblwres80 libmission-control-plugins0 libnautilus-extension1a libnspr4 libnspr4-0d libnss3 libnss3-1d libnux-2.0-0 libnux-2.0-common libpango1.0-0 libperl5.14 libpython2.7 libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math libreoffice-style-human libreoffice-style-tango libreoffice-writer librhythmbox-core5 libsane-hpaio libsqlite3-0 libssl1.0.0 libsyncdaemon-1.0-1 libtiff4 libtotem0 libudev0 libunity-core-5.0-5 libvlc5 libvlccore5 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxatracker1 libxslt1.1 light-themes lightdm linux-firmware linux-generic linux-headers-3.2.0-30 linux-headers-3.2.0-30-generic linux-headers-generic linux-image-3.2.0-30-generic linux-image-generic linux-libc-dev mahjongg nautilus nautilus-data nautilus-sendto-empathy nux-tools nvidia-current nvidia-current-updates openssl perl perl-base perl-modules policykit-1-gnome printer-driver-hpcups printer-driver-hpijs printer-driver-postscript-hp psmisc python-apport python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat python-debtagshw python-gst0.10 python-piston-mini-client python-problem-report python-software-properties python-ubuntu-sso-client python-ubuntuone-client python-ubuntuone-storageprotocol python-uno python2.7 python2.7-minimal qdbus resolvconf rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins sessioninstaller software-center software-properties-common software-properties-gtk sysv-rc sysvinit-utils telepathy-gabble telepathy-mission-control-5 thunderbird thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us totem totem-common totem-mozilla totem-plugins tzdata ubuntu-docs ubuntu-sso-client ubuntu-sso-client-gtk ubuntuone-client ubuntuone-installer udev udisks unity unity-common unity-greeter unity-lens-music unity-scope-musicstores unity-services uno-libs3 update-manager update-manager-core update-notifier update-notifier-common ure vino vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse xdiagnose xkb-data xserver-common xserver-xorg-core xserver-xorg-input-synaptics xserver-xorg-video-intel xul-ext-ubufox
```

I then looked around the internet to find a solution and tried to do sudo apt-get update. This was the response:
```
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise Release.gpg                                     
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise Release                                         
Err http://ppa.launchpad.net precise InRelease                                                                                     
  
Err http://ppa.launchpad.net precise Release.gpg                                                                                   
  Could not resolve 'ppa.launchpad.net'
Err http://archive.canonical.com precise InRelease                                                                                 
  
Err http://extras.ubuntu.com precise InRelease                                                                                     
  
Err http://archive.canonical.com precise Release.gpg                                                           
  Could not resolve 'archive.canonical.com'
Err http://extras.ubuntu.com precise Release.gpg                             
  Could not resolve 'extras.ubuntu.com'
Err http://ca.archive.ubuntu.com precise InRelease                           
  
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main TranslationIndex
Err http://ca.archive.ubuntu.com precise-updates InRelease                   
  
Err http://ca.archive.ubuntu.com precise-backports InRelease                 
  
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted TranslationIndex
Err http://ca.archive.ubuntu.com precise Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Err http://ca.archive.ubuntu.com precise-updates Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Err http://ca.archive.ubuntu.com precise-backports Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Err http://security.ubuntu.com precise-security InRelease
  
Err http://security.ubuntu.com precise-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main Translation-en
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted Translation-en
Reading package lists... Done
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/InRelease  

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease  

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/InRelease  

W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu/dists/precise/InRelease  

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu/dists/precise/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
flynn58@Flynn58-Ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise InRelease
Err http://ca.archive.ubuntu.com precise InRelease
  
Err http://ca.archive.ubuntu.com precise-updates InRelease
  
Err http://ca.archive.ubuntu.com precise-backports InRelease
  
Err http://archive.canonical.com precise InRelease
  
Err http://ca.archive.ubuntu.com precise Release.gpg                                                      
  Could not resolve 'ca.archive.ubuntu.com'
Err http://ca.archive.ubuntu.com precise-updates Release.gpg                                              
  Could not resolve 'ca.archive.ubuntu.com'
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise Release.gpg            
Err http://archive.canonical.com precise Release.gpg                                                      
  Could not resolve 'archive.canonical.com'
Err http://ca.archive.ubuntu.com precise-backports Release.gpg                                             
  Could not resolve 'ca.archive.ubuntu.com'
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise Release                 
Err http://ppa.launchpad.net precise InRelease                                                             
  
Err http://security.ubuntu.com precise-security InRelease                                                  
  
Err http://ppa.launchpad.net precise Release.gpg                         
  Could not resolve 'ppa.launchpad.net'
Err http://extras.ubuntu.com precise InRelease                           
  
Err http://security.ubuntu.com precise-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://extras.ubuntu.com precise Release.gpg
  Could not resolve 'extras.ubuntu.com'
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted TranslationIndex
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/main Translation-en
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) precise/restricted Translation-en
Reading package lists... Done
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/InRelease  

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease  

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/InRelease  

W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu/dists/precise/InRelease  

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu/dists/precise/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Could not resolve 'extras.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

I have no idea what to do here, and I really just want to update my packages so I can move on an upgrade to 12.10

Please help me.

---

### Post by newb85 on 2012-11-21
Something seems amiss in your apt sources.  Some of your addresses are incorrect.  Please give the output of
```
cat /etc/apt/sources.list
```

---

