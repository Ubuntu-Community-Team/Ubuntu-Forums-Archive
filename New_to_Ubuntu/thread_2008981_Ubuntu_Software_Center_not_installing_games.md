---
title: "Ubuntu Software Center not installing games"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by enroxorz on 2012-06-23
Hello All,

I have been experiencing issues with some of the Humble Bundle games that I got. 

When I try to install some of them I get the error below (the games I am having an issue with are also there).

Thanks in advance

=====================================================

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The folloowing packages have unmet dependencies:

swordandsworcery: Depends: swordandsworcery-bin (= 1.56-0ubuntu2) but it is a virtual package

The following packages have unmet dependencies:

limbo: Depends: limbo-bin (= 1.0-0ubuntu4) but it is a virtual package

The following packages have unmet dependencies:

lonesurvivor: Depends: lonesurvivor-bin (= 1.11d-0ubuntu2) but it is a virtual package

The following packages have unmet dependencies:

psychonauts: Depends: psychonauts-bin (>= 1.2) but it is a virtual package

---

### Post by drpjkurian on 2012-06-24
how did you install it.
You may get this issue if you use aptitude instead of apt-get.
Hope this will help you. This is my presumption...

---

### Post by Fernhill Linux Project on 2012-06-24
How are you trying to install the games?

I purchased the Humble Bundle V and clicking the link on the email they send takes you to the download page. There is a big orange button 'Download For Ubuntu' after clicking that Software Centre opens, next I clicked install and logged in to my launchpad account as prompted, then the game installed without problem.

---

### Post by Jack Vermicelli on 2012-09-20
Resurrecting this thread because I have the same problem.

In Software Center, each game from my Humble Bundle showed "Not Found," with or without a star rating- see image. 

[http://i.imgur.com/GkUyX.png](http://i.imgur.com/GkUyX.png)

After fiddling for some time, I can see each one in my Software Center now, but each results in unresolved dependencies. In the "details" for each, I see something like the following:

```
spacepiratesandzombies: Depends: spacepiratesandzombies-bin but it is a
virtual package
```

If I in Software Center go to File>Reinstall Previous Purchases, attempting to "re-install" one of the titles from there tells me that I need to check my internet connection a few times, and then gives me the following message- see image.

[http://i.imgur.com/un1YC.png](http://i.imgur.com/un1YC.png)


Attempting to install this dependency through apt-get led me through the following, which I aborted for obvious reasons.

```


[LIST=1]
[*]aj@ajs-dt:~$ sudo apt-get install torchlight-bin
[*][sudo] password for aj:
[*]Reading package lists... Done
[*]Building dependency tree
[*]Reading state information... Done
[*]Some packages could not be installed. This may mean that you have
[*]requested an impossible situation or if you are using the unstable
[*]distribution that some required packages have not yet been created
[*]or been moved out of Incoming.
[*]The following information may help to resolve the situation:
[*]The following packages have unmet dependencies:
[*] torchlight-bin:i386 : Depends: libxmu6:i386 but it is not going to be installed
[*]E: Unable to correct problems, you have held broken packages.
[*]aj@ajs-dt:~$ ^C
[*]aj@ajs-dt:~$ sudo apt-get install libxmu6:i386
[*]Reading package lists... Done
[*]Building dependency tree
[*]Reading state information... Done
[*]The following packages were automatically installed and are no longer required:
[*]  libjaxp1.3-java libxerces2-java libtextcat-data libhyphen0 lightdm
[*]  ttf-sil-gentium libhsqldb-java libalut0 uno-libs3 libneon27-gnutls
[*]  libservlet2.5-java ttf-sil-gentium-basic libtextcat0 ure xfonts-mathml
[*]  libmythes-1.2-0
[*]Use 'apt-get autoremove' to remove them.
[*]The following packages will be REMOVED:
[*]  acpi-support amnesia brltty-x11 gimp gnome-settings-daemon gvfs
[*]  gvfs-backends gvfs-bin gvfs-fuse libgnomekbd7 libgtkglext1
[*]  libgtkglextmm-x11-1.2-0 liblightdm-gobject-1-0 libreoffice libreoffice-base
[*]  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
[*]  libreoffice-draw libreoffice-emailmerge libreoffice-filter-mobiledev
[*]  libreoffice-impress libreoffice-java-common libreoffice-math
[*]  libreoffice-report-builder-bin libreoffice-style-human libreoffice-writer
[*]  libxaw7 libxklavier16 libxmu6 lightdm-gtk-greeter nautilus nautilus-sendto
[*]  nvidia-173 nvidia-current python-uno screensaver-default-images
[*]  unity-greeter vbam-gtk virtualbox virtualbox-dkms virtualbox-qt x11-apps
[*]  x11-session-utils x11-utils x11-xkb-utils x11-xserver-utils xfce4-session
[*]  xfce4-settings xfce4-utils xorg xscreensaver xscreensaver-data
[*]  xscreensaver-gl xserver-common xserver-xorg xserver-xorg-core
[*]  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
[*]  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
[*]  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
[*]  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
[*]  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128
[*]  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
[*]  xserver-xorg-video-neomagic xserver-xorg-video-nouveau
[*]  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
[*]  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
[*]  xserver-xorg-video-s3virge xserver-xorg-video-savage
[*]  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
[*]  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
[*]  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware
[*]  xserver-xorg-video-voodoo xterm xubuntu-default-settings
[*]The following NEW packages will be installed:
[*]  libxmu6:i386
[*]0 upgraded, 1 newly installed, 96 to remove and 0 not upgraded.
[*]Need to get 52.3 kB of archives.
[*]After this operation, 3,070 MB disk space will be freed.
[*]Do you want to continue [Y/n]? n
[*]Abort.
[*]aj@ajs-dt:~$
[/LIST]
 
```If anyone can shed some light on this, I'd be grateful. I imagine I could probably go with another installation route, editing the xfce menu isn't within my knowledge,a nd I understand that it's a pain. Thanks.

---

### Post by fslezak on 2012-09-21
Yipe!

Uninstall a lot for a game?

Let's see...

Try to update and upgrade.

```
sudo apt-get update && sudo apt-get upgrade
```

If you are still getting the error message, please respond if there is a Windows version.

---

