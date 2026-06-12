---
title: "Video troubleshooting"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by adfgvx on 2012-04-06
Hello everybody,

I recently switched from Ubuntu 10.04 to Xubuntu by following the instructions [here]("http://www.psychocats.net/ubuntu/purexfcelucid"), and now I am having problems playing flv and mp4 videos. When I first tried to play a flv video on Totem Video Player, I had to install a thing so it could play MPEG-4 AAC (if I remember correctly). When I installed it (it was called gstreamer0.10-plugins-bad) and tried to play a flv video, the sound played correctly, but the video display was covered in multicolored flickering lines, like some sort of static, on top of the video. The same thing happens when I play mp4 videos. I tried installing VLC Media Player, but it did the same thing.

When I had Ubuntu, all kinds of videos played correctly.

I appreciate any help you may be able to give me.

---

### Post by cbennett926 on 2012-04-06
Hello,

Have you tried installing the xubuntu-restricted-drivers?

Here's a guide that might help!

[http://www.anthonynotes.com/2011/10/30/tech-thoughts-xubuntu-11-10-post-installation-guide/](http://www.anthonynotes.com/2011/10/30/tech-thoughts-xubuntu-11-10-post-installation-guide/)

---

### Post by adfgvx on 2012-04-07
Thanks for the quick reply!

I installed xubuntu-restricted-extras and rebooted, but that didn't help. I tried to install xubuntu-restricted-drivers using sudo apt-get install xubuntu-restricted-drivers but got a message saying "Couldn't find package xubuntu-restricted-drivers." I tried to install Medibuntu, but got several errors. I also tried installing w32codecs and w64codecs, but got errors both times.

---

### Post by Rodney9 on 2012-04-07
Open Terminal and copy and paste the code below into Terminal, hit enter and it will ask you for your password and to agree.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

then run ```
sudo apt-get install xubuntu-restricted-drivers
```

Rodney

---

### Post by pootan on 2012-04-07
I've been using Xubuntu for years and never heard of a package named xubuntu-restricted-drivers and have never needed it for video playback. It6 looks to me like you've uninstalled a lot of gstreamer packages which are needed for Totem, which is a gnome based player, to run. You could try reinstalling vlc or totem and it might bring back any dependancies you need or you can read through that list you uninstalled and reinstall any gstreamer packages. 

Also by uninstalling all those packages you dind't get a default Xubuntu install. You got a pure Xfce install.

---

