---
title: "New nvidia-current in Oneiric repos (270.41.19-0ubuntu1)"
date: 2011-06-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-06-14
Alberto Milone has uploaded a new version of NVidia proprietary drivers in Oneiric repos.
This is, however, not the latest stable.
We can see from Nvidia's web site that the latest stable is 275.09.07 from today 14th June 2011.
The 270.41.19 driver is from 20th May 2011.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/nvidia-settings/270.41.19-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/nvidia-settings/270.41.19-0ubuntu1)

> Changelog
nvidia-settings (270.41.19-0ubuntu1) oneiric; urgency=low

  * New upstream release.
 -- Alberto Milone <email address hidden>   Tue, 14 Jun 2011 19:20:08 +0200

---

### Post by ronacc on 2011-06-14
give alberto a chance nvidia just put 275.09.07 up today !

---

### Post by Harry33 on 2011-06-14
> **ronacc said:**
> give alberto a chance nvidia just put 275.09.07 up today !

True, I wasn't actually criticising Alberto in any way.
My attention was to inform people here of these uploads.

---

### Post by Harry33 on 2011-06-15
Anyway, what is important in this 270.41.19 build in Oneiric repos, is that it now accepts new 3.0 kernels.

>   * debian/dkms.conf{.in}:
    - Enable builds for 3.0 kernels.
  * debian/control{.in}:
    - Drop transitional packages.
  * Add buildfix_kernel_3.0.patch:
    - Add support for linux 3.0.

---

### Post by VinDSL on 2011-06-15
Oh, you're such a tease, Harry!  :D

I just got 3D Unity working, for the first time in many days, and...

Now, I must try to break it, again!

Okay, be back in a few minutes... or not.

Wish me luck!  LoL!

---

### Post by lucazade on 2011-06-15
> **VinDSL said:**
> Oh, you're such a tease, Harry!  :D

I just got 3D Unity working, for the first time in many days, and...

Now, I must try to break it, again!

Okay, be back in a few minutes... or not.

Wish me luck!  LoL!

Drum roll

:popcorn:

---

### Post by VinDSL on 2011-06-15
> **lucazade said:**
> Drum roll

:popcorn:
Tah dah!  :D


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-15-jun-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-15-jun-2011(2).png")[/INDENT]


```

vindsl@Zuul:~$ date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p
**[COLOR="Red"]Wed Jun 15 03:02:07 MST 2011[/COLOR]**
**[COLOR="Red"]Ubuntu oneiric (development branch)[/COLOR]**
**[COLOR="red"]Linux 3.0.0-0300rc3-generic[/COLOR]**
**[COLOR="red"]unity 3.8.14[/COLOR]**
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2**[COLOR="red"] NVIDIA 270.41.19[/COLOR]**

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
vindsl@Zuul:~$ 

```

Piece of cake!

I think I'll quit, while I'm ahead...  ;)

---

### Post by VMC on 2011-06-15
I always install using nvidia's "run" file. 

64-bit 275.09.07 Found [here]("http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html").

---

### Post by Harry33 on 2011-06-15
> **VMC said:**
> I always install using nvidia's "run" file. 

64-bit 275.09.07 Found [here]("http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html").

The same newest beta nvidia-current_275.09.07 is also in the Xorg-edgers PPA.

---

### Post by XMasterrrr on 2011-06-15
> **Harry33 said:**
> The same newest beta nvidia-current_275.09.07 is also in the Xorg-edgers PPA.

Thank's it works

---

### Post by Harry33 on 2011-06-15
Well that was fast.
Alberto Milone has uploaded the latest nvidia-current (275.09.07) into Oneiric official repos. This driver is also certified as being stable.

> nvidia-graphics-drivers (275.09.07-0ubuntu1) oneiric; urgency=low
  * New upstream release:
    - Added support for the following GPUs:
      o GeForce GTX 560
      o GeForce GT 545
      o GeForce GTX 560M
      o GeForce 410M
      o GeForce 320M
      o GeForce 315M
      o Quadro 5010M
      o Quadro 3000M
      o Quadro 4000M
    - Fixed a bug that caused desktop corruption in GNOME 3 after a
      VT-switch or suspend/resume cycle.
    - Fixed a bug that caused freezes and crashes when resizing
      windows in KDE 4 with desktop effects enabled using X.Org X
      server version 1.10 or later.
    - Modified the X driver to request that hardware inform the
      audio driver whenever a display is disabled. This will allow
      the audio driver to generate the appropriate jack unplug
      events to applications.
    - Added support for the GL_EXT_x11_sync_object extension. See
      the extension specification in the OpenGL registry here:
      [http://www.opengl.org/registry/specs/EXT/x11_sync_object.txt](http://www.opengl.org/registry/specs/EXT/x11_sync_object.txt)
      for more details.
    - Improved performance of window resize operations in KDE 4 on
      systems with slow CPUs.
    - Added support for hardware button based pairing to NVIDIA 3D
      Vision Pro. Single click button on the hub to enter into a
      pairing mode which pairs one pair of glasses at a time. Double
      click the same button on the hub to enter into a pairing mode
      which pairs multiple pairs of glasses at a time.
    - Added unofficial GLX protocol support (i.e., for GLX indirect
      rendering) for the following OpenGL extensions:
      o GL_NV_framebuffer_multisample_coverage
      o GL_NV_texture_barrier
    - Added GLX protocol support (i.e., for GLX indirect rendering)
      for the following OpenGL extension:
      GL_NV_register_combiners2
    - Fixed a bug that caused the pop-out and external DVI displays
      to go blank on Lenovo ThinkPad W701 laptops.
    - Fixed a bug that caused corruption on the menus in OpenOffice.
      org when the screen is rotated.
    - Improved performance of certain memory allocations.
    - Fixed a bug that caused Java2D widgets to disappear when Java
      is configured to render using FBOs.
    - Added a new X configuration option "BaseMosaic" which can be
      used to extend a single X screen transparently across all of
      the available display outputs on each GPU. See "Appendix B.
      X Config Options" in the README for more information.

Date: Wed, 15 Jun 2011 16:04:39 +0200
Changed-By: Alberto Milone <alberto.milone at canonical.com>

---

### Post by VanR on 2011-06-15
Yep, I've running it on Natty and Oneiric. Both with 3.0-0 kernel. So far it's smooth.

---

### Post by briancb on 2011-06-22
Downloaded and installed the newest Nvidia driver. Unfortunately failed to fully boot stopped at checking battery.

I am running Kernel 3.0.1

---

### Post by sparker256 on 2011-06-22
> **briancb said:**
> Downloaded and installed the newest Nvidia driver. Unfortunately failed to fully boot stopped at checking battery.

I am running Kernel 3.0.1

It helps to list version numbers of what you call newest Nvidia driver so we can better help. The version that I am running is 275.09.07 and it has a problem with the latest mesa (7.10.3-0ubuntu3) version so I am running mesa (7.10.2-0ubuntu2) version. 

Take a look at this thread post #14 and look at what I did to get Nvidia Current running.

[http://ubuntuforums.org/showthread.php?t=1783213&page=2](http://ubuntuforums.org/showthread.php?t=1783213&page=2)

Bill

---

### Post by briancb on 2011-06-23
> **sparker256 said:**
> It helps to list version numbers of what you call newest Nvidia driver so we can better help. The version that I am running is 275.09.07 and it has a problem with the latest mesa (7.10.3-0ubuntu3) version so I am running mesa (7.10.2-0ubuntu2) version. 

Take a look at this thread post #14 and look at what I did to get Nvidia Current running.

[http://ubuntuforums.org/showthread.php?t=1783213&page=2](http://ubuntuforums.org/showthread.php?t=1783213&page=2)

Bill
Thank you Bill, I will have a look at your thread. The driver was 275.09.07. I have had to do a new install so I'll try again.

Brian

---

### Post by dino99 on 2011-06-23
as acpid have issue, i've purged it then purged nvidia-current too.
The surprise is when i want to reinstall nvidia-current (acpid is one of its dependenies): get a warning box saying it wont be installed.
Installing acpid first, then nvidia-current can be installed too.

---

