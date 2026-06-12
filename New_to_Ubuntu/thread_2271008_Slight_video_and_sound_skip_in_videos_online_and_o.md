---
title: "Slight video and sound skip in videos online and offline"
date: 2015-03-26
forum: New to Ubuntu
---

### Post by send2 on 2015-03-26
Hi all,

I am using Ubuntu Trusty 14.04 LTS with a Toshiba Satellite A505-S6986. I did not have this problem with the previous version of Ubuntu, Precise 12.04 LTS. Let me elaborate:
when I am on You Tube watching a video at full screen 720 HD or when I am just watching a downloaded video at regular, not even using full screen I get a hiccup so to speak from time to time, the video and sound seem to skip for a fraction of a second and then it keeps on going normally until at another point when it skips again. 

Is there a way to "fine" tune my settings to smooth out the video and sound so they don't skip anymore? Any codecs I need to check for?

thanks for the help.

---

### Post by DuckHook on 2015-03-26
Please tell us:
1. What browser are you running and with what plugins/extensions etc?
2. How many tabs do you have open and how many other apps?
3. Was 12.04 running Unity on 2D or 3D?
4. Have you tried another browser? If so, what result?

---

### Post by send2 on 2015-03-28
> **DuckHook said:**
> Please tell us:
1. What browser are you running and with what plugins/extensions etc?
2. How many tabs do you have open and how many other apps?
3. Was 12.04 running Unity on 2D or 3D?
4. Have you tried another browser? If so, what result?

Sorry for the delay in replying to you DuckHook. Here are some of the aswers to your questions:

1. I am running Firefox 36.0.4. 

Extensions: Lastpass 3.1, No Script 2.6, Save as Pdf 1.5, Ubuntu Firefox Modifications 3., Image Zoom 0.6, Webmail Ad Blocker.

   Plugins: OpenH264 Video Codec by Cisco Systems 1.3, Shockwave Flash 11.2.2, DivX Web Player 1.4, Gnome Shell Intergration, iTunes Application Detector, Quicktime Plugin 7.6, VLC Multimedia Plugin (compatible with videos3.1.0.1), Windows Media Plugin 10 (compatible, videos)

2. I usually don't have other apps running, I have 3 pages open, one is my web provider's home page, the second Lastpass, the third the page with Yahoo video, I also tried playing video with only one page open (also only with a video player open when offline, still get the same hiccup). 

3. It was running 3D with Gnome classic. I am using regular Gnome as my desktop now. 

4. Yes I have tried Opera, Chrome, still same result. 

Thanks for your help....

---

### Post by Rob Sayer on 2015-03-28
I would suspect the [COLOR=#000000]OpenH264 Video Codec plugin first.  It shouldn't be necessary anyway.  This'll tell you how to yank it:

[/COLOR]https://support.mozilla.org/en-US/questions/1042708

---

### Post by DuckHook on 2015-03-28
IMO if the problem extends across multiple browsers, then it isn't likely to be a Firefox CODEC issue. However, disabling the CODEC can't hurt as it's easy to re-enable if it turns out not to be the problem.

Your laptop is a decent machine with decent graphics. Did you have the proprietary nVidia driver installed in 12.04, but the default community driver in your latest version?

You can also try invoking Firefox from the command line. This will show any error messages that are hidden in a graphical invocation. Be warned: this method spits out a lot of stuff, not just warnings and errors. You may be better off redirecting it to a file on your desktop.```
firefox > ~/Desktop/firefox_output &
```...Linux is case sensitive, so you must type into the terminal *exactly* the above. Better to cut and paste. Once FF is running, go into YouTube and play something. As soon as you get a stutter, close FF. You now have enough logging to try finding what the problem is. The output is lengthy and obscure, but you are looking for any lines that contain "WARNING" or "ERROR". This is where a sophisticated line editor like Geany really comes into its own```
sudo apt-get install geany
```...Geany is actually an IDE, which is a Swiss army knife of programmer goodies, but for our purposes, it's sufficient to treat it as just a really powerful line editor. Please do not post the whole output of the file into the body of this thread. It is too much. However, you can attach your file if you like, and forum members can have a look at it that way.

**Caveat**

It has been pointed out to me by a kind fellow international forum member that instructions assuming the existence of "Desktop" are really far too English-centric and will not work on anything other than and English-speaking installs. Therefore, to universalize these instructions, either just:```
firefox > ~/firefox_output &
```...and then look for the file in your home folder or, if such clutter in your home folder bothers you as much as it bothers me, use my original instructions, but substitute for the name "Desktop" whatever the name of "Desktop" is in your language.

---

### Post by send2 on 2015-03-28
> **Rob Sayer said:**
> I would suspect the [COLOR=#000000]OpenH264 Video Codec plugin first.  It shouldn't be necessary anyway.  This'll tell you how to yank it:

[/COLOR]https://support.mozilla.org/en-US/questions/1042708

Hi Rob Sayer,

i toggled the plugin to false, but I am not sure how to remove it or if it can be even be removed. Thanks for your help.

---

### Post by send2 on 2015-03-28
To DuckHook, 

is it normal for the installation of geany to want to remove the following?

```
 sudo apt-get install geany
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont gcc-4.8-base:i386 kde-l10n-engb libasn1-8-heimdal:i386
  libasound2:i386 libasound2-plugins:i386 libasyncns0:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libcapi20-3 libcapi20-3:i386 libcups2:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libelf1:i386 libexif12:i386
  libexpat1:i386 libffi6:i386 libflac8:i386 libfontconfig1:i386
  libfreetype6:i386 libgcrypt11:i386 libgd3:i386 libgif4:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
  libglib2.0-0:i386 libglu1-mesa:i386 libgnutls26:i386 libgpg-error0:i386
  libgphoto2-6:i386 libgphoto2-port10:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386
  libgstreamer0.10-0:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libice6:i386
  libieee1284-3:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386
  libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386
  libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386 libldap-2.4-2:i386
  libllvm3.4:i386 libltdl7:i386 libmpg123-0:i386 libogg0:i386 libopenal1:i386
  liborc-0.4-0:i386 libosmesa6 libosmesa6:i386 libp11-kit-gnome-keyring:i386
  libp11-kit0:i386 libpcap0.8:i386 libpciaccess0:i386 libpulse0:i386
  libroken18-heimdal:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsm6:i386 libsndfile1:i386
  libspeexdsp1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386
  libtasn1-6:i386 libtiff5:i386 libtxc-dxtn-s2tc0:i386 libusb-1.0-0:i386
  libv4l-0:i386 libv4lconvert0:i386 libvorbis0a:i386 libvorbisenc2:i386
  libvpx1:i386 libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386
  libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxshmfence1:i386
  libxslt1.1:i386 libxt6:i386 libxxf86vm1:i386 linux-headers-3.13.0-32
  linux-headers-3.13.0-32-generic linux-headers-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
  linux-image-generic ocl-icd-libopencl1:i386 p11-kit-modules:i386 p7zip
  wine-gecko2.21 wine-gecko2.21:i386 wine-gecko2.34 wine-gecko2.34:i386
  wine-mono0.0.8 wine-mono4.5.4 wine1.7 wine1.7-amd64 wine1.7-i386:i386
  winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  geany-common
The following NEW packages will be installed:
  geany geany-common
0 upgraded, 2 newly installed, 0 to remove and 10 not upgraded.
Need to get 3,808 kB of archives.
After this operation, 9,872 kB of additional disk space will be used.
Do you want to continue? [Y/n] y

```

checking on this....

---

### Post by send2 on 2015-03-28
> **DuckHook said:**
> IMO if the problem extends across multiple browsers, then it isn't likely to be a Firefox CODEC issue. However, disabling the CODEC can't hurt as it's easy to re-enable if it turns out not to be the problem.

Your laptop is a decent machine with decent graphics. Did you have the proprietary nVidia driver installed in 12.04, but the default community driver in your latest version?

You can also try invoking Firefox from the command line. This will show any error messages that are hidden in a graphical invocation. Be warned: this method spits out a lot of stuff, not just warnings and errors. You may be better off redirecting it to a file on your desktop.```
firefox > ~/Desktop/firefox_output &
```...Linux is case sensitive, so you must type into the terminal *exactly* the above. Better to cut and paste. Once FF is running, go into YouTube and play something. As soon as you get a stutter, close FF. You now have enough logging to try finding what the problem is. The output is lengthy and obscure, but you are looking for any lines that contain "WARNING" or "ERROR". This is where a sophisticated line editor like Geany really comes into its own```
sudo apt-get install geany
```...Geany is actually an IDE, which is a Swiss army knife of programmer goodies, but for our purposes, it's sufficient to treat it as just a really powerful line editor. Please do not post the whole output of the file into the body of this thread. It is too much. However, you can attach your file if you like, and forum members can have a look at it that way.

**Caveat**

It has been pointed out to me by a kind fellow international forum member that instructions assuming the existence of "Desktop" are really far too English-centric and will not work on anything other than and English-speaking installs. Therefore, to universalize these instructions, either just:```
firefox > ~/firefox_output &
```...and then look for the file in your home folder or, if such clutter in your home folder bothers you as much as it bothers me, use my original instructions, but substitute for the name "Desktop" whatever the name of "Desktop" is in your language.

I had the proprietary driver in last Ubuntu version and I just installed NVIDIA driver called "NVIDIA binary driver-version 331.38 from NVIDIA-331 (proprietary,tested)" today.

I already disabled the codec but still get the hiccup.

Obtaining the file you asked for gave the following: .... trying to upload file, getting "invalid format" .... will be back after I find out what formats are accepted.

Let me try again:


thanks again.....

---

### Post by DuckHook on 2015-03-29
> **send2 said:**
> ...is it normal for the installation of geany to want to remove the following?The notification that you are seeing has nothing to do with installing Geany. It would have shown up had you tried to install any app. It is all of the old and no longer used packages that were installed to satisfy dependencies at some point in the past, but which are no longer needed. Examples would be old kernels that have been superseded by new kernels, or libraries that have been rendered obsolete because the app they supported has since moved on to newer libraries, etc. These packages are not automatically removed from your system. But apt tracks them and whenever you invoke apt, it reminds you to remove them manually.

Therefore, it's okay to run the install command and answer "y" to install Geany. Those other packages won't be removed by this process. However, you may wish to remove them anyway and recover the disk space. You have a lot of them, and since they are no longer of any use, removing them won't harm your system.

To remove, the command is:```
sudo apt-get autoremove
```

---

### Post by DuckHook on 2015-03-29
> **send2 said:**
> I had the proprietary driver in last Ubuntu version and I just installed NVIDIA driver called "NVIDIA binary driver-version 331.38 from NVIDIA-331 (proprietary,tested)" today.The new driver will not take effect until you reboot your system. Please do so and see if it helps.

---

### Post by DuckHook on 2015-03-29
> **send2 said:**
> ...the file you asked for...Am going through it now. Can't see anything out of the ordinary and don't think the problem is in your browser or your CODECS. Time to look at your HW. Please post result of:```
lspci -nnk | grep -iA2 audio
```

---

### Post by send2 on 2015-03-29
> **DuckHook said:**
> The notification that you are seeing has nothing to do with installing Geany. It would have shown up had you tried to install any app. It is all of the old and no longer used packages that were installed to satisfy dependencies at some point in the past, but which are no longer needed. Examples would be old kernels that have been superseded by new kernels, or libraries that have been rendered obsolete because the app they supported has since moved on to newer libraries, etc. These packages are not automatically removed from your system. But apt tracks them and whenever you invoke apt, it reminds you to remove them manually.

Therefore, it's okay to run the install command and answer "y" to install Geany. Those other packages won't be removed by this process. However, you may wish to remove them anyway and recover the disk space. You have a lot of them, and since they are no longer of any use, removing them won't harm your system.

To remove, the command is:```
sudo apt-get autoremove
```

Thanks for the explanation, I will do so.

---

### Post by send2 on 2015-03-29
> **DuckHook said:**
> The new driver will not take effect until you reboot your system. Please do so and see if it helps.

Looking at You Tube videos this morning in 720 HD with the new driver, the video is very good but I still get a hiccup, it seems like it is the audio track that skips every now and then, it happens so fast that it is hard to make sure, the video now does not seem to skip, just the audio.

I will check now using local video content and not online..... yes, it is the audio track, video seems to be working great. I tried a video I had with VLC, xine and Mplayer.

---

### Post by send2 on 2015-03-29
> **DuckHook said:**
> Am going through it now. Can't see anything out of the ordinary and don't think the problem is in your browser or your CODECS. Time to look at your HW. Please post result of:```
lspci -nnk | grep -iA2 audio
```

Here it is:

```
 [SIZE=2]lspci -nnk | grep -iA2 audio
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: snd_hda_intel
--
01:00.1 Audio device [0403]: NVIDIA Corporation GT216 HDMI Audio Controller [10de:0be2] (rev a1)
    Subsystem: Toshiba America Info Systems Device [1179:ff15]
    Kernel driver in use: snd_hda_intel[/SIZE]

```

---

### Post by DuckHook on 2015-03-29
> **send2 said:**
> ...yes, it is the audio track...Yours might be [this]("https://wiki.ubuntu.com/Audio/PositionReporting") problem. It's worth following the instructions and seeing if it works.

---

### Post by send2 on 2015-03-29
> **DuckHook said:**
> Yours might be [this]("https://wiki.ubuntu.com/Audio/PositionReporting") problem. It's worth following the instructions and seeing if it works.

I followed the instructions you gave me and used solution 1 and later 2, but I am still having the audio problem. I will try now the turning off pulse audio timer scheduling and see if this helps.

Will be back with the results....

Ok, I think we may have this solved, I kept solution 1 (solution dealing with the position_fix quirking) and I turned off pulse audio timer scheduling. Now video seems to work at 720 HD and full screen as I wanted it. I also checked offline video playback and had no audio skipping. 

Thanks DuckHook for your help. I will wait a few days to see if the hiccuping of sound crops up again before I mark this thread solved.

---

### Post by DuckHook on 2015-03-29
Glad you squashed this one.

Good Luck and Happy Ubuntuing!

---

### Post by send2 on 2015-03-30
> **DuckHook said:**
> Glad you squashed this one.

Good Luck and Happy Ubuntuing!

Thank you! You have been of great help. See you around in the forum!

---

