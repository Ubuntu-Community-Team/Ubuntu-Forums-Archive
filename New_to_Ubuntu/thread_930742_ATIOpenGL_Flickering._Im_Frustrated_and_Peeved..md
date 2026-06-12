---
title: "ATI/OpenGL Flickering. Im Frustrated and Peeved."
date: 2008-09-26
forum: New to Ubuntu
---

### Post by kestal on 2008-09-26
So here it is. By far I love Ubuntu more than any other Linux Distro, but anything that is resource intensitive, flickers. Even screensavers. I am using a laptop with an ATI 9600 video card. (I know, old, but in no way should have these problems, especially with OpenGL).

I posted something about it and nobody replied (that actually read my whole post), so I was a bit frustrated. Any OpenGL programs flicker. 

I switched to Xscreensaver, it still flickers.

Turning off Compiz is not a solution to 'flickering', just a workaround which hinders the overall desktop experience. no matter what way you look at it. Other Distro's do not have this problem on my card.

Worst of all, this ONLY happens on Ubuntu. It happens on Xubuntu but not nearly as much (at a tolerable level), though I prefer gnome. OpenSuse = no flickering. Mandriva = No Flickering (but I dislike the distro). I prefer Ubuntu. What is it on Ubuntu that causes this? Im using 8.04.1 (fully updated) and I am upgraded to the ATI 8.5 driver.

Any ideas on how to fix?

---

### Post by markbuntu on 2008-09-26
ATI has fixed this problem with TexturedVideo in the 8.9 driver. But it is a workaround like every other graphics driver uses. The real fix will be when dri2 is released which will be in a few months hopefully.

---

### Post by Fatman_UK on 2008-09-26
Is there any news for NVIDIA users? (Or is it just me? :D )

Compiz sure is purty. But I just can't use it on my home system due to the flickering and occasional GDM crash.

Ah, well. At least I'll be able to enable it on my work system (ATI).

---

### Post by kestal on 2008-09-26
> **markbuntu said:**
> ATI has fixed this problem with TexturedVideo in the 8.9 driver. But it is a workaround like every other graphics driver uses. The real fix will be when dri2 is released which will be in a few months hopefully.

I was a bit too ambitious with my 2nd ubuntu partition while installing 8.9 right when it came out and I didn't install it properly, so I figured I'd wait a bit longer until the dust settles. But that was just me experimenting right as it was announced. 

About dri2, I figured it would have been released by now. They've been talking about it for a while... was it postponed or something?

If 8.9 does fix it, if anything, how? Do I need to get rid of the 3d desktop effects? I might try it again.

What ATI card do you have? Was it on a 32bit or 64bit system?

Thank you for the replies.

---

### Post by markbuntu on 2008-09-26
Actually, I have not tried the 8.9 driver yet and am using 8.8 on my i386 install and 8.6 on my amd64 install on the same machine with a HD36501GB card but even with the 8.6 driver I could get rid of most applications flickering by turning off TexturedVideo and still run compiz.

Anyway, there is something in the release notes for 8.9 about fixing the flickering caused by the TexturedVideo option and these notes are usually right on. The drivers ati releases are not betas, they are releases. They have their own closed testing program but they have put theselves on a pretty tight release schedule, every 5 weeks I think with 3 weeks of testing and bug fixing before release. 

You, and everyone else using these drivers should really read the release notes for them. There is a link to the release notes from the driver download page.

---

### Post by kewlito on 2008-10-22
The problem still exists with catalyst 8.10.

---

### Post by Buckwheat469 on 2008-11-17
Problem still occurs with ATI HD 3200 and any video (random flickering when screen changes, like if the analog clock hand moves on the desktop). 3D gameplay is horrible too. Compiz works fine. Problem also affects full screen applications, like Nexuiz or MythTV by making the screen vertically scrambled (run the video through a shredder, that's what it looks like). 

The fix for the shredded video is to start apps in windowed mode. It seems the screen has a problem with its visible area, so starting a screen at 1679x1023 works for me (one pixel off). The hard part is trying to find the command line switch to start it in windowed mode.

As for the flickering. I've sped up the card as much as possible with the below configuration. I've also contacted ATI support, but they state that the Linux drivers are As-Is and are not supported. After which I stated that they are playing favorites to Microsoft. I don't know if that goes against any court rulings about Microsoft's monopoly status, but I hope it does.

If anyone knows a switch that will make ATI video work without flickering, please let us know!

**XORG.CONF**

******
Other stuff not relevant
******

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	Option        "backingstore" "true"
	Option        "AllowGLXWithComposite" "true"
	##  Option "FSAAEnable" "off"
  	Option "Capabilities" "0×00000000"
  	Option "VideoOverlay" "on"
  	#Option "OpenGLOverlay" "off"
	##  Option "FSAAScale" "0"
  	#Option "XAANoOffscreenPixmaps" "true"
  	#Option "AllowGLXWithComposite" "true"
  	#Option "DisableGLXRootClipping" "true"
        Option "TexturedVideo" "on"
  	Option "TexturedVideoSync" "on"
	##Option         "XvmcUsesTextures" "True"
EndSection

******
Other stuff not relevant
******

Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by Buckwheat469 on 2009-01-30
Catalyst 9.1 fixed the issue, but I don't know if the additional config settings I did fixed it or if the new driver did (I forgot to check before doing the config)

Steps:

- Download and install Catalyst 9.1+ from AMD.
- Restart
- Open Terminal and type:
   ```
aticonfig --input=/etc/X11/xorg.conf --ovt opengl --ovon 0 --vs on
```

Happy viewing :popcorn:!

---

### Post by AndyM3 on 2009-02-01
Catalyst 9.1 didn't want to install. It installed 8.846 or something similar. My X is version 7.4, isn't that the latest?
The screensaver flickers like before, but now it also shows some white and pink strips. I'd like to post a screenshot, but I can't capture OpenGL applications.
This actually "fixed" video playback, which was also flickering. "Fixed" means it works in full screen, but in windowed mode some chunks of the Totem window turn into black.
I remember that I installed Elisa on my Eee and it was flickering. Disabling the desktop cube solved that problem. Well, it doesn't have the same result now. Also, my Eee is runing the latest Eeebuntu (I think it's basically 8.10) and it didn't flicker with Compiz, not even when the desktop cube is active.

P.S: My desktop is running Linux Mint 6. Would that cause incompatibility?

---

### Post by zika on 2009-02-01
> **Buckwheat469 said:**
> If anyone knows a switch that will make ATI video work without flickering, please let us know!
System->Preferences->MultiMedia_Systems_Selector->Video->X_Window_System(No Xv) works for me without any tinkering with aticonfig. worked with 8.12 and works with 9.1 (i.e. 8.561 and 8.573)

---

### Post by perixx on 2009-02-02
> aticonfig --input=/etc/X11/xorg.conf --ovt opengl --ovon 0 --vs on

No workie here (Xubuntu x64 Hardy), I've got fglrx 9.1 installed and working properly.
Mplayer will playback flicker-free in fullscreen-, but not in windowed mode. Certain OpenGL apps won't do flicker-free at all (e.g. freedroidRPG or naev), others will, like UT2004. Haven't checked wine yet, though.


perixx

---

### Post by sendblink23 on 2010-10-11
Honestly i gave up on ATI for linux usage.. decided to pop in my computer a cheap Nvidia card which works way better on it than how my CF 5770's ever did. Thank god my motherboard can hold 4 graphic cards(minor issue I need to switch the DVI cable when i plan on booting to the other OSes)... that way I'll just use the ATI's on Windows 7 for gaming & OSX... and just leave the Nvidia for linux.

---

### Post by zika on 2010-10-11
You reminded me of this thread.
Since my last message here I've gone to open-source drivers and never looked back. No more ATI drivers, for almost 20 months... :)
Try it.

---

### Post by perixx on 2010-10-17
> **zika said:**
> You reminded me of this thread.
Since my last message here I've gone to open-source drivers and never looked back. No more ATI drivers, for almost 20 months... :)
Try it.While this is true for 2D with newer distro's and older gcards (mine is a x1950gt and it runs perfectly out of the box), it's not quite for brand new gcards.
Also, open source 3D support is probably in a usable state around 11.04 via the improved Gallium3D implementation. At least with older cards.
 
Tried an Ati HD5670 two weeks ago and I just couldn't get accellerated 2D graphics with it, neither with the "radeon", nor with the "fglrx" driver. It was unusable. 

But it wasn't even to boot under XP with this card, so it's not quite sure, what the problem actually is: hardware or software? I suppose the card was defect or it's a vendor-specific problem. Maybe the 5xxx series is has yet some quirks. So, it went back to sender. I'll give it another try with a different card.

One thing to keep in mind is, that Nvidia's open source drivers are far behind those of Ati by now. So, currently Nvidia is only an option, if you fully rely on the proprietary drivers and are willing to buy a new card every time the product support ends. This may be true for tech enthusiasts and hardcore gamers, which use Windows mostly, anyway.

perixx

---

### Post by perixx on 2010-11-09
If it's true what they write on phoronix, the flickering issue should've been addressed from kernel version 2.6.35.1 upwards...

---

### Post by perixx on 2011-02-12
Just in case anyone needs to know:

Xubuntu 10.04 (LTS) - and maybe other desktops too - have a kernel too old for supporting Ati 5xxx series via open source drivers. This very likely also applies to other distros with kernels < 2.6.35.1. I've been using an Ati 5670 for about 3 months now - with the proprietary driver, until the next LTS version is out. Works like a charm.

You can easily install the driver by booting into the recovery shell and using the 'sgfxi' script. You need to 'wget' it first, of course, as described on this website (also from the shell):

[http://smxi.org/site/install.htm](http://smxi.org/site/install.htm)

Before starting it with the ```
sgfxi
```command (which will install the currently availible driver directly from Ati), you need to make sure the X-server is stopped by entering```
stop gdm
```
The rest is all done automatically, you just need to press [Enter] a few times, that's it. 
Oh, and, don't forget you have to use 'sgfxi' from the booted shell after a kernel update again, in order a new kernel module gets compiled and installed.

perixx

---

