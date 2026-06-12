---
title: "HOWTO Ubuntu Lite"
date: 2005-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by christooss on 2005-12-02
[SIZE="6"]**How to install Ubuntu Lite on your computer**[/SIZE]

1. What is UbuntuLite?

Ubuntu Lite is an unofficial project of few guys. We tend to build Ubuntu installation which would siut LOW RAM and Low Mhz computer. You can find our page on [ubuntulite.org]("http://ubuntulite.org/")

2. Do I need UbuntuLite? You have so many lite Linux distributions?

Yes you do.

2.1 OK. But why?

Beacause Ubuntu Lite is Ubuntu based. Whit that you get apt-get functions any many packages you want to install after. ANd you get security and version fixes.

3. OK I know what it is, but how can I install it?

[COLOR="Red"]At this point I want to thank [/COLOR][[COLOR="Red"]Blackpaw[/COLOR]]("http://ubuntuforums.org/member.php?u=31207") [COLOR="Red"]for providing us repositories.[/COLOR]
First you have to install Ubutnu on your computer. At begining choose [COLOR="SeaGreen"]SERVER[/COLOR] installation. And when you get in to Terminal you have to edit your sources.list. Write 
```
sudo vim /etc/apt/sources.list
```

Uncoment all official repositories with removin # at the beggining of the line. Than add following line in sources.list
```
deb http://blueeyedcreature.net/ubuntu ./
```

Save and close

When you get back in terminal write
```
sudo apt-get update
sudo apt-get install ubuntu-lite-desktop
```

And after you are done restart your machine and you will find your self in WDM login manager. Its extension of XDM another login manager.

Login as user and there you have working Ubuntu Lite system with IceWM as windows manager installed. You have plenty other useful applications installed. Check for whole list at [Our WIKI]("http://ubuntulite.org/wiki/index.php/Package_List")

4. OK Thanks man!! But Im having problems. What can I do

First think that you can do is to look at [Oour Mailing list]("http://groups.google.com.au/group/ubuntu_lite/") if the problem has been solved. If you don't get your anwser there please send us mail and we hope we could help you. You can find us on IRC to. Chanell is #ubuntu-lite on Freenode. Ofcourse you can post your question here but mailing list is prefered mode :)

5. Hey nice project but how can I help

Again Sign on our mailing list and anwser questions if someone gets in to trouble. And go to our IRC chanell and help there to.

6. Hey hasn't there been a iso?

Iso still exist but its in a real testing mode. Many users get lots of errors. So prefered mode is apt-get install soulution. But there is a good news im trying to to bulid next version of CD. [COLOR="Red"]If there is someone who has expiriences with building ubuntu based install CDs. PLEASE Mail on mailing lits.[/COLOR]

7. Who are you christooss? :)

Im that guy who provided you a helpful [HOWTO Ubuntu mini ram]("http://ubuntuforums.org/showthread.php?t=42873") :)

8. Round up!!

8.1 Ubuntu server installation
8.2 Edit your sources.list
8.3 apt-get install ubuntu-lite-desktop
8.4 If problems check [http://ubuntulite.org/](http://ubuntulite.org/) [Mailing List]("http://groups.google.com.au/group/ubuntu_lite/") and IRC #ubuntu-lite at Freenode

Here I want to thank all you guy who started UbuntuLIte project.

If you find any tiping mistakess please notify me.

---

### Post by az on 2005-12-03
1.  Would you post the dependancies of ubuntu-lite-desktop?

2.  It is GPL?  Is the .dsc .orig.tar.gz available?  (probably a dumb question, but the maker of Automatix (ubuntu helper script) unfortunately recently made his thing proprietary)

3.  Would you make this a project on launchpad.net to integrate with Ubuntu proper (and upload to universe?)

---

### Post by christooss on 2005-12-03
This is the current version.

> abiword, acpi, acpi-support, acpid, anacron, apmd, bc, beep-media-player, bittornado, bittornado-gui, bogofilter, cdparanoia, cdrecord, cupsys,
cupsys-bsd, cupsys-client, cupsys-driver-gimpprint, dbus-1-utils, dillo, dc, doc-debian, dvd+rw-tools, esound, emelfm, fetchmail, mozilla-firefox, 
mozilla-browser, foomatic-db, foomatic-db-engine, foomatic-db-gimp-print, foomatic-db-hpijs, foomatic-filters, foomatic-filters-ppds, gaim,
gnome-sudo, gnumeric, gqview, graveman, gs-esp, hal, hotkey-setup, hplip, hplip-ppds, irssi-text, icewm, icewm-themes, icewm-common,
icewm-gnome-support, icepref, iceme, ivman, lftp, libesd-alsa0, libgl1-mesa, libglib2.0-data, libglut3, libsasl2-modules, libxp6, links2,
lynx, mc, menu, mgp, mkisofs, mousepad, numlockx, pnm2ppa, powermanagement-interface, powernowd, procmail, readahead, rox-filer, screen,
scrollkeeper, slocate, smbclient, sylpheed, synaptic, ttf-arabeyes, ttf-arphic-bkai00mp, ttf-arphic-bsmi00lp, ttf-arphic-gbsn00lp,
ttf-arphic-gkai00mp, ttf-baekmuk, ttf-bitstream-vera, ttf-freefont, ttf-indic-fonts, x-ttcidfont-conf, ttf-kochi-gothic, ttf-kochi-mincho, ttf-malayalam-fonts, xfonts-scalable, xfonts-100dpi, xfonts-75dpi, ttf-mgopen, ubuntu-docs, unzip, wdm, x-ttcidfont-conf, x-window-system-core,
xchat, xkeyboard-config, xorg-driver-synaptics, xpdf, xterm, xzgv, zip, xine-ui, xmms

Hm I don't know how to make dsc or tar.gz file. i made this meta package with equivs. But I would be happy to give this files to Community :)

I will look in to lunchpad. And than hopefully include it universe. But that would mean no media files :)

---

### Post by kultex on 2005-12-04
Hi Christoss,

I want to thank you for your work and want to give some informations for not so advanced linux users:

short introduction to icewm: [http://www.osnews.com/story.php?news_id=7774](http://www.osnews.com/story.php?news_id=7774)
----------------------------------------------------------------------
Infos about vim:

to scroll down and delete the # is easy, but to get into writing mode you have to type i - than you can write the extra repository - to get out of the writing mode you type Esc - to save the document and exit vim you typ ZZ
to exit without saving you type :q   (more easy: sudo nano /etc/apt/sources.list)
---------------------------------------------------------------------
SHUTDOWN: after login you will have problems to turn off your computer, because the halt of the shutdown menu is not working.

open xterm

$ sudo /sbin/shutdown -h now

it will shut down - with sudo /sbin/shutdown -r now   it will reboot

to make it more easy for the next sessions:

you open xterm:

$ sudo visudo

you add the following line:
your_username ALL=(root) NOPASSWD: /sbin/shutdown

to save press F2   to exit F10

$ sudo mousepad /etc/X11/icewm/preferences

you insert the following lines to the 6.th line of the document

ShutdownCommand="/sbin/shutdown -h now"
RebootCommand="/sbin/shutdown -r now"

you save the document, restart iceWM.
Shutdown and reboot from strg+alt+del - menu are now working
---------------------------------------------------------------------------------------------
TOOLBAR: to open common programs more easy:

you open xterm:

$ sudo mousepad /etc/X11/icewm/toolbar

you put a # at the beginning of every line and ad the following lines:

prog Xterm xterm xterm
prog Firefox firefox firefox
prog Mozilla mozilla mozilla
prog Abiword /usr/share/AbiSuite-2.4/icons/abiword_16 abiword
prog Mousepad mousepad mousepad
prog Sylpheed sylpheed-debian sylpheed
prog Xine xine xine
prog Xmms xmms xmms
prog EmelFM /usr/share/pixmaps/icon_dirparent.xpm /bin/sh -c "/usr/X11R6/bin/emelfm"
prog Gaim /usr/share/pixmaps/gaim-menu.xpm /bin/sh -c "/usr/bin/gaim"
prog Gqview gqview gqview
prog Synaptic /usr/share/synaptic/pixmaps/synaptic_32x32.xpm /bin/sh -c "/usr/bin/gksudo /usr/sbin/synaptic"
prog xpdf xpdf xpdf
prog rox rox /bin/sh -c "/usr/bin/rox" 

for rox there is no xpm available in the installation

those programs, you do not want to have in your toolbar put # at the beginning of the line
save the document, restart IceWM and you will have easy acess to xterm, firefox, mozilla and abiword.......
----------------------------------------------------------------------------------------------
MENU:  you can do the same with $ sudo mousepad /etc/X11/icewm/menu to get the programs you want in the root/start menu

SECURITY: Copy the files /etc/X11/icewm/menu+toolbar+preferences with emelfm or rox to $HOME/.icewm since modifications to this file will be discarded when you (re)install icewm.

ICONS: You can download more icons from [http://themes.freshmeat.net/projects/iceicons/](http://themes.freshmeat.net/projects/iceicons/) extract them to $ HOME/.icewm/icons and edit the included winoptions file - for details see [http://bbs.cvut.cz/~covex/icewm/iceicons/](http://bbs.cvut.cz/~covex/icewm/iceicons/) - alternativ you can copy all icons to /usr/share/pixmaps  (I prefer this)
-------------------------------------------------------------------
AUTOMOUNT with ivman: To get the automount function working, create with mousepad a file named startup in $HOME/.icewm:

#!/bin/sh
exec /usr/bin/ivman

then you have to make startup executable:

$ chmod +x /.icewm/startup

in rox it works perfect - in emelfm you can not unmount the devices
--------------------------------------------------------------------
MULTIPLE KEYBOARDS:
You can use setxkbmap to do it. For example, to load 3 keyboards - english, german and italian (us, de, it) and to switch between them using BOTH SHIFTS, run this:

setxkbmap -option grp:switch,grp:shift_toggle us,de,it

Alternatively, you can edit your xorg.conf ($: sudo mousepad /etc/X11/xorg.config) and restart X server, but any subsequent setxkbmap will overwrite those settings. Here is quote from my xorg.conf

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"     "de,lt"
        Option          "XkbOptions"    "grp:shift_toggle"
EndSection

more details:  
for your keyboards: in /etc/X11/xkb/symbols all the keyboard shortcuts are listened and in every is detailed information
[http://pascal.tsu.ru/en/xkb/](http://pascal.tsu.ru/en/xkb/)
[http://www.linux-es.org/docs/HOWTO/mini/Intkeyb](http://www.linux-es.org/docs/HOWTO/mini/Intkeyb)

---

### Post by christooss on 2005-12-04
Thanks for the sgutdown thing. This has been known problem. Currentlly solved with wdm conf file editing

[http://www.opensubscriber.com/message/xubuntu-devel@lists.ubuntu.com/2579245.html](http://www.opensubscriber.com/message/xubuntu-devel@lists.ubuntu.com/2579245.html)

---

### Post by LostinLinux on 2005-12-31
Hi, first of all please bear with me. I am from a very orthodox Windows background and i program in C++ but i dont have a clue where to start in Linux.

Anyway, my problem. I have a really cool old notebook, AMD K6 2 500Mhz, 64MB RAM etc etc, you know the sort.

Anyway, i wanted to install ubuntu (i have used knoppix before) but its a pretty hefty OS so this Lite edition is great. So i downloaded and recorded the ISO etc etc installed it all perfectly, logged in with "me" and "none" but i only get to the terminal prompt. I assumed that just installing the ISO image would give me a graphical user interface of some kind??? Or do i need to install the server part first as in the manual HOW TO?

I would appreciate any help in getting my laptop running ubuntu :)

Regards

---

### Post by LostinLinux on 2006-01-01
Sorry, typical noob error...posting without fully reading :(

I forgot:
sudo dpkg-reconfigure xserver-xorg 

God, how i love linux :p

---

### Post by wfx on 2006-01-02
Hi,
i post only what i use maybe you found something usefull.
Display Manager: bash (i use  .bash_profile to automatic log into X)
Window Manager: Openbox
Backgroundimage setting: feh
Set some applicationwindow to a predefined size: devilspie
System information: torsmo
I use a vaio c1ve so for her extra jog wheel: sjog (not relay happy with it)
Development (python): pida
Office: Abiword (none gnome version) and gnumeric
For gtk settings: gtk-theme-switch
Filemanager: mc (thunar would be nice)
Fun: scummvm and dosbox
Video: mplayer-nogui
Music: mpd with ncmpc


**my***~/.bash_profile*:
```

# Stealing form the web :-)
# Start X only if im local and the server is not running.
ps -axc | grep -w xinit
if [ $? = 1 ] &&  [ ! `who loves me | cut -s -f 2 -d "("` ]
then
  startx
fi

```

**my***~/.xinitrc*:
```

feh --bg-scale /usr/share/backgrounds/Serbian_Frost.jpg
xset -b
exec devilspie&
exec torsmo&
exec sjog -ns&
exec openbox

```

**my***~/.torsmorc*:
```

...
TEXT
$nodename - $sysname $kernel on $machine
${color grey}Uptime$color $uptime
${color grey}Time$color $time
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 6}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 6}
${color grey}CPU Usage:$color $cpu% ${cpubar 6}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
${color grey}Battery: ${battery BAT1}
${color grey}Networking:
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
${color grey}File systems:
/ $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Temperatures:
CPU:$color ${i2c temp 1}\uffffC${color grey} - MB:$color ${i2c temp 2}\uffffC

```

**for mpd**
```

cd
mkdir -p .mpd/playlists

```

**my***~/.mpdconf* (Change the music_directory /TO/YOUR/DIRECTORY)
```

# MPD CONFIG FILE
# For a full description of all config parameters,
# Check the mpd man page, "man mpd".

##################### REQUIRED ###########################
port                    "6600"
music_directory         "~/Music"
playlist_directory      "~/.mpd/playlists"
log_file                "~/.mpd/mpd.log"
error_file              "~/.mpd/mpd.error"
##########################################################

##########################################################
# EVERYTHING ELSE IS OPTIONAL
##########################################################

################# FILESYSTEM SETTINGS ####################
#
# If the names of files or directories are
# not correctly displayed then set the
# following to the filesystem coding.
#
#       Usually this is either:
#       ISO-8859-1 or UTF-8
#
# After changing the filesystem_charset
# you will need to recreate the db:
#       mpd --create-db
#
#filesystem_charset "ISO-8859-1"
#
##########################################################

#################### OPTIONAL FILES ######################
#
# Location of DB file
#
db_file         "~/.mpd/mpd.db"
#
# The state file (if set) will be a file
# for storing all current information
# (playlist, playing/paused, etc...) from
# the last MPD session. This will be used
# to recreate your last MPD session after
# restart.
#
state_file              "~/.mpd/mpdstate"
#
##########################################################

################### VOLUME MIXER #########################
#
# Examples:
# ALSA Mixer
mixer_type              "alsa"
mixer_device            "default"
mixer_control           "PCM"
#
# OSS Mixer
#mixer_type             "oss"
#mixer_device           "/dev/mixer"
#mixer_control          "PCM"
#
# Software Mixer
#mixer_type             "software"
#
##########################################################


################## AUDIO OUTPUT ##########################
#
# OSS Audio Output
#ao_driver              "oss"
#ao_driver_options      "dsp=/dev/dsp"
#
# ALSA Audio Output
ao_driver               "alsa09"
ao_driver_options       "dev=hw:0,0"
#
# Set this if you have problems
# playing audio files.
# This will resample your music so
# that it comes out at the set rate.
#
#audio_output_format    "44100:16:2"
#
# You should not need mess with
# this value unless you know
# what you're doing.
#
#audio_write_size       "1024"
#
##########################################################

################# REPLAYGAIN #############################
#
# Use Replay Gain (album or title)
#       http://www.replaygain.org
#
#replaygain             "album"
#
# Sets the pre-amp used for files that have replaygain
# info.  Valid values are between -15 to 15 (in dB).
#
#replaygain_preamp      "0"
#
##########################################################


################ OUTPUT BUFFER SETTINGS ##################
#
# You should not need to mess with this
# unless you know what you're doing.
#
#audio_buffer_size      "2048"
#
# This means exactly what it says, it will
# buffer your file up to the percentage of
# the buffer before it begins playing.
#
#buffer_before_play     "25%"
#
##########################################################


################### HTTP PROXY ###########################
#
# http_proxy_host       "proxy.isp.com"
# http_proxy_port       "8080"
# http_proxy_user       "user"
# http_proxy_password   "password"
#
##########################################################

################# SECURITY SETTINGS ######################
#
# It is encouraged to run MPD as
# non-superuser.  If you start mpd as root
# (for example, in an init script), set
# this value, then  mpd will drop root priveleges
# and runs as the user specified.
#
#user           "nobody"
#
# Set this value if you only have one
# address you want to allow connection to.
#
#bind_to_address        "localhost"
#
# If you want to setup MPD to use
# passwords set them here
#
#password               "password1@read,add,control,admin"
#password               "password2@read"
#
# Specify permissions used by default when no password is
# given by for a connection/client.
#
#default_permissions    "read,add,control,admin"
#
##########################################
################ MISCELLANEOUS OPTIONS ###################
#
# This setting exists as precaution against attacks.
#
#max_playlist_length    "16384"
#
# Valid options are "default", "secure" or "verbose".
#log_level              "default"
#
#connection_timeout     "60"
#
# This should be fine for 2-3 people using clients
# at the same time.
#
#max_connections        "5"
#
# No need to change these unless you know better.
#
#max_command_list_size  "2048"
#max_output_buffer_size "2048"
#
# This will make playlists compatible with normal music
# players.
#
#save_absolute_paths_in_playlists "no"
#
##########################################################

```

Changes: add mpd fun.

---

### Post by jbaloul on 2006-01-03
Hey guys,
First off i think that this project was called for....bless ya'll !!!

If it meens anything, i have been customizing and working with a trimed ubuntu for quite a while that is based on fluxbox, i experimented with damn small linux for quite a while to acheive my goal which was EXACTLY THIS:
***To build an UbuntuLite System which can be installed on any machine whether a secure trimmed server or a low cost work station***

In my case i have installed and tested different types of packages on almost  all types of machines from IBM & Dell rack servers, AMD64s, Dual Cpu's to Pentium 2 garbage machines....I personally administer Trimmed servers of this kind which host other Virtual Servers (Linux, BSD, & windows) using VMWare...I think my expierience from those nail biting sleepless nights can contribute to this type of project...

Anyhow, for the newbies out there, i think it is very important to have them understand that running a LITE desktop does not mean that they cannot enjoy applications that are based on other window managers...

EXAMPLE:
For instance if users wanted to install TSclient (a Gnome Based Remote Desktop & VNC front end application) they would have to understand a few things:
1. All is possible if you install (apt-get install) the correct package with the correct dependancies.
2. To control the look & feel of the application (fonts, colors, skin, etc...) your best bet would be to install something like " gnome-control-center " (and it's dependancies ofcource) because in this case the Gnome application's look and feel is controled by Gnome. If it was a package like Kopete (KDE messenger), or Ksysguard (KDE version of the windows Task Manager) for example i would reccomend installing a package like Kcontrol which provides the features in gnome-control-center but for KDE applications.
3. a lite weight desktop is based on a skeleton system built from minimum packages which provides server like (command line) functionality, whith a Window Manager on top (Window Manager -  the Gui or in other terms X-windows manager, or the Graphical Desktop itself)
4. The Window Manager is a seperate part from the Server itself (windows users will have a difficult time understanding this at first). The Window Manager can be changed, configured or disabled if needed. If disabled it will not effect server applications which run as a daemon (service) like Postifx (a mail server). 
5. If you accidently made a mistake and broke your X-Window-Manager from starting up....PLEASE don't panic, give up, and reinstall Windows. Your system is stil functioning....just the Graphical part of it is not.

I personally would reccomend sticking Synaptic - The Graphical package manager - somewhere visible (Desktop or first in the Menu) as one of the first things a New user will stumble on when he first logs in. (I saw that the package was included)
Many users who come to the Linux World to experiment are confused from all the new package names and have no idea were to start or what to use.



Hope i provided some useful info,
Jacob

P.S keep up the good work!!! & Happy 2006 !!!

---

### Post by christooss on 2006-01-03
For all of you who are listening :)

Is there any chance that Rox-filer could be installed without XFCE dependencies. They are quite large and there are many people who has Dial-up connection. 

Fortunatly this will be solved with Ubuntu-Lite Install/LiveCD. I hope this *thing* will be avalible in few weeks. I just have to find a spare disc and than configure everything. If you guys have any idea for Ubuntu-lite i.e. How to configure IceWM and other applications.

If you think that IceWM should be replaced please report.
If you think of and other solution that will bring Ubuntu-lite to a HIGHER level :) please you are welcome to speak out loud.

Thanks for your post jbaloul and thank you wfx for you configuration suggestions

Again you are welcome to our IRC chanell #ubunut-lite at Freenode

Bye

---

### Post by jbaloul on 2006-01-03
thanks for the invitation my freind....

regarding Ice...cya@irc will discuss there!

jacob

---

### Post by earobinson on 2006-01-03
looking forward to the live cd

---

### Post by LPA on 2006-01-04
Forgive the suggestion, but for us poor slobs that do NOT understand Linux and do NOT program, and still would like to run Ubuntu LITE - is there a version (or can someone make one) that will just install automatically? Like the Ubuntu distributions? Can someone make one single file that can be downloaded, burned to a CD and then booted from?

TiA

Richard / LPA

---

### Post by christooss on 2006-01-04
Not yet. I hope it will be in few weeks.

---

### Post by christooss on 2006-01-04
But for now if you have any questions how to install or any thing else. Please ask

---

### Post by earobinson on 2006-01-04
LPA you should be able to blindly follow the guide to get it to work

---

### Post by DariusTriplet on 2006-01-04
Here's a (somewhat) simplified guide:

1) Put the Ubuntu install CD in the drive and (re)boot your computer.
2) You'll encounter a screen with the Ubuntu logo that asks about the type of installation; type "server" and press ENTER.
3) There will be some screens asking questions; simply follow the directions (or, when in doubt, choose the default option).
4) Ubuntu will install.  After it finishes and the computer reboots, login at the prompt with the name and password you provided during installation.
5) The trickiest part:  You need to edit a text file, **sources.list**, in order to install ubuntu-lite-desktop.

After you log in, type the following:
```
sudo nano /etc/apt/sources.list
```

You'll see some text.  What you want to do is go down the list, and if you see a line that starts with a # symbol and has the word "deb" immediately after, remove the #.  This will allow your computer to access the package servers (known as "repositories") and download/install the files from there.

You'll also want to add another line to the end of the file:

```
deb http://blueeyedcreature.net/ubuntu ./
```

This will allow for your computer to download and install the ubuntu-lite-desktop package, which is the point of this exercise.  :) 

After you add that line, press CTRL-O to save the changes.

6) Only two more commands, and you're ready to go!  Type at the prompt:

```
sudo apt-get update
```

which will let APT (the utility that communicates with the repositories and handles package downloads/installations) know that you changed sources.list.  After that finishes, type:

```
sudo apt-get install ubuntu-lite-desktop
```

This downloads and installs the ubuntu-lite-desktop package.

After that finishes, type

```
sudo reboot
```

to restart your computer.  After the reboot, you should be at a new login screen; if you are, then Ubuntu Lite will have  properly installed!

As previously stated, if you have any questions, please ask; we're more than happy to help!

---

### Post by jbaloul on 2006-01-05
very nice guide Sir DariusTriplet !

jacob

---

### Post by meborc on 2006-01-05
after 
**sudo apt-get update**
i would also include
**sudo apt-get upgrade**
to upgrade the packages already installed with the server install... 
just to make sure everything is up-to-date ;)

---

### Post by mohapi on 2006-01-06
Yay! It works! :D 

I've got it running on a CTX EzBook 700E with 128MB and a AMD K6-2 475Mhz in it (originally it was only 64MB and 233Mhz). 

Now I just gotta figure out how to get my PCMCIA wireless going, and it will be GOLDEN.

Thanks, gang! :cool:

---

### Post by christooss on 2006-01-06
For your wireless just check any Ubuntu howto. It works :) cause after all this is only UBUNTU lite :)

---

### Post by mohapi on 2006-01-06
It's running great. Fast, too. USB ports work nice, which is good, since I'd rather use my USB key to move files to it. 

I'm hacking my way through installing ndiswrapper so I can see if my wireless will work. I'll let you know how it goes.

---

### Post by mohapi on 2006-01-07
Hmm. The ndiswrapper problem has compounded itself. I can't seem to install my wireless without it, but it won't compile for me either. I can't install it off the standard 5.10 install CD, either.

That's OK. I'm going to try a 'server' install from the 5.10 CD next.

Thanks! :smile:

---

### Post by gatorbrit on 2006-01-17
Is it possible to install ubuntu lite on a laptop without an internet connection?  I have an old CTX P133 with 84MB ram.  But I have no way of connecting it to the internet.

---

### Post by earobinson on 2006-01-17
untill they come out with an install cd I dont think so.

---

### Post by wfx on 2006-01-20
Hmmm, is there a way to rebuild ubuntu (base) against uclibc?

---

### Post by sabredog on 2006-01-20
Hmm

I have an old p166 with 96mb RAM and a 1gb HDD. Would Ubuntu Light work on this at all? 

Currently it has Feather Linux on it at the moment.

cheers and thanks

---

### Post by RIOT on 2006-01-27
Edit:  I was able to install it after all.

---

### Post by loell on 2006-02-04
:(  i have a very tragic expirience with ubuntulite 1.1, its not just unstable
its also destructive. it wipe out my disk files that ive been keeping for 12 months

:evil: :evil: :evil:

---

### Post by christooss on 2006-02-04
Sabre dog : Yes

Loell: DONT use install CD use my Howto

---

### Post by crouton on 2006-02-18
I have downloaded the UbuntuLite 1.0 .iso, and it successfully installed on a Compaq Presario 1235.

System Specs:
CPU: AMD K6-266
RAM: 32M
HD: 4GB
Video: NeoMagic NM2160 (MagicGraph 128XD) 2MB
Sound: Aureal of some type (not listed in lspci, still working on this)
Network: None (working to get PCMCIA 802.11g card going)

System boots in about 5 minutes from cold to usable desktop.  IceWM runs fairly nice.

Next tasks are to determine if I can get the machine to compile a new kernel, so I can activate the Aureal.  Should be fun transferring lots of .debs via my USB stick. :)

If you guys need a webpage editor and/or tester let me know.  Is there an IRC channel currently for realtime discussion?

---

### Post by christooss on 2006-02-18
Irc chanell exists but Im the only one there. So everybody are welcome there. Im ready to help and discust.

crouton: Could you please try to install UbuntuLite through this HowTo. And post Boot time. From start to WDM and than till usable desktop

If I can ask you one more thing :) If you will get network card to work please write a litle Howto so all users could know how to fix that. I will put it on the page.

But please come to IRC chanell #ubuntu-lite @ FREENODE

---

### Post by Abdi110 on 2006-02-28
Hi, first time poster. Kind of new to sitting down and messing with Linux for more then 10 min. My only other dabs into it have been Freesco, IPCop (which is awesome if you're looking to get a firewall setup), and Knoppix. Other then that I'm a Windows kid.

I've spent the past week working with my roommate buildind a new media server, since I had some extra time I thought it may be neat to try Linux and see how far I'd go before I'd break out a Windows install disc and get back to setting the system up. It's been almost a week now and I haven't been able to pull my self away from this machine. Ubuntu and Linux rocks.

I'm not ready yet to move away from Windows on my desktop machine as there are a number of programs I haven't found counter parts for and I need to read up about how multi-monitor under Linux, but there isn't much past web browsing that I do on my Thinkpad 570. (:

The system is about 7 years old, p2 350something, with about 128 megs of ram. I used the Ultrabase with cdrom to do the server install, then went step by step with the HOWTO on getting Lite setup. The system takes about 5 min to boot to the login screen, and something like 3 sec to get into IceWM. My random 3com PCMCIA card worked right from install.

After install was done I went ahead and removed the Ultrabase when the system was turned off. If Ubuntu can or can't deal with an undock I really don't care as the only times I've used the base were for drastic things, like an OS install. After reading the dozen or so posts about the Microsoft MN-520 wireless card, I've opted to pick up a new ASUS wifi card when I've got the cash.

Other then that UbuntuLite is great.

The question that a Linux newb like me would ask is what are the differences between Gnome and IceWM? I can see that IceWM starts up a ton faster then Gnome, and is a little liter visually out of the box (which I like), but is there anything Gnome can do that IceWM can't?

Thanks.

---

### Post by nursegirl on 2006-02-28
Does anyone have any screenshots?

---

### Post by gingermark on 2006-02-28
There are these: [http://www.linuxcdmall.com/ubuntulite-screenshots.html](http://www.linuxcdmall.com/ubuntulite-screenshots.html)

They include shots from the install CD christooss says not to use. But there are shots of the installed system, and I **assume** they are relatively accurate?

---

### Post by altainta on 2006-04-10
actually i m interested in UBUNTULITE
but i want to know a few things before trying it
First of all i am noob in linux but can do what u have mentioned in the installation procedure. I want to know and ask a few thing kindly help

I want to know that i want to customize UBUNTU to use a specifice program with no other fancy crap eating up resources.

I want to also know that how come SCREEN comman work ?

suppose i am using DOS  (a example for console)
i started format which will take atleast 1 hr ( by guessing) and i want to use other program for editing a text file suppose edit.com. How come i will make it.
I know it is called multitasking and i also know that it is possible in linux but can u explain me the UBUNTU way ?

---

### Post by dmizer on 2006-04-13
loaded ubuntu-light on my toshiba techra 8100 laptop last night.
piii 700mhz
128meg ram
2gig hdd

this machine screams with ubuntu light.  boot is under 2 minutes, and i'm up to a useable desktop in seconds.

only two problems, and i'm working on that:
1) sudo doesn't work right. (edit: fixed ... just got the updates and now it works)
2) sound doesn't work.

---

### Post by christooss on 2006-04-13
Thanks for reports

Please do post your tests on our page which is up and runing

[http://www.ubuntulite.org/dokuwiki/doku.php?id=performance](http://www.ubuntulite.org/dokuwiki/doku.php?id=performance)

There are no articles jet but fill free to add them at wiki

---

### Post by dmizer on 2006-04-22
just popped in to add, this setup rocks.  i am able to play dvds with no skip and perfect sound on a 700mhz pc with 128meg of ram (wasn't possible in windows ... i had to get more ram to get smooth playback).

i still havn't resolved all my sound problem. i was suprised to learn that sound worked for my dvd player, but not for gaim.

i will post in the ubuntu lite wiki once i get sound to work properly.

finally found the time to fix the sound.  just edited /etc/libao.conf so that it said: default_driver=alsa

---

### Post by GoodPanos on 2006-05-24
Still don't understand how you get the icons on the desktop.  :-k   For instance the Firefox icon.

Any steps on how to do this??

---

### Post by dmizer on 2006-05-26
[QUOTE=GoodPanos]Still don't understand how you get the icons on the desktop.  :-k   For instance the Firefox icon.

Any steps on how to do this??[/QUOTE]
i've read it's possible, but requires more hoops than i'm willing to jump through.  it might partly be becuse that's one of the ways that icewm saves resources.

not enough that firefox is right down there on your tool bar? ;)

---

### Post by jon_benge on 2006-05-26
If you want desktop icons then you need to install ROX-FILER. [Click here]("http://www.ubuntuforums.org/showthread.php?t=171203") for a tutorial on installing ROX.

If you follow the guide in that thread, you will end up with some great eye candy. Check out these attachments

---

### Post by confused57 on 2006-05-30
Just installed Ubuntu Lite on my 500 Mhz, 256 ram and I'm really liking what I've seen thus far, quite a bit different from using (X)(K)ubuntu, but I'm trying to learn my way around the system.  It's installed on the Dapper RC server version.

I tried installing xubuntu-desktop, thinking I could do so and just switch session at the wdm login; but I get a message about the Xfree86-common and score-181, and I'm unable to install the xubuntu-desktop using "sudo aptitude install xubuntu-desktop".  Are there some dependencies or something I need to resolve in order to install it or is it even possible?

Also, can I  install gdm or kdm as an alternate login manager?

Great job on the Ubuntu Lite project.   I'm reading the links and suggestions in this thread, so maybe I'll reach at least a mediocre level of proficiency using Ubuntu Lite.  I've only been using Linux for about 5 months, a lot of fun, but miles to go.

---

### Post by dmizer on 2006-05-30
[QUOTE=confused57]Also, can I  install gdm or kdm as an alternate login manager?[/QUOTE]
wdm was chosen for its light weight.  gdm or kdm will slow you down quite a bit on boot.  but other than that, there's nothing to stop you from changing your boot manager.

---

### Post by dmizer on 2006-06-01
is it possible/recommended to upgrade the base of ubuntu lite to dapper?

---

### Post by confused57 on 2006-06-02
I installed Ubuntu-Lite on the Dapper server install, but that doesn't really answer your question...

---

### Post by nugget on 2006-07-24
I was wondering how easy or hard it would be to swich to fluxbox but keep all the stuff that you get from ubuntu-lite package or what ever it is called?

I kinda know my way around linux and I've read quite a bit but I'm still very noobish to put it. I've used many window managers and I love fluxbox when I used DSL. And I would love to go light weight, I've done it before, but I like fluxbox more so I was just wondering. I have an idea that it would not be very hard, but then I would want to get rid of IceWM and all the extra stuff that it has that I don't need, like some of the libs and such because that would just be a waste. I know that installing it would be very easy, apt-get install fluxbox or what ever the package is called. but removing IceWM and the libs and depencencies that I don't need would be a lot more difficult for me.

---

### Post by tripleee on 2006-08-04
If you want fluxbox (or in my case sawfish) instead of icewm, just install that as well on top of what you already have, and tweak your .Xsession to use that instead of the default ... or if you're on a single-user system you could update-alternatives to use your preferred window manager as the system-wide x-window-manager. You can have several window managers installed, they generally don't conflict.

The package manager is smart enough to remove unused libraries, so when you uninstall icewm you should see other packages go along with it (for example, icewm-common).

---

### Post by gholen on 2006-08-11
Just a tip about Ubuntu Lite!

apt-get the wonderful rxvt-unicode!

This is a development of the rxvt terminal, and it supports transparency, and lots of other stuff!
And the best thing of it all, it&#347; fast, light and does start in less then a second (my system is a 200mhx, 48 MB ram and 3,2 GB hard drive):D 

// Ambjörn AKA gholen

---

### Post by ashrack on 2006-08-27
I installed XUBUNTU-DESKTOP on a P2 350@390MHz with 196MB RAM! And the system is very slow and is constantly trashing the swap file!
So is there a way that I could totally remove XUBUNTU-DESKTOP and have the system in a similar state as if I were to do a SERVER install so I could then follow the guide!!
ps. I would prefer going for a fresh install but I cant since 3other CLIENT computers are dependant on it for Internet Sharing.

---

### Post by confused57 on 2006-08-27
I don't know if this would work or not:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by dmizer on 2006-09-21
i hope it's not too late for this to be of use to you:

> **ashrack said:**
> ps. I would prefer going for a fresh install but I cant since 3other CLIENT computers are dependant on it for Internet Sharing.

i was in a similar situation a while back.  i needed to do some hardware upgrades as well as thin out the software and change up the system (i got rid of all my gui's).  anyway, long story short, i employed an ancient 500mhz docked laptop running knoppix as a substitute.

docked because the dock had an ethernet port and the laptop didn't (eth0) and i used an old pcmcia network adapter i dug out of a box for eth1 :-P  kind of a frankenstein setup but hey ...

with knoppix, i was able to make use of my network attached storage, do nat, samba, dns, ssh server, netbeui domain resolution, as well as firewall and port forwarding.  worked flawlessly for the week.  not a hiccup.

wasn't pretty, but hey ... can't complain about results.

---

### Post by Ziptar on 2006-09-24
I just installed Ubuntu Lite on an Old Dell Lattitude CPx J650GT. I had Ubuntu on it already but, I had some odd package installation issues, I was going to reinstall anyway so I thought I'd give lite a try... like it so far takes me back years to when I worked in Solaris. I am really rusty with X and the command line after years of windows server admining but, I think I'll keep lite, it's clean and minimal.. I like that...

the Live 1.1 CD wouldn't install for me so I did the server install and then the packages accoring to christooss's how to here. Worked just fine. The PCMCIA and the [$17.49 Ralink RT2500 card]("http://www.ubuntuforums.org/showthread.php?t=262842") I bought were detected and installed when I checked with lshw all I had to do was edit /etc/network/interfaces to

```
# The loopback network interface
# auto lo
# iface lo inet loopback

auto ra0
iface ra0 inet dhcp
pre-up iwconfig ra0 essid mywirelessessid
pre-up iwconfig ra0 key off
```

and I was off and running, I still need to go back and doo some of the stuff kultex pointed out earlier in the thread and I may install ROX. I have a few questions first thought...

My USB Pen won't automount I have ivamn and usbmount installed but I still need to do ```
sudo su
mkdir /media/usbi
mount t- auto /dev/sda1 /media/usbi
```
to get it to work.. is that the best I can do??

I have an HP PSC 2510 Wireless All in one I need to setup but, when I click HPLIP Toolboox I doesn't start. Should I install HPLIP 1.6.9 ????

Can anyone give me some tips on tweaking the Alps Touchpad?? It works but it's pretty wonky.. I [found a thread here]("http://www.ubuntuforums.org/showthread.php?t=78904") but, I am not sure how much of it applies to lite??

and can someone recommend me a good GUI file manager?? I installed fileruner but, it leaves alot to be desired, is there one out there similar to Ubuntu's??

Thanks

---

### Post by dmizer on 2006-09-26
for all of your issues, you can just use the guides here.  as long as the directions are written with terminal commands, you'll be okay.  (if no terminal commands are given, ask for them).

as for your usb pen, you might be able to correct the situation by adding an entry to fstab.

---

### Post by Ziptar on 2006-09-26
Thanks dmizer, I'll start setting stuff up and see how it goes...

BTW I was re-reading kultex's post and some how I missed this the first time, if it doesn't work I'll try fstab.

```
AUTOMOUNT with ivman: To get the automount function working, create with mousepad a file named startup in
$HOME/.icewm:

#!/bin/sh
exec /usr/bin/ivman

then you have to make startup executable:

$ chmod +x /.icewm/startup

in rox it works perfect - in emelfm you can not unmount the devices
```

---

### Post by dmizer on 2006-09-26
let me know how that works out for you, and if you experience any slowdown as a result.

remember icewm is a very lightweight desktop because it's cut back on some of the "unnecessary" features that slow things down, so some things you would otherwise do with the gui will have to be done by command line.  it's the price we pay for speed.  the more you add to icewm to make it act like gnome or kde, the slower icewm will be.

---

### Post by Ziptar on 2006-09-27
I got ROX on the desktop and Automount via ivman working last night. Now slowdown that is noticeable so far. Ivan automounts my USB Pen and CD. I can't eject the CD though once it's mounted. I'll have to look into that.

Anyone know how I can configure NUMLOCK off when icewn starts?? each time I retart it my numlock turns on again??

---

### Post by Zed on 2006-09-27
You probably have numlockx installed.

```

sudo apt-get remove numlockx

```

---

### Post by aldar on 2006-10-12
I have installed Ubuntu Lite and everything is ok except that my startup file isn't working. I have the file in my $HOME/.icewm dir, it's called "startup", it is read and executable by all. I have only one line in it:
     rdesktop -u "" -g 800x600 192.168.0.55 -f
I used to have this above that: #!/bin/bash    but made no difference.
When I startx, the icewm desktop comes up, but no rdesktop. If I then manually run the startup file from icewm, rdesktop starts just like it should. What am I missing?

---

### Post by eeried on 2006-10-13
> I was wondering how easy or hard it would be to swich to fluxbox but keep all the stuff that you get from ubuntu-lite package or what ever it is called?
snip
I would want to get rid of IceWM and all the extra stuff that it has that I don't need, like some of the libs and such because that would just be a waste. I know that installing it would be very easy, apt-get install fluxbox or what ever the package is called. but removing IceWM and the libs and depencencies that I don't need would be a lot more difficult for me.


This is exactly what I'd like to do and there has been no satisfying answer yet.

> The package manager is smart enough to remove unused libraries, so when you uninstall icewm you should see other packages go along with it (for example, icewm-common).

Not exactly smart enough.

I think a decent install option would be to install from the alternate Ubuntu CD: server install. Then when you install the lite desktop, use aptitude instead of apt-get: aptitude keeps track of all dependencies more completely than apt-get. When you want to remove IceWM: do ```
aptitude remove --purge icewm.
```
It shouldn't matter if the lite-desktop package is removed too (at least not until you upgrade to a future release of Ubuntu-Lite). I know Xubuntu is all right without its xubuntu-desktop package.

With "aptitude install" and "aptitude remove" you should be allright.

However, this may not be the solution, so please help!

PS: Hello, Christoos, I think Fluxbox instead of IceWM should be included in Ubuntu Lite for lightness sake (and Fluxbox rocks!)

---

### Post by dmizer on 2006-10-31
> **Ziptar said:**
> I got ROX on the desktop and Automount via ivman working last night. Now slowdown that is noticeable so far. Ivan automounts my USB Pen and CD. I can't eject the CD though once it's mounted. I'll have to look into that.
to eject the cd, you have to unmount first.  in rox, you can right click on the cdrom folder in /media (i made a shortcut for this folder on my desktop ... see attached screenshot) and select unmount.  then you can eject the cdrom.  or you can just unmount it with the cli:
```
sudo umount /media/cdrom
```

i noticed a significant increase in time required to load the icewm desktop after enabling ivman and automounting my nfs shares.  desktop still loads faster than xubuntu, and once it's loaded ... she still screams.

> **eeried said:**
> PS: Hello, Christoos, I think Fluxbox instead of IceWM should be included in Ubuntu Lite for lightness sake (and Fluxbox rocks!)
i'm not a developer, i have just adopted this thread because i love how icewm revived my old laptops.

but i do know that icewm was chosen because of it's more shallow learning curve.  believe me, i know fluxbox rocks (come on ... see through panels anyone?), but icewm is much easier for a first time user who just wants to browse, send email, and chat.

here's my current screen shot.  auto mounted home folder, auto mounted nfs, auto mounted usb thumb drive, and auto mounted cdrom on the desktop :) ... using the GreenBuntu theme.

---

### Post by ipok on 2006-11-03
v

---

### Post by HydroDiOxide on 2006-11-17
Tried this HOWTO on an 6.10 command line install but when i try to install the ubuntu-lite-desktop I get an error E: Broken Packages with a whole lot of Depends: ... but it is not installable

What might be wrong?

SOLVED forgot to uncomment additional repositories.

---

### Post by lemonsCC on 2006-11-26
My internet keeps going out with Ubuntu Lite.  It works until I try to startX...  I only know it works in the CLI because I can spt-get

Any tips?

---

### Post by dmizer on 2006-11-26
> **lemonsCC said:**
> My internet keeps going out with Ubuntu Lite.  It works until I try to startX...  I only know it works in the CLI because I can spt-get

Any tips?

you're probably getting stuck with ipv6, but i'm not sure.

open firefox and browse to about:config
search for ipv6 and disable it by double clicking on it.
restart firefox and try again.

---

### Post by jis on 2007-01-22
> **kultex said:**
> 
[...]
SHUTDOWN: after login you will have problems to turn off your computer, because the halt of the shutdown menu is not working.

open xterm

$ sudo /sbin/shutdown -h now

it will shut down - with sudo /sbin/shutdown -r now   it will reboot

to make it more easy for the next sessions:

you open xterm:

$ sudo visudo

you add the following line:
your_username ALL=(root) NOPASSWD: /sbin/shutdown

to save press F2   to exit F10

$ sudo mousepad /etc/X11/icewm/preferences

you insert the following lines to the 6.th line of the document

ShutdownCommand="/sbin/shutdown -h now"
RebootCommand="/sbin/shutdown -r now"

you save the document, restart iceWM.
Shutdown and reboot from strg+alt+del - menu are now working
---------------------------------------------------------------------------------------------
[...]
----------------------------------------------------------------------------------------------
[...]
SECURITY: Copy the files /etc/X11/icewm/menu+toolbar+preferences with emelfm or rox to $HOME/.icewm since modifications to this file will be discarded when you (re)install icewm.
[...]
-------------------------------------------------------------------
AUTOMOUNT with ivman: 
[...]
in rox it works perfect - in emelfm you can not unmount the devices
]

First of all, thanks for the instructions, Kultex. Everything didn't work for me, though.

As for SHUTDOWN: "sudo /sbin/shutdown -h now" does not work for me. If I run it from a terminal I end up in console where the last text is like this: my_computer_name login [3783.010513] Power down. It does not help, if I add P option for shutdown command. I did also the changes "to make it more easy for the next sessions", but only login does work in the login screen :(. My best option is to exit to login screen, press Alt-SysRq-s Alt-SysRq-u Alt-SysRq-b and power button during reboot to turn off computer, I guess. Is it critical to put the two lines in  /etc/X11/icewm/preferences exactly starting at the 6th line of the file? Is it neccessary to restart IceWM; isn't reboot enough? BTW. strg is better known as Ctrl.

As for SECURITY: If I copy the files like you suggest, and modify e.g. /etc/X11/icewm/toolbar the changes do not take place; I have to modify the copy under home directory.

As for AUTOMOUNT: I can not unmount USB flash drive. In terminal, umount command outputs
> umount: /media/USB DISK is not in the fstab (and you are not root). I wonder , if it is safe to remove the drive without unmounting. Anyway, if I do, the mount point disappears from /media directory.

BTW: During bootup I get this message: [   42949372.960000] ACPI: Unable to locate RSDP.
How do you copy text from XTerm to another application?

---

### Post by jis on 2007-01-22
Is it possible to upgrade Ubuntu Lite to Edgy or other later ubuntu version? At least HydroDiOxide has reported in this thread he has applied this howto for ubuntu 6.10...

What is the best way to keep Ubuntu Lite updated? Is it "sudo aptitude update && sudo aptitude upgrade" regularly?!

---

### Post by confused57 on 2007-01-22
This method worked for me to enable shutdown/reboot from the login screen:
[http://www.opensubscriber.com/message/xubuntu-devel@lists.ubuntu.com/2579245.html](http://www.opensubscriber.com/message/xubuntu-devel@lists.ubuntu.com/2579245.html)

I had a problem with Xubuntu6.10 shutting down completely, haven't heard of the problem with Dapper, but here was the fix:
[http://www.ubuntuforums.org/showthread.php?t=318414&highlight=shutdown](http://www.ubuntuforums.org/showthread.php?t=318414&highlight=shutdown)

Also, you'd need to use sudo to umount your USB DISK:
```
sudo umount /media/USB
```
or wherever it's mounted.

Here's some instructions for using the pico editor(I think it's similar to nano):
[http://www.lowfatlinux.com/linux-editor-pico.html](http://www.lowfatlinux.com/linux-editor-pico.html)

man nano may give some useful instructions...

Also, you may want to save the output of commands in terminal to a text file, e.g.
```
lsmod > lsmod.txt
```

That way, you'll have a text file with the command output saved to a text file that you can refer to.

---

### Post by jis on 2007-01-22
Thanks, confused57.  I had to do the both tricks to be able to properly shut down. I installed ubuntu-lite-desktop on top of ubuntu server 6.06.1 and later updated system in terminal by
```
sudo aptitude update && sudo aptitude upgrade
```. 

In contrary what you say, I can mount USB DISK without sudo. It happens automatically when I stick an USB flash drive in and then click its mount point in rox or emelfm. (I have done what has been told in the AUTOMOUNT section of [these instructions]("http://ubuntuforums.org/showpost.php?p=543661&postcount=4").) Only when I would like to unmount the USB DISK before removing it physically I get the described error.

---

### Post by jis on 2007-01-22
> **confused57 said:**
> 
Also, you may want to save the output of commands in terminal to a text file, e.g.
```
lsmod > lsmod.txt
```

That way, you'll have a text file with the command output saved to a text file that you can refer to.

OK, but in Xubuntu's terminal you can copy-paste any text by right-clicking the text selected by mouse. I guess this kind of behavior is not possible in Ubuntu lite.

---

### Post by x_helium on 2007-01-26
SUCCESS!!!

Here was my process for getting Ubuntu Lite on a 2GB USB pen drive, written for relatively new Linux users like myself (Using IBM T30)

1.  Remove hard drive
2.  Attach USB pen drive
3.  Power on and boot to Ubuntu server install disk
(It took the BIOS a little bit to recognize that the hard drive was missing.  It may seem like the notebook is hanging but be patient.  The BIOS will recognize the USB drive as the only hard drive)
4.  Choose to install to hard drive (Default Option)
5.  The install from here is the same as a regular server install.  GRUB will auto load onto /dev/sda with no problems.  (The install is much slower than a CD to HD install)
6.  Once the install is complete, remove CD and reboot to USB drive (Keep HD removed)
7.  Edit sources.list
$sudo nano /etc/grub/sources.list
8.  add a line:
deb [http://blueeyedcreature.net/ubuntu](http://blueeyedcreature.net/ubuntu) ./
9.  Uncomment all other repos by removing the # a the begging of the line
10. $sudo apt-get update
11. $sudo apt-get install ubuntu-lite-desktop

End of the install

Thanks to all those that have posted!

---

### Post by jis on 2007-01-27
I can not umount USB DISK as normal user in terminal, rox or emelfm, but I can by thunar.

---

### Post by dmizer on 2007-01-28
> **jis said:**
> OK, but in Xubuntu's terminal you can copy-paste any text by right-clicking the text selected by mouse. I guess this kind of behavior is not possible in Ubuntu lite.

all you need to do is highlight the text you wish to copy.  HIGHLIGHT ONLY, no right clicking or anything.  then to paste, simply middle click (clicking the mouse wheel works if you don't have 3 mouse buttons) where you wish the past to go.

this will work from any application into any other application.  for example, highlight text in a howto in firefox, and middle click in the terminal, and the command will appear.  too boot, it saves you two clicks!

by the way, this behavior works in ALL distributions of ubuntu (ie, you can copy/pase with this same method in xubuntu too).

as far as unmounting the usb disk ... you just need to be aware that one of the reasons ubuntu lite is so quick is that it dispenses with some of the conveniences avaliable to you in some of the other ubuntu releases.  unfortunately, this means that the best way to unmount removable media is via sudo at the command line.

---

### Post by jis on 2007-01-29
Thanks for the hint, dmizer.

---

### Post by jis on 2007-01-29
I added a regular user by command adduser USERNAME. Is there better way, maybe Graphical UI? (Xubuntu has users-admin.) Anyway, when logged as the created user, I can not mount USB DISK (error: permission denied) and I can not unmount cdrom (error: only the other user can unmount it.)

---

### Post by jis on 2007-02-06
I am now able to mount USB DISK as an additional regular user after I commanded sudo adduser USERNAME plugdev, but I still can't unmount. I can't unmount cdrom either. Anybody else have tried adding users in their Ubuntu lite system?

---

### Post by kultex on 2007-02-17
@jis

my howto was written long time ago - for 5.10 - so things could have been changed - if you have any suggestions I change it.

I have to set up an audioserver within the next days with 6.06, so I have to get into it again

The unmount problem: I am not a fan of those automount things, which are not made for desktops like icewm or fluxbox and causes there nothing else than problems....  the problem is, that ubuntu is adding the automount tings also to the server installation - if you use just a normal debian installation, you can do all the stuff in the menu and fstab - like the menu entry for ejecting is:   

prog "unmount cdrom" "cdumount.png" xterm -e "/usr/bin/eject /media/cdrom"

and that workes there for shure

kultex

---

### Post by noalternative on 2007-03-06
Since the website is down, I thought people would like to know that support for ubuntu-lite has switched to the [ubuntu-lite mailing list]("http://groups.google.com/group/ubuntu_lite") at google.

Also if the repository goes down in the future it is possible to install the ubuntu-lite desktop from files at the google site.

just manually download ubuntu-lite-desktop.deb , you may have to join the list to do this. 

sudo dpkg -i ubuntu-lite-desktop_0.3_i386.deb

If you get dependency errors "sudo apt-get -f install"

Also, since breezy is going to be obsoleted in the next couple of months, the installation instructions need to updated.   You need to do a server install from the "server install cd" with all versions of ubuntu after breezy.

We also have a tiny xserver called xvesa at the google list.  If you use jwm or openbox along with this it is possible to operate ubuntu with as little as 16 mb of memory.  Ofcoarse you need to manually install a word processor, file manager, terminal program and browser etc, but it can be done, just ask for advise.

There are also some other goodies at the list, like icebuntu icewm theme, which looks alot like the default gnome desktop,  the ubuntu wallpapers to match it, I nice lite but full featured paint program called mtPaint, and a version of fvwm-crystal that works with dapper.  There is also the latest version of jwm in tar.bz2 form.  The default dapper version is very old.

---

### Post by noalternative on 2007-03-09
kick:popcorn:

---

### Post by noalternative on 2007-03-15
Just updated some information on some files at the mailing list on the previous post.:guitar:

---

### Post by dimeotane on 2007-03-18
I'm curious if this install method could get a lite version of ubuntu onto an Ebox-2300:

for $106 you get a palm sized cpu.  the ebox-2300 is a 200mhz-128meg PC with compact flash storage.

Check out the [ebox-2300]("http://www.wdlsystems.com/modperl/view_services.cgi?r=detail&prod_num=1EBOX23&aisle_id=799")

Right now the puppy linux enthusiasts are trying out the ebox-2300.   They say ubuntu is too bloated.  How much disk space does this minimal install require?  Would it fit on a 1 GB or 2GB compact flash?   The next thing to figure out is if the ethernet, sound, and graphics are detected correctly.... 

Perhaps ubuntu-lite can make this work?

---

### Post by jah2007 on 2007-03-25
Hi
is Ubuntu Light still around?
Can it run on ppc Imac g3?

---

### Post by dmizer on 2007-03-25
> **dimeotane said:**
> I'm curious if this install method could get a lite version of ubuntu onto an Ebox-2300:

for $106 you get a palm sized cpu.  the ebox-2300 is a 200mhz-128meg PC with compact flash storage.

Check out the [ebox-2300]("http://www.wdlsystems.com/modperl/view_services.cgi?r=detail&prod_num=1EBOX23&aisle_id=799")

Right now the puppy linux enthusiasts are trying out the ebox-2300.   They say ubuntu is too bloated.  How much disk space does this minimal install require?  Would it fit on a 1 GB or 2GB compact flash?   The next thing to figure out is if the ethernet, sound, and graphics are detected correctly.... 

Perhaps ubuntu-lite can make this work?
i've managed to install ubuntu lite on a 2gb hard drive, but there's not a lot of room to spare, so kernel upgrades are tricky, and you have to make sure you delete all your old kernels.  you'll really need to be conscious of disk space usage.

in ubuntu lite, hardware detection is equal to that of full blown ubuntu.  iow ... if it works in ubuntu/xubuntu, it will work in ubuntu lite.  but hardware configuration will be (for the most part) restricted to the command line.

as for it working on that specific hardware ... i really have no idea.

> **jah2007 said:**
> Hi
is Ubuntu Light still around?
Can it run on ppc Imac g3?

according to this post: [http://ubuntuforums.org/showpost.php?p=2258562&postcount=78](http://ubuntuforums.org/showpost.php?p=2258562&postcount=78) ubuntu lite is still alive, but the most activity for it is taking place on the mailing list.  you should be able to install ubuntu lite on a ppc as long as you start with a command line only install.  though ... i have not tried this, so i can't confirm direct experience with this, and a cursory search through this thread doesn't turn up any other ppc posts.

---

### Post by noalternative on 2007-04-06
> **noalternative said:**
> Since the website is down, I thought people would like to know that support for ubuntu-lite has switched to the [ubuntu-lite mailing list]("http://groups.google.com/group/ubuntu_lite") at google.

Also if the repository goes down in the future it is possible to install the ubuntu-lite desktop from files at the google site.

just manually download ubuntu-lite-desktop.deb , you may have to join the list to do this. 

sudo dpkg -i ubuntu-lite-desktop_0.3_i386.deb

If you get dependency errors "sudo apt-get -f install"

Also, since breezy is going to be obsoleted in the next couple of months, the installation instructions need to updated.   You need to do a server install from the "server install cd" with all versions of ubuntu after breezy.

We also have a tiny xserver called xvesa at the google list.  If you use jwm or openbox along with this it is possible to operate ubuntu with as little as 16 mb of memory.  Of coarse you need to manually install a word processor, file manager, terminal program and browser etc, but it can be done, just ask for advise.

There are also some other goodies at the list, like icebuntu icewm theme, which looks much like the default gnome desktop,  the ubuntu wallpapers to match it, A nice lite but full featured paint program called mtPaint, and a version of fvwm-crystal(transparency without an opengl compatible graphics driver) that works with dapper.  There is also the latest version of jwm in tar.bz2 form.  The default dapper version is very old.

ubuntu-lite 7.04 is currently being developed by mailing list  member Shae Smittle.  He has a survey out, where you can tell him about features you would like to see in the next release.  [Click here.]("http://www.surveymonkey.com/s.asp?u=406643633786"):KS

---

### Post by noalternative on 2007-04-06
evening kick.

---

### Post by noalternative on 2007-04-08
> **noalternative said:**
> ubuntu-lite 7.04 is currently being developed by mailing list  member Shae Smittle.  He has a survey out, where you can tell him about features you would like to see in the next release.  [Click here.]("http://www.surveymonkey.com/s.asp?u=406643633786"):KS


Shae Smittle, the developer of Ubuntu-lite 7.04, is refining his package
selection choices.  He has put out a second survey, which is public and
can be accessed [here]("http://www.surveymonkey.com/s.asp?u=468313642585").  

The survey also allows you sign up as a tester. If you would like direct
contact with the developers, please [visit the mailing list.]("http://groups.google.com/group/ubuntu_lite") ):P

---

### Post by noalternative on 2007-04-09
> **noalternative said:**
> Since the website is down, I thought people would like to know that support for ubuntu-lite has switched to the [ubuntu-lite mailing list]("http://groups.google.com/group/ubuntu_lite") at google.

Also if the repository goes down in the future it is possible to install the ubuntu-lite desktop from files at the google site.

just manually download ubuntu-lite-desktop.deb , you may have to join the list to do this. 

sudo dpkg -i ubuntu-lite-desktop_0.3_i386.deb

If you get dependency errors "sudo apt-get -f install"

Also, since breezy is going to be obsoleted in the next couple of months, the installation instructions need to updated.   You need to do a server install from the "server install cd" with all versions of ubuntu after breezy.

We also have a tiny xserver called xvesa at the google list.  If you use jwm or openbox along with this it is possible to operate ubuntu with as little as 16 mb of memory.  Ofcoarse you need to manually install a word processor, file manager, terminal program and browser etc, but it can be done, just ask for advise.

There are also some other goodies at the list, like icebuntu icewm theme, which looks alot like the default gnome desktop,  the ubuntu wallpapers to match it, I nice lite but full featured paint program called mtPaint, and a version of fvwm-crystal that works with dapper.  There is also the latest version of jwm in tar.bz2 form.  The default dapper version is very old.

Shae Smittle, the developer of ubuntu-lite 7.04 is doing a [3rd survey]("http://www.surveymonkey.com/s.asp?u=552243643682.") on
Ubuntu-lite.


Among other things the desktop package choices are now between openbox/rox
and ede.  Please visit the survey if you would like to weigh in.  If you
would like to contact the developers directly [visit the list]("http://groups.google.com/group/ubuntu_lite")

---

### Post by noalternative on 2007-04-10
> **noalternative said:**
> Shae Smittle, the developer of ubuntu-lite 7.04 is doing a [3rd survey]("http://www.surveymonkey.com/s.asp?u=552243643682.") on
Ubuntu-lite.


Among other things the desktop package choices are now between openbox/rox
and ede.  Please visit the survey if you would like to weigh in.  If you
would like to contact the developers directly [visit the list]("http://groups.google.com/group/ubuntu_lite")

evening bump.:popcorn:

---

### Post by shae on 2007-04-17
Wow.  My name seems popular in this post.  Yes I am working on updating Ubuntu-Lite.  

The last maintainer is MIA.  I am currently contemplating the how to turn the results of the preferences of the community into a light, easy to use desktop.  This can be tough and would love any help I can get.  I am going to start a list of the tentative schedule.  

As soon as 7.04 goes gold, I am going to create the package for beta testing of the package selection.  Then we will need to find and create the proper artwork.  

I am sure there are several dependency errors with the old package.  It was made for 6.06.  It needed a overhaul and I have made good progress on it.  But I will need lots of help and people with systems that they can hose for a little bit to get the best choices for packages.

In summation:
1) Ubuntu-Lite 7.04 is in the works.
2) We will be needing voices and help testing, please visit the aforementioned google group.
3) If you have that old PC sitting in the back or want to be on the cutting edge of speed, I hope Ubuntu-Lite will be for you.
  
P.S. I am looking into making for TinyX something similar to the Restricted drivers manager in 7.04, but to do this I will need people with the hardware to help testing.  I only have a computer with a i810 integrated video chipset to test it on.

---

### Post by blackpaw on 2007-06-26
Heya.

> **noalternative said:**
> 
Also if the repository goes down in the future it is possible to install the ubuntu-lite desktop from files at the google site.


Sorry for going missing aswell, I have had "things" to do.. 
The ubuntu lite repository is on my server, it will not go down unless I cause gigs of traffic with it.. which is unlikely to happen as it is a pretty lo-fi thing that only few people will be using. 

Shae offered to continue the support for ubuntu lite and eventually update the package.. if you need a place to host a forum or a small website/wiki let me know.

cheers, 


andreas

[EMAIL="ubuntu@blueeyedcreature.net"]ubuntu@blueeyedcreature.net[/EMAIL]

---

### Post by eeried on 2007-06-27
> i've managed to install ubuntu lite on a 2gb hard drive, but there's not a lot of room to spare, so kernel upgrades are tricky, and you have to make sure you delete all your old kernels. you'll really need to be conscious of disk space usage.

I've installed Xubuntu on a 2GB HDD.

Would it be advisable to join forces with the Fluxbuntu team rather then go on with the Ubuntu-Lite project? I would suppose those who don't like Flux could install IceWM.

cheers

---

### Post by noalternative on 2007-09-21
The ubuntulite project has been revived and is being lead by Shae Smittle.  The new version is in beta testing, and is to be based on open-box wm, and fbpanel, with the slim display manager.   

In order to install it follow these instruction.

[http://ubuntuforums.org/search.php?searchid=27525257](http://ubuntuforums.org/search.php?searchid=27525257)

We need testers.  

BTW, you should not install the old version of ubuntu-lite on anything after dapper drake. :KS

---

### Post by elect on 2007-11-11
How can i use remote desktop? Vino doesnt work... -.-

---

### Post by quantboy on 2008-01-05
> **noalternative said:**
> The ubuntulite project has been revived and is being lead by Shae Smittle.  The new version is in beta testing, and is to be based on open-box wm, and fbpanel, with the slim display manager.   

In order to install it follow these instruction.

[http://ubuntuforums.org/search.php?searchid=27525257](http://ubuntuforums.org/search.php?searchid=27525257)

We need testers.  

BTW, you should not install the old version of ubuntu-lite on anything after dapper drake. :KS

How's this coming along?  I've an old computer I can try UbuntuLite on.  That link above points to a blank page.

---

### Post by K.Mandla on 2008-01-10
Try 

[http://ubuntulite.tuxfamily.org/](http://ubuntulite.tuxfamily.org/)

:D

---

