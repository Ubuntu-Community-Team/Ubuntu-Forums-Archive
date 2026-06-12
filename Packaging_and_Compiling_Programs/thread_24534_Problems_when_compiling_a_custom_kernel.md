---
title: "Problems when compiling a custom kernel"
date: 2005-04-07
forum: Packaging and Compiling Programs
---

### Post by Carrot on 2005-04-07
Hi all,

I want to compile a custom ubuntu kernel. What is the difference between the linux-source-2.6.10 pkg in binary repository and the kernel source retrieved by 'apt-get source linux-image-2.6.10-5-386'?

I follow the instructions in [KernelBuildpackageDetailedHowto](http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto),    the dpkg-buildpackage command complains about missing 2.6.10-34 abi...( I forgot the exact error message, but there is only '2.6.10-33' in the abi directory.)

What should i do? Any help will be appreciated.

---

### Post by az on 2005-04-07
linux-source is the source with all the patches included.  This is how it is different from the same version kernel sourceyou get from kernel.org.

linux-image is a precompiled binary of that kernel.

---

### Post by Carrot on 2005-04-08
Thanks for your reply.

As described in the wiki howto, I should use the pkg from 'apt-get source ...' for running the 'dpkg-buildpackage' command. In fact, I tried 'make-kpkg' on the linux-source pkg several times. It worked fine with my own kernel configuration, except the VESA frame buffer. No matter it is compiled into the kernel or as a module, I got a black screen when booting the kernel with "vga=...". But the official ubuntu kernel(2.6.10-5-686) works fine. Below is my configuration file (frame buffer section):

> 
#
# Graphics support
#
CONFIG_FB=y
CONFIG_FB_MODE_HELPERS=y
CONFIG_FB_TILEBLITTING=y
# CONFIG_FB_CIRRUS is not set
# CONFIG_FB_PM2 is not set
# CONFIG_FB_CYBER2000 is not set
# CONFIG_FB_ASILIANT is not set
# CONFIG_FB_IMSTT is not set
# CONFIG_FB_VGA16 is not set
CONFIG_FB_VESA=m
CONFIG_VIDEO_SELECT=y
# CONFIG_FB_HGA is not set
# CONFIG_FB_RIVA is not set
# CONFIG_FB_I810 is not set
# CONFIG_FB_INTEL is not set
# CONFIG_FB_MATROX is not set
# CONFIG_FB_RADEON_OLD is not set
# CONFIG_FB_RADEON is not set
# CONFIG_FB_ATY128 is not set
# CONFIG_FB_ATY is not set
# CONFIG_FB_SAVAGE is not set
# CONFIG_FB_SIS is not set
# CONFIG_FB_NEOMAGIC is not set
# CONFIG_FB_KYRO is not set
# CONFIG_FB_3DFX is not set
# CONFIG_FB_VOODOO1 is not set
# CONFIG_FB_TRIDENT is not set
# CONFIG_FB_VIRTUAL is not set

#
# Console display driver support
#
CONFIG_VGA_CONSOLE=y
CONFIG_DUMMY_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE=m
# CONFIG_FONTS is not set
CONFIG_FONT_8x8=y
CONFIG_FONT_8x16=y

#
# Logo configuration
#
# CONFIG_LOGO is not set


Anything wrong?

---

### Post by gny on 2005-04-12
A thing i usually do when i compile a custom kernel is to copy the config file
 from an old kernel.

```

cp /boot/config-<kernel.version.here>-<arch> /usr/src/linux/.config

```

Be sure to name it .config

then run

```

make oldconfig

```

On all the questions you can just hit enter and the default value will be used which usually is enough. If you press ? a short information is displayed.

Then if you want you can do
```

make menuconfig

```
And procced as usuall.

This way you know that you get an kernel with similar configuration as your old one.

 :razz:

---

### Post by mendicant on 2005-04-12
I recently rebuilt my kernel on Hoary, and I just used the linux-source package, using the old /boot/config-... as a template, as gny mentioned.  I've never built the kernel by getting the source package itself.

I also typically use make-kpkg.

---

### Post by edebont on 2005-04-13
[QUOTE=gny]A thing i usually do when i compile a custom kernel is to copy the config file
 from an old kernel.

```

cp /boot/config-<kernel.version.here>-<arch> /usr/src/linux/.config

```

Be sure to name it .config

then run

```

make oldconfig

```

On all the questions you can just hit enter and the default value will be used which usually is enough. If you press ? a short information is displayed.

Then if you want you can do
```

make menuconfig

```
And procced as usuall.

This way you know that you get an kernel with similar configuration as your old one.

 :razz:[/QUOTE]

This is a nice workaround. However you still don't know what the proper settings are for the VESA framebuffer kernel settings. Does anybody know them ?

---

### Post by gny on 2005-04-13
Ooh, 
I didn't read your message close enough. Sorry.
No, I don't know the settings. But does it work if you use the old config from 2.6.10 when you compile a 2.6.11?
if so you could check out whats different under frambufferssetting. 

The 2.6.11 that is in universe (i think) does not work for me at all. I think whoever compiled it has changed alot of settings in the config.

What kind of video card do you have. like if you have an nvidia  some framebuffers will not work and some will. I had this problem myself. X would not start unless i unloaded a framebuffer module that was not compatible with the nvidia module.

---

### Post by Carrot on 2005-04-13
Finally I got VESA FB worked with my custom kernel.

As described in the following posts:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=1837](https://bugzilla.ubuntu.com/show_bug.cgi?id=1837)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=282234](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=282234)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=289810](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=289810)

It seems that the vesafb support should be compliled in as a module and be loaded manually into the initrd image. Make sure that the following two lines are in '/etc/mkinitrd/modules' before running 'fakeroot make-kpkg --initrd ...':
> 
vesafb
fbcon


ubuntu hoary + nvidia 7174

---

### Post by edebont on 2005-04-13
[QUOTE=Carrot]Finally I got VESA FB worked with my custom kernel.

It seems that the vesafb support should be compliled in as a module and be loaded manually into the initrd image. Make sure that the following two lines are in '/etc/mkinitrd/modules' before running 'fakeroot make-kpkg --initrd ...':


ubuntu hoary + nvidia 7174[/QUOTE]

Thanks for tip ! Adding "vesafb" & 'fbcon" to /etc/mkinitrd/modules was the solution to the problem.

---

### Post by Iceybrow on 2005-07-15
[QUOTE=gny]Ooh, 
I didn't read your message close enough. Sorry.
No, I don't know the settings. But does it work if you use the old config from 2.6.10 when you compile a 2.6.11?
if so you could check out whats different under frambufferssetting. 

The 2.6.11 that is in universe (i think) does not work for me at all. I think whoever compiled it has changed alot of settings in the config.

What kind of video card do you have. like if you have an nvidia  some framebuffers will not work and some will. I had this problem myself. X would not start unless i unloaded a framebuffer module that was not compatible with the nvidia module.[/QUOTE]


I tried compiling that to, as is, and with different processor family options, and it gave me errors related to DVB. I reported it as a bug and got a reply from a guy saying that "it is not for use". Funny that it should be in the Ubuntu multiverse, if it is not for use. Now I am trying 2.6.12-2 from kernel.org  I would like to apply certain linuxtv.org
patches to get a certain DVB-T card working.

---

### Post by cosi on 2006-11-19
In Edgy, the steps to enable vesafb and fbcon in a custom kernel & initrd are slightly different:

1) Open /etc/initramfs-tools/modules
2) Add
   vesafb
   fbcon

If you have created a custom kernel using the make-kpkg command, you can simply do (this is what I did):
3) sudo dpkg-reconfigure linux-image-`uname -r`

- or - (I haven't tried this myself)
3) sudo update-initramfs -u

---

