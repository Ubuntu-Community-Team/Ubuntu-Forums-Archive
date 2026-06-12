---
title: "Ubuntu Desktop Computing Made Easy (Ubuntu 8.10)"
date: 2009-05-07
forum: Outdated Tutorials &amp; Tips
---

### Post by TrakerJon on 2009-05-07
This documentation is intended for folks that would like to add additional programs and applications to their Ubuntu Desktop installation making their overall experience similar to that of other well known operating systems (less the huge software expense). 

Recommended: Pentium 4 or higher workstation with 1Gb physical memory, 256 Mb graphics card, 10/100 Ethernet card and 20+ Gb hard disk. If you install everything I've listed it takes up about 4 Gb on your hard drive (I use ext4 disk formatting but the default ext3 formatting is fine).

Multimedia functionality and collaborative applications are a big part of the Internet these days, this post is oriented towards installing useful codecs, plug-ins, programs and applications. Please keep in mind older computers may have video performance issues due to high CPU usage and increased memory requirements.

The easiest way to perform most of these installs is to copy and paste from this post into a terminal window (found in Accessories). I strongly suggest installing a few things at a time, testing each along the way.

**Start by going to System > select Administration > select Software Sources > Check the all the boxes under the Ubuntu Software, Third-Party Software and Updates tabs > Close and Reload**

Get all the available Ubuntu updates at this point, look for the update notification icon on the task bar. Reboot after updating your system and then install as many of the following as you wish...again, I suggest installing a few things at a time, testing each along the way.

If you're having slowness issues with the default repository go to System > select Administration > select Software Sources > Ubuntu Software tab > Download from: drop down menu > select Other > click Select Best Server and  when it finishes the query click Choose Server > Close and Reload.

Many of these installations require access to the Medibuntu Repository and enabling some additional software sources. Directions are on this site: **[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)** or if you have Ubuntu 9.04 "Jaunty Jackalope" simply do the following from a terminal window:

**sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list**

**sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update**

Several codecs and plug-ins are needed for playing a variety multimedia formats correctly...(installing ubuntu-restricted-extras can sometimes be problematic, try this method if you've experienced issues).
**sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-plugins-farsight gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools**

Install these as well (some may be installed at this point, no worries)
**sudo apt-get install realplayer w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev jackd sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc jack-tools libjackasyn0 avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc**

Last but not least...
**sudo apt-get install easytag-aac faac faad ffmpeg ffmpeg2theora flac gxine icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmozjs0d libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1 mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 libamrnb3 libamrwb3 sox tagtool toolame vorbis-tools gecko-mediaplayer**

Install some fonts.
**sudo apt-get install msttcorefonts mplayer-fonts ttf-xfree86-nonfree xfs**

Adobe Flash too…
**sudo apt-get install flashplugin-nonfree**

Install the latest Sun Java JRE
**sudo apt-get install gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin unixodbc**


**ATI and Nvidia Drivers and Desktop Effects**

This requires some effort on the part of the user to know exactly what graphics card they have installed, use with caution and please read all applicable instructions or notes along the way.

The new Ubuntu 9.04 Jaunty Jackalope system comes with a Nouveau display graphic driver by default and the advanced effects cannot be used. If you've already tried to enable restricted Ubuntu drivers and ATI/nVidia cannot be found in the list try installing the ATI/nVidia driver with this tutorial:

1. Run Applications/Add/Remove
2. From the left menu choose System Tools
3. Next from the right menu, find and select for install: Desktop Effects (Compiz Setup) and ATI/Nvidia binary X.org Driver (nVidia could be version 173 or 177). Selecting the driver will get the list of supported graphics cards.
4. Click Apply Changes and after installation go to System/Administration/Hardware Drivers
5. The system will search for available drivers, choose the recommended option from the list and activate the driver by clicking Activate.
6. Restart your system and the new ATI/nVidia graphic display driver will be in use.

*Unsupported* updated versions of X.org drivers, libraries, etc. for Ubuntu **[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates")**
Note: Import the key and add the repositories for your specific distribution in System > Administration > Software Sources then run **sudo apt-get update** from a terminal window.


**Compiz, Emerald and Screenlets**

The default Ubuntu display setup lets you choose from None, Normal or Extra. Make it a lot more configurable with the CompizConfig Settings Manager...found in System > Preferences after installing the following:
**sudo apt-get install compizconfig-settings-manager gnome-art usplash startupmanager compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald screenlets librsvg2-common fusion-icon**

Notes: Make sure you enable Visual Effects "**Extra**" (right click on your desktop, choose change Desktop Background and click on the Visual Effects tab) before adusting Compiz settings. Reset Compiz defaults by going into CCSM > Preferences > Profile & Backend > Click Reset to defaults.


A fairly good collection of various media players like Audacious, Amarok, Esperanza, Kaffeine and VLC (install realplayer w32codecs libxine1-ffmpeg and libdvdcss2 first).
**sudo apt-get install audacious amarok esperanza xmms2 kaffeine vlc vlc-plugin-esd mozilla-plugin-vlc**

Notes: In order to open .m3u files with Audacious set Nautilus (preferences -> behavior tab) to always "view" the file and not ask.

Additional Notes: In Kaffeine be sure to verify the decoder references under Settings and xine Engine Parameters to reflect the correct paths to Realplayer, Win32 codecs and your DVD drive. I ran into a folder permissions issue in my home folder when launching kaffeine, if you experience this issue very carefully use the following commands from a terminal window:
**sudo chown -R username:username ~/.kde** (put in *your* "username")
**sudo chmod -R 700 ~/.kde**


Ardour, SoundKonverter, Jokosher and AcidRip for multimedia recording, editing, conversions, mixing, etc.
**sudo apt-get install ardour soundkonverter jokosher lmms acidrip**

K9Copy, K3b and DeVeDe when you need DVD, CD, VCD and VCD software (requires libdvdcss2)
**sudo apt-get install k9copy k3b devede**

Streamripper will allow you to download internet radio station broadcasts.
**sudo apt-get install streamripper**

**Shoutcast** is a good place to shop for internet radio stations. **[http://www.shoutcast.com/]("http://www.shoutcast.com/")**


**P2P (peer to peer) clients**
 
Gnutella is a lot like Limewire or Morpheus (see Firewalls and avast! sections below before using).
**sudo apt-get install gtk-gnutella**

Vuze can be handy for things not found with Gnutella (see Firewalls and avast! sections below before using).
**sudo apt-get install vuze**

**Frostwire** is similar to Gnutella (see Firewalls and avast! sections below before using).
**[http://www.frostwire.com/]("http://www.frostwire.com/")**

Note: Your Java JRE is not broken and the Frostwire package is not corrupt but there is a known issue that causes the install to fail when using the Ubuntu GDebi Package Installer. The latest release of FrostWire requires that you install it from a terminal window **sudo dpkg -i frostwire-4.18.1.i586.deb** Be aware that the program installs as the root user, when the application launches complete the install process and then relaunch as the current user from Applications > Internet > FrostWire. You should have complete functionality now, customize as desired.


**AceoneISO2** is a CD/DVD image manipulator for Linux (used primarily with .iso files).
**[http://www.getdeb.net/search.php?keywords=acetoneiso]("http://www.getdeb.net/search.php?keywords=acetoneiso")**

Various compression/extraction and encoding/decoding utilities...
**sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils aish uudeview mpack lha arj cabextract file-roller**

**avast!** makes a very good anti-virus product for Linux it can be downloaded free for home use from **[http://avast.com/eng/download-avast-for-linux-edition.html]("http://avast.com/eng/download-avast-for-linux-edition.html")** You'll need the home user free registration key (emailed to you from their site). The key can be pasted into a terminal window after you type avast at a terminal command prompt. The gui icon is located in Applications > Accessories. Update the program frequently and scan all questionable downloads.


Thunderbird is a light weight and very popular email client.
**sudo apt-get install thunderbird spamassassin**

Setup your Gmail, Yahoo, AOL, Hotmail accounts in Thunderbird (use POP port 1024)
**[http://webmail.mozdev.org/index.html]("http://webmail.mozdev.org/index.html")**

Sunbird is one of the best open source calendars.
**sudo apt-get install sunbird lightning-extension**

Skype lets you talk and chat with friends all over the world.
**sudo apt-get install skype**

Note: You might have to configure your Options > Sound Devices > Sound In/Sound Out within Skype and test with the Echo/Sound test Service. I also had to enable and adjust my Ubuntu Volume Controls > Preferences > Mic and Mic Boost settings.

Fonts, fonts and more fonts...for use in a variety of word processing applications (pick and choose).
**sudo apt-get install ttf-larabie-straight ttf-larabie-deco xfonts-terminus-dos xfonts-terminus xfonts-terminus-oblique xfonts-mona tv-fonts ttf-tuffy ttf-sjfonts ttf-georgewilliams ttf-fifthhorseman-dkg-handwriting ttf-essays1743 ttf-opensymbol ttf-mgopen ttf-freefont ttf-dustin ttf-dejavu-extra ttf-dejavu-core ttf-dejavu ttf-bpg-georgian-fonts ttf-bitstream-vera equivs ttf-sil-gentium gnome-specimen**

Note: Postfix is related to some of these fonts, be careful not to modify your Postfix configurations if you're using it for email purposes, otherwise use the default settings if/when prompted.

I typically don’t use the Arabic and Asian fonts, to remove them from a terminal window type: 
**sudo apt-get remove ttf-kochi-mincho ttf-kochi-gothic ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ttf-unfonts-core ttf-indic-fonts-core ttf-wqy-zenhei**

Note: Add them by simply using install instead of remove.

**HP printer driver issues? [http://hplipopensource.com/hplip-web/downloads.html]("http://hplipopensource.com/hplip-web/downloads.html")**

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

The web interface for Wordnet is **[http://wordnetweb.princeton.edu/perl/webwn]("http://wordnetweb.princeton.edu/perl/webwn")**

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

**webKam** is simple webcam application **[http://code.google.com/p/webkam-kde4/downloads/list]("http://code.google.com/p/webkam-kde4/downloads/list")**

**Elltube** is a YouTube downloader and converter **[http://elltube.sourceforge.net/download]("http://elltube.sourceforge.net/download")**

A complete Web Authoring System for Linux desktop users to rival programs like FrontPage and Dreamweaver.
**sudo apt-get install kompozer**

If you program in C\C++ languages you’ll need Build-Essential packages.
**sudo apt-get install build-essential **

Geany is a fast and lightweight IDE (Integrated Development Environment) for programming in various languages.
**sudo apt-get install geany**

Eclipse is an awesome open-source IDE for Java, C, C++, and Python. 
**sudo apt-get install eclipse eclipse-cdt eclipse-pydev**

Vim and Gvim may come in handy for file editing (gedit works good too).
**sudo apt-get install vim-full vim-doc cscope vim-gnome tcl8.4 vim-gui-common vim-runtime tclreadline cbrowser**

Cream is another gui interface for Vim (like Gvim) that allows for ease of use and improved functionality.
**sudo apt-get install cream**

Gedit (Text Editor in Accessories) is installed by default but the plugins are not...
**sudo apt-get install gedit-plugins**

Note: Enable Gedit plugins in Edit > Preferences > Plugins. 
The Gedit wiki is at **[http://live.gnome.org/Gedit]("http://live.gnome.org/Gedit")**

jEdit is a java based full featured editor (make sure you have Sun JRE installed).
**sudo apt-get install jedit**

Meld is a visual diff and merge tool.
**sudo apt-get install meld**

gFTP is a generic FTP client (port 21 is typical and consider file permissions when uploading).
**sudo apt-get install gftp**

Convert .rpm files to .deb **[http://www.howtoforge.com/converting_rpm_to_deb_with_alien]("http://www.howtoforge.com/converting_rpm_to_deb_with_alien")**
**sudo apt-get install alien**

Htop is a process manager to view available memory and CPU usage or manage running processes.
**sudo apt-get install htop**

Sysinfo is a simple program which displays your computer's system information.
**sudo apt-get install sysinfo**

HardInfo displays info about the hardware, software, and can perform simple benchmarks.
**sudo apt-get install hardinfo**

Byzanz records your desktop and saves it to animated GIF files (viewable in a web browser). 
**sudo apt-get install byzanz**

Note: Byzanz is a panel applet and not listed in Applications, add it by right-clicking the panel and selecting Add to Panel > Desktop Recorder. Desktop effects have to be turned off to use Byzanz. More information is available by typing man byzanz-record from a terminal window.

Fish (the applet, not the shell) is a fun animated panel applet that tells fortunes.
**sudo apt-get fortune-mod fortunes-min librecode0**

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

**luckyBackup**...a powerful, fast and reliable backup & sync tool **[http://luckybackup.sourceforge.net/download.html]("http://luckybackup.sourceforge.net/download.html")**

Partimage system backup, instructions can be found at: **[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")**
**sudo apt-get install partimage**

KDE Partition Manager allows you to manage your disks, partitions and file systems:
**sudo apt-get install partitionmanager**

GParted is the GNOME partition editor for creating, reorganizing and deleting disk partitions. 
**sudo apt-get install gparted**

Note: Documentation can be found at **[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")**

**Reconstructor** will help you create your own Ubuntu based distribution **[http://www.reconstructor.org/index.php?option=com_frontpage&Itemid=1]("http://www.reconstructor.org/index.php?option=com_frontpage&Itemid=1")**

**Defrag** (or fidefrag I should say)

**sudo apt-get install bzr python-psyco**
**bzr branch lp:fidefrag**
**cd fidefrag/src**
**sudo python fidefrag.py -d /<directory name>**

Note: It's not a good idea to defrag your whole system, some directories won't react very well. I typically defrag /usr (this one takes a long time), /var, /lib, /home, /etc, /bin and /sbin

**Google Earth** install: **[http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/]("http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/")**

**Show wallpaper or background color while logging in to Ubuntu**: **[http://ubuntuforums.org/showthread.php?t=753261]("http://ubuntuforums.org/showthread.php?t=753261")**

Rainy days or a lot of time to kill?
**sudo apt-get install frozen-bubble**

Kids in the house?
**sudo apt-get install gcompris gcompris-sound-en tuxpaint gnucap**


**Firewalls** 

Internet security is important these days and firewalls can be quite complex, hopefully the following will help...use only one of these two applications and please read all of the documentation first. Most people are already behind a broadband router configured to give you "TruStealth" protection on the internet...check your current protection at the Sheilds Up! link below before being too concerned.

**ufw** ("uncomplicated firewall" included with Ubuntu), by default is set to "allow" all network traffic, the wiki instructions are at **[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")** then **sudo ufw enable** the firewall at system startup.

Personally I would rather use the gui interface for ufw... 
**sudo apt-get install gufw**
 
**Firestarter** is quite easy to configure **[https://help.ubuntu.com/community/Firestarter]("https://help.ubuntu.com/community/Firestarter")**
**sudo apt-get install firestarter**

Load Firestarter at startup: [http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html]("http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html")
Note: In nano the ^ is the Ctrl key on most keyboards [http://mintaka.sdsu.edu/reu/nano.html]("http://mintaka.sdsu.edu/reu/nano.html")

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


**The Jaunty wiki** can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Jaunty]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty")**

**Ubuntu 8.10** (Intrepid Ibex) **How-To [http://www.funnestra.org/ubuntu/intrepid/]("http://www.funnestra.org/ubuntu/intrepid/")**

**The UNR (Ubuntu Netbook Remix) wiki is here [https://wiki.ubuntu.com/UNR]("https://wiki.ubuntu.com/UNR")**

**The Ubuntu Pocket Guide** can be found at **[http://www.ubuntupocketguide.com/download_main.html]("http://www.ubuntupocketguide.com/download_main.html")**

**Ubuntu Desktop Essentials [http://www.techotopia.com/index.php/Ubuntu_Desktop_Essentials]("http://www.techotopia.com/index.php/Ubuntu_Desktop_Essentials")**

**Best 100** Open Source Applications **[http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/](http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/)**

**Best 50** Ubuntu Opensource Applications For Design And Developing **[http://www.emmaalvarez.com/2007/12/top-best-50-ubuntu-opensource.html]("http://www.emmaalvarez.com/2007/12/top-best-50-ubuntu-opensource.html")**

**GetDeb** software site for Ubuntu and Debian [**http://www.getdeb.net/**]("http://www.getdeb.net/")

**Gnome Desktop software** site [**http://www.gnomefiles.org/**]("http://www.gnomefiles.org/")

**KDE-Apps.org [http://www.kde-apps.org/]("http://www.kde-apps.org/")**

**Ubuntu PPA Search [https://edge.launchpad.net/ubuntu/+ppas]("https://edge.launchpad.net/ubuntu/+ppas")**

**Ubuntu Games [https://help.ubuntu.com/community/Games]("https://help.ubuntu.com/community/Games")**

**Cool wallpaper and more [http://www.kde-look.org/]("http://www.kde-look.org/")**


**Procedure to enable WPA Wireless in Ubuntu**

Sometimes wireless adapters (usually internal ones) don’t want to work right after the initial Ubuntu operating system install, even if the system recognises the hardware. The following should help if you’re in that situation.

If you have wired Internet connectivity update the software sources list **sudo apt-get update**

**sudo apt-get install wpasupplicant** (may already be installed)

**sudo apt-get install network-manager-gnome network-manager** (may already be installed)

**sudo gedit /etc/network/interfaces** Comment out the lines without “lo” entries (using #) and save the file, if you have just installed Ubuntu this may not be necessary.

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


**Setup Samba peer-to-peer with Windows [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")**

Install Samba stuff
**sudo apt-get install samba samba-common samba-tools smbclient swat samba-doc samba-doc-pdf smbfs libpam-smbpass libsmbclient libsmbclient-dev winbind samba-dbg libwbclient0**

Once Samba is installed you can setup a very basic shared folder as follows: 

You’ll need to create Samba passwords with this command:

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

**sudo /etc/init.d/samba restart**

Use this command from a terminal window to check that your smb.conf doesn’t contain any syntax errors: **testparm**

Don't forget to create your shared folder and modify the permissions as needed. You may also have to allow specific IP address TCP/UDP access through your firewall as well. Keep in mind if security is an issue to read up a lot more on the topic.


**How to setup remote access [http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop]("http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop")**


**Web based workstation and application administration**

**webmin and usermin** can be found at **[http://www.webmin.com/usermin.html]("http://www.webmin.com/usermin.html")**


**CommuniGate Pro** 

CommuniGate Systems' goal is to consolidate all forms of Internet Communications into one address space, making the single address for email, IM, VoIP and video calling, more productive, portable, and independent of tariffs and tolls of closed network topologies. **[https://www.communigate.com/forms/cgp_try_before_you_buy.php]("https://www.communigate.com/forms/cgp_try_before_you_buy.php")**


**Alternative shells for Linux**...

C, K, T, Z & Fish shells
**sudo apt-get install csh ksh tcsh zsh fish**

**Bash Reference Manual [http://www.gnu.org/software/bash/manual/bashref.html]("http://www.gnu.org/software/bash/manual/bashref.html")**

**chmod calculator [http://www.javascriptkit.com/script/script2/chmodcal.shtml]("http://www.javascriptkit.com/script/script2/chmodcal.shtml")**


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
**deb-src [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main **

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C713DA6**


**Collection of useful commands...**
---------------------------------------------------------------   
**Searching for Packages:** 	        apt-cache search some_string      
**Show Package Info:** 		apt-cache showpkg xxx             
**Show Package Dependencies:** 	apt-cache depends xxx             
**Install:** 			apt-get install xxx               
**Re-Install:** 			apt-get --reinstall install xxx   
**Remove:** 			        apt-get remove xxx                
**Remove All (configs too):** 	apt-get remove --purge xxx
**Upgrade**: 			apt-get -u upgrade
**Show Upgrades:** 			apt-show-versions -u
**Show All Installed Packages:**	dpkg --list                       
**Find Package by File Name:** 	apt-file search /bin/ping         
**Find filenames in a Package**: 	apt-file list xxx                 
**Updating the apt-file Cache:** 	apt-file update
**Info on Installed Package**        aptitude show xxx
**System Hardware Info**             sudo lshw > hardware.txt

**Linux Command Directory [http://www.oreillynet.com/linux/cmd/]("http://www.oreillynet.com/linux/cmd/")**

**Linux Commands - A practical reference [http://www.pixelbeat.org/cmdline.html]("http://www.pixelbeat.org/cmdline.html")**

**Linux Newbie Administrator Guide [http://linux-newbie.sunsite.dk/]("http://linux-newbie.sunsite.dk/")**

Clean up your system and free up space with **sudo apt-get clean** and **sudo apt-get autoremove**

If you're curious (like me) or have the need to know **uname -a && cat /etc/*release** in a terminal window will tell you the kernel version and release date, the distro id/release/codename/description.


Ok, about **wine**...in most cases a free to use Linux program will work just as well as apps on that other well known operating system. I don't recommend it but for the folks that want to use wine this wiki should help **[https://help.ubuntu.com/community/Wine]("https://help.ubuntu.com/community/Wine")**

**Three Ways to Install Latest Wine in Ubuntu 9.04 Jaunty Jackalope [http://www.wine-reviews.net/wine-reviews/news/three-ways-to-install-latest-wine-in-ubuntu-904-jaunty-jackalope/print.html]("http://www.wine-reviews.net/wine-reviews/news/three-ways-to-install-latest-wine-in-ubuntu-904-jaunty-jackalope/print.html")**

**Wine Application Database (AppDB) [http://appdb.winehq.org/]("http://appdb.winehq.org/")**


-Traker

Dell GX270 3.2GHz Pentium 4 w/ 2Gb SDRAM using NVIDIA GeForce 6200 AGP video and MSI Wind Netbook U100 1.6GHz Intel Atom w/ 2Gb SDRAM using Intel Mobile 945GME Express video on Ubuntu 9.04

---

### Post by suitedaces on 2009-05-07
Mightn't be for everyone, but looks like you've put in a lot of effort, and a good few people will find it helpful. Nice.

---

### Post by wgilbert5 on 2009-05-07
I am absolutely stunned!  What a tremendous amount of work and knowledge went into this post.  I, for one, am grateful and will be using this store of linux info very often.  Thank you for thinking of others and posting this for all to use.  Bill:P

---

### Post by tmos22 on 2009-05-07
Epic thread, all i was looking for, thanks mate

---

### Post by juancarlospaco on 2009-05-07
**Defrag your system... ??? fidefrag??? Defrag an EXT4 filesystem???**
*Defrag?, antivirus? what's next? i need antispyware and Ubuntu Genuine Advantage?*

---

### Post by 1BigBore on 2009-05-07
Impressive.
Will this work with the 9.04 release?

Thanks.

---

### Post by TrakerJon on 2009-05-07
> **1BigBore said:**
> Impressive.
Will this work with the 9.04 release?

Thanks.

Yes it will...make sure you follow the link to the Mediubuntu instructions for your version/release...and other version/release specific items like AcetoneISO2. I've had the best luck with 8.10 so far...

Cheers!

---

### Post by TrakerJon on 2009-05-07
> **juancarlospaco said:**
> **Defrag your system... ??? fidefrag??? Defrag an EXT4 filesystem???**
*Defrag?, antivirus? what's next? i need antispyware and Ubuntu Genuine Advantage?*

Yes, believe it or not files do get fragmented on Linux...I didn't believe it either at first but it does work and help out a bit. Antivirus...well let's just say that's mostly for scanning files to be used on other operating systems that are prone to that sort of thing. 

No activex, no spyware, no GWA just good fun...the best things in life can be free...or at least free to use hahaha.

---

### Post by TrakerJon on 2009-05-07
> **wgilbert5 said:**
> I am absolutely stunned!  What a tremendous amount of work and knowledge went into this post.  I, for one, am grateful and will be using this store of linux info very often.  Thank you for thinking of others and posting this for all to use.  Bill:P


My pleasure and my passion...glad you will enjoy it...please share with friends.

---

### Post by Ms_Angel_D on 2009-05-07
> **TrakerJon said:**
> Install Microsoft fonts.
**sudo apt-get install msttcorefonts**

Fonts and more fonts...mainly for use in OpenOffice if desired.
**sudo apt-get install ttf-larabie-straight ttf-larabie-deco mplayer-fonts xfonts-terminus-dos xfonts-terminus xfonts-terminus-oblique xfonts-mona tv-fonts ttf-tuffy ttf-sjfonts ttf-sil-padauk ttf-sil-ezra ttf-paktype ttf-georgewilliams ttf-fifthhorseman-dkg-handwriting ttf-farsiweb ttf-essays1743 ttf-opensymbol ttf-nafees ttf-mgopen ttf-gentium ttf-freefont ttf-dustin ttf-devanagari-fonts ttf-dejavu-extra ttf-dejavu-core ttf-dejavu ttf-bpg-georgian-fonts ttf-bitstream-vera ttf-alee equivs ttf-sazanami-gothic ttf-sazanami-mincho**

For Ubuntu 9.04 Jaunty the command is instead:
> sudo apt-get install ttf-larabie-straight ttf-larabie-deco mplayer-fonts xfonts-terminus-dos xfonts-terminus xfonts-terminus-oblique xfonts-mona tv-fonts ttf-tuffy ttf-sjfonts ttf-sil-padauk ttf-sil-ezra ttf-paktype ttf-georgewilliams ttf-fifthhorseman-dkg-handwriting ttf-farsiweb ttf-essays1743 ttf-opensymbol ttf-nafees ttf-mgopen ttf-freefont ttf-dustin ttf-devanagari-fonts ttf-dejavu-extra ttf-dejavu-core ttf-dejavu ttf-bpg-georgian-fonts ttf-bitstream-vera ttf-alee equivs ttf-sazanami-gothic ttf-sazanami-mincho

Epic post man, thanks for creating it!!!

---

### Post by TrakerJon on 2009-05-07
> **MetalHellsAngel said:**
> For Ubuntu 9.04 Jaunty the command is instead:


Epic post man, thanks for creating it!!!

Glad folks are enjoying it, please share with friends and acquaintances.

Regards,

Traker

---

### Post by Roanoke on 2009-05-07
I question if adobe makes a good pdf viewer. Although the recent security flaws are windows only, it's still slow and bulky.

---

### Post by GreenBowlPacker_3 on 2009-05-08
I'm somewhat new to Ubuntu, I didn't even know some of that stuff could be done.  I will definatly be coming back to this wealth of info.  Thanks!

---

### Post by TrakerJon on 2009-05-08
> **Roanoke said:**
> I question if adobe makes a good pdf viewer. Although the recent security flaws are windows only, it's still slow and bulky.

Seems to launch fairly quickly on my system without any rendering issues sometimes found using other .pdf viewers. Do you know of a better viewer? Please post any other useful applications or programs that you like not included with the default Ubuntu installation and I'll be glad to check them out.

---

### Post by Roanoke on 2009-05-08
Well, I use gnome's default viewer (evince) personally, and haven't found a problem with it so far. It's too bad there isn't a browser plugin, but oh well. For KDE, I'd go with okular, but I have no experience here.

---

### Post by TrakerJon on 2009-05-09
> **Roanoke said:**
> Well, I use gnome's default viewer (evince) personally, and haven't found a problem with it so far. It's too bad there isn't a browser plugin, but oh well. For KDE, I'd go with okular, but I have no experience here.


There is a Adobe Reader 9.1 plug-in for Firefox, I also like the PDF Download add-on available as an extention. :)

---

### Post by Roanoke on 2009-05-10
I know that there's one for adobe, I meant for evince.

---

### Post by TrakerJon on 2009-05-12
> **neo-man said:**
> Nice Thread. Thanks for nice howto. Will it work in Jaunty Jackalope?


Yes it will...make sure you follow the link to the Mediubuntu instructions for your version/release...and other version/release specific items like AcetoneISO2 for example. Enjoy!

---

