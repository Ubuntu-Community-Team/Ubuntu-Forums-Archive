---
title: "Ubuntu Desktop Computing Made Easy Karmic Koala 9.10"
date: 2009-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by TrakerJon on 2009-11-17
This is my Karmic Koala post (Jaunty Jackalope can be found at [http://ubuntuforums.org/showthread.php?t=1181327]("http://ubuntuforums.org/showthread.php?t=1181327")). Enjoy and share!

This documentation is intended for folks that would like to add additional programs and applications to their Ubuntu Karmic Koala installation for a better overall experience with very little effort. Please keep in mind older computers may have video performance issues due to high CPU usage and increased memory requirements.

Recommended: Pentium 4 or higher processor with 1Gb SDRAM, 256Mb graphics card, 10/100 Ethernet card and 20Gb hard disk.

The easiest way to perform most of these installs is to copy and paste from this post into a terminal window (found in Accessories). 

**Start by going to System > select Administration > select Software Sources > Check the appropriate boxes under the Ubuntu Software, Third-Party Software and Updates tabs > Close and Reload**

Update Notice: There have been reports of operating system shutdown issues relating to the "_*pre-released*_" (karmic-proposed) kernel update (linux-headers-2.6.31-21 and linux-image-2.6.31-21 files) currently offered in the Ubuntu Repositories. In other words, when in in doubt, don't do it. Only install the important security (karmic-security) and recommended updates (karmic-updates) unless you're willing to risk a reinstall to test it out. 

Install the available Ubuntu updates at this point, look for the update notification icon on the task bar. Reboot after updating your system and then install as many of the following as you wish.

If you're having slowness issues with the default repository go to System > select Administration > select Software Sources > Ubuntu Software tab > Download from: drop down menu > select Other > click Select Best Server and  when it finishes the query click Choose Server > Close and Reload.

Many of these installations require access to the Medibuntu Repository and enabling some additional software sources. Directions are on this site: **[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)** or  simply do the following from a terminal window:

[B]sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update[/B]

If you're having problems with the main Medibuntu Repository manually enter a mirror site's URLs in **System > Administration > Software Sources > Other Software**. Click close and choose reload (you might get an error message). Then from a terminal prompt run run **sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring** followed by **sudo apt-get update**.

Mirror 1:

deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) karmic free non-free
deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) karmic free non-free

Mirror 2:

deb [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) karmic free non-free
deb-src [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) karmic free non-free

Mirror 3:

deb [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) karmic free non-free
deb-src [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) karmic free non-free


**Media players, codecs, plug-ins and accessories** are needed for playing various multimedia formats.

**sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools freepats gstreamer0.10-gnomevfs liba52-0.7.4 libass3 libavcodec52 libavformat52 libavutil49 libcdaudio1 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfreebob0 libgsm1 libid3tag0 libiptcdata0 libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmpcdec3 libmpeg2-4 libofa0 libopenspc0 libpostproc51 libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0 libtwolame0 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc easytag-aac faac faad ffmpeg ffmpeg2theora flac icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmozjs0d libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1a mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 libamrnb3 libamrwb3 sox tagtool twolame vorbis-tools gecko-mediaplayer build-essential comerr-dev cpp-4.3 dpkg-dev g++ g++-4.3 g++-4.4 g++-4.4-multilib gcc-4.3 gcc-4.3-base gcc-4.3-multilib gcc-4.4-multilib gcc-multilib gettext gnome-mplayer guile-1.8 html2text intltool-debian ladspa-sdk lib64gcc1 lib64gomp1 lib64stdc++6 libao2 libaudio2 libavdevice52 libavifile-0.7c2 libc6-amd64 libc6-dev-amd64 libcurl4-gnutls-dev libdiscid0 libgcc1-dbg libgcrypt11-dev libggi-target-terminfo libggi-target-x libggi2 libgii1 libgii1-target-x libgnutls-dev libgpg-error-dev libgssrpc4 libidn11-dev libkadm5srv6 libkdb5-4 libkrb5-dev libldap2-dev liblrdf0 liblzo2-2 libmail-sendmail-perl libmpeg3-1 libmusicbrainz3-6 libopenal1 libqt3-mt libqt4-xml libqtcore4 libqtgui4 libraptor1-dev libreadline5 libstdc++6-4.3-dev libstdc++6-4.4-dev libsvga1 libsys-hostname-long-perl libtasn1-3-dev libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml2-dev libxslt1-dev mplayer-nogui mplayer-skins patch po-debconf zlib1g-dev libdvbpsi5 libebml0 libiso9660-5 liblua5.1-0 libmatroska0 libsdl-image1.2 jack-tools jackd libjackasyn0 qjackctl libjack0 libkadm5clnt6**

Adobe Flash
**sudo apt-get install flashplugin-nonfree flashplugin-installer**

The latest Sun Java JRE
**sudo apt-get install gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin unixodbc**

Kaffeine - KDE Media Player
**sudo apt-get install kaffeine**

Amarok is a powerful music player for Linux with an intuitive interface.
**sudo apt-get install amarok**

Ardour, SoundKonverter, LMMS, Jokosher and AcidRip for multimedia recording, editing, conversions, mixing, etc.
**sudo apt-get install ardour soundkonverter jokosher lmms acidrip**

K9Copy, K3b and DeVeDe when you need DVD, CD, VCD and VCD software (requires libdvdcss2)
**sudo apt-get install k9copy k3b devede**


**GetDeb** is another repository you definitely will want. Follow the **"How to Install Apps from GetDeb"** instructions before attempting to install the following eleven applications. **[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)**

**VLC** (VideoLAN Client) is a portable multimedia player capable of reading most audio and video formats.
**[http://www.getdeb.net/software/VLC](http://www.getdeb.net/software/VLC)**
**sudo apt-get install vlc**

**Audacious2** is the very innovative Audio Replacement for XMMS
**[http://www.getdeb.net/software/Audacious](http://www.getdeb.net/software/Audacious)**
**sudo apt-get install audacious**

**Songbird** is a desktop Web player, digital jukebox and Web browser mash-up.
**[http://www.getdeb.net/software/Songbird](http://www.getdeb.net/software/Songbird)**
**sudo apt-get install songbird**

**Transmageddon** supports almost any format as its input and can generate a very large host of output files.
**[http://www.getdeb.net/software/Transmageddon](http://www.getdeb.net/software/Transmageddon)**
**sudo apt-get install transmageddon**

**Audacity** is a cross-platform multitrack audio editor.
**[http://www.getdeb.net/software/Audacity](http://www.getdeb.net/software/Audacity)**
**sudo apt-get install audacity**

**AceoneISO2** is a CD/DVD image manipulator for Linux (used primarily with .iso files).
**[http://www.getdeb.net/software/AcetoneISO](http://www.getdeb.net/software/AcetoneISO)**
**sudo apt-get install acetoneiso**

**Azureus** can be handy for things not found with Gnutella (see Firewalls and avast! sections below before using).
**[http://www.getdeb.net/software/Azureus](http://www.getdeb.net/software/Azureus)**
**sudo apt-get install azureus**

**Frostwire** is similar to Gnutella (see Firewalls and avast! sections below before using).
**[http://www.getdeb.net/software/Frostwire](http://www.getdeb.net/software/Frostwire)**
**sudo apt-get install frostwire**

**Shutter** is a feature-rich screenshot program.
**[http://www.getdeb.net/software/Shutter](http://www.getdeb.net/software/Shutter)**
**sudo apt-get install shutter**

**PDF MOD** is a simple tool for modifying PDF documents. 
**[http://www.getdeb.net/software/PDFMod](http://www.getdeb.net/software/PDFMod)**
**sudo apt-get install pdfmod**

**KompoZer** is a complete web authoring system. 
**[http://www.getdeb.net/software/Kompozer](http://www.getdeb.net/software/Kompozer)**
**sudo apt-get install kompozer**

Streamripper will allow you to download internet radio station broadcasts.
**sudo apt-get install streamripper**


Gnutella is a lot like Limewire or Morpheus (see Firewalls and avast! sections below before using).
**sudo apt-get install gtk-gnutella**

**Streamtastic** is the java based gui for Streamripper.
Download the stable version from **[https://code.launchpad.net/streamtastic/+download]("https://code.launchpad.net/streamtastic/+download")**

Notes: Install Streamripper and then create a folder in your home directory called Streamtastic. Create a sub folder of Streamtastic called downloads. Download Streamtastic and extract the files into the Streamtastic folder. Launch the Streamtastic.sh file from a command prompt (user@ubuntu-desktop:~/Streamtastic$ ./Streamtastic.sh) and when prompted point the download destination to your downloads folder. Select the station you would like to listen to and right-click on the reference to play and/or record. You can play and record at the same time, you'll be prompted to select a player (if you've installed amarok or vlc they're in /usr/bin). If you need to edit the configuration file to change the path to your player or download preferences, it can be found in a hidden .streamtastic folder in your home directory. 
If you have folder permissions issues do the following:
**sudo chown -R username:username ~/Streamtastic** (put in *your* "username")
**sudo chmod -R 700 ~/Streamtastic**

**Shoutcast** is a good place to shop for internet radio stations. **[http://www.shoutcast.com/](http://www.shoutcast.com/)**


**ATI/nVidia Drivers and Advanced Desktop Effects**

This requires some effort on the part of the user to know exactly what graphics card they have installed, use with caution and please read all applicable instructions.

Ubuntu 9.10 Karmic Koala comes with a Nouveau display graphic driver by default. The following should help install the drivers you need.

1. Click Applications > Ubuntu Software Center
2. From the left menu choose Get Free Software
3. In the search field on the right find and install Advanced Desktop Effects Settings (Compiz Setup) and ATI or nVidia binary X.org Drivers (based on what graphics card you have inside the computer). Selecting the driver and clicking the arrow to the right will get the list of supported graphics cards.
4. After the installations go to System > Administration > Hardware Drivers.
5. The system will search for available drivers, choose the recommended option from the list and activate the driver by clicking Activate.
6. Restart your system and the new ATI/nVidia graphic display driver will be in use.

Unsupported updated versions of X.org drivers, libraries, etc. for Ubuntu [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)
Note: Import the key and add the repositories for your specific distribution in System > Administration > Software Sources then run sudo apt-get update from a terminal window.

**Compiz, Emerald and Screenlets**

The default Ubuntu display setup lets you choose from None, Normal or Extra. Make it more configurable with the CompizConfig Settings Manager...found in System > Preferences after installing the following:
**sudo apt-get install compizconfig-settings-manager gnome-art usplash startupmanager compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald screenlets librsvg2-common fusion-icon gnome-splashscreen-manager libart2-ruby1.8 libatk1-ruby1.8 libcairo-ruby1.8 libemeraldengine0 libgconf2-ruby libgconf2-ruby1.8 libgdk-pixbuf2-ruby1.8 libglade2-ruby libglade2-ruby1.8 libglib2-ruby1.8 libgnome2-ruby libgnome2-ruby1.8 libgnomecanvas2-ruby1.8 libgtk2-ruby1.8 libpango1-ruby1.8 libruby1.8 libtidy-0.99-0 python-chardet python-compizconfig python-evolution python-feedparser python-gtkmozembed python-utidylib python-wnck ruby ruby1.8 menu**

Notes: Make sure you enable Visual Effects "**Extra**" (right click on your desktop, choose change Desktop Background and click on the Visual Effects tab) before adusting Compiz settings. Reset Compiz defaults by going into CCSM > Preferences > Profile & Backend > Click Reset to defaults.


Various compression/extraction and encoding/decoding utilities...
**sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils aish uudeview mpack lha arj cabextract file-roller libuu0**


**avast!** makes a very good anti-virus product for Linux it can be downloaded free for home use from **[http://avast.com/eng/download-avast-for-linux-edition.html](http://avast.com/eng/download-avast-for-linux-edition.html)** You'll need the home user free registration key (emailed to you from their site). The key can be pasted into a terminal window after you type avast at a terminal command prompt. The gui icon is located in Applications > Accessories. Update the program frequently and scan all questionable downloads.


**Email, VoIP and Text Chat**

Thunderbird, Sunbird and SpamAssassin for email and integrated calendar.
**sudo apt-get install thunderbird sunbird lightning-extension spamassassin calendar-google-provider calendar-timezones libdigest-hmac-perl libdigest-sha1-perl liberror-perl libio-socket-inet6-perl libmail-spf-perl libnet-dns-perl libnet-ip-perl libnetaddr-ip-perl libsocket6-perl re2c spamc**

Skype lets you talk and chat with friends all over the world.
**sudo apt-get install skype skype-common**

Note: You might have to configure your Options > Sound Devices > Sound In/Sound Out within Skype and test with the Echo/Sound test Service. I also had to enable and adjust my Ubuntu Volume Controls > Preferences > Mic and Mic Boost settings.

Kopete is an instant messenger client supporting AIM, ICQ, Live Messenger, Yahoo, Jabber, and more.
**sudo apt-get install kopete**

XChat is an IRC chat program that allows for multiple IRC channels (chat rooms) at the same time.
**sudo apt-get install xchat**

Pidgin is an easy to use and free chat client to connect to AIM, MSN, Yahoo, and more chat networks all at once.
**sudo apt-get install pidgin pidgin-data pidgin-libnotify**


Popular fonts for OpenOffice and other word processing applications.
**sudo apt-get install ttf-mscorefonts-installer mplayer-fonts ttf-xfree86-nonfree xfs cabextract ttf-liberation ttf-mscorefonts-installer**

Fonts, fonts and more fonts (pick and choose).
**sudo apt-get install ttf-larabie-straight ttf-larabie-deco xfonts-terminus-dos xfonts-terminus xfonts-terminus-oblique xfonts-mona tv-fonts ttf-tuffy ttf-sjfonts ttf-georgewilliams ttf-fifthhorseman-dkg-handwriting ttf-essays1743 ttf-opensymbol ttf-mgopen ttf-freefont ttf-dustin ttf-dejavu-extra ttf-dejavu-core ttf-dejavu ttf-bpg-georgian-fonts equivs ttf-sil-gentium gnome-specimen bsd-mailx dctrl-tools devscripts diffstat dput libapt-pkg-perl libauthen-sasl-perl libdevel-symdump-perl libio-pty-perl libio-stringy-perl libipc-run-perl libparse-debcontrol-perl libpod-coverage-perl libterm-size-perl libtest-pod-perl lintian patchutils postfix wdiff**

Note: Postfix is is associated with some of these fonts, be careful not to modify Postfix configurations if required for email purposes, otherwise select "no configuration" when prompted.

I typically don&#8217;t use Arabic and Asian fonts, to remove them from a terminal window type:
**sudo apt-get remove ttf-kochi-mincho ttf-kochi-gothic ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ttf-unfonts-core ttf-indic-fonts-core ttf-wqy-zenhei**

Note: Add them by simply using install instead of remove.

**HP printer driver issues? [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)**

Adobe still makes one of the best .pdf viewers.
**sudo apt-get install acroread acroread-fonts**

PDFedit is editor for manipulating PDF documents.
**sudo apt-get install pdfedit**

PDF-Shuffler allows for merging or splitting of pdf documents...rotate, crop and rearrange pages using an interactive and intuitive graphical interface. 
**sudo apt-get install pdfshuffler python-poppler python-pypdf**

AbiWord is a fast and easy to use word processing program.
**sudo apt-get install abiword**

gLabels is a program for creating labels and business cards for the GNOME desktop environment.
**sudo apt-get install glabels glabels-data**

iSpell comes in handy when spell checking documents from a terminal window
**sudo apt-get install ispell iamerican spell**

Wordnet is a comprehensive word database maintained by Princeton University
**sudo apt-get install wordnet tcl8.5 tk8.5 wordnet-base wordnet-gui**

The web interface for Wordnet is **[http://wordnetweb.princeton.edu/perl/webwn](http://wordnetweb.princeton.edu/perl/webwn)**

FBReader is an e-book reader for various platforms.
**sudo apt-get install fbreader**

Dia is similar to Microsoft® Visio.
**sudo apt-get install dia**

GanttProject is a tool for creating a project schedule with Gantt and resource load charts.
**[http://ganttproject.biz/download.php](http://ganttproject.biz/download.php)**

Planner for Gant charts and project plans.
**sudo apt-get install planner**

Scribus is a desktop publishing application.
**sudo apt-get install scribus**

Inkscape and Skencil for illustrations.
**sudo apt-get install inkscape skencil**

Gimp is an incredible image editing application.
**sudo apt-get install gimp gimp-data-extras gimp-gap gimp-plugin-registry libblas3gf libcv1 libcvaux1 libgfortran3 libglew1.5 libgtkglext1 libhighgui1 liblapack3gf liblqr-1-0 libtiff-tools gimp-data libgimp2.0**

Byzanz records your desktop and saves it to animated GIF files (viewable in a web browser).
**sudo apt-get install byzanz**

Note: Byzanz is a panel applet and not listed in Applications, add it by right-clicking the panel and selecting Add to Panel > Desktop Recorder. Desktop effects have to be turned off to use Byzanz. More information is available by typing man byzanz-record from a terminal window.

Xara Xtreme is a user friendly vector graphics drawing program.
**sudo apt-get install xaralx xaralx-examples**

Blender is open source software for 3D modeling, animation, rendering, interactive creation and playback.
**sudo apt-get install blender**

**webKam** is simple webcam application **[http://code.google.com/p/webkam-kde4/downloads/list](http://code.google.com/p/webkam-kde4/downloads/list)**

**Elltube** is a YouTube downloader and converter **[http://elltube.sourceforge.net/download](http://elltube.sourceforge.net/download)**

If you program in C\C++ languages you&#8217;ll need Build-Essential packages.
**sudo apt-get install build-essential **

Geany is a fast and lightweight IDE (Integrated Development Environment) for programming in various languages.
**sudo apt-get install geany**

Eclipse is an awesome open-source IDE for Java, C/C++ and Python.
**[http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/]("http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/")**

Note: Eclipse is available from the repositories but limits you to java development by default, I recommend the manual install referenced above. If you are unfortunate enough to develop apps in C/C++ (like me) this link should help as well... **[http://www.eclipse.org/cdt/downloads.php](http://www.eclipse.org/cdt/downloads.php)**

Vim, Gvim and Cream may come in handy for file editing (gedit works good too).
**sudo apt-get install vim-doc cscope vim-gnome tcl8.4 vim-gui-common vim-runtime libruby1.8 tclreadline cbrowser cream**
 
Gedit (Text Editor in Accessories) is installed by default but the plugins are not...
**sudo apt-get install gedit-plugins**

Note: Enable Gedit plugins in Edit > Preferences > Plugins.
The Gedit wiki is at **[http://live.gnome.org/Gedit](http://live.gnome.org/Gedit)**

jEdit is a java based full featured editor (make sure you have Sun JRE installed).
**sudo apt-get install jedit**

Meld is a visual diff and merge tool.
**sudo apt-get install meld**

gFTP is a generic FTP client (port 21 is typical and consider file permissions when uploading).
**sudo apt-get install gftp**

Convert .rpm files to .deb **[http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien)**
**sudo apt-get install alien**

Htop, SysInfo and HardInfo for referencing system information and benchmarking.
**sudo apt-get install htop sysinfo hardinfo**

Byzanz records your desktop and saves it to animated GIF files (viewable in a web browser).
**sudo apt-get install byzanz**

Note: Byzanz is a panel applet and not listed in Applications, add it by right-clicking the panel and selecting Add to Panel > Desktop Recorder. Desktop effects have to be turned off to use Byzanz. More information is available by typing man byzanz-record from a terminal window.

Fish (the applet, not the shell) is a fun animated panel applet that tells fortunes.
**sudo apt-get install fortune-mod fortunes-min librecode0**

Note: Add the panel applet by right-clicking the panel and selecting Add to Panel > Fish.

Glipper is a clipboard manager for the GNOME panel.
**sudo apt-get install glipper**

Note: If Clipboard manager does not appear in the panel applet menu, in a terminal window cd /usr/lib/glipper then run ./glipper It should allow you to add it as a panel applet at this point. The keyboard shortcut is <Ctrl><Alt>c

GNOME Commander is a "two-pane" graphical filemanager for the Gnome desktop environment.
**sudo apt-get install gnome-commander**

Add some useful features to nautilus...
**sudo apt-get install nautilus-actions nautilus-gksu nautilus-image-converter nautilus-open-terminal nautilus-script-audio-convert nautilus-script-collection-svn nautilus-script-manager nautilus-sendto nautilus-share nautilus-wallpaper imagemagick libapr1 libaprutil1 libsvn1 subversion**

NTFS Configuration Tool mounts NTFS drives (2000/XP/2003/Vista).
**sudo apt-get install ntfs-config**
**gksudo ntfs-config**

Note: Found in System > Administration.

**luckyBackup**...a powerful, fast and reliable backup & sync tool **[http://luckybackup.sourceforge.net/download.html](http://luckybackup.sourceforge.net/download.html)**

Partimage system backup, instructions can be found at: **[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)**
**sudo apt-get install partimage**

KDE Partition Manager allows you to manage your disks, partitions and file systems:
**sudo apt-get install partitionmanager**

Note: Documentation can be found at **[http://docs.kde.org/development/en/extragear-sysadmin/partitionmanager/index.html](http://docs.kde.org/development/en/extragear-sysadmin/partitionmanager/index.html)**

GParted is the GNOME partition editor for creating, reorganizing and deleting disk partitions.
**sudo apt-get install gparted dmraid jfsutils kpartx libdmraid1.0.0.rc15 xfsprogs reiserfsprogs reiser4progs ntfsprogs**

Note: Documentation can be found at **[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)**

**Reconstructor** will help you create your own Ubuntu based distribution **[http://www.reconstructor.org/wiki/reconstructor](http://www.reconstructor.org/wiki/reconstructor)**


**Defrag** (or fidefrag I should say)

**sudo apt-get install bzr python-psyco bzrtools python-paramiko**
**bzr branch lp:fidefrag**
**cd fidefrag/src**
**sudo python fidefrag.py -d /<directory name>**

Note: It's not a good idea to defrag your whole system, some directories won't react very well. I typically defrag /usr (this one takes a long time), /var, /lib, /home, /etc, /bin and /sbin


**Google Earth** install: **[http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)**


Rainy days or a lot of time to kill? Frozen Bubble is a very addictive game.
**sudo apt-get install frozen-bubble**

Kids in the house? Childsplay, GCompris and TuxPaint.
**sudo apt-get install childsplay childsplay-alphabet-sounds-bg python-numpy python-pygame python-sqlalchemy gcompris gcompris-sound-en tuxpaint tuxpaint-config gnucap gcompris-data libgnet2.0-0 libnetpbm10 netpbm tuxpaint-data tuxpaint-plugins-default tuxpaint-stamps-default libfltk1.1**


**Firewalls**

Internet security is important these days and firewalls can be quite complex, hopefully the following will help...use only one of these two applications and please read all of the documentation first. Most people are already behind a broadband router configured to give you "TruStealth" protection on the internet...check your current protection at the Sheilds Up! link below before being too concerned.

**ufw** ("uncomplicated firewall" included with Ubuntu), by default is set to "allow" all network traffic, the wiki instructions are at **[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)** then **sudo ufw enable** the firewall at system startup.

Personally I would rather use the gui interface for ufw...
**sudo apt-get install gufw**
 
**Firestarter** is quite easy to configure **[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)**
**sudo apt-get install firestarter menu**

Check your firewall protection at Sheilds Up! (click Proceed and use the All Service Ports option).
[**https://www.grc.com/x/ne.dll?bh0bkyd2**]("https://www.grc.com/x/ne.dll?bh0bkyd2")

Wireshark is a full featured network protocol analyzer.
**sudo apt-get install wireshark**


**Simple file encryption using GnuPG**

From a terminal window in the directory where the file is stored:
gpg -c <filename> (encrypts, prompts twice for pass-phrase, creates <filename.gpg>)
gpg <filename.gpg> (decrypts, prompts for pass-phrase)

Notes: The source file can be deleted or moved after encryption. Sometimes when decrypting the pass-phrase prompt will pop-up behind the pinentry window. Type **man gpg** from a terminal window for more options. If you would like more advanced file encryption with keys and signatures visit **[http://www.gnupg.org/documentation/howtos.en.html](http://www.gnupg.org/documentation/howtos.en.html)** for more information.

Advanced file encryption with GNU Privacy Assistant (use with caution and knowledge)
**sudo apt-get install gpa**


**The Karmic wiki** can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)**

**The Jaunty wiki** can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)**

**The UNR (Ubuntu Netbook Remix) wiki is here [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)**

**The Ubuntu Pocket Guide** can be found at **[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)**

**Ubuntu Desktop Essentials [http://www.techotopia.com/index.php/Ubuntu_Desktop_Essentials](http://www.techotopia.com/index.php/Ubuntu_Desktop_Essentials)**

**ListOfOpenSourcePrograms [https://help.ubuntu.com/community/ListOfOpenSourcePrograms](https://help.ubuntu.com/community/ListOfOpenSourcePrograms)**

**Best 100** Open Source Applications **[http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/](http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/)**

**Best 50** Ubuntu Opensource Applications For Design And Developing **[http://www.emmaalvarez.com/2007/12/top-best-50-ubuntu-opensource.html](http://www.emmaalvarez.com/2007/12/top-best-50-ubuntu-opensource.html)**

**GetDeb** software site for Ubuntu and Debian [**http://www.getdeb.net/**]("http://www.getdeb.net/")

**Gnome Desktop software** site [**http://www.gnomefiles.org/**]("http://www.gnomefiles.org/")

**Linux App Finder [http://linuxappfinder.com/](http://linuxappfinder.com/)**

**KDE-Apps.org [http://www.kde-apps.org/](http://www.kde-apps.org/)**

**Ubuntu PPA Search [https://edge.launchpad.net/ubuntu/+ppas](https://edge.launchpad.net/ubuntu/+ppas)**

**Ubuntu Games [https://help.ubuntu.com/community/Games](https://help.ubuntu.com/community/Games)**

**Cool wallpaper and more [http://www.kde-look.org/](http://www.kde-look.org/)**


**Maximus Issues** (windows always maximize when an application is launched)
If you have a Netbook and auto maximize windows is driving you crazy try this from a terminal window: type gconf-editor then go to Apps > Maximus > check no_maximize


If **Firefox windows open off screen or are too large to use**, you may need to reset Firefox's controls and toolbars.

1. Close down Firefox completely: On the Firefox window, click the File menu then select Exit.
2. From a terminal window type: firefox -safe-mode
3. Firefox should start up with a Firefox Safe Mode dialog with options.
4. Check mark Reset toolbars and controls.
5. Click Make Changes and Restart to restart Firefox


**Get your Trash Can and other desktop icons back**...

The default for new installed Ubuntu is clean desktop. So, for example, if you want to get your Trash Icon back you need to change the default setting.

**Step 1**. Run Desktop Configuration Editor

Open Application > Accessories > Terminal and type gconf-editor.

**Step 2**. Change the value for trash_icon_visible

After the Desktop configuration Editor is displayed, open apps > nautilus > desktop and click the value for trash_icon_visible. This also works for your computer, home and network icons.


**Setup Samba peer-to-peer with Windows [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)**

Install Samba stuff
**sudo apt-get install samba samba-common samba-tools smbclient swat samba-doc samba-doc-pdf smbfs libpam-smbpass libsmbclient libsmbclient-dev winbind samba-dbg libwbclient0 smbldap-tools ldb-tools keyutils libuser1 python-libuser system-config-samba libconvert-asn1-perl libcrypt-smbhash-perl libdigest-md4-perl libjcode-pm-perl libldb0 libnet-ldap-perl libtevent0 libunicode-map-perl libunicode-map8-perl libunicode-maputf8-perl libunicode-string-perl openbsd-inetd**

Once Samba is installed you can setup a very basic shared folder as follows:

You&#8217;ll need to create Samba passwords with this command:

**sudo smbpasswd -a USERNAME**

Make a backup copy of the original smb.conf file, in case you make an error:

**sudo cp /etc/samba/smb.conf ~**

Add a share to the very end of the file:

**sudo gedit /etc/samba/smb.conf**

[mystuff]
path = /home/USERNAME/mystuff
available = yes
valid users = USERNAME
read only = no
browsable = yes
public = yes
writable = yes

(There should be no spaces between the lines, and note also that there should be a single space both before and after each of the equal signs.)

Save the file and restart samba with  this command:

**sudo service samba restart**

Use this command from a terminal window to check that your smb.conf doesn&#8217;t contain any syntax errors: **testparm**

Don't forget to create your shared folder and modify the permissions as needed. You may also have to allow specific IP address TCP/UDP access through your firewall as well. Keep in mind if security is an issue to read up a lot more on the topic.


**How to setup remote access [http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)**


**Alternative shells for Linux**...

C, K, T, Z & Fish shells
**sudo apt-get install csh ksh tcsh zsh fish xsel zsh-doc**

**Bash Reference Manual [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)**

**chmod calculator [http://www.javascriptkit.com/script/script2/chmodcal.shtml](http://www.javascriptkit.com/script/script2/chmodcal.shtml)**


**Adding a Personal Package Archive (PPA) to your Ubuntu repositories**

Adding a PPA to Ubuntu takes no more than a couple of minutes.

**Step 1**: Copy the lines from the apt sources.list entries section of the PPA overview page. For example:

deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main

**Step 2**: On your Ubuntu computer, open System > Administration > Software Sources.

**Step 3**: Click the Third Party Software tab.

**Step 4**: Click the Add button.

**Step 5**: Paste the individual lines copied in step 1 by clicking the Add Source button.

When prompted, reload the software sources information. Don't worry if you see a warning about unverified software sources; we're going to fix that next.

**Adding the PPA's key to Ubuntu**

Now Ubuntu knows about the PPA. It also needs to know how to check the software hasn't changed since Launchpad built it.

Note: This is not an endorsement of any of the software in PPAs. You must make sure you trust the PPA owner before installing their software.

**Step 1**: On the PPA's overview page you'll see the PPA's OpenPGP key id. It'll look something like this: 1024/12345678. Copy it, or make a note of, *the portion after the slash*, e.g: 12345678.

**Step 2**: Open your terminal and enter:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 12345678

Replace 12345678 with the key id you copied in step 1.

**Step 3**: Finally, tell Ubuntu to re-load the details of each software archive it knows about:

sudo apt-get update

You're now ready to install software from the PPA, using a tool such as apt-get in the Terminal or Synaptic.

**Popular PPAs**

You can update your system with *"unsupported packages"* from these *"untrusted"* PPAs by adding them to your Software Sources. 

**VLC (VideoLAN Client)**
**deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) karmic main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D**
**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828**

**Compiz**
**deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) karmic main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 42C24D89**

**Shutter**
**deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) karmic main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 009ED615**

**FireFox**
**deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) karmic main** 
**deb-src [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) karmic main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C713DA6**

**X Updates** 
**deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) karmic main** 
**deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) karmic main** 

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9**


**Collection of useful commands...**
---------------------------------------------------------------   
**Searching for Packages:**             apt-cache search some_string      
**Show Package Info:**         apt-cache showpkg xxx             
**Show Package Dependencies:**     apt-cache depends xxx             
**Install:**             apt-get install xxx               
**Re-Install:**             apt-get --reinstall install xxx   
**Remove:**                     apt-get remove xxx                
**Remove All (configs too):**     apt-get remove --purge xxx
**Upgrade**:             apt-get -u upgrade
**Show Upgrades:**             apt-show-versions -u
**Show All Installed Packages:**    dpkg --list                       
**Find Package by File Name:**     apt-file search /bin/ping         
**Find filenames in a Package**:     apt-file list xxx                 
**Updating the apt-file Cache:**     apt-file update
**Info on Installed Package**        aptitude show xxx
**System Hardware Info**             sudo lshw > hardware.txt

**Linux Command Directory [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)**

**Linux Commands - A practical reference [http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)**

Clean up your system and free up space with **sudo apt-get clean** and **sudo apt-get autoremove**

If you're curious (like me) or have the need to know **uname -a && cat /etc/*release** in a terminal window will tell you the kernel version and release date, the distro id/release/codename/description.


Ok, about **wine**...in most cases a free to use Linux program will work just as well as apps on that other well known operating system. I don't recommend it but for the folks that like wine this wiki should help **[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)**

**Wine Application Database (AppDB) [http://appdb.winehq.org/](http://appdb.winehq.org/)**


To my friends...

I'm more than willing to add your suggestions and reference your favorite applications, this is your post as much as mine. I do ask that you keep the description brief and on a general level (for new users) when making recommendations. I started posting "Ubuntu Desktop Computing Made Easy" a while back (Gutsy Gibbon) mainly out of the frustration I had getting my workstation and personal computer to perform as expected (without hours upon hours of setup, search and configuration). It's my goal to make it "easy" for anyone to setup an Ubuntu Desktop Computer with everything they need or want, in a short period of time, ensuring the overall experience is an enjoyable one. 

Note: This post can be found very quickly by doing a Google search on Ubuntu Desktop Computing Made Easy. If you would like to link to this post or publish it elsewhere I do request that you obtain permission and give credit where credit is due.

Regards,

-TrakerJon

Dell GX270 3.2GHz Pentium 4 w/ 2Gb SDRAM using NVIDIA GeForce 6200 AGP video and MSI Wind Netbook U100 1.6GHz Intel Atom w/ 2Gb SDRAM using Intel Mobile 945GME Express video on Ubuntu 9.10

---

### Post by VolkerLanz on 2009-12-20
> 
KDE Partition Manager allows you to manage your disks, partitions and file systems:
sudo apt-get install partitionmanager

GParted is the GNOME partition editor for creating, reorganizing and deleting disk partitions.
sudo apt-get install gparted dmraid gparted jfsutils kpartx libdmraid1.0.0.rc15 xfsprogs reiserfsprogs reiser4progs ntfsprogs

Note: Documentation can be found at [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)


KDE Partition Manager uses most of the packages you suggest to install for GParted as well, so it should read:

sudo apt-get install partitionmanager jfsutils xfsprogs reiserfsprogs reiser4progs ntfsprogs

KDE Partition Manager docs are here:

[http://docs.kde.org/development/en/extragear-sysadmin/partitionmanager/index.html](http://docs.kde.org/development/en/extragear-sysadmin/partitionmanager/index.html)

---

