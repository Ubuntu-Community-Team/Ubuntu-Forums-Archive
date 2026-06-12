---
title: "tried installing ubuntu-restricted-extras got error here is what i git"
date: 2019-03-23
forum: New to Ubuntu
---

### Post by pratap73 on 2019-03-23
```
wget [https://raw.githubusercontent.com/quidsup/flashless-extras/master/flashless.sh](https://raw.githubusercontent.com/quidsup/flashless-extras/master/flashless.sh) && bash flashless.sh
--2019-03-23 11:53:30--  [https://raw.githubusercontent.com/quidsup/flashless-extras/master/flashless.sh](https://raw.githubusercontent.com/quidsup/flashless-extras/master/flashless.sh)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.152.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.152.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3085 (3.0K) [text/plain]
Saving to: &#8216;flashless.sh.1&#8217;

flashless.sh.1      100%[===================>]   3.01K  --.-KB/s    in 0.005s  

2019-03-23 11:53:31 (604 KB/s) - &#8216;flashless.sh.1&#8217; saved [3085/3085]

Do you want to install Microsoft TrueType Fonts (y/n)? y
Updating repositories
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety InRelease                    
Ign:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) yakkety InRelease                    
Ign:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) yakkety-updates InRelease
Ign:4 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) yakkety-backports InRelease
Ign:5 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) yakkety-security InRelease
Err:6 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) yakkety Release
  404  Not Found [IP: 91.189.88.162 80]
Err:7 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) yakkety-updates Release
  404  Not Found [IP: 91.189.88.162 80]
Err:8 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) yakkety-backports Release
  404  Not Found [IP: 91.189.88.162 80]
Err:9 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) yakkety-security Release
  404  Not Found [IP: 91.189.88.162 80]
Reading package lists... Done
E: The repository 'http://in.archive.ubuntu.com/ubuntu yakkety Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://in.archive.ubuntu.com/ubuntu yakkety-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://in.archive.ubuntu.com/ubuntu yakkety-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://in.archive.ubuntu.com/ubuntu yakkety-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

Installing Restricted Extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package gstreamer1.0-plugins-bad is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gstreamer1.0-plugins-good gstreamer1.0-plugins-base

Package oxideqt-codecs-extra is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  oxideqt-codecs

Package gstreamer1.0-plugins-ugly is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package gstreamer1.0-libav is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package lame
E: Package 'unrar' has no installation candidate
E: Unable to locate package gstreamer1.0-fluendo-mp3
E: Couldn't find any package by glob 'gstreamer1.0-fluendo-mp3'
E: Couldn't find any package by regex 'gstreamer1.0-fluendo-mp3'
E: Package 'gstreamer1.0-plugins-bad' has no installation candidate
E: Package 'gstreamer1.0-plugins-ugly' has no installation candidate
E: Package 'gstreamer1.0-libav' has no installation candidate
E: Unable to locate package gstreamer1.0-fluendo-mp3
E: Couldn't find any package by glob 'gstreamer1.0-fluendo-mp3'
E: Couldn't find any package by regex 'gstreamer1.0-fluendo-mp3'
E: Unable to locate package libdvdread4
E: Unable to locate package libk3b6-extracodecs
E: Package 'oxideqt-codecs-extra' has no installation candidate
E: Unable to locate package libavcodec-extra
E: Unable to locate package libavcodec-ffmpeg-extra56
Installing Microsoft Fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ttf-mscorefonts-installer

To install DVD CSS Decoder run: sudo apt install libdvd-pkg

Flashless extras script complete :)
```

---

### Post by Dennis N on 2019-03-23
You get 404: Not Found error because Yakkety release (16.10) is no longer supported. The repository is closed. You should upgrade to a supported version: 18.04 or 18.10.

---

### Post by Impavidus on 2019-03-23
> **Dennis N said:**
> You get 404: Not Found error because Yakkety release (16.10) is no longer supported. The repository is closed. You should upgrade to a supported version: 18.04 or 18.10.

Indeed. Where "upgrade" means fresh install, as trying to release upgrade from a dead release, via some other dead releases, is likely to end in failure.

---

### Post by pratap73 on 2019-03-23
it's not even upgrading

---

