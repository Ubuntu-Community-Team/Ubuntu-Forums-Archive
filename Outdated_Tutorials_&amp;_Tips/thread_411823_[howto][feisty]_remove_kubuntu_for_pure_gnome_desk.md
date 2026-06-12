---
title: "[howto][feisty] remove kubuntu for pure gnome desktop"
date: 2007-04-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Baji on 2007-04-17
Hi this should show to way for people who are trying to revert back to gnome after install kubuntu.

this guide assumes you have multiverse/universe repositories enabled. 

I've tested it on most recent feisty to date

```
Linux flyingdutchman 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

```

lets remove kubuntu (ive purposely excluded Amarok and K3B )

```
sudo apt-get remove kwin kubuntu-default-settings kubuntu-artwork-usplash ksystemlog ksysguard ksplash-engine-moodin ksplash ksnapshot ksmserver kppp kpdf kopete kooka konversation konsole konq-plugins knetworkconf kmplayer-konq-plugins konq-plugins kmix kmenuedit kmailcvt klipper kio-locate kio-apt kicker khelpcenter kghostview kfind kdnssd kdeprint kdepasswd kdenetwork-kfile-plugins kdenetwork-filesharing kdemultimedia-kio-plugins kdemultimedia-kfile-plugins kdegraphics-kfile-plugins kdeadmin-kfile-plugins kde-systemsettings kde-style-polyester kde-guidance kcron kcontrol kate kamera kaffeine-xine language-selector-qt adept adept-batch adept-installer adept-manager adept-notifier adept-updater ark digikam kaddressbook kontact kde-core kde-devel kdebase kdebase-dev kubuntu-konqueror-shortcuts konqueror libkonq4-dev kdesdk libattr1-dev kdelibs4-dev kdeartwork-style kdeartwork-misc ktip libaspell-dev kspy kdesdk-kio-plugins libneon26 libaudiofile-dev libpcre3-dev kpager kapptemplate liblualib50-dev umbrello libapr1 kdeartwork-theme-icon libkexiv2-0 subversion libsasl2-dev libavahi-client-dev libogg-dev libjasper-1.701-dev libpcrecpp0 libsvn1 kdesdk-kfile-plugins liblua50-dev lua50 libavahi-qt3-dev libacl1-dev kdeartwork-emoticons hspell kdewallpapers libxslt1-dev kbugbuster kcachegrind libxml2-dev libtiff4-dev libart-2.0-dev libesd0-dev libasound2-dev libtiffxx0c2 kpersonalizer poxml libmeanwhile1 kdelibs kunittest kappfinder libartsc0-dev libopenexr-dev kdesdk-misc libavahi-common-dev kdesdk-scripts libaprutil1 libvorbis-dev gettext-kde kuiviewer libidn11-dev libbz2-dev libarts1-dev kmtrace kbabel akregator arts bogofilter bogofilter-bdb bogofilter-common debtags enscript gwenview hwdb-client-kde karm katapult kbstate kde-icons-mono knetworkmanager kregexpeditor knode libnl1-pre6 ncompress network-manager libnm-util0 dhcdbd ocrad networkstatus zoo kitchensync imagemagick p7zip-full openoffice.org-kde openoffice.org-style-crystal kubuntu-desktop

```

now lets make sure we haven't lost anything essential

```
 sudo apt-get install ubuntu-desktop ubuntu-minimal ubuntu-standard
```

that should do the trick

ps. This list is by no means complete feel free to add more and I will update it

---

### Post by bruenig on 2007-04-17
I wrote a little script that allows you to determine the difference between the meta packages. It will find the dependencies of the first meta package, and then subtract the dependencies of the second meta package to tell you what is unique about the first package and therefore allow you to know what you need to remove if for instance you were trying to get rid of everything in kubuntu-desktop and keep ubuntu-desktop.

This solution is better than some of the other ones because it only uninstalls unique dependencies making sure you don't lose overlapping dependencies and therefore making you reinstall them like the post above which has you reinstall ubuntu-desktop, ubuntu-minimal, and ubuntu-standard.

To use the script, first
```
gedit metadiff # or use kate for kde and mousepad for xfce
```

Then copy and paste this stuff, save and then exit.
```
#!/bin/bash
#Get dependencies list
META_ONE=$(apt-cache show $1-desktop | grep ^Depends: | sed -e 's/,//g'  -e 's/Depends: //' -e 's/| //g' -e 's/ /\n/g')
META_TWO=$(apt-cache show $2-desktop | grep ^Depends: | sed -e 's/,//g'  -e 's/Depends: //' -e 's/| //g' -e 's/ /\n/g')

#Set up grep strings
GREP_STRING=$(for x in $(echo $META_TWO); do echo "$x|" ;done)
CLEAN_GREP=$(echo $GREP_STRING | sed -e 's/\ //g' -e "s/$/\'/" -e "s/^/\'|/")

#Use grep strings to determine unique packages
UNIQUE=$(echo -e "$META_ONE" | grep -Evw $CLEAN_GREP | grep -v \+)
echo $UNIQUE

#Uncomment the line below in order to enable automatic removal of the dependency list.
#sudo apt-get remove $UNIQUE
```

Make the script executable by doing
```
chmod +x metadiff
```

And then you can use this script by doing
```
./metadiff kubuntu ubuntu # you can use kubuntu xubuntu or ubuntu and in which ever order
```

This will find the dependencies of kubuntu, and then remove any dependencies from that list that are also dependencies of ubuntu and therefore leave you with a small and nondestructive list of things to remove.

So the run above would ouput this. (note this is the list on edgy, probably different on feisty, so run the script yourself to get the list for your particular machine)

[COLOR="Blue"]adept akregator amarok ark arts bogofilter cdrdao dbus digikam gdb gwenview hwdb-client-kde k3b kaddressbook kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-guidance-powermanager kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksystemlog ktorrent kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin libarts1-akode libnss-mdns pmount qca-tls speedcrunch vorbis-tools wlassistant[/COLOR]

After seeing the list, if you are content with it, you can uncomment the last line of the script (the one that says #sudo apt-get remove $UNIQUE) and then run the script again to have it automatically remove all of that. Or if for instance you want to keep something like amarok or k3b, you can type "sudo apt-get remove " and then copy and paste the list (after removing the stuff from the list that you want to keep).

Note: This script could be improved by using prompts and in some other ways, but it works as is and I am too lazy to do that.

---

### Post by rlgoddard on 2007-04-17
Hi,

After executing your script on my Feisty Beta, comparing my ubuntu and xubuntu packages, and then uncommenting the last line (re-running ./metadiff ubuntu xubuntu), it removes all packages for both ubuntu-desktop and xubuntu-desktop.  Actually, that was the intended effect for my situation because I use Enlightenment nowadays, but is that what your script was supposed to do?

Take care,
Russ

---

### Post by bruenig on 2007-04-17
When you look at the script, it should only have removed the stuff that was outputted initially

What it ouputs initially is stuff stored in $UNIQUE (hence the echo $UNIQUE). Then at the bottom there, it removes stuff stored in $UNIQUE.

Are you saying it is removing stuff that was not in the initial output?

---

### Post by rlgoddard on 2007-04-17
> **bruenig said:**
> When you look at the script, it should only have removed the stuff that was outputted initially

What it ouputs initially is stuff stored in $UNIQUE (hence the echo $UNIQUE). Then at the bottom there, it removes stuff stored in $UNIQUE.

Are you saying it is removing stuff that was not in the initial output?


Yup.  That's what I am saying.  It removed programs referenced in both xubuntu-desktop and ubuntu-desktop.  The initial output only listed the programs to be removed referenced by ubuntu-desktop.

Take care,
Russ

---

### Post by bruenig on 2007-04-17
> **rlgoddard said:**
> Yup.  That's what I am saying.  It removed programs referenced in both xubuntu-desktop and ubuntu-desktop.  The initial output only listed the programs to be removed referenced by ubuntu-desktop.

Take care,
Russ

Could you give me an example of such a program that was removed but is in both ubuntu and xubuntu.

---

### Post by rlgoddard on 2007-04-18
> **bruenig said:**
> Could you give me an example of such a program that was removed but is in both ubuntu and xubuntu.
 
I will need to re-test tonight to give you an example.  If my memory serves me right, I do not recall any shared packages between ubuntu and xubuntu that was removed.  I do recall that your script not only removed the packages of ubuntu-desktop, but also asked me (through apt-get) if I would be willing to remove packages from xubuntu-desktop as well.
 
Also, would it be possible if I could substitute aptitude for apt-get?  I'd like to use aptitude instead of apt-get.
 
Take care,
Russ

---

### Post by bruenig on 2007-04-18
Yeah, you can just replace apt-get with aptitude in that commented line.

---

### Post by rlgoddard on 2007-04-19
> **bruenig said:**
> Yeah, you can just replace apt-get with aptitude in that commented line.

This is the output I get with aptitude after "sudo aptitude install xubuntu-desktop ubuntu-desktop:

```
joey@joey:~$ ./metadiff xubuntu ubuntu
apport-gtk dbus-1-utils gqview libglib2.0-data libjpeg-progs mousepad orage python-exo thunar thunar-archive-plugin thunar-media-tags-plugin thunar-volman-plugin update-manager vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-mailwatch-plugin xfce4-mcs-plugins xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4 xfwm4 xfwm4-themes xscreensaver xubuntu-default-settings xubuntu-system-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
The following packages are BROKEN:
  update-notifier vim xscreensaver-data-extra xubuntu-desktop 
The following packages are unused and will be REMOVED:
  xfce4-mcs-manager xfce4-mixer xli 
The following packages will be REMOVED:
  apport-gtk dbus-1-utils gqview libglib2.0-data libjpeg-progs mousepad 
  orage python-exo thunar thunar-archive-plugin thunar-media-tags-plugin 
  thunar-volman-plugin update-manager vim-runtime xfce4-appfinder 
  xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin 
  xfce4-dict-plugin xfce4-fsguard-plugin xfce4-mailwatch-plugin 
  xfce4-mcs-plugins xfce4-mixer-alsa xfce4-mount-plugin 
  xfce4-netload-plugin xfce4-notes-plugin xfce4-panel 
  xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session 
  xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager 
  xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin 
  xfce4-xkb-plugin xfdesktop4 xfprint4 xfwm4 xfwm4-themes xscreensaver 
  xubuntu-default-settings 
0 packages upgraded, 0 newly installed, 47 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 96.1MB will be freed.
The following packages have unmet dependencies:
  update-notifier: Depends: dbus-1-utils (>= 0.60) but it is not installable
                   Depends: update-manager but it is not installable
  xubuntu-desktop: Depends: apport-gtk but it is not installable
                   Depends: dbus-1-utils but it is not installable
                   Depends: gqview but it is not installable
                   Depends: libglib2.0-data but it is not installable
                   Depends: libjpeg-progs but it is not installable
                   Depends: mousepad but it is not installable
                   Depends: orage but it is not installable
                   Depends: python-exo but it is not installable
                   Depends: thunar but it is not installable
                   Depends: thunar-archive-plugin but it is not installable
                   Depends: thunar-media-tags-plugin but it is not installable
                   Depends: thunar-volman-plugin but it is not installable
                   Depends: update-manager but it is not installable
                   Depends: vim-runtime but it is not installable
                   Depends: xfce4-appfinder but it is not installable
                   Depends: xfce4-battery-plugin but it is not installable
                   Depends: xfce4-clipman-plugin but it is not installable
                   Depends: xfce4-cpugraph-plugin but it is not installable
                   Depends: xfce4-dict-plugin but it is not installable
                   Depends: xfce4-fsguard-plugin but it is not installable
                   Depends: xfce4-mailwatch-plugin but it is not installable
                   Depends: xfce4-mcs-plugins but it is not installable
                   Depends: xfce4-mixer-alsa but it is not installable
                   Depends: xfce4-mount-plugin but it is not installable
                   Depends: xfce4-netload-plugin but it is not installable
                   Depends: xfce4-notes-plugin but it is not installable
                   Depends: xfce4-panel but it is not installable
                   Depends: xfce4-quicklauncher-plugin but it is not installable
                   Depends: xfce4-screenshooter-plugin but it is not installable
                   Depends: xfce4-session but it is not installable
                   Depends: xfce4-smartbookmark-plugin but it is not installable
                   Depends: xfce4-systemload-plugin but it is not installable
                   Depends: xfce4-taskmanager but it is not installable
                   Depends: xfce4-terminal but it is not installable
                   Depends: xfce4-utils but it is not installable
                   Depends: xfce4-verve-plugin but it is not installable
                   Depends: xfce4-weather-plugin but it is not installable
                   Depends: xfce4-xkb-plugin but it is not installable
                   Depends: xfdesktop4 but it is not installable
                   Depends: xfprint4 but it is not installable
                   Depends: xfwm4 but it is not installable
                   Depends: xfwm4-themes but it is not installable
                   Depends: xscreensaver but it is not installable
                   Depends: xubuntu-default-settings but it is not installable
  vim: Depends: vim-runtime (= 1:7.0-164+1ubuntu7) but it is not installable
  xscreensaver-data-extra: Depends: libjpeg-progs but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop
update-notifier
vim
xscreensaver-data-extra
xubuntu-desktop

Leave the following dependencies unresolved:
libglib2.0-0 recommends libglib2.0-data
xscreensaver-gl recommends xscreensaver
xscreensaver-gl-extra recommends xscreensaver
Score is -1945

Accept this solution? [Y/n/q/?] 
```With apt-get (after "sudo apt-get install xubuntu-desktop ubuntu-desktop):

```

joey@joey:~$ ./metadiff xubuntu ubuntu
apport-gtk dbus-1-utils gqview libglib2.0-data libjpeg-progs mousepad orage python-exo thunar thunar-archive-plugin thunar-media-tags-plugin thunar-volman-plugin update-manager vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-mailwatch-plugin xfce4-mcs-plugins xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4 xfwm4 xfwm4-themes xscreensaver xubuntu-default-settings xubuntu-system-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xubuntu-system-tools is not installed, so not removed
The following packages were automatically installed and are no longer required:
  fortunes-min fortune-mod netpbm libnetpbm10 xarchiver
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  apport-gtk dbus-1-utils gqview libglib2.0-data libjpeg-progs mousepad orage python-exo thunar thunar-archive-plugin thunar-media-tags-plugin
  thunar-volman-plugin ubuntu-desktop update-manager update-notifier vim vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-mailwatch-plugin xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin
  xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin
  xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4 xfwm4
  xfwm4-themes xscreensaver xscreensaver-data-extra xubuntu-default-settings xubuntu-desktop
0 upgraded, 0 newly installed, 50 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 104MB disk space will be freed.
Do you want to continue [Y/n]? 
```

---

### Post by bruenig on 2007-04-19
Looks like apt-get is cleaner. Aptitude is too greedy when it comes to dependencies, which could cause problems. The apt-get looks fine and should work. Are you still sure that it removed both the last time because from that last output it looks like it would only remove the xubuntu stuff.

---

### Post by crazybilly on 2007-08-18
awesome. this script is just what I was looking for (assuming it's working well)...at least it cleard out a lot of the stuff that I know was xubuntu only

Thanks.

---

