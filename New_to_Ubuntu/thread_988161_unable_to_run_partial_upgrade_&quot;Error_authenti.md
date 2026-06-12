---
title: "unable to run partial upgrade &quot;Error authenticating some packages&quot;"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by wess126 on 2008-11-20
Dear Friends,

I am running Ubuntu 8.04 on a dell precision 690 machine.

My problems started when I upgraded from ubuntu 7.10 to 8.04 using the upgrade manager. Once the upgrade was complete I had major problems with my graphics card and some other hardware. I have recently fixed this with the help of our system admin. However I still have trouble installing some updates.

When I launch update manager I am told that not all updates could be installed. I have a suspicion that their was an incomplete upgrade from 7.10 to 8.04. When I run the partial upgrade (to complete things) I get an error. See attached screen shot, with authentication problems. Below is a list of the packages which could not be authenticated. My systems administrator suggested that I should backup and do a clean install. I would very much like to avoid doing this and hopefully fix the installation by completing the upgrade. 

Has anyone had a similar problem or does anyone have a solution other than  clean re-install?

Many thanks for your help
Wesley

_**Package list**_
alacarte
base-files
bind9-host
compiz
compiz-core
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
dbus
dnsutils
evolution
evolution-common
evolution-data-server
evolution-data-server-common
evolution-exchange
evolution-plugins
f-spot
foo2zjs
friendly-recovery
g++
g++-4.2
gedit
gedit-common
gnome-cards-data
gnome-games
gnome-games-data
gnome-panel
gnome-panel-data
gtk2-engines-murrine
gvfs-fuse
hal
hal-info
initramfs-tools
jockey-common
jockey-gtk
language-support-writing-en
libbind9-30
libdbus-1-3
libdns35
libgdata-google1.2-1
libgdata1.2-1
libgtk-vnc-1.0-0
libisc35
libisccc30
libisccfg30
libntfs-3g23
libpolkit-gnome0
libsmbclient
libsmbios1
libstdc++6-4.2-dev
libtotem-plparser10
linux-generic
linux-headers-generic
linux-image-generic
linux-restricted-modules-generic
logrotate
module-init-tools
ntfs-3g
openoffice.org
openoffice.org-base
openoffice.org-base-core
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-evolution
openoffice.org-filter-binfilter
openoffice.org-filter-mobiledev
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-help-en-gb
openoffice.org-help-en-us
openoffice.org-impress
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-math
openoffice.org-officebean
openoffice.org-style-human
openoffice.org-writer
openoffice.org-writer2latex
pm-utils
policykit-gnome
python-apt
python-qt4
python-qt4-common
python-uno
r-base
r-base-core
r-base-core-dbg
r-base-dev
r-cran-rpart
r-recommended
rhythmbox
samba-common
seahorse
smbclient
tomboy
transmission-common
transmission-gtk
ufw
update-notifier
update-notifier-common
winbind
xserver-xorg
xserver-xorg-input-all
xserver-xorg-video-all
xserver-xorg-video-amd
xserver-xorg-video-cirrus
xserver-xorg-video-geode
xserver-xorg-video-intel
xserver-xorg-video-nsc

---

### Post by ohzopants on 2008-11-20
I would take a look at my sources.list file in /etc/apt/ (I'm pretty sure that's the right path, but I'm at work on a windows pc so I can't double check).

At the end of each line it should say "hardy" for 8.04.  If it still says "gutsy" then apt is still using the gutsy repos.  You could try changing all the "gutsy"s for "hardy"s and then run:

```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by ohzopants on 2008-11-20
Just a clarification: usually this step is done for you automatically during the upgrade process but I guess it's possible that it did not do it correctly.

Hope this helps.

---

### Post by philinux on 2008-11-20
If it's done a partial a better way would be open synaptic.
System>admin>synaptic package manager.

Click the Reload button. After it's done that click on the custom filters button bottom left.
Then click the Upgradable Upstream. Then click mark all upgrades. Then apply. At this point it will probably say certain packages need t be removed. Just check the list. It probably wants to remove older versions of stuff. This is usually normal after a partial upgrade.

---

### Post by wess126 on 2008-11-21
you guys rock, thanks to philinux. I used the synaptic approach and it worked a treat. How do I formally thank you?

---

### Post by rob2uk on 2009-05-08
> **philinux said:**
> If it's done a partial a better way would be open synaptic.
System>admin>synaptic package manager.

Click the Reload button. After it's done that click on the custom filters button bottom left.
Then click the Upgradable Upstream. Then click mark all upgrades. Then apply. At this point it will probably say certain packages need t be removed. Just check the list. It probably wants to remove older versions of stuff. This is usually normal after a partial upgrade.

I hate exaggerating, so I won't say that this post saved my life.

However, it *did* just save my PC's life - I was getting to the point of launching it from the window (now **there** is a word I don't use as often as I used to!)

Thanks again!

---

### Post by Paul86fxr on 2010-05-04
Excellent Philinux this should be a sticky for the lucid upgrade, thanks again

---

