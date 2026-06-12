---
title: "Common Problems / Frequently Asked Questions About Testing"
date: 2010-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-10-12
Here are answers to some commonly asked questions and solutions to common problems when testing pre-release Ubuntu versions. It will be updated during the testing period as necessary, so you may want to check back. Feel free to post suggestions for things that you think should be included (I won't promise to include them all, since making the document unnecessarily long typically discourages people from reading). 

[list] [*]**How can I upgrade to Oneiric?**

There's basically no point in upgrading to Natty at this point. It exists as a release in the archive, but isn't open for development, the Debian auto-sync hasn't started, and you can't really do anything useful. Unless you're a toolchain hacker or have special interest in a particular Debian sync issue, it's going to stay this way until after UDS.

That said, if you just want to feel like an early adopter, you can upgrade by replacing all instances of "natty" in your /etc/apt/sources.list with "oneiric", and issuing ```
sudo apt-get update && sudo apt-get dist-upgrade
```

Other methods such as using Update Manager will not be working until around Alpha 1. Be advised that "apt-get dist-upgrade"ing isn't a supported upgrade method for regular upgrades; it's only used in the early stages of a development cycle since it's the only way to upgrade during those periods.


[*]**I already have a testing installation. Do I have to reinstall the latest alpha / beta / RC when it comes out?**

If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the alpha / beta / RC, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix.

The milestone releases (alphas, betas and the RC) are slightly stabilized snapshots of the package archive at pre-decided dates, so they reflect the latest state of Natty on those dates. If you're up to date, you already have the latest packages. If you have to reinstall, and have an old disc image, you may want to [use zsync]("https://help.ubuntu.com/community/ZsyncCdImage") to avoid having to download the whole image.


[*]**If I install the alpha / beta / RC now, do I need to reinstall the final version when it's released? **

You don't have to (Update Manager will let you upgrade to the final version), but you may want to, if one or more of the below apply:

[list]
[*] You have tweaked your testing installation to a point where you're not aware of its exact components and configuration 


[*] You have replaced essential components of your installation with versions from external repositories / PPAs


[*] You have used package installation scripts or similar tools which are not trusted by the Ubuntu development community


[*] You have applied hacks / workarounds for testing purposes for good reason (prompted during structured testing, bug triage etc.), which may cause problems during daily usage of a stable installation


[*] You're affected by potential corner cases that may require a reinstall to fix (which will be documented in the release notes)[/list]


[*]**Update Manager offers a "Partial Upgrade". What should I do?**

[Read this]("http://ubuntuforums.org/showthread.php?t=1751299").


[*]**When / at what time will the alpha / beta / RC be released?**

Take a look at the [release schedule]("http://ubuntuforums.org/showthread.php?t=1747647") There's no specific time of the day for releases; just wait for the official release announcement, which will be mirrored immediately in the forum with a sticky thread as well.
 

[*]**I'm trying to report a bug, but I'm redirected to [this page]("http://help.ubuntu.com/community/ReportingBugs"). What's going on?**

That's intentional; you'll understand what's going on once you read that page :)


[*]**I'm trying to report a bug, but I don't know which package it belongs to. What should I do?**

Take a look at the [Bugs/FindRightPackage page on the wiki]("wiki.ubuntu.com/Bugs/FindRightPackage"), and try invoking Apport's (currently rather primitive) symptom-based reporting mode by issuing ```
ubuntu-bug
``` with no arguments. If those don't help, feel free to start a thread, or join the #ubuntu-bugs channel on [the Freenode IRC network]("help.ubuntu.com/community/InternetRelayChat") to ask for assistance.


[*]**My testing installation is badly broken. Is there a way to roll back to the stable release, or a relatively stable point in the development branch?**

No. You'll have to fix your installation or do a fresh install.


[*]**I haven't been getting updates for a while. Is it that there's nothing new in Natty, or is there a problem with the servers?**

The archive mirror you're using is probably lagging behind. You can see the status of the mirrors at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors). Also note that there will be relatively few updates during the freeze periods leading to alpha, beta and RC releases.


[*]**I downloaded the daily CD image, but it's oversized and I can't burn it on a CD.**

The daily images get built automatically, and due to the rapid and asynchronous nature of uploads to the development branch, no effort can be made to make them fit on a CD on a daily basis; such an effort is only made for the milestones. Note that you can still use oversized CD images for testing in a virtual machine.


[*]**Is testing Oneiric in a virtual machine useful?**

For testing kernels, X, and anything that interacts directly or at a low level with hardware, it's hard to produce useful bug reports. If filing bug reports from virtual machine installs, don't forget that they will be reports about Ubuntu failing to work on that particular virtual machine, and don't forget to indicate that you're testing on a virtual machine in your bug report. While virtual machines are a valid use case, bugs from real hardware are much more useful. If, however, you're only looking to test high-level functionality such as userspace applications, user interfaces, documentation, translations and so on, virtual machines are mostly fine.[/list]

---

### Post by novatillasku on 2011-05-18
Hi, i'm not sure my oneiric is ok.Today have this updates, is correct?
(sorry for my english ;-)

Se instalarán los siguientes paquetes NUEVOS:
  gnome-desktop3-data libappindicator3-1 libavahi-ui-gtk3-0 libcanberra-gtk3-0
  libcanberra-gtk3-module libdbusmenu-gtk3-3 libgail-3-0 libgnome-desktop-3-0
  libgnome-media-profiles-3.0-0 libgnomekbd7 libindicator3-3 libntfs-3g80
  libunique-3.0-0 libvte-2.90-9
Se actualizarán los siguientes paquetes:
  apport apport-gtk avahi-autoipd avahi-daemon avahi-utils baobab bsdmainutils
  checkbox checkbox-gtk firefox firefox-globalmenu firefox-gnome-support
  gconf-defaults-service gconf2 gconf2-common gir1.2-freedesktop
  gir1.2-gconf-2.0 gir1.2-glib-2.0 gir1.2-gtk-3.0 gnome-disk-utility
  gnome-media gnome-nettool gnome-screenshot gnome-search-tool
  gnome-settings-daemon gnome-system-log gnome-terminal gnome-terminal-data
  gnome-utils-common gstreamer0.10-alsa gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-tools gstreamer0.10-x
  icedtea-6-jre-cacao icedtea-6-jre-jamvm inputattach libasound2
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7
  libavahi-glib1 libavahi-gobject0 libavahi-ui0 libexif12 libgconf2-4
  libgdu-gtk0 libgdu0 libgirepository-1.0-1 libgladeui-1-11 libgnomekbd-common
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgweather-common libldap-2.4-2 libnautilus-extension1
  libnm-glib-vpn1 libnm-glib2 libnm-util1 libnss3 libnss3-1d libopencc1
  libpixman-1-0 libpng12-0 libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-style-human libreoffice-writer libsmbclient
  libwbclient0 libxklavier16 nautilus nautilus-data network-manager ntfs-3g
  nvidia-common openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  python-apport python-cupshelpers python-problem-report
  python-ubuntuone-control-panel python-uno python-wsgi-intercept rdesktop
  samba-common samba-common-bin smbclient software-center
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev ttf-opensymbol ubuntuone-control-panel
  ubuntuone-control-panel-gtk uno-libs3 ure wget xserver-common
  xserver-xorg-core

---

### Post by Harry33 on 2011-05-18
> **novatillasku said:**
> Hi, i'm not sure my oneiric is ok.Today have this updates, is correct?
(sorry for my english ;-)

Se instalarán los siguientes paquetes NUEVOS:
  gnome-desktop3-data libappindicator3-1 libavahi-ui-gtk3-0 libcanberra-gtk3-0
  libcanberra-gtk3-module libdbusmenu-gtk3-3 libgail-3-0 libgnome-desktop-3-0
  libgnome-media-profiles-3.0-0 libgnomekbd7 libindicator3-3 libntfs-3g80
  libunique-3.0-0 libvte-2.90-9
Se actualizarán los siguientes paquetes:
  apport apport-gtk avahi-autoipd avahi-daemon avahi-utils baobab bsdmainutils
  checkbox checkbox-gtk firefox firefox-globalmenu firefox-gnome-support
  gconf-defaults-service gconf2 gconf2-common gir1.2-freedesktop
  gir1.2-gconf-2.0 gir1.2-glib-2.0 gir1.2-gtk-3.0 gnome-disk-utility
  gnome-media gnome-nettool gnome-screenshot gnome-search-tool
  gnome-settings-daemon gnome-system-log gnome-terminal gnome-terminal-data
  gnome-utils-common gstreamer0.10-alsa gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-tools gstreamer0.10-x
  icedtea-6-jre-cacao icedtea-6-jre-jamvm inputattach libasound2
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7
  libavahi-glib1 libavahi-gobject0 libavahi-ui0 libexif12 libgconf2-4
  libgdu-gtk0 libgdu0 libgirepository-1.0-1 libgladeui-1-11 libgnomekbd-common
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgweather-common libldap-2.4-2 libnautilus-extension1
  libnm-glib-vpn1 libnm-glib2 libnm-util1 libnss3 libnss3-1d libopencc1
  libpixman-1-0 libpng12-0 libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-style-human libreoffice-writer libsmbclient
  libwbclient0 libxklavier16 nautilus nautilus-data network-manager ntfs-3g
  nvidia-common openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  python-apport python-cupshelpers python-problem-report
  python-ubuntuone-control-panel python-uno python-wsgi-intercept rdesktop
  samba-common samba-common-bin smbclient software-center
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev ttf-opensymbol ubuntuone-control-panel
  ubuntuone-control-panel-gtk uno-libs3 ure wget xserver-common
  xserver-xorg-core

That is correct, the GTK+3 porting has begun.
After those updates, your desktop will not be the same again.

---

### Post by cecilpierce on 2011-05-18
Desktop ?
Even my chair is getting shaky

---

### Post by Harry33 on 2011-05-18
> **cecilpierce said:**
> Desktop ?
Even my chair is getting shaky

Well that might be better estimation. :P

---

### Post by dniMretsaM on 2011-05-19
> **23meg said:**
> 

[LIST]
[*]**How can I upgrade to Oneiric?**

There's basically no point in upgrading to **Oneiric** at this point. It exists as a release in the archive, but isn't open for development, the Debian auto-sync hasn't started, and you can't really do anything useful. Unless you're a toolchain hacker or have special interest in a particular Debian sync issue, it's going to stay this way until after UDS.

That said, if you just want to feel like an early adopter, you can upgrade by replacing all instances of "**natty**" in your /etc/apt/sources.list with "oneiric", and issuing ```
sudo apt-get update && sudo apt-get dist-upgrade
```Other methods such as using Update Manager will not be working until around Alpha 1. Be advised that "apt-get dist-upgrade"ing isn't a supported upgrade method for regular upgrades; it's only used in the early stages of a development cycle since it's the only way to upgrade during those periods.
[/LIST]
Is this what you meant? (see bolded)

---

### Post by seeker5528 on 2011-05-19
> **23meg said:**
> That said, if you just want to feel like an early adopter, you can upgrade by replacing all instances of "maverick" in your /etc/apt/sources.list with "oneiric", and issuing ```
sudo apt-get update && sudo apt-get dist-upgrade
```

*Cringe* :P

Personally I always prefer to do the normal upgrade first ```
sudo apt-get upgrade
```

Or in Synaptic use the 'Mark All Upgrades' button if 'Settings --> preferences --> general --> system upgrade:' is set to 'Default Upgrade' which is the equivalent of 'apt-get upgrade'.

You could try setting the 'System Upgrade:' in Synaptic to 'Smart Upgrade' which is equivalent to 'apt-get dist-upgrade', but I prefer to using apt-get at the command line for that, then if the list of things that would be removed seems excessive or whacked in some other way, revert back to Synaptic.

If I didn't like what dist-upgrade would do, then I select individual packages installing small groups of packages, always monitoring what will be removed and what packages of a related group (samba, perl, etc...)  can't be upgraded and canceling if there is some question about what would be removed or if installing some part of a related set of packages and not other parts might leave things partially working or not working.

Later, Seeker

---

### Post by cariboo on 2011-05-20
I was a bit short of time when I posted this, I did a search and replace for natty, but didn't even think of doing it for Maverick.

**Edit**: FIxed

---

### Post by loukingjr on 2011-06-02
ok well, running xubuntu 11.10a1 in virtualbox and so far everything works except the users and groups module won't launch. I looked at the .desktop file and is no mention of xfce. do I need to change it?

thanks.

I also tried to add myself to the group vboxsf in the terminal using "useradd -G vboxsf louis" but it just tells me I'm already a user.

---

### Post by Dark_Ronius on 2011-09-01
> **23meg said:**
> **When / at what time will the alpha / beta / RC be released?**

Take a look at the [release schedule]("http://ubuntuforums.org/showthread.php?t=1747647") There's no specific time of the day for releases; just wait for the official release announcement, which will be mirrored immediately in the forum with a sticky thread as well.
 

I was so tempted to ask this regarding the beta... I've been so impatient and have kept checking back since the clock turned 12 midnight!!

Will the official announcement be made on ubuntu.com? I'll keep checking back in this forum till then.

---

### Post by cariboo on 2011-09-01
There isn't a set time for the release, the beta will be released when it is ready, and not a minute sooner.

---

### Post by Dark_Ronius on 2011-09-01
> **cariboo907 said:**
> There isn't a set time for the release, the beta will be released when it is ready, and not a minute sooner.

And I wouldn't have it any other way.

---

### Post by SheamusPatt on 2011-09-06
Much of this thread is now outdated, since Oneiric Beta 1 is now released.

In fact, it can probably be largely replaced by [https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Beta1](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Beta1) .

---

### Post by martin-gaspo on 2011-09-28
I think this is common problem, but it doesnt need separated topic. So I put it here. I hope it will help somebody.
**Skype in Ubuntu 11.10 Oneiric Ocelot**

[LIST=1]
[*]You need to install skype using
```
sudo apt-get install skype:i386
```

[*]In order to make it work with Pulse Audio you need to install also x86 librasries for pulse:
```
sudo apt-get install libpulse0:i386
```
[/LIST]


I've spent whole day looking for this solution and I coundt find it anywhere. Enjoy.

---

### Post by cariboo on 2011-09-28
> **martin-gaspo said:**
> I think this is common problem, but it doesnt need separated topic. So I put it here. I hope it will help somebody.
**Skype in Ubuntu 11.10 Oneiric Ocelot**

[LIST=1]
[*]You need to install skype using
```
sudo apt-get install skype:i386
```

[*]In order to make it work with Pulse Audio you need to install also x86 librasries for pulse:
```
sudo apt-get install libpulse0:i386
```
[/LIST]


I've spent whole day looking for this solution and I coundt find it anywhere. Enjoy.

There a couple of threads dealing with third party apps like skype and googleearth and the change to multiarch in this subforum.

---

### Post by M93 on 2011-09-28
everything seems to work great except for the mouse pad, as soon as i log in after a restart a box appears with "hover mouse" title
i have to choose what hovering with the mouse would do and there is no a "nothing" option....now if i hover the mouse on anything for 3 seconds it clicks it right away....very annoying, if u know a solution please tell me.
thanks.

---

