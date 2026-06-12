---
title: "Accidental upgrade...any way to undo? Help!"
date: 2005-02-22
forum: Repositories &amp; Backports
---

### Post by pasmith on 2005-02-22
OK folks, I think I really blew it. I was trying to install a game from the Hoary distro (I'm using Warty) and it needed a newer version of a particular lib than the one I had. So after trying a bunch of other things, I issued this command:

sudo apt-get -t Hoary upgrade libexpat1

(libexpat1 is the library I wanted to upgrade).

And suddenly, bam, a TON of stuff got upgraded:

The following packages have been kept back:
  gnome-cpufreq-applet gstreamer0.8-a52dec gstreamer0.8-mad
  gstreamer0.8-mpeg2dec gstreamer0.8-swfdec gtk2-engines-crux
  gtk2-engines-lighthouseblue gtkhtml3.2 libgal2.2-common libgcrypt7
  libgnutls10 libgtkhtml3.2-11 libpt-plugins-v4l libsdl-image1.2 python-hip
  python2.3-examples python2.3-gdbm python2.3-glade2 python2.3-gnome2
  python2.3-gtk2 python2.3-librdf python2.3-mpz python2.3-mysqldb
  python2.3-numarray python2.3-osd python2.3-pycurl python2.3-pymacs
  python2.3-pyorbit python2.3-reportlab python2.3-sqlite xfree86-common
  xine-ui xserver-xfree86
The following packages will be upgraded:
  cabextract gftp-common gftp-gtk gstreamer0.8-plugins libcurl2 libsvga1
  libswfdec0 openoffice.org-mimelnk python2.3-adns python2.3-clientcookie
  python2.3-crypto python2.3-egenix-mxdatetime python2.3-egenix-mxproxy
  python2.3-egenix-mxstack python2.3-egenix-mxtexttools
  python2.3-egenix-mxtools python2.3-eunuchs python2.3-fixedpoint
  python2.3-gadfly python2.3-htmlgen python2.3-htmltmpl python2.3-iconvcodec
  python2.3-id3lib python2.3-imaging python2.3-imaging-sane python2.3-jabber
  python2.3-kjbuckets python2.3-ldap python2.3-musicbrainz python2.3-opengl
  python2.3-pam python2.3-pexpect python2.3-pgsql python2.3-pylibacl
  python2.3-pyopenssl python2.3-pyxattr python2.3-simpletal python2.3-twisted
  python2.3-twisted-bin python2.3-unit python2.3-xml python2.3-xmpp wesnoth
  wesnoth-data wesnoth-editor wesnoth-music wesnoth-server
  xfree86-driver-synaptics
48 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.


I blissfully hit Y at the prompt without really thinking, then watched all this stuff scroll by in a panic.

So do I now have a system with one foot in the Warty world and one foot in the Hoary world? What's going to happen if I reboot? Will my system come back?

Help!!??

Clearly no one should be giving this linux newbie power-tools to play with. :)

---

