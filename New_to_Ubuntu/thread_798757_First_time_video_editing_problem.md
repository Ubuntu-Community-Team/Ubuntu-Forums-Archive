---
title: "First time video editing problem"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Benbow on 2008-05-18
I have been using a windows based video editor on xp and have been looking for alternatives on Ubuntu. During my initial trial I have attempted to use cinelerra but after installing via synaptic I was unable to use and I came up with the following error message:

benbow@benbow-desktop:~$ cinelerra
cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen

Could anyone tell me what it means?

---

### Post by quelx on 2008-05-18
try ```
sudo apt-get install libfaad0 libfaac0
```

---

### Post by Benbow on 2008-05-18
Thanks for the tip but:

benbow@benbow-desktop:~$ sudo apt-get install libfaad0 libfaac0
[sudo] password for benbow:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libfaad0
benbow@benbow-desktop:~$ cinelerra
cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen

Any other ideas?

---

### Post by quelx on 2008-05-18
I think you are running a different version of ubuntu than me.

Open Synaptic (System>Administration>Synaptic...)

search for libfaac and libfaad and install the libraries you have listed (not the dummy packages or dev packages if they are listed).

---

### Post by Benbow on 2008-05-18
Thanks, Quelx. Both libfaac & libfaad are already installed. I am running Gutsy at the moment.
Any other ideas?

---

### Post by quelx on 2008-05-18
what does ```
ls -l /usr/lib/libquicktime*
``` show?

---

### Post by Benbow on 2008-05-18
Hi Quelx

benbow@benbow-desktop:~$ ls -l /usr/lib/libquicktime*
lrwxrwxrwx 1 root root      29 2008-05-18 18:30 /usr/lib/libquicktimehv-1.6.0.so.1 -> libquicktimehv-1.6.0.so.1.0.0
-rw-r--r-- 1 root root 6262348 2007-04-24 15:51 /usr/lib/libquicktimehv-1.6.0.so.1.0.0
lrwxrwxrwx 1 root root      21 2008-05-09 22:17 /usr/lib/libquicktime.so.1 -> libquicktime.so.1.0.0
-rw-r--r-- 1 root root  918344 2007-08-04 19:15 /usr/lib/libquicktime.so.1.0.0

/usr/lib/libquicktime1:
total 252
-rw-r--r-- 1 root root 43700 2007-08-04 19:15 lqt_audiocodec.so
-rw-r--r-- 1 root root  7596 2007-08-04 19:15 lqt_dv.so
-rw-r--r-- 1 root root 81288 2007-08-04 19:15 lqt_ffmpeg.so
-rw-r--r-- 1 root root 24280 2007-08-04 19:15 lqt_mjpeg.so
-rw-r--r-- 1 root root  7108 2007-08-04 19:15 lqt_png.so
-rw-r--r-- 1 root root 32696 2007-08-04 19:15 lqt_rtjpeg.so
-rw-r--r-- 1 root root 31036 2007-08-04 19:15 lqt_videocodec.so
-rw-r--r-- 1 root root 18572 2007-08-04 19:15 lqt_vorbis.so
benbow@benbow-desktop:~$

---

### Post by quelx on 2008-05-18
According to the build log:
[http://launchpadlibrarian.net/8695500/libquicktime_1.0.0%2Bdebian-4ubuntu1_i386.changes](http://launchpadlibrarian.net/8695500/libquicktime_1.0.0%2Bdebian-4ubuntu1_i386.changes)

faad/faac support was dropped in the latest version for gutsy

You will need to build the package yourself to re-enable faac/faad support

I'm running hardy and the support was re-added back.  So your options seem to be upgrade to 8.04 or build the libquicktime from source.

maybe this

```
sudo apt-get install apt-build
sudo apt-build libquicktime1
```

I think it should find the libraries and auto enable them.

I think...

then ```
sudo dpkg -i libquitime-xxxxx.deb
```

---

### Post by Benbow on 2008-05-18
Hi quelx

Sadly it failed and I don't know exactly what I am doing - looks like I will have to upgrade to Hardy.

Thanks for your efforts.
Bri

---

