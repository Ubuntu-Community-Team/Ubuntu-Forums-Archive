---
title: "Nouveau not able to run Unity?"
date: 2011-06-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-06-28
Is it currently not possible to run Unity using Novueau + libgl1-mesa-dri-experimental?

---

### Post by beew on 2011-06-28
> **MacUntu said:**
> Is it currently not possible to run Unity using Novueau + libgl1-mesa-dri-experimental?

It certainly is possible, I am doing it right now. You can get all the packages by running Additional Drivers. Two drivers will show up, the Nvidia closed source driver and something called 3D experimental driver (that is Nouveau + libgl1-meas-dri-experimental + maybe some other things), if you want nouveau choose the second one.

Opps sorry, just realize this is an OO thread.

---

### Post by lucazade on 2011-06-28
@MacUntu

paste the output of:
/usr/lib/nux/unity_support_test -p 

and:
glxinfo

also a look at:
/var/log/Xorg.0.log 
could you tell you if modules and extensions are properly loaded.

---

### Post by MacUntu on 2011-06-28
Segmentation fault (core dumped) [yay]

name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

Nothing exciting in /var/log/Xorg.0.log

---

It looks like I broke something. Shouldn't there be an alternative 'gl_conf'?

---

### Post by lucazade on 2011-06-28
> **MacUntu said:**
> Segmentation fault (core dumped) [yay]

name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

Nothing exciting in /var/log/Xorg.0.log

---

It looks like I broke something. Shouldn't there be an alternative 'gl_conf'?

this?

```
sudo update-alternatives --config gl_conf
sudo ldconfig
sudo update-initramfs -u
```

taken from here: [https://wiki.ubuntu.com/X/Drivers](https://wiki.ubuntu.com/X/Drivers)
never played with this so I don't know about it.

Here I'm not able to use nouveau (also w/o experimental drivers) from a couple of releases of Ubuntu.
After some minutes there is a hard freeze and a lot of glitches, luckily I use the blob driver :)

---

### Post by MacUntu on 2011-06-28
Ah, that now is 'i386-linux-gnu_gl_conf' - maybe that's causing confusion. Well I'm going to sit that one out and install the BLOB again. :-)

---

### Post by coffeecat on 2011-06-29
> **MacUntu said:**
> Is it currently not possible to run Unity using Novueau + libgl1-mesa-dri-experimental?

I believe (but am not 100% sure) that I have just run Unity 3d with nouveau but **without** libgl1-mesa-dri-experimental.

Booting up with a live USB prepared from today's (29th June) live ISO on a machine with a GeForce 8400GS GPU, I was rather surprised to be presented with what looks like the 3d, not the 2d desktop. The trash icon is quite distinctive.

Unfortunately I wasn't able to test this by logging out and into both desktops in the live session, because all the panel icons are [missing at the moment](http://ubuntuforums.org/showthread.php?t=1792797), including the shutdown button. And Alt-SysReq-K just sends me to a tty or blank screen.

I've got Oneiric installed on my other desktop machine with ATI graphics so I didn't want to install it to this nvidia one just yet. What are others with nvidia cards seeing?

---

### Post by sparker256 on 2011-06-29
> **coffeecat said:**
> I believe (but am not 100% sure) that I have just run Unity 3d with nouveau but **without** libgl1-mesa-dri-experimental.

Booting up with a live USB prepared from today's (29th June) live ISO on a machine with a GeForce 8400GS GPU, I was rather surprised to be presented with what looks like the 3d, not the 2d desktop. The trash icon is quite distinctive.

Unfortunately I wasn't able to test this by logging out and into both desktops in the live session, because all the panel icons are [missing at the moment](http://ubuntuforums.org/showthread.php?t=1792797), including the shutdown button. And Alt-SysReq-K just sends me to a tty or blank screen.

I've got Oneiric installed on my other desktop machine with ATI graphics so I didn't want to install it to this nvidia one just yet. What are others with nvidia cards seeing?
A quick way that I have found is to try to pull one of the lauchpad icons right to the desktop. 3D will let you but 2D will not.

Bill

---

### Post by mc4man on 2011-06-29
> **coffeecat said:**
> I believe (but am not 100% sure) that I have just run Unity 3d with nouveau but **without** libgl1-mesa-dri-experimental.
 What are others with nvidia cards seeing?
It's now 'built-in' and available by default - mesa changelog

 > debian/libgl1-mesa-dri.install.linux.in:
    - Move nouveau gallium driver from -dri-experimental to -dri.  Upstream
      is no longer adamant that bugs should be ignored.  Try installing it by
      default to get a better Unity experience OOTB. (LP: #759562)

---

### Post by coffeecat on 2011-06-29
> **sparker256 said:**
> A quick way that I have found is to try to pull one of the lauchpad icons right to the desktop. 3D will let you but 2D will not.

Bill

Now, why didn't I think of that? :) Thanks. I am indeed getting 3d Unity ootb with nouveau - see screenshot.

> **mc4man said:**
> It's now 'built-in' and available by default - mesa changelog

Excellent news. Thanks

---

### Post by MacUntu on 2011-06-29
Thanks for the info. Now I know it's my (system's :P) fault.

---

