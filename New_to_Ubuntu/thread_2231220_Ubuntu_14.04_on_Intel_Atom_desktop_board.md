---
title: "Ubuntu 14.04 on Intel Atom desktop board"
date: 2014-06-24
forum: New to Ubuntu
---

### Post by pondweed on 2014-06-24
Hello, can someone help please.
I've Just installed Ubuntu 14.04 on an Intel D2550MUD2 desktop board which has Intel Graphics Media Accelerator 3650. By default it is unusable due to slow graphics updating. By that I mean if you open something like the file manager, it will fade in slow steps over a few seconds, and same when you close it. Any ideas where to start please.

In  windows I would check device manager to see if the graphics driver was installed and then check for updates if it was. With Linux/Ubuntu, I've no idea where to start. Thanks for any help.

---

### Post by grahammechanical on 2014-06-24
Hi

You can go to the power/cog menu and select About This Computer. That will take you to Details page and tell you about the graphics on your system. What does it say?
 
Ubuntu has a fall back open source video driver for graphic adapters that cannot provide hardware accelerated video rendering. The system sometimes falls back on this video driver. It attempts to provide an approximation of a 3D rendered user interface. It is noticeably slower than what we would expect from modern graphic adapters.

While you are at the Details page you can enter System Settings. Go to Software and Updates>Additional Drivers tab. Allow the utility time to do its work and you will be offered proprietary video drivers that you can experiment with to see if you can get a better user experience.

Regards.

---

### Post by pondweed on 2014-06-24
Thanks very much for replying and for the info, I appreciate it. Here are the results:

graphics: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)

no additional drivers available.
no proprietary drivers are in use

---

### Post by 3rdalbum on 2014-06-24
Wikipedia shows that this GPU is made by PowerVR, not by Intel. The Wikipedia article says there are no 3D drivers on Linux for this GPU, only some basic 2D support.

Ubuntu really does need 3D support, but some of the versions of Ubuntu with different desktop environments (Lubuntu, Kubuntu, Xubuntu) work perfectly well with only 2D support.

If you particularly want Ubuntu and not Xubuntu/Lubuntu, you can try the following two suggestions for speeding up Ubuntu's performance on your computer:

**Turn off transparency in the Dash**

1. Open the hidden file in your home directory called ".xprofile" (you can press Control-H to view hidden files) or create it if it doesn't exist.
2. At the bottom of the file, add the line "export UNITY_LOW_GFX_MODE=1"
3. Save your changes, log out and log back in

**Turn off window animations**

1. In the terminal, run these commands:

```
sudo apt-get install compizconfig-settings-manager
ccsm
```

This installs the Compizconfig program and then runs it.

2. Untick the boxes next to "Animations" and "Fading Windows". DO NOT CLICK ANYTHING ELSE.

---

### Post by pondweed on 2014-06-24
Thanks very much. I did as you suggest but it's still not useable, so I suppose I'll have to try one of the others. I was expecting someone to say that "Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)" was not correct for this graphics chipset. Does it seem like the right one? I read about a driver called "cedarview" for this chipset with regards to an older version of Ubuntu (12.something). Is that no longer applicable to this version?

---

### Post by pondweed on 2014-06-24
I've decided to take a loss and get rid of this board, I should have done more research before buying it. Thanks for all your help though.

---

### Post by verymadpip on 2014-06-24
Hi there.
Why not try out Xubuntu.
For the time & effort involved in downloading it & making a bootable USB it might be worth it.
Got to be cheaper than buiying a ne w mobo surely?

As an aside I run Xubuntu 14.04 on a netbook with the PowerVR chip (think mines a 3600 or a 3650) & it runs great.

---

### Post by pondweed on 2014-06-24
Okay, thanks, I'll give it a go and see what happens. I'm downloading now.

---

### Post by sandyd on 2014-06-24
Also check out lubuntu (which is in my opinion lighter than XFCE/Xubuntu)

---

### Post by pondweed on 2014-06-24
Xubuntu booting from USB, "display can't display this video mode..." message on monitor... haha, been here before a couple of years ago. I don't know why I keep coming back to try Linux. Anyway, I appreciate the help, but I've spent enough time on it now. Thanks again.

---

