---
title: "Systemd for Oneiric?"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sumski on 2011-09-26
So, is there a systemd package for Oneiric?

---

### Post by tekstr1der on 2011-09-26
Search much?

[http://lmgtfy.com/?q=systemd+ubuntu](http://lmgtfy.com/?q=systemd+ubuntu)

---

### Post by lucazade on 2011-09-26
I don't think you will find any systemd package in repos, there are some outdated ppa with systemd but I don't suggest you to try..
[https://wiki.ubuntu.com/systemd](https://wiki.ubuntu.com/systemd)

*if* systemd will land in ubuntu it will be after 12.04 LTS, but sincerly I doubt this will happen.

---

### Post by oldos2er on 2011-09-26
```
ann@ann-Dell-XPS-410:~$ aptitude show live-config-systemd
Package: live-config-systemd             
New: yes
State: not installed
Version: 3.0~a22-1ubuntu1
Priority: optional
Section: universe/misc
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 61.4 k
Suggests: systemd
Conflicts: live-config-backend, live-config-backend
Replaces: live-config-backend, live-config-backend
Provides: live-config-backend
Description: Debian Live - System Configuration Scripts (systemd backend)
 live-config contains the scripts that configure a Debian Live system during the
 boot process (late userspace). 
 
 This package contains the systemd backend (experimental!).
Homepage: http://live.debian.net/devel/live-config/
```

The "experimental!" is enough to scare me away.

---

### Post by sumski on 2011-09-26
> **tekstr1der said:**
> Search much?

[http://lmgtfy.com/?q=systemd+ubuntu](http://lmgtfy.com/?q=systemd+ubuntu)

I couldn't find any other than that oldos2er posted, and i know there was a Maverick PPA...

---

### Post by t1497f35 on 2011-09-26
> **lucazade said:**
> 
*if* systemd will land in ubuntu it will be after 12.04 LTS, but sincerly I doubt this will happen.
Of course it can only be adopted _after_ 12.04.

Though I hope it gets adopted (not to start a rant, just my opinion).
2 serious pros:
1) Much more advanced and versatile than Ubuntu's "upstart", in fact, it almost looks like the ultimate choice.
2) Canonical doesn't have to waste dev time to keep "upstart" up to date, also afaik the dev who started "upstart" doesn't work anymore for Canonical or so.

1 cons:
1) Takes effort to adopt. But by 12.10 systemd should be more mature to make for a relatively painless transition.

---

### Post by tekstr1der on 2011-09-26
> **sumski said:**
> I couldn't find any other than that oldos2er posted, and i know there was a Maverick PPA...

The PPA listed in the Ubuntu Wiki article did not mention being Maverick-specific. Strange that it is.

I am interested in seeing systemd becoming the standard across distros.

As it is clearly still highly experimental, I wouldn't expect it (if ubuntu adopts it at all) in an LTS till 14.04. Canonical's got a lot of time and effort invested in upstart.

---

### Post by lucazade on 2011-09-26
> **t1497f35 said:**
> Of course it can only be adopted _after_ 12.04.

Though I hope it gets adopted (not to start a rant, just my opinion).
2 serious pros:
1) Much more advanced and versatile than Ubuntu's "upstart", in fact, it almost looks like the ultimate choice.
2) Canonical doesn't have to waste dev time to keep "upstart" up to date, also afaik the dev who started "upstart" doesn't work anymore for Canonical or so.

1 cons:
1) Takes effort to adopt. But by 12.10 systemd should be more mature to make for a relatively painless transition.

I hope as well it will be adopted in future, transition anyway is quite hard as you stated.
This is an interesting overview made by the systemd author himself comparing sysvinit,	Upstart	and systemd.
[http://0pointer.de/blog/projects/why.html](http://0pointer.de/blog/projects/why.html)
(didn't know Scott leaved Canonical.. searched now.. he's on Google boat)

---

### Post by castrojo on 2011-09-26
> **t1497f35 said:**
> 1) Much more advanced and versatile than Ubuntu's "upstart", in fact, it almost looks like the ultimate choice.

Citation needed!

> 
2) Canonical doesn't have to waste dev time to keep "upstart" up to date, also afaik the dev who started "upstart" doesn't work anymore for Canonical or so.

Right, he works at Google, which includes working on Upstart for ChromeOS.

---

### Post by t1497f35 on 2011-09-26
> **castrojo said:**
> Citation needed!
Citations don't matter, since one can cite even a demented person. What matters is facts and common sense. If the link above your post isn't enough - then I can't help you figure it out.

---

### Post by alphacrucis2 on 2011-09-26
I read that SUSE have backed out of including it in their upcoming release. It sounds like they needed more time get get everything sorted out so will now delay it till the following release. I suspect Canonical had enough on their plate getting 11.10 out without adding the complication of systemd. The latest Fedora has it but they have the advantage that the main systemd dev works for Redhat.

---

### Post by sumski on 2011-09-26
I would also like systemd replacing upstart, but for now it would satisfy me if it would be included in repositories, at least some semi-official PPA (this would obviously help testing systemd on Ubuntu -Debian, openSUSE and Arch have them and they didn't replace their own init's)

---

### Post by seeker5528 on 2011-09-26
> **t1497f35 said:**
> Citations don't matter, since one can cite even a demented person. What matters is facts and common sense. If the link above your post isn't enough - then I can't help you figure it out.

Of course a list of checkboxes indicating supported features is only useful if said features are proven to be useful enough to justify the added complexity otherwise all you have is a [Rube Goldberg machine](http://en.wikipedia.org/wiki/Rube_Goldberg_machine). 

But maybe that's just me. :p

Later, Seeker

---

### Post by ranch hand on 2011-09-26
> **oldos2er said:**
> ```
ann@ann-Dell-XPS-410:~$ aptitude show live-config-systemd
Package: live-config-systemd             
New: yes
State: not installed
Version: 3.0~a22-1ubuntu1
Priority: optional
Section: universe/misc
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 61.4 k
Suggests: systemd
Conflicts: live-config-backend, live-config-backend
Replaces: live-config-backend, live-config-backend
Provides: live-config-backend
Description: Debian Live - System Configuration Scripts (systemd backend)
 live-config contains the scripts that configure a Debian Live system during the
 boot process (late userspace). 
 
 This package contains the systemd backend (experimental!).
Homepage: http://live.debian.net/devel/live-config/
```The "experimental!" is enough to scare me away.
I don't think that should be too much worry at this point.  11.10 is based on Debian unstable.

Systemd is in the Debian testing repo (29-1.1) so it has gotten secure enough to be in the repo that 12.04 will be based on.

That does not strike me as real scary.

That said we are using sysvinit in testing and unstable.

The package in unstable (Sid) is 30~a27-1 by the way.

---

### Post by ranch hand on 2011-09-26
> **alphacrucis2 said:**
> I read that SUSE have backed out of including it in their upcoming release. It sounds like they needed more time get get everything sorted out so will now delay it till the following release. I suspect Canonical had enough on their plate getting 11.10 out without adding the complication of systemd. The latest Fedora has it but they have the advantage that the main systemd dev works for Redhat.
Yes, supposedly there should be no new, unused before, packages of import in 12.04.

It will be easier for Debian to go to systemd than for Ubuntu as compatibility with syvinit is pretty good right now.  Upstart compatibility, as I understand it, is nothing.  Therefore there would (will?) be a good deal of work to do to use systemd in Ubuntu.

---

### Post by ranch hand on 2011-09-26
I have not picked my victim yet but one of my Debian testing or unstable installs is going to get systemd installed.  Right now I am leaning toward Sid as it has a newer version but I have not really looked into that version very well.

The one in testing seems to be working pretty well for the folks that I have heard about using it.

Of coarse one thing should be kept in mind, I am a Rube Goldberg fan.  Not sure that this is a Rube Goldberg type design but I expect I will find out when I install it and take a closer look.

I do think the combination of plymouth, upstart and ureadahead comes awfully close.

---

### Post by jbicha on 2011-09-26
> **alphacrucis2 said:**
> I read that SUSE have backed out of including it in their upcoming release. It sounds like they needed more time get get everything sorted out so will now delay it till the following release. I suspect Canonical had enough on their plate getting 11.10 out without adding the complication of systemd. The latest Fedora has it but they have the advantage that the main systemd dev works for Redhat.

You read wrong. It's been removed from one testing repository so that the developers can focus on getting systemd ready for 12.1, their next release. [https://lwn.net/Articles/459493](https://lwn.net/Articles/459493)

> **ranch hand said:**
> 
It will be easier for Debian to go to systemd than for Ubuntu as  compatibility with syvinit is pretty good right now.  Upstart  compatibility, as I understand it, is nothing.  Therefore there would  (will?) be a good deal of work to do to use systemd in Ubuntu.

No, as systemd is Linux only and Debian is not, Debian as far as I know has no actual plan to move away from the universal init system they are using now, although systemd will be packaged and hopefully will work as an alternative.

---

### Post by ranch hand on 2011-09-27
Yes, doubt that they would change to it, at least any time soon.  Sysvinit works great.  Why change what works?

They are working on it as a Debian package however.   I like fooling with things.  I have several installs of each of stable, testing and Sid.

One Squeeze is my secure business install.   One Testing is my main use install.  The rest are for testing various things.

Many have, or soon will, served their current purposes.  Therefore I have to find some other way to screw with them.

Systemd caught my eye a few months ago as being really interesting.  I never have checked  because I have another thing in mind for the extra 2 Squeeze installs (Debian-LIve), but I think there is even a package in those repos too.

---

### Post by sumski on 2011-09-27
Interesting - 
[http://lists.debian.org/debian-devel/2011/07/msg00269.html](http://lists.debian.org/debian-devel/2011/07/msg00269.html)

---

### Post by t1497f35 on 2011-09-27
> **seeker5528 said:**
> Of course a list of checkboxes indicating supported features is only useful if said features are proven to be useful enough to justify the added complexity otherwise all you have is a [Rube Goldberg machine]("http://en.wikipedia.org/wiki/Rube_Goldberg_machine"). 

But maybe that's just me. :p

Later, Seeker
FYI the dev behind it is Lennart who's a serious (long) longtime Linux contributor and he works for Red Hat who's also a longtime Linux heavyweight contributor, not to mention the long list of features and some mainline distros that are clearly in favor of it for serious reasons. So, with all respect, your assumptions that systemd could be some type of abstract fallacy tells us more about yourself then about systemd.

---

### Post by el_koraco on 2011-09-27
> **ranch hand said:**
> Yes, doubt that they would change to it, at least any time soon.  Sysvinit works great.  Why change what works?


Because systemd promises to be a one-stop shop for the whole HAL-udev-dbus-consolekit-policykit-whateverelse mess. Upstart was supposed to do the same, but the geek wars stopped it dead, so it's a semi-finished product with no real prospects for future development. Systemd is not perfect, but the potential is there, with development shifting to that particular mechanism. Of course, with Debian's dinosaur-like pace of adopting new software (the big stuff, not the latest version of a music player), any sort of certainty is gone out the window.

---

### Post by ranch hand on 2011-09-27
> **el_koraco said:**
> Because systemd promises to be a one-stop shop for the whole HAL-udev-dbus-consolekit-policykit-whateverelse mess. Upstart was supposed to do the same, but the geek wars stopped it dead, so it's a semi-finished product with no real prospects for future development. Systemd is not perfect, but the potential is there, with development shifting to that particular mechanism. Of course, with Debian's dinosaur-like pace of adopting new software (the big stuff, not the latest version of a music player), any sort of certainty is gone out the window.
That is kind of misleading.

Debian is certainly slow to put things into Debian Stable.  Cutting edge things do get into the experimental repo pretty fast, though.

So you can get it from there and stick it in Sid anytime you want.  Takes a while to get into the Sid repo.  Usually pretty fast into the Testing repo from Sid.

Not sure what the rules for the Squeeze backports repo is on things that are stable in Wheezy but nothing new is likely to make it to the Squeeze repos at all.  Wheezy, right now, is quite different than Squeeze.

We are using the 3.0.0+39 kernel (standard kernel - I am using the liquorix kernel 3.0.0.1).  Iceweasel is 6.0.2.

Not that "backwards".

Systemd will have to prove itself to be up to Debian standards for a package before it hits what ever the Debian stable version is at the time, as the standard install anyway.  This will not happen in Squeeze as it is released.

From what I have read systemd sounds like it may be good.   With the big changes in Gnome I would be surprised if it makes it in Wheezy.  It still needs a lot of work and then it would have to be integrated into Debian.  Just getting the gnome3 and gtk3 bugs worked out to match the rules for a stable release makes me think it will be the one after Wheezy before you could see it in Debian Stable.

Could be wrong of coarse.  Someone may get all the bugs worked out in time.  I may not be giving the Debian devs enough credit.  Just can't see it as a priority though.

---

### Post by castrojo on 2011-09-27
> **el_koraco said:**
> Upstart was supposed to do the same, but the geek wars stopped it dead, so it's a semi-finished product with no real prospects for future development.

I don't know where you get your information, but this is untrue, there are paid developers working on Upstart and currently there are no plans to stop development.

---

### Post by sumski on 2011-09-28
> **el_koraco said:**
> Of course, with Debian's dinosaur-like pace of adopting new software (the big stuff, not the latest version of a music player), any sort of certainty is gone out the window.

Well, systemd entered in Debian repos on the same day it got released, so i wouldn't call it slow, ranch_hand explained it better. Doubt it will be default in Wheezy, *maybe* Wheezy +1 , but it doesn't have to be default , it's good enough to be offered as an alternative. 

I personally haven't had any issues with it on both my Sid and Arch installations, and it's much simpler than sysv-init/upstart

---

### Post by el_koraco on 2011-09-29
> **castrojo said:**
> I don't know where you get your information, but this is untrue, there are paid developers working on Upstart and currently there are no plans to stop development.

There's a difference between Canonical and Google paying devs to work on an init system nobody really wants (and, honestly, how much of the development work is developing new features, and how much is patching), and one accepted in all the distros. I don't know enough about init to say which one is better, but systemd is getting all the momentum. 

@Debian
yeah, stuff hits Experimental on release, but by the time Debian patches stuff to work on a gazillion obscure architectures and deals with the bugs arising from patching...

---

### Post by ranch hand on 2011-09-29
> **el_koraco said:**
> There's a difference between Canonical and Google paying devs to work on an init system nobody really wants (and, honestly, how much of the development work is developing new features, and how much is patching), and one accepted in all the distros. I don't know enough about init to say which one is better, but systemd is getting all the momentum. 

@Debian
yeah, stuff hits Experimental on release, but by the time Debian patches stuff to work on a gazillion obscure architectures and deals with the bugs arising from patching...
You do have a good point.  Debian is very unwilling to release their "stable" release in an unstable condition.

---

### Post by madjr on 2011-09-30
hmm, i dont think systemd is unstable that it cant be tested to possibly be included for 12.04?

both the recent **fedora** and **mandriva** have it already and **opensuse** is getting it for 12.1

i havent had any problems with it, in fact i think is way better than upstart and the **best experience i had**. I love it!

Makes the OS feel like a real OS.

so ubuntu is going to postpone testing for another year?

i say look how it goes and if things dont go well for any reason then ok drop it for that release, else i see no motive not to start.

---

### Post by el_koraco on 2011-09-30
> **madjr said:**
> hmm, i dont think systemd is unstable that it cant be tested to possibly be included for 12.04?


A sizeable portion of the rc scripts has been turned into "native" upstart jobs in Ubuntu. systemd has no compatibility with Upstart, but with sysvinit (even the BSD style rc scripts in Arch, probably Slackware too, although Slack is a world unto itself). That would mean either moving all the jobs back into sysvrc scripts, or coding everything in C. Honestly, Ubuntu is so commited to Upstart, it will probably take them the full 12.04 to 14.04 dev cycle to move to systemd, if they choose to do it at all. 

[QUOTE=ranch hand]You do have a good point.  Debian is very unwilling to release their "stable" release in an unstable condition.     [/QUOTE]

Which is mostly the sane approach, but if you want to go off the beaten track, you may end up not so happy. Say, running a custom X session with xinit and getting ConsoleKit to do the job properly. Also, a lot of the instability is not a result of the software included, but Debian's patching. In general, Debian Stable doesn't offer much more stability than the bleeding edge distros that stick to unmodified code, but it often lacks improvements in technology (sayz me as a happy Squeeze user).

---

### Post by madjr on 2011-09-30
> **el_koraco said:**
> A sizeable portion of the rc scripts has been turned into "native" upstart jobs in Ubuntu. systemd has no compatibility with Upstart, but with sysvinit (even the BSD style rc scripts in Arch, probably Slackware too, although Slack is a world unto itself). That would mean either moving all the jobs back into sysvrc scripts, or coding everything in C. Honestly, Ubuntu is so commited to Upstart, it will probably take them the full 12.04 to 14.04 dev cycle to move to systemd, if they choose to do it at all. 



wow, really, damn that sounds terrible...

i just love systemd, so i hope they start as soon as possible on this. ;/

**crapstart and plybadmouth**, has always made the ubuntu boot and shutdown experience so unpleasant and unpolished.

first impressions matter and this gives the worst first impression...

now, i wonder what ubuntu guys would had done if systemd became a dependency of gnome...

---

### Post by MadMan2k on 2011-09-30
> **madjr said:**
> 
i havent had any problems with it, in fact i think is way better than upstart and the **best experience i had**. I love it!

Makes the OS feel like a real OS.
may I ask how you are using your OS? I mean for typical desktop usage it should not matter whether its upstart or systemd...

---

### Post by madjr on 2011-09-30
> **MadMan2k said:**
> may I ask how you are using your OS? I mean for typical desktop usage it should not matter whether its upstart or systemd...

[http://0pointer.de/blog/projects/why.html](http://0pointer.de/blog/projects/why.html)

systemd offers many things to make for a better experience like **Shell-free bootup**, faster boot up, kills remaining processes, etc.

i have experienced them my self and love them.

gladly this is open source and the old "fail components" can be abandoned in a shorter time frame for ones that have more features and generally work better when they become available.

---

### Post by jbicha on 2011-09-30
madjr, why the hate for Plymouth? It's the standard boot splashscreen.

And upstart was used everywhere until systemd came along a few months ago.

---

### Post by effenberg0x0 on 2011-10-01
Sorry to jump in. Plymouth gets on my nerves. I really would love to see another option on Ubuntu for the pink screen of death / always distorted logo screen. A small "Ubuntu Friends" logo on the top left corner while the user would not be deprived of seeing his own PC boot messages would be great. Or an easy GUI way through which users could choose what to have in their splash screen, including the option of nothing - also great. But the whole idea of hiding system info from the user is so.... windows.

And then there's one of the darkest things one can do today in Ubuntu: see below. 

```

[04:04 AM][al:HOME-OFFICE:~]
$ sudo apt-get remove plymouth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  abiword abiword-plugin-grammar abiword-plugin-mathview accountsservice
  acpi-support acpid aisleriot alsa-base alsa-utils anacron apparmor
  apparmor-utils apport apport-gtk aptdaemon apturl at at-spi avahi-daemon
  avahi-utils backintime-common backintime-gnome banshee
  banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore
  binfmt-support bluez bluez-alsa bluez-cups bluez-gstreamer brasero brltty
  brltty-x11 bsd-mailx buzztard buzztard-data checkbox checkbox-gtk colord
  compiz compiz-gnome compiz-plugins-main compiz-plugins-main-default
  compizconfig-backend-gconf compizconfig-settings-manager computer-janitor
  computer-janitor-gtk console-setup consolekit cron cups
  cups-driver-gutenprint dbus dbus-x11 ddclient dkms dmsetup dnsmasq e2fsprogs
  eject empathy evolution evolution-data-server evolution-exchange
  evolution-plugins evolution-webcal firefox-gnome-support friendly-recovery
  ftp gconf-defaults-service gconf-editor gconf2 gconf2-common geoclue
  geoclue-ubuntu-geoip gir1.2-gconf-2.0 gir1.2-mutter-3.0
  gir1.2-panelapplet-4.0 gksu gnome-applets gnome-applets-data gnome-bluetooth
  gnome-codec-install gnome-color-chooser gnome-control-center
  gnome-disk-utility gnome-keyring gnome-media gnome-media-common gnome-panel
  gnome-panel-bonobo gnome-panel-data gnome-power-manager gnome-search-tool
  gnome-session gnome-session-bin gnome-session-fallback gnome-settings-daemon
  gnome-shell gnome-sudoku gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-themes-standard gnome-time-admin gnome-tweak-tool
  gnome-user-share gnumeric gparted grub-common grub-emu grub-gfxpayload-lists
  grub-pc grub-pc-bin grub2 grub2-common gstreamer-dbus-media-service
  gstreamer0.10-gconf gstreamer0.10-gnomevfs gstreamer0.10-plugins-good-dbg
  gthumb gthumb-data gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse hostname
  hplip hplip-cups ibus ibus-pinyin ibus-table icoutils ifupdown
  indicator-datetime indicator-power indicator-session indicator-sound
  indicator-sound-gtk2 initramfs-tools initscripts irqbalance jockey-common
  jockey-gtk jockey-kde katepart kbd kde-runtime kdebase-runtime kdelibs-bin
  kdelibs5-plugins kdepim-runtime kdepimlibs-kio-plugins kdoctools
  keyboard-configuration kubuntu-debug-installer language-selector-common
  language-selector-gnome lftp libabiword-2.8 libakonadi-contact4
  libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libaudio-scrobbler-perl
  libbonoboui2-0 libbuzztard0 libcamel-1.2-29 libcamel1.2-19 libcanberra-pulse
  libcompizconfig0 libcryptui0 libdevmapper-event1.02.1 libdevmapper1.02.1
  libebackend-1.2-1 libebackend1.2-0 libebook1.2-10 libebook1.2-12
  libecal1.2-10 libecal1.2-8 libedata-book-1.2-11 libedata-book1.2-8
  libedata-cal-1.2-13 libedata-cal1.2-10 libedataserver1.2-14
  libedataserver1.2-15 libedataserverui-3.0-1 libedataserverui1.2-11
  libegroupwise1.2-13 libemail-valid-perl libevolution libfolks-telepathy25
  libfolks25 libgconf2-4 libgconf2.0-cil libgdu0 libgksu2-0
  libgnome-desktop-2-17 libgnome-media-profiles-3.0-0 libgnome-media0
  libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-common
  libgnome2.24-cil libgnomekbd4 libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgoffice-0.8-8 libgtkhtml-editor0
  libgtkhtml3.14-19 libgweather-3-0 libgweather-common libgweather1
  libio-socket-ssl-perl libkabc4 libkatepartinterfaces4 libkcal4 libkcalutils4
  libkde3support4 libkdewebkit5 libkemoticons4 libkfile4 libkhtml5 libkio5
  libkmediaplayer4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4
  libkparts4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4
  libktexteditor4 liblvm2app2.2 liblwp-protocol-https-perl libmailtransport4
  libmetacity-private0 libmicroblog4 libmutter0 libnet-dbus-perl libnss-mdns
  liboobs-1-5 libpanel-applet-4-0 libparse-debcontrol-perl libparted0debian1
  libplasma3 libpolkit-gtk-1-0 libqapt-runtime libqtgconf1 libreoffice-gnome
  librpc-xml-perl libsane libsolid4 libsyncdaemon-1.0-1 libubuntuone-1.0-1
  libubuntuone1.0-cil libunique-1.0-0 libunique-3.0-0 libunity-2d-private0
  libwww-perl libxml-parser-perl libxml-twig-perl libxml-xpath-perl
  light-themes lightdm lintian linux-generic linux-image-2.6.38-11-generic
  linux-image-2.6.38-8-generic linux-image-3.0.0-0300-generic
  linux-image-3.0.0-12-generic linux-image-generic linux-sound-base logrotate
  mdadm media-player-info metacity metacity-common modemmanager
  module-init-tools mountall mutter-common mysql-server mysql-server-5.1
  nautilus nautilus-actions nautilus-sendto nautilus-sendto-empathy
  nautilus-share netbase ntfs-3g ntpdate onboard oneconf openssh-server parted
  pcmciautils pidgin pidgin-libnotify pidgin-otr pitivi
  plasma-scriptengine-javascript plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text
  plymouth-theme-xubuntu-logo plymouth-theme-xubuntu-text pm-utils policykit-1
  policykit-1-gnome postfix powermgmt-base ppp pppconfig pppoeconf pptp-linux
  procps pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 python-aptdaemon
  python-aptdaemon-gtk python-aptdaemon.gtk3widgets
  python-aptdaemon.gtkwidgets python-compizconfig python-gconf python-gnome2
  python-kde4 python-pyatspi python-ubuntuone-control-panel qapt-batch
  quadrapassel rsyslog samba sane-utils screen-resolution-extra seahorse
  sessioninstaller shotwell simple-scan software-center
  software-properties-gtk system-tools-backends telepathy-salut telnet
  thunderbird thunderbird-globalmenu thunderbird-gnome-support tomboy
  totem-mozilla ubuntu-artwork ubuntu-minimal ubuntu-sso-client
  ubuntu-standard ubuntu-system-service ubuntu-wallpapers ubuntuone-client
  ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-gtk
  ubuntuone-couch udev udisks ufw unity unity-2d unity-2d-launcher
  unity-2d-panel unity-2d-places unity-2d-spread unity-common
  unity-lens-applications update-notifier upower upstart ureadahead
  usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data
  util-linux wireless-crda xchat xchat-common xdiagnose xorg xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo xul-ext-ubufox
The following NEW packages will be installed:
  gir1.2-atspi-2.0 gir1.2-wnck-3.0 python-pyatspi2
The following packages will be upgraded:
  evolution-common evolution-data-server-common gnome-orca
  python-ubuntuone-client unity-lens-music
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
5 upgraded, 3 newly installed, 433 to remove and 6 not upgraded.
Need to get 3,318 kB/3,328 kB of archives.
After this operation, 1,274 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] ^C
[04:15 AM][al:HOME-OFFICE:~]
$ 

```

I mean, seriously? Look at that. WTF is that? Nothing should be like that. Nothing IS like that. 

Regards,
Effenberg

---

### Post by lucazade on 2011-10-01
> **effenberg0x0 said:**
> Sorry to jump in. Plymouth gets on my nerves. ..

yes, me too.. but like services managment it doesn't affect my everyday work.
xsplash is still in the repos but I'm not so brave to test it again, anyway it was cool at lucid time.
plymouth is linked to mountall package in order to do fsck at boot time, so that is the problem with deps.
if you want to quickly disable you can use this:
sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disable

---

### Post by effenberg0x0 on 2011-10-01
> **lucazade said:**
> 
sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disable

Hey lucazade,

Sure, I did, a long time ago. The pink/purple thing never really worked  for me: it was always distorted, no logo, weird logo, stuck, etc. 

But what I meant is that the everyday user can kill his PC easily by  following a common logic/procedure. And for something stupid. This is  wrong.

**Potential Average Users **(general concerns)"Gee, I don't like plymouth. My church advise against it."
"plymouth really doesn't go with my tie. I wish it looked more like a blackberry"
"I am a football player! I don't want plymouth / too pink for me"
"1 4m 4 hacker! plym0uth sux! PWN3D!"

**Potential Average Users Solution**
"This is why I use Ubuntu! You can select and use the software you want.  I feel so free as in Beer & Bird right now that I am gonna remove  plymouth! Yey!"
"$sudo apt-get remove plymouth"

[B]Potential Average Users Support Request at the Forum
[/B]"Unity stopped working after latest updates. All I did was run apt-get and now I'm stuck at a black screen"

It's quite dangerous for something that is only supposed to be aesthetically pleasant...

Well, thats IMHO anyway.

Regards,
Effenberg

---

### Post by jbicha on 2011-10-01
So, you disabled Plymouth "a long time ago" because it wasn't good enough. How do you know that it doesn't work now?

I guess it's a good thing you didn't try out upstart in its first year or maybe you'd have similar bad first impressions.

---

### Post by el_koraco on 2011-10-01
> **madjr said:**
> 
**crapstart and plybadmouth**, has always made the ubuntu boot and shutdown experience so unpleasant and unpolished.


What are you talking about? The Plymouth boot screen gets distorted no matter which distro you're on if you install proprietary drivers. It's a thing of pure beauty on KMS drivers. Ubuntu's problem may be in the packaging of Plymouth, which is hardcoded to take down a lot, but that's not a problem in itself. Anyway, Plymouth is being coded into systemd as well, just not quite that hardcore. For now, anyway. 

And what exactly does upstart have to do with the "polish" of booting and shutting down? The stuff on Pottering's list is a compilation of tasks that will make the job easier for system administrators, packagers, developers, and distro maintainers, not necessarily something a typical desktop user will even notice (the same goes for upstart). Singing praises to systemd as something that greatly refines your desktop experience is nonsense, since pretty much the only thing you're interfacing with directly is the systemctl utility, which has a more complicated syntax than rc scripts. 

```
update-rc.d avahi disable
systemctl service avahi.service disable
```Not to mention the handling of network initialization, which adds 15 seconds to Fedora's boot time (without actually starting the network connection, no, we need network manager to work only in the GUI, fsck the other runlevels). Ya know, since we're talking about a "polished boot procedure" and all...

---

### Post by effenberg0x0 on 2011-10-01
> "So, you disabled Plymouth "a long time ago" because it wasn't good enough. How do you know that it doesn't work now?"I install and reinstall Ubuntu some times a day, mostly in VMs. In first boots, prior to customizations, there it is. I can't possibly customize all VMs I create and destroy for testing software.

But it is disabled for a long time in MY PCs and the workstation I spend more time on, laptop, etc. Along with other stuff I don't like, such as grub2 themes, network-manager, etc. Mine are customized the way I like it, of course, which is the beauty of Linux and FOSS. But, I work for a company with many PCs, that does IT services for many other companies, with many other PCs... Although I rarely touch other people PCs (I'm in internal IT development), I work directly with IT service guys. So I still have to have some contact with it anyway. 

> I guess it's a good thing you didn't try out upstart in its first year or maybe you'd have similar bad first impressions.     Nah, you don't know me, you can't say that. I'm very open-minded. But I am targeted at results. plymouth will mature, of course. Hell, it may even get to be 3D and revolutionize the face of the modern boot process in the near-future. But I don't like what it serves for. It's too much complication and risk solely for a quick glimpse on some logo and to hide information that I Do want to see at every boot.  I can imagine it might serve the purposes of PC Vendors, that will want to have their logo there, etc. But it doesn't do me any good. Not now, not if it matures greatly. 

Regards,
Effenberg

---

### Post by ranch hand on 2011-10-01
> **jbicha said:**
> So, you disabled Plymouth "a long time ago" because it wasn't good enough. How do you know that it doesn't work now?

I guess it's a good thing you didn't try out upstart in its first year or maybe you'd have similar bad first impressions.
Ah yes, the good old Ubuntu Member attach mode at any question of Plymouth lovelyness. 

Plymouth is responsible for 3 to 20 minute boot time on my box (see sig).  It will not shut down at all unless I use alt-SysRq-b.  This started at the Release of 10.04, kind of worked at RC time.

If you read other forums folks actually are permitted to bring this up.  So nice that you can't on the official Ubuntu Forums without getting the "it is all wonderful you are just too stupid to use it" song and dance.

Good luck with that in the long run.

---

### Post by lucazade on 2011-10-01
jbicha is allowed to have an opinion like everyone else here.. if he is a member or not it doesn't matter.

What is important is all the effort he put in Ubuntu development, really relevant in Oneiric.

---

### Post by effenberg0x0 on 2011-10-01
> **ranch hand said:**
> Ah yes, the good old Ubuntu Member attach mode at any question of Plymouth lovelyness. 

@Ranch
Yeah... I was under the impression Ubuntu Forums was a different place. I honestly have a lot of fun helping users fix their PCs when I can and there are some very nice folks around here. But honestly, flame war / free aggression mode from some individuals here is starting to **** me off. I guess it's inevitable in any sort of online community. Now I really understand your advice better.

@ Lucazade
Hey man :) Agreed, so does everyone else. The aggressiveness is what is in question here.

Regards,
Effenberg

---

### Post by madjr on 2011-10-01
well the plymouth problem is so bad at the moment that linuxmint developers had to disable it and make the boot screen totally black...

"***The Linux Mint team has decided to remove the plymouth boot screen**. Instead of the animated boot screen, Linux mint will only have a **black screen**. According to the developers, because the speed at which many computers boots, the boot screen animation is not generally visible or **if visible it does not complete the animation giving it an _[COLOR="DarkRed"]unprofessional[/COLOR]_ look.***"

yes, everyone i know always tells me if there is something **wrong** with my computers after seeing the boot screen... (on intel hardware is a little better, but not on log out or shutdown..)

> jbicha is allowed to have an opinion like everyone else here.. if he is a member or not it doesn't matter.

What is important is all the effort he put in Ubuntu development, really relevant in Oneiric. 

jbicha is awesome and we all appreciate his contributions, but unfortunately plymouth is not something that's been helping the image of ubuntu these years... (but i have hopes for the future tho..)

---

### Post by jbicha on 2011-10-01
I'm not advocating for or against plymouth; I'm just saying that everyone uses it...because we believe users would rather have something simple & pretty to look at instead of text scrolling across the screen.

It is interesting that Linux Mint 11 ships with plymouth disabled. (Maybe I'll boot it and see what black looks like.)

---

### Post by effenberg0x0 on 2011-10-02
I hope Ubuntu eventually does the same as Mint. Or, even better, come up with some simpler, less screen-intrusive solution. As I mentioned earlier, something like a small "Circle of Friends" logo in the top-left corner while the system is loading and displaying messages right below would be great (and stylish). It could probably please both audiences (pink no-messages fans and black all-messages fans). Don't know what the best technology for that would be thou.


Regards,
Effenberg

---

### Post by cariboo on 2011-10-02
This thread is wandering pretty far of topic, it's actually ranch hand, that has a bug up his butt concerning Ubuntu ever since his problem with plymouth came up.

BTW plymouth works on my system with nvidia graphics.

Let's continue the discussion about systemd.

---

### Post by BwackNinja on 2011-10-02
Nice (rather large) set of messages discussing systemd:
[http://lists.debian.org/debian-devel/2011/07/msg00269.html](http://lists.debian.org/debian-devel/2011/07/msg00269.html)

Lennart's response in that thread:
[http://lists.debian.org/debian-devel/2011/07/msg00281.html](http://lists.debian.org/debian-devel/2011/07/msg00281.html)

Some major points for those who don't feel like doing hours of reading:
- Migration can be a pain for example:
  - all of /etc/default/* is deprecated (completely unused unless sourced by some script)
  - switching to using systemd service files overrides customized SysV initscripts
  - new tools and new syntax
  - SysV is lighter on resources than systemd (for 99.9999% of users that doesn't even pretend to matter)
  - not everything has been converted to use systemd unit files (not that they necessarily need to)
  - new syntax for starting services is less powerful, however, they are much shorter and do just about everything (and can do everything because you can still call bash scripts, its just frowned upon) as well as it abstracts out the generic part of initscripts
  - for Ubuntu specifically, Upstart to systemd would be an odd migration considering the lack of some SysV scripts to fall back to
  - Upstream or package maintainers need (READ: should) to add systemd unit files for their applications that have SysV scripts or Upstart jobs.
- It has a better connection with Plymouth, showing boot messages better, etc
- systemd is Linux-specific, it makes use of special Linux-only features which is a problem for portability (Lennart is vehemently against portability for systemd, suggesting instead another implementation based on shared interfaces for other platforms like FreeBSD)
- systemd is attempting to replace ConsoleKit (does parts already, still far in the future)
  - systemd handles multiseat far better
  - systemd cleans up ended user sessions based on cgroups
- Well documented
- Can also replace inet.d

BFS (-ck patches):
- I haven't seen this question answered well anywhere. I haven't tried it myself (I will in the next few weeks probably) but from what I've read concerning how these different parts interact, yes, you can still use systemd. BFS does not take cgroups into account during scheduling, unlike the default scheduler. You still need to build the kernel with cgroups support to be able to use basically all the useful things that systemd allows you to do that aren't directly related to booting. You wouldn't be able to look at any useful status of a service, kill services (especially groups), and may not be able to shutdown properly without cgroups.

Opinion stuff:
- First of all the annoying pattern, people try to make Lennart seem to be a bad guy. This happened a lot when pulseaudio became the mainstream thing. This has legitimate origins in things that make people angry like avoiding portability and not taking anyone who's trying to run systemd in a non-supported configuration (like without cgroups). Also, people should know that to make things better, things break (especially those in this forum should know this well already). Mostly I see long discussions full of people ignorant to the workings of systemd acting like experts and complaining about what is actually a gross oversimplification of pulseaudio/systemd.
- systemd is going the way that pulseaudio went. There will be some pain, but the end result is worth it. Its not just that its different, its better, period, and all we have now is to wait until we decide its worth the pain to move to it. People saw from pulseaudio all the was only on the surface: networked audio, and another layer above the soundcard. Now, if we look deeper, we'll see proper support for multichannel sound with upmixing and downmixing that actually makes sense, passthrough support that's easy to use, support for non-static configurations and migration between audio devices, etc. systemd is more than just a faster boot. It is proper multiseat, proper babysitting of processes, better service dependency resolution, simplified configuration of daemons (actually human-readable, yay), useful (even some graphical) tools for looking at the status of services, etc.


Back Offtopic:
Everyone knows that you can disable the splash of plymouth by removing "splash" from your kernel line (or just press esc and you'll go to text), right? Plymouth is more than just a splash screen, and that's why Ubuntu, among other distributions depend on it. For example, it handles the password prompt for decryption of partitions in both the graphical and text case.

---

### Post by el_koraco on 2011-10-02
> **madjr said:**
> well the plymouth problem is so bad at the moment that linuxmint developers had to disable it and make the boot screen totally black...

"***The Linux Mint team has decided to remove the plymouth boot screen**. Instead of the animated boot screen, Linux mint will only have a **black screen**. According to the developers, because the speed at which many computers boots, the boot screen animation is not generally visible or **if visible it does not complete the animation giving it an _[COLOR=DarkRed]unprofessional[/COLOR]_ look.***"



Hold on there sonny boy. Mint's decision to boot with a black screen has little to do with anything but aesthetics. In your post you clearly praised systemd and spit fire on "crapstart", ignorantly tying it to Plymouth, and your big argument is Mint and "everybody you know".  Actually, I find it hard to see why you're even bringing Plymouth into the game apart from an apparent desire to engage in a discussion you can't really participate in based on a knowledge of stuff. 

In your case, i'll quote the ninja: "Mostly I see long discussions full of people ignorant to the workings of systemd acting like experts"

---

### Post by madjr on 2011-10-02
> **el_koraco said:**
> 

In your case, i'll quote the ninja: "Mostly I see long discussions full of people ignorant to the workings of systemd acting like experts"

if we're going into the quote game now, let me bring in another quote:

*"systemd is going the way that pulseaudio went. There will be some pain, but the end result is worth it. **Its not just that its different, _its better_, period**..."*.

I never said or presumed i was am an expert (i just stated my OPINION that systemd was better, and it looks like am right), and am willing to become clear on all the confusion surrounding this topic (which am not the only one), but still from what i have already read so far, am defending systemd over upstart, specially in the long run.

also i dont see why you want to **force others to stop participating** on a dumb and generic thread about systemd.. or on any other thread. **You dont have the right** to do that, as you're just acting like an... and I wasnt the one that got this offtopic. **The OP just asked for "a package"** and everyone else started pulling it their way.

And if we're really "*going to go back to topic*", then i dont see anything else to discuss here. I believe this thread is already a candidate to be marked as **solved** and/or if the mods want, even closed.

---

### Post by el_koraco on 2011-10-02
Sorry, but calling the product of a lot of hard work "crapstart" without any sort of arguments is arrogant and insulting. It's not like anyone forced you to do that.

---

### Post by madjr on 2011-10-02
> **el_koraco said:**
> Sorry, but calling the product of a lot of hard work "crapstart" without any sort of arguments is arrogant and insulting. It's not like anyone forced you to do that.

well am sorry about that, i know lots of work went on there, but i dont think at this point focusing too much effort into it is a good idea.

---

### Post by sgage on 2011-10-02
> **el_koraco said:**
> Sorry, but calling the product of a lot of hard work "crapstart" without any sort of arguments is arrogant and insulting. It's not like anyone forced you to do that.

Telling somebody to "hold on there sonny boy" is rather on the insulting side, as well.

---

### Post by madjr on 2011-10-02
we need to look at this way:

**Wayland, Btrfs and systemd** (and things like gnome3 and unity) may be at their initial years (infancy), but they will be the substitutes of the technology that we have today and that has served many of us pretty well.

But those technologies are pretty much at their limit right now, so we need to accept it and embrace the idea for the better...

yes, change brings chaos, confusion and lots of discussion, but is better to be done sooner than later.

---

### Post by BwackNinja on 2011-10-02
You realize that in Lennart's original post announcing systemd, he gave as much praise to upstart, both as an init daemon and simply as a project, as one could while still saying that it is fundamentally flawed and not something that he could just extend to get the necessary functionality.

Upstart isn't just another crappy init daemon that isn't systemd, upstart is _GOOD_. That's why it'll be a while until Ubuntu drops it (if they do). Now upstart is trying to keep up, its author (Scott James Remnant) read and responded positively to the announcement of systemd and said that he'd try to address the issues Lennart raised about upstart. (link: [http://netsplit.com/2010/04/30/on-systemd/](http://netsplit.com/2010/04/30/on-systemd/) )

---

### Post by madjr on 2011-10-02
> **BwackNinja said:**
> You realize that in Lennart's original post announcing systemd, he gave as much praise to upstart, both as an init daemon and simply as a project, as one could while still saying that it is fundamentally flawed and not something that he could just extend to get the necessary functionality.

Upstart isn't just another crappy init daemon that isn't systemd, upstart is _GOOD_. That's why it'll be a while until Ubuntu drops it (if they do). Now upstart is trying to keep up, its author (Scott James Remnant) read and responded positively to the announcement of systemd and said that he'd try to address the issues Lennart raised about upstart. (link: [http://netsplit.com/2010/04/30/on-systemd/](http://netsplit.com/2010/04/30/on-systemd/) )

um, the article is over a year old (when sd was not used on any distro), it could be that he may had changed his mind about some things now...

would love to see a new update article from him.

---

### Post by MacUntu on 2011-10-02
So, bottom line: there is no systemd for Oneiric, right?

---

### Post by BwackNinja on 2011-10-02
> **madjr said:**
> um, the article is over a year old (when sd was not used on any distro), it could be that he may had changed his mind about some things now...

would love to see a new update article from him.

Well, part of the point of that is that it was an immediate respons to the initial post on systemd.

I've looked, and its hard to find anything that specifically says anything about addressing the vague issues with upstart. That said, I think a lot of functionality of upstart is being neglected by just about everyone who isn't Ubuntu because no one really uses upstart jobs. That in itself is an issue because it involves migration from SysV scripts into a format that is still bash and doesn't have the benefits of being short and sweet like systemd's unit files do. systemd's unit files are being committed to the various upstreams, while I'm pretty sure upstart's aren't.

Now I actually see that upstart is well documented, for example: [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html) but systemd is being pushed harder upstream, as well as its less of a maintainence burden to ship systemd units than upstart jobs, so its harder now to push upstart jobs upstream.

---

### Post by BwackNinja on 2011-10-02
> **MacUntu said:**
> So, bottom line: there is no systemd for Oneiric, right?

I'd say just use the debian packages. There's an active systemd maintainer for debian who also shows up a lot in the mailing lists. I suspect that those packages should work fine. I wouldn't expect to see them in Ubuntu, if for no other reason than you shouldn't be changing your init daemon anyway and to have systemd in the archives means that it needs to at least be partially accomodated and ensured to boot up properly (which is a waste of testing unless the order is given to switch to systemd).

---

### Post by MacUntu on 2011-10-02
Hm, last time I tried that package was in Natty:

[http://ubuntuforums.org/showpost.php?p=9977403&postcount=28](http://ubuntuforums.org/showpost.php?p=9977403&postcount=28)

Maybe I'll give it a shot tomorrow. :-)

---

### Post by ikt on 2011-10-02
> **madjr said:**
> yes, change brings chaos, confusion and lots of discussion, but is better to be done sooner than later.

I think having programs which are fairly new yet not widely tested is a major bugbear with ubuntu, MS has said himself that even software which is fairly well tested, the moment you put it in front of several million people issues come up that weren't seen before.

Did you notice the absurd amount of fire the forums had when 11.04 was released in the state it was? Were you there when 8.04 was released with a beta firefox and a pulse audio that was only recently released?

There are two distinct edges, 

[IMG]http://blend.gatewaycc.edu/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/webteam/bell2.gif[/IMG]

While Debian sits on conservative borderline laggard, Ubuntu can more than safely sit with the pragmatics,(occasionally branching out from the early adopters) and being that the LTS releases are the most popular releases of Ubuntu and the most used, I don't see why aiming to have every release be on par with an LTS release is not worth aiming for. (and that doesn't include having major components dropped at the first sign of something potentially better, this is what I believe separates Ubuntu from fedora).

---

### Post by nothingspecial on 2011-10-02
I'll let cariboo907 reopen this if he feels further debate is of any value.

For now, closed.

---

### Post by cariboo on 2011-10-02
Re-opened, as I feel discussion about systemd, as we will have to deal with it eventually, is interesting.

---

### Post by madjr on 2011-10-03
> **ikt said:**
> I think having programs which are fairly new yet not widely tested is a major bugbear with ubuntu, MS has said himself that even software which is fairly well tested, the moment you put it in front of several million people issues come up that weren't seen before.

Did you notice the absurd amount of fire the forums had when 11.04 was released in the state it was? Were you there when 8.04 was released with a beta firefox and a pulse audio that was only recently released?



lol , yes, i was there and i still have nightmares of it


> 
There are two distinct edges, 

[IMG]http://blend.gatewaycc.edu/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/webteam/bell2.gif[/IMG]

While Debian sits on conservative borderline laggard, Ubuntu can more than safely sit with the pragmatics,(occasionally branching out from the early adopters) and being that the LTS releases are the most popular releases of Ubuntu and the most used, I don't see why aiming to have every release be on par with an LTS release is not worth aiming for. (and that doesn't include having major components dropped at the first sign of something potentially better, this is what I believe separates Ubuntu from fedora).

i never said they need to include unfinished stuff on an LTS release (that's un-mature and irresponsible).

Am referring to that they need to start testing early (maybe create a separate branch just for that).

in fact i would like to see ubuntu start discussions of a [better release and testing cycle]("http://netsplit.com/2011/09/08/new-ubuntu-release-process/") that would work for their developers and their audience at the next UDS...

---

### Post by el_koraco on 2011-10-03
> **madjr said:**
> well am sorry about that, i know lots of work went on there, but i dont think at this point focusing too much effort into it is a good idea.

I can agree with that. Hearing SJR and Pottering talk about the systems, you get the impression they both have their advantages, but hedging your bets on maintaining an init system whose author no longer works for you is a little bit on the wild side. It seems easier to let Red Hat do the work and lay back, like all distros are preparing to do.

---

### Post by BwackNinja on 2011-10-03
So... beyond potentially not working while it gets set up for Ubuntu, how much would switching actually affect any user?

- I've edited some /etc/default/* files
- I've edited the /etc/init.d/lircd file back a few releases ago

What has anyone done, if anything that would change if the switch was made to systemd?

---

### Post by el_koraco on 2011-10-04
> **BwackNinja said:**
> So... beyond potentially not working while it gets set up for Ubuntu, how much would switching actually affect any user?


Unless people are running their own upstart scripts, probably not a lot. If Canonical would port all the native upstart jobs to systemd, or revert them back to sysvinit scripts, desktop users would hardly feel the difference. Maybe the server users might have a tougher time, since I suspect a lot of them have customized upstart jobs, scripts and stuff.

---

