---
title: "Which Flavour/Linux Distrubution is the best for my old PC?"
date: 2016-07-18
forum: New to Ubuntu
---

### Post by daveppeters on 2016-07-18
Hello All - I have an old PC I want to re purpose for watching Region 2 DVDs and occasional streaming. If it performs ok, I may use it to listen to music over my local network but not much else. It has an AMD Sempron 2500+ processor with 2GB RAM and 160GB Hard Drive. Would Lubuntu be the best choice for this machine or would an older Ubuntu (like 12.04 or 14.04) run well on it? I am planning to use VLC as the media player.

Thanks for the recommendations

---

### Post by grahammechanical on 2016-07-18
Does this machine have a video adapter? If so, then what model is it? How much video memory does it have?

The video adapter is what limits old PCs. Even Old Ubuntu 12.04 will require a video adapter that can do hardware accelerated 3D rendering. Otherwise, all video rendering will have to be done by the CPU and that will affect the user's visual experience. 

Download Lubuntu 16.04. Create an install disc and run Lubuntu in a live session and see how it goes. The minimum hardware requirements of Ubuntu and the flavours based on Ubuntu, such as Lubuntu, do not seem to increase from one release to the next.

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

Regards.

---

### Post by sudodus on 2016-07-18
Yes, Lubuntu has the lightest desktop environment of the Ubuntu flavours, much lighter than standard Ubuntu and lighter than Xubuntu and Ubuntu MATE. I would also recommend that you try Lubuntu live. You need to install Lubuntu restricted extras in order to play DVDs and other videos.

```
sudo apt-get install lubuntu-restricted-extras
```

That computer will probably play DVDs well, but maybe not play high definition video (1280x720-50p and similar) well unless there is a separate video card, and you can find a suitable video driver.

We recommend a current version (of Lubuntu), so that you get security updates. Start with 16.04 LTS, and if it does not work, try with the previous LTS version 14.04.1 LTS.

Another alternative is to try an ultra-light linux distro, for example Wary Puppy, TahrPup or Tiny Core. But I don't know, if they provide good video players.

See this link for more tips: [Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by daveppeters on 2016-07-18
Sorry, I forgot about the video card - it has a Radeon X800 GTO so I don't think there will be any issues there.

---

### Post by sudodus on 2016-07-19
Please try live with Lubuntu according to this link: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

I think and hope that the free driver will work with your Radeon graphics card. Let us know how it works :-)

---

### Post by mastablasta on 2016-07-20
> **daveppeters said:**
> Sorry, I forgot about the video card - it has a Radeon X800 GTO so I don't think there will be any issues there.

these radeon x series have mixed linux support. some work excellent others work bad. You will be using opensource Radeon driver. i suggest you start with Xubuntu and work your way "up" from there to Ubutnu or Kubuntu. Lubuntu is also an option but i think Xubuntu will be easier to start with.

---

