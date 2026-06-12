---
title: "Help with updating intel graphics driver"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by Ponchielli on 2012-09-24
Hi, I'm new to the forum and I've being using Ubuntu for 2 years now but I still don't understand a lot of things. So I thought of asking for help here. The problem is I'm trying to run dota2 using wine, but I can't play any game I try to install on this pc and it's always because of the video card. So I have to either try to update the drivers or buy a new card. I want to try updating the drivers because I'm not sure if I want to spend money on hardware just to play this game. I have no clue on what I have to do to update the drivers. The intel website says I have to go to this website [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) which is not beginner friendly at all...     What I have is this:   Intel® Core™2 Duo CPU E7200 @ 2.53GHz × 2   Intel® G33 x86/MMX/SSE2 Ubuntu 12.04    And the requirements for the game Processor:  Pentium 4 3.0GHz  Graphics: DirectX 9 compatible video card with 128 MB, Shader model 2.0. ATI X800, NVidia 6600 or better     So, can I run it on my pc? And how do I update the drivers?!? Please help!

---

### Post by Ponchielli on 2012-10-02
I've found a tutorial on this website on how to update the drivers [http://www.ivankristianto.com/os/ubuntu/install-intel-latest-driver-to-your-ubuntu-10-04/1278/](http://www.ivankristianto.com/os/ubuntu/install-intel-latest-driver-to-your-ubuntu-10-04/1278/)  Should I try doing it? I couldn't find anything else on the internet about this. Can someone that understand about this please help? It would be much appreciated. Thanks.

---

### Post by BicyclerBoy on 2012-10-02
That article is old & directed at 10.04..
Actually most of it will probably still work in 12.04..

xorg-edgers ppa has the latest intel drivers (& kernel). This is only useful for the later gen intel graphics.

But with old intel chipset graphics G33 G43 it is very likely pointless.
The nVidia 6600 is prob 10x better than G33..

Wine has to convert win directx/directdraw to native openGL. 
There are numerous potential problems running games in Wine.

It is a good idea to search winehq game database & try to follow any instructions.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13522](http://appdb.winehq.org/objectManager.php?sClass=application&iId=13522)

---

### Post by Ponchielli on 2012-10-03
First of all thanks very much for the reply.
I looked in the wine website but just as in any other site in the internet that talks about this, the only solutions apparently are to either update the drivers or to buy a new video card. 


About what you said: "Wine has to convert win directx/directdraw to native openGL.", is there a way to check if wine is doing this correctly? I would like to at least make sure that all else is working fine before I completely give up on trying to run this game on my computer. 

At least the game menu now works fine with the launch settings -window and -nod3d9ex. Does this make sure that opengl is working fine?

Thanks again!

---

### Post by BicyclerBoy on 2012-10-04
You can check the OpenGL rendering in linux

glxinfo | grep OpenGL
glxgears

There are clues in the first cmd to check for software rasteriser (bad)

You can check dx in wine by running std windows test prog "dxdiag"; run the direct draw d3d tests.

I know nothing about your game title or its cmd line options..
I guess the -nod3d9ex stops it trying to use directx9 API.

---

### Post by NikTh on 2012-10-04
Ubuntu with Unity has another diagnostic tool (OpenGL included). 

```
/usr/lib/nux/unity_support_test -p
``` 

I assume this is problem with wine (?)

---

### Post by mips on 2012-10-04
> **Ponchielli said:**
> What I have is this:   Intel® Core™2 Duo CPU E7200 @ 2.53GHz × 2   **Intel® G33** 

Not sure what IGP chipset that MB has but the latest Intel drivers are here,

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Just add the PPA, update & install.

---

### Post by Ponchielli on 2012-10-04
The opengl gears worked fine, dx seems to be normal. The command line "/usr/lib/nux/unity_support_test -p" resulted in:  " OpenGL vendor string:   Tungsten Graphics, Inc OpenGL renderer string: Mesa DRI Intel(R) G33 x86/MMX/SSE2 OpenGL version string:  1.4 Mesa 8.0.2  Not software rendered:    yes Not blacklisted:          yes GLX fbconfig:             yes GLX texture from pixmap:  yes GL npot or rect textures: yes GL vertex program:        yes GL fragment program:      yes GL vertex buffer object:  yes GL framebuffer object:    yes GL version is 1.4+:       yes  Unity 3D supported:       yes"  So I supposed all is fine as well. And I tried installing the ppa but it didn't work, I had to remove it later with app purge because there were a few problems with my desktop. I'm not sure if this is a problem with wine or the video card, because other games have similar problems also. But I guess there is nothing else to do?  Thanks for help anyway!

---

### Post by NikTh on 2012-10-04
So I asked if this is a wine problem , cuz I have no big experience with wine. Maybe wants an adjustment for take full advantage of you G.Card's capability .. don't know. 

You can try to find help in wine's forum too , If you want. : [http://forum.winehq.org/](http://forum.winehq.org/)

OR you can give it a try in ubuntu-2d session. (lighter). 
From login screen and at login box , click on little Ubuntu Icon and select "ubuntu-2d" and see.

Thanks

---

### Post by Ponchielli on 2012-10-10
Sorry for the late reply. 

I'll give it a try thank you.

---

