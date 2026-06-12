---
title: "Cannot Install Skype"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by rhenium3 on 2008-08-13
I get this error:

E: /var/cache/apt/archives/skype_2.0.0.72-1_i386.deb: trying to overwrite `/usr/share/icons/skype.png', which is also in package skype-common

I tried to remove the file, there is nothing there as I can see, any suggestions?

---

### Post by hyper_ch on 2008-08-13
how do you try to install it?

---

### Post by rhenium3 on 2008-08-13
using synaptic package and the .deb file downloaded from the website, neither work

---

### Post by rhenium3 on 2008-08-13
When I do sudo apt-get install skype, this is what happenes:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xmms2-plugin-lastfm menu libdiscid0 libresid-builder0c2a
  xmms2-plugin-musepack xmms2-plugin-avformat xmms2-plugin-avcodec
  xmms2-plugin-vocoder xmms2-plugin-cdda xmms2-plugin-gnomevfs
  xmms2-plugin-daap xmms2-plugin-ao libdbus-1-dev xmms2-plugin-m3u
  xmms2-plugin-asx xmms2-plugin-cue xmms2-plugin-curl libdbus-glib-1-dev
  xmms2-plugin-mp4 xmms2-plugin-flac xmms2-plugin-ofa xmms2-plugin-mms
  libsidplay2 xmms2-plugin-pls xmms2-plugin-oss xmms2-plugin-sid
  xmms2-plugin-smb libpurple-dev xmms2-plugin-rss xmms2-plugin-ices
  xmms2-plugin-modplug xmms2-plugin-jack xmms2-plugin-wma xmms2-plugin-xml
  xmms2-plugin-xspf libofa0 xmms2-plugin-icymetaint
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  skype
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/15.5MB of archives.
After this operation, 20.5MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  skype
Install these packages without verification [y/N]? y
(Reading database ... 122804 files and directories currently installed.)
Unpacking skype (from .../skype_2.0.0.72-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/skype_2.0.0.72-1_i386.deb (--unpack):
 trying to overwrite `/usr/share/icons/skype.png', which is also in package skype-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/skype_2.0.0.72-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rhenium3 on 2008-08-14
any ideas?

---

### Post by hyper_ch on 2008-08-15
try:

```

sudo dpkg -P /var/cache/apt/archives/skype_2.0.0.72-1_i386.deb

```

---

### Post by gandalf2000 on 2008-08-15
Open synaptic and completely remove Skype not just "mark for removal", do the "mark for complete removal".  After that is finished do the "mark for installation".  This has helped me a couple of times after an installation has gone bad.

---

### Post by MonkeyRail on 2008-08-15
Have you tried installing it from the [Medibuntu Repository]("http://www.medibuntu.org/")?
It worked for me.
Full instructions on are the site.

---

### Post by mencial on 2009-06-17
> **rhenium3 said:**
> I get this error:

E: /var/cache/apt/archives/skype_2.0.0.72-1_i386.deb: trying to overwrite `/usr/share/icons/skype.png', which is also in package skype-common

I tried to remove the file, there is nothing there as I can see, any suggestions?

Just for the record: This happened to me too. The problem was that I had installed the Skype package from the Medibuntu repository ([http://packages.medibuntu.org/](http://packages.medibuntu.org/)) which breaks it up in two packages, skype and skype-common; then later configured the Skype repository ([http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian)) which has a newer version, and puts it all in one package, skype. Synaptic sees the new version of package skype and tries to upgrade it, but does nothing with package skype-common, and there are files that conflict.

The solution is, if you really want the newer version straight from the Skype repository, to first uninstall both skype and skype-common, and then install skype alone.

There might be a reason to keep the older version from the Medibuntu repository, which is probably repackaged to play nice with the rest of Ubuntu.

---

### Post by alz3abi on 2010-01-14
> **mencial said:**
> Just for the record: This happened to me too. The problem was that I had installed the Skype package from the Medibuntu repository ([http://packages.medibuntu.org/](http://packages.medibuntu.org/)) which breaks it up in two packages, skype and skype-common; then later configured the Skype repository ([http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian)) which has a newer version, and puts it all in one package, skype. Synaptic sees the new version of package skype and tries to upgrade it, but does nothing with package skype-common, and there are files that conflict.

The solution is, if you really want the newer version straight from the Skype repository, to first uninstall both skype and skype-common, and then install skype alone.

There might be a reason to keep the older version from the Medibuntu repository, which is probably repackaged to play nice with the rest of Ubuntu.

```

sudo bash
apt-get remove skype skype-common
wget http://www.skype.com/go/getskype-linux-ubuntu
dpkg -i skype*.deb


```

---

