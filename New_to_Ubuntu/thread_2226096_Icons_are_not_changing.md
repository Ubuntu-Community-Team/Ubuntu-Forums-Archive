---
title: "Icons are not changing"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by sivakumar-sakam on 2014-05-25
My icons are not changing when I am trying to change from Unity Tweak Tool(Ubuntu 14.04)

---

### Post by grumblebum2 on 2014-05-25
What icon set and how did you install?

---

### Post by sivakumar-sakam on 2014-05-25
Some of them installed via Nooblabs(sudo apt-get install <icon name>) and other via copied to themes folder. Installed so many please check attached snapshot.. 
Thanks for your quick reply.. :)

---

### Post by grumblebum2 on 2014-05-25
What does this terminal command give you ...
```
ls ~/.icons /usr/share/icons
```

---

### Post by sivakumar-sakam on 2014-05-25
Adwaita                  LoginIcons
cab_extract.png          mac-cursors
cab_view.png             malys-uniblue
contrastlarge            MBuntu-OSX
convertme.png            MBuntu-SL
default                  MBuntu-XL
DMZ-Black                NITRUX-2
DMZ-White                NITRUX-Buttons-2
elementary               Numix
elementary-mono-dark     nuoveXT2
Faenza                   oxygen
Faenza-Ambiance          redglass
Faenza-Dark              ubuntu-mono-dark
Faenza-Darker            ubuntu-mono-light
Faenza-Darkest           unity-icon-theme
Faenza-Radiance          unity-webapps-applications
Faience                  whiteglass
gnome                    zoncolor
handhelds                zoncolorBrave
hicolor                  zoncolorBrown
HighContrast             zoncolorDull
Humanity                 zoncolorGreen
Humanity-Dark            zoncolorGrey
Humanity-Dark-Blue       zoncolorGreyDark
Humanity-Dark-Brown      zoncolorMaroon
Humanity-Dark-Graphite   zoncolorMix-YellowTurquoise
Humanity-Dark-Green      zoncolorOrange
Humanity-Dark-Orange     zoncolorPink
Humanity-Dark-Pink       zoncolorPurple
Humanity-Dark-Purple     zoncolorRed
Humanity-Dark-Red        zoncolorSilver
Humanity-Dark-Yellow     zoncolorSky
Humanity-Light-Blue      zoncolorSlate
Humanity-Light-Brown     zoncolorWhite
Humanity-Light-Graphite  zoncolorXtra-Faenza-Darkest
Humanity-Light-Green     zoncolorXtra-Faenza-Light
Humanity-Light-Orange    zoncolorXtra-Silver-Faenza-Darkest
Humanity-Light-Pink      zoncolorXtra-Sky-Faenza-Light
Humanity-Light-Purple    zoncolorXtra-Slate-Faenza-Darkest
Humanity-Light-Red       zoncolorXtra-Slate-Faenza-Light
Humanity-Light-Yellow    zoncolorXtra-Ubuntuish-Dark
Ieos7                    zoncolorXtra-Ubuntuish-Light
locolor

---

### Post by grumblebum2 on 2014-05-25
Can you copy paste from your terminal and then highlight with left mouse 
and hit the # icon to enclose in code blocks.(# icon only shows in advanced reply)
eg
```
glen@Trusty:~$ ls ~/.icons /usr/share/icons
/home/glen/.icons:
GartoonRedux  ubuntu-mono-dark

/usr/share/icons:
Adwaita                         DMZ-Black-Medium  Faience        redglass
AlkanoBlack                     DMZhaloG          gnome          RezoBlack
Breeze                          DMZ-White         handhelds      RingOrange
cab_extract.png                 DMZ-White-Large   hicolor        ubuntu-mono-dark
cab_view.png                    DMZ-White-Medium  HighContrast   ubuntu-mono-light
ComixCursors-Opaque-Black       Faba              Humanity       unity-icon-theme
ComixCursors-Opaque-Slim-Black  Faenza            Humanity-Dark  unity-webapps-applications
ComixCursors-Orange-Huge        Faenza-Ambiance   IsBig          whiteglass
ComixCursors-Slim-Black         Faenza-Dark       locolor        XenonBlue
crystalblue                     Faenza-Darker     LoginIcons
default                         Faenza-Darkest    Moka
DMZ-Black                       Faenza-Radiance   oxy-black
```

I installed the Faenza icons using the noobslab ppa.
No problem switching to  Faenza-Dark icons using UTT.
Terminal confirms dconf change...
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **gsettings get org.gnome.desktop.interface icon-theme**
'Faenza-Dark'
```

---

### Post by sivakumar-sakam on 2014-05-25
okay. I have installed KDE and then removed it.. after then issue started...

```
contrastlarge            MBuntu-OSX
convertme.png            MBuntu-SL
default                  MBuntu-XL
DMZ-Black                NITRUX-2
DMZ-White                NITRUX-Buttons-2
elementary               Numix
elementary-mono-dark     nuoveXT2
Faenza                   oxygen
Faenza-Ambiance          redglass
Faenza-Dark              ubuntu-mono-dark
Faenza-Darker            ubuntu-mono-light
Faenza-Darkest           unity-icon-theme
Faenza-Radiance          unity-webapps-applications
Faience                  whiteglass
gnome                    zoncolor
handhelds                zoncolorBrave
hicolor                  zoncolorBrown
HighContrast             zoncolorDull
Humanity                 zoncolorGreen
Humanity-Dark            zoncolorGrey
Humanity-Dark-Blue       zoncolorGreyDark
Humanity-Dark-Brown      zoncolorMaroon
Humanity-Dark-Graphite   zoncolorMix-YellowTurquoise
Humanity-Dark-Green      zoncolorOrange
Humanity-Dark-Orange     zoncolorPink
Humanity-Dark-Pink       zoncolorPurple
Humanity-Dark-Purple     zoncolorRed
Humanity-Dark-Red        zoncolorSilver
Humanity-Dark-Yellow     zoncolorSky
Humanity-Light-Blue      zoncolorSlate
Humanity-Light-Brown     zoncolorWhite
Humanity-Light-Graphite  zoncolorXtra-Faenza-Darkest
Humanity-Light-Green     zoncolorXtra-Faenza-Light
Humanity-Light-Orange    zoncolorXtra-Silver-Faenza-Darkest
Humanity-Light-Pink      zoncolorXtra-Sky-Faenza-Light
Humanity-Light-Purple    zoncolorXtra-Slate-Faenza-Darkest
Humanity-Light-Red       zoncolorXtra-Slate-Faenza-Light
Humanity-Light-Yellow    zoncolorXtra-Ubuntuish-Dark
Ieos7                    zoncolorXtra-Ubuntuish-Light
locolor

```

---

### Post by grumblebum2 on 2014-05-25
> **sivakumar-sakam said:**
> okay. I have installed KDE and then removed it.. after then issue started...


It pays to put all relevant info in your first post.
No idea what exactly you installed or subsequently uninstalled.
kubuntu-desktop???

---

### Post by sivakumar-sakam on 2014-05-25
Yes Kubuntu-desktop.......

---

### Post by grumblebum2 on 2014-05-25
> **sivakumar-sakam said:**
> Yes Kubuntu-desktop.......
kubuntu-desktop is just a meta-package that contains no application itself but just lists numerous packages as dependencies.
ie 
Installing kubuntu-desktop pulls in all the packages needed for a kubuntu/kde desktop environment.
However removing kubuntu-desktop only removes the actual kubuntu-desktop package.
The packages kubuntu-desktop installed as dependencies remain.

Nowadays installing kde with Gnome already installed can cause problems.

Haven't dealt with it myself.
You will need to google "completely remove kubuntu-desktop in 14.04"
May be easier to backup and reinstall.

This solution was used in the past but only up to date with 12.10
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

If it's any help these are all the new packages to be installed if I was to install kubuntu-desktop in my 14.04 Ubuntu install...
```
about-distro akonadi-backend-mysql akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark audiocd-kio baloo bluedevil cdparanoia cdrdao colord-kde consolekit cryptsetup cryptsetup-bin docbook-xsl dolphin dragonplayer freerdp-x11 freespacenotifier gnupg-agent gnupg2 gpgsm gstreamer0.10-qapt gtk2-engines-oxygen gtk3-engines-oxygen gwenview ibus-qt4 icoutils k3b k3b-data kaccessible kaddressbook kamera kate kate-data katepart kcalc kde-base-artwork kde-baseapps-bin kde-baseapps-data kde-config-gtk-style kde-config-pimactivity kde-config-tablet kde-config-telepathy-accounts kde-config-whoopsie kde-runtime kde-runtime-data kde-style-oxygen kde-telepathy kde-telepathy-approver kde-telepathy-auth-handler kde-telepathy-contact-list kde-telepathy-data kde-telepathy-declarative kde-telepathy-desktop-applets kde-telepathy-filetransfer-handler kde-telepathy-integration-module kde-telepathy-minimal kde-telepathy-send-file kde-telepathy-text-ui kde-touchpad kde-wallpapers-default kde-window-manager kde-window-manager-common kde-workspace kde-workspace-bin kde-workspace-data kde-workspace-kgreet-plugins kde-zeroconf kdegraphics-strigi-analyzer kdelibs-bin kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdepasswd kdepim-kresources kdepim-runtime kdepimlibs-kio-plugins kdesudo kdoctools khelpcenter4 kinfocenter kio-audiocd kio-mtp klipper kmag kmail kmenuedit kmix kmousetool knotes konsole kontact korganizer krdc kscreen ksnapshot ksysguard ksysguardd ksystemlog ktorrent ktorrent-data kubuntu-debug-installer kubuntu-desktop kubuntu-docs kubuntu-driver-manager kubuntu-notification-helper kubuntu-settings-desktop kubuntu-settings-netbook kubuntu-web-shortcuts kwalletmanager libaccounts-qt1 libaio1 libakonadi-calendar4 libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadi-notes4 libakonadi-socialutils4 libakonadiprotocolinternals1 libattica0.4 libbaloocore4 libbaloofiles4 libbaloopim4 libbaloowidgets4 libbalooxapian4 libbluedevil1 libboost-program-options1.54.0 libboost-thread1.54.0 libcalendarsupport4 libchm1 libck-connector0 libcln6 libcryptsetup4 libdebconf-kde0 libdlrestrictions1 libdmtx0a libepub0 libeventviews4 libflac++6 libgpgme++2 libgps20 libgrantlee-core0 libgrantlee-gui0 libhsqldb1.8.0-java libibus-qt1 libincidenceeditorsng4 libindicate-qt1 libindicate5 libk3b6 libkabc4 libkactivities-bin libkactivities-models1 libkactivities6 libkalarmcal2 libkateinterfaces4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4 libkcddb4 libkcmutils4 libkcompactdisc4 libkdcraw-data libkdcraw23 libkde3support4 libkdeclarative5 libkdecorations4abi1 libkdecore5 libkdepim4 libkdepimdbusinterfaces4 libkdesu5 libkdeui5 libkdewebkit5 libkdgantt2-0 libkdnssd4 libkemoticons4 libkephal4abi1 libkexiv2-11 libkexiv2-data libkfbapi1 libkfile4 libkfilemetadata4 libkgapi2-2 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkio5 libkipi-data libkipi11 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmanagesieve4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkolab0 libkolabxml1 libkonq-common libkonq5-templates libkonq5abi1 libkontactinterface4 libkparts4 libkpeople3 libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4 libksane-data libksane0 libksba8 libkscreen1 libkscreensaver5 libksgrd4 libksieve4 libksieveui4 libksignalplotter4 libktexteditor4 libktnef4 libktorrent-l10n libktorrent5 libktpcommoninternalsprivate7 libkubuntu0 libkunitconversion4 libkwineffects1abi4 libkwinglesutils1 libkwinglutils1abi3 libkworkspace4abi2 libkxmlrpcclient4 liblightdm-qt-3-0 libloudmouth1-0 libmailcommon4 libmailimporter4 libmailtransport4 libmessagecomposer4 libmessagecore4 libmessagelist4 libmessageviewer4 libmicroblog4 libmodemmanagerqt1 libmuonprivate2 libmusicbrainz5-0 libmygpo-qt1 libmysqlclient18 libnepomuk4 libnepomukcleaner4 libnepomukcore4abi1 libnepomukquery4a libnepomukutils4 libnetworkmanagerqt1 libnoteshared4 libntrack-qt4-1 libntrack0 liboath0 libokularcore4 libopenconnect2 libpam-ck-connector libperl4-corelibs-perl libphonon4 libpimactivity4 libpimcommon4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4abi4 libplasmagenericshell4 libpolkit-qt-1-1 libpoppler-qt4-4 libprison0 libprocesscore4abi1 libprocessui4a libpth20 libqaccessibilityclient0 libqalculate5 libqalculate5-data libqapt2 libqapt2-runtime libqgpgme1 libqimageblitz4 libqmobipocket1 libqoauth1 libqrencode3 libqt4-qt3support libqt4-sql-mysql libqtglib-2.0-0 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libreoffice-base libreoffice-base-drivers libreoffice-java-common libreoffice-kde libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb libreoffice-style-oxygen libruby1.9.1 libsendlater4 libservlet3.0-java libsignon-qt1 libsolid4 libstreamanalyzer0 libstreams0 libsyndication4 libtag-extras1 libtaskmanager4abi5 libtelepathy-logger-qt4-1 libtelepathy-qt4-2 libtemplateparser4 libthreadweaver4 libvirtodbc0 libweather-ion6 libxcb-damage0 libxcb-record0 libxcb-xtest0 libxerces-c3.1 libyaml-0-2 libzip2 lightdm-kde-greeter muon-discover muon-notifier muon-updater mysql-client-core-5.5 mysql-common mysql-server-core-5.5 nepomuk-core-data nepomuk-core-runtime ntrack-module-libnl-0 odbcinst odbcinst1debian2 okular okular-extra-backends oxygen-cursor-theme oxygen-icon-theme pam-kwallet partitionmanager phonon phonon-backend-gstreamer phonon-backend-gstreamer-common phonon-backend-gstreamer1.0 pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook plasma-nm plasma-runner-telepathy-contact plasma-scriptengine-javascript plasma-widget-folderview plasma-widget-kimpanel plasma-widget-menubar plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text polkit-kde-1 print-manager python3-dbus.mainloop.qt python3-pykde4 python3-pyqt4 python3-sip qapt-batch qapt-deb-installer quassel quassel-data ruby ruby1.9.1 scdaemon shared-desktop-ontologies skanlite socat software-properties-kde systemsettings ttf-dejavu-core ttf-oxygen-font-family ubuntu-release-upgrader-qt usb-creator-kde user-manager vcdimager virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
```

You could preface that lot with ```
sudo apt-get **-s** remove
```and see what you get.
Using the **-s** (simulate) option won't uninstall anything. Remove the **-s** to actually run.


Afterwards run 
```
sudo apt-get install ubuntu-desktop
```
just to make sure you still have the needed **ubuntu-desktop** packages

---

### Post by sivakumar-sakam on 2014-05-26
Awesome man.... it worked perfectly...
thank you so much....

---

### Post by grumblebum2 on 2014-05-26
No problem.
Put that in your knowledge bank. :p

---

### Post by sivakumar-sakam on 2014-05-26
ya Sure;)

---

