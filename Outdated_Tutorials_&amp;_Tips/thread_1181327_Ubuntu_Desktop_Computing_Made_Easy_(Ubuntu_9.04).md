---
title: "Ubuntu Desktop Computing Made Easy (Ubuntu 9.04)"
date: 2009-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by TrakerJon on 2009-06-07
This documentation is intended for folks that would like to add additional programs and applications to their Ubuntu Jaunty Jackalope installation (Karmic Koala can be found at [http://ubuntuforums.org/showthread.php?t=1310795]("http://ubuntuforums.org/showthread.php?t=1310795")) for a better overall experience. Please keep in mind older computers may have video performance issues due to high CPU usage and increased memory requirements.

Recommended: Pentium 4 or higher processor with 1Gb SDRAM, 256Mb graphics card, 10/100 Ethernet card and 20Gb hard disk. 

The easiest way to perform most of these installs is to copy and paste from this post into a terminal window (found in Accessories). I strongly suggest installing a few things at a time, testing each along the way.

**Start by going to System > select Administration > select Software Sources > Check all the boxes under the Ubuntu Software, Third-Party Software and Updates tabs > Close and Reload**

Get all the available Ubuntu updates at this point, look for the update notification icon on the task bar. Reboot after updating your system and then install as many of the following as you wish.

If you're having slowness issues with the default repository go to System > select Administration > select Software Sources > Ubuntu Software tab > Download from: drop down menu > select Other > click Select Best Server and  when it finishes the query click Choose Server > Close and Reload.

Many of these installations require access to the Medibuntu Repository and enabling some additional software sources. Directions are on this site: **[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)** or if you have Ubuntu 9.04 "Jaunty Jackalope" simply do the following from a terminal window:

**sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list**

**sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update**

Codecs and plug-ins are needed for playing various multimedia formats (try this method if you've experienced issues with ubuntu-restricted-extras).
**sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-plugins-farsight gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools**

Install these as well (some may already be installed at this point, no worries)
**sudo apt-get install realplayer w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev jackd sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc jack-tools libjackasyn0 avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc**

Last but not least...
**sudo apt-get install easytag-aac faac faad ffmpeg ffmpeg2theora flac gxine icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmozjs0d libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1 mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 libamrnb3 libamrwb3 sox tagtool toolame vorbis-tools gecko-mediaplayer**

Install some fonts.
**sudo apt-get install msttcorefonts mplayer-fonts ttf-xfree86-nonfree xfs**

Adobe Flash too&#8230;
**sudo apt-get install flashplugin-nonfree**

Install the latest Sun Java JRE
**sudo apt-get install gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin unixodbc**


**ATI and Nvidia Drivers and Desktop Effects**

This requires some effort on the part of the user to know exactly what graphics card they have installed, use with caution and please read all applicable instructions or notes along the way.

Ubuntu 9.04 Jaunty Jackalope comes with a Nouveau display graphic driver by default and the advanced effects cannot be used. If you've already tried to enable restricted Ubuntu drivers and ATI/nVidia cannot be found in the list try installing the ATI/nVidia driver with this tutorial:

1. Run Applications/Add/Remove
2. From the left menu choose System Tools
3. Next from the right menu, find and select for install: Desktop Effects (Compiz Setup) and ATI/Nvidia binary X.org Driver (nVidia could be version 173 or 177). Selecting the driver will get the list of supported graphics cards.
4. Click Apply Changes and after installation go to System/Administration/Hardware Drivers
5. The system will search for available drivers, choose the recommended option from the list and activate the driver by clicking Activate.
6. Restart your system and the new ATI/nVidia graphic display driver will be in use.

*Unsupported* updated versions of X.org drivers, libraries, etc. for Ubuntu **[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")**
Note: Import the key and add the repositories for your specific distribution in System > Administration > Software Sources then run **sudo apt-get update** from a terminal window.


**Compiz, Emerald and Screenlets**

The default Ubuntu display setup lets you choose from None, Normal or Extra. Make it a lot more configurable with the CompizConfig Settings Manager...found in System > Preferences after installing the following:
**sudo apt-get install compizconfig-settings-manager gnome-art usplash startupmanager compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald screenlets librsvg2-common fusion-icon**

Notes: Make sure you enable Visual Effects "**Extra**" (right click on your desktop, choose change Desktop Background and click on the Visual Effects tab) before adusting Compiz settings. Reset Compiz defaults by going into CCSM > Preferences > Profile & Backend > Click Reset to defaults.


Various media players (Audacious, Amarok, Kaffeine and VLC) (install realplayer w32codecs libxine1-ffmpeg and libdvdcss2 first).
**sudo apt-get install audacious amarok kaffeine vlc** 

Notes: In order to open .m3u files with Audacious set Nautilus (preferences -> behavior tab) to always "view" the file and not ask.

Additional Notes: In Kaffeine be sure to verify the decoder references under Settings and xine Engine Parameters to reflect the correct paths to Realplayer, Win32 codecs and your DVD drive. I ran into a folder permissions issue in my home folder when launching kaffeine, if you experience this issue very carefully use the following commands from a terminal window:
**sudo chown -R username:username ~/.kde** (put in *your* "username")
**sudo chmod -R 700 ~/.kde**


Ardour, SoundKonverter, Jokosher and AcidRip for multimedia recording, editing, conversions, mixing, etc.
**sudo apt-get install ardour soundkonverter jokosher lmms acidrip**

K9Copy, K3b and DeVeDe when you need DVD, CD, VCD and VCD software (requires libdvdcss2)
**sudo apt-get install k9copy k3b devede**

**Transmageddon** supports almost any format as its input and can generate a very large host of output files.
[http://www.getdeb.net/software/Transmageddon](http://www.getdeb.net/software/Transmageddon)

Note: Follow the instructions for "How to Install Apps from GetDeb" first before attempting to install Transmageddon.
**[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)**

Streamripper will allow you to download internet radio station broadcasts (Streamtastic is the java gui for Streamripper).
**sudo apt-get install streamripper**

**Streamtastic** is the java based gui for Streamripper.
Download the stable version from **[https://code.launchpad.net/streamtastic/+download]("https://code.launchpad.net/streamtastic/+download")**

Notes: Install Streamripper and then create a folder in your home directory called Streamtastic. Create a sub folder of Streamtastic called downloads. Download Streamtastic and extract the files into the Streamtastic folder. Launch the Streamtastic.sh file from a command prompt (user@ubuntu-desktop:~/Streamtastic$ ./Streamtastic.sh) and when prompted point the download destination to your downloads folder. Select the station you would like to listen to and right-click on the reference to play and/or record. You can play and record at the same time, you'll be prompted to select a player (if you've installed amarok or vlc they're in /usr/bin). The configuration file to change the path to your preferences can be found in the hidden .streamtastic folder in your home directory. 
If you have folder permissions issues do the following:
**sudo chown -R username:username ~/Streamtastic** (put in *your* "username")
**sudo chmod -R 700 ~/Streamtastic**

**Shoutcast** is a good place to shop for internet radio stations. **[http://www.shoutcast.com/](http://www.shoutcast.com/)**


**P2P (peer to peer) clients**
 
Gnutella is a lot like Limewire or Morpheus (see Firewalls and avast! sections below before using).
**sudo apt-get install gtk-gnutella**

Vuze can be handy for things not found with Gnutella (see Firewalls and avast! sections below before using).
**sudo apt-get install vuze**

**Frostwire** is similar to Gnutella (see Firewalls and avast! sections below before using).
**[http://www.getdeb.net/software/Frostwire](http://www.getdeb.net/software/Frostwire)**

Note: Follow the instructions for "How to Install Apps from GetDeb" first before attempting to install FrostWire.
**[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)**


**AceoneISO2** is a CD/DVD image manipulator for Linux (used primarily with .iso files).
[http://www.getdeb.net/software/AcetoneISO](http://www.getdeb.net/software/AcetoneISO)

Note: Follow the instructions for "How to Install Apps from GetDeb" first before attempting to install AceoneISO2.
**[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)**

Various compression/extraction and encoding/decoding utilities...
**sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils aish uudeview mpack lha arj cabextract file-roller**

**avast!** makes a very good anti-virus product for Linux it can be downloaded free for home use from **[http://avast.com/eng/download-avast-for-linux-edition.html](http://avast.com/eng/download-avast-for-linux-edition.html)** You'll need the home user free registration key (emailed to you from their site). The key can be pasted into a terminal window after you type avast at a terminal command prompt. The gui icon is located in Applications > Accessories. Update the program frequently and scan all questionable downloads.


Thunderbird, Sunbird and SpamAssassin for email and integrated calendar.
**sudo apt-get install thunderbird sunbird lightning-extension spamassassin**

Setup your Gmail, Yahoo, AOL, Hotmail accounts in Thunderbird (use POP port 1024)
**[http://webmail.mozdev.org/index.html](http://webmail.mozdev.org/index.html)**

Skype lets you talk and chat with friends all over the world.
**sudo apt-get install skype**

Note: You might have to configure your Options > Sound Devices > Sound In/Sound Out within Skype and test with the Echo/Sound test Service. I also had to enable and adjust my Ubuntu Volume Controls > Preferences > Mic and Mic Boost settings.

Fonts, fonts and more fonts...for use in a variety of word processing applications (pick and choose).
**sudo apt-get install ttf-larabie-straight ttf-larabie-deco xfonts-terminus-dos xfonts-terminus xfonts-terminus-oblique xfonts-mona tv-fonts ttf-tuffy ttf-sjfonts ttf-georgewilliams ttf-fifthhorseman-dkg-handwriting ttf-essays1743 ttf-opensymbol ttf-mgopen ttf-freefont ttf-dustin ttf-dejavu-extra ttf-dejavu-core ttf-dejavu ttf-bpg-georgian-fonts ttf-bitstream-vera equivs ttf-sil-gentium gnome-specimen**

Note: Postfix is related to some of these fonts, be careful not to modify your Postfix configurations if you're using it for email purposes, otherwise use no configuration setting if/when prompted.

I typically don&#8217;t use the Arabic and Asian fonts, to remove them from a terminal window type: 
**sudo apt-get remove ttf-kochi-mincho ttf-kochi-gothic ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ttf-unfonts-core ttf-indic-fonts-core ttf-wqy-zenhei**

Note: Add them by simply using install instead of remove.

**HP printer driver issues? [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)**

Adobe still makes one of the best .pdf viewers.
**sudo apt-get install acroread acroread-fonts**

PDFedit is editor for manipulating PDF documents.
**sudo apt-get install pdfedit**

AbiWord is a fast and easy to use word processing program similar to Microsoft® Word.
**sudo apt-get install abiword**

gLabels is a program for creating labels and business cards for the GNOME desktop environment.
**sudo apt-get install glabels**

iSpell comes in handy when spell checking documents from a terminal window
**sudo apt-get install ispell**

Wordnet is a comprehensive word database maintained by Princeton University
**sudo apt-get install wordnet**

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

Inkscape for illustrations.
**sudo apt-get install inkscape**

Gimp is an incredible image editing application.
**sudo apt-get install gimp gimp-data-extras gimp-gap gimp-plugin-registry**

Xara Xtreme is a user friendly vector graphics drawing program.
**sudo apt-get install xaralx**

Blender is open source software for 3D modeling, animation, rendering, interactive creation and playback.
**sudo apt-get install blender**

**webKam** is simple webcam application **[http://code.google.com/p/webkam-kde4/downloads/list](http://code.google.com/p/webkam-kde4/downloads/list)**

**Elltube** is a YouTube downloader and converter **[http://elltube.sourceforge.net/download](http://elltube.sourceforge.net/download)**

A complete Web Authoring System for Linux desktop users to rival programs like FrontPage and Dreamweaver.
**sudo apt-get install kompozer**

If you program in C\C++ languages you&#8217;ll need Build-Essential packages.
**sudo apt-get install build-essential **

Geany is a fast and lightweight IDE (Integrated Development Environment) for programming in various languages.
**sudo apt-get install geany**

**Eclipse** is an awesome open-source IDE for Java, C/C++ and Python. 
**[http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/]("http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/")**
If you are unfortunate enough to develop apps in C/C++ (like me) this link should help as well... **[http://www.eclipse.org/cdt/downloads.php]("http://www.eclipse.org/cdt/downloads.php")**

Note: The Eclipse version available from the Ubuntu repositories is seriously outdated and has known issues...so no apt-get install if you want the latest and greatest.

Vim, Gvim and Cream may come in handy for file editing (gedit works good too).
**sudo apt-get install vim-full vim-doc cscope vim-gnome tcl8.4 vim-gui-common vim-runtime tclreadline cbrowser cream**
 
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

Wink creates advanced tutorials and presentations.
**sudo apt-get install wink**

Glipper is a clipboard manager for the GNOME panel.
**sudo apt-get install glipper**

Note: If Clipboard manager does not appear in the panel applet menu, in a terminal window cd /usr/lib/glipper then run ./glipper It should allow you to add it as a panel applet at this point. The keyboard shortcut is <Ctrl><Alt>c

GNOME Commander is a "two-pane" graphical filemanager for the Gnome desktop environment. 
**sudo apt-get install gnome-commander**

Add some useful features to nautilus...
**sudo apt-get install nautilus-actions nautilus-gksu nautilus-image-converter nautilus-open-terminal nautilus-script-audio-convert nautilus-script-collection-svn nautilus-script-manager nautilus-sendto nautilus-share nautilus-wallpaper**

NTFS Configuration Tool mounts NTFS drives (2000/XP/2003/Vista).
**sudo apt-get install ntfs-config**
**gksudo ntfs-config**

Note: Found in System > Administration.

**luckyBackup**...a powerful, fast and reliable backup & sync tool **[http://luckybackup.sourceforge.net/download.html](http://luckybackup.sourceforge.net/download.html)**

Partimage system backup, instructions can be found at: **[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)**
**sudo apt-get install partimage**

KDE Partition Manager allows you to manage your disks, partitions and file systems:
**sudo apt-get install partitionmanager**

GParted is the GNOME partition editor for creating, reorganizing and deleting disk partitions. 
**sudo apt-get install gparted**

Note: Documentation can be found at **[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)**

**Reconstructor** will help you create your own Ubuntu based distribution **[http://www.reconstructor.org/wiki/reconstructor](http://www.reconstructor.org/wiki/reconstructor)**

**Defrag** (or fidefrag I should say)

**sudo apt-get install bzr python-psyco**
**bzr branch lp:fidefrag**
**cd fidefrag/src**
**sudo python fidefrag.py -d /<directory name>**

Note: It's not a good idea to defrag your whole system, some directories won't react very well. I typically defrag /usr (this one takes a long time), /var, /lib, /home, /etc, /bin and /sbin

**Google Earth** install: **[http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)**

**Show wallpaper or background color while logging in to Ubuntu**: **[http://ubuntuforums.org/showthread.php?t=753261](http://ubuntuforums.org/showthread.php?t=753261)**

Rainy days or a lot of time to kill?
**sudo apt-get install frozen-bubble**

Kids in the house?
**sudo apt-get install gcompris gcompris-sound-en tuxpaint gnucap**


**Firewalls** 

Internet security is important these days and firewalls can be quite complex, hopefully the following will help...use only one of these two applications and please read all of the documentation first. Most people are already behind a broadband router configured to give you "TruStealth" protection on the internet...check your current protection at the Sheilds Up! link below before being too concerned.

**ufw** ("uncomplicated firewall" included with Ubuntu), by default is set to "allow" all network traffic, the wiki instructions are at **[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)** then **sudo ufw enable** the firewall at system startup.

Personally I would rather use the gui interface for ufw... 
**sudo apt-get install gufw**
 
**Firestarter** is quite easy to configure **[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)**
**sudo apt-get install firestarter**

Load Firestarter at startup: [http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html](http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html)
Note: In nano the ^ is the Ctrl key on most keyboards [http://mintaka.sdsu.edu/reu/nano.html](http://mintaka.sdsu.edu/reu/nano.html)

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


**The Jaunty wiki** can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)**

**Ubuntu 8.10** (Intrepid Ibex) **How-To [http://www.funnestra.org/ubuntu/intrepid/](http://www.funnestra.org/ubuntu/intrepid/)**

**The UNR (Ubuntu Netbook Remix) wiki is here [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)**

**The Ubuntu Pocket Guide** can be found at **[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)**

**Ubuntu Desktop Essentials [http://www.techotopia.com/index.php/Ubuntu_Desktop_Essentials](http://www.techotopia.com/index.php/Ubuntu_Desktop_Essentials)**

**Best 100** Open Source Applications **[http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/](http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/)**

**Best 50** Ubuntu Opensource Applications For Design And Developing **[http://www.emmaalvarez.com/2007/12/top-best-50-ubuntu-opensource.html](http://www.emmaalvarez.com/2007/12/top-best-50-ubuntu-opensource.html)**

**GetDeb** software site for Ubuntu and Debian [**http://www.getdeb.net/**]("http://www.getdeb.net/")

**Gnome Desktop software** site [**http://www.gnomefiles.org/**]("http://www.gnomefiles.org/")

**KDE-Apps.org [http://www.kde-apps.org/](http://www.kde-apps.org/)**

**Ubuntu PPA Search [https://edge.launchpad.net/ubuntu/+ppas](https://edge.launchpad.net/ubuntu/+ppas)**

**Ubuntu Games [https://help.ubuntu.com/community/Games](https://help.ubuntu.com/community/Games)**

**Cool wallpaper and more [http://www.kde-look.org/](http://www.kde-look.org/)**


**Procedure to enable WPA Wireless in Ubuntu**

Sometimes wireless adapters (usually internal ones) don&#8217;t want to work right after the initial Ubuntu operating system install, even if the system recognises the hardware. The following should help if you&#8217;re in that situation.

If you have wired Internet connectivity update the software sources list **sudo apt-get update**

**sudo apt-get install wpasupplicant** (may already be installed)

**sudo apt-get install network-manager-gnome network-manager** (may already be installed)

**sudo gedit /etc/network/interfaces** Comment out the lines without &#8220;lo&#8221; entries (using #) and save the file, if you have just installed Ubuntu this may not be necessary.

Create a file by: **sudo gedit /etc/default/wpasupplicant**, **add entry ENABLED=0** and save the file.

**sudo touch /etc/default/wpasupplicant**

**Reboot your system.**

When prompted to connect to a wireless network, select the desired one and enter in the key if necessary.


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
**sudo apt-get install samba samba-common samba-tools smbclient swat samba-doc samba-doc-pdf smbfs libpam-smbpass libsmbclient libsmbclient-dev winbind samba-dbg libwbclient0 smbldap-tools ldb-tools keyutils**

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


**Web based workstation and application administration**

**webmin and usermin** can be found at **[http://www.webmin.com/index.html](http://www.webmin.com/index.html)**


**CommuniGate Pro** 

CommuniGate Systems' goal is to consolidate all forms of Internet Communications into one address space, making the single address for email, IM, VoIP and video calling, more productive, portable, and independent of tariffs and tolls of closed network topologies. **[https://www.communigate.com/forms/cgp_try_before_you_buy.php](https://www.communigate.com/forms/cgp_try_before_you_buy.php)**


**Editing /boot/grub/menu.lst to change the GRUB boot menu**

The GRUB boot menu configuration is in the file
/boot/grub/menu.lst

1. backup menu.lst:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup

2. edit menu.lst:
sudo gedit /boot/grub/menu.lst

***Do not skip the first step*** (i.e. backing up the original menu.lst file). 

If you completely hose up your or menu.lst file to the point that your machine won&#8217;t boot, you can fix it by booting in recovery mode (or from a live CD) and then copying your menu.lst-backup to menu.lst overwriting the existing one. In fact, try this method whenever you do something to your system making it unusable.


**Alternative shells for Linux**...

C, K, T, Z & Fish shells
**sudo apt-get install csh ksh tcsh zsh fish**

**Bash Reference Manual [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)**

**chmod calculator [http://www.javascriptkit.com/script/script2/chmodcal.shtml](http://www.javascriptkit.com/script/script2/chmodcal.shtml)**


**Adding a Personal Package Archive (PPA) to your Ubuntu repositories**

Adding a PPA to Ubuntu takes no more than a couple of minutes.

**Step 1**: Copy the lines from the apt sources.list entries section of the PPA overview page. For example:

deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) jaunty main

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

**OpenOffice**
**deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 247D1CFF**

**VideoLAN Client (VLC)**
**deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) jaunty main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D**

**Compiz**
**deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 42C24D89**

**Shutter**
**deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) jaunty main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 009ED615**

**FireFox**
**deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main** 
**deb-src [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C713DA6**

**X Updates** 
**deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main** 
**deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main** 

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9**

**Wine**
**deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) jaunty main** 
**deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) jaunty main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9CB8DB0**


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


Ok, about **wine**...in most cases a free to use Linux program will work just as well as apps on that other well known operating system. I don't recommend it but for the folks that want to use wine this wiki should help **[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)**

**Three Ways to Install Latest Wine in Ubuntu 9.04 Jaunty Jackalope [http://www.wine-reviews.net/wine-reviews/news/three-ways-to-install-latest-wine-in-ubuntu-904-jaunty-jackalope/print.html](http://www.wine-reviews.net/wine-reviews/news/three-ways-to-install-latest-wine-in-ubuntu-904-jaunty-jackalope/print.html)**

**Wine Application Database (AppDB) [http://appdb.winehq.org/](http://appdb.winehq.org/)**


To my friends...

I'm more than willing to add your suggestions and reference your favorite applications, this is your post as much as mine. I do ask that you keep it brief and on a general level while making it so the average person can use the topic or application quite readily. I started posting "Ubuntu Desktop Computing Made Easy" a while back (Gutsy Gibbon) mainly out of the personal frustration I had getting my workstation and personal computer to perform as expected (without hours upon hours of setup, search and configuration). It's my goal to make it "easy" for anyone to setup an Ubuntu Desktop Computer with everything they need or want ensuring the overall experience an enjoyable one.

Note: This post can be found very quickly by doing a Google search on Ubuntu Desktop Computing Made Easy.

Regards,

-TrakerJon

Dell GX270 3.2GHz Pentium 4 w/ 2Gb SDRAM using NVIDIA GeForce 6200 AGP video and MSI Wind Netbook U100 1.6GHz Intel Atom w/ 2Gb SDRAM using Intel Mobile 945GME Express video on Ubuntu 9.04

---

### Post by ACMiller on 2009-07-05
Absolutely brilliant. Thanks for putting the time and effort into making this, it's a great help and source of info to point people to. Thanks.

---

### Post by TrakerJon on 2009-07-09
> **ACMiller said:**
> Absolutely brilliant. Thanks for putting the time and effort into making this, it's a great help and source of info to point people to. Thanks.

Glad to do it, please share with others.

---

### Post by unlimitedz on 2009-07-10
This is great, does anyone know of a similar write-up for 8.10?

---

### Post by TrakerJon on 2009-07-11
> **unlimitedz said:**
> This is great, does anyone know of a similar write-up for 8.10?

Everything you see should work for Intrepid 8.10 just make sure any repositories listed reflect that distribution and not Jaunty...and don't forget to share with friends.

---

### Post by aimwin on 2009-07-11
Dear Sir

Something wrong somewhere in your tutorial.

I use Ubuntu9.04+Edubuntu9.04+Remix I try to do more update according to your tutorial.

UMMMM Yes I end up with black screen and nothing else when I reboot.
Not after the first few instructions. But later parts.

I end up have to reinstall clean Ubuntu 9.04 and Education pack.

So your instruction had mess my Ubuntu 9.04.

Lucky I kept all my data in another Drive - Ntfs.
So I did not loose any data.

Good Luck for anyone else to try.

---

### Post by tad1073 on 2009-07-11
This must have taken you months to compile. Excellent work...

---

### Post by Jonae on 2009-07-12
Thanks for sharing with us.

---

### Post by TrakerJon on 2009-07-12
> **aimwin said:**
> Dear Sir

Something wrong somewhere in your tutorial. I use Ubuntu9.04 + Edubuntu9.04 + Remix I try to do more update according to your tutorial. UMMMM Yes I end up with black screen and nothing else when I reboot. Not after the first few instructions. But later parts...


aimwin, please tell me some things about your computer (make, model, etc.). If you're installing graphics drivers incompatible with your system it can cause problems. I'll be glad to assist you if possible but I need a little bit more from you than a random comment stating something isn't right. ;) 7-12-09

aimwin, I installed the edubuntu add-on pack on three different computers and found no issues with the software and without a response from you I can only believe that you either mistyped some commands or installed graphics drivers incompatible with your system. 7-18-09

Traker

---

### Post by TrakerJon on 2009-07-12
> **tad1073 said:**
> This must have taken you months to compile. Excellent work...

Glad to do it my friend, please share with others.

---

### Post by TrakerJon on 2009-07-12
> **Jonae said:**
> Thanks for sharing with us.

My pleasure and my passion, please pass it along to friends and acquaintances.

---

### Post by PureLoneWolf on 2009-07-13
Superb guide, although I would mention "Lightning" as it is Sunbird that integrates with Thunderbird properly.

```
sudo apt-get install lightning-extension
```

For anyone interested.

:D

---

### Post by TrakerJon on 2009-07-13
> **PureLoneWolf said:**
> Superb guide, although I would mention "Lightning" as it is Sunbird that integrates with Thunderbird properly.

```
sudo apt-get install lightning-extension
```

For anyone interested.

:D

Thank you, I'll add it to the post right away.

---

### Post by crownedzero on 2009-07-16
Wow, it's going to take me weeks to go through all of this. Greatly appreciated!

---

### Post by Leibrockoli on 2009-07-16
Really awesome thread. I just installed 9.04 today, and this thread really helped me out.

Thanks a whole lot!

---

### Post by TrakerJon on 2009-07-17
> **crownedzero said:**
> Wow, it's going to take me weeks to go through all of this. Greatly appreciated!

LOL nooo it should only take about two or three hours, enjoy!

---

### Post by TrakerJon on 2009-07-17
> **Leibrockoli said:**
> Really awesome thread. I just installed 9.04 today, and this thread really helped me out.

Thanks a whole lot!


Glad I could help, remember to share with friends. If you have anything you would like to see added I'll be glad to test it out before posting.

---

### Post by Ziggy72 on 2009-07-20
Thank you very much for this. It's really appreciated!

---

### Post by Man Eating Duck on 2009-07-21
Wow, gotta join the choir of praise here. Thanks a lot, TrakerJon, post of the year!

I usually get around to this level of completeness about two weeks after installation, now I spent three minutes picking and choosing everything into a humongous command line and about seven minutes waiting for the install :)
You even indicated a cople of utilities I didn't know about despite having used ubuntu since dapper.

The only ones I missed was wine (well...) and gqview, otherwise I can't think of anything.

---

### Post by BLTicklemonster on 2009-07-21
Looks for "thank you" button...

Oh well.

Thank you.

---

### Post by fleton on 2009-07-21
Amazing post, thank you :D

---

### Post by ubuntizer on 2009-07-21
Thanks a lot. Great Post. \\:D/

---

### Post by TrakerJon on 2009-07-23
> **Man Eating Duck said:**
> Wow, gotta join the choir of praise here. Thanks a lot, TrakerJon, post of the year!

I usually get around to this level of completeness about two weeks after installation, now I spent three minutes picking and choosing everything into a humongous command line and about seven minutes waiting for the install :)
You even indicated a cople of utilities I didn't know about despite having used ubuntu since dapper.

The only ones I missed was wine (well...) and gqview, otherwise I can't think of anything.

You hit on my primary reason for the post...I found it had become a long drawn out process to simply help myself or someone else out with a new install without going back several times to add things that were missing. This cuts the time down a great deal and sharing it with others seems to make it easier for them as well. I'm glad everyone replying appreciates the effort, bookmark the page as I will be making periodic updates and additions...and of course share with friends....with any luck Canonical with start releasing a DVD with most of these packages available upon install. :D

---

### Post by TrakerJon on 2009-07-23
> **ubuntizer said:**
> Thanks a lot. Great Post. \\:D/

Glad you guys are getting some use out of it...it sure helps me in a rush.

---

### Post by TrakerJon on 2009-07-23
> **Ziggy72 said:**
> Thank you very much for this. It's really appreciated!

No problem Ziggy...I really enjoy Ubuntu as you can probably tell. Share with other folks when you can :D

---

### Post by Old_Grey_Wolf on 2009-07-26
TrakerJon,

Nice job.

I have a USB thumb drive I use when setting up new installs of Linux. I have wallpapers, themes, compiz setting, and other stuff saved on it. I was slowly building a file with instructions similar to what you posted. Thanks, you saved me some time. I copied your post and saved it to the USB thumb drive.

---

### Post by keldai on 2009-07-26
very useful..
thx for sharing

---

### Post by TrakerJon on 2009-07-26
> **Old_Gray_Wolf said:**
> TrakerJon,

Nice job.

I have a USB thumb drive I use when setting up new installs of Linux. I have wallpapers, themes, compiz setting, and other stuff saved on it. I was slowly building a file with instructions similar to what you posted. Thanks, you saved me some time. I copied your post and saved it to the USB thumb drive.

I use a USB drive for my Netbook Remix install, it's very useful I agree. I'm trying to avoid writing a wiki  since there are folks far better at doing it than me. What I hopefully can accomplish over time is a quick guide (in a somewhat loose organizational scheme) to make it easy for folks to get what they need faster after an install...or maybe simply provide things they didn't know about, have forgotten or quite possibly overlooked. Thanks for the compliment and please share with a friend or three.

---

### Post by TrakerJon on 2009-07-26
> **keldai said:**
> very useful..
thx for sharing

Party on friend...share with your buds.

---

### Post by TrakerJon on 2009-07-31
Be sure to check back for frequent additions and updates.

-Traker

---

### Post by harrykar on 2009-08-13
> **TrakerJon said:**
> Be sure to check back for frequent additions and updates.

-Traker

How many media libraries! Only take a glance on their descriptions is IMHO useful. Very good job my compliments:). Keep it highly updated

PS:
Maybe would be better for newbies if you mention that[INDENT] 1. ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```command produce a fisiological WARNING: 
```
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]?
```and the user must respond: y

2. **gstreamer0.10-pitfdll **is not found by Synaptic

3.**w32codecs** (w64codecs for amd64 systems) is part of* medibuntu's*** non-free-codecs** package

4. **avifile-win32-plugin **is not found by Synaptic

5. Instead of **easytag **maybe is better**easytag-aac **(for MP4/AAC too)[/INDENT]

---

### Post by TrakerJon on 2009-08-17
> **harrykar said:**
> How many media libraries! Only take a glance on their descriptions is IMHO useful. Very good job my compliments:). Keep it highly updated

PS:
Maybe would be better for newbies if you mention that[INDENT] 1. ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```command produce a fisiological WARNING: 
```
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]?
```and the user must respond: y

2. **gstreamer0.10-pitfdll **is not found by Synaptic

3.**w32codecs** (w64codecs for amd64 systems) is part of* medibuntu's*** non-free-codecs** package

4. **avifile-win32-plugin **is not found by Synaptic

5. Instead of **easytag **maybe is better**easytag-aac **(for MP4/AAC too)[/INDENT]


You have a point on # 1. but that's pretty much a given, either you want the key to the repository or not...don't you think?

On # 2 & 4 you might want to change your repository references to point to the main Canonical server, these are readily available on most mirrors as well.

This post is geared towards 32 bit systems (since most folks have them) but thanks for the 64 bit reference in # 3.

Good suggestion on # 5, will add it now.

- Traker

---

### Post by TrakerJon on 2009-08-17
> **chang_m33 said:**
> Nice documentation. Thanks

You're very welcome, please share with others whenever possible.

- Traker

---

### Post by ramesh20033 on 2009-08-18
I have just installed Ubuntu9.04 in my computer and Trakerjon"s excellent tutorial has comein handy to me.Thanks a lot Trakerjon for the excellent tutorial.

Regards
Ramesh

---

### Post by Crystal Visions on 2009-08-18
Much kudos [COLOR=Black]to TrakerJon fo[/COLOR]r this excellent post. Really good for us newbies. :)
Thanks.

---

### Post by TrakerJon on 2009-08-19
> **ramesh20033 said:**
> I have just installed Ubuntu9.04 in my computer and Trakerjon"s excellent tutorial has come in handy to me.Thanks a lot Trakerjon for the excellent tutorial.

Regards
Ramesh


Hope you get as much enjoyment out of Ubuntu as I do...glad I could be of some service, please share with other folks when possible.

---

### Post by TrakerJon on 2009-08-19
> **Crystal Visions said:**
> Much kudos [COLOR=Black]to TrakerJon fo[/COLOR]r this excellent post. Really good for us newbies. :)
Thanks.

My pleasure, welcome to the wonderful world of Ubuntu ;)

---

### Post by wnelson on 2009-09-05
Thank you so very much.....It's bookmarked....

Walt

---

### Post by wnelson on 2009-09-05
By the way it works with karmic....

---

### Post by alibabajr on 2009-09-06
Thanks, worked great for me, I have not done all of it but what ever I have, it worked fine. 
great effort.
thanks once again

---

### Post by zebedeeboss on 2009-09-10
As a newbie to Ubuntu this was a god send - hopefully one day I will understand exactly what I have just done  but for now its great to tweak the system with some expert knowledge

THANK YOU :):):)

---

### Post by dlradlt on 2009-09-11
this is a awesome thread everything i needed and then some

thanks

---

### Post by TrakerJon on 2009-09-11
> **wnelson said:**
> Thank you so very much.....It's bookmarked....

Walt

You're so very welcome Walt, please share with friends.

---

### Post by TrakerJon on 2009-09-11
> **wnelson said:**
> By the way it works with karmic....


Thanks, I haven't tried that yet...good to know...I'll pass it along.

---

### Post by TrakerJon on 2009-09-11
> **alibabajr said:**
> Thanks, worked great for me, I have not done all of it but what ever I have, it worked fine. Great effort. Thanks once again.

Glad you enjoy it, if there is ever anything you would like to add please let me know.

Traker

---

### Post by TrakerJon on 2009-09-11
> **zebedeeboss said:**
> As a newbie to Ubuntu this was a god send - hopefully one day I will understand exactly what I have just done  but for now its great to tweak the system with some expert knowledge

THANK YOU :):):)


I've been there myself and always found it difficult to remember what I read or did so I decided to make a quick guide of sorts. I'm sure I'll do the same for the next release.

---

### Post by -_- Joseph -_- on 2009-09-11
It was a lot for someone like me to read but it was worth it

Keep up the good work


                                       ,Joseph

---

### Post by TrakerJon on 2009-09-11
> **dlradlt said:**
> This is an awesome thread everything I needed and then some.

Thanks


Hopefully I'll add even more, if I can find the time.

---

### Post by TrakerJon on 2009-09-12
> **-_- Joseph -_- said:**
> It was a lot for someone like me to read but it was worth it

Keep up the good work, Joseph
 

Hahaha Well, Joe I'm sorry it wasn't a short read but then anything worth having isn't usually that easy either. I tried to include the stuff that most people would want and then a little extra for good measure. :D

---

### Post by black scorpio on 2009-09-12
very great thank you so much.

---

### Post by TrakerJon on 2009-09-12
> **black scorpio said:**
> very great thank you so much.


...and I thank you for sharing with others.

Traker

---

### Post by Sidewinder1 on 2009-09-19
TrackerJon:
This Tutorial is beyond awesome! Your selfless, tireless efforts at sharing are only exceeded by your boundless knowledge and good taste. You truely epitomize the FOSS philosophy; I want to have your baby. :-)
I wish this was around when I started; and I'll see to it that it gets maximum exposure to all that I cajole into trying Ubuntu.
Sincerest, humblest gratitude.
Side

---

### Post by TrakerJon on 2009-09-19
> **Sidewinder1 said:**
> TrackerJon:
This tutorial is beyond awesome! Your selfless, tireless efforts at sharing are only exceeded by your boundless knowledge and good taste. You truly epitomize the FOSS philosophy; I want to have your baby. :-)
I wish this was around when I started; and I'll see to it that it gets maximum exposure to all that I cajole into trying Ubuntu.
Sincerest, humblest gratitude.
Side

Whoa! Well, if you resemble Catherine Zeta-Jones or Megan Fox I'm sure we can make arrangements :D Yes, please do share as much as possible, we've all been there at one time or another and getting over the initial hurdles often leads to bigger and better things, I'm glad it's helping folks out as much as it seems to be...regards to all.

- Traker

---

### Post by aakboy on 2009-09-19
[COLOR=DarkGreen][SIZE=4]Thanks a lot for great Tutorial !!!
awesome..
[/SIZE][/COLOR]

---

### Post by TrakerJon on 2009-09-23
> **aakboy said:**
> [COLOR=DarkGreen][SIZE=4]Thanks a lot for great Tutorial !!!
awesome..[/SIZE][/COLOR]

Glad it's getting some global exposure, makasih!

---

### Post by Jonners59 on 2009-09-25
I have install office 2007 on my Ubuntu 8.04.  Now I am having an issue with activation

I can not activate the product.  It said I had over used the license, so I tried the by phone option, but it did not give the telephone number to call.  Finally found the number on MS websites.  to save others the hours of searching, here is the link:

[http://www.microsoft.com/licensing/existing-customers/activation-centers.aspx](http://www.microsoft.com/licensing/existing-customers/activation-centers.aspx)

I called MS and got the activation numbers, BUT now I realize that** the boxes the numbers go in are blanke**d out and I can not type in them.

Can anyone help me please?

---

### Post by TrakerJon on 2009-09-25
> **Jonners59 said:**
> I have install office 2007 on my Ubuntu 8.04.  Now I am having an issue with activation

I can not activate the product.  It said I had over used the license, so I tried the by phone option, but it did not give the telephone number to call.  Finally found the number on MS websites.  to save others the hours of searching, here is the link:

[http://www.microsoft.com/licensing/existing-customers/activation-centers.aspx](http://www.microsoft.com/licensing/existing-customers/activation-centers.aspx)

I called MS and got the activation numbers, BUT now I realize that the **boxes the numbers go in are blanked out** and I can not type in them. Can anyone help me please?

OpenOffice will save in most Microsoft Office formats, Crossover Linux [http://www.codeweavers.com/products/cxlinux/]("http://www.codeweavers.com/products/cxlinux/") or Play On Linux [http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html") might help you but I personally don't recommend trying to run Microsoft products on Linux operating systems, that's like putting Ford parts in a Mercedes. Do a Google search for **Office 2007 Ubuntu** and good luck.

---

### Post by Jonners59 on 2009-09-26
> **TrakerJon said:**
> OpenOffice will save in most Microsoft Office formats, Crossover Linux [http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/) or Play On Linux [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html) might help you but I personally don't recommend trying to run Microsoft products on Linux operating systems, that's like putting Ford parts in a Mercedes. Do a Google search for **Office 2007 Ubuntu** and good luck.

Thank you.
I have installed the playonlinux sw but that does not change or correct the problem.

Office 2007 is outstanding, and is, I hate to say it well advanced of any other office type suite.  I have got it working perfectly using WINE, but for the activation.  If you have not tried it do not critisize it.  I would say it is more like putting a jet engine in an aston martin.  Best of both worlds

I will have to continue my search.

---

### Post by TrakerJon on 2009-09-26
> **Jonners59 said:**
> Thank you.
I have installed the playonlinux sw but that does not change or correct the problem.

Office 2007 is outstanding and (I hate to say it) well advanced compared to any other office suite. I have it working  using WINE except for the activation. If you haven't tried it, don't criticize it, I would say it is more like putting a jet engine in an Aston Martin. Best of both worlds.

I will have to continue my search.

That you will my friend. I suggest you attempt a dual boot Ubuntu/Win XP SP3 scenario instead of trying to load Office 2007 onto a somewhat unwilling Ubuntu desktop victim. Yes, I have and do use Office 2007. Most people don't require all the extensive desktop publishing abilities that is included with the suite but I'm glad at least one of us is an enthusiast. BTW, I would never do that to a Vanquish S either. :wink:

---

### Post by Capt. Blackwood on 2009-09-29
Sound's more like putting Nitrus in an Ariel Atom. o.O
 
I don't dig MS Office 2007. But i'm diein to get '03 running asap.

---

### Post by TrakerJon on 2009-09-30
> **Capt. Blackwood said:**
> Sound's more like putting Nitrus in an Ariel Atom. o.O
 
I don't dig MS Office 2007. But i'm diein to get '03 running asap.


Guys, I recommend that you use the PPA channels and update your Ubuntu operating system to the latest version of OpenOffice. My post gives you instructions how to do just that...enjoy.

---

### Post by mdsmedia on 2009-10-01
I hate to turn this into a flamewar, and that is not my intention, but while I agree that Office is superior to OpenOffice, MS doesn't make it available to Linux, and there are alternatives, native to Linux, for almost anything Office provides.

I prefer to use native apps and I thank TrakerJon for this excellent tutorial. If I can't get what I want from native apps, I resign myself to not being able to do so. So far, that hasn't been the case in most circumstances, and the pros far outweigh the cons of FOSS. If you're looking for a "free" way to run your Windows apps, you're tying yourself to Windows.

---

### Post by Capt. Blackwood on 2009-10-01
> **TrakerJon said:**
> Guys, I recommend that you use the PPA channels and update your Ubuntu operating system to the latest version of OpenOffice. My post gives you instructions how to do just that...enjoy.


So 9.04 doesn't have the latest open office?


What's the current?

---

### Post by TrakerJon on 2009-10-02
> **mdsmedia said:**
> I hate to turn this into a flamewar, and that is not my intention, but while I agree that Office is superior to OpenOffice, MS doesn't make it available to Linux, and there are alternatives, native to Linux, for almost anything Office provides.

I prefer to use native apps and I thank TrakerJon for this excellent tutorial. If I can't get what I want from native apps, I resign myself to not being able to do so. So far, that hasn't been the case in most circumstances, and the pros far outweigh the cons of FOSS. If you're looking for a "free" way to run your Windows apps, you're tying yourself to Windows.

I agree, MS Office has more capabilities than OpenOffice and overall is probably a better product. It's still my contention though...that for most people who simply want to type a letter, create basic spreadsheets or put together a quick slide presentation OpenOffice will definitely do the trick. Again, if you want MS Office to work without issues I recommend a dual boot scenario to get the best of both worlds.

- Traker

---

### Post by TrakerJon on 2009-10-02
> **Capt. Blackwood said:**
> So 9.04 doesn't have the latest open office?


What's the current?

You can get OpenOffice 3.1.1 via the PPA channels I have listed. I'm not sure what the current update is through the Ubuntu mirror sites. #-o

---

### Post by harrykar on 2009-10-08
> **TrakerJon said:**
> You have a point on # 1. but that's pretty much a given, either you want the key to the repository or not...don't you think?

I personally agree with you but don't guess agree my daughter 11 years old(that point was born from her observation). I guess that for a so called *newbie* the psyco side is important as well as the technical one and any of WARNINGS is *lethal* for them.        

> **TrakerJon said:**
> On # 2 & 4 you might want to change your repository references to point to the main Canonical server, these are readily available on most mirrors as well.

What you mean ? main Canonical servers is pointed by default just after a new distro install. I don't get that point  
Ok get it(im delayed but..). I change to Main repo server (actually i am in Karmic) and that's the output(same as in Jaunty):

```
 
harrykar@harrykar-desktop:~$ sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-plugins-farsight gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-good is already the newest version.
E: Couldn't find package gstreamer0.10-pitfdll

``````

...
...
Package gstreamer0.10-plugins-farsight is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gstreamer0.10-plugins-bad
E: Package gstreamer0.10-plugins-farsight has no installation candidate
...
E: Couldn't find package w32codecs
...
E: Package avifile-win32-plugin has no installation candidate
...
E: Package libsox1 has no installation candidate
...
E: Package toolame has no installation candidate
...
E: Package acroread has no installation candidate
...
E: Package wink has no installation candidate

```I warn you that i test actually all that in a 9.10 (alias Karmic Koala) beta release running into a VM.

In other words i don't think it is a mirror problem(a *mirror *normally simply mirror the Main site) so i change again to my local mirror

> **TrakerJon said:**
> This post is geared towards 32 bit systems (since most folks have them) but thanks for the 64 bit reference in # 3.

In the same manner most people now use AMD64 release because of fisiological(time-depended)  hardware improvements (virtualization etc)

PS: I feel myself to advise Firefox *autopager* plugin that helps (you're not distracted to click on pages back and forth) on browsing very long threads /pages

---

### Post by TrakerJon on 2009-10-09
harrykar, I'm not sure what's causing your install/update problems, maybe that you're running a RC version of Karmic or that you're having connectivity issues running the OS within a VM (that could have a NAT'd or bridged IP problem). I've installed all of the above applications and plug-ins numerous times since your first reply without any of the issues or the complications that your experiencing. If you enable the third party references and add the additional repositories in software sources you should be fine. If you're having connection problems with the mirror site you're currently using simply connect to another faster one as outlined above. I wish I could assist you more but this post is meant to merely be a fast and easy way to get a full featured desktop computing environment and it's not really geared towards troubleshooting or problem resolution. If you need technical assistance there are many folks that will be glad to help you throughout the various posts and forums.

-TrakerJon

---

### Post by ublintu on 2009-11-01
Hi,
It`s a great tutorial. I used it in jaunty, but I changed to karmic. When I try to install codecs I get just this and I cant install most of them:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsox1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libsox1 has no installation candidate

for example libsox1 changed to libsox1a. Is it the same package? Is it the solution If I change all of them with the new ones? Will it work in karmic like in jaunty?

---

### Post by TrakerJon on 2009-11-01
> **ublintu said:**
> Hi,
It`s a great tutorial. I used it in jaunty, but I changed to karmic. When I try to install codecs I get just this and I cant install most of them:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsox1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libsox1 has no installation candidate

for example libsox1 changed to libsox1a. Is it the same package? Is it the solution If I change all of them with the new ones? Will it work in karmic like in jaunty?

Ok, you're a little ahead of the curve but I can appreciate that...the short answer is yes. I'm working on a post for Karmic I just haven't got it out yet. You'll notice that toolame is now twolame also. The VLC vlc-plugin-esd and ttf-bitstream-vera font seems to be missing in Karmic. The instructions for nVidia/ATI drivers has changed a little as well...Advanced Desktop Effects is now the package name in Karmic for what is Desktop Effects in Jaunty.

---

### Post by ublintu on 2009-11-01
Yes I changed a few things when I installed compiz and medibuntu.
Thanks 4 the help. I changed those packages and I could install them. I think I`m fine now, but I will check it from your next tutorial.

---

### Post by TrakerJon on 2009-11-02
> **ublintu said:**
> Yes I changed a few things when I installed compiz and medibuntu. Thanks 4 the help. I changed those packages and I could install them. I think I`m fine now, but I will check it from your next tutorial.

I'm glad you had success installing the new packages. I've posted the initial Karmic Koala equivalent of this post pending review by the powers that be...it needs some revising and additions that I will be making in the upcoming days. I have to say this, I'm not completely happy with the new release, there are several issues with multimedia applications (Kaffeine, Audacious and RealPlayer) that I've already discovered. I've also encountered some permissions related concerns with Karmic Koala as well. If you have a fully functioning Jaunty Jackalope install you may want to wait until they've worked all the bugs out first before upgrading or replacing your existing operating system installation.

---

### Post by 565Customz on 2009-11-02
i have no idea what alot of those programs do...so i just installed them all...lol

---

### Post by TrakerJon on 2009-11-02
> **565Customz said:**
> i have no idea what alot of those programs do...so i just installed them all...lol

Well, if you didn't, you would definitely know what you're missing hahaha. :D

---

### Post by Old_Grey_Wolf on 2009-11-02
> **TrakerJon said:**
> I've posted the initial Karmic Koala equivalent of this post pending review by the powers that be...it needs some revising and additions that I will be making in the upcoming days.

After your "Made Easy (Ubuntu 9.10)" is finalized, please post a link to it in this thread. It will help those of us monitoring this thread to find it.

Many thanks for your work to help others!!!

 :D

---

### Post by TrakerJon on 2009-11-03
> **Old_Gray_Wolf said:**
> After your "Made Easy (Ubuntu 9.10)" is finalized, please post a link to it in this thread. It will help those of us monitoring this thread to find it.

Many thanks for your work to help others!!!

 :D


First, I do appreciate the good words. Secondly, I've posted the Karmic update, still waiting for the moderators to release it. In the mean time I've found quite a few modifications to my initial post that need to be made. I'm beginning to see that several of the third party application developers have dropped the ball when it comes to their submissions to the new release (not unlike Windows 7). In other words, the Karmic Koala release is great but the available applications...not so much.

---

### Post by TrakerJon on 2009-11-20
> **Old_Gray_Wolf said:**
> After your "Made Easy (Ubuntu 9.10)" is finalized, please post a link to it in this thread. It will help those of us monitoring this thread to find it.

Many thanks for your work to help others!!!

 :D


Ubuntu Desktop Computing Made Easy (Karmic 9.10) has officially been posted and can be found at [http://ubuntuforums.org/showthread.php?t=1310795](http://ubuntuforums.org/showthread.php?t=1310795)

---

