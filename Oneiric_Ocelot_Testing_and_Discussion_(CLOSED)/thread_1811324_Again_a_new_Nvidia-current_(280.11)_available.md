---
title: "Again a new Nvidia-current (280.11) available"
date: 2011-07-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-24
This is a quick update.
A new nvidia-current (280.11) is available, from xorg-edgers.
There is also a new version of nvidia-settings.

> 
nvidia-graphics-drivers (280.11-0ubuntu1~edgers~oneiric) oneiric; urgency=low
  * New upstream release
 -- Rico Tzschichholz <email address hidden>   Sun, 24 Jul 2011 20:59:59 +0200


---

### Post by Harry33 on 2011-07-25
Hmm, this is strange.

If I upgrade nvidia-current 280.04 to 280.11, my set up (AMD64, Nvidia GTX285) hangs especially with terminal and synaptic (actually it always says terminal does not respond).
Also if I try to reboot or shutdown, it says terminal does not respond.

Immedialtely after downgrading back to 280.04, everything works well.

Both of those driver versions are from xorg-edgers (built by Ricotz).

---

### Post by VinDSL on 2011-07-25
I've been running 280.11 most of the day, and except for an occasional Compiz crash (which I hadn't experienced prior to the upgrade) everything has been working fine.

Maybe I'll downgrade also...

---

### Post by dino99 on 2011-07-25
installed on i386 pae and works fine.

---

### Post by Harry33 on 2011-07-25
I think this has sometihing to do with mutter and terminal.
So, gnome-shell session may be affected.

---

### Post by Harry33 on 2011-07-25
Some new findings:

The issue seems not be with Mutter nor with Gnome-Shell.
I get the same system hang with fallback session (gnome-panel3).
For example after starting Terminal and Synaptic a couple of times, the system will not shut down anymore. Instead, I get a message window saying terminal not responding.
If I start and restart terminal three times, there are three different instances of terminals, none of them responding (although the actual application window is closed).
At the same time I can hear porcessor fan speeding up and and I notice a great memory consumption.

So, this is all with nvidia-current 280.11.
With 280.04 I have no issues.

---

### Post by dino99 on 2011-07-25
maybe watch kern.log, i've got a segfault with gnome-panel while shuting down

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/815879](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/815879)

had to force closing synaptic & gtkorphan too via htop, was not able to close them as usual neither with menu nor x icon.

---

### Post by Harry33 on 2011-07-25
> **dino99 said:**
> maybe watch kern.log, i've got a segfault with gnome-panel while shuting down

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/815879](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/815879)

had to force closing synaptic & gtkorphan too via htop, was not able to close them as usual neither with menu nor x icon.

Dino, this is interesting.
Did you get this with 280.11 driver?
If so (like me), downgrade to 280.04 driver and see what happens.

Here (the xorg-edgers pool):
[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers/)

---

### Post by dino99 on 2011-07-25
yes with the latest 280.11 and with 3.0.0.6

---

### Post by dino99 on 2011-07-25
> **dino99 said:**
> yes with the latest 280.11 and with 3.0.0.6

and confirm again the synaptic issue: have to pkill it for closing

edit: after closing everything via menu and/or x icons; i've shutdown the system but a popup warn with: 3 terminal "not reponding", like you had.

---

### Post by Harry33 on 2011-07-25
> **dino99 said:**
> and confirm again the synaptic issue: have to pkill it for closing

edit: after closing everything via menu and/or x icons; i've shutdown the system but a popup warn with: 3 terminal "not reponding", like you had.

OK Dino,
by installing 280.04 you solve this issue (or by the 275.09 from the repos).
Perhaps the bug report (815879) of yours should be updated with this info.

---

### Post by dino99 on 2011-07-26
hm, its strange: after downgrading to 275.09, i still need to pkill both terminal & synaptic

so it seems that something else is borked :(

---

### Post by Harry33 on 2011-07-26
> **dino99 said:**
> hm, its strange: after downgrading to 275.09, i still need to pkill both terminal & synaptic

so it seems that something else is borked :(

Could you also try the 280.04 from xorg-edgers. The direct link to pool is in my previous post above (# 8 ).

---

### Post by dino99 on 2011-07-26
cant find 280.04, so i'm waiting for next 280.18 coming soon.

---

### Post by Harry33 on 2011-07-26
Yes they have removed it from the pool.
Well the same driver can be found on another PPA's as well.
Like here (Mingming Ren, Test PPA):
[https://launchpad.net/~portis25/+archive/test/](https://launchpad.net/~portis25/+archive/test/)

And from Mr MEE PPA:
[https://launchpad.net/~mj-casalogic/+archive/bumblebee](https://launchpad.net/~mj-casalogic/+archive/bumblebee)

---

### Post by dino99 on 2011-07-26
Thanks Harry for the links, will try it.

---

### Post by caryb on 2011-07-26
I read this thread from a Kubuntu perspective thinking you guys are pulling my chain as for the last 3 weeks I have been running with a vesa driver as any attempt to install any Nvidia driver wants to remove 50% of my KDE install:confused:


Cary

---

### Post by buzzmandt on 2011-07-26
> **caryb said:**
> I read this thread from a Kubuntu perspective thinking you guys are pulling my chain as for the last 3 weeks I have been running with a vesa driver as any attempt to install any Nvidia driver wants to remove 50% of my KDE install:confused:


Cary


Really????

I would recommend you do a sudo apt-get dist-upgrade, reboot, then try install nvidia again

I just did a sudo apt-get dist-upgrade, reboot followed by a sudo apt-get install nvidia-current.
That test box is purring like a kitten.

---

### Post by Harry33 on 2011-08-01
The latest nvidia-current in xorg-edgers PPA (280.13) does not solve this issue.
This version is, however, the newest stable release from NVidia.

> Changelog
nvidia-graphics-drivers (280.13-0ubuntu1~edgers~oneiric) oneiric; urgency=low

  * New upstream release
    - Added support for the following GPUs:
      o GeForce GTX 570M
      o GeForce GTX 580M
    - Fixed a GLX bug that could cause the X server to crash when rendering
      a display list using GLX indirect rendering.
    - Fixed a GLX bug that could cause a hang in applications that use X
      server grabs.
    - Fixed an X driver bug that caused 16x8 stipple patterns to be rendered
      incorrectly.
    - Fixed a GLX_EXT_texture_from_pixmap bug that caused corruption when
      texturing from sufficiently small pixmaps and, in particular, corruption
      in the GNOME Shell Message Tray.
    - Added unofficial GLX protocol support (i.e., for GLX indirect rendering)
      for the following OpenGL extension:
      o GL_EXT_vertex_attrib_64bit
    - Added GLX protocol support (i.e., for GLX indirect rendering) for the
      following OpenGL extensions:
      o GL_ARB_half_float_pixel
      o GL_EXT_packed_depth_stencil
 -- Rico Tzschichholz <email address hidden>   Mon, 01 Aug 2011 18:25:32 +0200

---

### Post by VinDSL on 2011-08-02
> **VinDSL said:**
> I've been running 280.11 most of the day, and except for an occasional Compiz crash (which I hadn't experienced prior to the upgrade) everything has been working fine.

Maybe I'll downgrade also...

> **Harry33 said:**
> The latest nvidia-current in xorg-edgers PPA (280.13) does not solve this issue.

Heh!

I updated to 280.11

Then, I was going to downgrade.

I went on holiday for a week, and I when I got back, I couldn't remember why I was going to downgrade, so I left it alone.

Now, I'm running 280.13.  And, I still can't remember what the issue was.  LoL!

I added nVidia-current to Conky tonight, because I'm having a hard time remembering the version I'm currentlt running, e.g.

```

${voffset 1}${offset -2}${font OpenLogos:size=12}${color2}Z${voffset -4}${font DroidSans:size=8.65}${color3}${offset 3}${sysname}${offset 3}${kernel}${offset 3}/${offset 3}nVidia-current${offset 3}${pre_exec dpkg --status nvidia-current | grep Version | cut -f 1 -d '-' | sed 's/[^.,0-9]//g'}${font}

```

Output is "nVidia-current 280.13".

Here are the test results for 280.13...

```

$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p && echo && dpkg -s mesa-utils && echo

Tue Aug  2 02:14:23 MST 2011
Ubuntu oneiric (development branch)
Linux 3.0.0-7-generic
unity 4.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13

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

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

```

Everything is working fine!

Can you refresh my memory, please?

What was the "issue"?

---

### Post by portis on 2011-08-02
Could it be this one:
[http://www.nvnews.net/vbulletin/showthread.php?t=164619](http://www.nvnews.net/vbulletin/showthread.php?t=164619)
Gtk apps go into infinite loop when quitting


> **VinDSL said:**
> Heh!

I updated to 280.11

Then, I was going to downgrade.

I went on holiday for a week, and I when I got back, I couldn't remember why I was going to downgrade, so I left it alone.

Now, I'm running 280.13.  And, I still can't remember what the issue was.  LoL!

I added nVidia-current to Conky tonight, because I'm having a hard time remembering the version I'm currentlt running, e.g.

```

${voffset 1}${offset -2}${font OpenLogos:size=12}${color2}Z${voffset -4}${font DroidSans:size=8.65}${color3}${offset 3}${sysname}${offset 3}${kernel}${offset 3}/${offset 3}nVidia-current${offset 3}${pre_exec dpkg --status nvidia-current | grep Version | cut -f 1 -d '-' | sed 's/[^.,0-9]//g'}${font}

```

Output is "nVidia-current 280.13".

Here are the test results for 280.13...

```

$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p && echo && dpkg -s mesa-utils && echo

Tue Aug  2 02:14:23 MST 2011
Ubuntu oneiric (development branch)
Linux 3.0.0-7-generic
unity 4.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13

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

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

```

Everything is working fine!

Can you refresh my memory, please?

What was the "issue"?

---

### Post by VinDSL on 2011-08-02
> **portis said:**
> Could it be this one:
[http://www.nvnews.net/vbulletin/showthread.php?t=164619](http://www.nvnews.net/vbulletin/showthread.php?t=164619)
Gtk apps go into infinite loop when quitting
Interesting!

Well, I thought I would test the theory, but...


```

vindsl@Zuul:~$ cd Downloads
vindsl@Zuul:~/Downloads$ cd nVidia
vindsl@Zuul:~/Downloads/nVidia$ dir
nvidia-current_275.09.07-0ubuntu1_i386.deb
vindsl@Zuul:~/Downloads/nVidia$ sudo dpkg -i *.deb[sudo] password for vindsl: 
**[COLOR="Red"]dpkg: warning: downgrading nvidia-current from 280.13-0ubuntu1~edgers~oneiric to 275.09.07-0ubuntu1.[/COLOR]**
(Reading database ... 144606 files and directories currently installed.)
Preparing to replace nvidia-current 280.13-0ubuntu1~edgers~oneiric (using nvidia-current_275.09.07-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
[B][COLOR="Red"]dpkg: dependency problems prevent configuration of nvidia-current:
 libgl1-mesa-glx (7.12.0~git20110801.5b3c7199-0ubuntu0sarvatt) breaks nvidia-current (<= 275.09.07-0ubuntu1) and is installed.[/COLOR][/B]
  Version of nvidia-current to be configured is 275.09.07-0ubuntu1.
[B][COLOR="Red"]dpkg: error processing nvidia-current (--install):
 dependency problems - leaving unconfigured[/COLOR][/B]
Processing triggers for man-db ...
Errors were encountered while processing:
 nvidia-current
vindsl@Zuul:~/Downloads/nVidia$ 

```

---

### Post by VinDSL on 2011-08-02
Okay, I reinstalled 280.13

Hrm...

I wonder how far I can roll back nvidia-current without breaking UbuOO?!?!?

---

### Post by Harry33 on 2011-08-02
> **VinDSL said:**
> Okay, I reinstalled 280.13

Hrm...

I wonder how far I can roll back nvidia-current without breaking UbuOO?!?!?

280.04 works well, in fact much more fluent rendering than 275.09.07 from the official repos.

---

### Post by Harry33 on 2011-08-02
> **VinDSL said:**
> Heh!

I updated to 280.11

Then, I was going to downgrade.

I went on holiday for a week, and I when I got back, I couldn't remember why I was going to downgrade, so I left it alone.

Now, I'm running 280.13.  And, I still can't remember what the issue was.  LoL!

I added nVidia-current to Conky tonight, because I'm having a hard time remembering the version I'm currentlt running, e.g.

```

${voffset 1}${offset -2}${font OpenLogos:size=12}${color2}Z${voffset -4}${font DroidSans:size=8.65}${color3}${offset 3}${sysname}${offset 3}${kernel}${offset 3}/${offset 3}nVidia-current${offset 3}${pre_exec dpkg --status nvidia-current | grep Version | cut -f 1 -d '-' | sed 's/[^.,0-9]//g'}${font}

```

Output is "nVidia-current 280.13".

Here are the test results for 280.13...

```

$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p && echo && dpkg -s mesa-utils && echo

Tue Aug  2 02:14:23 MST 2011
Ubuntu oneiric (development branch)
Linux 3.0.0-7-generic
unity 4.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13

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

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

```

Everything is working fine!

Can you refresh my memory, please?

What was the "issue"?

This is the issue with 280.11 and 280,13:

If I upgrade nvidia-current from 275.09.07 or from 280.04 to 280.11 or to 280.13,
my set up (AMD64, Nvidia GTX285) hangs with synaptic or terminal (actually it always says terminal does not respond).
Also if I try to reboot or shutdown, a warning message terminal does not respond.

---

### Post by VinDSL on 2011-08-02
> **Harry33 said:**
> 280.04 works well, in fact much more fluent rendering than 275.09.07 from the official repos.
Done!  

Seems to work fine...  ;)

```

vindsl@Zuul:~$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p && echo && dpkg -s mesa-utils && echo

Tue Aug  2 12:13:01 MST 2011
Ubuntu oneiric (development branch)
Linux 3.0.0-7-generic
unity 4.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 **[COLOR="Red"]NVIDIA 280.04[/COLOR]**

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

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

vindsl@Zuul:~$

```

Heh!  Finding that deb was a stinker-pot!  :D

I finally snagged it here:  [https://launchpad.net/~xorg-edgers/+archive/ppa/+build/2637739](https://launchpad.net/~xorg-edgers/+archive/ppa/+build/2637739)

---

### Post by Harry33 on 2011-08-02
> **VinDSL said:**
> https://launchpad.net/~xorg-edgers/+archive/ppa/+build/2637739[/url]

You can also find the version 280.04 from these two PPA's
- MrMEEE:
  [https://launchpad.net/~mj-casalogic/+archive/bumblebee](https://launchpad.net/~mj-casalogic/+archive/bumblebee)
- Mingming Ren:
  [https://launchpad.net/~portis25/+archive/test](https://launchpad.net/~portis25/+archive/test)


I noticed you are using xorg-edgers mesa (7.12 git branch).
That may not work at all with the 275.09.07 from the official repos.

So did you try the 280.13 stable driver with mesa 7.12?
Did terminal and synaptic work without hanging?

---

### Post by VinDSL on 2011-08-02
> **Harry33 said:**
> I noticed you are using xorg-edgers mesa (7.12 git branch).
That may not work at all with the 275.09.07 from the official repos.

So did you try the 280.13 stable driver with mesa 7.12?
Did terminal and synaptic work without hanging?
I'm on the trot right now, Harry.

I've never experienced any hanging in the terminal or Synaptic, on my rig (config listed above / hardware in my sig).

There was some reason that I didn't particularly care for 280.11, but by the time I got home from holiday, I couldn't remember why, so I let it be - and eventually upgraded to 280.13

Put another way, I had an issue, but it must not have been too important, because I'm remiss to remember what it was.

At this point, I can't tell a functional difference between any of them. They're all working fine for me.

If you want me to try to reproduce your issue, let me know specifically what you would like me to install, and I'll try to break my PC later tonight, when I get back to the abode.  ;)

---

### Post by Harry33 on 2011-08-03
> **VinDSL said:**
> I'm on the trot right now, Harry.

I've never experienced any hanging in the terminal or Synaptic, on my rig (config listed above / hardware in my sig).

There was some reason that I didn't particularly care for 280.11, but by the time I got home from holiday, I couldn't remember why, so I let it be - and eventually upgraded to 280.13

Put another way, I had an issue, but it must not have been too important, because I'm remiss to remember what it was.

At this point, I can't tell a functional difference between any of them. They're all working fine for me.

If you want me to try to reproduce your issue, let me know specifically what you would like me to install, and I'll try to break my PC later tonight, when I get back to the abode.  ;)

OK.
Well, because I do not know why some nvidia-current versions do get gnome-terminal and synaptic hang on my setup, I cannot tell how you could test it.
However, I am using drm and mesa of the official repos, my setup is fully upgraded.
I do use gnome-shell from ricotz staging PPA, but this issue is evident also if I try gnome-panel from official repos.
Nvidia-current from Oneiric repos (275.09.07 works fine with me, also the 280.04 version (from xorg-edgers).
But the versions 280.11 and 280.13 do not work.
Simply starting synaptic makes my system hang and it will not even reboot nor halt without SysRq + R-E-I-S-U-B.

---

### Post by Edward7 on 2011-08-03
Thanks for the information.

---

### Post by VinDSL on 2011-08-03
> **Harry33 said:**
> OK.
Well, because I do not know why some nvidia-current versions do get gnome-terminal and synaptic hang on my setup, I cannot tell how you could test it.
The only ongoing problem(s) I'm having is... the &^@! window decorations disappearing.

This is caused by this-or-that player (Banshee, Rhythmbox) crashing.

I've actually setup a Launcher...

```

$ unity-window-decorator --replace

```

... so I don't have to do it from CLI.

That said, I'm constantly in the terminal (several times an hour) and into Synaptic (every hour or so) - and I've never had a problem, regardless of which version of nVidia drivers that I'm running.

So, 280.04 is as good as any, for me.

I've got it pinned right now, so let us know when it's safe to go forward.  ;)

---

### Post by dino99 on 2011-08-03
nvidia set 280.13 as STABLE

---

### Post by Harry33 on 2011-08-03
> **dino99 said:**
> nvidia set 280.13 as STABLE

Yes that is the stable version.
However, it may just be that the issue is how Ubuntu installs multiarch support and libgl-mesa files.
I think I have to try the libgl-mesa 7.12 git branch (and possibly the drm too) the xorg-edgers have and then nvidia-current 280.13 with that.

---

### Post by Harry33 on 2011-08-03
> **VinDSL said:**
> The only ongoing problem(s) I'm having is... the &^@! window decorations disappearing.

This is caused by this-or-that player (Banshee, Rhythmbox) crashing.

I've actually setup a Launcher...

```

$ unity-window-decorator --replace

```

... so I don't have to do it from CLI.

That said, I'm constantly in the terminal (several times an hour) and into Synaptic (every hour or so) - and I've never had a problem, regardless of which version of nVidia drivers that I'm running.

So, 280.04 is as good as any, for me.

I've got it pinned right now, so let us know when it's safe to go forward.  ;)

For me the 280.04 version is the only one working OK.
Do you have all the updates installed from xorg-edgers (mesa + drm + xserver)?

---

### Post by EgoGratis on 2011-08-03
I always wondered so i will ask here.

If i use Ubuntu 11.04 and add x-swat PPA then i get new Intel/AMD/NVIDIA drivers easily.

But what about the kernel?

Sometimes i read there are performance improvements and fixes in newer kernel for some graphic. Do you update your kernel too or just graphic driver and wait six month for newer kernel in newer Ubuntu?

---

### Post by Harry33 on 2011-08-03
> **EgoGratis said:**
> I always wondered so i will ask here.

If i use Ubuntu 11.04 and add x-swat PPA then i get new Intel/AMD/NVIDIA drivers easily.

But what about the kernel?

Sometimes i read there are performance improvements and fixes in newer kernel for some graphic. Do you update your kernel too or just graphic driver and wait six month for newer kernel in newer Ubuntu?

I would stick with Natty kernell and not upgrade it to Oneiric's 3.0.0 kernell.
Your system may not even boot with the Oneiric kernel.

---

### Post by VinDSL on 2011-08-04
> **Harry33 said:**
> Do you have all the updates installed from xorg-edgers (mesa + drm + xserver)?
Everything... the whole enchilada.  ;)


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/Screenshot at 2011-08-04 01:59:39(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot at 2011-08-04 01:59:39.png")[/INDENT]

---

### Post by dino99 on 2011-08-04
> **slicx11 said:**
> is your issue solved? asking this because i need to things out with mine!

dont tried anything else but 280.04 which works smootly; so i dont want to break something working

---

### Post by Harry33 on 2011-08-04
> **dino99 said:**
> dont tried anything else but 280.04 which works smootly; so i dont want to break something working

I cannot get the 280.13 driver work.
I will try to install newer mesa (7.12 git) + possibly drm and xserver, all from xorg-edgers and try with that.

---

### Post by Harry33 on 2011-08-04
> **VinDSL said:**
> Everything... the whole enchilada.  ;)


Hmm, I do not see nvidia-current 280.13 there, only nvidia-settings. Where did you get nvidia-current from?
You have also installed all video drivers (ati, nouveau, intel, s3 etc).
I install only the one I use, for nvidia card - only nvidia-current.

---

### Post by VinDSL on 2011-08-04
> **Harry33 said:**
> Hmm, I do not see nvidia-current 280.13 there, only nvidia-settings. Where did you get nvidia-current from?
I'm running nvidia-current 280.04 right now. (see post #26).

I downloaded the deb from the link in that post, and installed it locally.

It's xorg-edgers too, but I didn't get it from their PPA (it wasn't available in the official repo) thus it doesn't show up in Origins, using Synaptic.

---

### Post by zekopeko on 2011-08-04
Anybody having problem with X not starting on boot and lightdm refusing to work? If I do startx from console I get logged into gnome-session-fallback even though the Nvidia driver is working and Ubuntu is reporting that 3D works (I can run OpenGL apps).

Happens both on 280.04 and 280.11.

---

### Post by tad1073 on 2011-08-04
I don't know if this will help but I added x-swat to 10.10 and x started just fine for me, but that is on 10.10.

---

### Post by Harry33 on 2011-08-05
> **tad1073 said:**
> I don't know if this will help but I added x-swat to 10.10 and x started just fine for me, but that is on 10.10.

Yes nvidia-current 280.13 is there for Maverick and Natty.
X-Swat (Ubuntu-X) has only fglrx for Oneiric, nothing else.

---

