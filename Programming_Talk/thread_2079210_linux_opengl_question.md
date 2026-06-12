---
title: "linux opengl question"
date: 2012-11-01
forum: Programming Talk
---

### Post by thedardanius on 2012-11-01
OK, this is really confusing:

on windows, you have opengl32.dll, standard implementation of OpenGL (1.1) for windows when you havent installed a driver of your GPU vendor. But how does this work on linux? Is there a e.g. nivdia driver for linux? And where are the libraries for opengl on linux? Do I need to install a new driver (since the windows support of OpenGL is as good as their compiler's C99 support: Awful) for linux if I want to game or what? And what is XFree86 actually? I read it somewhere when I was learning a bit of xlib.

---

### Post by trent.josephsen on 2012-11-01
I don't know much about OpenGL and I'm not sure how that relates to your question about drivers... there are drivers for different graphics cards, yes, but I don't see how that directly relates to OpenGL.

XFree86 and Xorg are two different windowing systems that implement the X11 protocol. XFree86 used to be the most popular, the implementation everybody used; but a licensing change sparked a mass migration to Xorg, a fork of XFree86. XFree86 is no longer under active development but you do see references to it from time to time, particularly in older documentation and in the names of some drivers that were developed when it was the dominant X implementation.

---

### Post by thedardanius on 2012-11-02
ok.

My question about OpenGL:
Do i need to install a better driver in Ubuntu if I want to game?
Because I dont know if the standard OpenGL implementation of Ubuntu is good...
On windows it *****, so I doubt about Ubuntu either.
Can you also explain me how OpenGL is implementated on linux?

---

### Post by thedardanius on 2012-11-02
I know you can implement OpenGL in a dozen ways but just the general concept please.

---

### Post by SledgeHammer_999 on 2012-11-02
It depends on your GPU. Some have really good open-source drivers with good performance and some other need the close-source driver have good performance.

---

### Post by bird1500 on 2012-11-02
[The Linux OpenGL ABI]("http://www.opengl.org/registry/ABI/")

But generally you should use helper libraries like freeglut and libglew, unless you're interested into learning the guts of the GL system.
Also, in the next few years a[ new Linux ABI]("http://www.phoronix.com/scan.php?page=news_item&px=MTE4NDA") is [on the way]("http://lists.freedesktop.org/archives/mesa-dev/2012-September/027295.html").

---

### Post by thedardanius on 2012-11-03
but my question:
When I installed ubuntu, I didnt notice anything like a driver installation or sth. Do I need to install a driver or it this "default" driver good enough? Or is the driver in the linux kernel??

---

### Post by bird1500 on 2012-11-03
**Intel** - only one driver, developed by Intel, it's open source, ships by default with all distros.
**AMD** - 2 drivers, both developed by AMD, the open source one ships by default, is slower, has less features. The closed source one must be installed, one can do this in different ways. Google rocks.
**Nvidia** - 2 drivers. The open source one is called nouveau, it has less features and is slower and ships by default with all distros and is developed by the community, mostly by Red Hat. The closed source one is faster, has more features and is developed by Nvidia, not installed by default, can be installed in different ways - google rocks.
**Other** - it's your problem.

---

### Post by thedardanius on 2012-11-03
thank you/ So nvidia has a default driver on ubuntu?

---

### Post by steeldriver on 2012-11-03
You can list all the xserver-xorg-video-xxxx packages

```
$ dpkg -l | grep xserver-xorg-video
ii  xserver-xorg-video-all                 1:7.6+12ubuntu1                         X.Org X server -- output driver metapackage
ii  xserver-xorg-video-ati                 1:6.14.99~git20111219.aacbd629-0ubuntu2 X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-cirrus              1:1.3.2-4build1                         X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev               1:0.4.2-4ubuntu2                        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode               2.11.13-2build1                         X.Org X server -- Geode GX2/LX display driver
ii  xserver-xorg-video-intel               2:2.17.0-1ubuntu4.1                     X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64              6.9.0-1build2                           X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                 1:1.4.13.dfsg-4build2                   X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic            1:1.2.5-2build2                         X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau             1:0.0.16+git20111201+b5534a1-1build2    X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-openchrome          1:0.2.904+svn1050-1                     X.Org X server -- VIA display driver
ii  xserver-xorg-video-qxl                 0.0.16-2                                X.Org X server -- QXL display driver
ii  xserver-xorg-video-r128                6.8.1-5build2                           X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon              1:6.14.99~git20111219.aacbd629-0ubuntu2 X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-s3                  1:0.6.3-4build2                         X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-savage              1:2.3.3-1ubuntu1                        X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion       1:1.7.5-1build2                         X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                 1:0.10.3-3build2                        X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb              1:0.9.4-2build2                         X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                1:1.4.3-4build2                         X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident             1:1.3.4-2build2                         X.Org X server -- Trident display driver
ii  xserver-xorg-video-vesa                1:2.3.0-7build2                         X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware              1:12.0.1-1ubuntu1.1                     X.Org X server -- VMware display driver

```

---

### Post by bird1500 on 2012-11-04
> **thedardanius said:**
> thank you/ So nvidia has a default driver on ubuntu?
Yes, but this driver (nouveau) is the open-source one which isn't developed nor supported by Nvidia Corporation, but might be good enough for many people.

To find out what graphics driver is running on your system:
sudo apt-get install mesa-utils
then
glxinfo | grep version
which yields for me:
[PHP]
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 4.3.0 NVIDIA 310.14
OpenGL shading language version string: 4.30 NVIDIA via Cg compiler
[/PHP]Or just call "glxinfo" without " grep version" for a lot more info.

---

### Post by thedardanius on 2012-11-04
Thank you  very much!
I didnt install additional drivers, so if I want to game with OpenGL, it is recommended to get the vendor's own driver? I presume that one is of course faster.

---

### Post by thedardanius on 2012-11-04
I downloaded their linux 32-bit long lived driver, but I just got a .run file. How do I run this/install their closed source driver?

---

### Post by bird1500 on 2012-11-04
The easiest way to install Nvidia's binary driver is by going to "Addition Drivers", selecting "nvidia current" and "apply", then restart, that's it.

Otherwise you have to exit the X server and do random stuff like answering questions, in short:
Ctrl+Alt+F3
*<snip> (using root is against ubuntuforums policy) not found*
sudo stop lightdm (stops lightdm and the X server, otherwise the driver won't install)
cd /folder/with/your/downloaded/driver/
sudo ./the-nvidia-driver.sh (runs the nvidia driver installer as root)
(answer questions, basically "yes" to all)
sudo reboot

---

### Post by DarkAmbient on 2012-11-04
> **bird1500 said:**
> The easiest way to install Nvidia's binary driver is by going to "Addition Drivers", selecting "nvidia current" and "apply", then restart, that's it.

Prior to Ubuntu 12.10, you what's mentioned above. 

In Ubuntu 12.10, this have moved to software-sources.

* Easiest way to find it would be to search the dash for Software sources.
* Another way would be to open software centre, click edit in menu then software-sources.
* You can also open the "system-menu" most up right, then systemsettings, then you got software-sources in there.

Well inside software-sources, you see that the last tab is named Additional Drivers.

I find this move to be slightly confusing to be honest.

Anyway, hopefully I'm using the corresponding english names for named apps or menus. Got swedish language in my Ubuntu-installation.

---

### Post by bird1500 on 2012-11-04
Since he's got Nvidia, "sudo apt-get install nvidia-current" is the quickest option. Prior to this he might need enabling "Canonical Partners" in the software sources, I'm not sure.

---

### Post by thedardanius on 2012-11-05
Thank you guys very much!

---

