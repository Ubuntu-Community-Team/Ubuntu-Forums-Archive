---
title: "Need update help"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by davidzaq1 on 2012-09-28
Hello,



I updated my system from Ubuntu 10.04 to 12.04, 10.04 was flawless  and worked perfect but I wanted to have the new design. I installed the  12.04 but had a few bugs with it, mostly with the videos being really  choppy and hesitating or freezing every second or two. I read something  that said they updated the video driver so I tried that and when I  rebooted it went into the terminal. So, when every I turned the computer  on, all I got was the the terminal and that was it. So, I went and bought the 12.04 disk and did a clean install. But now I  am getting messages that my packages are out of date.  I tried to update  through the software center but it just disappeared and I think the  message I got was one saying the software center was one of the out  dated packages. 
  Below is the message I am getting.
  The problem cannot be reported: 
  You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs: 
  software-center, apt, apt-utils, aptdaemon, aptdaemon-data, dbus,  dbus-x11, dconf-gsettings-backend, dconf-service, fontconfig,  fontconfig-config, gir1.2-gtk-3.0, gir1.2-javascriptcoregtk-3.0,  gir1.2-pango-1.0, gir1.2-webkit-3.0, glib-networking,  glib-networking-common, glib-networking-services, gnome-icon-theme,  gnupg, gpgv, initscripts, libapt-inst1.4, libapt-pkg4.12,  libcairo-gobject2, libcairo2, libcups2, libdbus-1-3, libdconf0,  libexpat1, libfontconfig1, libgail-3-0, libgcrypt11, libglib2.0-0,  libglib2.0-bin, libglib2.0-data, libgnutls26, libgssapi-krb5-2,  libgstreamer-plugins-base0.10-0, libgtk-3-0, libgtk-3-bin,  libgtk-3-common, libjavascriptcoregtk-3.0-0, libjpeg-turbo8,  libk5crypto3, libkrb5-3, libkrb5support0, libldap-2.4-2, libpango1.0-0,  libpolkit-agent-1-0, libpolkit-backend
I updated my system from Ubuntu 10.04 to 12.04, 10.04 was flawless  and worked perfect but I wanted to have the new design. I installed the  12.04 but had a few bugs with it, mostly with the videos being really  choppy and hesitating or freezing every second or two. I read something  that said they updated the video driver so I tried that and when I  rebooted it went into the terminal. So, when every I turned the computer  on, all I got was the the terminal and that was it. So, I went and bought the 12.04 disk and did a clean install. But now I  am getting messages that my packages are out of date.  I tried to update  through the software center but it just disappeared and I think the  message I got was one saying the software center was one of the out  dated packages. 
  Below is the message I am getting.
  The problem cannot be reported: 
  You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs: 
  software-center, apt, apt-utils, aptdaemon, aptdaemon-data, dbus,  dbus-x11, dconf-gsettings-backend, dconf-service, fontconfig,  fontconfig-config, gir1.2-gtk-3.0, gir1.2-javascriptcoregtk-3.0,  gir1.2-pango-1.0, gir1.2-webkit-3.0, glib-networking,  glib-networking-common, glib-networking-services, gnome-icon-theme,  gnupg, gpgv, initscripts, libapt-inst1.4, libapt-pkg4.12,  libcairo-gobject2, libcairo2, libcups2, libdbus-1-3, libdconf0,  libexpat1, libfontconfig1, libgail-3-0, libgcrypt11, libglib2.0-0,  libglib2.0-bin, libglib2.0-data, libgnutls26, libgssapi-krb5-2,  libgstreamer-plugins-base0.10-0, libgtk-3-0, libgtk-3-bin,  libgtk-3-common, libjavascriptcoregtk-3.0-0, libjpeg-turbo8,  libk5crypto3, libkrb5-3, libkrb5support0, libldap-2.4-2, libpango1.0-0,  libpolkit-agent-1-0, libpolkit-backend-1-0, libpolkit-gobject-1-0,  libsasl2-2, libsqlite3-0, libssl1.0.0, libtasn1-3, libtiff4, libudev0,  libwebkitgtk-3.0-0, libwebkitgtk-3.0-common, libxml2, libxslt1.1,  oneconf, openssl, perl-base, policykit-1, policykit-1-gnome,  python-aptdaemon, python-aptdaemon.gtk3widgets, python-debtagshw,  python-gi, python-gi-cairo, python-piston-mini-client,  python-software-properties, python-ubuntu-sso-client, python2.7,  python2.7-minimal, shared-mime-info, sysv-rc, sysvinit-utils, tzdata,  ubuntu-sso-client, udev, upstart
  Can someone tell me how to fix this please?   
  -1-0, libpolkit-gobject-1-0,  libsasl2-2, libsqlite3-0, libssl1.0.0, libtasn1-3, libtiff4, libudev0,  libwebkitgtk-3.0-0, libwebkitgtk-3.0-common, libxml2, libxslt1.1,  oneconf, openssl, perl-base, policykit-1, policykit-1-gnome,  python-aptdaemon, python-aptdaemon.gtk3widgets, python-debtagshw,  python-gi, python-gi-cairo, python-piston-mini-client,  python-software-properties, python-ubuntu-sso-client, python2.7,  python2.7-minimal, shared-mime-info, sysv-rc, sysvinit-utils, tzdata,  ubuntu-sso-client, udev, upstart
  Can someone tell me how to fix this please?   
  thank you,
David

---

### Post by UltimateCat on 2012-09-28
Hi:
Make sure that you have all of the Ubuntu repositories for your 12.04 distrubution in your sources list.

Once you have all http:// (address for Ubuntu) in your sources. list you should be fine to open the terminal and run:

```
apt-get update

```And than run:
```
apt-get upgrade

```This document helps you with repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Here's how to add extra repositories if you like:
[http://www.howtogeek.com/howto/ubuntu/adding-extra-repositories-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/adding-extra-repositories-on-ubuntu/)

Have a good weekend!

---

