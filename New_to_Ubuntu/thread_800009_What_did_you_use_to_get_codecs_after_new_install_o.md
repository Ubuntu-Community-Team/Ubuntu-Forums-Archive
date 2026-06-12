---
title: "What did you use to get codecs after new install of 8.04?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by marcelo danico on 2008-05-19
I'll be installing 8.04 after 1.5+ years with 6.06.  Been a long time since I searched for codecs, plugins etc after a new install.

Anyone know a program or script to automate the setup of repositories, codecs etc to get all the multimedia going after a new install?

---

### Post by starcannon on 2008-05-19
This link will get you going :

[Medibuntu How To]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by HotShotDJ on 2008-05-19
In addition to Medibuntu (which I also recommend!) don't forget to install ubuntu-restricted-extras.

---

### Post by marcelo danico on 2008-05-19
Thanks, will I have to chase down the java jre and flash plugins separately or are they included.

---

### Post by wolfen69 on 2008-05-19
just search synaptic for jre(java) and flashplugin-nonfree. i get all my codecs by removing totem (i think it sucks) and installing mplayer and vlc. after you do the medibuntu thing:
```
sudo apt-get install libdvdcss2
``` for DVD playback

---

### Post by HotShotDJ on 2008-05-19
> **marcelo danico said:**
> Thanks, will I have to chase down the java jre and flash plugins separately or are they included.Those are in ubuntu-restricted-extras (although, after your done with this stuff, come back and we'll talk some more about Java).

---

### Post by TJCIB on 2008-05-19
I have enjoyed this guide

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

I believe its updated and, depending on your usage, will take care of most casual browsing, viewing, listening, etc.

---

### Post by marcelo danico on 2008-05-19
I also want to get rid of totem and use mplayer as default. 

Thanks for all the info.

---

### Post by stchman on 2008-05-19
> **marcelo danico said:**
> I'll be installing 8.04 after 1.5+ years with 6.06.  Been a long time since I searched for codecs, plugins etc after a new install.

Anyone know a program or script to automate the setup of repositories, codecs etc to get all the multimedia going after a new install?

If you are using 32 bit Hardy use the following:

```

sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

```

If 64 bit omit the pitfdll package as it does not exist in the 64 bit repos.

I have scripts to automate installs of software in Ubuntu.

[http://www.stchman.com/install_scripts.html](http://www.stchman.com/install_scripts.html)

Download the look at the scripts if you don't want all the software installed.

---

### Post by marcelo danico on 2008-05-19
Thanks STCHMAN, checked out your website, lots of great resources.
:KS

---

