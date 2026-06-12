---
title: "Extremely Poor Performance - Ubuntu 14.04 on Dell Mini 1010"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by camillo2 on 2014-06-04
HELLO & Thanks for the Welcone.  

I am a brand new Linux User - tho with considerable prior use of Windows and Chrome OS.

I have read all of the Forum Stickys and other sources; none of which is very encouraging; I don;t know where to go from here.

My machine [Dell Inspiron Mini 1010] uses the 'popular' integrated Intel (Poulsbo) graphics card and HD Audio Sound. I installed 14.04 about three weeks ago. The installation went smoothly, but Graphics are very very slow, and sound is extremely distorted.

Suggested next steps would be much appreciated.

Here are more details on my configuration as returned by a <inxi> query.

AND - Thanks in advance.

/Camillo

=====================

[FONT=arial][LEFT][FONT=FreeSans, serif]Graphics: Card: Intel System Controller Hub (SCH Poulsbo) Graphics Controller bus-ID: 00:02.0[/FONT][/FONT][/LEFT][FONT=arial][LEFT][FONT=FreeSans, serif]X.Org: 1.15.1 drivers: (unloaded: fbdev,vesa) Resolution: 1366x768@39.5hz[/FONT][/FONT][/LEFT][FONT=arial][LEFT][FONT=FreeSans, serif]GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits) GLX Version: 2.1 Mesa 10.1.0 Direct Rendering: Yes[/FONT][/FONT][/LEFT][FONT=arial][LEFT]
[/FONT][/LEFT][FONT=arial][LEFT][FONT=FreeSans, serif]Audio: Card: Intel System Controller Hub (SCH Poulsbo) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0[/FONT][/FONT][/LEFT][FONT=arial][LEFT][FONT=FreeSans, serif]Sound: Advanced Linux Sound Architecture ver: k3.13.0-[/FONT][/FONT][/LEFT]
=====================

---

### Post by TheFu on 2014-06-04
The choices are:
* Install a lighter desktop - like XFCE4 or LXDE and use it instead of Unity.
* Install better graphics drivers that fully support the GPU available - not very likely.

On Linux/UNIX systems, the "environment" is just another program. It is NOT the OS. Swapping out the GUI layer for something lighter takes 3-5 minutes, then just select the other GUI on the login page - click on the "gear" to see the options after installing an alternate.  

I don't know **anything** about Dell Minis - had an Asus Eee from 2009 and the video performance sucked - couldn't handle playback of any videos over 480p in resolution.  I decided to run  LXDE instead of Unity which worked great until 3 months ago when I upgraded to a current-Gen chromebook ($211), dropped Ubuntu 14.04 LXDE onto it and never looked back. My new system handles 1080p videos easily - because the more recent systems have better video support and a comparatively VERY FAST CPU, plus the automatically loaded Intel drivers sorta "just work." Couldn't comment on ChromeOS performance on the machine - ran it once enough to get a legacy boot to work and wiped it.  If I were doing it again, I'd get a Dell 11inch laptop with the same CPU (and many, many more upgrade capabilities) - they were on sale for $280 over Xmas.

Reading your signature has me thinking that you completely understand the driver issue.

Things that appear similar to Windows usually are NOT the same under the covers in Linux and ChromeOS so very limiting ... well - you already know that.

---

### Post by grahammechanical on 2014-06-04
> [COLOR=#000000][FONT=FreeSans]Gallium 0.4 on llvmpipe[/FONT][/COLOR]

That is an open source video driver that Ubuntu uses to fall back on if the graphic adapter cannot run Unity. We also get llvmpipe if there is some incompatibility with  proprietary video drivers or when we run Recovery mode>Resume. 

If Ubuntu was running of the "full" open source video driver (Nouveau) then the Details page would simply say "Gallium 0.4 on ..."

You can try experimenting with video drivers. You can run this command to see if the graphic adapter supports Unity

```
/usr/lib/nux/unity_support_test -p
```

This is what I see when I run that test code

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.1.3


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes


By the way, NVA5 is an Nvidia code for my Nvidia graphic adapter.

Regards.

---

### Post by camillo2 on 2014-06-07
Without any further suggestions - and considering my limited linux expertise, I think I will try loading a lighter configuration.

---

### Post by TheFu on 2014-06-07
> **camillo2 said:**
> Without any further suggestions - and considering my limited linux expertise, I think I will try loading a lighter configuration.

All you need to do for this is
* sudo aptitude update
* sudo aptitude install lxde
* logout
* On the login page, click the "gear", select LXDE
* Login as normal
Be happy.
Should take 3-5 min.

No need to reinstall the OS.  You can clean up storage from Unity later.

---

### Post by camillo2 on 2014-06-10
[COLOR=#000000]TheFu said:
All you need to do for this is[/COLOR]
[COLOR=#000000]* sudo aptitude update[/COLOR]
[COLOR=#000000]* sudo aptitude install lxde[/COLOR]
[COLOR=#000000]* logout

BUT:
"sudo aptitude update"  returns "no such command aptitude"


[/COLOR]

---

### Post by TheFu on 2014-06-10
Then insert "sudo apt-get install aptitude" at the beginning of the steps.
Aptitude has been recommended by Debian developers for years, because it is smarter about dependencies and can solve some dependency problems that other front-ends to APT cannot.

Whenever you see "no such command" .... that is a hint to install it ... provided you know what the command does. Google can help with that. No need to wait for a response on a blog/forums to learn.

---

### Post by camillo2 on 2014-06-16
Thanx "TheFu" for your suggestions - the general gist of the suggestions was very helpful.

But after about 2 months of exasperation with Ubuntu 14 on the Dell Mini, I thought I would give Lubuntu a try.

SURPRISE ! It worked very well right out of the box!  So far I am enjoying good graphics and Audio - Haven't tried video as yet. The distribution has Gallium 0.4 installed.

I am developing a bit more experience and confidence now and may try other desktops as time permits.

In the meantime, if there is anyone out there with linux on a Dell Mini [Inspiron] I would be happy to hear of their experience with that box.

Thanks again to TheFu and to Grahammechanical for their help and encouragement.

---

