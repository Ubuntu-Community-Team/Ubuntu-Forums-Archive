---
title: "rhythmbox plugins"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by uwillpanic on 2012-07-25
I tried connecting my music player to my computer, and in rhythmbox I was prompted to install some updates, several of which had a red exclamation point next to them. It appeared to fail, and none of my music is moving. The message I got was:

 The following packages have unmet dependencies:

gstreamer0.10-ffmpeg: Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                      Depends: libavformat-extra-53 (>= 4:0.7.3-1) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                      Depends: libavutil-extra-51 (>= 4:0.7.3-1) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                      Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is to be installed
                      Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                      Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu0.1 is to be installed
                      Depends: libgstreamer0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu1 is to be installed
                      Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                      Depends: libpostproc-extra-52 (>= 4:0.7.3-1) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                      Depends: libswscale-extra-2 (>= 4:0.7.3-1) but 4:0.8.3ubuntu0.12.04.1 is to be installed
gstreamer0.10-ffmpeg:i386: Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                           Depends: libavformat-extra-53 (>= 4:0.7.3-1) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                           Depends: libavutil-extra-51 (>= 4:0.7.3-1) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                           Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is to be installed
                           Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                           Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu0.1 is to be installed
                           Depends: libgstreamer0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu1 is to be installed
                           Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                           Depends: libpostproc-extra-52 (>= 4:0.7.3-1) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                           Depends: libswscale-extra-2 (>= 4:0.7.3-1) but 4:0.8.3ubuntu0.12.04.1 is to be installed
gstreamer0.10-plugins-bad: Depends: libc6 (>= 2.15) but 2.15-0ubuntu10 is to be installed
                           Depends: libcairo2 (>= 1.2.4) but 1.10.2-6.1ubuntu3 is to be installed
                           Depends: libcdaudio1 (>= 0.99.12p2) but 0.99.12p2-10build1 is to be installed
                           Depends: libcurl3-gnutls (>= 7.16.2-1) but 7.22.0-3ubuntu4 is to be installed
                           Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                           Depends: libglib2.0-0 (>= 2.31.8) but 2.32.3-0ubuntu1 is to be installed
                           Depends: libgsm1 (>= 1.0.13) but 1.0.13-3 is to be installed
                           Depends: libgstreamer-plugins-bad0.10-0 (= 0.10.22.3-2ubuntu2) but 0.10.22.3-2ubuntu2 is to be installed
                           Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.36) but 0.10.36-1ubuntu0.1 is to be installed
                           Depends: libgstreamer0.10-0 (>= 0.10.36) but 0.10.36-1ubuntu1 is to be installed
                           Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu1 is to be installed
                           Depends: libopenal1 (>= 1:1.13) but 1:1.13-4ubuntu3 is to be installed
                           Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                           Depends: libpng12-0 (>= 1.2.13-4) but 1.2.46-3ubuntu4 is to be installed
                           Depends: librsvg2-2 (>= 2.14.4) but 2.36.1-0ubuntu1 is to be installed
                           Depends: librtmp0 (>= 2.3) but 2.4~20110711.gitc28f1bab-1 is to be installed
                           Depends: libschroedinger-1.0-0 (>= 1.0.9) but 1.0.11-1 is to be installed
                           Depends: libsndfile1 (>= 1.0.20) but 1.0.25-4 is to be installed
                           Depends: libssl1.0.0 (>= 1.0.0) but 1.0.1-4ubuntu5.3 is to be installed
                           Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
                           Depends: libvpx1 (>= 1.0.0) but 1.0.0-1 is to be installed
                           Depends: libxvidcore4 (>= 1.2.2) but 2:1.3.2-6 is to be installed
gstreamer0.10-plugins-bad:i386: Depends: libc6 (>= 2.15) but 2.15-0ubuntu10 is to be installed
                                Depends: libcairo2 (>= 1.2.4) but 1.10.2-6.1ubuntu3 is to be installed
                                Depends: libcdaudio1 (>= 0.99.12p2) but 0.99.12p2-10build1 is to be installed
                                Depends: libcurl3-gnutls (>= 7.16.2-1) but 7.22.0-3ubuntu4 is to be installed
                                Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                                Depends: libglib2.0-0 (>= 2.31.8) but 2.32.3-0ubuntu1 is to be installed
                                Depends: libgsm1 (>= 1.0.13) but 1.0.13-3 is to be installed
                                Depends: libgstreamer-plugins-bad0.10-0 (= 0.10.22.3-2ubuntu2) but 0.10.22.3-2ubuntu2 is to be installed
                                Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.36) but 0.10.36-1ubuntu0.1 is to be installed
                                Depends: libgstreamer0.10-0 (>= 0.10.36) but 0.10.36-1ubuntu1 is to be installed
                                Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu1 is to be installed
                                Depends: libopenal1 (>= 1:1.13) but 1:1.13-4ubuntu3 is to be installed
                                Depends: libopenspc0 but it is not going to be installed
                                Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                                Depends: libpng12-0 (>= 1.2.13-4) but 1.2.46-3ubuntu4 is to be installed
                                Depends: librsvg2-2 (>= 2.14.4) but 2.36.1-0ubuntu1 is to be installed
                                Depends: librtmp0 (>= 2.3) but 2.4~20110711.gitc28f1bab-1 is to be installed
                                Depends: libschroedinger-1.0-0 (>= 1.0.9) but 1.0.11-1 is to be installed
                                Depends: libsndfile1 (>= 1.0.20) but 1.0.25-4 is to be installed
                                Depends: libssl1.0.0 (>= 1.0.0) but 1.0.1-4ubuntu5.3 is to be installed
                                Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
                                Depends: libvpx1 (>= 1.0.0) but 1.0.0-1 is to be installed
                                Depends: libxvidcore4 (>= 1.2.2) but 2:1.3.2-6 is to be installed
gstreamer0.10-plugins-ugly: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is to be installed
                            Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                            Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                            Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu0.1 is to be installed
                            Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                            Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                            Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                            Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
gstreamer0.10-plugins-ugly:i386: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is to be installed
                                 Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                                 Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                                 Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu0.1 is to be installed
                                 Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                                 Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                                 Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                                 Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed

any help would be great

---

### Post by Frogs Hair on 2012-07-25
Did you have the Ubuntu restricted extras (media codecs) installed from the software center prior to trying to connect your music player? What kind of player do you use ?

---

### Post by uwillpanic on 2012-07-25
I did not, and I use a smart phone. I believe it has to do with compatibility with certain music file formats, seeing as I can't add music already in a folder either.

---

### Post by Frogs Hair on 2012-07-25
Install the extras package and try again. If you want to use the terminal. ```
sudo apt-get install ubuntu-restricted-extras 
```

---

### Post by bunntoo on 2012-07-25
The issue seems to be a dissatisfied gstreamer and it's accompaniment of ffmpeg.  My suggestion would be to keep reinstalling gstreamer-ffmpeg  (using apt-get) until there are no more complaints about dependencies.  However, it does seem like much of the libraries are asking to be upgraded.   Now it depends:  Does your computer participate in the automatic updates, daily.   Or is it running a one time installation of ubuntu?  My guess is the latter scenario.  ---  I have run into similar issues (using Arch).  I don't use sound much for now.   And I did notice that gstreamer was causing dependecy problems, so I removed it for now (I think it's an intriguing piece of software but needs attention to work correctly).    ---   To do this kind of work it helps to have access to two machines.  One to read online documentation and one to attempt the upgrades.  And upgrades is what I think you'll end up attempting.   ---adding note-- Mostly the system seems to be asking for ubuntu0.12.04  (ie  Version 12.04)

---

### Post by uwillpanic on 2012-07-25
> **Frogs Hair said:**
> Install the extras package and try again. If you want to use the terminal. ```
sudo apt-get install ubuntu-restricted-extras 
```

that did it. Thanks ^^

---

