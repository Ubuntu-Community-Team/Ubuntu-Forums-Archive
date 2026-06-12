---
title: "Anyone able to use Nvidia 173 drivers with Unity or GS?"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by haresear on 2011-09-25
I'm experimenting with how Oneiric beta2 and the 3.0 kernel runs on my Nvidia FX5200 graphics card. My card uses the Nvidia 173 drivers, and the only Nvidia drivers that I could get to install were those directly from Nvidia website (v 173.14.31). The drivers via jockey and the nvidia-173 drivers from Ubuntu repositories both failed to install.

Nvidia-settings seems to think that openGL is enabled with hardware acceleration, but Unity 3D and Gnome-shell won't run, so apparently something is missing. These results from "glxgears":

Unity 2D + Nvidia:                    ...............250 FPS
Gnome fallback + Nvidia: 1300 FPS
Unity 2D + nouveau:                   .............70 FPS

suggest that hardware openGL might be working with Gnome fallback, but is probably disabled with Unity 2D. Anyone know why that is? Anyone else had more success with the Nvidia 173 drivers?

---

### Post by Sworddragon on 2011-09-25
There is currently a bug that /usr/lib32/libGL.so, /usr/lib32/libGL.so.1 and /usr/lib32/libGL.so.1.2 are pointing to the libGL files in the mesa subfolder but they should point to the libGL files in the nvidia-current subfolder.

---

### Post by cmccauley on 2011-09-26
> **haresear said:**
> 
Nvidia-settings seems to think that openGL is enabled with hardware acceleration, but Unity 3D and Gnome-shell won't run, so apparently something is missing. These results from "glxgears":

Unity 2D + Nvidia:                    ...............250 FPS
Gnome fallback + Nvidia: 1300 FPS
Unity 2D + nouveau:                   .............70 FPS

 Anyone else had more success with the Nvidia 173 drivers?


Hi,

Not answering your question directly - maybe you can't upgrade to a newer driver. 
 
My card is an 8700M GT and I'm using the 280.13 driver (according to nvidia-settings).

18420 frames in 5.0 seconds = 3683.930 FPS
20021 frames in 5.0 seconds = 4004.075 FPS
20197 frames in 5.0 seconds = 4039.309 FPS
19896 frames in 5.0 seconds = 3979.189 FPS
20105 frames in 5.0 seconds = 4020.891 FPS

Chris

---

### Post by haresear on 2011-09-26
As far as I understand, driver versions above 173 don't support my FX5200 card.

---

### Post by effenberg0x0 on 2011-09-26
> 
Unity 2D + Nvidia:                    ...............250 FPS
Gnome fallback + Nvidia: 1300 FPS
Unity 2D + nouveau:                   .............70 FPS
The 2D version is targeted at systems that do not support OpenGL. Your does.
What about the results for the standard Ubuntu (not Ubuntu 2D) login option? Are there no results / worst results / similar results or you just can't even login to the session right now?

Have you tried purging / reinstalling Unity / Compiz / NVidia? If not, it would go like this:

Switch to a VT (ctrl+alt+f2 to f6), login, and run these: (not at terminal window):
```

sudo service lightdm stop
sudo apt-get remove --purge compiz compizconfig-backend-gconf compizconfig-backend-kconfig compizconfig-settings-manager compiz-core compiz-fusion-bcop compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-kde compiz-plugins compiz-plugins-extra compiz-plugins-main unity unity-2d unity-2d-default-settings unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread unity-asset-pool unity-common unity-place-applications unity-place-files nvclock nvclock-gtk nvclock-qt nvidia-173 nvidia-173-dev nvidia-173-kernel-source nvidia-180-kernel-source nvidia-180-libvdpau nvidia-180-modaliases nvidia-185-kernel-source nvidia-185-libvdpau nvidia-185-libvdpau-dev nvidia-96 nvidia-96-dev nvidia-96-kernel-source nvidia-cg-toolkit nvidia-common nvidia-current nvidia-current nvidia-current-dev nvidia-glx-173 nvidia-glx-173-dev nvidia-glx-180 nvidia-glx-180-dev nvidia-glx-185-dev nvidia-glx-96 nvidia-glx-96-dev nvidia-settings 
cd ~
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.31/NVIDIA-Linux-x86-173.14.31-pkg1.run
sudo chmod +x NVIDIA-Linux-x86-173.14.31-pkg1.run
sudo ./NVIDIA-Linux-x86-173.14.31-pkg1.run
sudo apt-get update && sudo apt-get upgrade
sudo reboot now

```At the lightdm login screen, click the gear icon to make sure you are gonna login to Ubuntu, not Ubuntu 2D.
Inside Ubuntu (Unity 3D), if you have no panel or launcher, switch to a VT (ctrl+alt+f2 to f6), login, and run:
```

DISPLAY=:0.0 ccsm

```Press ctrl+alt+F7 to get back to desktop and check that ccsm has "Composite", "OpenGL" and "Ubuntu Unity Plugin" activated. It may crash, window decorations may disappear, clicking and focus may stop working (known bug while activating/deactivating plugins). If it does, switch again to a VT and run:

```

sudo service lightdm restart

```At this point, you should have a working Ubuntu, Compiz, OpenGL-enabled Unity Session, which you can customize with ccsm (icon sizes, behaviors, etc - knowing that ccsm and the session might crash while you do so).

Regards,
Effenberg

---

### Post by lucazade on 2011-09-26
To check if your system can handle Unity try this test:


```
/usr/lib/nux/unity_support_test -p

```

this is what I get on nutty...
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTS 250/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 270.41.06

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

Unity supported:          yes

---

### Post by haresear on 2011-09-26
> **effenberg0x0 said:**
> The 2D version is targeted at systems that do not support OpenGL. Your does.
What about the results for the standard Ubuntu (not Ubuntu 2D) login option? Are there no results / worst results / similar results or you just can't even login to the session right now?


As I said in post #1, Unity (3D) won't run -- defaults to Unity 2D.

@lucazade: Thanks for the tip, that might be interesting

```
$/usr/lib/nux/unity_support_test -p
[OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
```Can't see why Unity thinks nvidia driver is blacklisted:
```

$ grep nvidia /etc/modprobe.d/*.conf
blacklist-framebuffer.conf:blacklist nvidiafb
nvidia-graphics-drivers.conf:# This file was installed by nvidia-173-updates
nvidia-graphics-drivers.conf:blacklist nvidia-current
nvidia-graphics-drivers.conf:blacklist nvidia-173
nvidia-graphics-drivers.conf:blacklist nvidia-96
nvidia-graphics-drivers.conf:blacklist nvidia-current-updates
nvidia-graphics-drivers.conf:blacklist nvidia-96-updates
nvidia-graphics-drivers.conf:alias nvidia nvidia-173-updates

```

---

### Post by haresear on 2011-09-26
> **Sworddragon said:**
> There is currently a bug that /usr/lib32/libGL.so, /usr/lib32/libGL.so.1 and /usr/lib32/libGL.so.1.2 are pointing to the libGL files in the mesa subfolder but they should point to the libGL files in the nvidia-current subfolder.

Well this raises some interesting questions:

If I install the Nvidia website drivers 173.14.31 manually, then these files are in /usr/lib/, and there is no /user/lib32/ directory.

If I install the Ubuntu nvidia-173 drivers (173.14.30), then these files don't exist at all (at least I couldn't find them). There is, however, now a /usr/lib32/nvidia-173/ directory with some other libGLxxx.so files, but no libGL.so* files. (I found that I can install nvidia-173 if I start clean, and don't try to use jockey first.) CORRECTION: libGL.so and libGL.so.1 do exist in the /usr/lib/nvidia-173/ directory. The /usr/lib32/nvidia-173 directory is empty.

Both these driver installs behave the same as I described in OP.

---

### Post by mrkennie on 2011-09-26
Do not rely on glxgears, it's not meant for benchmarking. A much more reliable test would be using something like OpenArena.

---

### Post by lucazade on 2011-09-26
> **haresear said:**
> As I said in post #1, Unity (3D) won't run -- defaults to Unity 2D.

@lucazade: Thanks for the tip, that might be interesting

```
$/usr/lib/nux/unity_support_test -p
[OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
```Can't see why Unity thinks nvidia driver is blacklisted:
```

$ grep nvidia /etc/modprobe.d/*.conf
blacklist-framebuffer.conf:blacklist nvidiafb
nvidia-graphics-drivers.conf:# This file was installed by nvidia-173-updates
nvidia-graphics-drivers.conf:blacklist nvidia-current
nvidia-graphics-drivers.conf:blacklist nvidia-173
nvidia-graphics-drivers.conf:blacklist nvidia-96
nvidia-graphics-drivers.conf:blacklist nvidia-current-updates
nvidia-graphics-drivers.conf:blacklist nvidia-96-updates
nvidia-graphics-drivers.conf:alias nvidia nvidia-173-updates

```

unity blacklist is different from blacklisting kernel modules, so you won't find it in /etc/modprobe.d/...

there is a blacklist inside nux, a core component of unity... here is a snippet of it:

```
tools/unity_support_test.c
7171// Blacklists of GPUs for Compiz.
7272struct PciDevice gpu_blacklist[] = {
7373  { 0x8086, 0x3577 },  // Intel : 82830M/MG
74   { 0x8086, 0x2562 }   // Intel : 82845G aka Poulsbo
 74  { 0x8086, 0x2562 },  // Intel : 82845G aka Poulsbo
 75  { 0x1002, 0x4c57 }   // ATI : Radeon Mobility 7500
7576};
7677 
7778// Checks whether an extension is supported by the GLX/OpenGL implementation
```
(taken from here: [http://bazaar.launchpad.net/~didrocks/nux/blacklist-readon-mobility/revision/325](http://bazaar.launchpad.net/~didrocks/nux/blacklist-readon-mobility/revision/325) )

don't know if there is a simple way to remove a card from the list without compiling and modifying this package by hand.

---

### Post by haresear on 2011-09-26
During my experiments with the Nvidia drivers, I've noticed that no matter what desktop I'm running, I get repeated popups notifying of various crashes of system components -- "unity 2d panel" is a frequent crash message (even when I'm running the gnome fallback desktop). I think I've probably wasted enough time on this for the time being. It seems pretty clear that the current Nvidia 173 drivers don't work well with the 3.0 kernel even when they can be installed. UPDATE: Actually I now see the same behavior with the nouveau drivers after a clean HD install, so 11.10 just isn't working well for me with any drivers.

PS - I ran the unity_test script with the nouveau drivers, and it came back with all "yes" for Unity 3D support, but can only display a blank white desktop. (This is only after a HD install -- on the liveCD, the Unity 3D test is negative.)

---

### Post by haresear on 2011-09-28
Just a final update before wrapping up this thread.

1. With the hint from lucazade, I was able to find a workaround for the Unity blacklisting, and managed to start Unity 3D. Although Unity seems to function, compiz uses 95% CPU even at idle, so everything happens in agonizingly slow motion (except for the mouse cursor). The only thing I found to be non-functional is that the Unity panel icons are invisible (but respond to mouse clicks). 

2. Although Unity 2D is functional it feels sluggish -- e.g. takes a couple of seconds for the Dash panel to come up.

3. Gnome-shell crashes within a few seconds of starting.

4. Gnome-fallback seems to function normally and feels responsive.

5. "System error" and "System program error" popups occur repeatedly while running any of the above four desktops.

6. Xubuntu-desktop functions normally and feels responsive -- it basically feels the same as Xubuntu 11.04. (No error popups.)

---

