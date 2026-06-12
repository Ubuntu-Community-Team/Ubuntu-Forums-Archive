---
title: "HOWTO: Install gOS on Ubuntu"
date: 2007-11-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Frak on 2007-11-04
**Only available for x86 based systems.**

Open your sources.list

Ubuntu
```
gksu gedit /etc/apt/sources.list
```

Kubuntu
```
kdesu kate /etc/apt/sources.list
```

Xubuntu
```
gksu mousepad /etc/apt/sources.list
```

Enter these lines
```
# gOS Repositories
deb http://packages.thinkgos.com/gos/ painful main
deb-src http://packages.thinkgos.com/gos/ painful main
```

Import the key
```
wget http://www.thinkgos.com/files/gos_repo_key.asc
sudo apt-key add gos_repo_key.asc
rm gos_repo_key.asc
sudo aptitude update
```

Install
```
sudo aptitude install greenos-desktop xorg
```

NOTE: I used aptitude, because if you don't like it and want to get rid of it, just run

```
sudo aptitude remove greenos-desktop
```

It will then remove the entire Environment for you.

---

### Post by Dave_Man on 2007-11-09
I'm getting a 404 error when trying to get the key.

---

### Post by smartboyathome on 2007-11-09
> **Frak said:**
> NOTE: I used aptitude, because if you don't like it and want to get rid of it, just run

```
sudo aptitude remove greenos-desktop
```

It will then remove the entire Environment for you.

You can use apt-get autoremove to do the same thing, so there is really no need for aptitude anymore. :)

---

### Post by Frak on 2007-11-09
> **smartboyathome said:**
> You can use apt-get autoremove to do the same thing, so there is really no need for aptitude anymore. :)
aptitude IMHO is easier to type than apt-get.

---

### Post by AndrewGene on 2007-11-10
> **Frak said:**
> aptitude IMHO is easier to type than apt-get.

haha, and I believe that aptitude will also get rid of the dependencies automatically unlike apt-get

---

### Post by Frak on 2007-11-10
> **AndrewGene said:**
> haha, and I believe that aptitude will also get rid of the dependencies automatically unlike apt-get
As stated above, apt-get autoremove will also remove the dependencies, but typing aptitude vs. apt-get autoremove is not a very difficult decision...

---

### Post by TheOtherLinuxFreak on 2007-11-10
does this install it like when you install e17? -when you log in you select which sesion you want? I would want to try it but I dont want to change my system at all.

---

### Post by creeco on 2007-11-10
gOS is still in beta stage, right?

---

### Post by Steveway on 2007-11-10
That's nice but you should never use sudo for a graphical application!
So instead of sudo mousepad/kate/gedit use gksu mousepad/kate/gedit (Or gksudo , though gksudo is only a symlink to gksu so they do the same thing.)

---

### Post by Frak on 2007-11-10
> **TheOtherLinuxFreak said:**
> does this install it like when you install e17? -when you log in you select which sesion you want? I would want to try it but I dont want to change my system at all.

Installs factory default e17 modded to gOS look. Only messes with the icon cache, and not by that much. Your DE will still be available from the **Session** menu.

> **creeco said:**
> gOS is still in beta stage, right?

Alpha

> **Steveway said:**
> That's nice but you should never use sudo for a graphical application!
So instead of sudo mousepad/kate/gedit use gksu mousepad/kate/gedit (Or gksudo , though gksudo is only a symlink to gksu so they do the same thing.)

fixed

---

### Post by yesjoshyes on 2007-11-10
after trying the sudo-aptitude install greenos-desktop, it gave me:

 sudo aptitude install greenos-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "greenos-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by Frak on 2007-11-10
> **yesjoshyes said:**
> after trying the sudo-aptitude install greenos-desktop, it gave me:

 sudo aptitude install greenos-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "greenos-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done
Did you run sudo aptitude update first?

---

### Post by yesjoshyes on 2007-11-11
> **Frak said:**
> Did you run sudo aptitude update first?

yes.  i followed all the steps exactly.  weird...

---

### Post by bratliff on 2007-11-11
Are there any advantages to Gos?

Bratliff

---

### Post by Frak on 2007-11-11
> **bratliff said:**
> Are there any advantages to Gos?

Bratliff
Not one, besides a lighter desktop.

---

### Post by travnewmatic on 2007-11-11
I'm on a Powerbook.

```
travnewmatic@travnewmatic-laptop:~$ gksu gedit /etc/apt/sources.list
travnewmatic@travnewmatic-laptop:~$ sudo aptitude install greenos-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
**Couldn't find any package whose name or description matched "greenos-desktop"**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
travnewmatic@travnewmatic-laptop:~$
```

And here is my sources.list

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release powerpc (20071016)]/ gutsy main
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://ports.ubuntu.com/ubuntu-ports/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://ports.ubuntu.com/ubuntu-ports/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://ports.ubuntu.com/ubuntu-ports/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-backports main restricted universe multiverse
# deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-security main
# Line commented out by installer because it failed to verify:
# deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-security main
# Line commented out by installer because it failed to verify:
# deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
# deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-security multiverse

[B]# gOS Repositories
deb http://packages.thinkgos.com/gos/ painful main
deb-src http://packages.thinkgos.com/gos/ painful main[/B]
```

---

### Post by Frak on 2007-11-11
I'll ask the gOS devs whats going on with the repo.

---

### Post by Caffeine_Junky on 2007-11-11
Dose anyone know what the "Minimum system Requirements" would be for the gOS Operating System??

---

### Post by travnewmatic on 2007-11-11
> **Caffeine_Junky said:**
> Dose anyone know what the "Minimum system Requirements" would be for the gOS Operating System??

not a PowerPC G4?  haha.

---

### Post by Frak on 2007-11-11
> **Caffeine_Junky said:**
> Dose anyone know what the "Minimum system Requirements" would be for the gOS Operating System??
Pretty low. I can't name the exact requirements, but just really low.

---

### Post by Caffeine_Junky on 2007-11-11
cool, thanks Frak, ..i just need to know them to answer a pretty important question that is being asked at > [http://www.faqly.com/faq/view/id/34](http://www.faqly.com/faq/view/id/34)

It is a pretty important one that has not received any definitive answer as of yet

---

### Post by cybersaga on 2007-11-12
The gOS repositories seem to be up now. I'm installing at the moment.

Thanks for the instructions btw. I couldn't get the gOS live CD to work in anything I have. Hopefully this works and I can try it out.

---

### Post by Caffeine_Junky on 2007-11-12
@ Frak

Is there any news on when the gOS Form will be back online ??

thanks

---

### Post by Frak on 2007-11-12
> **Caffeine_Junky said:**
> @ Frak

Is there any news on when the gOS Form will be back online ??

thanks
RAV TUX is currently moving the site, so It'd probably be better to ask him, Tux Aubrey, or Vorian

---

### Post by Caffeine_Junky on 2007-11-12
> **Frak said:**
> RAV TUX is currently moving the site, so It'd probably be better to ask him, Tux Aubrey, or Vorian

Cool ..

 ... yeah, it would be a big job, ..I just thought you may have heard something ..

no prob's bud, ...thanks for the reply.. :)

---

### Post by Mike Easter on 2007-11-14
I installed gOS w/ Enlightenment on my gutsy Ub by editing my sources.list to include the gOS repo/s and then install greenos-desktop.

The result of that is that my login session manager is tht of gOS rather than gnome's, which gOS doesn't have an options button, so I have to use F10 to manage sessions.  That doesn't bother me much.  Also my menus in Ub's Gnome have been rearranged and some icons changed, such as Firefox's.  That doesn't bother me much either, except that I don't know how to fix it.

What I want most to fix is the complete absence of anything google such as is seen on this screenshot [http://www.thecodingstudio.com/opensource/linux/screenshots/original/gOS%201.0/3.gif](http://www.thecodingstudio.com/opensource/linux/screenshots/original/gOS%201.0/3.gif)  and is described in this article [http://www.desktoplinux.com/news/NS8172133608.html](http://www.desktoplinux.com/news/NS8172133608.html)  Google-centric theme -  clicking on the e-mail icon takes you to Gmail, the news icon sends you off to Google News, and the calendar "application" is Google Calendar.

I have no icons on my gOS desktop, just an enlightenment taskbar, and no googlesearch at the top and no google applications in my E17 menus.

Should I assume that:
 - buying an Everex with gOS installed gets you googleized desktop + codecs for mp3 & DVD
 - installing gOS from a disk gets you google desktop but no codecs for mp3 & DVD
 - installing gOS from install greenos-desktop gets you E17 but no googleized desktop


I don't quite understand how this editor handles URLs, so if the above don't work, try these little ones [http://snipurl.com/1tmnc](http://snipurl.com/1tmnc) & [http://snipurl.com/1tmng](http://snipurl.com/1tmng)

---

### Post by cybersaga on 2007-11-14
I had the same result. I was able to configure the taskbar to look like one in the gOS screenshot, but without all the Google icons and the widgets on the desktop. There even aren't any icons on the desktop.

---

### Post by Mike Easter on 2007-11-14
> **cybersaga said:**
> I had the same result. .

Here's what Nick Hughart sez in faqly

<NH> Currently there is a greenos-desktop package in our repository, but it will not give you the complete experience. We are still hammering out the packaging, but eventually this will be easier to do. Also, we do not use network-manager so if you do install the greenos-desktop, network-manager will be replaced by the network configuration tools we are using. </NH> [http://www.faqly.com/question/view/id/84](http://www.faqly.com/question/view/id/84)  

> I was able to configure the taskbar to look like one in the gOS screenshot, 

How did you do that?

> but without all the Google icons and the widgets on the desktop. There even aren't any icons on the desktop.

Apparently greenos-desktop isn't really the gOS desktop of Everex or the CD/DVD iso.

---

### Post by cybersaga on 2007-11-14
> **Mike Easter said:**
> How did you do that?Right-click the taskbar -> 'shelf 1' -> 'Shelf Configuration'. Under layout, select the one with the two squares filled in on the bottom left (third one down). Then boost the size if you want.

That did it for me. If it doesn't for you, click on 'Advanced', look under 'Styles' and make sure 'invisible' is selected.

---

### Post by Old Pink on 2007-11-17
**Help me!**

... please?

> matt@matt-desktop:~$ sudo aptitude install greenos-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages are BROKEN:
  adept-batch adept-installer adept-manager adept-notifier adept-updater 
  apt apt-utils aptitude debtags emodule-greenos-fileman enlightenment 
  libecore1 libecore1-bin libecore1-con libecore1-config libecore1-evas 
  libecore1-fb libecore1-file libecore1-ipc libecore1-job libecore1-txt 
  libecore1-x libedbus0 libedje0 libedje0-bin libeet0 libefreet-mime0 
  libefreet1 libehal0 libembryo0 libembryo0-bin libevas1 
  libevas1-engine-buffer libevas1-engine-software-generic 
  libevas1-engine-software-x11 libevas1-loader-eet libevas1-loader-gif 
  libevas1-loader-jpeg libevas1-loader-png libevas1-loader-svg 
  libevas1-loader-tiff libevas1-loader-xpm libevas1-saver-eet 
  libevas1-saver-jpeg libevas1-saver-png python-apt synaptic 
The following packages have been automatically kept back:
  libcupsys2-dev libsvn1 linux-restricted-modules-2.6.20-16-386 
  openoffice.org-filter-mobiledev openoffice.org-style-andromeda 
  openoffice.org-style-human tk8.4 
The following NEW packages will be automatically installed:
  e17 enlightenment-data enlightenment-init-theme-greenos 
  enlightenment-theme-greenos gos-keyring greenos-artwork greenos-gdm-theme 
  greenos-wallpapers libevas1-loaders-all 
The following packages have been kept back:
  adept adept-common bsdutils cupsys cupsys-bsd cupsys-client cupsys-common 
  debian-goodies dpkg-dev firefox firefox-gnome-support g++ g++-4.1 
  gnome-system-tools hpijs hplip hplip-data k3b kate kcontrol kdebase-bin 
  kdebase-data kdebase-dev kdebase-kio-plugins kdepasswd kdeprint kdesktop 
  kdm kfind khelpcenter kicker klipper kmenuedit konqueror 
  konqueror-nsplugins konsole ksmserver ksplash ksysguard ksysguardd kwin 
  libc6-dev libcupsimage2 libcupsys2 libflac++5c2 libflac7 libk3b2 libkonq4 
  libmysqlclient15off libnspr4 libnss3 liboggflac3 libpcre3 libpcre3-dev 
  libpcrecpp0 libpng12-0 libpng12-dev libpoppler1 libpoppler1-glib 
  libpoppler1-qt libsmbclient libsndfile1 libssl-dev libssl0.9.8 
  libstdc++6-4.1-dev linux-restricted-modules-2.6.20-16-generic 
  linux-restricted-modules-common mount mysql-common openoffice.org 
  openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress 
  openoffice.org-java-common openoffice.org-kde openoffice.org-l10n-en-us 
  openoffice.org-math openoffice.org-style-crystal 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer openssl poppler-utils python-uno samba samba-common 
  sbackup scribes smbclient subversion tk8.4-dev ttf-opensymbol tzdata 
  util-linux util-linux-locales 
The following NEW packages will be installed:
  e17 enlightenment-data enlightenment-init-theme-greenos 
  enlightenment-theme-greenos gos-keyring greenos-artwork greenos-desktop 
  greenos-gdm-theme greenos-wallpapers libevas1-loaders-all 
1 packages upgraded, 46 newly installed, 0 to remove and 114 not upgraded.
Need to get 20.1MB of archives. After unpacking 27.6MB will be used.
The following packages have unmet dependencies:
  libevas1-loader-eet: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libecore1-x: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
               Depends: libxdamage1 (>= 1:1.1) but 1:1.0.3-3 is installed.
  adept-manager: Depends: libapt-pkg-libc6.4-6-3.53 which is a virtual package.
  libevas1-loader-gif: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libecore1-file: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
                  Depends: libcurl3 (>= 7.16.2-1) but 7.15.5-1ubuntu2.1 is installed.
                  Depends: libkrb53 (>= 1.6.dfsg.1) but 1.4.4-5ubuntu3.3 is installed.
  libecore1-bin: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libehal0: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
            Depends: libdbus-1-3 (>= 1.1.1) but 1.0.2-1ubuntu4 is installed.
  libecore1-con: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
                 Depends: libcurl3 (>= 7.16.2-1) but 7.15.5-1ubuntu2.1 is installed.
                 Depends: libkrb53 (>= 1.6.dfsg.1) but 1.4.4-5ubuntu3.3 is installed.
                 Depends: libssl0.9.8 (>= 0.9.8e-1) but 0.9.8c-4ubuntu0.1 is installed and it is kept back.
  libecore1-evas: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  adept-installer: Depends: libapt-pkg-libc6.4-6-3.53 which is a virtual package.
  libevas1-loader-png: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libecore1-ipc: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
                 Depends: libssl0.9.8 (>= 0.9.8e-1) but 0.9.8c-4ubuntu0.1 is installed and it is kept back.
  libecore1-job: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libecore1: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  adept-updater: Depends: libapt-pkg-libc6.4-6-3.53 which is a virtual package.
  libevas1-loader-jpeg: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libevas1-loader-svg: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
                       Depends: libglib2.0-0 (>= 2.14.0) but 2.12.11-0ubuntu1 is installed.
                       Depends: libgtk2.0-0 (>= 2.12.0) but 2.10.11-0ubuntu3 is installed.
                       Depends: librsvg2-2 (>= 2.18.1) but 2.16.0-0ubuntu2 is installed.
  libefreet-mime0: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
                   Depends: libcurl3 (>= 7.16.2-1) but 7.15.5-1ubuntu2.1 is installed.
                   Depends: libkrb53 (>= 1.6.dfsg.1) but 1.4.4-5ubuntu3.3 is installed.
  libecore1-config: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  aptitude: Depends: libapt-pkg-libc6.4-6-3.53 which is a virtual package.
  libevas1-loader-xpm: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  python-apt: Depends: libapt-pkg-libc6.4-6-3.53 which is a virtual package.
  adept-batch: Depends: libapt-pkg-libc6.4-6-3.53 which is a virtual package.
  emodule-greenos-fileman: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libecore1-txt: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libeet0: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
           Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is installed.
  apt-utils: Depends: libapt-pkg-libc6.4-6-3.53 which is a virtual package.
  apt: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
       Depends: libcurl3-gnutls (>= 7.16.2-1) but 7.15.5-1ubuntu2.1 is installed.
       Depends: libgcc1 (>= 1:4.2.1) but 1:4.1.2-0ubuntu4 is installed.
       Depends: libstdc++6 (>= 4.2.1) but 4.1.2-0ubuntu4 is installed.
  libevas1-saver-jpeg: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libevas1-engine-software-x11: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libembryo0-bin: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libevas1-engine-software-generic: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libembryo0: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  debtags: Depends: libapt-pkg-libc6.4-6-3.53 which is a virtual package.
  libevas1-engine-buffer: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libecore1-fb: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libevas1-saver-eet: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  synaptic: Depends: libapt-pkg-libc6.4-6-3.53 which is a virtual package.
  libevas1-loader-tiff: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libedbus0: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
             Depends: libdbus-1-3 (>= 1.1.1) but 1.0.2-1ubuntu4 is installed.
  enlightenment: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
                 Depends: libcurl3 (>= 7.16.2-1) but 7.15.5-1ubuntu2.1 is installed.
                 Depends: libdbus-1-3 (>= 1.1.1) but 1.0.2-1ubuntu4 is installed.
                 Depends: libkrb53 (>= 1.6.dfsg.1) but 1.4.4-5ubuntu3.3 is installed.
                 Depends: libpam0g (>= 0.99.7.1) but 0.79-4ubuntu2 is installed.
                 Depends: libssl0.9.8 (>= 0.9.8e-1) but 0.9.8c-4ubuntu0.1 is installed and it is kept back.
  adept-notifier: Depends: libapt-pkg-libc6.4-6-3.53 which is a virtual package.
  libevas1-saver-png: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libedje0-bin: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
  libefreet1: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
              Depends: libcurl3 (>= 7.16.2-1) but 7.15.5-1ubuntu2.1 is installed.
              Depends: libkrb53 (>= 1.6.dfsg.1) but 1.4.4-5ubuntu3.3 is installed.
  libevas1: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
            Depends: libfreetype6 (>= 2.3.5) but 2.2.1-5ubuntu1.1 is installed.
            Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is installed.
  libedje0: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
apt [0.6.46.4ubuntu10 (feisty, now)]
e17 [Not Installed]
emodule-greenos-fileman [Not Installed]
enlightenment [Not Installed]
enlightenment-data [Not Installed]
greenos-desktop [Not Installed]
libecore1 [Not Installed]
libecore1-bin [Not Installed]
libecore1-con [Not Installed]
libecore1-config [Not Installed]
libecore1-evas [Not Installed]
libecore1-fb [Not Installed]
libecore1-file [Not Installed]
libecore1-ipc [Not Installed]
libecore1-job [Not Installed]
libecore1-txt [Not Installed]
libecore1-x [Not Installed]
libedbus0 [Not Installed]
libedje0 [Not Installed]
libedje0-bin [Not Installed]
libeet0 [Not Installed]
libefreet-mime0 [Not Installed]
libefreet1 [Not Installed]
libehal0 [Not Installed]
libembryo0 [Not Installed]
libembryo0-bin [Not Installed]
libevas1 [Not Installed]
libevas1-engine-buffer [Not Installed]
libevas1-engine-software-generic [Not Installed]
libevas1-engine-software-x11 [Not Installed]
libevas1-loader-eet [Not Installed]
libevas1-loader-gif [Not Installed]
libevas1-loader-jpeg [Not Installed]
libevas1-loader-png [Not Installed]
libevas1-loader-svg [Not Installed]
libevas1-loader-tiff [Not Installed]
libevas1-loader-xpm [Not Installed]
libevas1-loaders-all [Not Installed]
libevas1-saver-eet [Not Installed]
libevas1-saver-jpeg [Not Installed]
libevas1-saver-png [Not Installed]

Score is -9700

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  libcupsys2-dev libsvn1 linux-restricted-modules-2.6.20-16-386 
  openoffice.org-filter-mobiledev openoffice.org-style-andromeda 
  openoffice.org-style-human tk8.4 
The following packages have been kept back:
  adept adept-batch adept-common adept-installer adept-manager 
  adept-notifier adept-updater apt apt-utils bsdutils cupsys cupsys-bsd 
  cupsys-client cupsys-common debian-goodies dpkg-dev firefox 
  firefox-gnome-support g++ g++-4.1 gnome-system-tools hpijs hplip 
  hplip-data k3b kate kcontrol kdebase-bin kdebase-data kdebase-dev 
  kdebase-kio-plugins kdepasswd kdeprint kdesktop kdm kfind khelpcenter 
  kicker klipper kmenuedit konqueror konqueror-nsplugins konsole ksmserver 
  ksplash ksysguard ksysguardd kwin libc6-dev libcupsimage2 libcupsys2 
  libflac++5c2 libflac7 libk3b2 libkonq4 libmysqlclient15off libnspr4 
  libnss3 liboggflac3 libpcre3 libpcre3-dev libpcrecpp0 libpng12-0 
  libpng12-dev libpoppler1 libpoppler1-glib libpoppler1-qt libsmbclient 
  libsndfile1 libssl-dev libssl0.9.8 libstdc++6-4.1-dev 
  linux-restricted-modules-2.6.20-16-generic 
  linux-restricted-modules-common mount mysql-common openoffice.org 
  openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress 
  openoffice.org-java-common openoffice.org-kde openoffice.org-l10n-en-us 
  openoffice.org-math openoffice.org-style-crystal 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer openssl poppler-utils python-uno samba samba-common 
  sbackup scribes smbclient subversion tk8.4-dev ttf-opensymbol tzdata 
  util-linux util-linux-locales 
0 packages upgraded, 0 newly installed, 0 to remove and 115 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
matt@matt-desktop:~$ 
... completed with no changes

---

### Post by puccaso on 2007-11-17
how do we get the google apps and the facebook links etc that you get on the gOS iso??

---

### Post by Frak on 2007-11-18
> **puccaso said:**
> how do we get the google apps and the facebook links etc that you get on the gOS iso??
That needs some reworking of webrunner and the iBar. I'll look into it.

---

### Post by ascandroli on 2007-11-19
I noticed that the gOS gtk theme "ubuntulooks-aquagreen-alt", is not included in this package, in fact I couldn't find it in any package, so I think it's not packaged at all. 
To achieve the gos live cd L&F I had to copy it manually from the theme from my live CD and install it using gtk-chtheme.

Thanks for the instructions, gOS desktop is sweet and light. kudos to the gOS crew.

Saludos.
Alejandro.

---

### Post by Factory on 2007-11-22
Where can we get out hands on those nice icons? I'd love a gcalendar/facebook etc icon pack.

---

### Post by Frak on 2007-11-22
> **Factory said:**
> Where can we get out hands on those nice icons? I'd love a gcalendar/facebook etc icon pack.
Ask on the [gOS forum]("http://www.cafelinux.org/gosforum"), they would have a better answer than I would.

---

### Post by K.Mandla on 2007-11-22
Thanks for the howto. I followed your instructions with a command-line installation, and I noticed that the greenos-desktop package doesn't pull in xorg, gdm, a gtk2 engine or any of the applications (like Firefox or XMMS) that are included by "default." 

These aren't your fault, I just thought I would mention them in case you want to include a note about that in your howto. Anyone who's installing from ground zero will need to add some more packages before reaching a usable state. Thanks again!

---

### Post by Frak on 2007-11-22
> **K.Mandla said:**
> Thanks for the howto. I followed your instructions with a command-line installation, and I noticed that the greenos-desktop package doesn't pull in xorg, gdm, a gtk2 engine or any of the applications (like Firefox or XMMS) that are included by "default." 

These aren't your fault, I just thought I would mention them in case you want to include a note about that in your howto. Anyone who's installing from ground zero will need to add some more packages before reaching a usable state. Thanks again!
Thanks K.Mandla, I'll update the guide to reflect that.

---

### Post by rich.bradshaw on 2007-11-22
With Kubuntu a choice doesn't appear in KDM to boot it - how do you load gOS?

Edit: Just ignore me!

---

### Post by rich.bradshaw on 2007-11-22
Hmm - it's just E17 at the moment - still cool, but would be interested to see it with the google shortcuts etc.

---

### Post by md5hash on 2007-11-22
i  just finished installing.. where is it?

---

### Post by Frak on 2007-11-23
> **md5hash said:**
> i  just finished installing.. where is it?
you may have to restart for the daemon to make the necissary changes.

---

### Post by smartboyathome on 2007-11-24
Also, it is located in the sessions part of your login screen.

---

### Post by microsoft92sucks on 2007-11-25
After I followed the how to, I rebooted the gOS login screen came up I pressed f10 to choose gOS but it wasn't there (nor e17, Enlightenment, nothing like that) So I went to synaptic to see if greenos desktop was installed and it wasn't so I tried to mark it for instillation but I got this 
```

Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies Make sure that all required repositories are added and enabled in the preferences

greenos-desktop:
 Depends: e17 but it is not going to be installed
 Depends: emodule-greenos-fileman but it is not going to be installed

```
But then attempt to install e17 & get,
```
Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies Make sure that all required repositories are added and enabled in the preferences

e17:
 Depends: enlightenment but it is not going to be installed
 Depends: libevas1-loaders-all but it is not going to be installed

```and something similar if I try to install emodule-greenos-fileman, or Enlightenment or anything else it tells me to install for something it won't let me install!
Does anyone know how to fix this?

---

### Post by Frak on 2007-11-27
> **microsoft92sucks said:**
> After I followed the how to, I rebooted the gOS login screen came up I pressed f10 to choose gOS but it wasn't there (nor e17, Enlightenment, nothing like that) So I went to synaptic to see if greenos desktop was installed and it wasn't so I tried to mark it for instillation but I got this 
```

Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies Make sure that all required repositories are added and enabled in the preferences

greenos-desktop:
 Depends: e17 but it is not going to be installed
 Depends: emodule-greenos-fileman but it is not going to be installed

```
But then attempt to install e17 & get,
```
Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies Make sure that all required repositories are added and enabled in the preferences

e17:
 Depends: enlightenment but it is not going to be installed
 Depends: libevas1-loaders-all but it is not going to be installed

```and something similar if I try to install emodule-greenos-fileman, or Enlightenment or anything else it tells me to install for something it won't let me install!
Does anyone know how to fix this?
Enable all repos and try again. The devs might be doing more maintenance. They were talking about having the Ubuntu installation of gOS being more like the ACTUAL gOS.

---

### Post by microsoft92sucks on 2007-11-28
I did a whole reinstall of Ubuntu and now I got it working fine.

Can you get Compiz-Fusion working on gOS?

---

### Post by mouseboyx on 2007-11-28
So gOS is just Ubuntu packaged with a different desktop environment?

The desktop environment is too simple i don't know why anyone would want to switch to it from gnome.

---

### Post by Frak on 2007-11-28
> **microsoft92sucks said:**
> I did a whole reinstall of Ubuntu and now I got it working fine.

Can you get Compiz-Fusion working on gOS?
It's possible, yet the e17 devs are working on their own version of Compiz, which will be lighter and more suited for the enlightenment environment.

@mousebox
gOS is actually ubuntu with different programs and proprietary codecs (only on the PC version from Everex | Fluendo Codecs; else the ubuntu-restricted-extras provides the codecs.). More suited for the casual user.

---

### Post by microsoft92sucks on 2007-11-28
> **Frak said:**
> It's possible, yet the e17 devs are working on their own version of Compiz, which will be lighter and more suited for the enlightenment environment.


Has anybody gotten compiz fusion working on e17?
If so is there a good how to on it?

When will there be a compiz just for e17?

---

### Post by Frak on 2007-11-28
> **microsoft92sucks said:**
> Has anybody gotten compiz fusion working on e17?
If so is there a good how to on it?

When will there be a compiz just for e17?
Again, check the gOS forums, I'ven't checked lately, so I couldn't tell you.

---

### Post by smartboyathome on 2007-11-29
I know Compiz WILL run on it, but you would have to use an Emerald theme with it (ick!). They are working on their own compositing manager (like Frak said) based off of xcompmgr, but right now it is broken and rendered completely unusable, so I would suggest using just xcompmgr (which for now will give you the same effects as Enlightenment's compositing manager).

---

### Post by go_beep_yourself on 2007-12-27
> **Frak said:**
> Open your sources.list

Ubuntu
```
gksu gedit /etc/apt/sources.list
```

Kubuntu
```
kdesu kate /etc/apt/sources.list
```

Xubuntu
```
gksu mousepad /etc/apt/sources.list
```

Enter these lines
```
# gOS Repositories
deb http://packages.thinkgos.com/gos/ painful main
deb-src http://packages.thinkgos.com/gos/ painful main
```

Import the key
```
wget http://www.thinkgos.com/files/gos_repo_key.asc
sudo apt-key add gos_repo_key.asc
rm gos_repo_key.asc
sudo aptitude update
```

Install
```
sudo aptitude install greenos-desktop xorg
```

NOTE: I used aptitude, because if you don't like it and want to get rid of it, just run

```
sudo aptitude remove greenos-desktop
```

It will then remove the entire Environment for you.

This only works with 32 bit because gOS isnt available in 64 bit.

---

### Post by tygern on 2008-02-04
If I were to install gOS on gutsy, would I still be able to access the default gutsy desktop manager (through the sessions menu)?

---

### Post by DarkZyzx on 2008-02-08
> **tygern said:**
> If I were to install gOS on gutsy, would I still be able to access the default gutsy desktop manager (through the sessions menu)?

Yes, I think so.
:popcorn:

---

### Post by tygern on 2008-02-08
Does anyone know for sure?

---

### Post by r4ik on 2008-02-09
Works like a charm !
Thanks to the OP.

---

### Post by tygern on 2008-02-11
Running the install command: ```
sudo aptitude install greenos-desktop xorg
``` removed vlc for some reason.  Anyone know why?

---

### Post by dogeatery on 2008-03-25
Hi, I am having trouble with finding and starting gOS desktop.  I installed it but when I look in my session manager, it does not appear as an option.  Any hints?

---

### Post by buggs187 on 2008-05-05
Now that gOS Space was released using gnome with ubuntu 7.10 is there a easy way to install there custom settings on 8.04?

---

### Post by Frak on 2008-05-05
> **buggs187 said:**
> Now that gOS Space was released using gnome with ubuntu 7.10 is there a easy way to install there custom settings on 8.04?
I'm still looking into the new developments. I'll post back soon.

---

### Post by vikas776 on 2008-05-06
wget [http://www.thinkgos.com/files/gos_repo_key.asc](http://www.thinkgos.com/files/gos_repo_key.asc)
--13:22:06--  [http://www.thinkgos.com/files/gos_repo_key.asc](http://www.thinkgos.com/files/gos_repo_key.asc)
           => `gos_repo_key.asc'
Resolving [www.thinkgos.com](www.thinkgos.com)... 72.47.199.71
Connecting to [www.thinkgos.com|72.47.199.71|:80](www.thinkgos.com|72.47.199.71|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
13:22:07 ERROR 404: Not Found.


i am not able to add key

plz someone help me

---

### Post by darthchaosofrspw on 2008-06-08
> **vikas776 said:**
> wget [http://www.thinkgos.com/files/gos_repo_key.asc](http://www.thinkgos.com/files/gos_repo_key.asc)
--13:22:06--  [http://www.thinkgos.com/files/gos_repo_key.asc](http://www.thinkgos.com/files/gos_repo_key.asc)
           => `gos_repo_key.asc'
Resolving [www.thinkgos.com](www.thinkgos.com)... 72.47.199.71
Connecting to [www.thinkgos.com|72.47.199.71|:80](www.thinkgos.com|72.47.199.71|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
13:22:07 ERROR 404: Not Found.


i am not able to add key

plz someone help me

I believe the E17 version of gOS (gOS Rocket E) is no longer officially supported, as the official repositories for gOS Rocket E were deleted from their website when they introduced gOS Space.

---

### Post by GhostAir89 on 2008-07-29
So that mean gOS in no longer opensource:mad:
what a shame!:(

---

### Post by Frak on 2008-07-29
> **GhostAir89 said:**
> So that mean gOS in no longer opensource:mad:
what a shame!:(
?

It's still Open Source. It has to be legally. I'm just too lazy to update :P

---

### Post by highphilosopher on 2008-08-16
> **Frak said:**
> aptitude IMHO is easier to type than apt-get.

you-must-be-kidding.-apt-get-is-so-easy-to-type.

:)

---

### Post by x0x on 2008-11-24
i am getting error 


--(c0re@c0re)-(/home/c0re)--
--(22:03:Mon,24 Nov 08:$)-- wget [http://www.thinkgos.com/files/gos_repo_key.asc](http://www.thinkgos.com/files/gos_repo_key.asc)
--2008-11-24 22:03:08--  [http://www.thinkgos.com/files/gos_repo_key.asc](http://www.thinkgos.com/files/gos_repo_key.asc)
Resolving [www.thinkgos.com](www.thinkgos.com)... 208.43.218.186
Connecting to [www.thinkgos.com|208.43.218.186|:80](www.thinkgos.com|208.43.218.186|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3992 (3.9K) [text/html]
Saving to: `gos_repo_key.asc'

100%[===================================================================================================================>] 3,992       --.-K/s   in 0s      

2008-11-24 22:03:11 (162 MB/s) - `gos_repo_key.asc' saved [3992/3992]

--(c0re@c0re)-(/home/c0re)--
--(22:03:Mon,24 Nov 08:$)-- sudo apt-key add gos_repo_key.asc
gpg: no valid OpenPGP data found.

---

### Post by japtar10101 on 2008-12-05
Huh.  Looks like we have to wait a little longer.  The repository is currently unavailable according to Google Groups:
[http://groups.google.com/group/goslinux/browse_thread/thread/fa20411a2cd600b2/fa2588ea45870041?lnk=gst&q=openpgp#fa2588ea45870041](http://groups.google.com/group/goslinux/browse_thread/thread/fa20411a2cd600b2/fa2588ea45870041?lnk=gst&q=openpgp#fa2588ea45870041)

---

