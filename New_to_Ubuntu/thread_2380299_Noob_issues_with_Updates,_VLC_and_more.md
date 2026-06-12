---
title: "Noob issues with Updates, VLC and more"
date: 2017-12-15
forum: New to Ubuntu
---

### Post by paulakreuzer on 2017-12-15
Hey, i'm a total noob to Ubuntu, Gnu Linux in general and using commands in the terminal.
I just got my new computer yesterday and the first thing I wanted to do is learn how to install and update apps.
I noticed I have two preinstalled apps called "Ubuntu Software" and "Software Updater".

Ubuntu Software right away told me some other preinstalled apps were out of date, so I clicked to update them all and it worked for all but two entries: "OS Updates" and "VLC".
Both remained in the list of due updates and when I clicked "Install" it turned to "Installing", the bar filled to the end and then it just aborted without an error.
After a reboot VLC was gone and it's no longer in the list of installed apps either.

Next I tried Software Updater which told me "Base Library for VLC and it´s modules" needs to be updated, so I tried that, but it ended with "The installation or removal of a software package failed."

I then found some basic command lines for updating/removing apps, so I tried:

[HTML]sudo apt-get upgrade[/HTML]

which printed out:

[HTML]
The following packages were automatically installed and are no longer required:
  libaribb24-0 libavcodec57 libavformat57 libavutil55
  libbasicusageenvironment1 libcddb2 libdvbpsi10 libebml4v5 libgroupsock8
  liblivemedia50 libmatroska6v5 libmicrodns0 libmpcdec6 libnfs8 libopenjp2-7
  libopenmpt-modplug1 libopenmpt0 libpostproc54 libproxy-tools
  libresid-builder0c2a libsdl-image1.2 libsidplay2v5 libsndio6.1 libssh2-1
  libswresample2 libswscale4 libupnp6 libusageenvironment3 libva-drm1
  libva-wayland1 libva-x11-1 libvlc-bin libvlc5 libvlccore8 libvlccore9
  libxcb-xv0 linux-headers-4.10.0-28 linux-headers-4.10.0-28-generic
  linux-image-4.10.0-28-generic linux-image-extra-4.10.0-28-generic vlc-bin
  vlc-data vlc-l10n vlc-plugin-notify vlc-plugin-qt vlc-plugin-samba
  vlc-plugin-skins2 vlc-plugin-video-output vlc-plugin-video-splitter
  vlc-plugin-visualization
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  libavcodec-extra
The following packages will be upgraded:
  libvlccore8

...

Do you want to continue? [Y/n]
[/HTML]

[HTML]Y[/HTML]

[HTML](Reading database ... 294841 files and directories currently installed.)
Preparing to unpack .../libvlccore8_3.0.0~~git20171210+r73147+99~ubuntu16.04.1_amd64.deb ...
Unpacking libvlccore8:amd64 (3.0.0~~git20171210+r73147+99~ubuntu16.04.1) over (3.0.0~~git20170923+r71740+81~ubuntu16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libvlccore8_3.0.0~~git20171210+r73147+99~ubuntu16.04.1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libvlccore.so.9.0.0', which is also in package libvlccore9:amd64 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libvlccore8_3.0.0~~git20171210+r73147+99~ubuntu16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML]

Since in the meantime I also tried re-installing VLC with Ubuntu Software, which failed (VLC is shown in the launcher as "Waiting to Install"), I thought removing VLC completely might help, so I tried

[HTML]sudo apt-get purge <VLC>[/HTML]

which just prints out:

[HTML]syntax error near unexpected token `newline'[/HTML]

So how can I fix VLC and system updates?

---

### Post by deadflowr on 2017-12-15
Crucial information missing:
What PPA is this from?
(Or what PPAs have you added?)

and please post the output for
```
sudo apt update
```

---

### Post by paulakreuzer on 2017-12-15
Thanks for the quick answer.

I had to look up what a PPA is and I didn't add any, but this is what was set up by default:

Canonical Partners
ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial main
ppa.launchpad.net/webupd8team/java/ubuntu xenial main
ppa.launchpad.net/videolan/master-daily/ubuntu xenial main


sudo apt update puts out:

```
Hit:1 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial InRelease
Get:2 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-updates InRelease [102 kB]
Hit:3 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease    
Get:4 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-security InRelease [102 kB]
Hit:5 http://ppa.launchpad.net/videolan/master-daily/ubuntu xenial InRelease   
Hit:6 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:7 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-updates/main amd64 DEP-11 Metadata [307 kB]
Hit:8 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease        
Get:9 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-updates/main DEP-11 64x64 Icons [214 kB]
Get:10 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-updates/universe Translation-en [229 kB]
Get:11 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-updates/universe amd64 DEP-11 Metadata [185 kB]
Get:12 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-updates/universe DEP-11 64x64 Icons [275 kB]
Get:13 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-updates/multiverse amd64 DEP-11 Metadata [5,888 B]
Get:14 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-security/main amd64 DEP-11 Metadata [62.4 kB]
Get:15 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-security/main DEP-11 64x64 Icons [62.6 kB]
Get:16 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-security/universe Translation-en [99.0 kB]
Get:17 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-security/universe amd64 DEP-11 Metadata [51.4 kB]
Get:18 http://ftp.energotel.sk/pub/linux/ubuntu/archive xenial-security/universe DEP-11 64x64 Icons [85.1 kB]
Fetched 1,782 kB in 1s (924 kB/s)                                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

If I continue with sudo apt list --upgradable it prints out:

```
Listing... Done
libavcodec-extra/xenial,xenial 7:3.3.3-2~ubuntu16.04.1~ppa1 all [upgradable from: 7:2.8.11-0ubuntu0.16.04.1]
libvlccore8/xenial 3.0.0~~git20171210+r73147+99~ubuntu16.04.1 amd64 [upgradable from: 3.0.0~~git20170923+r71740+81~ubuntu16.04.1]

```

Just so you know I don't know what any of what terminal prints out means.

---

### Post by mc4man on 2017-12-15
You could try what I mentioned here
[https://ubuntuforums.org/showthread.php?t=2380311&p=13721298&viewfull=1#post13721298](https://ubuntuforums.org/showthread.php?t=2380311&p=13721298&viewfull=1#post13721298)

Or if you'd prefer to get rid of the vlc ppa & use the standard Ubuntu vlc version that is easily done, just ask...

---

### Post by paulakreuzer on 2017-12-16
Thanks. I tried that.
Seems to work until the last command without an error but then it says:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-plugin-base (= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Also the VLC app is still shown in the launcher as "waiting to install".

PS: I redid steps 1+2, restarted the computer and the "VLC waiting to install" symbol in the launcher was gone.
Then I was able to finish the update with "Software Updater", which reinstalled VLC.

So now the only issue I have left is that "Ubuntu Software" keeps telling me that an OS update is available, but clicking "Install" just shows the progress bar for a short time, then it aborts without an error.

---

### Post by mc4man on 2017-12-16
Gave the ppa a check, they have an issue with 2 needed packages, vlc-plugin-video-output & vlc-plugin-base. As in - 
 ```
vlc-plugin-video-output : Breaks: vlc-plugin-base (< 3.0.0~rc1~20171206-1~) but 3.0.0~rc1~~git20171215+r73271+108~ubuntu16.04.1 is to be installed
```
So until they fix this you could 
1. do without vlc
2. remove the ppa & install ubuntu version (2.2.2


Edit: contacted ppa maintainers, maybe they'll fix .. It's just a simple change to the /debian/control file,i.e.
```
@@ -324,8 +324,8 @@
          ${shlibs:Depends},
          ${vlc:PluginABI}
 Enhances: vlc
-Breaks: vlc-plugin-base (<< 3.0.0~rc1~20171206-1~)
-Replaces: vlc-plugin-base (<< 3.0.0~rc1~20171206-1~)
+Breaks: vlc-plugin-base (<< 3.0.0~~rc1~20171206-1~)
+Replaces: vlc-plugin-base (<< 3.0.0~~rc1~20171206-1~)
 Description: multimedia player and streamer (video output plugins)
  VLC is the VideoLAN project's media player. It plays MPEG, MPEG-2, MPEG-4,
  DivX, MOV, WMV, QuickTime, WebM, FLAC, MP3, Ogg/Vorbis files, DVDs, VCDs,
```


If not done shortly then ask how to use ppa-purge to properly remove the ppa..

---

### Post by paulakreuzer on 2017-12-16
> **mc4man said:**
> 
So until they fix this you could 
2. remove the ppa & install ubuntu version (2.2.2


Yes, I think that's what I did:

> **paulakreuzer said:**
> 

PS: I redid steps 1+2, restarted the computer and the "VLC waiting to install" symbol in the launcher was gone.
Then I was able to finish the update with "Software Updater", which reinstalled VLC.

So now the only issue I have left is that "Ubuntu Software" keeps  telling me that an OS update is available, but clicking "Install" just  shows the progress bar for a short time, then it aborts without an  error.

PS: I fixed it! :)
With sudo apt-get automove followed by sudo apt-get dist-upgrade.

I think I'm starting to get the hang of this. :)
This topic can be close.

---

