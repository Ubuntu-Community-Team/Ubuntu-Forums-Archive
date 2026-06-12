---
title: "Two dead pc and one brain."
date: 2017-05-02
forum: New to Ubuntu
---

### Post by ickda on 2017-05-02
My old pc has been broken for over a year. She was ubuntu, I broke her apart, I remade her to my needs. It took much work and efert to do this but I did. Sadly overheating and gaming brought her to her knees. I kept her remains in the hope of repair. 
 A few years later, about a week ago my friend gave me a much better pc. A sluggish thing with windows 7 and no way to the boot menu. Broken laptop screen and one odd graphics chip leaves me rather limited. Then two nights ago and the hard drive died.
 after much wasted time, I cannibalized my ubuntu for her brain. I stuck her in and found that all of my drivers where still working my pc to a hundred percent. I updated everything, moving from 14 trusty to this. It is X something or other. 
 Though she is a little buggy, The new body needs a tweak to the software
[ATTACH=CONFIG]274923[/ATTACH][ATTACH=CONFIG]274924[/ATTACH][ATTACH=CONFIG]274925[/ATTACH].

---

### Post by wildmanne39 on 2017-05-02
Hello and welcome to the forum, this thread is in the wrong section but for me to know where to move it I need to know is this going to be a support question or are you just posting about what you have done?

---

### Post by ickda on 2017-05-02
I need help, Like I said she is buggy as hell. I even posted a error message. I get it at after login.
  Also Hi and thanks for the time.

---

### Post by wildmanne39 on 2017-05-02
Moved to New to Ubuntu.

---

### Post by ickda on 2017-05-02
But i ant new. It is just buggy.

---

### Post by wildmanne39 on 2017-05-02
Your thread is okay here, it will get the same attention it would in general help.

---

### Post by ickda on 2017-05-02
Well thenks anyway, as long as my baby gets the help she needs, that is all that matters.

---

### Post by Autodave on 2017-05-02
OK.....let's get some more info. I don't know if I can help you, but let's try and get some one who can some more info to start. What are the specs on this machine? Laptop or desktop? When does this error message appear?

---

### Post by ickda on 2017-05-02
Soon after the update. Before I did that, I had other odd issues that where resolved. At this point my lack of skill is preventing me from further fixing the issue.
[http://www.samsung.com/us/computer/pcs/NP300E5A-A02UB-specs](http://www.samsung.com/us/computer/pcs/NP300E5A-A02UB-specs).
 If you need information on ubuntu, I will need a consul command to get for I am forgetful.

I also worry that i may have old software that I do not need taking up space, if I can get any help with that, then I would be grateful. Though that is secondary to my concerns.

Nothing? I could realy use the help.

---

### Post by QIII on 2017-05-02
Please be patient.  We realize you could use the help -- that is the purpose of a support forum.

Understand that the community is volunteer-based.  We all have real lives.  We have jobs, families, hobbies.  We eat meals, go to movies, get involved in our hobbies.  Sometimes we try to sleep.

We are scattered all over the globe, so we are not always available when any particular user is having difficulty.

Please do not bump your thread any more often than about 12 hours.

---

### Post by ickda on 2017-05-02
No problem. I thought 4 hours was long enuff, thanks for up dating my entiqet.

---

### Post by #&amp;thj^% on 2017-05-02
From your screenshot you are most certainly running very outdated software IE: mate-panel 1.12
Not sure i can help here also...looks a mess
What dose this return from the terminal:
```
apt --installed list | grep 'automatic'
```

also this one:
```
apropos "" | grep "(1)"
```

This may provide some useful information that we can use to help you.
Please use code tags to wrap the return from the terminal.

---

### Post by ickda on 2017-05-02
```
alled,automatic]
libwinpr-handle0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-heap0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-input0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-interlocked0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-library0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-path0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-pool0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-registry0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-rpc0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-sspi0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-synch0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-sysinfo0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-thread0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwinpr-utils0.1/xenial,now 1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1 i386 [installed,automatic]
libwmf0.2-7/xenial,now 0.2.8.4-10.5ubuntu1 i386 [installed,automatic]
libwnck-3-0/xenial,now 3.14.1-2 i386 [installed,automatic]
libwnck-3-common/xenial,now 3.14.1-2 all [installed,automatic]
libwnck-common/xenial-updates,now 1:2.30.7-5ubuntu1.1 all [installed,automatic]
libwnck22/xenial-updates,now 1:2.30.7-5ubuntu1.1 i386 [installed,automatic]
libwpd-0.10-10/xenial,now 0.10.1-1ubuntu1 i386 [installed,automatic]
libwpg-0.3-3/xenial,now 0.3.1-1ubuntu1 i386 [installed,automatic]
libwps-0.4-4/xenial,now 0.4.3-1ubuntu1 i386 [installed,automatic]
libwrap0/xenial,now 7.6.q-25 i386 [installed,automatic]
libwww-perl/xenial,now 6.15-1 all [installed,automatic]
libwww-robotrules-perl/xenial,now 6.01-1 all [installed,automatic]
libwxbase3.0-0v5/xenial-updates,now 3.0.2+dfsg-1.3ubuntu0.1 i386 [installed,automatic]
libwxgtk3.0-0v5/xenial-updates,now 3.0.2+dfsg-1.3ubuntu0.1 i386 [installed,automatic]
libx11-xcb1/xenial,now 2:1.6.3-1ubuntu2 i386 [installed,automatic]
libx264-148/xenial,now 2:0.148.2643+git5c65704-1 i386 [installed,automatic]
libx265-79/xenial,now 1.9-3 i386 [installed,automatic]
libx86-1/xenial,now 1.1+ds1-10 i386 [installed,automatic]
libxapian-1.3-5/xenial,now 1.3.4-0ubuntu6 i386 [installed,automatic]
libxapian22v5/xenial,now 1.2.22-2 i386 [installed,automatic]
libxatracker2/xenial-updates,now 12.0.6-0ubuntu0.16.04.1 i386 [installed,automatic]
libxaw7/xenial,now 2:1.0.13-1 i386 [installed,automatic]
libxcb-composite0/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-dri2-0/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-dri3-0/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-glx0/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-icccm4/xenial,now 0.4.1-1ubuntu1 i386 [installed,automatic]
libxcb-image0/xenial,now 0.4.0-1build1 i386 [installed,automatic]
libxcb-keysyms1/xenial,now 0.4.0-1 i386 [installed,automatic]
libxcb-present0/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-randr0/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-render-util0/xenial,now 0.3.9-1 i386 [installed,automatic]
libxcb-render0/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-shape0/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-shm0/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-sync1/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-util1/xenial,now 0.4.0-0ubuntu3 i386 [installed,automatic]
libxcb-xfixes0/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-xkb1/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcb-xv0/xenial,now 1.11.1-1ubuntu1 i386 [installed,automatic]
libxcomposite1/xenial,now 1:0.4.4-1 i386 [installed,automatic]
libxcursor1/xenial,now 1:1.1.14-1 i386 [installed,automatic]
libxdamage1/xenial,now 1:1.1.4-2 i386 [installed,automatic]
libxfixes3/xenial,now 1:5.0.1-2 i386 [installed,automatic]
libxfont1/xenial,now 1:1.5.1-1 i386 [installed,automatic]
libxft2/xenial,now 2.3.2-1 i386 [installed,automatic]
libxi6/xenial,now 2:1.7.6-1 i386 [installed,automatic]
libxinerama1/xenial,now 2:1.1.3-1 i386 [installed,automatic]
libxkbcommon-x11-0/xenial,now 0.5.0-1ubuntu2 i386 [installed,automatic]
libxkbcommon0/xenial,now 0.5.0-1ubuntu2 i386 [installed,automatic]
libxkbfile1/xenial,now 1:1.0.9-0ubuntu1 i386 [installed,automatic]
libxklavier16/xenial,now 5.4-0ubuntu2 i386 [installed,automatic]
libxml-parser-perl/xenial,now 2.44-1build1 i386 [installed,automatic]
libxml-twig-perl/xenial,now 1:3.48-1 all [installed,automatic]
libxmu6/xenial,now 2:1.1.2-2 i386 [installed,automatic]
libxpm4/xenial-updates,xenial-security,now 1:3.5.11-1ubuntu0.16.04.1 i386 [installed,automatic]
libxrandr2/xenial,now 2:1.5.0-1 i386 [installed,automatic]
libxrender1/xenial,now 1:0.9.9-0ubuntu1 i386 [installed,automatic]
libxres1/xenial,now 2:1.0.7-1 i386 [installed,automatic]
libxshmfence1/xenial,now 1.2-1 i386 [installed,automatic]
libxslt1.1/xenial-updates,xenial-security,now 1.1.28-2.1ubuntu0.1 i386 [installed,automatic]
libxss1/xenial,now 1:1.2.2-1 i386 [installed,automatic]
libxt6/xenial,now 1:1.1.5-0ubuntu1 i386 [installed,automatic]
libxtables11/xenial,now 1.6.0-2ubuntu3 i386 [installed,automatic]
libxtst6/xenial,now 2:1.2.2-1 i386 [installed,automatic]
libxv1/xenial,now 2:1.0.10-1 i386 [installed,automatic]
libxvidcore4/xenial,now 2:1.3.4-1 i386 [installed,automatic]
libxvmc1/xenial,now 2:1.0.9-1ubuntu1 i386 [installed,automatic]
libxxf86dga1/xenial,now 2:1.1.4-1 i386 [installed,automatic]
libxxf86vm1/xenial,now 1:1.1.4-1 i386 [installed,automatic]
libyajl2/xenial,now 2.1.0-2 i386 [installed,automatic]
libyaml-0-2/xenial,now 0.1.6-3 i386 [installed,automatic]
libyaml-libyaml-perl/xenial,now 0.41-6build1 i386 [installed,automatic]
libyelp0/xenial,now 3.18.1-1ubuntu4 i386 [installed,automatic]
libzbar0/xenial,now 0.10+doc-10ubuntu1 i386 [installed,automatic]
libzephyr4/xenial,now 3.1.2-1build1 i386 [installed,automatic]
libzmq5/xenial,now 4.1.4-7 i386 [installed,automatic]
libzvbi-common/xenial,now 0.2.35-10 all [installed,automatic]
libzvbi0/xenial,now 0.2.35-10 i386 [installed,automatic]
lintian/xenial,now 2.5.43 all [installed,automatic]
linux-base/xenial,now 4.0ubuntu1 all [installed,automatic]
linux-firmware/xenial-updates,xenial-security,now 1.157.8 all [installed,automatic]
linux-headers-4.4.0-75/xenial-updates,xenial-security,now 4.4.0-75.96 all [installed,automatic]
linux-headers-4.4.0-75-generic/xenial-updates,xenial-security,now 4.4.0-75.96 i386 [installed,automatic]
linux-headers-4.4.0-77/xenial-updates,now 4.4.0-77.98 all [installed,automatic]
linux-headers-4.4.0-77-generic/xenial-updates,now 4.4.0-77.98 i386 [installed,automatic]
linux-image-4.4.0-75-generic/xenial-updates,xenial-security,now 4.4.0-75.96 i386 [installed,automatic]
linux-image-4.4.0-77-generic/xenial-updates,now 4.4.0-77.98 i386 [installed,automatic]
linux-image-extra-4.4.0-75-generic/xenial-updates,xenial-security,now 4.4.0-75.96 i386 [installed,automatic]
linux-image-extra-4.4.0-77-generic/xenial-updates,now 4.4.0-77.98 i386 [installed,automatic]
linux-sound-base/xenial,now 1.0.25+dfsg-0ubuntu5 all [installed,automatic]
lm-sensors/xenial,now 1:3.4.0-2 i386 [installed,automatic]
lp-solve/xenial,now 5.5.0.13-7build2 i386 [installed,automatic]
marco/xenial,now 1.12.1-1 i386 [installed,automatic]
marco-common/xenial,now 1.12.1-1 all [installed,automatic]
mate-applets-common/xenial,now 1.12.1-1 all [installed,automatic]
mate-backgrounds/xenial,now 1.12.0-1 all [installed,automatic]
mate-control-center/xenial,now 1.12.1-2 i386 [installed,automatic]
mate-control-center-common/xenial,now 1.12.1-2 all [installed,automatic]
mate-desktop/xenial,now 1.12.1-1 i386 [installed,automatic]
mate-desktop-common/xenial,now 1.12.1-1 all [installed,automatic]
mate-icon-theme/xenial,now 1.12.0-1 all [installed,automatic]
mate-indicator-applet-common/xenial,now 1.12.1-1 all [installed,automatic]
mate-media-common/xenial,now 1.12.1-1 all [installed,automatic]
mate-menus/xenial,now 1.12.0-1 i386 [installed,automatic]
mate-netbook-common/xenial,now 1.12.0-1 all [installed,automatic]
mate-netspeed-common/xenial,now 1.12.0-1 all [installed,automatic]
mate-notification-daemon/xenial,now 1.12.1-1 i386 [installed,automatic]
mate-notification-daemon-common/xenial,now 1.12.1-1 all [installed,automatic]
mate-panel/xenial,now 1.12.2-1 i386 [installed,automatic]
mate-panel-common/xenial,now 1.12.2-1 all [installed,automatic]
mate-polkit/xenial,now 1.12.0-3 i386 [installed,automatic]
mate-polkit-common/xenial,now 1.12.0-3 i386 [installed,automatic]
mate-power-manager-common/xenial,now 1.12.1-1 all [installed,automatic]
mate-screensaver/xenial,now 1.12.0-1 i386 [installed,automatic]
mate-screensaver-common/xenial,now 1.12.0-1 all [installed,automatic]
mate-sensors-applet-common/xenial,now 1.12.1-1 all [installed,automatic]
mate-session-manager/xenial,now 1.12.2-1 i386 [installed,automatic]
mate-settings-daemon/xenial,now 1.12.1-2build1 i386 [installed,automatic]
mate-settings-daemon-common/xenial,now 1.12.1-2build1 all [installed,automatic]
mate-system-monitor-common/xenial,now 1.12.2-1 all [installed,automatic]
mate-terminal/xenial,now 1.12.1-1 i386 [installed,automatic]
mate-terminal-common/xenial,now 1.12.1-1 all [installed,automatic]
mate-user-guide/xenial,now 1.12.0-1 all [installed,automatic]
mate-utils-common/xenial,now 1.12.0-1 all [installed,automatic]
media-player-info/xenial,now 22-2 all [installed,automatic]
menu-xdg/xenial,now 0.5 all [installed,automatic]
mesa-utils/xenial,now 8.3.0-1 i386 [installed,automatic]
mesa-vdpau-drivers/xenial-updates,now 12.0.6-0ubuntu0.16.04.1 i386 [installed,automatic]
metacity-common/xenial-updates,now 1:3.18.7-0ubuntu0.3 all [installed,automatic]
mozo/xenial,now 1.12.0-1 all [installed,automatic]
mscompress/xenial,now 0.4-3 i386 [installed,automatic]
mtools/xenial-updates,now 4.0.18-2ubuntu0.16.04 i386 [installed,automatic]
netpbm/xenial,now 2:10.0-15.3 i386 [installed,automatic]
ocl-icd-libopencl1/xenial,now 2.2.8-1 i386 [installed,automatic]
odbcinst/xenial,now 2.3.1-4.1 i386 [installed,automatic]
odbcinst1debian2/xenial,now 2.3.1-4.1 i386 [installed,automatic]
oneconf/xenial,now 0.3.9 all [installed,automatic]
oneconf-common/xenial,now 0.3.9 all [installed,automatic]
p11-kit/xenial-updates,now 0.23.2-5~ubuntu16.04.1 i386 [installed,automatic]
p11-kit-modules/xenial-updates,now 0.23.2-5~ubuntu16.04.1 i386 [installed,automatic]
p7zip/xenial,now 9.20.1~dfsg.1-4.2 i386 [installed,automatic]
p7zip-full/xenial,now 9.20.1~dfsg.1-4.2 i386 [installed,automatic]
patch/xenial,now 2.7.5-1 i386 [installed,automatic]
patchutils/xenial,now 0.3.4-1 i386 [installed,automatic]
perl-modules-5.22/xenial,now 5.22.1-9 all [installed,automatic]
pidgin-data/xenial-updates,xenial-security,now 1:2.10.12-0ubuntu5.2 all [installed,automatic]
pinentry-gnome3/xenial,now 0.9.7-3 i386 [installed,automatic]
pkg-config/xenial,now 0.29.1-0ubuntu1 i386 [installed,automatic]
pluma-common/xenial,now 1.12.2-2 all [installed,automatic]
plymouth-label/xenial-updates,now 0.9.2-3ubuntu13.1 i386 [installed,automatic]
policykit-1/xenial,now 0.105-14.1 i386 [installed,automatic]
poppler-data/xenial,now 0.4.7-7 all [installed,automatic]
poppler-utils/xenial-updates,now 0.41.0-0ubuntu1.1 i386 [installed,automatic]
postfix/xenial,now 3.1.0-3 i386 [installed,automatic]
pptp-linux/xenial,now 1.8.0-1 i386 [installed,automatic]
printer-driver-foo2zjs-common/xenial,now 20151024dfsg0-1ubuntu1 all [installed,automatic]
pulseaudio/xenial-updates,now 1:8.0-0ubuntu3.2 i386 [installed,automatic]
python/xenial,now 2.7.11-1 i386 [installed,automatic]
python-apt/xenial,now 1.1.0~beta1build1 i386 [installed,automatic]
python-aptdaemon/xenial,now 1.1.1+bzr982-0ubuntu14 all [installed,automatic]
python-aptdaemon.gtk3widgets/xenial,now 1.1.1+bzr982-0ubuntu14 all [installed,automatic]
python-attr/xenial,now 15.2.0-1 all [installed,automatic]
python-avahi/xenial,now 0.6.32~rc+dfsg-1ubuntu2 i386 [installed,automatic]
python-blinker/xenial,now 1.3.dfsg2-1build1 all [installed,automatic]
python-boto/xenial,now 2.38.0-1ubuntu1 all [installed,automatic]
python-bs4/xenial,now 4.4.1-1 all [installed,automatic]
python-bzrlib/xenial-updates,now 2.7.0-2ubuntu3 i386 [installed,automatic]
python-cairo/xenial,now 1.8.8-2 i386 [installed,automatic]
python-cffi-backend/xenial,now 1.5.2-1ubuntu1 i386 [installed,automatic]
python-chardet/xenial,now 2.3.0-2 all [installed,automatic]
python-cloudfiles/xenial,now 1.7.11-3 all [installed,automatic]
python-configobj/xenial,now 5.0.6-2 all [installed,automatic]
python-crypto/xenial-updates,xenial-security,now 2.6.1-6ubuntu0.16.04.2 i386 [installed,automatic]
python-cryptography/xenial-updates,xenial-security,now 1.2.3-1ubuntu0.1 i386 [installed,automatic]
python-cups/xenial,now 1.9.73-0ubuntu2 i386 [installed,automatic]
python-dbus/xenial,now 1.2.0-3 i386 [installed,automatic]
python-debian/xenial,now 0.1.27ubuntu2 all [installed,automatic]
python-debtagshw/xenial,now 2.0.1ubuntu6 all [installed,automatic]
python-defer/xenial,now 1.0.6-2build1 all [installed,automatic]
python-dirspec/xenial,now 13.10-1ubuntu1 all [installed,automatic]
python-dnspython/xenial,now 1.12.0-1 all [installed,automatic]
python-ecdsa/xenial,now 0.13-2 all [installed,automatic]
python-enum34/xenial,now 1.1.2-1 all [installed,automatic]
python-gdbm/xenial,now 2.7.11-2 i386 [installed,automatic]
python-gi/xenial,now 3.20.0-0ubuntu1 i386 [installed,automatic]
python-gi-cairo/xenial,now 3.20.0-0ubuntu1 i386 [installed,automatic]
python-glade2/xenial,now 2.24.0-4ubuntu1 i386 [installed,automatic]
python-gobject/xenial,now 3.20.0-0ubuntu1 all [installed,automatic]
python-gobject-2/xenial,now 2.28.6-12ubuntu1 i386 [installed,automatic]
python-gpgme/xenial,now 0.3-1.1 i386 [installed,automatic]
python-gtk2/xenial,now 2.24.0-4ubuntu1 i386 [installed,automatic]
python-gtksourceview2/xenial,now 2.10.1-2build1 i386 [installed,automatic]
python-html5lib/xenial,now 0.999-4 all [installed,automatic]
python-httplib2/xenial,now 0.9.1+dfsg-1 all [installed,automatic]
python-idna/xenial,now 2.0-3 all [installed,automatic]
python-imaging/xenial-updates,xenial-security,now 3.1.2-0ubuntu1.1 all [installed,automatic]
python-ipaddress/xenial,now 1.0.16-1 all [installed,automatic]
python-jwt/xenial,now 1.3.0-1 all [installed,automatic]
python-keyring/xenial,now 7.3-1ubuntu1 all [installed,automatic]
python-launchpadlib/xenial-updates,now 1.10.3-3ubuntu0.1 all [installed,automatic]
python-lazr.restfulclient/xenial,now 0.13.4-5ubuntu1 all [installed,automatic]
python-lazr.uri/xenial,now 1.0.3-2build1 all [installed,automatic]
python-ldb/xenial,now 2:1.1.24-1ubuntu3 i386 [installed,automatic]
python-lockfile/xenial,now 1:0.12.2-1 all [installed,automatic]
python-lxml/xenial,now 3.5.0-1build1 i386 [installed,automatic]
python-mate-menu/xenial,now 1.12.0-1 i386 [installed,automatic]
python-minimal/xenial,now 2.7.11-1 i386 [installed,automatic]
python-ndg-httpsclient/xenial,now 0.4.0-3 all [installed,automatic]
python-netifaces/xenial,now 0.10.4-0.1build2 i386 [installed,automatic]
python-oauth/xenial,now 1.0.1-5 all [installed,automatic]
python-oauthlib/xenial,now 1.0.3-1 all [installed,automatic]
python-oneconf/xenial,now 0.3.9 all [installed,automatic]
python-openssl/xenial,now 0.15.1-2build1 all [installed,automatic]
python-paramiko/xenial,now 1.16.0-1 all [installed,automatic]
python-pil/xenial-updates,xenial-security,now 3.1.2-0ubuntu1.1 i386 [installed,automatic]
python-piston-mini-client/xenial,now 0.7.5-0ubuntu2 all [installed,automatic]
python-pkg-resources/xenial,now 20.7.0-1 all [installed,automatic]
python-pyasn1/xenial,now 0.1.9-1 all [installed,automatic]
python-pyasn1-modules/xenial,now 0.0.7-0.1 all [installed,automatic]
python-pycurl/xenial,now 7.43.0-1ubuntu1 i386 [installed,automatic]
python-requests/xenial,now 2.9.1-3 all [installed,automatic]
python-samba/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.6 i386 [installed,automatic]
python-secretstorage/xenial,now 2.1.3-1 all [installed,automatic]
python-service-identity/xenial,now 16.0.0-2 all [installed,automatic]
python-setuptools/xenial,now 20.7.0-1 all [installed,automatic]
python-simplejson/xenial,now 3.8.1-1ubuntu2 i386 [installed,automatic]
python-sip/xenial,now 4.17+dfsg-1build1 i386 [installed,automatic]
python-six/xenial,now 1.10.0-3 all [installed,automatic]
python-talloc/xenial,now 2.1.5-2 i386 [installed,automatic]
python-tdb/xenial,now 1.3.8-2 i386 [installed,automatic]
python-twisted-bin/xenial,now 16.0.0-1 i386 [installed,automatic]
python-twisted-core/xenial,now 16.0.0-1 all [installed,automatic]
python-twisted-web/xenial,now 16.0.0-1 all [installed,automatic]
python-ubuntu-sso-client/xenial,now 13.10-0ubuntu11 all [installed,automatic]
python-urllib3/xenial-updates,now 1.13.1-2ubuntu0.16.04.1 all [installed,automatic]
python-wadllib/xenial,now 1.3.2-3 all [installed,automatic]
python-wxgtk3.0/xenial,now 3.0.2.0+dfsg-1build1 i386 [installed,automatic]
python-wxversion/xenial,now 3.0.2.0+dfsg-1build1 all [installed,automatic]
python-xapian/xenial,now 1.2.22-2build1 i386 [installed,automatic]
python-xdg/xenial,now 0.25-4 all [installed,automatic]
python-xlib/xenial,now 0.14+20091101-5 all [installed,automatic]
python-zope.interface/xenial,now 4.1.3-1build1 i386 [installed,automatic]
python2.7/xenial-updates,xenial-security,now 2.7.12-1ubuntu0~16.04.1 i386 [installed,automatic]
python2.7-minimal/xenial-updates,xenial-security,now 2.7.12-1ubuntu0~16.04.1 i386 [installed,automatic]
python3-apport/xenial-updates,now 2.20.1-0ubuntu2.5 all [installed,automatic]
python3-aptdaemon/xenial,now 1.1.1+bzr982-0ubuntu14 all [installed,automatic]
python3-aptdaemon.gtk3widgets/xenial,now 1.1.1+bzr982-0ubuntu14 all [installed,automatic]
python3-blinker/xenial,now 1.3.dfsg2-1build1 all [installed,automatic]
python3-brlapi/xenial-updates,now 5.3.1-2ubuntu2.1 i386 [installed,automatic]
python3-bs4/xenial,now 4.4.1-1 all [installed,automatic]
python3-cairo/xenial,now 1.10.0+dfsg-5build1 i386 [installed,automatic]
python3-cffi-backend/xenial,now 1.5.2-1ubuntu1 i386 [installed,automatic]
python3-chardet/xenial,now 2.3.0-2 all [installed,automatic]
python3-crypto/xenial-updates,xenial-security,now 2.6.1-6ubuntu0.16.04.2 i386 [installed,automatic]
python3-cryptography/xenial-updates,xenial-security,now 1.2.3-1ubuntu0.1 i386 [installed,automatic]
python3-cups/xenial,now 1.9.73-0ubuntu2 i386 [installed,automatic]
python3-cupshelpers/xenial,now 1.5.7+20160212-0ubuntu2 all [installed,automatic]
python3-debian/xenial,now 0.1.27ubuntu2 all [installed,automatic]
python3-defer/xenial,now 1.0.6-2build1 all [installed,automatic]
python3-gi-cairo/xenial,now 3.20.0-0ubuntu1 i386 [installed,automatic]
python3-html5lib/xenial,now 0.999-4 all [installed,automatic]
python3-httplib2/xenial,now 0.9.1+dfsg-1 all [installed,automatic]
python3-idna/xenial,now 2.0-3 all [installed,automatic]
python3-jwt/xenial,now 1.3.0-1 all [installed,automatic]
python3-louis/xenial,now 2.6.4-2 all [installed,automatic]
python3-lxml/xenial,now 3.5.0-1build1 i386 [installed,automatic]
python3-mako/xenial,now 1.0.3+ds1-1ubuntu1 all [installed,automatic]
python3-markupsafe/xenial,now 0.23-2build2 i386 [installed,automatic]
python3-oauthlib/xenial,now 1.0.3-1 all [installed,automatic]
python3-oneconf/xenial,now 0.3.9 all [installed,automatic]
python3-pexpect/xenial,now 4.0.1-1 all [installed,automatic]
python3-pil/xenial-updates,xenial-security,now 3.1.2-0ubuntu1.1 i386 [installed,automatic]
python3-piston-mini-client/xenial,now 0.7.5-0ubuntu2 all [installed,automatic]
python3-pkg-resources/xenial,now 20.7.0-1 all [installed,automatic]
python3-problem-report/xenial-updates,now 2.20.1-0ubuntu2.5 all [installed,automatic]
python3-psutil/xenial,now 3.4.2-1 i386 [installed,automatic]
python3-ptyprocess/xenial,now 0.5-1 all [installed,automatic]
python3-pyasn1/xenial,now 0.1.9-1 all [installed,automatic]
python3-pyatspi/xenial,now 2.18.0+dfsg-3 all [installed,automatic]
python3-pycurl/xenial,now 7.43.0-1ubuntu1 i386 [installed,automatic]
python3-pylast/xenial,now 1.0.0-1 all [installed,automatic]
python3-pyqt5/xenial,now 5.5.1+dfsg-3ubuntu4 i386 [installed,automatic]
python3-pyqt5.qtopengl/xenial,now 5.5.1+dfsg-3ubuntu4 i386 [installed,automatic]
python3-renderpm/xenial,now 3.3.0-1 i386 [installed,automatic]
python3-reportlab/xenial,now 3.3.0-1 all [installed,automatic]
python3-reportlab-accel/xenial,now 3.3.0-1 i386 [installed,automatic]
python3-requests/xenial,now 2.9.1-3 all [installed,automatic]
python3-setuptools/xenial,now 20.7.0-1 all [installed,automatic]
python3-sip/xenial,now 4.17+dfsg-1build1 i386 [installed,automatic]
python3-six/xenial,now 1.10.0-3 all [installed,automatic]
python3-software-properties/xenial-updates,now 0.96.20.6 all [installed,automatic]
python3-speechd/xenial,now 0.8.3-1ubuntu3 all [installed,automatic]
python3-systemd/xenial,now 231-2build1 i386 [installed,automatic]
python3-urllib3/xenial-updates,now 1.13.1-2ubuntu0.16.04.1 all [installed,automatic]
python3-xapian1.3/xenial,now 1.3.4-0ubuntu1 i386 [installed,automatic]
python3-xdg/xenial,now 0.25-4 all [installed,automatic]
python3-xkit/xenial,now 0.5.0ubuntu2 all [installed,automatic]
python3.5/xenial-updates,xenial-security,now 3.5.2-2ubuntu0~16.04.1 i386 [installed,automatic]
python3.5-minimal/xenial-updates,xenial-security,now 3.5.2-2ubuntu0~16.04.1 i386 [installed,automatic]
qdbus/xenial,now 4:4.8.7+dfsg-5ubuntu2 i386 [installed,automatic]
qpdf/xenial,now 6.0.0-2 i386 [installed,automatic]
qt-at-spi/xenial,now 0.4.0-3 i386 [installed,automatic]
qtchooser/xenial,now 52-gae5eeef-2build1~gcc5.2 i386 [installed,automatic]
qtcore4-l10n/xenial,now 4:4.8.7+dfsg-5ubuntu2 all [installed,automatic]
qttranslations5-l10n/xenial,now 5.5.1-2build1 all [installed,automatic]
rename/xenial,now 0.20-4 all [installed,automatic]
rhythmbox-data/xenial,now 3.3-1ubuntu7 all [installed,automatic]
samba/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.6 i386 [installed,automatic]
samba-common/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.6 all [installed,automatic]
samba-dsdb-modules/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.6 i386 [installed,automatic]
samba-libs/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.6 i386 [installed,automatic]
samba-vfs-modules/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.6 i386 [installed,automatic]
sbsigntool/xenial-updates,now 0.6-0ubuntu10.1 i386 [installed,automatic]
secureboot-db/xenial,now 1.1 i386 [installed,automatic]
session-migration/xenial,now 0.2.3 i386 [installed,automatic]
shotwell-common/xenial,now 0.22.0+git20160108.r1.f2fb1f7-0ubuntu1 all [installed,automatic]
software-center-aptdaemon-plugins/xenial,now 0.1.6build1 all [installed,automatic]
software-properties-common/xenial-updates,now 0.96.20.6 all [installed,automatic]
software-properties-gtk/xenial-updates,now 0.96.20.6 all [installed,automatic]
sound-theme-freedesktop/xenial,now 0.8-1 all [installed,automatic]
speech-dispatcher/xenial,now 0.8.3-1ubuntu3 i386 [installed,automatic]
speech-dispatcher-audio-plugins/xenial,now 0.8.3-1ubuntu3 i386 [installed,automatic]
squashfs-tools/xenial,now 1:4.3-3ubuntu2 i386 [installed,automatic]
ssl-cert/xenial,now 1.0.37 all [installed,automatic]
syslinux/xenial,now 3:6.03+dfsg-11ubuntu1 i386 [installed,automatic]
syslinux-common/xenial,now 3:6.03+dfsg-11ubuntu1 all [installed,automatic]
syslinux-legacy/xenial,now 2:3.63+dfsg-2ubuntu8 i386 [installed,automatic]
system-config-printer-common/xenial,now 1.5.7+20160212-0ubuntu2 all [installed,automatic]
system-tools-backends/xenial,now 2.10.2-2 i386 [installed,automatic]
systemd/xenial-updates,now 229-4ubuntu17 i386 [installed,automatic]
t1utils/xenial,now 1.39-2 i386 [installed,automatic]
tdb-tools/xenial,now 1.3.8-2 i386 [installed,automatic]
thermald/xenial-updates,now 1.5-2ubuntu4 i386 [installed,automatic]
topmenu-gtk-common/xenial,now 0.2.1+git20151210.8c6108f-3 all [installed,automatic]
transmission-common/xenial,now 2.84-3ubuntu3 all [installed,automatic]
ttf-mscorefonts-installer/xenial,now 3.4+nmu1ubuntu2 all [installed,automatic]
ttf-ubuntu-font-family/xenial,now 1:0.83-0ubuntu2 all [installed,automatic]
ttf-wqy-microhei/xenial,now 0.2.0-beta-2 all [installed,automatic]
ubuntu-mono/xenial-updates,now 14.04+16.04.20161024-0ubuntu1 all [installed,automatic]
ubuntu-release-upgrader-gtk/xenial-updates,now 1:16.04.21 all [installed,automatic]
ubuntu-sso-client/xenial,now 13.10-0ubuntu11 all [installed,automatic]
ubuntuone-client-data/xenial,now 15.10+15.10.20151007 all [installed,automatic]
udisks2/xenial,now 2.1.7-1ubuntu1 i386 [installed,automatic]
unattended-upgrades/xenial-updates,now 0.90ubuntu0.3 all [installed,automatic]
unixodbc/xenial,now 2.3.1-4.1 i386 [installed,automatic]
uno-libs3/xenial-updates,xenial-security,now 5.1.6~rc2-0ubuntu1~xenial1 i386 [installed,automatic]
update-inetd/xenial,now 4.43 all [installed,automatic]
update-motd/xenial,now 3.6-0ubuntu1 all [installed,automatic]
update-notifier/xenial-updates,now 3.168.4 i386 [installed,automatic]
update-notifier-common/xenial-updates,now 3.168.4 all [installed,automatic]
upower/xenial-updates,now 0.99.4-2ubuntu0.3 i386 [installed,automatic]
ure/xenial-updates,xenial-security,now 5.1.6~rc2-0ubuntu1~xenial1 i386 [installed,automatic]
usb-creator-common/xenial,now 0.3.2 i386 [installed,automatic]
usb-modeswitch-data/xenial,now 20151101-1 all [installed,automatic]
usbmuxd/xenial,now 1.1.0-2 i386 [installed,automatic]
va-driver-all/xenial,now 1.7.0-1 i386 [installed,automatic]
vdpau-driver-all/xenial,now 1.1.1-3ubuntu1 i386 [installed,automatic]
vdpau-va-driver/xenial,now 0.7.4-5 i386 [installed,automatic]
vlc-data/xenial-updates,now 2.2.2-5ubuntu0.16.04.1 all [installed,automatic]
vlc-nox/xenial-updates,now 2.2.2-5ubuntu0.16.04.1 i386 [installed,automatic]
vlc-plugin-samba/xenial-updates,now 2.2.2-5ubuntu0.16.04.1 i386 [installed,automatic]
winbind/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.6 i386 [installed,automatic]
wine/xenial,now 1:1.6.2-0ubuntu14 i386 [installed,automatic]
wine-gecko2.21/xenial,now 2.21-0ubuntu1 i386 [installed,automatic]
wine-mono0.0.8/xenial,now 0.0.8-0ubuntu1 all [installed,automatic]
wine1.6/xenial,now 1:1.6.2-0ubuntu14 i386 [installed,automatic]
wine1.6-i386/xenial,now 1:1.6.2-0ubuntu14 i386 [installed,automatic]
winetricks/xenial,now 0.0+20141009+svn1208-2ubuntu1 all [installed,automatic]
wireless-regdb/xenial,now 2015.07.20-1ubuntu1 all [installed,automatic]
wodim/xenial,now 9:1.1.11-3ubuntu1 i386 [installed,automatic]
wpasupplicant/xenial,now 2.4-0ubuntu6 i386 [installed,automatic]
x11-apps/xenial,now 7.7+5+nmu1ubuntu1 i386 [installed,automatic]
x11-common/xenial,now 1:7.7+13ubuntu3 all [installed,automatic]
x11-session-utils/xenial,now 7.7+2 i386 [installed,automatic]
x11-utils/xenial,now 7.7+3 i386 [installed,automatic]
x11-xfs-utils/xenial,now 7.7+2 i386 [installed,automatic]
x11-xkb-utils/xenial,now 7.7+2 i386 [installed,automatic]
x11-xserver-utils/xenial,now 7.7+7 i386 [installed,automatic]
xfonts-base/xenial,now 1:1.0.4+nmu1 all [installed,automatic]
xfonts-encodings/xenial,now 1:1.0.4-2 all [installed,automatic]
xfonts-utils/xenial,now 1:7.7+3 i386 [installed,automatic]
xinit/xenial-updates,now 1.3.4-3ubuntu0.1 i386 [installed,automatic]
xinput/xenial,now 1.6.2-1 i386 [installed,automatic]
xorg-docs-core/xenial,now 1:1.7.1-1ubuntu1 all [installed,automatic]
xserver-common/xenial-updates,now 2:1.18.4-0ubuntu0.2 all [installed,automatic]
xserver-xorg/xenial,now 1:7.7+13ubuntu3 i386 [installed,automatic]
xserver-xorg-core/xenial-updates,now 2:1.18.4-0ubuntu0.2 i386 [installed,automatic]
xserver-xorg-input-all/xenial,now 1:7.7+13ubuntu3 i386 [installed,automatic]
xserver-xorg-input-evdev/xenial,now 1:2.10.1-1ubuntu2 i386 [installed,automatic]
xserver-xorg-input-synaptics/xenial,now 1.8.2-1ubuntu3 i386 [installed,automatic]
xserver-xorg-input-vmmouse/xenial,now 1:13.1.0-1ubuntu2 i386 [installed,automatic]
xserver-xorg-input-wacom/xenial,now 1:0.32.0-0ubuntu3 i386 [installed,automatic]
xserver-xorg-legacy/xenial-updates,now 2:1.18.4-0ubuntu0.2 i386 [installed,automatic]
xserver-xorg-video-all/xenial,now 1:7.7+13ubuntu3 i386 [installed,automatic]
xserver-xorg-video-amdgpu/xenial-updates,now 1.1.2-0ubuntu0.16.04.1 i386 [installed,automatic]
xserver-xorg-video-ati/xenial,now 1:7.7.0-1 i386 [installed,automatic]
xserver-xorg-video-cirrus/xenial,now 1:1.5.3-1ubuntu3 i386 [installed,automatic]
xserver-xorg-video-fbdev/xenial,now 1:0.4.4-1build5 i386 [installed,automatic]
xserver-xorg-video-intel/xenial-updates,now 2:2.99.917+git20160325-1ubuntu1.2 i386 [installed,automatic]
xserver-xorg-video-mach64/xenial,now 6.9.5-1build2 i386 [installed,automatic]
xserver-xorg-video-mga/xenial,now 1:1.6.4-1build2 i386 [installed,automatic]
xserver-xorg-video-neomagic/xenial,now 1:1.2.9-1build2 i386 [installed,automatic]
xserver-xorg-video-nouveau/xenial,now 1:1.0.12-1build2 i386 [installed,automatic]
xserver-xorg-video-openchrome/xenial,now 1:0.3.3+git20160310-1 i386 [installed,automatic]
xserver-xorg-video-qxl/xenial,now 0.1.4-3ubuntu3 i386 [installed,automatic]
xserver-xorg-video-r128/xenial,now 6.10.0-1build2 i386 [installed,automatic]
xserver-xorg-video-radeon/xenial,now 1:7.7.0-1 i386 [installed,automatic]
xserver-xorg-video-savage/xenial,now 1:2.3.8-1ubuntu3 i386 [installed,automatic]
xserver-xorg-video-siliconmotion/xenial,now 1:1.7.8-1ubuntu6 i386 [installed,automatic]
xserver-xorg-video-sisusb/xenial,now 1:0.9.6-2build5 i386 [installed,automatic]
xserver-xorg-video-tdfx/xenial,now 1:1.4.6-1build2 i386 [installed,automatic]
xserver-xorg-video-trident/xenial,now 1:1.3.7-1build2 i386 [installed,automatic]
xserver-xorg-video-vesa/xenial,now 1:2.3.4-1build2 i386 [installed,automatic]
xserver-xorg-video-vmware/xenial,now 1:13.1.0-2ubuntu3 i386 [installed,automatic]
xz-utils/xenial,now 5.1.1alpha+20120614-2ubuntu2 i386 [installed,automatic]
yelp-xsl/xenial,now 3.18.1-1 all [installed,automatic]
zenity/xenial,now 3.18.1.1-1ubuntu2 i386 [installed,automatic]
zenity-common/xenial,now 3.18.1.1-1ubuntu2 all [installed,automatic]
ickda@ickda-the-pup:~$
```

---

### Post by ickda on 2017-05-02
```
ptardiff (1)         - program that diffs an extracted archive against an une...
ptargrep (1)         - Apply pattern matching to the contents of files in a t...
ptx (1)              - produce a permuted index of file contents
pulseaudio (1)       - The PulseAudio Sound System
purple-remote (1)    - Send remote commands to Pidgin/Finch
pwd (1)              - print name of current/working directory
pwdx (1)             - report current working directory of a process
pxelinux-options (1) - utility to set PXELINUX hard-coded options.
py3clean (1)         - removes .pyc and .pyo files
py3compile (1)       - byte compile Python 3 source files
py3versions (1)      - print python3 version information
pybuild (1)          - invokes various build systems for requested Python ver...
pyclean (1)          - removes .pyc and .pyo files
pycompile (1)        - byte compile Python source files
pydoc (1)            - the Python documentation tool
pydoc2.7 (1)         - the Python documentation tool
pydoc3 (1)           - the Python documentation tool
pydoc3.5 (1)         - the Python documentation tool
pygettext (1)        - Python equivalent of xgettext(1)
pygettext2.7 (1)     - Python equivalent of xgettext(1)
pygettext3 (1)       - Python equivalent of xgettext(1)
pygettext3.5 (1)     - Python equivalent of xgettext(1)
pyhtmlizer (1)       - pretty-print Python source as HTML
pysetup3.5 (1)       - pysetup tool
python (1)           - an interpreted, interactive, object-oriented programmi...
python2 (1)          - an interpreted, interactive, object-oriented programmi...
python2.7 (1)        - an interpreted, interactive, object-oriented programmi...
python3 (1)          - an interpreted, interactive, object-oriented programmi...
python3.5 (1)        - an interpreted, interactive, object-oriented programmi...
python3.5m (1)       - an interpreted, interactive, object-oriented programmi...
python3m (1)         - an interpreted, interactive, object-oriented programmi...
pyversions (1)       - print python version information
qdbus (1)            - a communication-interface for qt-based applications
qmqp-sink (1)        - parallelized QMQP test server
qmqp-source (1)      - parallelized QMQP test generator
qpdf (1)             - PDF transformation software
qpdldecode (1)       - Decode a QPDL stream into human readable form.
qrttoppm (1)         - convert output from the QRT ray tracer into a portable...
qshape (1)           - Print Postfix queue domain and age distribution
qtchooser (1)        - a wrapper used to select between Qt development binary...
qtconfig-qt4 (1)     - Configuration tool for Qt
qvlc (1)             - the VLC media player
ranlib (1)           - generate index to archive.
rasttopnm (1)        - convert a Sun rasterfile into a portable anymap
rawtopgm (1)         - convert raw grayscale bytes into a portable graymap
rawtoppm (1)         - convert raw RGB bytes into a portable pixmap
rbash (1)            - restricted bash, see bash(1)
rcp (1)              - secure copy (remote file copy program)
rctest (1)           - RFCOMM testing
rdiffdir (1)         - compute and apply signatures and diffs to directories
readelf (1)          - Displays information about ELF files.
readlink (1)         - print resolved symbolic links or canonical file names
readom (1)           - read or write data Compact Discs
realpath (1)         - print the resolved path
recode-sr-latin (1)  - convert Serbian text from Cyrillic to Latin script
recountdiff (1)      - recompute patch counts and offsets
red (1)              - line-oriented text editor
rediff (1)           - fix offsets and counts of a hand-edited diff
regedit (1)          - Wine registry editor
regsvr32 (1)         - Wine DLL Registration Server
rename (1)           - renames multiple files
rename.ul (1)        - rename files
rendercheck (1)      - simple tests of the X Render extension.
renice (1)           - alter priority of running processes
reset (1)            - terminal initialization
resize (1)           - set environment and terminal settings to current xterm...
rev (1)              - reverse lines characterwise
rfcomm (1)           - RFCOMM configuration utility
rgb3toppm (1)        - combine three portable graymaps into one portable pixmap
rgrep (1)            - print lines matching a pattern
rhythmbox (1)        - music player and library for tagged files using GStreamer
rhythmbox-client (1) - controls a running instance of rhythmbox
rletopnm (1)         - convert a Utah Raster Tools RLE image file into a PNM ...
rlogin (1)           - OpenSSH SSH client (remote login program)
rm (1)               - remove files or directories
rmdir (1)            - remove empty directories
rnano (1)            - Restricted mode for Nano's ANOther editor, an enhanced...
rpcclient (1)        - tool for executing client side MS-RPC functions
rpcgen (1)           - an RPC protocol compiler
rsh (1)              - OpenSSH SSH client (remote login program)
rstart (1)           - a sample implementation of a Remote Start client
rstartd (1)          - a sample implementation of a Remote Start rsh helper
rsync (1)            - a fast, versatile, remote (and local) file-copying tool
run-mailcap (1)      - execute programs via entries in the mailcap file
run-with-aspell (1)  - script to help use GNU Aspell as an ispell replacement
runcon (1)           - run command with specified security context
runuser (1)          - run a command with substitute user and group ID
rview (1)            - Vi IMproved, a programmers text editor
rvim (1)             - Vi IMproved, a programmers text editor
rvlc (1)             - the VLC media player
sane-find-scanner (1) - find SCSI and USB scanners and their device files
sbattach (1)         - UEFI secure boot detached signature tool
sbigtopgm (1)        - convert an SBIG CCDOPS file into a portable graymap
sbsiglist (1)        - Create EFI_SIGNATURE_LIST signature databases
sbsign (1)           - UEFI secure boot signing tool
sbvarsign (1)        - UEFI authenticated variable signing tool
sbverify (1)         - UEFI secure boot verification tool
scanimage (1)        - scan an image
scp (1)              - secure copy (remote file copy program)
screendump (1)       - dump the contents of a virtual console to stdout
script (1)           - make typescript of terminal session
scriptreplay (1)     - play back typescripts, using timing information
sdiff (1)            - side-by-side merge of file differences
sdptool (1)          - control and interrogate SDP servers
seahorse (1)         - Passwords and Keys
sed (1)              - stream editor for filtering and transforming text
see (1)              - execute programs via entries in the mailcap file
select-default-iwrap (1) - Selects the user default ispell dictionary for use...
select-editor (1)    - select your default sensible-editor from all installed...
sendmail (1)         - Postfix to Sendmail compatibility interface
sensible-browser (1) - sensible editing, paging, and web browsing
sensible-editor (1)  - sensible editing, paging, and web browsing
sensible-pager (1)   - sensible editing, paging, and web browsing
sensors (1)          - print sensors information
seq (1)              - print a sequence of numbers
services-admin (1)   - Services Administration Tool
session-installer (1) - allows applications to easily install and remove soft...
session-migration (1) - Migrate in user session settings.
sessreg (1)          - manage utmpx/wtmpx entries for non-init clients
setarch (1)          - change reported architecture in new program environmen...
setfacl (1)          - set file access control lists
setfattr (1)         - set extended attributes of filesystem objects
setleds (1)          - set the keyboard leds
setmetamode (1)      - define the keyboard meta key handling
setsid (1)           - run a program in a new session
setterm (1)          - set terminal attributes
setupcon (1)         - sets up the font and the keyboard on the console
setvtrgb (1)         - customize the console color map
setxkbmap (1)        - set the keyboard using the X Keyboard Extension
sftp (1)             - secure file transfer program
sg (1)               - execute command as different group ID
sgitopnm (1)         - convert a SGI image file to a portable anymap
sh (1)               - command interpreter (shell)
sh.distrib (1)       - command interpreter (shell)
sha1pass (1)         - Create a SHA1 password hash
sha1sum (1)          - compute and check SHA1 message digest
sha224sum (1)        - compute and check SHA224 message digest
sha256sum (1)        - compute and check SHA256 message digest
sha384sum (1)        - compute and check SHA384 message digest
sha512sum (1)        - compute and check SHA512 message digest
shares-admin (1)     - Shared Folders Administration Tool
sharesec (1)         - Set or get share ACLs
shasum (1)           - Print or Check SHA Checksums
shotwell (1)         - a digital photo organizer
showfont (1)         - font dumper for X font server
showkey (1)          - examine the codes sent by the keyboard
showrgb (1)          - display an rgb color-name database
shred (1)            - overwrite a file to hide its contents, and optionally ...
shuf (1)             - generate random permutations
simple-scan (1)      - Scanning utility
sirtopnm (1)         - convert a Solitaire file into a portable anymap
size (1)             - list section sizes and total size.
skill (1)            - send a signal or report process status
slabtop (1)          - display kernel slab cache information in real time
sldtoppm (1)         - convert an AutoCAD slide file into a portable pixmap
sleep (1)            - delay for a specified amount of time
slogin (1)           - OpenSSH SSH client (remote login program)
slxdecode (1)        - Decode a SLX stream into human readable form.
smbcacls (1)         - Set or get ACLs on an NT file or directory names
smbclient (1)        - ftp-like client to access SMB/CIFS resources on servers
smbcontrol (1)       - send messages to smbd, nmbd or winbindd processes
smbcquotas (1)       - Set or get QUOTAs of NTFS 5 shares
smbget (1)           - wget-like utility for download files over SMB
smbstatus (1)        - report on current Samba connections
smbtar (1)           - shell script for backing up SMB/CIFS shares directly t...
smbtree (1)          - A text based smb network browser
smproxy (1)          - Session Manager Proxy
smtp-sink (1)        - parallelized SMTP/LMTP test server
smtp-source (1)      - parallelized SMTP/LMTP test generator
snap (1)             - Tool to interact with snaps
snice (1)            - send a signal or report process status
soelim (1)           - interpret .so requests in groff input
software-center (1)  - manage software
software-properties-gtk (1) - Software Sources List editor
sort (1)             - sort lines of text files
sotruss (1)          - trace shared library calls through PLT
spctoppm (1)         - convert an Atari compressed Spectrum file into a porta...
spd-conf (1)         - A simple tool for basic configuration of Speech Dispat...
spd-say (1)          - send text-to-speech output request to speech-dispatcher
speaker-test (1)     - command-line speaker test tone generator for ALSA
speech-dispatcher (1) - server process managing speech requests in Speech Dis...
spellintian (1)      - simple spellchecker based on Lintian's data files
split (1)            - split a file into pieces
splitdiff (1)        - separate out incremental patches
splitfont (1)        - extract characters from an ISO-type font.
sprof (1)            - read and display shared object profiling data
sputoppm (1)         - convert an Atari uncompressed Spectrum file into a por...
ssh (1)              - OpenSSH SSH client (remote login program)
ssh-add (1)          - adds private key identities to the authentication agent
ssh-agent (1)        - authentication agent
ssh-argv0 (1)        - replaces the old ssh command-name as hostname handling
ssh-copy-id (1)      - use locally available keys to authorise logins on a re...
ssh-keygen (1)       - authentication key generation, management and conversion
ssh-keyscan (1)      - gather ssh public keys
st4topgm (1)         - convert an SBIG ST4 format file into a portable graymap
start-pulseaudio-x11 (1) - PulseAudio Sound Server X11 Startup Script
startx (1)           - initialize an X session
stat (1)             - display file or file system status
stdbuf (1)           - Run COMMAND, with modified buffering operations for it...
strace (1)           - trace system calls and signals
stream (1)           - a lightweight tool to stream one or more pixel compone...
stream-im6 (1)       - a lightweight tool to stream one or more pixel compone...
strings (1)          - print the strings of printable characters in files.
strip (1)            - Discard symbols from object files.
stty (1)             - change and print terminal line settings
su (1)               - change user ID or become superuser
sum (1)              - checksum and count the blocks in a file
svlc (1)             - the VLC media player
symcryptrun (1)      - Call a simple symmetric encryption tool
sync (1)             - Synchronize cached writes to persistent storage
synclient (1)        - commandline utility to query and modify Synaptics driv...
syndaemon (1)        - a program that monitors keyboard activity and disables...
syslinux (1)         - install the SYSLINUX bootloader on a FAT filesystem
syslinux-legacy (1)  - install the SYSLINUX bootloader on a FAT filesystem
syslinux2ansi (1)    - converts a syslinux-format screen to pc-ansi
system-config-printer (1) - configure a CUPS server
system-config-printer-applet (1) - print job manager
system-tools-backends (1) - message dispatcher for system-tools-backends
systemctl (1)        - Control the systemd system and service manager
systemd (1)          - systemd system and service manager
systemd-analyze (1)  - Analyze system boot-up performance
systemd-ask-password (1) - Query the user for a system password
systemd-bootchart (1) - Boot performance graphing tool
systemd-cat (1)      - Connect a pipeline or program's output with the journal
systemd-cgls (1)     - Recursively show control group contents
systemd-cgtop (1)    - Show top control groups by their resource usage
systemd-delta (1)    - Find overridden configuration files
systemd-detect-virt (1) - Detect execution in a virtualized environment
systemd-escape (1)   - Escape strings for usage in system unit names
systemd-inhibit (1)  - Execute a program with an inhibition lock taken
systemd-machine-id-setup (1) - Initialize the machine ID in /etc/machine-id
systemd-notify (1)   - Notify service manager about start-up completion and o...
systemd-path (1)     - List and query system and user paths
systemd-resolve (1)  - Resolve domain names, IPV4 and IPv6 addresses, DNS res...
systemd-run (1)      - Run programs in transient scope or service or timer units
systemd-tty-ask-password-agent (1) - List or process pending systemd password...
t1ascii (1)          - convert PostScript Type 1 font from binary to ASCII
t1asm (1)            - assemble PostScript Type 1 font
t1binary (1)         - convert PostScript Type 1 font from ASCII to binary
t1disasm (1)         - disassemble PostScript Type 1 font
t1mac (1)            - translate a PFA or PFB PostScript Type 1 font into Mac...
t1unmac (1)          - translate a Mac PostScript Type 1 font into PFA or PFB...
tabs (1)             - set tabs on a terminal
tac (1)              - concatenate and print files in reverse
tail (1)             - output the last part of files
tailf (1)            - follow the growth of a log file
tap2deb (1)          - create Debian packages which wrap .tap files
tap2rpm (1)          - create RPM packages which wrap .tap files
tar (1)              - The GNU version of the tar archiving utility
tarcat (1)           - concatenates the pieces of a GNU tar multi-volume archive
taskset (1)          - set or retrieve a process's CPU affinity
tbl (1)              - format tables for troff
tee (1)              - read from standard input and write to standard output ...
telnet (1)           - user interface to the TELNET protocol
telnet.netkit (1)    - user interface to the TELNET protocol
tempfile (1)         - create a temporary file in a safe manner
test (1)             - check file types and compare values
testparm (1)         - check an smb.conf configuration file for internal corr...
tgatoppm (1)         - convert TrueVision Targa file into a portable pixmap
tgz (1)              - makes a gzip'd tar archive
thinkjettopbm (1)    - convert HP ThinkJet printer commands file to PBM
thunderbird (1)      - thunderbird - Mail User Agent (MUA) and newsgroup/RSS ...
tic (1)              - the terminfo entry-description compiler
tifftopnm (1)        - convert a TIFF file into a portable anymap
tificc (1)           - little cms ICC profile applier for TIFF.
tilda (1)            - first person shooter console likeness terminal
time (1)             - run programs and summarize system resource usage
time-admin (1)       - Time Administration Tool
timedatectl (1)      - Control the system time and date
timeout (1)          - run a command with a time limit
tkconch (1)          - connect to SSH servers graphically
tload (1)            - graphic representation of system load average
toe (1)              - table of (terminfo) entries
top (1)              - display Linux processes
toshsat1800-irdasetup (1) - IrDA setup utility for Toshiba Satellite 1800
toshset (1)          - manipulate bios and hardware settings of Toshiba laptops
touch (1)            - change file timestamps
tput (1)             - initialize a terminal or query terminfo database
tr (1)               - translate or delete characters
transicc (1)         - little cms ColorSpace conversion calculator.
transmission-gtk (1) - a bittorrent client
transset (1)         - Set transparency on a window
trial (1)            - run unit tests
trigger-panel-run-dialog (1) - helper tool of the GNOME main menu applet for ...
troff (1)            - the troff processor of the groff text formatting system
true (1)             - do nothing, successfully
truncate (1)         - shrink or extend the size of a file to the specified size
trust (1)            - Tool for operating on the trust policy store
tset (1)             - terminal initialization
tsort (1)            - perform topological sort
tty (1)              - print the file name of the terminal connected to stand...
twistd (1)           - run Twisted applications (TACs, TAPs)
tzselect (1)         - view timezones
ubuntu-bug (1)       - file a bug report using Apport, or update an existing ...
ucf (1)              - Update Configuration File: preserve user changes in co...
ucfq (1)             - query the ucf database
ucfr (1)             - Update Configuration File Registry: associate packages...
ucs2any (1)          - generate BDF fonts containing subsets of ISO 10646-1 c...
udisksctl (1)        - The udisks command line tool
ul (1)               - do underlining
ulockmgr_server (1)  - Lock Manager Server for FUSE filesystems
uname (1)            - print system information
uncompress (1)       - compress or expand files
unexpand (1)         - convert spaces to tabs
unicode_start (1)    - put keyboard and console in unicode mode
unicode_stop (1)     - revert keyboard and console from unicode mode
uniq (1)             - report or omit repeated lines
unlink (1)           - call the unlink function to remove the specified file
unlzma (1)           - Compress or decompress .xz and .lzma files
unopkg (1)           - LibreOffice Extension Manager
unshare (1)          - run program with some namespaces unshared from parent
unsquashfs (1)       - tool to uncompress squashfs filesystems
unwrapdiff (1)       - demangle word-wrapped patches
unxz (1)             - Compress or decompress .xz and .lzma files
unzip (1)            - list, test and extract compressed files in a ZIP archive
unzipsfx (1)         - self-extracting stub for prepending to ZIP archives
update-alternatives (1) - maintain symbolic links determining default commands
update-desktop-database (1) - Build cache database of MIME types handled by d...
update-mime-database (1) - a program to build the Shared MIME-Info database c...
upower (1)           - UPower command line tool
uptime (1)           - Tell how long the system has been running.
usb-devices (1)      - print USB device details
usb_modeswitch (1)   - control the mode of 'multi-state' USB devices
usb_modeswitch_dispatcher (1) - Linux wrapper for usb_modeswitch (not intende...
usb_printerid (1)    - prints the ID of the printer on a USB port
usbmuxd (1)          - Expose a socket to multiplex connections from and to i...
users (1)            - print the user names of users currently logged in to t...
users-admin (1)      - Users Administration Tool
utmpdump (1)         - dump UTMP and WTMP files in raw format
uuidgen (1)          - create a new UUID value
uxterm (1)           - X terminal emulator for Unicode (UTF-8) environments
uz (1)               - gunzips and extracts a gzip'd tar'd archive
vbetool (1)          - run real-mode video BIOS code to alter hardware state
vdir (1)             - list directory contents
vi (1)               - Vi IMproved, a programmers text editor
view (1)             - Vi IMproved, a programmers text editor
viewres (1)          - graphical class browser for Xt
vim (1)              - Vi IMproved, a programmers text editor
vimdiff (1)          - edit two, three or four versions of a file with Vim an...
vlc (1)              - the VLC media player
vlc-wrapper (1)      - a wrapper to drop privileges with VLC
vmmouse_detect (1)   - VMware mouse device autodetection tool
volname (1)          - return volume name
vstp (1)             - VisioBraille file transferring
w (1)                - Show who is logged on and what they are doing.
w.procps (1)         - Show who is logged on and what they are doing.
wall (1)             - write a message to all users
watch (1)            - execute a program periodically, showing output fullscreen
watchgnupg (1)       - Read and print logs from a socket
wbinfo (1)           - Query information from winbind daemon
wbmptopbm (1)        - convert a wireless bitmap (wbmp) file to a portable bi...
wc (1)               - print newline, word, and byte counts for each file
wftopfa (1)          - Convert a Wadalab base font to Postscript .PFA (or .PF...
whatis (1)           - display one-line manual page descriptions
whereis (1)          - locate the binary, source, and manual page files for a...
which (1)            - locate a command
whiptail (1)         - display dialog boxes from shell scripts
who (1)              - show who is logged on
whoami (1)           - print effective userid
widl (1)             - Wine Interface Definition Language (IDL) compiler
wine (1)             - run Windows programs on Unix
wineboot (1)         - perform Wine initialization, startup, and shutdown tasks
winebuild (1)        - Wine dll builder
winecfg (1)          - Wine Configuration Editor
wineconsole (1)      - The Wine console
winecpp (1)          - Wine C and C++ MinGW Compatible Compiler
winedbg (1)          - Wine debugger
winedump (1)         - A Wine DLL tool
winefile (1)         - Wine File Manager
wineg++ (1)          - Wine C and C++ MinGW Compatible Compiler
winegcc (1)          - Wine C and C++ MinGW Compatible Compiler
winemaker (1)        - generate a build infrastructure for compiling Windows ...
winemine (1)         - Wine Minesweeper game
winepath (1)         - Tool to convert Unix paths to/from Win32 paths
wineserver (1)       - the Wine server
winetricks (1)       - manage virtual windows environments using wine
winicontoppm (1)     - convert a Windows .ico file into 1 or more portable pi...
wmc (1)              - Wine Message Compiler
wmctrl (1)           - interact with a EWMH/NetWM compatible X Window Manager.
wodim (1)            - write data to optical disk media
word-list-compress (1) - word list compressor/decompressor for GNU Aspell
wrc (1)              - Wine Resource Compiler
wrestool (1)         - extract resources from Microsoft Windows(R) binaries
write (1)            - send a message to another user
x-session-manager (1) - Start the MATE Desktop Environment.
x-terminal-emulator (1) - manual page for MATE Terminal Emulator
x-window-manager (1) - The MATE Window Manager
x11perf (1)          - X11 server performance test program
x11perfcomp (1)      - X11 server performance comparison program
xargs (1)            - build and execute command lines from standard input
xauth (1)            - X authority file utility
xbiff (1)            - mailbox flag for X
xbmtopbm (1)         - convert an X11 or X10 bitmap into a portable bitmap
xboxdrv (1)          - A Xbox/Xbox360 gamepad driver that works in userspace
xboxdrvctl (1)       - remote control application for the xboxdrv daemon
xbrlapi (1)          - X11 BrlAPI helper for Linux/Unix
xcalc (1)            - scientific calculator for X
xclipboard (1)       - X clipboard client
xclock (1)           - analog / digital clock for X
xcmsdb (1)           - Device Color Characterization utility for X Color Mana...
xconsole (1)         - monitor system console messages with X
xcursorgen (1)       - create an X cursor file from a collection of PNG images
xcutsel (1)          - interchange between cut buffer and selection
xdg-desktop-icon (1) - command line tool for (un)installing icons to the desktop
xdg-desktop-menu (1) - command line tool for (un)installing desktop menu items
xdg-email (1)        - command line tool for sending mail using the user's pr...
xdg-icon-resource (1) - command line tool for (un)installing icon resources
xdg-mime (1)         - command line tool for querying information about file ...
xdg-open (1)         - opens a file or URL in the user's preferred application
xdg-screensaver (1)  - command line tool for controlling the screensaver
xdg-settings (1)     - get various settings from the desktop environment
xdg-user-dir (1)     - Find an XDG user dir
xdg-user-dirs-update (1) - Update XDG user dir configuration
xditview (1)         - display ditroff output
xdpyinfo (1)         - display information utility for X
xdriinfo (1)         - query configuration information of DRI drivers
xedit (1)            - simple text editor for X
xev (1)              - print contents of X events
xeyes (1)            - a follow the mouse X demo
xfd (1)              - display all the characters in an X font
xfontsel (1)         - point and click selection of X11 font names
xfsinfo (1)          - X font server information utility
xgamma (1)           - Alter a monitor's gamma correction through the X server
xgc (1)              - X graphics demo
xgettext (1)         - extract gettext strings from source
xhost (1)            - server access control program for X
ximtoppm (1)         - convert an Xim file into a portable pixmap
xinit (1)            - X Window System initializer
xinput (1)           - utility to configure and test X input devices
xkbbell (1)          - XKB extension user utility
xkbcomp (1)          - compile XKB keyboard description
xkbevd (1)           - XKB event daemon
xkbprint (1)         - print an XKB keyboard description
xkbvleds (1)         - XKB extension user utility
xkbwatch (1)         - XKB extension user utility
xkill (1)            - kill a client by its X resource
xload (1)            - system load average display for X
xlogo (1)            - X Window System logo
xlsatoms (1)         - list interned atoms defined on server
xlsclients (1)       - list client applications running on a display
xlsfonts (1)         - server font list displayer for X
xmag (1)             - magnify parts of the screen
xman (1)             - Manual page display program for the X Window System
Xmark (1)            - summarize x11perf results
xmessage (1)         - display a message or query in a window (X-based /bin/e...
xmlcatalog (1)       - Command line tool to parse and manipulate XML or SGML ...
xmllint (1)          - command line XML tool
xmodmap (1)          - utility for modifying keymaps and pointer button mappi...
xmore (1)            - plain text display program for the X Window System
Xorg (1)             - X11R7 X server
xpmtoppm (1)         - convert an X11 pixmap into a portable pixmap
xprop (1)            - property displayer for X
xqxdecode (1)        - Decode a XQX stream into human readable form.
xrandr (1)           - primitive command line interface to RandR extension
xrdb (1)             - X server resource database utility
xrefresh (1)         - refresh all or part of an X screen
Xserver (1)          - X Window System display server
xset (1)             - user preference utility for X
xsetmode (1)         - set the mode for an X Input device
xsetpointer (1)      - set an X Input device as the main pointer
xsetroot (1)         - root window parameter setting utility for X
xsetwacom (1)        - commandline utility to query and modify wacom driver s...
xsm (1)              - X Session Manager
xstdcmap (1)         - X standard colormap utility
xsubpp (1)           - compiler to convert Perl XS code into C code
xterm (1)            - terminal emulator for X
xvidtune (1)         - video mode tuner for Xorg
xvinfo (1)           - Print out X-Video extension adaptor information
xvminitoppm (1)      - convert a XV "thumbnail" picture to PPM
xwd (1)              - dump an image of an X window
xwdtopnm (1)         - convert a X11 or X10 window dump file into a portable ...
xwininfo (1)         - window information utility for X
xwud (1)             - image displayer for X
xxd (1)              - make a hexdump or do the reverse.
xz (1)               - Compress or decompress .xz and .lzma files
xzcat (1)            - Compress or decompress .xz and .lzma files
xzcmp (1)            - compare compressed files
xzdiff (1)           - compare compressed files
xzegrep (1)          - search compressed files for a regular expression
xzfgrep (1)          - search compressed files for a regular expression
xzgrep (1)           - search compressed files for a regular expression
xzless (1)           - view xz or lzma compressed (text) files
xzmore (1)           - view xz or lzma compressed (text) files
ybmtopbm (1)         - convert a Bennet Yee "face" file into a portable bitmap
yelp (1)             - browse system documentation
yes (1)              - output a string repeatedly until killed
ypdomainname (1)     - show or set the system's NIS/YP domain name
yuvsplittoppm (1)    - convert a Y- and a U- and a V-file into a portable pixmap
yuvtoppm (1)         - convert Abekas YUV bytes into a portable pixmap
zcat (1)             - compress or expand files
zcmp (1)             - compare compressed files
zdiff (1)            - compare compressed files
zegrep (1)           - search possibly compressed files for a regular expression
zeisstopnm (1)       - convert a Zeiss confocal file into a portable anymap
zenity (1)           - display GTK+ dialogs
zfgrep (1)           - search possibly compressed files for a regular expression
zforce (1)           - force a '.gz' extension on all gzip files
zgrep (1)            - search possibly compressed files for a regular expression
zip (1)              - package and compress (archive) files
zipcloak (1)         - encrypt entries in a zipfile
zipdetails (1)       - display the internal structure of zip files
zipgrep (1)          - search files in a ZIP archive for lines matching a pat...
zipinfo (1)          - list detailed information about a ZIP archive
zipnote (1)          - write the comments in zipfile to stdout, edit comments...
zipsplit (1)         - split a zipfile into smaller zipfiles
zjsdecode (1)        - Decode a ZjStream into human readable form.
zless (1)            - file perusal filter for crt viewing of compressed text
zlib-flate (1)       - raw zlib compression program
zmore (1)            - file perusal filter for crt viewing of compressed text
znew (1)             - recompress .Z files to .gz files
zsoelim (1)          - satisfy .so requests in roff input
ickda@ickda-the-pup:~$
```

Code tags?

```
sudo apt-add-repository ppa:ubuntu-mate-dev/ppa
sudo apt-add-repository ppa:ubuntu-mate-dev/wily-mate
sudo apt-get update
sudo apt-get install --no-install-recommends mate-desktop-environment
Just did this cents mate is outdated.
running software updater as a redundancy.
80. mb ish of data to down-lode. is updating,
```

Update on reboot after up date. Error message gone after log in, my greeter (log in screen) is broken, that is the login screen. I replaced it at one point, but earthier the version up date of Ubuntu messed it up or it was the move. still can log in but still.
Do not remember the replacement greeter was, Just remembered I replaced it. This use to be just a Ubuntu os. But nothing is origanle. I have her tuned for gaming.

I still need help cleaning out the attic so to speak.
I got this when I used ap get update,
```
ickda@ickda-the-pup:~$ sudo apt-get update
[sudo] password for ickda: 
Sorry, try again.
[sudo] password for ickda: 
Reading package lists... Done
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
ickda@ickda-the-pup:~$ 
```
 All help is appreciated, I am giving this a break in tell a reply is given. Thank you for helping me remove a error. Stability is in reach, going to look for a new greater.

Well, why not.
I got compiz up and running. Installed Simple Desktop Display Manager, would like to chang the background on it and add a profile picture. Ubuntu is a good base to work with. I think i even have the boot loader changed if memory serves, sad I can see her no more. I can only see the loading screen of log in...... So much info lost to me....... Well to me it is gibberish but is is mine to see, (Huh what is with this font?) I need to remove a few windows managers that i am not using.  
 Could use any clean up help you can think of.
 My pc is so far from vanilla it could be chocolate. I can not even remember how many times I broke the interface and was stuck in terminal only. Or just crashed it. Fun times.
 She runs good. I could also due some feed back.

How do i find out what display manger software I have on my pc? I can seem to find out anything. Will mate mess with my display manger is anther q that sounds rather important. But who knows  I am but a buffoon staggering around hear.
 I could use some help with my display manager also.... It looks nice but if there is a tool to edit or a place to point me, I am coming to a dead end it seems. Though the last guy that commented, he sent me well to the right path so thanks.

---

### Post by Geoffrey_Arndt on 2017-05-02
Are you certain you're even running a current version of Mate'?  Using the standard repos for just that current version? . . . I thought I saw references to "wily" in one of your output posts.

It's no wonder your system is unstable.

I would suggest to save off any important data.   

Although Mate is not a heavy DE - perhaps looking at another Ubuntu based distro such as "Linux Lite" would be worth your time.    JerryB has put in some great helper scripts and a custom app to launch those scripts (like installing Steam and other items)

---

### Post by ickda on 2017-05-02
I did update after that was taken. I did not bother positing the results of that again cuz when i reran them, it looked the same.
 Is thou suggesting I find another desktop enviroment? Mate is rather cool looking though. I like that I can use my windows key.
I have changed everything that runs my graphics interface. Ubuntu is only ubutnu if I am running in terminal mode. I have tinkered with much. Like I said before stability is pretty good at this point. Just trying to clean out the redundant files. Run some maintenance and free up space.

---

### Post by Geoffrey_Arndt on 2017-05-02
Mate is a fine version of Ubuntu.   I was concerned you were mixing repos & releases but you say you've updated since posting that output.   I probably can't help much with "cleaning up" and clearing redundancies . . as my standard approach is to run a clean system from the start and use different machines for prod-test-dev.   There are apps though for cleaning one's system - - I've just never needed them.     You might want to take a look at Bleachbit, and perhaps there are others that do similar functions (also, check out Parted Magic Rescue System (lot's of great utilities).

---

### Post by QIII on 2017-05-02
ickda --

Please use the standard font and color -- and avoid the special formatting.

---

### Post by ickda on 2017-05-02
> **QIII said:**
> ickda --

Please use the standard font and color -- and avoid the special formatting.
I liked it. If you give me a tool, I will use it. Live a little.  SO drape looking with out color.

I am going to be changing it. it is nice, but if I can find something with a little flavor then I would be so happy.
I could I use some help editing my log in screen. photos and stuff. I hear it has a tweek tool or something.
I will also look into though's program's you mentioned.

---

### Post by QIII on 2017-05-02
Clearly you did not understand the instructions. 

If you modify your posts again after I have edited them a second time, a clearer message will be in order.

---

### Post by ickda on 2017-05-03
I got three or four desktop environments. Mat is the only usable one, though I can say for certin that Mat is missing around 10 to 50 percents of its code. It is a testament to his coder that he is even working, I uninstalled it and aborted its install...... I went to replace it with dugite and that was bored. I think compiz is behind. Due To fact I had the install codes to Ubuntu unity at hand I installed it via terminal Code ctrl+alt F1.  From there I when into reboot to find my wifi shot and mat working,,,,, Right now I am installing plasma due to the greeter I am using was made for the two to go to gather. I figure it is a decent shot at stability. If this fails I will install meta-city.

Computer broke, very basic usage. am using classic Ubuntu as of know, very broken and think I need help with compiz. But will refrain from further action. I have failed to solve the problem, Just happy I could find a way to login.

---

### Post by ickda on 2017-05-04
> **Geoffrey_Arndt said:**
> Mate is a fine version of Ubuntu.   I was concerned you were mixing repos & releases but you say you've updated since posting that output.   I probably can't help much with "cleaning up" and clearing redundancies . . as my standard approach is to run a clean system from the start and use different machines for prod-test-dev.   There are apps though for cleaning one's system - - I've just never needed them.     You might want to take a look at Bleachbit, and perhaps there are others that do similar functions (also, check out Parted Magic Rescue System (lot's of great utilities).
Thank you, removing all of my graphic interfaces and run into a error. My code is most likely a mess. The tool bleachbit cleaned house, though she ran into a error.
 I am running this as I type this. Going to renistall Bridgie or firebox for the ui.
'[COLOR=#242729][FONT=Consolas]aptitude purge `dpkg --get-selections | grep gnome | cut -f 1`[/FONT][/COLOR]aptitude -f install
aptitude purge `dpkg --get-selections | grep deinstall | cut -f 1`
aptitude -f install

---

### Post by lammert-nijhof on 2017-05-07
You have an i3-2350M and have inserted a disk of another very old system coming from 32 bit CPU (AMD or Intel?), while the i3 is a 64 bit CPU. Stop fooling around, you are lucky, that it is still booting, reinstall the system and wipe the disk. Ubuntu Mate 64 bits release 16.04 LTS or 17.04 would be a good choice.

---

