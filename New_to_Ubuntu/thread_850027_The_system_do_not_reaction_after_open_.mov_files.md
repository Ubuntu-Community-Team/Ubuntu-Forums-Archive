---
title: "The system do not reaction after open .mov files"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by x1iaodong on 2008-07-05
I am using ubuntu 8.04 and the system do not reaction for several times after I run some 
files with extension .mov. 
Is it a bug of the OS?

---

### Post by ZabiGG on 2008-07-05
You need to install the appropriate player and codecs (you might night to enable restricted repositories and applications). What video player is installed on your system?

---

### Post by coolaj86 on 2008-07-05
If you want to install all media support (.mov, .mpg, .wma, etc) you can use a script like [this]("http://twdp.hobby-site.org/pub/ubuntu/media-ubuntu.sh"):

```
sudo wget --no-verbose http://www.medibuntu.org/sources.list.d/hardy.list -O \
/etc/apt/sources.list.d/medibuntu.list
sudo apt-get --yes --quiet update
sudo apt-get --yes --quiet install medibuntu-keyring
sudo apt-get --yes --quiet update

sudo apt-get --yes --quiet install ubuntu-restricted-extras gstreamer0.10-plugins-base \
gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly \
gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse \
gstreamer0.10-plugins-good vlc

sudo apt-get --yes --quiet install libdvdcss2 w32codecs aacplusenc ffmpeg acroread \
acroread-escript acroread-plugins mozilla-acroread non-free-codecs

sudo apt-get --yes --quiet flashplugin-nonfree
```

This will install all of the media codecs in the Ubuntu and Medibuntu repositories

---

