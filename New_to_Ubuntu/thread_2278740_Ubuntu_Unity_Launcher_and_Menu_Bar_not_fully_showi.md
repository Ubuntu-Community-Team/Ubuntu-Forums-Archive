---
title: "Ubuntu Unity Launcher and Menu Bar not fully showing"
date: 2015-05-18
forum: New to Ubuntu
---

### Post by BrokenZilence on 2015-05-18
Yesterday I installed Ubuntu 15.04 on a 250gb partition on my hardrive with windows on another partition. When I first booted into Ubuntu after installed and troubleshooting a grub launch error, I noticed that my applauncher and menu bar were barely showing. As if my desktop was zoomed in( heres what I mean [https://drive.google.com/open?id=0Bx35G5aZ4cjZa1g0N0JVMkU4MTg&authuser=0](https://drive.google.com/open?id=0Bx35G5aZ4cjZa1g0N0JVMkU4MTg&authuser=0) ). However before installing during the test drive everything was perfectly normal. Ive tried everything on the forums so far dealing with Unity problems with it not showing and such. However its not mine isn't showing, its just partially hidden. Does anyone have a fix for this or should I resort to re-installing and trying my luck with that?


Thanks
    ~BrokenZilence

---

### Post by Vladlenin5000 on 2015-05-18
Hi and welcome.

No wonder you couldn't find a solution: You were looking for something to do with the launcher and your problem has nothing to do with it.
It's just overscan, a TV feature, nothing to do with Ubuntu. Preferably, you should correct it with the TV settings: Search for TV modes, overscan/underscan, PC mode, etc. etc. in your TV menus. Assuming you already set the correct resolution, one of the modes - and only one - will be just right. 
If you don't have/can't find such settings, then you must do it from the system. Depending on the graphics card/chip and driver you have it can be quite simple or not so easy. Post such details so we can suggest something in case you can't do it from the TV.

---

### Post by BrokenZilence on 2015-05-18
> **Vladlenin5000 said:**
> Hi and welcome.

No wonder you couldn't find a solution: You were looking for something to do with the launcher and your problem has nothing to do with it.
It's just overscan, a TV feature, nothing to do with Ubuntu. Preferably, you should correct it with the TV settings: Search for TV modes, overscan/underscan, PC mode, etc. etc. in your TV menus. Assuming you already set the correct resolution, one of the modes - and only one - will be just right. 
If you don't have/can't find such settings, then you must do it from the system. Depending on the graphics card/chip and driver you have it can be quite simple or not so easy. Post such details so we can suggest something in case you can't do it from the TV.

Ohh thanks for the quick response, I guess it was a Nvidia issue as my monitor lacks such options. My windows Os I use primarily for Gaming and I got Ubuntu to use as a video editing/graphics design OS. In windows I use 1600x1200 4:3 resolution. And I'm wanting to do 1920:1080 16:9 on Ubuntu for better look at what im working on so its not stretched to my screen like the 1600 resolution is. So I just set my Ubuntu Resolution down to 1600x1200 and it looks okay now. I guess Ill just have to find a better fix for this in the future as I really don't want it to use the same resolution.

At least it looks ok for now, Thank you.
   ~BrokenZIlence

---

### Post by Vladlenin5000 on 2015-05-18
It isn't a OS issue and neither a Nvidia issue. Not having those settings in the TV (and it overscanning by default anyway) it just means a lazy/cheap TV manufacturer. 
Considering you have Nvidia, if you installed the proprietary drivers (you probably did) then:

1. Open "NVIDIA X Server Settings" (search in dash)
2. Adjust the resolution back to the recommend (maximum) for your output device (TV) or use "Auto" in X Server Display Configuration.
3. In the same page/windows you'll find **underscan** with a slider to the right.

Simply push it a little bit, apply, and check how it looks. Repeat until it covers the screen area entirely without bleeding out.
Obs.: You can use the save to file feature. Then you can use that file to get the settings back in case of a fresh install, upgrade, etc.

PS. Changing the resolution isn't a solution. At best it's an ugly & amateurish "workaround".

---

