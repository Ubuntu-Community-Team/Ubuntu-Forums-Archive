---
title: "Remove Unnecessary Packages and Other Random Tidbits"
date: 2008-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Sam Lars on 2008-06-06
This is a general guide to the some things that I like to remember whenever I reinstall, including a long list of packages that can be potentially removed.
This is based on Gnome, but some things should or can be common with KDE or Xubuntu.
If I have something wrong or you have any questions, feel free to let me know. I'll try to update this as much as possible.
 
 
_**Packages I install/utilize:**_
 
smartmontools

[LIST]
[*]Find power cycles (and more) of hard disk (the following command indicates if you have the [hard drive bug]("http://ubuntuforums.org/showthread.php?t=805570"), it's up to you if you think it needs fixing based on that information)
[/LIST]
```
sudo smartctl -d ata -a /dev/sda | grep Cycle
```gnomesword

[LIST]
[*]Bible software.
[/LIST]
gthumb

[LIST]
[*]Though eog is installed by default, it seems to use a lot of memory. Gthumb also provides many useful basic functions such as cropping, mass resize/convert, and color adjustment.
[/LIST]
firestarter

[LIST]
[*]A GUI to configure iptables firewall.
[/LIST]
icedtea

[LIST]
[*]Free implementation of the Java environment.
[/LIST]
audacity

[LIST]
[*]Very good audio editing program.
[/LIST]
dvdrip

[LIST]
[*]For making video files from DVDs.
[/LIST]
boinc
boinc-manager

[LIST]
[*]Client and manager program respectively for [distributed computing]("http://boinc.berkeley.edu/"). You can install just the client and manage it remotely.
[/LIST]
sensors-applet

[LIST]
[*]Monitor temperature and fan speeds on the panel through acpi, lm-sensors, hddtemp, etc. You may want to set lm-sensors up with:
[/LIST]
```
 sudo sensors-detect
```Nautilus has a few plugins available, notably:
image resize

[LIST]
[*]Provides options to rotate and resize images from the right-click menu.
[/LIST]
open terminal

[LIST]
[*]Provides on option to open a terminal from the right-click menu. Clicking on/in a directory opens a terminal starting in that directory, clicking on the desktop will open it in your home folder.
[/LIST]
gksu

[LIST]
[*]Provides an option to open a file as root. Useful to not have to use the above plugin or root user Nautilus.
[/LIST]
sound convert

[LIST]
[*]Provides options to convert audio files from the right click menu. I haven't had much luck with it, but it could be useful.
[/LIST]
emerald
emerald-theme-manager

[LIST]
[*]An alternative to Metacity that can handle transparency, very customizable, themes available [here]("http://gnome-look.org/").
[/LIST]
compizconfig-settings-manager

[LIST]
[*]Enable plugins and alter their settings for Compiz.
[/LIST]
ndiswrapper
ndisgtk

[LIST]
[*]Use Windows drivers for wireless cards. This has been my best friend through most of my time with Linux. :)
[/LIST]
conky

[LIST]
[*]Place customized information on your desktop. More info [here]("http://ubuntuforums.org/showthread.php?t=281865").
[/LIST]
five-a-day-applet

[LIST]
[*][https://wiki.ubuntu.com/5-A-Day](https://wiki.ubuntu.com/5-A-Day)
[*]This requires this repository line:
[/LIST]
```
deb http://ppa.launchpad.net/5-a-day/ubuntu hardy main
```avant-window-navigator

[LIST]
[*]This is like the Mac OS X bar. Gdesklets has an attempt at this, too, but I have been very impressed at this program. It combines launchers with a window list, and can also have applets like the Gnome panel. Between this and Conky, along with a couple of short programs I wrote, I no longer need my Gnome panel. :)
[/LIST]
balsa

[LIST]
[*]An email program. I've had problems every time I've used Evolution. Thunderbird is nice, but I've found Balsa to be very fast, and integrates well with Gnome.
[/LIST]
espeak

[LIST]
[*]This is a very simple text to speech program that is installed by default. I think with a little creativity it could be very useful. For example, I had it read a warning when my processor got too hot.
[*]You can have it read a text file via
[/LIST]
```
espeak -f /path/to/file
```
_**REMOVALS**_
 
I have spent a lot of time trying to cut down Ubuntu installs to fit on 1.5 GB hard drives and into RAM, so anything that I can remove is helpful sometimes.
These are programs and packages that I have found I don't need. You may need them. I'll try to explain (to you and myself both) what they do. Based on that, it's your decision. If in doubt, don't remove anything. Aptitude will tell you of almost anything that will totally break your system or another package, but try to remember what you have done in case something breaks.
There are many guides on the forums about how to remove unused packages, and they can make a great second step to removing things from this list, especially gtkorphan.
If a package A depends on package B, then removing package B will also remove package A, e.g. removing apturl will remove ubufox
 
ubuntu-desktop

[LIST]
[*]This is what is called a "metapackage." It doesn't actually contain anything, it just makes sure that all of the default desktop applications are installed. If you remove something it depends on, it will be removed too. That's fine. When (if) you upgrade, it may be a good idea to reinstall it.
[/LIST]
ttf

[LIST]
[*]If you search for this in Synaptic you will find that a lot of other language fonts are installed by default. If you don't plan an reading or writing with them, you can remove them.
[/LIST]
bluez-gnome
bluez-utils

[LIST]
[*]If you don't have Bluetooth capability, you can remove these packages.
[/LIST]
xscreensaver-gl
xscreensaver-data
rss-glx
screensaver-default-images

[LIST]
[*]I'm not interested in using any pretty screensavers on my laptop. I just blank the screen rather than make it heat up or waste CPU time. Leaving gnome-screensaver retains the basic ability.
[/LIST]
tomboy

[LIST]
[*]An application for note taking that I have never used.
[/LIST]
ekiga
libopal-2.2

[LIST]
[*]Something like Skype, you can talk/conference over the Internet. I've never used it.
[/LIST]
xcursor-themes

[LIST]
[*]Extra themes for your mouse cursor.
[/LIST]
language-support-writing-en
language-support-en
language-support-translations-en

[LIST]
[*]All of these are metapackages that depend on all of the writing tools, general language support, and translations for English (or whatever language you have installed, the last two letters will be different).
[/LIST]
myspell-en-za

[LIST]
[*]South African English dictionary.
[/LIST]
openoffice.org-l10n-en-gb
openoffice.org-help-en-gb

[LIST]
[*]British English translation and help for OpenOffice.
[/LIST]
openoffice.org-l10n-en-za

[LIST]
[*]South African English translation for OpenOffice.
[/LIST]
openoffice.org-thesaurus-en-au

[LIST]
[*]Australian English thesaurus for OpenOffice.
[/LIST]
yelp

[LIST]
[*]Help viewer. I choose to use the forums and the internet rather than any of the locally installed help.
[/LIST]
gimp-help-common
gimp-help-en

[LIST]
[*]Help files for the Gimp. Again, I prefer online.
[/LIST]
gnome-user-guide

[LIST]
[*]User guide for Gnome. Again, I prefer getting anything I need online.
[/LIST]
diveintopython

[LIST]
[*]Ever wanted to learn the Python programming language? This is the book for you! Check into it. Otherwise, you can remove it.
[/LIST]
ubuntu-docs

[LIST]
[*]General Ubuntu documentation. I prefer online.
[/LIST]
thunderbird-locale-en-gb

[LIST]
[*]This Great Britain locale for Thunderbird is installed though Thunderbird isn't, which is odd. One of the language support packages depends on it.
[/LIST]
linux-generic
linux-restricted-modules-generic

[LIST]
[*]These are metapackages for the kernel versions and restricted modules respectively.
[/LIST]
linux-restricted-modules-2.6.24-16-generic

[LIST]
[*]This provides madwifi (Atheros), fglrx (ATI), nvidia, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN), fcdsl, fcdslusba, fcusb, fwlanusb, fxusb (AVM ISDN x86 only). If you don't use any of these, you can remove it.
[/LIST]
nvidia-kernel-common

[LIST]
[*]For the nvidia driver.
[/LIST]
linux-headers-generic

[LIST]
[*]This is a metapackage.
[/LIST]
linux-headers-2.6.24-16
linux-headers-2.6.24-16-generic

[LIST]
[*]These are only needed if you need to recompile the kernel.
[/LIST]
ppp
pppconfig
pppoeconf
wvdial

[LIST]
[*]Used in modem and similar connections. Not needed for wireless or ethernet connections.
[/LIST]
xsane
xsane-common

[LIST]
[*]Used for scanners.
[/LIST]
tracker
tracker-search-tool
libdeskbar-tracker
libtracker-gtk0

[LIST]
[*]Desktop search tool. I don't find it useful enough to keep.
[/LIST]
zenity

[LIST]
[*]Displays dialog boxes.
[/LIST]
gnome-games
gnome-games-data
gnome-cards-data

[LIST]
[*]The default gnome games. I don't play them enough to keep them.
[/LIST]
scim
scim-bridge-agent
scim-bridge-client-gtk
scim-gtk2-immodule
scim-modules-socket
libscim8c2a
libchewing     (thank you Wim De Winter)

[LIST]
[*]A way to set up input for languages with different alphabets.
[/LIST]
brltty
brltty-x11

[LIST]
[*]For Braille interfaces.
[/LIST]
gnome-app-install

[LIST]
[*]The nice Add/Remove Applications in the menu.
[/LIST]
ubufox

[LIST]
[*]This helps with the installation of flash and other plugins for Firefox.
[/LIST]
apturl

[LIST]
[*]This is a dependency of ubufox, it allows packages to be installed with the syntax "apt : package"
[/LIST]
python-pyatspi
at-spi

[LIST]
[*]Accessibility support.
[/LIST]
mousetweaks

[LIST]
[*]Mouse accessibility support.
[/LIST]
gnome-mag

[LIST]
[*]The Gnome magnifier. I'd prefer the Compiz plugin.
[/LIST]
gnome-orca

[LIST]
[*]Gnome screen reader.
[/LIST]
bogofilter
bogofilter-bdb
libgsl0ldbl

[LIST]
[*]Spam filter for use with Evolution or maybe Thunderbird.
[/LIST]
ubuntu-sounds

[LIST]
[*]Ubuntu's sounds.
[/LIST]
example-content

[LIST]
[*]Sample files to use when testing/showing off Ubuntu.
[/LIST]
evolution-exchange

[LIST]
[*]Evolution plugin for Microsoft Exchange mail.
[/LIST]
evolution-webcal

[LIST]
[*]Evolution plugin for web-based calendars.
[/LIST]
guile-1.6-libs

[LIST]
[*]A programming language.
[/LIST]
gnome-pilot
gnome-pilot-conduits

[LIST]
[*]Tools for PalmPilot devices.
[/LIST]
gnome-accessibility-themes

[LIST]
[*]A high-contrast theme.
[/LIST]
eog

[LIST]
[*]As I mentioned above, I prefer gthumb.
[/LIST]
deskbar-applet

[LIST]
[*]The Deskbar applet for the panel.
[/LIST]
contact-lookup-applet

[LIST]
[*]The contact lookup applet for the panel.
[/LIST]
fast-user-switch-applet

[LIST]
[*]The applet for switching users for the panel.
[/LIST]
jockey-common
jockey-gtk

[LIST]
[*]This program is responsible for installing restricted drivers such as nvidia or b43.
[/LIST]
splix

[LIST]
[*]This is a driver for samsung laser printers.
[/LIST]
min12xxw

[LIST]
[*]Printer driver for KonicaMinolta PagePro.
[/LIST]
xserver-xorg-video-all

[LIST]
[*]You should be able to remove this metapackage, as well as everything but v4l, vesa, vga, fbdev, dummy, and the one you are using. If you are using a proprietary driver, such as nvidia, it might be a good idea to leave the open source driver, nv, just in case.
[/LIST]
tsclient

[LIST]
[*]For connecting to other machines remotely.
[/LIST]
vino

[LIST]
[*]Server that allows others to access your desktop remotely.
[/LIST]
sound-juicer

[LIST]
[*]A CD ripper, Rhythmbox takes care of my needs.
[/LIST]
make

[LIST]
[*]For compiling packages.
[/LIST]
lftp

[LIST]
[*]For getting files via ftp using the command line.
[*]I think this is required for the Rhythmbox Cover Art and Lyrics plugins.
[/LIST]
 
_**Miscellaneous tips:**_
 
Control Processor scaling from the panel applet:
```
sudo dpkg-reconfigure gnome-applets
```"Yes" to run cpufreq as root. Possibly a security problem, but I've risked it.
 
Change percentage reserved for root on filesystem.  This is responsible for the difference between "Free" and "Available" space. (-m <percent>)
```
tune2fs -m 1 /dev/external
```Run a script at boot
```
/etc/init.d/something.sh
sudo chmod 755 something.sh
sudo update-rc.d something.sh defaults
```OR
 
Boot scripts
```
/etc/rc.d/rc2.d/SXXscript
```Shutdown scripts
```
/etc/rc.d/rc0.d/KXXscript
```Run in order of number XX.
 
_**  Great Firefox addons:**_

[Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865")

[LIST]
[*]You can subscribe to lists that will block ads and content for you.  I always add EasyElement+EasyList from [the subscription site]("http://adblockplus.org/en/subscriptions").
[*]Removes 99.99% of ads, depending on what sites you visit.
[*]You can also add wildcard filters to block items.
[/LIST]
 [Cooliris Previews]("https://addons.mozilla.org/en-US/firefox/addon/2207")

[LIST]
[*]A way to open a webpage or image without opening a whole new tab, in its own pseudo-window inside the browser.  You can also bookmark pages in a similar temporary way.
[/LIST]
[PicLens]("https://addons.mozilla.org/en-US/firefox/addon/5579")

[LIST]
[*]Windows/Mac only (for now, they say), but very cool way to browse pictures and movies from Google, YouTube, and some other sites.
[*]Until it's supported on Linux, [searchme.com]("http://www.searchme.com/") offers a similar interface that is web-based.
[/LIST]
 
I'll end with a script to save battery power. This is placed in /etc/acpi/battery.d and /etc/acpi/ac.d, and I've named it 99-savings.sh. This causes it to run every time the system switches from AC to battery or vice versa, and the script knows which part to run based on whether it's on AC or battery. It's a combination of a script I found somewhere on the forums, the powertop suggestions. I added some processes that I don't really want running while on battery power that will be stopped but started again when back on AC.
I've tested it a bit, and I don't think that every line does exactly what it should. I think some other power management utilities write their own values in some of these places. All in all, though, I think it's worth it.
**Update August 16, 2008** - Added xbacklight commands at the end of each section.  You have to install xbacklight and tell Gnome power manager in the power settings not to manage your screen brightness for this to work.  I was thinking that it would be nice if it would remember what your brightness was before going on battery instead of setting its arbitrary value, and then I thought - hey, I think I could do that!  So with my usual odd variable and hackish methods, I think it can remember what your backlight was before you went on battery and reset it when you go back on AC.  You can change the value after *xbacklight -set* from 30 to whatever percent you wish.
For some reason, every time I run xbacklight, regardless of what I have the setting at or whether it's as me or root, it reports 42.857143 when I run it.  But the script seems to work.  Go figure.
```
#!/bin/bash
 
# Go fast.  More or less Ubuntu defaults
if on_ac_power; then
  hdparm -B 255 -S 240 -M 254 /dev/sda
  mount -o remount,commit=5 /
  mount -o remount,commit=5 /home
  echo 0 > /proc/sys/vm/laptop_mode
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  iwpriv wlan0 power_profile 1
  echo 50 > /proc/sys/vm/swappiness
  echo 3000 > /proc/sys/vm/dirty_expire_centisecs
  hal-disable-polling --device /dev/scd0 --enable-polling
  /etc/init.d/postfix start
  /etc/init.d/anacron start
  /etc/init.d/ntp start
  LINEBACKER=$(/tmp/backlightgot)
  xbacklight -set $LINEBACKER
else # Save power
  hdparm -B 1 -S 4 -M 128 /dev/sda
  mount -o remount,commit=600 /
  mount -o remount,commit=600 /home
  echo 5 > /proc/sys/vm/laptop_mode
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 30000 > /proc/sys/vm/dirty_writeback_centisecs
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  iwpriv wlan0 power_profile 5
  echo 10 > /proc/sys/vm/swappiness
  echo 0 > /proc/sys/vm/dirty_expire_centisecs
  hal-disable-polling --device /dev/scd0
  /etc/init.d/postfix stop
  /etc/init.d/anacron stop
  /etc/init.d/ntp stop
  /etc/init.d/rsync stop
  /etc/init.d/smartmontools stop
  xbacklight > /tmp/xbacklightgot
  xbacklight -set 30
fi
```

---

### Post by infinitejones on 2008-06-07
This looks really interesting, but can you repost it with the formatting/html tags fixed?

---

### Post by Sam Lars on 2008-06-07
Sure thing, it's done, with a few updates included.  Thanks for letting me know, I had some problems getting it to submit, and since it didn't directly post here, I didn't notice.

---

### Post by Vadi on 2008-06-08
Does "sudo smartctl -d ata -a /dev/sda | grep Cycle" fix the harddrive bug if you have it?

---

### Post by TheGreatGoat on 2008-06-08
No, that command will not fix it, that command will just help you figure out if you have the cycle count problem in the first place.

You might want to check [here]("http://ubuntuforums.org/showthread.php?t=772159&highlight=hard+drive+cycle+count+fix"), or [here]("http://ubuntuforums.org/showthread.php?t=591503&highlight=Load+Cycle+Count"), but be sure that you read the disclaimers and instructions VERY carefully.  And if you doubt anything, don't do it.

---

### Post by Gourgi on 2008-06-08
very good post, full of details , thanks
i removed some packages that i didn't want

:popcorn:

---

### Post by kpkeerthi on 2008-06-09
Thank You Sam Lars. I have been/was looking to remove some unneeded packages on my laptop.

---

### Post by leetrefz on 2008-06-09
Thanx, this was incredibly helpful. Down to 1.1 gig used.

---

### Post by muadnu on 2008-06-10
How do you get those plugins for Nautilus? I thought I could find them in Edit->Preferences or somewhere like that, but I haven't been able to find them. Do I have to download something?

EDIT: Just found them via Synaptic!

---

### Post by fluteflute on 2008-06-21
Another one to remove is diveintopython (a book about programming).

[https://bugs.edge.launchpad.net/ubuntu/+bug/241920](https://bugs.edge.launchpad.net/ubuntu/+bug/241920)

---

### Post by Sam Lars on 2008-06-29
Yes, I have that in there.  I did actually use it when I was writing my first basic pygtk program, but I do think it's odd that it's installed with no visible link to it anywhere...
I might try organizing this differently, right now it's loosely upon program type.

---

### Post by garethsimpsonuk on 2008-06-29
gr8 guide by the way m8. I'm sure this will be very useful for ppl who want a server gui but need to remove a lot of the fat.

it's not very clear that when it says 'this is a dependency of ubuntu-desktop' that 'ubuntu-dekstop' wont actually be removed.

well done :)

---

### Post by Sam Lars on 2008-06-29
I'm not sure where you got that specific quote, but if ubuntu-desktop depends on something, and you remove that something, ubuntu-desktop will be removed, too.  I added a comment about that before the removals section now.  Thanks for mentioning it, I'm glad you like the guide.

---

### Post by phoenix81000 on 2008-07-17
is there a way you can throw all this in an GUI, it be a great tool to install on a new system.. atm its a lot of typing and pasting. I made a small script which you can run which will remove most of the useless prgms, not the IF stuff just the plain useless junk. You can see it here [http://pastebin.org/52100](http://pastebin.org/52100)

> 
#!/bin/sh
#
# Meuk Cleaner v0.2
#
clear
echo Created by Phoenix81000
echo Props to Sam Lars 
echo [http://ubuntuforums.org/showthread.php?t=820804](http://ubuntuforums.org/showthread.php?t=820804)
sudo apt-get -q -y purge ubuntu-desktop bluez-gnome bluez-utils xscreensaver-gl xscreensaver-data rss-glx screensaver-default-images tomboy ekiga libopal-2.2 xcursor-themes language-support-writing-en language-support-en language-support-translations-en myspell-en-za openoffice.org-l10n-en-gb openoffice.org-help-en-gb openoffice.org-l10n-en-za openoffice.org-thesaurus-en-au gimp-help-common yelp gimp-help-en gnome-user-guide diveintopython ubuntu-docs thunderbird-locale-en-gb ppp pppconfig pppoeconf wvdial xsane xsane-common tracker tracker-search-tool libdeskbar-tracker libtracker-gtk0 zenity gnome-games gnome-games-data gnome-cards-data scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket libscim8c2a brltty brltty-x11 gnome-app-install python-pyatspi at-spi mousetweaks gnome-mag gnome-orca bogofilter bogofilter-bdb libgsl0ldbl ubuntu-sounds example-content evolution-exchange evolution-webcal guile-1.6-libs gnome-pilot gnome-pilot-conduits gnome-accessibility-themes eog deskbar-applet contact-lookup-applet fast-user-switch-applet splix min12xxw tsclient vino sound-juicer 
echo cleaning...
sudo apt-get -q -y autoremove
sudo apt-get -q -y clean
clear
echo xxxx Meuk Remover Routine Completed! xxxx  


My first attempt at a script anyway. Basically paste this in a new file and call it meukcleaner.sh then open a terminal and run it by sh meukcleaner.sh Saved me lots of time when i reinstall ubuntu :D



thx for the info though!

---

### Post by Wim De Winter on 2008-07-17
Very, very useful. Thanks a lot!

Found another package that I didn't need: libchewing, it's an intelligent phonetic input method library for Chinese. I don't need that!

---

### Post by Sam Lars on 2008-07-17
Wow, a GUI for this?  That would be a lot of code.  I've written a small program to have a GUI for rsync (accidentally lost it), and a smaller program to set my CPU governor (doesn't work), but nothing this big.  I might take that as a long term project... gtkorphan is similar.
That's a great little script, thanks!
Somewhere along the line I have already removed that package, but I'll add it to the list.  Thanks!

---

### Post by Sam Lars on 2008-08-16
I've added some packages to the script that phoenix81000 posted.  A few that were autoremoved after the script anyway, some extra fonts, etc.  I'll attach the modified script.
I reinstalled a couple of computers recently and it got me to thinking about writing a simple program for this.
But I'm a bit more understanding of the seemingly slow schedule that development has sometimes... I may have some time this fall to get that started.  I'm sorting through NFS and wireless issues in the meantime...

---

### Post by phoenix81000 on 2009-02-20
Well, its like a year later? idk..

Anyway did u ever end up making a gui? If not i will **** a friend of mine to do it ^^ I hope the script has been useful for others.

---

### Post by Vadi on 2009-02-20
ubuntu tweak ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)) now has this option

---

### Post by aaronhahn777 on 2009-03-26
Thanks alot...  this is great.

---

### Post by light50 on 2009-06-15
cheers

---

### Post by mechanic on 2009-11-01
Watch dependencies, zenity -> metacity (the desktop mamager), ppp -> network-manager (!) , no way I want those erased!

---

### Post by Mr.Double on 2009-11-30
I have a problem :(. I deleted  packages listed above in this thread and my CD`s/USB-devices not automounted now :(
I use synaptic package manager and check "Mark the selected package for complete removal" when delete packages. How get back auto mount devices? (Ubuntu 9.10)

---

