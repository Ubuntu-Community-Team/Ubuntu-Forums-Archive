---
title: "How to list (recursively) all recommendations of a package?"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by EECOLOR on 2013-01-03
I am (very) new to linux and ubuntu and I am patiently trying to build an installable CD using the ubuntu-mini-remix iso. For years I have removed stuff from Windows before installing it, so I was delighted with the option to add stuff here in the linux world.

I have created some working iso's (steep learning curve), so it's going pretty well.

I have searched the internet for information about the Recommends part of apt-get and I know that it's not smart for new users to install everything without them. On the other hand, some people say that it's good to know more about the packages you are installing.

'Recommends' seems to have a different meaning for different packages:
[LIST]
[*]Installing 'plasma-desktop' (kde) with recommends installs 'unity' as well. 
[*]Installing 'virtualbox-ose-guest-utils' without recommends does not install the part that lets you mount a shared folder. 
[/LIST]

I have found the apt-rdepends tool, but that lists more than I want: ```
apt-rdepends --follow=1,2,4 --show=4 plasma-desktop
```

I could use grep on the above output, but then I can not see what package it belongs to.

In order to learn more I want some tips on the following things:
[LIST]
[*]How to list the packages with recommended packages recursively?
[*]Where to find information about the intentions of the 'recommended packages'?
[/LIST]

Thank you

---

### Post by tgalati4 on 2013-01-03
Start with the major packages:

tgalati4@Dell600m-mint14 ~/Desktop $ apt-cache depends xserver-xorg
xserver-xorg
  Depends: xserver-xorg-core
 |Depends: xserver-xorg-video-all
  Depends: <xorg-driver-video>
    fglrx
    fglrx-updates
    nvidia-173
    nvidia-173-updates
    nvidia-current
    nvidia-current-updates
    nvidia-experimental-304
    nvidia-experimental-310
    virtualbox-guest-x11
    xserver-xorg-video-ati
    xserver-xorg-video-cirrus
    xserver-xorg-video-dummy
    xserver-xorg-video-fbdev
    xserver-xorg-video-geode
    xserver-xorg-video-intel
    xserver-xorg-video-mach64
    xserver-xorg-video-mga
    xserver-xorg-video-modesetting
    xserver-xorg-video-neomagic
    xserver-xorg-video-nouveau
    xserver-xorg-video-openchrome
    xserver-xorg-video-qxl
    xserver-xorg-video-r128
    xserver-xorg-video-radeon
    xserver-xorg-video-s3
    xserver-xorg-video-savage
    xserver-xorg-video-siliconmotion
    xserver-xorg-video-sis
    xserver-xorg-video-sisusb
    xserver-xorg-video-tdfx
    xserver-xorg-video-trident
    xserver-xorg-video-vesa
    xserver-xorg-video-vmware
 |Depends: xserver-xorg-input-all
  Depends: <xorg-driver-input>
    xserver-xorg-input-acecad
    xserver-xorg-input-aiptek
    xserver-xorg-input-elographics
    xserver-xorg-input-evdev
    xserver-xorg-input-joystick
    xserver-xorg-input-kbd
    xserver-xorg-input-mouse
    xserver-xorg-input-mtrack
    xserver-xorg-input-multitouch
    xserver-xorg-input-mutouch
    xserver-xorg-input-penmount
    xserver-xorg-input-synaptics
    xserver-xorg-input-tslib
    xserver-xorg-input-vmmouse
    xserver-xorg-input-void
    xserver-xorg-input-wacom
  Depends: xserver-xorg-input-evdev
  Depends: libc6
  Depends: xkb-data
  Depends: x11-xkb-utils
  Recommends: libgl1-mesa-dri

---

### Post by ibjsb4 on 2013-01-04
You can also get a list of package details.  Example ..

[http://packages.ubuntu.com/precise/xserver-xorg-core](http://packages.ubuntu.com/precise/xserver-xorg-core)

---

### Post by DuckHook on 2013-01-04
All of you realize that this flies so far above "absolute beginners" that you should be getting nosebleed?

---

### Post by tgalati4 on 2013-01-04
That is true, but the OP asked a question about respinning and getting a list of critical packages.  We were all beginners at one time.

---

### Post by Cheesehead on 2013-01-04
It's not listing, but in some circumstances it is handy to show the interlocking dependency relationships:

I used [FONT="Courier New"]apt-cache dotty hello > hellofile[/FONT] to generate an image of the complete dependency tree for the 'hello' package. 

Then use [FONT="Courier New"]xdot hellofile[/FONT] to view the tree.

Be patient, xdot may take a couple minutes to generate the image. There are over 4000 image elements to process in this example. The apt-cache man page has instructions on how to limit the output for a more focused chart.


Generally, good practice in customizing an environment is to start with the ubuntu-minimal, ubuntu-standard, or *buntu-desktop metapackages and add/delete from there.
ubuntu-minimal is barely enough to boot, get online, and use the package manager.
ubuntu-standard is a fully-featured command line environment.
ubuntu-desktop is what the LiveCD/LiveUSB installer installs, a complete GUI environment, including applications.


And don't forget about apt-get's --simulate flag, so you can safely see what removing any package will really do to a system!

---

