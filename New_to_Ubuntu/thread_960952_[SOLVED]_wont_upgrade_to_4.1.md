---
title: "[SOLVED] wont upgrade to 4.1"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-10-27
have the 4.0 desktop enviroment on top of ubuntu install.  my update wont upgrade to 4.1 and on top of that my menu bar is gone what is going on?

---

### Post by Xiong Chiamiov on 2008-10-28
4.0 of ... oh, KDE.  Your problems are most likely due to the fact that, well, KDE 4.0 was a beta, and full of bugs.  Good news is, 4.1 is actually mostly usable, if we can get you updated to it.

When you say that it "won't upgrade", what do you mean?  How are you trying to update?  What is happening when you do?

---

### Post by PatrickMoore on 2008-10-28
through synaptec, ultimately its downloading the update and then  is saying a file is corrupt and cancelling installation yes kde. i'm losing faith in my experment. i wanted to try a new gui and it seems gnome is the only stable and aesthetically pleasing one

---

### Post by PatrickMoore on 2008-10-28
when i click on my update manager and elect a partial upgrade i am getting this error

```
Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.
```
```
amor-kde4
ark-kde4
blinken-kde4
bovo-kde4
dolphin-kde4
gtk-qt-engine
gwenview-kde4
juk-kde4
kalgebra-kde4
kalzium-data-kde4
kalzium-kde4
kamera-kde4
kanagram-kde4
kappfinder-kde4
katomic-kde4
kbattleship-kde4
kblackbox-kde4
kblocks-kde4
kbounce-kde4
kbreakout-kde4
kbruch-kde4
kcalc-kde4
kcharselect-kde4
kcolorchooser-kde4
kcron-kde4
kde-window-manager
kdeaccessibility-kde4
kdeadmin-kde4
kdeartwork-emoticons-kde4
kdeartwork-kde4
kdeartwork-misc-kde4
kdeartwork-style-kde4
kdeartwork-theme-icon-kde4
kdeartwork-theme-window-kde4
kdebase-bin-kde4
kdebase-data-kde4
kdebase-kde4
kdebase-plasma-kde4
kdebase-workspace
kdebase-workspace-bin
kdebase-workspace-data
kdebase-workspace-libs4+5
kdegames-card-data-kde4
kdegames-kde4
kdegames-mahjongg-data-kde4
kdegraphics-kde4
kdemultimedia-kde4
kdemultimedia-kio-plugins-kde4
kdenetwork-kde4
kdepasswd-kde4
kdepimlibs-data
kdepimlibs5
kdessh-kde4
kdetoys-kde4
kdeutils-kde4
kdewallpapers-kde4
kdf-kde4
kdiamond-kde4
kdm-kde4
kfind-kde4
kfloppy-kde4
kfourinline-kde4
kgamma-kde4
kgeography-data-kde4
kgeography-kde4
kget-kde4
kgoldrunner-kde4
kgpg-kde4
khangman-kde4
kig-kde4
kiriki-kde4
kiten-kde4
kjots-kde4
kjumpingcube-kde4
klettres-data-kde4
klettres-kde4
klines-kde4
klipper-kde4
kmahjongg-kde4
kmines-kde4
kmix-kde4
kmplot-kde4
knetwalk-kde4
knetworkconf-kde4
knewsticker-kde4
kolf-kde4
kollision-kde4
kolourpaint4-kde4
konqueror-kde4
konqueror-nsplugins-kde4
konquest-kde4
konsole-kde4
kopete-kde4
kpackage-kde4
kpat-kde4
kpercentage-kde4
kppp-kde4
krdc-kde4
kreversi-kde4
krfb-kde4
kruler-kde4
ksame-kde4
kscd-kde4
kscreensaver-kde4
kshisen-kde4
ksirk-kde4
ksnapshot-kde4
kspaceduel-kde4
ksquares-kde4
kstars-kde4
ksudoku-kde4
ksysguard-kde4
ksysguardd-kde4
ksystemlog-kde4
kteatime-kde4
ktimer-kde4
ktouch-kde4
ktuberling-kde4
kturtle-kde4
ktux-kde4
kubrick-kde4
kuser-kde4
kwalletmanager-kde4
kweather-kde4
kwin-kde4
kwordquiz-kde4
kwrite-kde4
libakonadiprivate1
libkcddb4-kde4
libkdecorations4
libkdeedu4-kde4
libkdegames4-kde4
libkdepim4-kde4
libkipi5
libkiten4-kde4
libkonq5
libkonq5-templates
libkrosspython0
libkrossruby0
libksane0
libkwineffects1
libmarble4-kde4
libokularcore1-kde4
libplasma2
libpoppler-qt2
libpoppler-qt4-3
libqimageblitz4
libqt4-help
libqt4-webkit
libqt4-xmlpatterns
libsbigudrv0
lskat-kde4
marble-data-kde4
marble-kde4
okular-kde4
parley-data-kde4
parley-kde4
python-qt4
python-qt4-common
python-qt4-dbus
python-sip4
step-kde4
superkaramba-kde4
sweeper-kde4
systemsettings-kde4
```

im not sure how to fix this or find the broken files to resolve the dependancy issue

---

### Post by PatrickMoore on 2008-10-28
some progress updated to 4.1 by manual upgrade via terminal however my task bar is gone. i cant recover it and im getting frustrated

---

### Post by PatrickMoore on 2008-10-28
i rebuilt it

---

### Post by SunnyRabbiera on 2008-10-28
did you try the [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/) repository?

---

### Post by PatrickMoore on 2008-10-28
> **SunnyRabbiera said:**
> did you try the [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/) repository?

i modified my repositories and it finally worked i think i pasted a little too much

---

