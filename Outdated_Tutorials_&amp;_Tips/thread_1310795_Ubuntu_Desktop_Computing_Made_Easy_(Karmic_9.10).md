---
title: "Ubuntu Desktop Computing Made Easy (Karmic 9.10)"
date: 2009-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by TrakerJon on 2009-11-02
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


**Clam Antivirus** (to be listed as Virus Scanner in Applications > Accessories) **[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)**

**sudo apt-get install clamav clamtk**

Operations available from a terminal session...

Update virus definitions: **sudo freshclam**

Scan files in your home directory: **sudo clamscan** 

Scan files in an entire directory: **sudo clamscan -r /<directory name>** 

Scan on the entire drive: **sudo clamscan -r /** 


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

### Post by lokutus25 on 2009-11-12
Amazing! Thanx!! :)

---

### Post by Warprunner on 2009-11-12
Simply TERRIFIC...Thank you!!!!!:KS

---

### Post by Tiganjero on 2009-11-12
Wow! Amazing! This will help a lot of people, since there hasn't been a tutorial this good posted in a while...

---

### Post by ublintu on 2009-11-14
The new "[B]Ubuntu Desktop Computing Made Easy" is out!
I will use this.
Thank you!
[/B]

---

### Post by noelvh on 2009-11-14
This is with out a doubt one of the best how to's I have ever seen for ubuntu.
It is well laided out and written. I have copied it to my UberNote note book, for future use, and to share. My thanks goes out to you for compiling this document.

You should add UberNote to this as a means of taking notes, and sharing them online for free, and its a plugin for Firefox.

Noel

---

### Post by TrakerJon on 2009-11-18
> **lokutus25 said:**
> Amazing! Thanx!! :)

You're very welcome, come back and visit, edits and updates will be ongoing until the next release.

---

### Post by TrakerJon on 2009-11-18
> **noelvh said:**
> This is with out a doubt one of the best how to's I have ever seen for ubuntu.
It is well laided out and written. I have copied it to my UberNote note book, for future use, and to share. My thanks goes out to you for compiling this document.

You should add UberNote to this as a means of taking notes, and sharing them online for free, and its a plugin for Firefox.

Noel

Noted and thank you, there are a variety of applications that aren't available (or up to speed yet) for Karmic so come back periodically for revisions.

---

### Post by TrakerJon on 2009-11-18
> **ublintu said:**
> The new "[B]Ubuntu Desktop Computing Made Easy" is out!
I will use this.
Thank you!
[/B]

It's not fully revised yet but it's getting there. Thanks for following my posts :D

---

### Post by TrakerJon on 2009-11-18
> **Tiganjero said:**
> Wow! Amazing! This will help a lot of people, since there hasn't been a tutorial this good posted in a while...

I'm very glad it made it to the General Help section, it should reach a few more folks that way. Cheers!

---

### Post by TrakerJon on 2009-11-18
> **Warprunner said:**
> Simply TERRIFIC...Thank you!!!!!:KS

Your thanks is appreciated, share and enjoy!

---

### Post by audiomick on 2009-11-18
My thanks to. You're a legend  :)

---

### Post by TrakerJon on 2009-11-18
> **audiomick said:**
> My thanks too. You're a legend  :)

Hahaha...diligent maybe. Legend? ...not yet but I'm working on it ;)

---

### Post by GCoffee on 2009-11-18
Definately looks like a good tutorial :) - Will mail my M$ user friends a copy of this ;)

Cheers,
GCoffee.

---

### Post by RJ12 on 2009-11-18
Just got a really big question about the guide. This is about Karmic but why are you adding a reference to menu.lst for GRUB which in Karmic is GRUB2 and dosent use menu.lst? You might want to change or delete that part.

Other than that little issue I love your Guide!!!!!!!:p:p:p:P:):popcorn::KS

---

### Post by TrakerJon on 2009-11-18
> **RJ12 said:**
> Just got a really big question about the guide. This is about Karmic but why are you adding a reference to menu.lst for GRUB which in Karmic is GRUB2 and dosen't use menu.lst? You might want to change or delete that part.

Other than that little issue I love your Guide!!!!!!!:p:p:p:P:):popcorn::KS

You are very correct my friend, still cleaning up the post, thanks for pointing that out. It was a carry over from Jaunty that I didn't catch. I'm still in the testing phase on this release, I'll be rewriting instructions for installing ATI/nVidia drivers, references to Compiz and a few other things in the next few weeks. There's also some pending updates to applications as well. Come back to visit and share when you can, enjoy!

---

### Post by Paresh on 2009-11-21
Hi TrackerJon

Great post, thanks for taking the time to update it, have some :popcorn:.

I noticed a typo: ```
sudo apt-get **install** fortune-mod fortunes-min librecode0
```
might trip some newbies.

Also, I think the 'modern' way to restart samba is ```
sudo service samba restart
``` but both work, so it's down to your preference.

Finally, is it worth mentioning **system-config-samba** as a simple gui tool for configuring samba shares?

---

### Post by TrakerJon on 2009-11-21
> **Paresh said:**
> Hi TrackerJon

Great post, thanks for taking the time to update it, have some :popcorn:.

I noticed a typo: ```
sudo apt-get **install** fortune-mod fortunes-min librecode0
```
might trip some newbies.

Also, I think the 'modern' way to restart samba is ```
sudo service samba restart
``` but both work, so it's down to your preference.

Finally, is it worth mentioning **system-config-samba** as a simple gui tool for configuring samba shares?


All very good points and I'll update accordingly, thanks! I gotta stop editing early in the morning hahaha.

---

### Post by Uncle Spellbinder on 2009-11-21
Incredible howto. Thanks so much. Many a newbie will be thrilled by such an easy to understand howto.

Well done!

Have one on me.....

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/Guinness.jpg[/IMG]

;)

---

### Post by wangsuda on 2009-11-21
Amazing guide, thank you! Your tips helped me learn how to use the command line. Again, thanks!

---

### Post by TrakerJon on 2009-11-21
> **Uncle Spellbinder said:**
> Incredible howto. Thanks so much. Many a newbie will be thrilled by such an easy to understand howto.

Well done!

Have one on me.....

;)


Yeah! Now that's what I'm talking about...a cold Guinness will modivate me to do just about anything. Glad you like it! Share when you can. :D

---

### Post by TrakerJon on 2009-11-21
> **wangsuda said:**
> Amazing guide, thank you! Your tips helped me learn how to use the command line. Again, thanks!

The command line is the best place to actually see what's going on and what additional options you may have...it's very powerful if used for good and not evil hahaha. Enjoy! ;)

---

### Post by egalvan on 2009-11-21
> **RJ12 said:**
> J This is about Karmic but why are you adding a reference to menu.lst for GRUB which in **Karmic is GRUB2 and dosent use menu.lst**? You might want to change or delete that part.




The default on a clean Karmic install is GRUB2.

But Karmic can be installed with GRUB Legacy **or** GRUB2.

---

### Post by TrakerJon on 2009-11-21
> **egalvan said:**
> The default on a clean Karmic install is GRUB2.

But Karmic can be installed with GRUB Legacy **or** GRUB2.

Agreed, unfortunately editing the menu settings on Grub2 probably isn't advisable or recommended for the average user as it may result in boot failures. Since Grub2 is installed by default on new installations of Karmic Koala I probably won't post on this topic.

---

### Post by VraiChevalier on 2009-11-21
Wicked good! Thank you very much. 

I just received a new Acer One netbook as a gift and installed Karmic netbook remix on it. I am liking the Karmic very much but the "maximus" was driving me crazy! Found the solution in short order right here.

Thanks again. Nice work.

---

### Post by TrakerJon on 2009-11-22
> **VraiChevalier said:**
> Wicked good! Thank you very much. 

I just received a new Acer One netbook as a gift and installed Karmic netbook remix on it. I am liking the Karmic very much but the "maximus" was driving me crazy! Found the solution in short order right here.

Thanks again. Nice work.

Glad I could help, maximus drove me "crazy" a few months back and thought there must be others having the same problem. Karmic works great on my MSI Netbook as well. Enjoy and share.

---

### Post by Digikid on 2009-11-22
Wow.  Bookmarked for sharing.  Well done.

---

### Post by TrakerJon on 2009-11-22
> **Digikid said:**
> Wow. Bookmarked for sharing. Well done.

Thank you, more to come, feel free to visit anytime or pass along the address.

---

### Post by egalvan on 2009-11-22
> **TrakerJon said:**
> Agreed, unfortunately editing the menu settings on Grub2 probably isn't advisable or recommended for the average user as it may result in boot failures. 

Yes, GRUB2 is very different from Legacy.
More files, and some that should not be edited directly.
I just wanted to point out that GRUB2 is not the ONLY option, and that Legacy will at times be used.

You may want to point this out.

And StartUpManager for GRUB2 is reported to be nearing completion.

> 
Since Grub2 is installed by default on new installations of Karmic Koala I probably won't post on this topic.

There are a few good tutorials on GRUB2, a link to one or two would be good.


Again,
 THANKS for a great HowTo!

---

### Post by egalvan on 2009-11-22
How about making this a PDF file, so it can be downloaded and perused offline?
Such as when installing a clean copy of Karmic?

I would find this VERY useful, and would be willing to donate $1 for my copy.
(as I have done for other articles I find useful)

---

### Post by Uncle Spellbinder on 2009-11-22
> **Digikid said:**
> Wow.  Bookmarked for sharing.

Same here. Also added it to my signature in the hopes it well help others. 



As a side note, I think a mod should make this thread a sticky thread.

---

### Post by TrakerJon on 2009-11-22
> **Uncle Spellbinder said:**
> Same here. Also added it to my signature in the hopes it well help others. 

As a side note, I think a mod should make this thread a sticky thread.


Well, it made it to the General Help section, maybe I'll get sticky status soon :D
Thanks for promoting my post, the more folks we can help the better.

Cheers!

- TrakerJon

---

### Post by TrakerJon on 2009-11-22
> **egalvan said:**
> Yes, GRUB2 is very different from Legacy.
More files, and some that should not be edited directly. I just wanted to point out that GRUB2 is not the ONLY option, and that Legacy will at times be used. You may want to point this out.

And StartUpManager for GRUB2 is reported to be nearing completion.

There are a few good tutorials on GRUB2, a link to one or two would be good.

Again,
THANKS for a great HowTo!


No worries, I knew where you were coming from. Grub2 is an overall improvement for the most part but it does further remove the end user from managing their own system which concerns me a little about the direction they're heading in this regard. I'll have to give some thought to your proposal about posting the links since it is an advanced topic that would probably only interest folks like us willing to hose up their system in the pursuit of knowledge. ;)

---

### Post by TrakerJon on 2009-11-22
> **egalvan said:**
> How about making this a PDF file, so it can be downloaded and perused offline? Such as when installing a clean copy of Karmic? I would find this VERY useful, and would be willing to donate $1 for my copy. (as I have done for other articles I find useful)

Good suggestion and well noted, I'll probably make one available sometime in the future after I've made some needed additions and revisions. Since the Ubuntu Forums are a valuable source of free and helpful information (as Ubuntu itself is) it would be my intention to make the .pdf as a gratis offering if posted. I'm all for an honest $1 but I do still believe the best things in life should be monetarily free. Spellbinder's virtual offer of a cold Guinness is more the kind of payment I'm looking for regarding my posts :D

---

### Post by TrakerJon on 2009-11-25
> **egalvan said:**
> How about making this a PDF file, so it can be downloaded and perused offline?
Such as when installing a clean copy of Karmic?

I would find this VERY useful, and would be willing to donate $1 for my copy.
(as I have done for other articles I find useful)

Just as an after thought, if you go to the red Tread Tools link at the top you can choose Show Printable Version for a graphics free reference when printing a hard copy. Cheers!

---

### Post by egalvan on 2009-11-25
> **egalvan said:**
> How about making this a PDF file, so it can be downloaded and perused offline?

I would find this VERY useful, and would be willing to [COLOR="Red"]donate[/COLOR] $1 for my copy.
(as I have done for other articles I find useful)

> **TrakerJon said:**
> Good suggestion and well noted,.
 the Ubuntu Forums are a valuable source of free and helpful information (as Ubuntu itself is)
 it would be **my intention to make the .pdf as a gratis offering if posted.**
 I'm all for an honest $1 but I do still believe the best things in life should be monetarily free.
 Spellbinder's virtual offer of a cold Guinness is more the kind of payment I'm looking for regarding my posts :D

I am a firm believer in Free, free, and gratis,
and FOSS/OSS, GPL, and Creative Commons.
Which is why I stated that it should be a [COLOR="Red"]DONATION[/COLOR].

BUT, I am also a firm believer in SHARING THE LOAD.
ESPECIALLY if one is making money off the work of others.

DONATING small amounts, such a $1, is a good way of being  TRUE UBUNTUAN.

I donate money to two web sites, and to several software authors, such as PartedMagic (subscription), AdBlock, etc.
Total per year is still far less than the old Microsoft tax, and I have better software to use and enjoy.

Unless a community supports its resources, those resources start to dry up, become less common.

Copyright apologists state that without copyright, there is no payment,
and without payment there is no art.
Hogwash.
A true artist will produce art...
paid or not, he will produce...
he has no choice, like breathing itself.
He must breathe, or die...
He must produce art, or die.

but just like good service in a restaurant, or elsewhere, 
a nice tip is always appreciated.

and a good artist should always be appreciated.


P.S.
AdBlock as already dropped one of its servers due to rising co$t$.
How long before more servers are dropped?
I use it.
I donated.

*Ext2 Installable File System For Windows*
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
has not been upgraded in over a year, and is un-usable in its current form for current Linux users.
 The authors can't afford to up-date? Who knows?
I use it.
I donated.

---

### Post by egalvan on 2009-11-25
> **TrakerJon said:**
> go to the red Thread Tools link you can choose Show Printable Version for a graphics free reference when printing a hard copy. Cheers!

hey great! I never knew that!
Thanks!

Now if the "convert to PDF" firefox ad-on still worked...

(it either states it cannot convert at this time, or simply never does anything. Probably totally overloaded)


An afterthought...

If I "print" this page to PDF, I get no indication of file location. :(
Where does the .pdf end up?
:(

---

### Post by audiomick on 2009-11-25
> **egalvan said:**
> hey great! I never knew that!
Thanks!

Neither did I. Thanks from me too. :p


```
If I "print" this page to PDF, I get no indication of file location. :(
Where does the .pdf end up?
:(

```
My home directory has a "PDF" folder in it that I am sure I didn't create by hand.
I would have called it something more intelligent, like "fred" maybe...;)
Mine land there

---

### Post by TrakerJon on 2009-11-25
> **egalvan said:**
> I am a firm believer in Free, free, and gratis,
and FOSS/OSS, GPL, and Creative Commons.
Which is why I stated that it should be a [COLOR="Red"]DONATION[/COLOR].

BUT, I am also a firm believer in SHARING THE LOAD.
ESPECIALLY if one is making money off the work of others.

DONATING small amounts, such a $1, is a good way of being  TRUE UBUNTUAN...

> **egalvan said:**
> I am a firm believer in Free, free, and gratis,
and FOSS/OSS, GPL, and Creative Commons. Which is why I stated that it should be a [COLOR="Red"]DONATION[/COLOR]. BUT, I am also a firm believer in SHARING THE LOAD. ESPECIALLY if one is making money off the work of others. DONATING small amounts, such a $1, is a good way of being  TRUE UBUNTUAN...

Whoa, I by no means meant offense by my comments. Everything you see in my post was either learned, acquired or contributed and I'm just passing it along collectively. It's just my way of giving back more than trying to claim original thought or conception. 

If you paste the printable version of this post into OpenOffice Word Processor (and adjust for aesthetics) it will save as as a pdf (toolbar option) for reference or emailing. I believe by default files in OpenOffice default to the Documents folder in your home directory. Cheers and Happy Thanksgiving!

-TrakerJon

---

### Post by egalvan on 2009-11-26
> **TrakerJon said:**
> Whoa, I by no means meant offense by my comments.
 Everything you see in my post was either learned, acquired or contributed and I'm just passing it along collectively.
 It's just my way of giving back more than trying to claim original thought or conception. 


And I took absolutely NO offense. Really :)
Your views and beliefs are admirable, as is you skill in explaining Linux things.
You enjoy this work.
It's good work.

So I see nothing wrong with donating a buck or two if I can get it as a PDF. 
I may be the only one in Ubuntu-land to think so... :)


> 
If you paste the printable version of the post into OpenOffice Word Processor (and adjust for page length)
 it will save as as a pdf if you would like one for reference or emailing.
 Cheers and Happy Thanksgiving!

-TrakerJon

---

### Post by egalvan on 2009-11-26
> **audiomick said:**
> 
```
If I "print" this page to PDF, I get no indication of file location. :(
Where does the .pdf end up?
:(

```
My home directory has a "PDF" folder in it that I am sure I didn't create by hand.
I would have called it something more intelligent, like "fred" maybe...;)
Mine land there

Nope, no .pdf print files in my home directory.
and since I don't know what the file name is, it's difficult to search for it.

Anybody with an idea on this?

---

### Post by Dinesh Balaji on 2009-11-26
i was lookin for a post like this..Million thanks and hugs!!:-)

---

### Post by nomnex on 2009-11-26
Can you install and run Wink on Karmic 32 bit without problem?

```
sudo apt-get install wink
```

---

### Post by TrakerJon on 2009-11-26
> **nomnex said:**
> Can you install and run Wink on Karmic 32 bit without problem?

```
sudo apt-get install wink
```

nomnex, if you look closely at the notes for this install...

Wink creates advanced tutorials and presentations.
sudo apt-get install wink

Note: ***Unfortunately Wink isn't available in the Karmic Koala repositories yet.***

Hopefully Satish will have an updated release for Karmic Koala out soon, I really like this program.

-TrakerJon

---

### Post by TrakerJon on 2009-11-26
> **Dinesh Balaji said:**
> I was lookin for a post like this..Million thanks and hugs! !:-)

Glad I could be of assistance, it's my pleasure to save folks time and effort searching for solutions. Don't let this post keep you from learning how things work on Linux though, it's meant to create a solid foundation to build up from so that you can experience and learn bigger and better things :D

---

### Post by audiomick on 2009-11-26
> **egalvan said:**
> Nope, no .pdf print files in my home directory.
and since I don't know what the file name is, it's difficult to search for it.

Anybody with an idea on this?

In applications> accessories> search for files ( or something similar. Mine is called ""dateien suchen" ;) )

type in ```
*.pdf
```

that will search for and list all the pdf files on the computer

the * means "any combination of characters", and is applicable for lots of other commands as well

---

### Post by Uncle Spellbinder on 2009-12-02
> **TrakerJon said:**
> **Media players, codecs, plug-ins and accessories** are needed for playing various multimedia formats.

**sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools freepats gstreamer0.10-gnomevfs liba52-0.7.4 libass3 libavcodec52 libavformat52 libavutil49 libcdaudio1 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfreebob0 libgsm1 libid3tag0 libiptcdata0 libjack0 libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmpcdec3 libmpeg2-4 libofa0 libopenspc0 libpostproc51 libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0 libtwolame0 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev jackd sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc jack-tools libjackasyn0 avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc easytag-aac faac faad ffmpeg ffmpeg2theora flac gxine icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmozjs0d libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1a mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 libamrnb3 libamrwb3 sox tagtool twolame vorbis-tools gecko-mediaplayer build-essential comerr-dev cpp-4.3 dpkg-dev g++ g++-4.3 g++-4.4 g++-4.4-multilib gcc-4.3 gcc-4.3-base gcc-4.3-multilib gcc-4.4-multilib gcc-multilib gettext gnome-mplayer guile-1.8 html2text intltool-debian ladspa-sdk lib64gcc1 lib64gomp1 lib64stdc++6 libao2 libaudio2 libavdevice52 libavifile-0.7c2 libc6-amd64 libc6-dev-amd64 libcurl4-gnutls-dev libdiscid0 libgcc1-dbg libgcrypt11-dev libggi-target-terminfo libggi-target-x libggi2 libgii1 libgii1-target-x libgnutls-dev libgpg-error-dev libgssrpc4 libidn11-dev libkadm5srv6 libkdb5-4 libkrb5-dev libldap2-dev liblrdf0 liblzo2-2 libmail-sendmail-perl libmpeg3-1 libmusicbrainz3-6 libopenal1 libqt3-mt libqt4-xml libqtcore4 libqtgui4 libraptor1-dev libreadline5 libstdc++6-4.3-dev libstdc++6-4.4-dev libsvga1 libsys-hostname-long-perl libtasn1-3-dev libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml2-dev libxslt1-dev mplayer-nogui mplayer-skins patch po-debconf qjackctl zlib1g-dev libdvbpsi5 libebml0 libiso9660-5 liblua5.1-0 libmatroska0 libsdl-image1.2 vlc libtar libvcdinfo0 libvlc2 libvlccore2 vlc-data vlc-nox vlc-plugin-pulse**

TrakerJon, my only suggestion on your fine work with *Ubuntu Desktop Computing Made Easy (Karmic 9.10)* would be to separate the above entry into three smaller entries:

Codecs and plug-ins
Media Players
Accessories

---

### Post by TrakerJon on 2009-12-03
> **Uncle Spellbinder said:**
> TrakerJon, my only suggestion on your fine work with *Ubuntu Desktop Computing Made Easy (Karmic 9.10)* would be to separate the above entry into three smaller entries:

Codecs and plug-ins
Media Players
Accessories

Well, that was done mainly for speed of installation but I do see your point. Unfortunately, that will require some real effort on my part (simply because there are so many shared dependencies and associated files that it will probably result in a lot of redundant file references in the post)...care to do that for me? :) 

Seriously though, I did think about that specific issue and after discussing it several folks...most of them tend to install most everything posted anyway. Again, good point, I don't want to load people up with stuff they won't use (nor do I want to leave a lot of useful stuff out either). I'll see what I can do on the next install in my test environment.

-TrakerJon

---

### Post by TrakerJon on 2009-12-14
The latest Audacious has been released, minor bugs have been fixed as far as I can tell. If you have problems with the plug-ins installing on the first try use **sudo apt-get -f install** to correct the issue then run **sudo apt-get install audacious**. Still no Wink, I realize it's not an Ubuntu supported open source application but it would be nice to have since it's been available in previous releases (Satish, dude, don't let us down). I've added the Transmageddon application (seems to work fairly well now) and GetDeb installation instructions have been updated on my post. I also added the files associated with Kaffeine (the icon can be gleaned from Wikipedia). All in all I've almost completed the post for now. Enjoy!

-TrakerJon

---

### Post by Musl1m on 2010-01-26
I'm having a problem with Xara Xtreme I've installed it through the Ubuntu Software Centre and it works fine except that there is no file menu in the application. Any help plz?

---

### Post by Uncle Spellbinder on 2010-02-06
Any plans on a howto like this for Lucid, once it's released?

---

### Post by wangsuda on 2010-02-06
> **Uncle Spellbinder said:**
> Any plans on a howto like this for Lucid, once it's released?
Wouldn't most of the code stay the same?

---

### Post by TrakerJon on 2010-02-15
> **Uncle Spellbinder said:**
> Any plans on a howto like this for Lucid, once it's released?

Probably, most likely there will be some changes as things progress. I'm looking forward to the upcoming release as I'm sure a lot of other folks are...still no Wink for the current release, that would sure come in handy for tutorials regarding Lucid.

---

### Post by TrakerJon on 2010-02-15
> **Musl1m said:**
> I'm having a problem with Xara Xtreme I've installed it through the Ubuntu Software Centre and it works fine except that there is no file menu in the application. Any help plz?

I would try installing it from a command line (always the best way) after un-installing with the --purge option. 

**sudo apt-get remove <packagename> --purge**

**sudo apt-get install xaralx libwxbase2.6-0 libwxgtk2.6-0 xaralx-svg xaralx-examples**

---

### Post by wangsuda on 2010-02-25
I hope you don't mind me adding my two cents worth, but I thought I would recommend a program called PDF Shuffler. If you want a simple program for editing PDF binders, combining various PFDs into one binder, or merging PDF binders, then PDF Shuffler is for you! More information, screenshots, and download information can be found at [http://sourceforge.net/projects/pdfshuffler/](http://sourceforge.net/projects/pdfshuffler/)

---

### Post by TrakerJon on 2010-02-28
> **wangsuda said:**
> I hope you don't mind me adding my two cents worth, but I thought I would recommend a program called PDF Shuffler. If you want a simple program for editing PDF binders, combining various PFDs into one binder, or merging PDF binders, then PDF Shuffler is for you! More information, screenshots, and download information can be found at [http://sourceforge.net/projects/pdfshuffler/](http://sourceforge.net/projects/pdfshuffler/)

Thanks for the suggestion, I'll check it out and may very well add it after some general testing.

---

### Post by daethyme on 2010-03-13
Yeah, what they said, I really thank you for your passion and knowledge. I'm new to all of this but I'm no longer using my Vista part, except at work sometimes. I'm learning how to do everything I need to do on open source and you've helped me make a large step in that direction. This **** rocks!

---

### Post by TrakerJon on 2010-03-21
> **daethyme said:**
> Yeah, what they said, I really thank you for your passion and knowledge. I'm new to all of this but I'm no longer using my Vista part, except at work sometimes. I'm learning how to do everything I need to do on open source and you've helped me make a large step in that direction. This **** rocks!

_________________________________________________________________

Glad you like it...I'll be doing a post for the next release as well. Cheers!

Traker

---

### Post by Keith1212 on 2010-03-23
great guide thanks.

---

### Post by TrakerJon on 2010-04-21
> **Keith1212 said:**
> great guide thanks.

My pleasure, check back from time to time, things do change. I just made some updates that were brought to my attention in reference to a proposed kernel update and an outage at the primary Medibuntu repository.

Regards,

TrakerJon

---

### Post by TrakerJon on 2010-05-04
Ubuntu Desktop Computing Made Easy (Lucid 10.04) has now been posted in the Ubuntu General Help Forum. Enjoy!

[http://ubuntuforums.org/showthread.php?t=1469825]("http://ubuntuforums.org/showthread.php?t=1469825")

TrakerJon

---

