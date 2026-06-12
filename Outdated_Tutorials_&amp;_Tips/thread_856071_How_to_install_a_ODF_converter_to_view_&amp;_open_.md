---
title: "How to install a ODF converter to view &amp; open DOCX files in OpenOffice"
date: 2008-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxmaveric on 2008-07-11
:guitar::guitar:Microsoft office 2007 untilizes the .docx documents format. This is a simple tutorial on how to enable this feature in OpenOffice for Debian based or an Ubuntu Linux system using the command line.

Here are the .deb package downloads to install the ODF converter:

Install & Download the converter using the following commands at the command line:

For i386 users enter the following at the command line:

[ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb](ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb)

or

wget [ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb](ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb)


For Amd64 users:
[http://cesium.di.uminho.pt/pub/getde...deb1_amd64.deb](http://cesium.di.uminho.pt/pub/getde...deb1_amd64.deb)

or

wget [http://cesium.di.uminho.pt/pub/getde...deb1_amd64.deb](http://cesium.di.uminho.pt/pub/getde...deb1_amd64.deb)


Now to install the downloaded .deb package

i386 users use the following command at the command prompt:

sudo dpkg -i odf-converter_1.0.0-2~getdeb1_i386.deb

or

amd64 users use:

sudo dpkg -i odf-converter_1.0.0-2~getdeb1_amd64.deb

This should do it and I hope this helps out.

---

### Post by be4truth on 2008-07-11
~$ wget [ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb](ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb)
--06:28:07--  [ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb](ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb)
           => `ww...tdeb1_i386.deb'
Resolving ftp-mirror.internap.com... 64.74.207.33
Connecting to ftp-mirror.internap.com|64.74.207.33|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR ww...tdeb1_i386.deb ... 
No such file `ww...tdeb1_i386.deb'.

looks like the link for 32 bit is broken

---

### Post by sarah.fauzia on 2008-07-12
```
wget http://cesium.di.uminho.pt/pub/getde...deb1_amd64.deb
--00:18:16--  http://cesium.di.uminho.pt/pub/getde...deb1_amd64.deb
           => `getde...deb1_amd64.deb'
Resolving cesium.di.uminho.pt... 193.136.19.148
Connecting to cesium.di.uminho.pt|193.136.19.148|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
00:18:17 ERROR 404: Not Found.

```

The link for the 64 bit is also broken. I hope these links are fixed!

---

### Post by azer89 on 2008-07-12
broken links for i386

too bad....:confused::confused::confused:

---

### Post by linuxmaveric on 2008-07-12
re: links broken for i386 & 64bit.

I tried the following at the command line for i386:

wget [ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb](ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb)

& for 64bit users:

wget [http://cesium.di.uminho.pt/pub/getde...deb1_amd64.deb](http://cesium.di.uminho.pt/pub/getde...deb1_amd64.deb)

and this worked just fine. I have my desktop set up to download packages/files straight to my "documents" folder in my home directory. 

I hope this works for ya.

Double check your work and let me know if this works.

---

### Post by be4truth on 2008-07-13
> **linuxmaveric said:**
> re: links broken for i386 & 64bit.

I tried the following at the command line for i386:

wget [ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb](ftp://ftp-mirror.internap.com/pub/ww...tdeb1_i386.deb)

& for 64bit users:

wget [http://cesium.di.uminho.pt/pub/getde...deb1_amd64.deb](http://cesium.di.uminho.pt/pub/getde...deb1_amd64.deb)

and this worked just fine. I have my desktop set up to download packages/files straight to my "documents" folder in my home directory. 

I hope this works for ya.

Double check your work and let me know if this works.

Nope: doesn't work.

---

### Post by embeemb on 2008-07-13
These are the proper locations to download the deb files from

**_i386_**
[ftp://ftp-mirror.internap.com/pub/www.getdeb.net/od/odf-converter_1.0.0-2~getdeb1_i386.deb](ftp://ftp-mirror.internap.com/pub/www.getdeb.net/od/odf-converter_1.0.0-2~getdeb1_i386.deb)

*OR*

wget [ftp://ftp-mirror.internap.com/pub/www.getdeb.net/od/odf-converter_1.0.0-2~getdeb1_i386.deb](ftp://ftp-mirror.internap.com/pub/www.getdeb.net/od/odf-converter_1.0.0-2~getdeb1_i386.deb)

**_AMD64_**

[http://cesium.di.uminho.pt/pub/getdeb/od/odf-converter_1.0.0-2~getdeb1_amd64.deb](http://cesium.di.uminho.pt/pub/getdeb/od/odf-converter_1.0.0-2~getdeb1_amd64.deb)

*OR*

wget [http://cesium.di.uminho.pt/pub/getdeb/od/odf-converter_1.0.0-2~getdeb1_amd64.deb](http://cesium.di.uminho.pt/pub/getdeb/od/odf-converter_1.0.0-2~getdeb1_amd64.deb)

To install:

**_i386_**
sudo dpkg -i odf-converter_1.0.0-2~getdeb1_i386.deb

*OR*

_**AMD64**_
sudo dpkg -i odf-converter_1.0.0-2~getdeb1_amd64.deb

via [UbuntuGeek]("http://www.ubuntugeek.com/ubuntu-tip-how-to-openview-docx-files-in-openoffice.html")

---

