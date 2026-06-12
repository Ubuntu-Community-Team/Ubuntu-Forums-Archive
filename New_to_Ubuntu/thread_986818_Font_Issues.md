---
title: "Font Issues"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by TaintedBllack on 2008-11-18
Hi, I tried posting about this before but didn't get any responses at all. So I will try again. I have searched all over and haven't found anything relating to this subject, but maybe I am just searching for all the wrong terms.

Well my problem is that in a lot applications the fonts won't show up properly. I am using Ubuntu 8.10

Here is an example of the issue:

[http://img180.imageshack.us/my.php?image=screenshotjd2.png]("http://img180.imageshack.us/my.php?image=screenshotjd2.png")

This only happens in non gtk apps. Any help would be greatly appreciated.

---

### Post by nhasian on 2008-11-19
give this command in a terminal a try:

```
sudo dpkg-reconfigure gnome-desktop-data gnome-control-center gnome-menus gnome-system-tools gnome-applets gnome-session
```

---

### Post by TaintedBllack on 2008-11-19
> **nhasian said:**
> give this command in a terminal a try:

```
sudo dpkg-reconfigure gnome-desktop-data gnome-control-center gnome-menus gnome-system-tools gnome-applets gnome-session
```

Just tried it.. Still having the same issue. Any more suggestions?

---

### Post by TaintedBllack on 2008-11-19
Please help with this.

---

### Post by nhasian on 2008-11-19
i'm out of ideas.  Can you tell me when this problem started happening?  Were there any changes to the system that you can think of that might have affected the fonts?

---

### Post by TaintedBllack on 2008-11-19
Tried a fresh install and still having the same problem.

---

### Post by Therion on 2008-11-19
Try changing themes.  

Does the problem persist under "default" themes such as Human Clearlooks and/or BlueBuntu instance?

---

### Post by starcannon on 2008-11-19
This happened to me using compiz quite a while back, though I haven't seen it happen lately. Perhaps try turning off desktop effects and see what happens, if that makes the screen decorations come back, then one can start solving the problem of compiz messing them up; as I think on it a bit more, it seemed that for me it was a compiz with emerald problem, but I could be dismembering wrongly as it was quite some time ago.

---

### Post by TaintedBllack on 2008-11-19
With desktop effects disabled I now get this: (font in amarok now working just fine, but still not with wine)

[http://img440.imageshack.us/my.php?image=screenshotuh9.png]("http://img440.imageshack.us/my.php?image=screenshotuh9.png")


and the same thing happens with any theme.

---

### Post by Elfy on 2008-11-19
Try to disable antialiasing - it apparently works for nvidia cards, I had the same issue with 'scribbled' out fonts.

[http://www.nvnews.net/vbulletin/showthread.php?t=122178](http://www.nvnews.net/vbulletin/showthread.php?t=122178)

Someone in the same thread reports the font missing thing - I eventually got mine dealt with by a clean install and not using my old /home.

---

### Post by starcannon on 2008-11-19
Wine uses the ms core fonts doesn't it? I can't remember for certain.

Lets try getting a few packages installed:

Enable Medibuntu if you have not done so already:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then
```
sudo apt-get install ubuntu-restricted-extras
```

its a biggish download, but keep an eye on it from time to time, at some point some eula screens will need you to click that you agree. The ms core fonts are in that package as well as a bunch of other good stuff you'll want anyway.

---

### Post by TaintedBllack on 2008-11-19
> **starcannon said:**
> Wine uses the ms core fonts doesn't it? I can't remember for certain.

Lets try getting a few packages installed:

Enable Medibuntu if you have not done so already:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then
```
sudo apt-get install ubuntu-restricted-extras
```

its a biggish download, but keep an eye on it from time to time, at some point some eula screens will need you to click that you agree. The ms core fonts are in that package as well as a bunch of other good stuff you'll want anyway.

Already have that and the ms core fonts installed.

---

### Post by TaintedBllack on 2008-11-19
> **forestpixie said:**
> Try to disable antialiasing - it apparently works for nvidia cards, I had the same issue with 'scribbled' out fonts.

[http://www.nvnews.net/vbulletin/showthread.php?t=122178](http://www.nvnews.net/vbulletin/showthread.php?t=122178)

Someone in the same thread reports the font missing thing - I eventually got mine dealt with by a clean install and not using my old /home.

How do I enable/disable antialiasing?

---

### Post by starcannon on 2008-11-19
Regarding the quoted post by forestpixie, if what he/she meant was that they assumed the problem to be one of the user config files, then one could try nuking them back to default.

Got to:
Places>Home

Press:
Ctrl+H

Send to the trashcan:

[LIST]
[*].gconf
[*].gconfd
[*].config
[*].fontconfig
[*].gnome2
[*].gnome2_private
[*].nautilus
[/LIST]
Reboot the machine, a new default set of those files will be create, you can always retrieve them from the trash can (so long as you didn't empty it) if you need one of them back for any reason.

You can mess with some of the font settings by going to:
System>Preferences>Appearance: and click on the Fonts tab, I really like the way the Subpixel Smoothing (LCD) option looks on my laptops and desktop LCD's.

Other than that, reading around in that forum you referred to, you may be able to do some xorg.conf file hacking, though I would be uncertain where to start for something like this.

---

### Post by starcannon on 2008-11-19
The nvidia driver readme file is available here:
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.07/README/README.txt](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.07/README/README.txt)

The section that looks particularly interesting considering the nv forum post you referred to is: 
```

Appendix E. OpenGL Environment Variable Settings
______________________________________________________________________________

FULL SCENE ANTIALIASING

Antialiasing is a technique used to smooth the edges of objects in a scene to
reduce the jagged "stairstep" effect that sometimes appears. Full-scene
antialiasing is supported on GeForce or newer hardware. By setting the
appropriate environment variable, you can enable full-scene antialiasing in
any OpenGL application on these GPUs.

Several antialiasing methods are available and you can select between them by
setting the __GL_FSAA_MODE environment variable appropriately. Note that
increasing the number of samples taken during FSAA rendering may decrease
performance.

The following tables describe the possible values for __GL_FSAA_MODE and the
effects that they have on various NVIDIA GPUs.



    __GL_FSAA_MODE     GeForce, GeForce2, Quadro, and Quadro2 Pro
    ---------------    ------------------------------------------------------
    0                  FSAA disabled
    1                  FSAA disabled
    2                  FSAA disabled
    3                  1.5 x 1.5 Supersampling
    4                  2 x 2 Supersampling
    5                  FSAA disabled
    6                  FSAA disabled
    7                  FSAA disabled




    __GL_FSAA_MODE     GeForce4 MX, GeForce4 4xx Go, Quadro4 380,550,580
                       XGL, and Quadro4 NVS
    ---------------    ------------------------------------------------------
    0                  FSAA disabled
    1                  2x Bilinear Multisampling
    2                  2x Quincunx Multisampling
    3                  FSAA disabled
    4                  2 x 2 Supersampling
    5                  FSAA disabled
    6                  FSAA disabled
    7                  FSAA disabled




    __GL_FSAA_MODE     GeForce3, Quadro DCC, GeForce4 Ti, GeForce4 4200 Go,
                       and Quadro4 700,750,780,900,980 XGL
    ---------------    ------------------------------------------------------
    0                  FSAA disabled
    1                  2x Bilinear Multisampling
    2                  2x Quincunx Multisampling
    3                  FSAA disabled
    4                  4x Bilinear Multisampling
    5                  4x Gaussian Multisampling
    6                  2x Bilinear Multisampling by 4x Supersampling
    7                  FSAA disabled




    __GL_FSAA_MODE     GeForce FX, GeForce 6xxx, GeForce 7xxx, Quadro FX
    ---------------    ------------------------------------------------------
    0                  FSAA disabled
    1                  2x Bilinear Multisampling
    2                  2x Quincunx Multisampling
    3                  FSAA disabled
    4                  4x Bilinear Multisampling
    5                  4x Gaussian Multisampling
    6                  2x Bilinear Multisampling by 4x Supersampling
    7                  4x Bilinear Multisampling by 4x Supersampling
    8                  4x Bilinear Multisampling by 2x Supersampling
                       (available on GeForce FX and later GPUs; not
                       available on Quadro GPUs)


ANISOTROPIC TEXTURE FILTERING

Automatic anisotropic texture filtering can be enabled by setting the
environment variable __GL_LOG_MAX_ANISO. The possible values are:

    __GL_LOG_MAX_ANISO                    Filtering Type
    ----------------------------------    ----------------------------------
    0                                     No anisotropic filtering
    1                                     2x anisotropic filtering
    2                                     4x anisotropic filtering
    3                                     8x anisotropic filtering
    4                                     16x anisotropic filtering

4x and greater are only available on GeForce3 or newer GPUs; 16x is only
available on GeForce 6800 or newer GPUs.

VBLANK SYNCING

Setting the environment variable __GL_SYNC_TO_VBLANK to a non-zero value will
force glXSwapBuffers to sync to your monitor's vertical refresh (perform a
swap only during the vertical blanking period).

When using __GL_SYNC_TO_VBLANK with TwinView, OpenGL can only sync to one of
the display devices; this may cause tearing corruption on the display device
to which OpenGL is not syncing. You can use the environment variable
__GL_SYNC_DISPLAY_DEVICE to specify to which display device OpenGL should
sync. You should set this environment variable to the name of a display
device; for example "CRT-1". Please look for the line "Connected display
device(s):" in your X log file for a list of the display devices present and
their names. You may also find it useful to review Appendix G (Configuring
Twinview) and the section on Ensuring Identical Mode Timings in Appendix J.

DISABLING CPU-SPECIFIC FEATURES

Setting the environment variable __GL_FORCE_GENERIC_CPU to a non-zero value
will inhibit the use of CPU-specific features such as MMX, SSE, or 3DNOW!. Use
of this option may result in performance loss.

CONTROLLING FORK(2) HANDLING BEHAVIOR

In order to clean up and reinitialize system resources the NVIDIA OpenGL
implementation needs to be aware of fork(2) system calls. The mechanism used
by the NVIDIA OpenGL implementation to detect fork(2) system calls does not
work well on systems using the LinuxThreads implementation of pthreads. For
thread safety the NVIDIA OpenGL implementation disables its fork(2) detection
on LinuxThreads-based systems. Setting the environment variable
__GL_ALWAYS_HANDLE_FORK to a non-zero value will enable fork(2) detection on
all systems. Setting the environment variable __GL_ALWAYS_HANDLE_FORK will
reduce thread safety on LinuxThreads-based systems. It is strongly recommended
to only set the __GL_ALWAYS_HANDLE_FORK environment variable when running
single threaded applications that are known to use fork.
```

I'm not sure what Option line to put in but hopefully this will at least get you looking in the right direction.

GL keep asking, someone here is gonna know what to do, just wish it was me.

---

### Post by Elfy on 2008-11-19
I did in effect blitz the configs when I did a clean install - but I didn't have the problem before needing the beta nvidia driver - and it was apparently a mistake on their part in building the driver.

Of course it could all be nothing to do with that - no idea if the op actually has nvidia :)

---

### Post by starcannon on 2008-11-19
> **forestpixie said:**
> I did in effect blitz the configs when I did a clean install - but I didn't have the problem before needing the beta nvidia driver - and it was apparently a mistake on their part in building the driver.

Of course it could all be nothing to do with that - no idea if the op actually has nvidia :)

Ha, I just realised I wasn't paying attention to who posted what $sudo slap-forhead.
I set all of my installs up with a separate /home partition, so a clean install will look the same for me when I get back in, so I have to manually nuke config files in my /home/username directories if I have some issue with them.

Anyway, glad yours worked out for you, though I'm uncertain why the OP's is not.

---

### Post by TaintedBllack on 2008-11-19
So it definitely has to do with the nvidia drivers.. I just disabled them and it fixed the problem.

---

### Post by Elfy on 2008-11-20
Ok - so what card do you have in the machine? We could be getting somewhere now :0

---

### Post by TaintedBllack on 2008-11-20
> **forestpixie said:**
> Ok - so what card do you have in the machine? We could be getting somewhere now :0

GeForce4 Ti 4800 SE

---

### Post by Elfy on 2008-11-21
Ok - try this then - uninstall all the drivers that you have installed for the card - if you've at some point used the driver form the nvidia site remove that as well.

Reboot - open software sources - update tab. Enable proposed, close and reload.

Now open Hardware Drivers - see if the nvidia-glx-96 is now there for your card - it must be version 96.43.09 - the old .05 version will not work.

If it's there - let it install the driver and reboot.

---

