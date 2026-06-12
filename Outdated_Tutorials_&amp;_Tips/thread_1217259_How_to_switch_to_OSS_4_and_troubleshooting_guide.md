---
title: "How to switch to OSS 4 and troubleshooting guide"
date: 2009-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by martinbaselier on 2009-07-19
I just switched to OSS 4 a couple of days ago. Since the difference in sound is amazing, I decided to create this topic and share my experiences. 
There's a different version of this document on my weblog, see the references below. Both contain basically the same information.
Both documents are originally written for ubuntu Jaunty and tested first with kernel 8.26-13.

**benefits**
-better sound quality
-smaller [latency](http://en.wikipedia.org/wiki/Latency_(audio))
-less cpu usage
-better documentation

**drawbacks**
-your card may not be supported
-midi is not supported yet.
-sound recording on generic usb sound devices is not yet implemented, and support for those devices is still considered experimental. 

**Installation**
vist [opensound.com](http://www.opensound.com), choose download on the left side, then you are asked about your OS. If you have a 32-bits ubuntu, choose Linux 2.6 (x86) (DEB). If you have an AMD64, choose the AMD64 deb. 

You will now be on a page with 2 download links, the deb to install and the installation instructions. Save them both. 

The next thing to do is, view the documentation you just downloaded to check if your card is supported.
update: the document seems somewhat outdated. 
[This list seems more up to date.](http://www.opensound.com/osshw.html)

When it is supported, just follow the instructions in the documentation.

For the curious readers, here they are:
Reboot, choose recovery mode when booting and choose the command prompt next (with or without networking). Go to the directory where you downloaded the deb, and type.
```

dpkg -i oss-linux-4.1-1052_i386.deb

```
Reboot and oss 4 is up and running. 

**Troubleshooting**

**general alsa support**
There are a few ways to redirect alsa output to oss
According to what I've read the best way is to use **libasound2-plugins** from the ubuntu repositories.
```

ls /usr/lib/libasound.* -la
-rw-r--r-- 1 root root 1386648 2009-05-11 04:26 /usr/lib/libasound.a
-rw-r--r-- 1 root root     840 2009-05-11 04:25 /usr/lib/libasound.la
lrwxrwxrwx 1 root root      18 2009-07-11 11:07 /usr/lib/libasound.so -> libasound.so.2.0.0
lrwxrwxrwx 1 root root      18 2009-07-11 11:07 /usr/lib/libasound.so.2 > libasound.so.2.0.0
-rw-r--r-- 1 root root  812980 2009-05-11 04:26 /usr/liblibasound.so.2.0.0

```
If it does not and has references to something called salsa, use the following code:
```

sudo apt-get install libasound2-plugins
cd /usr/lib
sudo rm libasound.so libasound.so.2
sudo ln -s libasound.so.2.0.0 libasound.so
sudo ln -s libasound.so.2.0.0 libasound.so.2

```
Both the oss and the arch wiki, tell how to create a alsa configuration file. This would be either /etc/asound.conf or ~/asoundrc.
Don't do this unless you really have to for some reason. This cause my 44,1 kHz mp3's to stop playing, since my sound card is setup at 48kHz.
Check if either of those files exist and move them to a different location, for backup.

**Jack audio connection kit**

I had everything working perfectly, except for jack, which would not run.
When I tried **sudo jackd -H**, it did not show oss a driver option. 
```

ls /usr/lib/jack/
[code]
should show a file called jack_oss.so
If it's there, but jackd does not show it as an option, run **sudo ldconfig**.
If you don't have the file, you don't have the official ubuntu version of **libjack0**, but a version, from a third party. You would have to check your repositories, find out which one has libjack0 in it, disable that one, synchronise the package index, remove libjack0, then reinstall it and all packages you had installed, which were depending on it.

**gstreamer**
This includes systemsounds, totem-gstreamer, Songbird, Banshee and probably some other applications too. 
type gstreamer-plugins in a terminal, choose **custom** for both input and output, **osssink** as input-pipeline, and osssrc as the output one.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121636&stc=1&d=1248013073[/IMG]


**flash**

First let met tell you, that switching to OSS solved a long time flash problem I had, as a nice side effect. ([See this topic]("http://ubuntuforums.org/showthread.php?t=1209293"))

[code]
ls /usr/lib/libflashsupport.so -al
should output:
lrwxrwxrwx 1 root root 38 2009-07-17 00:13 /usr/lib/libflashsupport.so -> /usr/lib/oss/lib/libflashsupport_32.so

```
or if you have installed the 64 bit version, it should point to that file.

If it does not, you probably have libflashsupport installed, remove it (**sudo apt-get remove libflashsupport**) and create your own hyperlink.
[code]
sudo ln -s /usr/lib/oss/lib/libflashsupport_32.so /usr/lib/libflashsupport.so
[/code[


**READ THIS**
Please do **not** use this thread to ask for solutions for problem you encounter. Just create a new thread in the [http://ubuntuforums.org/forumdisplay.php?f=334]multimedia and video-forum[/url] and post a link here. This is to prevent this thread from becoming cluttered with all kinds of different problems (like so many other threads).

This thread is not meant to discuss wetter OSS is better as alsa or not. You are free to create a thread in a different place and post a link here.

If you see mistakes or things missing in this guide, please post them, so this post can be corrected. 

**Uninstall**
If it somehow does not work for you, this is how to remove it:
Reboot and start in a root prompt, as described above. Then enter:
**sudo apt-get purge oss-linux**

references: 
[the arch wiki](http://wiki.archlinux.org/index.php/OSS)
[this weblog article](http://insanecoding.blogspot.com/2009/05/perfect-sound-with-oss-version-4.html)
[the oss wiki](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)
[A different version of this document.](http://martinbaselier.wordpress.com/2009/07/25/how-to-switch-from-alsa-to-ossv4)

---

