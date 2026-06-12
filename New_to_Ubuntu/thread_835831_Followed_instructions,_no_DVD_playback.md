---
title: "Followed instructions, no DVD playback"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-06-20
Hi folks, 

I followed the instructions here to try to get DVD playback in ubuntu. I'm using Ubuntu 8.04. 

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

I followed the instructions, fired up Totem, and got a "Could not read from resource" error. I can see the DVD disc on my desktop and when I double click it, it opens. 

I have VLC installed as well and the File --> Open Disc --> DVD (menus) and File --> Open Disc --> DVD commands do not work. Nothing opens up at all when I use those commands. 

Thanks, 

-'Mage

---

### Post by AndThenWhat on 2008-06-20
I found a website that looks like it may be useful to you:

[http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback](http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback)

---

### Post by Bubba64 on 2008-06-21
> **UnWarierMage224 said:**
> Hi folks, 

I followed the instructions here to try to get DVD playback in ubuntu. I'm using Ubuntu 8.04. 

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

I followed the instructions, fired up Totem, and got a "Could not read from resource" error. I can see the DVD disc on my desktop and when I double click it, it opens. 

I have VLC installed as well and the File --> Open Disc --> DVD (menus) and File --> Open Disc --> DVD commands do not work. Nothing opens up at all when I use those commands. 

Thanks, 



-'Mage


[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
This will tell you about the Ubuntu restricted extras.
You also need the win32codes in synaptic, you may want to install the gstreamer extras in add remove, this gives you more gstreamer library stuff than your original instructions.

---

### Post by UnWarierMage224 on 2008-06-21
AndThenWhat, 

I followed the instructions at that website.
They did not get DVD playback working in totem, but they DID get DVD playback working in VLC, which is just fine for me. 
HOWEVER, video playback is still very choppy and the audio/video gets unsynced at times. 

What to do?

-'Mage

---

### Post by Pjotr123 on 2008-06-21
Disable visual effects:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )

---

