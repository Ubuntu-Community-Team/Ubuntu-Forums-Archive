---
title: "HOWTO:script for install additional packages after installation"
date: 2005-05-26
forum: Outdated Tutorials &amp; Tips
---

### Post by evermind on 2005-05-26
I just wrote a script which handles / automate the first time install of packages and other useful stuff after an installation

My goal was:
- relative easy to customize and extend

FEATURES:
- add sources to /etc/apt/sources.list
- console-based-menus to select packages 
- a --noask option is available it will not ask you for any input (hope so)
- some more options are available
- and lately I created a GUI with zenity for it. BUT i dislike GUIs so I
  will spend no more time on it it was just for fun and edu ;)
**v0.3**
- easier to add packages in the VARS
**v0.4**
- internal changes
**v0.4.2**
- added fixes for hoary (in functions)
  *hoary-sound-fix: [http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)
  *enable_network_autoconfiguration
  ./ubuntu-addons.bash_v042_uf -nu --fixes-only
**v0.4.4**
- fixes asound.conf fix-part as extra options (due to errors)
  added default .qt/qtrc
**v0.5**
 *added a function to disable screensaver in gmplayer and vlc (for all users)
 *added a function to generate default-configs for bmp/xmms (for all users if not exist)
               invoke the script with --fixes or --fixes-only and optional with --no-update
 *(fixed package ivman-0.5_pre3-3_i386.deb (now it starts/stop after/before dbus))
 *added display-version: invoke the script with --v  or --version
**v0.5.2**
 *bugfixes:fix user_name to user_names
 *(fixed ivman again package NEW: ivman-0.5_pre3-4_i386.deb (now it hopefully starts/stop after/before dbus))
 *function replace_string uses now sed instead of awk to substitute
 *bugfix: function tool_wget now won't exit after regular file-fetching
**v0.5.4**
# v0.5.3 2005-06-04 *bugfix: prepare strings for sed use, tuning replace_string function
# v0.5.4 2005-06-08 added function (install_apt_pkg) to handle apt-get errors with a package.
#	if installing packages together fail the script tries to install each package after the other
#	some new packages: lynx, nmap, gpm, vim-gnome, mp3blaster
#	dep issues with micq for sarge --> now we use deb [http://www.micq.org/deb/](http://www.micq.org/deb/) woody main instead of
#	deb [http://www.micq.org/deb/](http://www.micq.org/deb/) sarge main # please remove that line in your sources.list if you want to have
#	micq and allready used an earlier version of this script
#	*in fixes-section: check if dma is enabled on ide CD/DVD if not /etc/hdparm.conf will be edited
**v0.5.5**
# v0.5.5 2005-06-17 *new ivman-release (trival no need for update)
#	script invoked with --no-sources will not update /etc/apt/sources.list
#	*ADD function to remove dead repositories which where added with this script
#	new packages graveman (cd/dvd-burn-app)
#	now I set up an small reposiories for sim/graveman/gnomebaker/ivman
**v0.5.6**
# v0.5.6 2005-06-26 now you can add your favorite apt-get packages to ~/.ubuntu-addons-customrc
**v0.5.7**
#     v0.5.7 2005-07-01 added mplayerplug-in to my repository
**v0.5.8**
# v0.5.8 2005-07-05 added fix for mozplayerrc and backup existing files
#       in same directory with ext orig_`date +'%s'`

**v0.6.0**
# v0.6.0 2005-07-09 now with -t | --create-tarball [download]
#		or -to| --create-tarball-only [download]
#		you can create a tarball with all packages you selected + basic dependencies
#		INFO: the [download] option is meant to fetch packages/dependencies-pkg if they
#			are not allready fetched e.g.: ./ubuntu-addons.bash_v060 --create-tarball-only download
#		-eo | --extract-tarball-only    -e /path/to/tarball.tar
#		with this option you can extract a generated tarball to the places in which the
#		files needs to be

[COLOR=DarkRed]**UPDATE v0.6.4**[/COLOR]
# v0.6.1 2005-07-13 error_detection in func get_user_names/get_user_homes
# v0.6.2 2005-08-08 bugfix in function get_user_homes
# v0.6.3 2005-08-22 bugfix in fnc softlink new option add gzcat to /bin
#               fix in fnc disable_screensaver_in_movie_players vlc-setting now working hopefully
# v0.6.4 2005-08-23 small fixes


getting started:
bzcat ubuntu-addons.bash_v064.bz2 > ubuntu-addons.bash_v064
chmod +x ubuntu-addons.bash_v064
sudo ./ubuntu-addons.bash_v064 --help

or just

./ubuntu-addons.bash_v064

THIS SCRIPT IS NOT YET FULLY TESTED SO BE CAREFUL!!

For me it works fine but...
I just want to share it so if someone  find it useful.

this thread get me started to work on an own script [http://ubuntuforums.org/showthread.php?t=22646](http://ubuntuforums.org/showthread.php?t=22646)
the gui part was inspired from the haih script [http://ubuntuforums.org/showthread.php?t=22860](http://ubuntuforums.org/showthread.php?t=22860)


This are the packages provided yet -- but easily to extend

```
######## Multimedia-packages ###### ###### Description ######
*1: beep-media-player                   (winamp replace)
*2: gstreamer0.8-mad                    (mp3 plugin)
 3: xine-ui                             (xine std gui)
*4: totem-xine                          (video player)
*5: gvlc                                (video lan client player DVD)
*6: vlc-plugin-alsa                     (alsa-plugin for vlc)
*7: mplayer-386                         (must have Movieplayer)
*8: mplayer-fonts                       (fonts for mplayer)
 9: streamtuner                         (internet-radio shoutcast & co)
 10: gxine                              (GTK-GUI for xine)
*11: w32codecs                          (win32 codecs)

Please select Packages and press ENTER (CTRL+C to abort)
If you just press RETURN I select: packages with a *
If you want none of the above Packages press: n
example: 1 2 3 6

######## Misc-packages ###### ###### Description ######
*1: msttcorefonts                       (M$-Core-fonts)
*2: gnomebaker                          (burning a CD/DVD)
*3: gftp                                (GUI-ftp client)
*4: flashplayer-mozilla                 (Macromedia flashplayer)
*5: sun-j2re1.5                         (JAVA Virtualmachine)
*6: openssh-server                      (secure shell server)
*7: sim                                 (ICQ/AIM/... Messenger)
*8: micq                                (ICQ for console)
*9: mozilla-thunderbird                 (email client)
 10: mozilla-thunderbird-enigmail       (email client with encryption)
 11: mozplugger                         (plugin filehandling Mozilla/Firefox)

######## Dev-packages ###### ###### Description ######
 1: build-essential                     (Tools gcc make...)

######## localization-packages ###### ###### Description ######
*1: openoffice.org-l10n-de              (german language for openoffice)
*2: mozilla-thunderbird-locale-de       (german language for thunderbird)
*3: mozilla-firefox-locale-de-de        (german language for firefox)

######## hoary-fixes packages ###### ###### Description ######
*1: libesd-alsa0                        (NEEDED for: fix-hoary-sound)

######## Misc none-apt-packages ###### ###### Description ######
*1: miscfonts                           (M$ additionl fonts)
*2: firefox-forms                       (Firefox forms looking nicer)
*3: libdvdcss2[.deb]                    (for watching DVD's)
*4: metrix_metaldream1-bmp-skin         (nice winamp skin for bmp)
 5: mozpluggerrc                        (needed embedded movie with mozplugger)
*6: mplayerplug-in[.deb]                (embedded mplayer mozilla/firefox)
*7: ivman_automounter[.deb]             (mounts dvd/cd like gvm but systemwide)

######## fixes/enhancements ###### ###### Description ######
*1: network_(auto-up)                   (enable network autoconfiguration)
*2: fix-hoary-sound                     (fixes sound issues in hoary: alsa/esd)
 3: fix-hoary-sound2                    (generate /etc/asound.conf)
*4: bashrc_vimrc_qtrc                   (install own vimrc .bashrc qtrc (all users))
*5: disable_screensaver                 (during playing movies with mplayer/vlc (all users))
*6: bmp/xmms-config                     (generate a default config all users)
```

---

### Post by rider343 on 2005-06-20
your repos don't work :(
I received a 404 error on ivman, gnomebacker and graveman packs

---

### Post by evermind on 2005-06-20
[QUOTE=rider343]your repos don't work :(
I received a 404 error on ivman, gnomebacker and graveman packs[/QUOTE]

sorry about this
thx for reporting

I fixed the problem - so now it should work

---

### Post by sb73542 on 2005-06-28
[QUOTE=evermind]sorry about this
thx for reporting

I fixed the problem - so now it should work[/QUOTE]
 Thanks for putting this together!  Glad to see ivman too!  :-)

---

### Post by MemoryDump on 2005-06-29
GREAT script!! I just setup another ubuntu box and this saved me a whole bunch of time and potential headaches!
This post should be sticky!!
Thanks and pls keep on building upon it!

-MD :p

err.. spoke too soon I guess.. I got this error message during the install:
```
HTTP request sent, awaiting response... 200 OK
Length: 186,080 [text/plain]

100%[========================================================>] 186,080       37.53K/s    ETA 00:00

23:58:04 (37.45 KB/s) - `metrix_metaldream1.wsz' saved [186,080/186,080]


Install metrix_metaldream1-bmp-skin into: /usr/share/bmp/Skins
--23:58:04--  http://apt.cerkinfo.be/pool/main/mplayerplug-in/mplayerplug-in_2.80-0.1_i386.deb
           => `mplayerplug-in_2.80-0.1_i386.deb'
Resolving apt.cerkinfo.be... 164.15.125.10
Connecting to apt.cerkinfo.be[164.15.125.10]:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:58:05 ERROR 404: Not Found.
``` 

ideas?

---

### Post by evermind on 2005-06-30
@ MemoryDump
It looks like there is a new mplayerplug-in version released

ok I repacked the new version (to fit ubuntu dependencies)
hope mplayerplug-in  works
script updated (v0.57)
now mplayerplug-in is in category: network-packages
hf

thx

---

### Post by uberlinux on 2005-07-04
Install mozpluggerrc into: /etc/mozpluggerrc
ubuntu-addons.bash_v057_uf: line 176: [: ==: unary operator expected

++++++++++++++++++++++++++++++++++++++++++++++++++
This was the error min finally quit at...
Also, I am getting some kind of error with the Marrilat repositories...
++++++++++++++++++++++++++++++++++++++++++++++++++
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
++++++++++++++++++++++++++++++++++++++++++++++++++++
I get some kind of checksum error

---

### Post by evermind on 2005-07-05
[QUOTE=uberlinux]Install mozpluggerrc into: /etc/mozpluggerrc
ubuntu-addons.bash_v057_uf: line 176: [: ==: unary operator expected
[/QUOTE]
thx for reporting this I will look at it but /etc/mozpluggerrc should exist anyway

[B]edit
fixed in v0.5.8[/B]

> 
++++++++++++++++++++++++++++++++++++++++++++++++++
This was the error min finally quit at...
Also, I am getting some kind of error with the Marrilat repositories...
++++++++++++++++++++++++++++++++++++++++++++++++++
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages 
--cut---
I get some kind of checksum error

This script uses no marrilat reporitories, but you can post your sources.list anyway
(maybe its gone corrupt)

---

### Post by uberlinux on 2005-07-05
Wow, Thanks for the super fast response/fix!
Ill try it again, I love the style of this script by the way!
Could you maybe post your sources.list, I assume thay work great with this script!

---

### Post by hellraiser_rob on 2005-07-05
i don't need to use this script at present, but the theory of it is ace, and makes things so much easier for super noobs, much kudos to you!

---

### Post by evermind on 2005-07-05
[QUOTE=uberlinux]Wow, Thanks for the super fast response/fix!
Ill try it again, I love the style of this script by the way!
Could you maybe post your sources.list, I assume thay work great with this script![/QUOTE]

@uberlinux
here is my sources.list
@all
you normally don't need it if you have a "virgin" or less "messy" sources.list
(all sources after a line with "added with ubuntu-addons.bash_vxxx" is automatically
added with the script)

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://de.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://de.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://de.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://de.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe
 
## hoary multiverse [added with ubuntu-addons.bash_v054]
deb http://archive.ubuntu.com/ubuntu/ hoary multiverse
 
## hoary multiverse [added with ubuntu-addons.bash_v054]
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse
 
## hoary universe [added with ubuntu-addons.bash_v054]
deb http://de.archive.ubuntu.com/ubuntu hoary universe
 
## hoary universe [added with ubuntu-addons.bash_v054]
deb-src http://de.archive.ubuntu.com/ubuntu hoary universe
 
## hoary-security [added with ubuntu-addons.bash_v054]
deb http://security.ubuntu.com/ubuntu hoary-security universe
 
## hoary-security [added with ubuntu-addons.bash_v054]
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
 
## hoary-backports [added with ubuntu-addons.bash_v054]
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
 
## hoary-extras [added with ubuntu-addons.bash_v054]
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
 
## sarge main [added with ubuntu-addons.bash_v054]
deb http://www.micq.org/deb/ woody main
 
## hoary evrmd-misc-stuff [added with ubuntu-addons.bash_v055]
deb http://www2.fht-esslingen.de/~frbuit00/linux/debian-repo hoary evrmd-misc-stuff
```

thx for your feedback

---

### Post by beko on 2005-07-06
first post for me after i just started useing Ubuntu & I really want to thank you for this script because it save so long time for me to search the forums & look for these updates & patches.

keep working on that please......

Thank you so much \\:D/   \\:D/   \\:D/

---

### Post by uberlinux on 2005-07-09
THANK YOU SO MUCH, NOW I CAN PUT LINUX ON MY MOMS COMPUTER AS SHE CAN NOW PLAY JAVA GAMES!!!!

---

### Post by evermind on 2005-08-22
version 0.6.3
this is mostly a bugfix release
shortlog
# v0.6.1 2005-07-13 error_detection in func get_user_names/get_user_homes
# v0.6.2 2005-08-08 bugfix in function get_user_homes
# v0.6.3 2005-08-22 bugfix in fnc softlink new option add gzcat to /bin
#               fix in fnc disable_screensaver_in_movie_players vlc-setting now working hopefully


longlog and download
[http://www.ubuntuforums.org/showthread.php?p=187304#post187304](http://www.ubuntuforums.org/showthread.php?p=187304#post187304)

---

### Post by elkanguro on 2008-03-09
Hi, I can't download your script. Firefox, Wget and Links2 all don't save the script but only a file attachment.php. Can You help? Oh I didn't see the date of the last update:) Is this script still developing?

---

### Post by evermind on 2008-03-09
> **elkanguro said:**
> Hi, I can't download your script. Firefox, Wget and Links2 all don't save the script but only a file attachment.php. Can You help? Oh I didn't see the date of the last update:) Is this script still developing?

No this script is no longer in active development and it is mostly useless for current ubuntu versions. It was mainly meant to fix some odd behavior in these ubuntu versions around 2005. Only the package part could be a bit of interest -- so if you still like to get this script drop me a pm.

---

