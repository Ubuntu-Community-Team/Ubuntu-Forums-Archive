---
title: "how to open .rar files in ubuntu"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by satish.veeravalli@gmail.c on 2008-05-24
hi iam satish, iam new to ubuntu os i have a .rar file on Desktop and iam unable to unrar it so please help me soonhttp://ubuntuforums.org/images/smilies/icon_sad.gif
thnk u in advance

---

### Post by lswest on 2008-05-24
just do ```
sudo apt-get install unrar rar
``` and then you should be able to create & access rar archives.  (Double-click it to open the archive manager)  and unrar comes pre-installed in Hardy (8.04), so it should work just by double-clicking it.  If you receive an error message, please post it here.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
hi thanks for ur support i have entered the command in command liner and iam getting the fallowing message:
satishv@satishv-desktop:~$ sudo apt-get install unrar rar
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
satishv@satishv-desktop:~$> 

---

### Post by Maestro23 on 2008-05-24
> **satish.veeravalli@gmail.c said:**
> hi thanks for ur support i have entered the command in command liner and iam getting the fallowing message:
satishv@satishv-desktop:~$ sudo apt-get install unrar rar
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
satishv@satishv-desktop:~$

If you have Synatpic or Add/Remove programs open, close them before you try and the run the commands given to you.

---

### Post by Nepherte on 2008-05-24
It seems that another program has a lock on the file which makes it not possible for another process to access it. You could either wait some time or just relogin.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
iam the only user and i have root in this and no other is using this and iam using LTS6.06 thank u in advance

---

### Post by lswest on 2008-05-24
Try again in a few minutes, it might be that the update-manager is checking for updates or downloading them right now, if the problem persists, log out and back in, and the lock will be gone.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
now iam getting this :
satishv@satishv-desktop:~$ sudo apt-get install unrar rar
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
satishv@satishv-desktop:~$ sudo apt-get install unrar rar
Password:
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
satishv@satishv-desktop:~$

---

### Post by lswest on 2008-05-24
okay, so the packagename is wrong, try this:
```
apt-cache search unrar
``` and then copy and paste the returned package name that refers to a .rar unarchiver and substitute "unrar" from my original command with that name instead.

Alternatively, you can download the .deb from here: [http://packages.ubuntu.com/dapper/unrar](http://packages.ubuntu.com/dapper/unrar) and when when you double-click it, it should install the other required files (if any).

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
satishv@satishv-desktop:~$ apt-cache search unrar
satishv@satishv-desktop:~$ apt-cache search unrar
satishv@satishv-desktop:~$ apt-cache search unrar
 now nothing happing with this command

---

### Post by Maestro23 on 2008-05-24
lswest, he says he's running 6.06... So make sure he has the correct repositories enabled.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
> **satish.veeravalli@gmail.c said:**
> satishv@satishv-desktop:~$ apt-cache search unrar
satishv@satishv-desktop:~$ apt-cache search unrar
satishv@satishv-desktop:~$ apt-cache search unrar
 now nothing happing with this command
Download unrar
Download for all available architectures Architecture 	Package Size 	Installed Size 	Files
amd64 	89.4 kB	224 kB 	no current information
i386 	84.6 kB	216 kB 	no current information
powerpc 	93.0 kB	228 kB 	no current information 

among this files which one i should download

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
> **satish.veeravalli@gmail.c said:**
> Download unrar
Download for all available architectures Architecture 	Package Size 	Installed Size 	Files
amd64 	89.4 kB	224 kB 	no current information
i386 	84.6 kB	216 kB 	no current information
powerpc 	93.0 kB	228 kB 	no current information 

among this files which one i should download
lswest, yes iam using  ubuntu 6.06 LTS and iam very new new to this pls help me thank u in advance

---

### Post by lswest on 2008-05-24
i assume you're running 32 bit, which would constitute to i386, but you can check by running ```
uname -a
``` in the terminal (it will return a value, and if it's anything apart from x86_64 or amd64, then i386 is your choice)

[B]About the repositories:
go to system-->administration-->software sources, and make sure on the first tab that the first 4 checkboxes are checked (the other settings are fine) then try this: ```
sudo apt-get update
sudo apt-get install unrar rar
```
[/B]
Sorry about being unclear at first, i couldn't remember what was enabled or disabled by default in dapper anymore.

Try the repositories bit first.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
satishv@satishv-desktop:~$ uname -a
Linux satishv-desktop 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686GNU/Linux
satishv@satishv-desktop:~$ sudo apt-get update
Password:
Get:1 [http://oss.oracle.com](http://oss.oracle.com) unstable Release.gpg [189B]
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper Release
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 4B in 3s (1B/s)
Reading package lists... Done
satishv@satishv-desktop:~$ sudo apt-get install unrar rar
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
satishv@satishv-desktop:~$
hi iam getting this and its saying unrar is not installed 
thanks in advance..

---

### Post by lswest on 2008-05-24
try ```
sudo apt-get install unrar-nonfree
```

and if that doesn't work, try ```
apt-cache search unrar
``` again

I'm booting into a Dapper liveCD I have, i'll post back the exact command in a minute.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
and one more thing software sources are not there i can find only software properties and 4 check boxes are  marked..

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
hi,
this what happing :(

satishv@satishv-desktop:~$ sudo apt-get install unrar-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package unrar-nonfree
satishv@satishv-desktop:~$ apt-cache search unrar
satishv@satishv-desktop:~$
satishv@satishv-desktop:~$ apt-cache search unrar
satishv@satishv-desktop:~$

---

### Post by lswest on 2008-05-24
> **satish.veeravalli@gmail.c said:**
> and one more thing software sources are not there i can find only software properties and 4 check boxes are  marked..

They must have renamed it since Dapper, I'll post back the working command in a few.

Also, you can edit your posts using the "edit" button on the bottom right of your post.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
ok i will wait for ur reply thank u for ur good response..

---

### Post by RomeReactor on 2008-05-24
Hi. Satish, please post the output of this command:
```
cat /etc/apt/sources.list
```

It seems you don't have the multiverse repository enabled, which is [where you find unrar]("http://packages.ubuntu.com/dapper/unrar").

---

### Post by lswest on 2008-05-24
Okay, i just had a look at it, and the command that works for me is ```
sudo apt-get install unrar-free
``` However, that package does not have support for rar 3.0 (the newest one), so if you can still not extract the archive after install unrar-free, follow the link i posted above and download the i386 deb package, it should work for you.

*EDIT*
i realize my mistake, if you go to system-->administration-->sources properties, and then go to "add" check the last two boxes on the window (see attached image), then do ```
sudo apt-get update
sudo apt-get install unrar rar
```

Completely forgot you have to choose to "add" the repository and not to enable it, really sorry for that.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
hi,
this is what is got in command liner
satishv@satishv-desktop:~$ cat /etc/apt/sources.list

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free
satishv@satishv-desktop:~$

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
hi did u see that

---

### Post by lswest on 2008-05-24
> **satish.veeravalli@gmail.c said:**
> hi did u see that

You mean the output of the command?  Yes, but editing that file is the same as doing the steps i posted above, which you will probably be more comfortable doing than editing lines in the file.

To explain the image i posted, after you click "add" the new window pops up (which is why i drew the arrow) and those last two boxes i circled must be checked for you to be able to install unrar.

---

### Post by RomeReactor on 2008-05-24
Sorry for the late reply. You don't have the multiverse repository enabled; just follow lswest's advice and you'll be able to install unrar and decompress the archive you want.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
yes i have done the way u said but what is happing is even if i select the check boxes and adding its adding but when i open for next time non of the boxes two boxes are marked. and i have given in command liner what u said this is happing,

satishv@satishv-desktop:~$ sudo apt-get install unrar rar
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  rar unrar
0 upgraded, 2 newly installed, 0 to remove and 196 not upgraded.
5 not fully installed or removed.
Need to get 0B/329kB of archives.
After unpacking 709kB of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 6617 package `libgimp2.0':
 `Depends' field, invalid package name `libatk1.0-0!': character `!' not allowed - only letters, digits and -+._ allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)
satishv@satishv-desktop:~$

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
yes i have done the way u said but what is happing is even if i select the check boxes and adding its adding but when i open for next time non of the boxes two boxes are marked. and i have given in command liner what u said this is happing,

satishv@satishv-desktop:~$ sudo apt-get install unrar rar
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
rar unrar
0 upgraded, 2 newly installed, 0 to remove and 196 not upgraded.
5 not fully installed or removed.
Need to get 0B/329kB of archives.
After unpacking 709kB of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 6617 package `libgimp2.0':
`Depends' field, invalid package name `libatk1.0-0!': character `!' not allowed - only letters, digits and -+._ allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)
satishv@satishv-desktop:~$

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
hi r u busy?..

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
r u there
can u hwlp me out

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
yes i have done the way u said but what is happing is even if i select the check boxes and adding its adding but when i open for next time non of the boxes two boxes are marked. and i have given in command liner what u said this is happing,

satishv@satishv-desktop:~$ sudo apt-get install unrar rar
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
rar unrar
0 upgraded, 2 newly installed, 0 to remove and 196 not upgraded.
5 not fully installed or removed.
Need to get 0B/329kB of archives.
After unpacking 709kB of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 6617 package `libgimp2.0':
`Depends' field, invalid package name `libatk1.0-0!': character `!' not allowed - only letters, digits and -+._ allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)
satishv@satishv-desktop:~$
satish.veeravalli@gmail.c is online now Report Post   	Edit/Delete Message

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
hi can any one help me please read this posts and help me out thanks in advance

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
es i have done the way u said but what is happing is even if i select the check boxes and adding its adding but when i open for next time non of the boxes two boxes are marked. and i have given in command liner what u said this is happing,

satishv@satishv-desktop:~$ sudo apt-get install unrar rar
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
rar unrar
0 upgraded, 2 newly installed, 0 to remove and 196 not upgraded.
5 not fully installed or removed.
Need to get 0B/329kB of archives.
After unpacking 709kB of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 6617 package `libgimp2.0':
`Depends' field, invalid package name `libatk1.0-0!': character `!' not allowed - only letters, digits and -+._ allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)
satishv@satishv-desktop:~$
satish.veeravalli@gmail.c is online now Report Post Edit/Delete Message

---

### Post by lswest on 2008-05-24
Sorry, i had to go into town for a little bit, but the error is referring to a problem within the package, so try this: ```
sudo apt-get install -f
sudo apt-get autoremove
sudo apt-get install unrar
``` and see if it works.  Also, you might want to update the 196 packages that are out of date by doing ```
sudo apt-get upgrade
```

---

### Post by RomeReactor on 2008-05-24
Hi. Disregard this post.

Sorry again for the lateness.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
hi thank u for reply i have executed the commands given by u this is the output:
satishv@satishv-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 196 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 6617 package `libgimp2.0':
 `Depends' field, invalid package name `libatk1.0-0!': character `!' not allowed - only letters, digits and -+._ allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)
satishv@satishv-desktop:~$ sudo apt-get autoremove
E: Invalid operation autoremove
satishv@satishv-desktop:~$

---

### Post by lswest on 2008-05-24
it seems to be a problem with a package (faulty code) and it may be fixed by developers soon, but i'm not sure what the problem is, or what package it applies to.  if you want, you can email me the rar archive, i can extract it, and stick it into a tar.gz archive so you can extract it.  (as long as the archive is <10MB, otherwise you can add me on msn or skype or something and send me the file there).  Sorry i can't do much more for you.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
ok i will email it and pls do me favour and if possible pls fix my problem can u give me ur email is pls

---

### Post by lswest on 2008-05-24
you can send it to [COLOR="Red"]<snip>[/COLOR]  and i would love to fix it for you, but i can't, maybe start a seperate thread on the error with the dpkg, maybe someone knows more than i do with regards to that problem.  Be sure to include that you run Dapper 6.06.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
after upgrading fallowing is displayed and pls send me ur [COLOR="Red"]_email id_[/COLOR]

satishv@satishv-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
The following packages will be upgraded:
  app-install-data-commercial apt apt-utils base-files bind9-host bzip2
  ca-certificates cpio cupsys cupsys-bsd cupsys-client dbus dbus-1-utils
  debconf debconf-i18n dnsutils dselect dvd+rw-tools ekiga evince
  evolution evolution-data-server evolution-plugins file firefox
  firefox-gnome-support gdb gdm gimp gimp-data gimp-python gnupg gs-esp
  gstreamer0.10-esd gstreamer0.10-plugins-good gtk2-engines-pixbuf hal
  hal-device-manager info initramfs-tools iptables klogd
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libaudio2 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-glib1 libbind9-0
  libblkid1 libbz2-1.0 libcairo2 libcamel1.2-8 libcdio6 libcomerr2
  libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libdbus-1-2
  libdbus-glib-1-2 libdns21 libebook1.2-5 libecal1.2-3
  libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7
  libedataserverui1.2-6 libegroupwise1.2-9 libexchange-storage1.2-1
  libexif12 libflac7 libfreetype6 libgd2-noxpm libgeoip1 libgimp2.0
  libgnutls12 libgsf-1-113 libgsf-1-common libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtop2-7 libhal-storage1 libhal1 libhsqldb-java
  libicu34 libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libkpathsea4
  libkrb53 liblircclient0 liblwres9 libmagic1 libmagick9
  libmusicbrainz4c2a libmysqlclient15off libnspr4 libnss3 libopal-2.2.0
  libpng12-0 libpoppler1 libpoppler1-glib libpq4 libpt-1.10.0
  libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libsmbclient
  libsndfile1 libsnmp-base libsnmp9 libsoup2.2-8 libspeex1 libss2
  libssl0.9.8 libtag1c2a libtheora0 libuuid1 libvorbis0a libvorbisenc2
  libvorbisfile3 libwmf0.2-7 libwpd8c2a libx11-6 libxfont1 libxml2
  libxml2-utils linux-386 linux-image-2.6.15-26-386
  linux-restricted-modules-2.6.15-26-386 linux-restricted-modules-common
  lvm2 mysql-common openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  openssh-client openssl poppler-utils popularity-contest python-apt
  python-libxml2 python-uno python2.4 python2.4-apt python2.4-dbus
  python2.4-examples python2.4-gdbm python2.4-libxml2 python2.4-minimal
  python2.4-tk rdesktop readahead rsync samba-common screen slocate
  smbclient ssh-askpass-gnome synaptic sysklogd tar tcpdump tk8.4
  ttf-opensymbol udev unzip update-manager util-linux vim vim-common
  vim-runtime w3m xinit xscreensaver-data xscreensaver-gl
  xserver-xorg-core
194 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
Need to get 7653kB/218MB of archives.
After unpacking 19.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/main vim 1:7.0-035+1ubuntu5.2~dapper1 [710kB]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/main vim-common 1:7.0-035+1ubuntu5.2~dapper1 [192kB]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/main vim-runtime 1:7.0-035+1ubuntu5.2~dapper1 [6337kB]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/main dvd+rw-tools 7.0-6~dapper2 [138kB]
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/main libtag1c2a 1.4-4~dapper1 [103kB]
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/main libtheora0 0.0.0.alpha7-1ubuntu1~dapper1 [94.5kB]
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/main readahead 1:0.20050517.0220-0ubuntu5~dapper1 [21.7kB]
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/main liblircclient0 0.8.0-9ubuntu1~dapper1 [56.4kB]
Fetched 7653kB in 3m55s (32.5kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 6617 package `libgimp2.0':
 `Depends' field, invalid package name `libatk1.0-0!': character `!' not allowed - only letters, digits and -+._ allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)
satishv@satishv-desktop:~$

---

### Post by lswest on 2008-05-24
the upgrade will not work until the problem is solved with the dpkg, which i (as stated above) do not know enough to be able to solve.  Also, i posted my email above.

Okay, i have a fix that **might** work for you.

```
sudo gedit /var/lib/dpkg/available
``` and go to line 6617 and change the piece that says > `libatk1.0-0!' to > `libatk1.0-0'  I do not know if this will work, nor do i know if it will break anything else, this is just an idea i had.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
ok thanks alot for ur support and iam mailing in couple of mins and i hope u will do the best thanks once again

---

### Post by lswest on 2008-05-24
you're welcome, and i'm sorry i couldn't give you a definite fix, i'll be sure to email you back the tar archive asap.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
:)

---

### Post by lswest on 2008-05-24
I've emailed it back to you, hope it all works out.

---

### Post by satish.veeravalli@gmail.c on 2008-05-24
hi this is waht iam getting,:(

satishv@satishv-desktop:~$ sudo gedit /var/lib/dpkg/available
Password:

(gedit:12783): Gdk-WARNING **: locale not supported by Xlib

(gedit:12783): Gdk-WARNING **: cannot set locale modifiers
satishv@satishv-desktop:~$

---

### Post by johnnylavah on 2008-08-22
nice!

---

### Post by agitdd99 on 2008-08-27
> **lswest said:**
> just do ```
sudo apt-get install unrar rar
``` and then you should be able to create & access rar archives.  (Double-click it to open the archive manager)  and unrar comes pre-installed in Hardy (8.04), so it should work just by double-clicking it.  If you receive an error message, please post it here.

thanks dude...that's really help...
i'm using ubuntu 8.04.1. i hope ubuntu will include this rar from the start in the next intrepid ibex. everyone will be needing it very much.

---

### Post by Joeb454 on 2008-08-27
I don't think it does.

however the [rar]("apt://rar") package does come with the package '[ubuntu-restricted-extras]("apt://ubuntu-restricted-extras")' in 8.10 from what I've seen

---

