---
title: "Added Oibaf/graphics-drivers ppa but they're still not in use after re-boot"
date: 2020-06-19
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-06-19
Hello all,

So i added the Oibaf graphics drivers PPA as apparently it's good stuff, I'm not really sure what the benefit of it is though.

Is it that the generic graphics drivers provided by Ubuntu are not maintained or updated?

Anyway I've got enough Ubuntu related stuff to learn about ATM so I just went ahead and added the PPA and then updated / upgraded just to see if they would give any tangible benefit, but after re-booting I ran...```
glxinfo | grep OpenGL
```...and the output still read "OpenGL vendor string: X.Org" which I understand basically means that the newly installed drivers aren't in use.

What could be the cause of this? I took a Timeshift snapshot previous to adding the PPA and just restored that so as to avoid complication further down the line, but I'd like to have a second go at installing the alternative drivers if anyone can advise...

**Edit: Sorry, as people have pointed out I forgot to add my spec's, I've not got a discrete GPU, it's an AMD E2-1800 APU with Radeon HD integrated graphics**

---

### Post by deadflowr on 2020-06-19
So what's the gpu card?
All we know is you added the ppa drivers, but we know nothing else.

---

### Post by CelticWarrior on 2020-06-19
Please post you hardware specifications, in this case the graphics.

---

### Post by GhX6GZMB on 2020-06-19
oibaf only provides free drivers and updates. If your machine needs a proprietary/non-free graphics driver, sorry, but no cigar.

---

### Post by CatKiller on 2020-06-19
> **jcdenton1995 said:**
> So i added the Oibaf graphics drivers PPA as apparently it's good stuff, I'm not really sure what the benefit of it is though.

The open source graphics stack (so not the Nvidia one) is Mesa. Because Ubuntu isn't rolling release, the version of Mesa is fixed (except for the Hardware Enablement stack) for the Ubuntu version. The Oibaf PPA is one of several PPAs that have newer versions of Mesa. You might use one of them if you've got a newer AMD or Intel GPU that isn't supported by the older Mesa, or some particular bugfix.

---

### Post by jcdenton1995 on 2020-06-19
> **deadflowr said:**
> So what's the gpu card?
All we know is you added the ppa drivers, but we know nothing else.

> **CelticWarrior said:**
> Please post you hardware specifications, in this case the graphics.

Apologies to both, I've not got a discrete graphics card. It's a pokey little AMD E2-1800 APU with Radeon HD Graphics

> **CatKiller said:**
> The open source graphics stack (so not the Nvidia one) is Mesa. Because Ubuntu isn't rolling release, the version of Mesa is fixed (except for the Hardware Enablement stack) for the Ubuntu version. The Oibaf PPA is one of several PPAs that have newer versions of Mesa. You might use one of them if you've got a newer AMD or Intel GPU that isn't supported by the older Mesa, or some particular bugfix.

I see, does it not also include updated drivers for older graphics hardware, that allows them to work with newer versions of OpenGL, or is it the case that the newer versions use features that older hardware just doesn't have? (especially my old APU cracker) Sorry if that makes no sense, I haven't had chance to read into it much yet, save for [this really great introduction]("https://blogs.igalia.com/itoral/2014/07/29/a-brief-introduction-to-the-linux-graphics-stack/").

---

### Post by GhX6GZMB on 2020-06-19
For Radeon graphics, oibaf supports those. Check that you don't have a typo in your PPA, it should look like this:

```
http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu bionic main
```

There are almost daily upgrades to Radeon and AMD graphics; also older chips (my laptop is 12 years old...).

---

### Post by jcdenton1995 on 2020-06-20
> **ml9104 said:**
> For Radeon graphics, oibaf supports those. Check that you don't have a typo in your PPA

The package actually installed fine, I used the command...```
sudo apt-add-repository ppa:oibaf/graphics-drivers
```...before updating and upgrading, it installed a lot of lib files and seemed to have worked fine, but it's just that after re-booting it was still using the old drivers.

> There are almost daily upgrades to Radeon and AMD graphics; also older chips (my laptop is 12 years old...).

Cool, have yous seen any benefit from using them over the included drivers?

---

### Post by Holger_Gehrke on 2020-06-20
I think you're looking at the wrong part of the output of glxinfo. The right info is probably a line saying 'Version:' followed by a number in the section headed 'Extended renderer info (GLX_MESA_query_renderer):'. On a XUbuntu 18.04 with an AMD E2 with the HWE but without drivers from any ppa this section looks like this
```

Extended renderer info (GLX_MESA_query_renderer):
    Vendor: X.Org (0x1002)
    Device: AMD KABINI (DRM 2.50.0, 5.3.0-59-generic, LLVM 9.0.0) (0x9850)
    **Version: 19.2.8**
    Accelerated: yes
    Video memory: 1024MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 4.5
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2

```

Holger

---

### Post by Yellow Pasque on 2020-06-20
> **jcdenton1995 said:**
> but after re-booting I ran...glxinfo | grep OpenGL...and the output still read "OpenGL vendor string: X.Org" which I understand basically means that the newly installed drivers aren't in use.

You misunderstand. X.org is the correct vendor for open-source AMD drivers. And using a newer mesa version in oibaf PPA is not going to change that. Use this command for better info:
```
glxinfo -B
```

> I see, does it not also include updated drivers for older graphics hardware, that allows them to work with newer versions of OpenGL?
Yes, it includes the latest version of mesa. It could possibly allow newer OpenGL versions on older Radeon GPU's, but I wouldn't get too excited about that on a laptop GPU. Just because you can launch an OpenGL 4.x game, it doesn't mean it's going to be playable.

---

### Post by jcdenton1995 on 2020-06-20
> **Holger_Gehrke said:**
> I think you're looking at the wrong part of the output of glxinfo

[QUOTE=Yellow Pasque]You misunderstand. X.org is the correct vendor for open-source AMD  drivers. And using a newer mesa version in oibaf PPA is not going to  change that.[/QUOTE]

Thanks. Yes your right, I saved the output of glxinfo -B and then updated the drivers again and compared it with the new glxinfo -B output, and the Mesa version number had gone up, and the oibaf ppa string was in there - my bad!

Just to clarify, when the PPA says it provides updated drivers, does it mean drivers as in low level device drivers, or does driver simply mean the rest of the graphics stack i.e Mesa / OpenGL?

---

