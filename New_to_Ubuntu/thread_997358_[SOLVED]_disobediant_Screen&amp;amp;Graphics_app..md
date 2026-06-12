---
title: "[SOLVED] disobediant Screen&amp;amp;Graphics app."
date: 2008-11-29
forum: New to Ubuntu
---

### Post by nnjond on 2008-11-29
Hi, Can anyone help me?

I've installed Ibex with a new graphics card ( GeForce FX 5500), but Ive lost the 1600X1200 res @75Hz for my Dell P1130 monitor. I've found the Screen & Graphics app in Places> Computer> Filesystem> usr> share> applications -and I can click all the right menus but they revert  back to 

800X600 @ 60 Hz plugn play.

Thanks

---

### Post by beno1990 on 2008-11-29
Have you installed the nVidia graphics card driver? You have to do it manually from the repos.

---

### Post by HullDown on 2008-11-29
I had similar issues with my Gateway monitor and GeForce.  A couple of things to check for: 

1) You have NVIDIA hardware enabled.  System > Administration > Hardware Drivers. If NVIDIA accelerator is not on the list, go to repositories and get it. 

2) Once NVIDIA is working, go through System > Administration > NVIDIA X Server Settings.  Make adjustments to set up.  I found that sometimes you just have to fight to get the settings to save, but with enough time you win. 

Hope that helps.

---

### Post by nnjond on 2008-11-29
I think i've installed the driver, but don't know how to "run as root"

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by beno1990 on 2008-11-29
```

sudo nvidia-xconfig

```

Any command preceded with "sudo" will be executed as if you were logged in as root (administrator/superuser) account.

---

