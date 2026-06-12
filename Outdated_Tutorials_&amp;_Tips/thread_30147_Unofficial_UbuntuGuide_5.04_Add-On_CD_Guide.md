---
title: "Unofficial UbuntuGuide 5.04 Add-On CD Guide"
date: 2005-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jiyuu0 on 2005-04-27
For those who:
-have no/slow internet connections
-have problems connecting to ubuntu and backports repositories
-are too lazy to do all the apt-get and commands
-are new to linux and doesn't know much about it
-just wants things to be configured right
-wants ubuntu to be multimedia and internet ready

[SIZE=4]**Unofficial Ubuntu 5.04 Add-On CD**[/SIZE]

Includes:

UbuntuGuide ([http://ubuntuguide.org](http://ubuntuguide.org))

Bootable SystemRescueCd ([http://sysresccd.org)](http://sysresccd.org))
-contain tools like Partition Manager (that can resize Windows), etc.

An install script (ug-install.sh) that will:
-custom/auto install all the Add-On Apps mentioned in UbuntuGuide (no internet connection required)
-fix the sound prob (for most computers)
-associate dvd, multimedia files to open with xine-ui and xmms rather than totem
-associate graphic files to open with gthumb
-improve fonts appearance in GNOME desktop

Linux Extras (/media/cdrom0/packages/linux/extras/):
-The Linux Documentation Project - HOWTOs

Windows Extras (/media/cdrom0/packages/windows/extras/):
-Firefox 1.06
-Thunderbird 1.06
-Gaim 1.4.0
-Gimp 2.2.8
-etc

To install/extract the Add-On CD:
**sudo sh /media/cdrom0/install.sh**
*This will only copy the packages into your hardisk. A copy of UbuntuGuide will be located on Desktop

To custom install Add-On Apps after install/extract the Add-On CD:
**sudo sh $HOME/ug-install.sh**
*This will prompt you [Y/n/q] to install all the Add-On Apps

Optional - To auto/unattended install Add-On Apps after install/extract the Add-On CD:
**sudo sh $HOME/ug-install.sh -auto**
*This will save you lots of time. It will assumed Y to install all. Apps that needs input will only appear at the end of installation

Once the script (ug-install.sh) is installed, things are in place and multimedia, internet apps are ready to go...

Download:
[ubuntu-5.04-add-on-cd-2005-08-01.tgz](http://www.frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-2005-08-01.tgz) 
-UbuntuGuide 4.17
-Applications Snapshots (2005-08-01)

Mirror (make sure the version number is the latest):
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

---

### Post by mtron on 2005-04-27
very nice idea! 
Thanks! 

How much user interaction will it nead? and: are you using the java deb or install bin from sun?

---

### Post by Sionide on 2005-04-27
Great idea, can't wait to get my hands on this! I have (some) troubles downloading stuff from the Internet due to dodgy network proxies and firewalls. So this will be an ideal friend for my Ubuntu install...

Need any help putting it all together? I'll do what I can.

---

### Post by mrbass on 2005-04-27
I was actually trying to do this.  I'm not on my computer with the bookmark but making a debian cd was way over my head to get apt-cdrom add to recognize it.  So instead I just made a script with the .deb files and used dpkg -i...arggh.  Anyway it works well if anyone wants to try it I'll put it here...I think it's around 85MB.  I'll start another thread so .zip file doesn't get confused with the cd.

Yeah I could host it jiyuu0...currently have 4.5TB/month bandwidth on my site.

edit: ok now at computer How to make a custom debian cd is way over my head
[http://wiki.debian.net/?DebianCustomCD](http://wiki.debian.net/?DebianCustomCD)
not sure if one can do it with jidgo or not.
[http://www.debian.org/CD/jigdo-cd/](http://www.debian.org/CD/jigdo-cd/)

---

### Post by Sionide on 2005-04-27
When it's finished - why not go the full hogg and get the ubuntu developers to put the official stamp on it?? The Ubuntu Guide itself is absolutely amazing. I don't see why they'd object...

---

### Post by jiyuu0 on 2005-04-27
[QUOTE=mrbass]I was actually trying to do this.  I'm not on my computer with the bookmark but making a debian cd was way over my head to get apt-cdrom add to recognize it.  So instead I just made a script with the .deb files and used dpkg -i...arggh.  Anyway it works well if anyone wants to try it I'll put it here...I think it's around 85MB.  I'll start another thread so .zip file doesn't get confused with the cd.

Yeah I could host it jiyuu0...currently have 4.5TB/month bandwidth on my site.

edit: ok now at computer How to make a custom debian cd is way over my head
[http://wiki.debian.net/?DebianCustomCD](http://wiki.debian.net/?DebianCustomCD)
not sure if one can do it with jidgo or not.
[http://www.debian.org/CD/jigdo-cd/](http://www.debian.org/CD/jigdo-cd/)[/QUOTE]

it would be great if you host it... :)

btw, if you have noticed, in the guide all the wget is pointing to this server [http://www.myosc.org/ubuntuguide](http://www.myosc.org/ubuntuguide) 
and i think the bandwidth there is also going to burst...
can i put all the files at your server? can i have a ssh login to the folder so that i can easily update it if there's a new version

now... what the CD would do is

1) it will contain the cache folder of my hard disk (all apps from ubuntuguide)
2) the configure script will then
    cp -fr /media/cdrom/packages/etc /
    cp -fr /media/cdrom/packages/var /
    *only the apt from etc and var
3) then there will be a modified version on ubuntuguide on desktop, where the instructions are the same... only no apt-get update and wget

by doing this, users should have no prob with broken dependencies as long they read it properly and don't apt-get update

---

### Post by jiyuu0 on 2005-04-27
before i finalized this... this is the script install.sh in the cd

```

#!/bin/bash

CD_PATH=`dirname "$0"`

clear
echo "Unofficial Ubuntu 5.04 Add-On CD"
echo "Applications Snapshots: 28th April 2005"
echo "URL: http://www.ubuntuguide.org"
echo "Author: Chua Wen Kiat (Kuala Lumpur, Malaysia)"
echo ""
echo "License GNU General Public License (http://www.gnu.org/licenses/gpl.html)"
echo ""
echo "General Notes:"
echo "-Script is tested on a fresh installation of the Ubuntu 5.04 x86 Install CD"
echo "-Script will only copy all applications into local hard disk"
echo "-To install, Read Unofficial Ubuntu 5.04 Add-On CD Guide located on Desktop"
echo ""
echo "Warnings:"
echo "-Do not 'sudo apt-get update'"
echo "-Doing this might disable offline installation"
echo "-Only do this if you want to install online/updated applications"
echo ""
echo "Install Unofficial Ubuntu 5.04 Add-On CD? [y/n]"
read YN
if [ "$YN" == "y" -o "$YN" == "Y" ]; then
  if [ `uname -m` != "i686" ]; then
    echo ""
    echo "Error! Execute this script on Ubuntu 5.04 x86!"
    echo ""
    echo "Installation aborted!"
    exit 1
  fi
  if [ `whoami` = "root" ]; then
    echo ""
    echo "Installing Unofficial Ubuntu 5.04 Add-On CD..."
    cp -fr "$CD_PATH/packages/etc/" /
    cp -fr "$CD_PATH/packages/var/" /

    chmod 600 /etc/apt/secring.gpg /etc/apt/trustdb.gpg
    chmod 644 /etc/apt/sources.list /etc/apt/trusted.gpg
    chmod 755 /etc/apt/apt.conf.d/
    chmod 644 /etc/apt/apt.conf.d/*

    chmod 644 /var/cache/apt/*.bin
    chmod 755 /var/cache/apt/archives/
    chmod 444 /var/cache/apt/archives/*.deb
    chmod 640 /var/cache/apt/archives/lock
    chmod 755 /var/cache/apt/archives/partial/

    chmod 644 /var/lib/apt/cdroms.list
    chmod 755 /var/lib/apt/lists/ /var/lib/apt/periodic/
    chmod 644 /var/lib/apt/periodic/*
    chmod 644 /var/lib/apt/lists/*
    chmod 640 /var/lib/apt/lists/lock
    chmod 755 /var/lib/apt/lists/partial/

    mkdir $HOME/Downloads/ 2>/dev/null
    cp -fr "$CD_PATH/packages/downloads/"*.* $HOME/Downloads/
    chown -R $SUDO_UID:$SUDO_GID $HOME/Downloads/

    mkdir $HOME/Desktop/Unofficial\ Ubuntu\ 5.04\ Add-On\ CD\ Guide/ 2>/dev/null
    tar zxf "$CD_PATH/"ubuntuguide.tgz -C $HOME/Desktop/Unofficial\ Ubuntu\ 5.04\ Add-On\ CD\ Guide/ 2>/dev/null
    chown -R $SUDO_UID:$SUDO_GID $HOME/Desktop/Unofficial\ Ubuntu\ 5.04\ Add-On\ CD\ Guide/
    /usr/bin/firefox $HOME/Desktop/Unofficial\ Ubuntu\ 5.04\ Add-On\ CD\ Guide/index.html 2>/dev/null &

    echo ""
    echo "Installation completed!"
  else
    echo ""
    echo "Error! Execute this script with root permission!"
    echo "Usage: sudo sh $0"
    echo ""
    echo "Installation aborted!"
  fi
else
  echo ""
  echo "Installation aborted!"
fi

```

---

### Post by jiyuu0 on 2005-04-28
finished... 325.0MB

going for 1 more round of testing and i'll try upload

hope my broadband is steady....

---

### Post by jiyuu0 on 2005-04-28
Unofficial Ubuntu 5.04 Add-On CD Guide
This version of guide is now temporary here:
[http://ubuntuguide.org/temp/](http://ubuntuguide.org/temp/)

This will be in the CD

---

### Post by jiyuu0 on 2005-04-28
the CD (332.1MB) is completed... if you can host it PM me

thanks :)

---

### Post by kahping on 2005-04-28
really cool idea! 

this would safe users a lot of time when performing initial system setup. also, those who format their PCs often (for various reasons) won't have to re-download everything everytime they re-install Ubuntu.

kahping

---

### Post by mrbass on 2005-04-28
Was anyone able to get a copy of this?  If so pm me so  I could host it too.

---

### Post by jiyuu0 on 2005-04-28
attached to the first post of this thread is the torrent file...
could someone test it... cause not played with torrent much

---

### Post by mrbass on 2005-04-28
I was able to download 256KB once the torrent was open...using Azureus on windows. After that it it's just, well, hmm..just stopped.  There has to be a serving seeding it I believe.

---

### Post by jiyuu0 on 2005-04-30
Announcing the availability of:
Unofficial Ubuntu 5.04 Add-On CD

[http://ubuntuguide.org/add-on-cd](http://ubuntuguide.org/add-on-cd)

If you have bandwidth to mirror this, do let me know the URL

---

### Post by mrbass on 2005-04-30
here's a mirror
[http://mrbass.org/linux/ubuntu/](http://mrbass.org/linux/ubuntu/)

---

### Post by jiyuu0 on 2005-05-02
next release of the cd... (in a few more days)

-some minor updates on the apps (jre-1_5_0_03, menu editor, xmms-wma)

-updated version of ubuntuguide

-custom-install script to install all the Add-On Applications section
just press y/n/q or enter all the way :)
save lot's of time

life is gettin easier these days  \\:D/

---

### Post by jiyuu0 on 2005-05-03
yes... the new version is out
[http://ubuntuguide.org/add-on-cd](http://ubuntuguide.org/add-on-cd)

once you installed a fresh ubuntu

insert the add-on cd then:
sudo sh /media/cdrom0/install.sh

to run auto-install script:
sudo sh $HOME/Downloads/ug-install.sh

this script will install all Add-On Applications into your Ubuntu, promted by [y/n/q]
it's best that you only run this script on a fresh installed ubuntu

---

### Post by mrbass on 2005-05-03
SWEEEEEEEEEEEEEEEEEEEEEET....nice work jiyuuo.  I didn't try the previous one because it didn't have the selection to install each app via a script.  This one DOES!!!.  This is the real deal.  It's awesome as it will be not super hard to maintain...mine was/is a copy and paste nightmare using dpkg -i.

Ok here's some constructive criticism and many suggestions....having said this I can't praise this enough.

a)Unofficial Ubuntu 5.04 Add-On CD - Auto Install? [y/n]
explain just a little more what Auto Install means.  I thought perhaps it meant to install all apps in one swoop which I didn't want to do.  Something like "Choose each application to install?"

b) [y/n/q] change to [Y/n/q]
this is consistent and indicates the default is Yes and just pressing ENTER makes it is the same as press y/Y which it does.

c) echo "Install Multimedia Player (RealPlayer)? [y/n/q]"
change to
echo "RealPlayer 10 installation path type /opt/RealPlayer"
echo "For everything else just press ENTER"
echo "Install Multimedia Player (RealPlayer)? [y/n/q]"

I realize this clears away and soon as they press enter but reminds them to type /opt/RealPlayer without having to resort to the guide.

d)apt-get -y --allow-unauthenticated install xfonts-intl-arabic xfonts-intl-asian xfonts-intl-chinese xfonts-intl-chinese-big xfonts-intl-european xfonts-intl-japanese xfonts-intl-japanese-big xfonts-intl-phonetic gsfonts-x11
      tar xvf msttcorefonts.tar -C /usr/share/fonts/truetype/
      fc-cache -f -v

heheh msttcorefonts...that's my method too...I couldn't figure out the other way either.  Could you split xfonts-intl fonts and msttcorefonts?  If not no biggie but I don't believe xfonts-intl are useful anymore with utf-8.  I believe it was required for kterm for example but kterm isn't required anymore and most apps now are qt or gtk.

e) apt-get -y --allow-unauthenticated install scim scim-chinese scim-config-socket scim-gtk2-immodule scim-tables-zh
Now to add Japanese and Korean would be awesome.  When using your cd it suggested scim-hangul so I guess that may be in the repositories now which means we can now input Korean.  I'll get back to you about this after I test it out.  Also I previously thought uim was not necessary but it is if you use KDE (kubuntu-desktop) so it's good to install it.
#sudo apt-get install anthy scim-gtk2-immodule  scim-chinese
apt-get -y --allow-unauthenticated install scim scim-chinese **scim-hangul anthy uim scim-uim**  scim-gtk2-immodule scim-tables-zh **scim-tables-ja scim-tables-ko**

also I'm almost 99% sure that scim-config-socket is a dependent of scim so it's not necessary to specify it.  anthy provides Japanese input....scim-hangul provides Korean input (gotta test this).

f) also could you add this to the end of the Chinese input script.
sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup

I explain it in more detail in my Japanese/Chinese SCIM input guide
[http://mrbass.org/linux/ubuntu/scim/](http://mrbass.org/linux/ubuntu/scim/)

f) A few things my ubuntu add-on zip has which this one doesn't is:
XFCE 4.2.1
sudo apt-get install xfce4 xfmedia xterminal xfce4-theme-brushedchrome
nvidia (auto install)
```

sudo dpkg -i /var/cache/apt/archives/nvidia-glx_1.0.7174-0ubuntu1_i386.deb nvidia-settings_1.0-3ubuntu2_i386.deb
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
sudo nvidia-glx-config enable
```

GNOME sound fix
DMA for cd-rom/dvd-rom...gotta test if it retains it after reboot
numlockx
ssh server
samba server

g) that build-essential ....how big is that 180MB???  I wonder how many would need this or install this (compile kernels and source, etc.).  I mean wouldn't this substantially reduce the cd size?

h) echo "Update Ubuntu (snapshots)? [y/n/q]"
I wasn't sure what this mean so perhaps clarify it more...
basically it upgrades the following to the lastest packages
firefox, openoffice, gimp

btw in case you just want to view my script without downloading 114MB just
wget iso.mrbass.org/ubuntu/ubuntuaddon.sh

---

### Post by mrbass on 2005-05-03
ok the Korean input does work...sweet.
[http://www.ubuntuforums.org/showthread.php?p=157209](http://www.ubuntuforums.org/showthread.php?p=157209)

---

### Post by Ride Jib on 2005-05-03
Just wanted to say thanks to jiyuu0. Your guide has helped me greatly get my computer to where I wanted it. Big thumbs up!

---

### Post by jiyuu0 on 2005-05-03
mrbass, thanks for the inputs... will look into it :)

---

### Post by mtron on 2005-05-04
shouldn't you also post the torrent link on the Addon CD Guide? will save loads of brandwidth.

---

### Post by jiyuu0 on 2005-05-04
i don't know how to make a torrent yet...
haven't got time to look into it... if you know direct step... do let me know :)

now updating the guide...

---

### Post by mandy2tom on 2005-05-04
[QUOTE=jiyuu0]Unofficial Ubuntu 5.04 Add-On CD Guide
This version of guide is now temporary here:
[http://ubuntuguide.org/temp/](http://ubuntuguide.org/temp/)

This will be in the CD[/QUOTE]
 Nice job!
Thanks
I was doing this on my pen drive for quick live cd installs.

torrent is the solution

I have been trying to find a tracker
I think most of us would be glad to leave a torrent running
I try to share someone's torrent every night, unused bandwidth

why not see if you can post it here
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

google search inurl:"6969" upload

any way good work thanks alot
I think the bigest issue for most people is embedded media in firefox i would like to see totem play all
mplayer bad

i would love to host it for you but I olny have 8 gigs a month on my site

here someone try this   

[ubuntu-5.04-add-on-cd-2005-05-02.iso.torrent](http://linuxtracker.org/download.php?id=211&name=ubuntu-5.04-add-on-cd-2005-05-02.iso.torrent) 

[email]mandy2tom@gmail.com[/email]

---

### Post by mrbass on 2005-05-05
I was watching attack of the show (formerly the screensavers) on g4tv and kevin rose showed how easy it's to create a decentralized torrent with azureus 2.3.0.  However, it'll only work for those who have that version.  But basically if the original seeded disappears it'll still work.  Plus it's anonymous not that it matters for linux .iso images and such.

---

### Post by secristrc on 2005-05-05
The CD sounds excellent, but why is i686 required ?

[COLOR=Blue]rcs@eagle:~$ sudo sh /media/cdrom0/install.sh
Password: xxxxxxxxxx
...
Install Unofficial Ubuntu 5.04 Add-On CD? [y/n]
y

Error! Execute this script on Ubuntu 5.04 x86!

Installation aborted!
rcs@eagle:~$ uname -a
Linux eagle 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005** i586 **GNU/Linux
rcs@eagle:~$[/COLOR]

_install.sh:_
[COLOR=Red]  if [ `uname -m` != "i686" ]; then
    echo ""
    echo "Error! Execute this script on Ubuntu 5.04 x86!"[/COLOR]

Does it really have to be i686 ?!

---

### Post by jiyuu0 on 2005-05-05
nope... i thought all x86 is i686

so there 
i686
i586

is there i486 and i386? the cd will work only for x86

will correct on next release

---

### Post by jiyuu0 on 2005-05-09
uploading new version... should be ready tomorrow (if my internet don't disconnect)

snapshots: 2005-05-08
contains all the offline cache used by ubuntuguide v 1.63

yes... 1 month from the day ubuntu 5.04 released :)

i'll try to make updates once a month on the 8th.

---

### Post by mrshark on 2005-05-09
first of all, thanks for your guide. Now some (constructive, i think) hints to improve it:

transcode and gstreamer0.8-lame are not in your add-on cd, so using them will fail installation of dvd::rip and goobox, respectively

even if w32codecs are installed, only xine works in playing divx and xvid movies (tried realplayer, mplayer and totem with no success...)

if you do not apply the trick in your guide for "How to configure sound to work properly in GNOME", after installing realplayer its window does not appear, till you kill esd...

audacity, with or without the previous trick, complains about not be able to play sounds: infact in: file, preferences, the reproduction and registration device selection boxes are emtpy (gnome sounds instead are working...)

ubm_1.2.5-0ubuntu1_all.deb is missing in the cd

please add if you can a program to watch tv via bttv (xawtv or other more "beautiful")

please add some links in every section about a firefox plugin, to test them (flash, java, pdf, etc)

---

### Post by jiyuu0 on 2005-05-09
i think you are refering to the older version...

2005-05-08 is still uploading at 8k/s :(
it contains all the transcode, dvdrip, goobox, ubm... etc

i'm not sure whether everyone needs to killall esd or apply "How to configure sound to work properly in GNOME"... that's why i put it in troubleshooting section rather than in the script to force apply

---

### Post by Alexander Kirillov on 2005-05-09
Thanks for the great tool!


Some comments:
 - would be great if you could include gstreamer-lame and ati drivers in the next version

 - it enables "testing" and "unstable" repositories on marillat. I think it is too risky for most: these repositories may have dependencies which are impossible to satisfy without updating, say, your glibc. I think that reasonabel default would be to enable "stable" and live "unstable" and "testing" commented out. Those who want them can enale them manually. 

 - as mentioned in another post, message "start automatic installation" is confisuing. Better: "start assisted installation" or somethign along these lines.

 - at the end of auto install script, it would be good to inform users that there are some apps that were copied to the hard drive cache but not installed (emacs, NVIDIA drivers,...) and tell that they can be installed using apt-get or synaptic.

---

### Post by jiyuu0 on 2005-05-09
[QUOTE=Alexander Kirillov]Thanks for the great tool!


Some comments:
 - would be great if you could include gstreamer-lame and ati drivers in the next version

 - it enables "testing" and "unstable" repositories on marillat. I think it is too risky for most: these repositories may have dependencies which are impossible to satisfy without updating, say, your glibc. I think that reasonabel default would be to enable "stable" and live "unstable" and "testing" commented out. Those who want them can enale them manually. 

 - as mentioned in another post, message "start automatic installation" is confisuing. Better: "start assisted installation" or somethign along these lines.

 - at the end of auto install script, it would be good to inform users that there are some apps that were copied to the hard drive cache but not installed (emacs, NVIDIA drivers,...) and tell that they can be installed using apt-get or synaptic.[/QUOTE]

now 86% uploaded... 

i tried the ati previously... never got it to work... seems like not compatible with my ati card... will try again next time

is gstreamer-lame = gstreamer0.8-lame_0.8.8-0.1_i386.deb?

"start automatic installation"
have changed to "start custom installation"

message to inform users that there are still cached apps... on next release (too late to cancel now)

reason i enable all the marillat is because some apps are there (e.g. acroread 7, transcode is in the testing)

---

### Post by jiyuu0 on 2005-05-09
suddenly thought of this...

ubuntu cd (install / live) doesn't have parted tool by default...

i'm wondering... maybe i should combine the
[http://www.sysresccd.org](http://www.sysresccd.org)

with 

[http://www.ubuntuguide.org/add-on-cd](http://www.ubuntuguide.org/add-on-cd)

downside... 110MB extra from sysresccd

---

### Post by mrbass on 2005-05-09
NO please don't.  Let's keep size to minimum.  I plan on only having a small zip addon that only has things ubuntu add-on cd doesn't.  In other words, stripping my current one down.  However, if it shoots too 600MB then some may not want to dl it just to automatically install some of the popular addons. Ultimate Boot CD Full Edition has Insert Linux on it and has QTParted. It's a 154MB download zipped .iso image.

---

### Post by jiyuu0 on 2005-05-09
it's out... :)

Download the latest image at:
[http://ubuntuguide.org/add-on-cd](http://ubuntuguide.org/add-on-cd)

Applications Snapshots: 8th May 2005
ubuntu-5.04-add-on-2005-05-08.iso

---

### Post by jiyuu0 on 2005-05-09
ok... i've finished compiling the add-on enchanced version CD

the normal version will only have the add-on content (337MB)

the enchanced version will have the add-on content and sysresccd.org (446 MB)
-partition resizer
-image tools
-etc

going through one more round of testing... and will start upload

reason of making this enchanced CD:
currently, in order to resize windows before installing linux... one have to use some tools like Partition Magic (Floopy) or Mepis... 

now this Add-On-E will do the trick :)

---

### Post by jodef on 2005-05-09
[QUOTE=jiyuu0]ok... i've finished compiling the add-on enchanced version CD

the normal version will only have the add-on content (337MB)

the enchanced version will have the add-on content and sysresccd.org (446 MB)
-partition resizer
-image tools
-etc

going through one more round of testing... and will start upload

reason of making this enchanced CD:
currently, in order to resize windows before installing linux... one have to use some tools like Partition Magic (Floopy) or Mepis... 

now this Add-On-E will do the trick :)[/QUOTE]Sounds great!! Thanks for all the hard work.

---

### Post by jiyuu0 on 2005-05-09
seems working fine... uploading :)

---

### Post by mrbass on 2005-05-09
ok my mirror is up

---

### Post by jiyuu0 on 2005-05-10
yub... it's up... 

Unofficial Ubuntu Add-On CD Enhanced (Standard + SystemRescueCd):
ubuntu-5.04-add-on-cd-e-2005-05-08.tgz (446.7 MB)

Contains:
-Snapshots of all the applications mentioned in the UbuntuGuide (8th May 2005)
-Bootable CD (SystemRescueCd) - Partition Magic clone, Ghost/Drive-image clone, etc

[http://ubuntuguide.org/add-on-cd](http://ubuntuguide.org/add-on-cd)

---

### Post by mandy2tom on 2005-05-11
both torrents are up at [http://www.linuxtracker.org/](http://www.linuxtracker.org/)

search for ubuntu

---

### Post by jiyuu0 on 2005-05-23
started compiling a newer version

Unofficial Ubuntu 5.04 Add-On CD Guide
Revision: 2.05 (Last updated on 24th May 2005)
Applications Snapshots: 23rd May 2005

---

### Post by jiyuu0 on 2005-05-24
new version of the add-on-cd is out

[b]Applications Snapshots: 23rd May 2005
UbuntuGuide - Revision: 2.05 (Last updated on 24th May 2005)[/b]

packages list
[http://ubuntuguide.org/add-on-cd/add-on-cd-2005-05-23](http://ubuntuguide.org/add-on-cd/add-on-cd-2005-05-23)

download
[http://www.frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-05-23.tgz](http://www.frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-05-23.tgz)

---

### Post by maspro on 2005-05-24
Could it be possible to add support for ATI cards, including 3d acceleration? If it's possible this would be really cool! 

 :smile:

---

### Post by jiyuu0 on 2005-05-28
updated version coming up...
snapshot (2005-05-27)

packages list:
[http://ubuntuguide.org/add-on-cd/add-on-cd-2005-05-27](http://ubuntuguide.org/add-on-cd/add-on-cd-2005-05-27)

major change in the sources.list (added backports packages...)
Ubuntu and Backports has higher priority than Marillat.

additional prog:
VNC Viewer for Windows
The Linux Documentation Project (HOWTOs - 20050528)

will finished upload in 1 or 2 days time (if my broadband don't die)

---

### Post by jiyuu0 on 2005-05-29
New version is out...

**Applications Snapshots: 27th May 2005**
UbuntuGuide - Revision: 3.00 (Last updated on 29th May 2005)
[http://ubuntuguide.org/add-on-cd](http://ubuntuguide.org/add-on-cd)

Changes:
-New version of UbuntuGuide (3.00)
-New sources.list (Marillat is configured to be lower priority)
-apt-get will install/update from Ubuntu and Backports repositories
-Marillat will only be used to install Acroread and Transcode
-Extra: The Linux Documentation Project - HOWTOs (20050528)
-Extra: VNC Free Edition Viewer (Windows) 4.1.1

Snapshot diff between - 2005-05-23 and 2005-05-27

```

2d1
< amule_1.2.6+rc7-2_i386.deb
10c9,10
< Azureus_2.3.0.0_linux.GTK.tar.bz2
---
> azureus_2.3.0.0-3~5.04ubp1_all.deb
> binutils_2.15-5ubuntu2.2_i386.deb
11a12
> bum_1.2.7_all.deb
15,17c16,18
< clamav_0.83-2ubuntu1_i386.deb
< clamav-base_0.83-2ubuntu1_all.deb
< clamav-freshclam_0.83-2ubuntu1_i386.deb
---
> clamav_0.85.1-2~5.04ubp1_i386.deb
> clamav-base_0.85.1-2~5.04ubp1_all.deb
> clamav-freshclam_0.85.1-2~5.04ubp1_i386.deb
25c26
< dvdrip_1%3a0.52.5-0.0_i386.deb
---
> dvdrip_1%3a0.52.2-0.0_i386.deb
29d29
< firestarter_1.0.1-1ubuntu2_i386.deb
31c31
< flashplayer-mozilla_7.0.25-woody0.0_i386.deb
---
> flashplayer-mozilla_7.0.25-0.0_i386.deb
36d35
< gaim_1%3a1.1.4-1ubuntu4.1_i386.deb
38d36
< gaim-data_1%3a1.1.4-1ubuntu4.1_all.deb
42a41
> gdb_6.3-5ubuntu1.1_i386.deb
52a52
> gnome-btdownload_0.0.20-1~5.04ubp1_all.deb
54c54
< gnome-menus_2.10.1-0ubuntu1+cvs20050425_i386.deb
---
> gnump3d_2.8-5_all.deb
64c64
< gstreamer0.8-lame_0.8.8-0.1_i386.deb
---
> gstreamer0.8-lame_0.8.8-0.2~5.04ubp1_i386.deb
73d72
< imagemagick_6%3a6.0.6.2-2.1ubuntu1_i386.deb
76d74
< jre-1_5_0_03-linux-i586.bin
78c76
< liba52-0.7.4_0.7.4-woody1_i386.deb
---
> liba52-0.7.4_0.7.4-1_i386.deb
82a81
> libavcodeccvs_2%3a20050427-0.0~5.04ubp1_i386.deb
85c84,85
< libclamav1_0.83-2ubuntu1_i386.deb
---
> libclamav1_0.85.1-2~5.04ubp1_i386.deb
> libcommons-cli-java_1.0-4_all.deb
91,92c91
< libdv4_0.103-woody2_i386.deb
< libdvdcss2_1.2.8-woody0.0_i386.deb
---
> libdvdcss2_1.2.8-1~5.04ubp1_i386.deb
94a94
> libfaac0_1.24-0.0_i386.deb
97d96
< libfaad2-0_2.0.0-0.5_i386.deb
99,100c98
< libfame-0.9_0.9.0-woody0.0_i386.deb
< libfribidi0_0.10.4-woody6_i386.deb
---
> libgcc1_1%3a4.0.0-7ubuntu6~5.04ubp1_i386.deb
113d110
< libgnome-menu0_2.10.1-0ubuntu1+cvs20050425_i386.deb
125a123
> liblog4j1.2-java_1.2.9-1_all.deb
143a142
> libpostproc0_2%3a20050427-0.0~5.04ubp1_i386.deb
166,169c165,166
< libswt-gtk3-java_3.0-6_all.deb
< libswt-gtk3-jni_3.0-6_i386.deb
< libtag1_1.3.1-1_i386.deb
< libtagc0_1.3.1-1_i386.deb
---
> libswt-gtk-3.1-java_3.0+3.1M4-3~5.04ubp1_all.deb
> libswt-gtk-3.1-jni_3.0+3.1M4-3~5.04ubp1_i386.deb
177a175
> Linux-html-single-HOWTOs.tar.gz
180d177
< mozilla-firefox_1.0.2-0ubuntu5.2_i386.deb
182d178
< mozilla-firefox-gnome-support_1.0.2-0ubuntu5.2_i386.deb
204c200
< nvu-1.0PR-pc-linux2.6.10-gnu.tar.bz2
---
> nvu_0.99+1.0pre-1~5.04ubp1_i386.deb
221d216
< python-xdg_0.9-1+cvs20050425_all.deb
223c218
< realplay-10.0.4.750-linux-2.2-libc6-gcc32-i586.bin
---
> realplayer_10.0.4-0.2~5.04ubp1_i386.deb
226d220
< samba_3.0.10-1ubuntu3_i386.deb
238c232
< skype_1.1.0.3-1_i386.deb
---
> skype_1.1.0.13-1_i386.deb
242d235
< smbfs_3.0.10-1ubuntu3_i386.deb
248d240
< streamtuner_0.99.99-3ubuntu0_i386.deb
250a243
> sun-j2re1.5_1.5.0+update02_i386.deb
257d249
< ubm_1.2.5-0ubuntu1_all.deb
258a251
> vnc-4_1_1-x86_win32_viewer.exe
260c253
< w32codecs_1%3a20050412-0.0_i386.deb
---
> w32codecs_1%3a20050216-0.0_i386.deb

```

---

### Post by jiyuu0 on 2005-05-29
Unfortunately Add-On-CD is discontinued...

---

### Post by mrbass on 2005-05-29
well I'll distribute it if you want.  Only thing that I possibly see is the license of mstcorefonts...need to hack it to install the .exe binaries.  If it's libdvdcss2 I'll easily distrubute that.  Also maybe that acroread is illegal to package as a deb file too but as far as I know adobe has never enforced it.  Anyway I guess my point is I'll mirror it if you want and take the risk.

---

### Post by jiyuu0 on 2005-05-29
[QUOTE=mrbass]well I'll distribute it if you want.  Only thing that I possibly see is the license of mstcorefonts...need to hack it to install the .exe binaries.  If it's libdvdcss2 I'll easily distrubute that.  Also maybe that acroread is illegal to package as a deb file too but as far as I know adobe has never enforced it.  Anyway I guess my point is I'll mirror it if you want and take the risk.[/QUOTE]

...

---

### Post by mrbass on 2005-05-29
I'll pm you instead.

---

### Post by weekend warrior on 2005-05-29
jiyuu0, why has this ended? It was really a wonderful addition, letting me recommend ubuntu to anyone without reservations. It placed ubuntu on an even playing field with other distros in terms of easy setup. Now without it, I honestly have to say I would hesitate recommending ubuntu  :(  Can you tell us the reasons for not continuing with it?

---

### Post by jiyuu0 on 2005-05-29
[QUOTE=weekend warrior]jiyuu0, why has this ended? It was really a wonderful addition, letting me recommend ubuntu to anyone without reservations. It placed ubuntu on an even playing field with other distros in terms of easy setup. Now without it, I honestly have to say I would hesitate recommending ubuntu  :(  Can you tell us the reasons for not continuing with it?[/QUOTE]

1 word...

copyrights

i just got to know it... :(

---

### Post by weekend warrior on 2005-05-29
Which bit is the most offending? Is there any chance of taking it out and continuing with the rest?

---

### Post by jiyuu0 on 2005-05-29
[QUOTE=weekend warrior]Which bit is the most offending? Is there any chance of taking it out and continuing with the rest?[/QUOTE]

that could be done... but i have to read every single package license... and that's licensing nightmare

---

### Post by weekend warrior on 2005-05-29
That's terrible  :mad:  If it comes down to that maybe the task could be divided up with the help of forum members? You could post packages you need info on and people could help look for licenses. 

BTW - Were you contacted by someone/group that asked you to stop or did you find out on your own?

---

### Post by jiyuu0 on 2005-05-29
[QUOTE=weekend warrior]That's terrible  :mad:  If it comes down to that maybe the task could be divided up with the help of forum members? You could post packages you need info on and people could help look for licenses. 

BTW - Were you contacted by someone/group that asked you to stop or did you find out on your own?[/QUOTE]

i just found out through the #ubuntu-devel chat room... got freeked out :(

---

### Post by jiyuu0 on 2005-05-29
i thought it's ok to put in CD as it's easily accessable from apt-get repositories...

could this be limited to some country?

if the CD is violating, then Backports and Marillat is too right as the packages are downloaded cache from them?

---

### Post by weekend warrior on 2005-05-29
I don't have a full understanding of the issue, but it would seem logical, as it's the same packages in question. I think the main "problem" country is the US, but could be others too....

What was said exactly that freaked you out in the chat?

---

### Post by jiyuu0 on 2005-05-29
[QUOTE=weekend warrior]I don't have a full understanding of the issue, but it would seem logical, as it's the same packages in question. I think the main "problem" country is the US, but could be others too....

What was said exactly that freaked you out in the chat?[/QUOTE]

I was told, it's like duplicating a legal CD an then distributing it...

it is possible to be sued over distribuing copyrighted packages (e.g. w32codecs, libdvdcss2, java, etc)

---

### Post by weekend warrior on 2005-05-29
Hmmm..... this a tough one  :-k  So then what **is** the difference between what you've put together and the repos? Is it because the packages on the repos are separated and on the CD are collected together as a unit? I think it's necessary to find out what the distinction is before trying to find a solution to continue this project. If there is no distinction, then according to what you were told the repos would be in violation as well.

---

### Post by mrshark on 2005-05-29
jiyuu0, in the case you do not want, even in the future, to rebuild the cd, can you please at least tell us the procedure used, so every one of us with a little time can make his own addon-cd, based on your great guide? the guide is ok, i think, because it does not contain software, it's like a big collection of small howtos. So, let us do the work, everyone for himself... PLEASEEEEE ;-)

---

### Post by maspro on 2005-05-29
It's really to bad to hear this really sad news. I was really hoping to download the latest version. :(

---

### Post by mrbass on 2005-05-29
search around and you might find it

---

### Post by maspro on 2005-05-29
[QUOTE=mrbass]search around and you might find it[/QUOTE]
 ;-)  You do not need to say more!  :grin:

---

### Post by jiyuu0 on 2005-05-31
since there are so many request (emails)...

Applications Snapshots: 29th May 2005
*last release (discontinuing this project)

Temporary Download:
[http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-05-29.tgz](http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-05-29.tgz)
*will shutdown this link on (5th June 2005)
*all packages are cache from Ubuntu, Backports and Marillat

What's new... 
-updated to UbuntuGuide 3.04
-auto/un-attended installation script for the entire Add-On-Applications section (read the index.html in the CD)

---

### Post by valnar on 2005-06-01
I cannot express to you how valuable this CD was with me choosing ubuntu as my distro of choice.  Without it, I may actually be tempted to go to Mepis or another distro that has "everything" installed.

I understand your reasons for discontinuing it, but perhaps you could rework it to a simple shell script that pulls everything down from the Internet?  Change the focus a little.  Instead of it being a time saving and bandwidth saving utility, just make it a time-saving utility instead?  I don't mind having to suck everything down from the respositories, I simply used your CD because it was scripted.

-Robert

---

### Post by jiyuu0 on 2005-06-03
[http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-06-02.tgz](http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-06-02.tgz)

*100% Marillat Free!

---

### Post by mrshark on 2005-06-04
[QUOTE=jiyuu0]*100% Marillat Free![/QUOTE]
exactly, what does this mean? That some packages have been left out? Or that they are now present in other repositories? Or what else? In particular, are decss, transcode, w32codecs gone? Thanks anyway for your great work

---

### Post by jiyuu0 on 2005-06-04
[QUOTE=mrshark]exactly, what does this mean? That some packages have been left out? Or that they are now present in other repositories? Or what else? In particular, are decss, transcode, w32codecs gone? Thanks anyway for your great work[/QUOTE]

still there... instead of using marillat, using backports

---

### Post by valnar on 2005-06-04
So does it pull everything from the Internet now instead of local?

Robert

---

### Post by mrshark on 2005-06-04
[QUOTE=jiyuu0]still there... instead of using marillat, using backports[/QUOTE]
how does this re-make your addon-cd legal? the problem was the software, not the site from where it came...

---

### Post by maspro on 2005-06-05
Is the cd going to be discontinued or not? I'm a bit puzzeld now. 

First there's this release:
[http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-05-29.tgz](http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-05-29.tgz)

and then there's this release:
[http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-06-02.tgz](http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-06-02.tgz)

 :???:

---

### Post by mrbass on 2005-06-16
new version is out 6-14 it's 558MB

---

### Post by Griffology on 2005-06-16
mrbass, thank you very much... I have found the resources your provided very useful!

---

### Post by mrbass on 2005-06-17
[[color=#CCA301]****[/color]]("member.php?u=1812")jiyuuo is da man

---

### Post by jiyuu0 on 2005-06-24
[http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-06-22.tgz](http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-06-22.tgz)

UbuntuGuide 4.06

Improved ug-install.sh script that will:
-install all the Add-On Apps
-fix the sound prob (for most cases)
-associate multimedia files to open with xine and xmms rather than totem
-"-auto" parameter for unattended installation for all the Add-On apps

Among the release of this Add-On CD, this is my favourite as once after the script is installed, things are in place and multimedia are ready to go :-)

---

### Post by valnar on 2005-06-24
Does the CD pull down any of the proprietary (DVD decryption, etc.) programs from the Internet that were banned last time?

Robert

---

### Post by jiyuu0 on 2005-06-24
[QUOTE=valnar]Does the CD pull down any of the proprietary (DVD decryption, etc.) programs from the Internet that were banned last time?

Robert[/QUOTE]

it is still the same as it is...

---

### Post by Skel on 2005-06-25
Now would i have to burn this cd to install it or is there a way to just extract it then install?

---

### Post by jiyuu0 on 2005-06-25
[QUOTE=Skel]Now would i have to burn this cd to install it or is there a way to just extract it then install?[/QUOTE]

The ISO contains the bootable SysRescCD. It has tools like Partition Manager (that can resize Windows), etc. So if, you need that tool, then you have to burn the ISO, else just extracting it will do :-)

You can use this method if u don't wish to burn it
[http://ubuntuguide.org/#mountunmountisofileswithoutburning](http://ubuntuguide.org/#mountunmountisofileswithoutburning)

To install/extract the CD
sudo sh /media/iso/install.sh
*This will only copy the packages into you hdd. A copy of UbuntuGuide will be located on Desktop.

To install applications from Ubuntu Add-on CD after copying it hd
sudo sh $HOME/Downloads/ug-install.sh

Optional - Install all applications on cd unattended
sudo sh $HOME/Downloads/ug-install.sh -auto

---

### Post by Skel on 2005-06-25
Thank You Very much

---

### Post by jiyuu0 on 2005-06-29
updated first post of this thread...

---

### Post by maspro on 2005-07-08
Why is there so much difference in size between the 2005-06-14 release and the 2005-06-22 release? It's almost a difference of about 60 MB. Are there fewer appz in the latest version of the add-on cd?

Just curious.  ;-)

---

### Post by jiyuu0 on 2005-07-08
[QUOTE=maspro]Why is there so much difference in size between the 2005-06-14 release and the 2005-06-22 release? It's almost a difference of about 60 MB. Are there fewer appz in the latest version of the add-on cd?

Just curious.  ;-)[/QUOTE]

i don't know either... din removed anything
2005-07-07 is ready, going to upload on mon (currently no broadband)

---

### Post by jiyuu0 on 2005-07-11
ubuntu-5.04-add-on-cd-e-2005-07-09

Latest Download: UbuntuGuide 4.14 Add-On-CD
[http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-07-09.tgz](http://frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-e-2005-07-09.tgz)

---

### Post by filemanager on 2005-07-12
How does this fix sound problems?

---

### Post by jiyuu0 on 2005-07-12
[QUOTE=filemanager]How does this fix sound problems?[/QUOTE]

for most of the PCs that i've tried... this solution will fix the sound
[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

the ug-install.sh script will automatically install this section if answer is "Y" to it

---

### Post by webbie180 on 2005-07-22
I downloaded the file in my friend's place and copied it to a CD.  Back home I copied the tgz file and l untar the file in my home directory.   Opened a terminal and type in 'sudo sh /media/cdrom0/install.sh' but cannot.  Wat should I be doing to do it right?  Very newbie here.  Pse help with step by step guide.

---

### Post by jiyuu0 on 2005-07-22
[QUOTE=webbie180]I downloaded the file in my friend's place and copied it to a CD.  Back home I copied the tgz file and l untar the file in my home directory.   Opened a terminal and type in 'sudo sh /media/cdrom0/install.sh' but cannot.  Wat should I be doing to do it right?  Very newbie here.  Pse help with step by step guide.[/QUOTE]

when you untar the file, there's an iso.

burn the iso into cd. (if you are in ubuntu. right click the file -> burn), 

once done burning, then issue the command

---

### Post by webbie180 on 2005-07-23
How to untar in Windows?  As I dont have a cdwriter at home.  My friend is using windows.  I need to do everything under windows first.  Thanks.

---

### Post by RadixLecti on 2005-07-23
There is a free program called zipgenius, [http://www.zipgenius.it/index2.html](http://www.zipgenius.it/index2.html) , that handles .tar. It replaced winzip on my win-comp a long time ago.

---

### Post by webbie180 on 2005-07-23
Thanks.  Will try it out.

---

### Post by webbie180 on 2005-07-23
Thanks, man.  WORKS.

---

### Post by RadixLecti on 2005-07-23
Glad to help.

---

### Post by Dural on 2005-07-26
[QUOTE=RadixLecti]Glad to help.[/QUOTE]
 I just finished installing the add-ons from the ubuntu add-on Cd. It went great, but then I restarted the computer in order to properly install everything. I got sent to the SystemRecovery CD and now I'm stuck in Gentoo Linux? How do I get out of it?

---

### Post by jiyuu0 on 2005-07-26
[QUOTE=Dural]I just finished installing the add-ons from the ubuntu add-on Cd. It went great, but then I restarted the computer in order to properly install everything. I got sent to the SystemRecovery CD and now I'm stuck in Gentoo Linux? How do I get out of it?[/QUOTE]

the add-on cd is a bootable system recovery tool too. so, just remove the cd from your cd-rom and restart again. you will be back into ubuntu :-)

---

### Post by Dural on 2005-07-26
^ Thank you. :)

---

### Post by craigevil on 2005-07-29
Great job. The add-on cd made the switch to Ubuntu easy and well worth it. Keep up the good work.

---

### Post by sb73542 on 2005-08-06
Hello, are you planning on continuing to update this CD, jiyuu0?  Will it continue to be available and usable when Breezy is released?  As someone else here said, this CD is possibly the only method that makes Ubuntu possible for me, as I have a dirt-slow dialup connection and a need for several major programs that Ubuntu leaves out.  I REALLY appreciate your hard work on this essential CD.

---

### Post by jiyuu0 on 2005-08-06
[QUOTE=sb73542]Hello, are you planning on continuing to update this CD, jiyuu0?  Will it continue to be available and usable when Breezy is released?  As someone else here said, this CD is possibly the only method that makes Ubuntu possible for me, as I have a dirt-slow dialup connection and a need for several major programs that Ubuntu leaves out.  I REALLY appreciate your hard work on this essential CD.[/QUOTE]

i'm not sure bout Breezy add-on, but a newer version of the add-on (2005-08-01) for hoary is ready. will be uploading on monday

---

### Post by zencoder on 2005-08-07
[QUOTE=jiyuu0]i'm not sure bout Breezy add-on, but a newer version of the add-on (2005-08-01) for hoary is ready. will be uploading on monday[/QUOTE]

Wow, this sounds great...I've just breezed through this thread, and it looks like a few versions of this CD have been made...is there an official site, repository, or location?  I know you were looking for hosting...I'm just saying at first glance, this is kind of confusing.  You've got a fairly active thread here, with several versions linked, some of which are dead links...you should consider getting a stable page or location (sourceforge?) to document changes and updates, and to point to the latest stable version.

Just my $0.02.  I look forward to trying out this tool!!!

---

### Post by jiyuu0 on 2005-08-07
i'm currently uploading
2005-08-01 build :-)

will let u all know when it's ready to be downloaded

---

### Post by jiyuu0 on 2005-08-07
OK. Uploaded :-)

Download:
[ubuntu-5.04-add-on-cd-2005-08-01.tgz](http://www.frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-2005-08-01.tgz) 

More Info:
[http://ubuntuforums.org/showpost.php?p=150088&postcount=1](http://ubuntuforums.org/showpost.php?p=150088&postcount=1)

Since there are still plenty of space in the CD, some extras :-)

Linux Extras (/media/cdrom0/packages/linux/extras/):
-The Linux Documentation Project - HOWTOs

Windows Extras (/media/cdrom0/packages/windows/extras/):
-Firefox 1.06
-Thunderbird 1.06
-Gaim 1.4.0
-Gimp 2.2.8
-etc

---

### Post by AndrewB on 2005-08-07
Thanks for the great guide, and cd info. I get used to Hoary, bout the time Breezy comes out! :)

---

### Post by floppy on 2005-08-07
Thank you so much. Your add-on puts the icing on the cake.

---

### Post by jerrykenny on 2005-08-18
Jiyuu0,  I'm currently downloading this to post to someone else with a 56k connection.  

I've no limit on my own uploading (albeit only 256k) . . . quite happy to upload as a bittorrent if you think thats the way to go ?

---

### Post by valnar on 2005-08-31
jiyuu0,

Will you be putting out a Breezy "edition" of this CD?

Robert

---

### Post by mailmaldi on 2005-09-06
u rock jiyuu0....

the only thing that didnt work from the add-on was the sound fixing part..(intel 915GAV motherboard... ](*,) )

the rest working smoothly and nicely...

gr8 work....


also if someun can help me out here....
i downloaded a lot of packages such as KDE,anjuta etc & all packages are in /var/cache/apt/archives.....

now i want to install the same packages on all my friends's pc's....

so how do i do it??

i vaguely remember seeing somewhere to create a backup of my apt-archives which i can restore later...can someun temme how...

i wanna be able to do apt-get install kubuntu-desktop on my friends pcs too...

---

### Post by oldlucky on 2005-09-08
What a great idea thanks to all you involved here this truly is a great distrubution.
I am almost ready to ditch windoze for good and this sort of addon makes it all the easier to do , just one question will the cd be updated again or will this be the last of the addon's for hoary (2005-08-01).

Cheers

---

### Post by jiyuu0 on 2005-09-08
[QUOTE=oldlucky]What a great idea thanks to all you involved here this truly is a great distrubution.
I am almost ready to ditch windoze for good and this sort of addon makes it all the easier to do , just one question will the cd be updated again or will this be the last of the addon's for hoary (2005-08-01).

Cheers[/QUOTE]

i think 2005-08-01 release is the last for hoary.

i can't promise breezy add-on cd yet, but if time permit it should be available 1 month after the release of breezy ;)

---

### Post by valnar on 2005-09-08
[QUOTE=jiyuu0]but if time permit it should be available 1 month after the release of breezy ;)[/QUOTE]

Then I will load Breezy one month after it comes out.   \\:D/ 

-Robert

---

### Post by Sheytan on 2005-09-21
Great job :)

I could quite to get ubuntu to work following the guide, but with the Add-on cd
everything works perfectly

---

### Post by Larry-in-Eastbay on 2005-09-21
[QUOTE=Sheytan]Great job :)

I could quite to get ubuntu to work following the guide, but with the Add-on cd
everything works perfectly[/QUOTE]
 Being another interested but not knowing type....

Why would this disc not work with the 5.10 version?

What would go wrong if I tried?

What kind of evil things will it do?

How exactly does this disc work in terms of installing the apps and is it not windows like where the app senses the version and installs accordingly?


I read this thread and though it helped make up my mind on installing ubuntu this weekend but it confusing since the 5.10 is now recommended for fixing alot of bugs but apparently this quickie easy CD will not work on that and only on the older and more  buggy 5.04.  

And then there is all the 5.04 to 5.10 updates that crash so that seems like the least attractive method.

Is there a way that the disc can be made to update or check for update all these add ons.  I have been reading these one at a time installs is a bit painful in terms of boredome/time consuming and occasional bug to fix so a one big swoop install is nice, kind of like the other one I have been looking at (SUSE with all those disks you get, for free).

I am interested in hearing from everyone.   Maybe the updating to 5.10 is not as buggy as it appears on this forum and I should install 5.04 with this add on disk then update?

TAKE CARE NOW EVERYONE!

---

### Post by chettyk on 2005-09-25
jiyuu0, you are the greatest! I practically sleep with your unofficial guide under my pillow. And this Add-On CD is just what I was looking for.

I have already used apt-get to download and install some of the stuff on the CD. Could that create a problem when I run the CD? I should think not. Anyway, I am going to give the CD a try.

---

### Post by darkjedi8359 on 2005-09-29
thank you for your great work, this saves me a lot of time :)

---

### Post by chettyk on 2005-09-29
[QUOTE=chettyk]
I have already used apt-get to download and install some of the stuff on the CD. Could that create a problem when I run the CD? I should think not. Anyway, I am going to give the CD a try.[/QUOTE]

Well, I went right ahead and ran the install script on the Add-On CD. After I installed Ubuntu 5.04, I had added the multiverse and universe repos in the sources.list, and run update and upgrade. Plus I had installed Thunderbird and stuff like Firestarter, flashplayer etc. It was only after this that I used the Add-On CD. It worked like a charm. In a matter of minutes, I installed all the additional software I required and the script also made the required configuration changes. I am delighted and thrilled. This CD is just what Ubuntu lacked all this while.

---

### Post by urbandryad on 2005-09-30
wait, the add-ons aren't already part of the Ubuntu iinstall CD already? Great, I have to find a way to burn this to disc. XD

---

### Post by linuxeiro on 2005-10-04
.

---

### Post by towsonu2003 on 2005-10-13
Hi,
Being a paranoid newbie, how do you update/upgrade these packages? I assume they won't automatically be updated by synaptic as synaptic categorizes those packages as 
Status: Installed (Local or Obsolete)
If it's local or obsolete, I wouldn't expect it to update it, right?

Also, I unchecked the repository entry {cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/} in synamptic, thinking that a cd is now useless. is this your cd, written by your script, or something else (I don't know how to read scripts...)?

---

### Post by chrisblack on 2005-10-24
Will the 2005-08-01  work on 5.10, or do we have to wait for you to release the update???

Chris

---

### Post by valnar on 2005-10-24
I think we are to assume that these are adequate replacements for Breezy.

[http://ubuntuforums.org/forumdisplay.php?f=86](http://ubuntuforums.org/forumdisplay.php?f=86)

-Robert

---

### Post by andlinux21 on 2005-10-24
So they don't have a ADD-On CD for 5.10 yet?:confused:

---

### Post by mveljko78 on 2005-11-03
i have no internet connection and i'm struggling loneger than a week to enable multimedia but in vain.
is there some package  smaller than cd so it can fit my usb 128mb?
:(

---

### Post by Georgie-o on 2005-11-03
Does this install correct the problem of a slow internet connection with the Ubuntu-installed Firefox.  I have read elsewhere that by unloading the Ubuntu-installed Friefox and reinstalling one directly from Firefox that the performance and speed will be greatly improved.  I have not done this yet because the fix seems a little out of my league...

---

### Post by onfyreforjesus on 2005-11-06
Dear Jiyuu,

when will you launch the unofficial add on cd for breezy?
will you support x86-64

dying to live in a windows free world.

Pls include ardour, rosegarden and  jamin and other stuff related to a home studio.

Pls do somethin for all musicians too.
:???: ;) 
God Bless

---

### Post by Inspector Hector on 2005-11-06
Jiyuu is taking a rest (for good reasons!) for some time, so he won't have the time for 5.10 cd.
[http://ubuntuforums.org/showthread.php?t=77704](http://ubuntuforums.org/showthread.php?t=77704)

Properly, the new maintainer(s) will start to build it.

---

### Post by tOpEzz on 2005-11-22
kool!!! look like i'm gonna learn linux from now...

---

### Post by minghai on 2006-01-09
Hi, does anyone have any leads to anybody working on a 5.10 Add-On CD?  Thanks!

Ming Hai

---

### Post by aysiu on 2006-01-09
[QUOTE=minghai]Hi, does anyone have any leads to anybody working on a 5.10 Add-On CD?  Thanks!

Ming Hai[/QUOTE] No leads. This may help, though:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by indraveni on 2006-06-07
Hi,


[QUOTE=jiyuu0]For those who:
-have no/slow internet connections
-have problems connecting to ubuntu and backports repositories
-are too lazy to do all the apt-get and commands
-are new to linux and doesn't know much about it
-just wants things to be configured right
-wants ubuntu to be multimedia and internet ready

[SIZE=4]**Unofficial Ubuntu 5.04 Add-On CD**[/SIZE]

Includes:

UbuntuGuide ([http://ubuntuguide.org](http://ubuntuguide.org))

Bootable SystemRescueCd ([http://sysresccd.org)](http://sysresccd.org))
-contain tools like Partition Manager (that can resize Windows), etc.

An install script (ug-install.sh) that will:
-custom/auto install all the Add-On Apps mentioned in UbuntuGuide (no internet connection required)
-fix the sound prob (for most computers)
-associate dvd, multimedia files to open with xine-ui and xmms rather than totem
-associate graphic files to open with gthumb
-improve fonts appearance in GNOME desktop

Linux Extras (/media/cdrom0/packages/linux/extras/):
-The Linux Documentation Project - HOWTOs

Windows Extras (/media/cdrom0/packages/windows/extras/):
-Firefox 1.06
-Thunderbird 1.06
-Gaim 1.4.0
-Gimp 2.2.8
-etc

To install/extract the Add-On CD:
**sudo sh /media/cdrom0/install.sh**
*This will only copy the packages into your hardisk. A copy of UbuntuGuide will be located on Desktop

To custom install Add-On Apps after install/extract the Add-On CD:
**sudo sh $HOME/ug-install.sh**
*This will prompt you [Y/n/q] to install all the Add-On Apps

Optional - To auto/unattended install Add-On Apps after install/extract the Add-On CD:
**sudo sh $HOME/ug-install.sh -auto**
*This will save you lots of time. It will assumed Y to install all. Apps that needs input will only appear at the end of installation

Once the script (ug-install.sh) is installed, things are in place and multimedia, internet apps are ready to go...

Download:
[ubuntu-5.04-add-on-cd-2005-08-01.tgz](http://www.frankandjacq.com/ubuntuguide/add-on-cd/ubuntu-5.04-add-on-cd-2005-08-01.tgz) 
-UbuntuGuide 4.17
-Applications Snapshots (2005-08-01)

Mirror (make sure the version number is the latest):
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)[/QUOTE]

I want to know what does the script ug-install.sh contains. 

Since I also want to create a CD which will allow user to autoinstall/ustom the Applications from CD jsut like the AddOn CD. 

So please can any one tell me what does this script ug-install.sh contcain which is responsible for the CD to run and how to create such CD.

---

