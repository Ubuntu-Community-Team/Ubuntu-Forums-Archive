---
title: "Problems playing video files"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by schoel on 2008-05-13
Whenever I try to watch a video all I see are horisontal stripes in different colours. I've tried both VLC and MPlayer and get the same result in both. The  icon of the file though is a frame from the movie.
I tried the same video file on my Windows computer with both Windows Media Player and VLC and it works fine.

Have you any idea what I can do about this? I've got Ubuntu 7.10 btw.

---

### Post by robalcorn on 2008-05-13
What kind of video file is it? And do you have all the necessary codecs installed?

---

### Post by Inxsible on 2008-05-13
If you have all the necessary codecs installed, then simply log off and then log in again. Better yet, restart your machine. I have seen that a couple of times and a reboot has always helped.

---

### Post by schoel on 2008-05-13
It's an avi / Xvid file. I thought VLC had it's own decoders? I didn't install any codecs. Where can I find those?

---

### Post by robalcorn on 2008-05-13
Go to Applications/ Add/Remove select all availableapplications at the top beside show: and select Ubuntu restricted extras.

---

### Post by Inxsible on 2008-05-13
Applications>>Add/Remove. Search for "gstreamer" without the quotes. Install every codec that you find. Then try again. You will have to restart VLC

---

### Post by SunnyRabbiera on 2008-05-13
> **schoel said:**
> It's an avi / Xvid file. I thought VLC had it's own decoders? I didn't install any codecs. Where can I find those?

you probably have to enable the restricted repositories and packages, dont worry easy fix.
there is a application called synaptic located under system> administration listed as synaptic package manager.
in it you go up to "settings" then to "repositories" and make sure all is checked off except the source code repositories
and again in the second tab in make sure all is checked off except the source code packages.
close the software sources window and hit the refresh button and install the package ubuntu-restricted-extras
that should help you get started.

---

### Post by schoel on 2008-05-13
Thanks for all the help, however, my problem persists. Nor a reboot neither the restricted extras solved my problem.

I downloaded and transfered this file from my Windows computer. Could that be the problem? I transfered it with my external harddrive which has FAT32 file system.

I'll try download some codecs and get back to you :)

---

### Post by SunnyRabbiera on 2008-05-13
Yeh do try to get as many codecs as possible, and try other players too.

---

### Post by schoel on 2008-05-13
BTW, I have the same problem with every video file I've tried playing. I do hear the sound though. I've tried 20+ files which all works on my Windows computer and they are all on my external hard drive.

---

### Post by Inxsible on 2008-05-13
> **schoel said:**
> BTW, I have the same problem with every video file I've tried playing. I do hear the sound though. I've tried 20+ files which all works on my Windows computer and they are all on my external hard drive.If you can hear the sound, I think its more likely a problem with your graphics card than the codecs.

---

### Post by SunnyRabbiera on 2008-05-13
well remember linux is not windows, but dont be afraid to keep on trying.
I know there is a lot of issues with getting stuff working under ubuntu but remember that ubuntu has policies involving using proprietary codecs.
dont give up, it might work for you if you keep on trying.
But one question, are you using the 64bit version of ubuntu or the 32bit?

---

### Post by schoel on 2008-05-13
I already had all codecs I could find by searching for gstreamer installed. I did however reinstall them without any luck. Have you guys got any other idea what my problem could be?

Thanks for all the help, again.

---

### Post by schoel on 2008-05-13
> **SunnyRabbiera said:**
> well remember linux is not windows, but dont be afraid to keep on trying.
I know there is a lot of issues with getting stuff working under ubuntu but remember that ubuntu has policies involving using proprietary codecs.
dont give up, it might work for you if you keep on trying.
But one question, are you using the 64bit version of ubuntu or the 32bit?

I'm using the 32 bit version.

What could I do about the graphics card then?

---

### Post by Inxsible on 2008-05-13
> **schoel said:**
> I'm using the 32 bit version.

What could I do about the graphics card then?What graphics card do you have? Are you using the restricted driver for your card?

---

### Post by schoel on 2008-05-13
> **Inxsible said:**
> What graphics card do you have? Are you using the restricted driver for your card?

ATI Radeon on an Asus laptop. No, I'm not using the restricted driver.

---

### Post by robalcorn on 2008-05-13
Try enabling the restricted driver for your radeon.

---

### Post by crjackson on 2008-05-13
> **schoel said:**
> Whenever I try to watch a video all I see are horisontal stripes in different colours. I've tried both VLC and MPlayer and get the same result in both. The  icon of the file though is a frame from the movie.
I tried the same video file on my Windows computer with both Windows Media Player and VLC and it works fine.

Have you any idea what I can do about this? I've got Ubuntu 7.10 btw.

Well this is my standard for video playback.  I always do the following and never have video playback issues.  I see your not really complaining about DVD playback (which is what this is intended for) however it does install a few things that may be helpfull and it will install any missing codecs.  I used to have the same issue as well but it went away after a kernel update I got from enableing proposed updates...

Backup your system before hand and you can alway revert back if you want..  **_And by all means, you should enable that restricted driver..._**

Try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Hardy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by schoel on 2008-05-14
Thanks for all the help! Using the restricted driver for my card helped!

---

### Post by crjackson on 2008-05-20
> **schoel said:**
> Thanks for all the help! Using the restricted driver for my card helped!

Glad you got it working.  Please click on the little star next to the quote button in the post by the person who helped you.

---

