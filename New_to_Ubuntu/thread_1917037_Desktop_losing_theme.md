---
title: "Desktop losing theme"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by Drowz0r on 2012-01-29
Hello all

I'm on ubuntu 11.10 64 bit.

Any idea why my usual desktop theme changes? See image for exact-o detaili-os

[http://img715.imageshack.us/img715/3622/screenygu.png](http://img715.imageshack.us/img715/3622/screenygu.png)

It happens in a seemingly unprovoked way.

Thanks

---

### Post by kazztan0325 on 2012-01-29
Hi Drowz0r,

Did you try to set theme again with 'Advanced Settings (gnome-tweak-tool)' after the issue had occurred?

---

### Post by Frogs Hair on 2012-01-29
Try the following commands taken from the link . ```
sudo apt-get remove nautilus-open-terminal
``` ```
nautilus -q
```

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by Drowz0r on 2012-02-26
> **kazztan0325 said:**
> Hi Drowz0r,

Did you try to set theme again with 'Advanced Settings (gnome-tweak-tool)' after the issue had occurred?

Hello there

Sorry, where is advanced settings? Under Appearance none of the themes match the theme above, and changing the theme does nothing.

Thanks though

---

### Post by Drowz0r on 2012-02-26
> **Frogs Hair said:**
> Try the following commands taken from the link . ```
sudo apt-get remove nautilus-open-terminal
``` ```
nautilus -q
```[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

I ran it but had:

```
drowz0r@Prime:~$ sudo apt-get remove nautilus-open-terminal
[sudo] password for drowz0r: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nautilus-open-terminal is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libatk1.0-0:i386 libxcomposite1:i386 nspluginwrapper libnspr4-0d:i386
  libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386 libpixman-1-0:i386
  libxinerama1:i386 nspluginviewer:i386 libxft2:i386 libthai0:i386
  libjasper1:i386 libpango1.0-0:i386 libxcb-render0:i386 libxcursor1:i386
  libxcb-shm0:i386 libxrandr2:i386 libnss3-1d:i386 libgtk2.0-0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by kazztan0325 on 2012-02-27
> **Drowz0r said:**
> Hello there

Sorry, where is advanced settings? Under Appearance none of the themes match the theme above, and changing the theme does nothing.

Thanks though

Hi Drowz0r,
'Advanced Settings' is not installed by default.
You can install it with Software Center or Synaptic Package Manager.
The package name is **'gnome-tweak-tool'**.
Once you installed it, you would be able to search and launch it by typing **Advanced Settings** in Unity's Dash.

---

### Post by Frogs Hair on 2012-02-27
> **Drowz0r said:**
> I ran it but had:

```
drowz0r@Prime:~$ sudo apt-get remove nautilus-open-terminal
[sudo] password for drowz0r: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nautilus-open-terminal is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libatk1.0-0:i386 libxcomposite1:i386 nspluginwrapper libnspr4-0d:i386
  libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386 libpixman-1-0:i386
  libxinerama1:i386 nspluginviewer:i386 libxft2:i386 libthai0:i386
  libjasper1:i386 libpango1.0-0:i386 libxcb-render0:i386 libxcursor1:i386
  libxcb-shm0:i386 libxrandr2:i386 libnss3-1d:i386 libgtk2.0-0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

That package is being removed by default since the instruction was written
Just try the Nautilus restart command.```
nautilus -q
```

---

### Post by Drowz0r on 2012-02-28
> **Frogs Hair said:**
> That package is being removed by default since the instruction was written
Just try the Nautilus restart command.```
nautilus -q
```

After a bit of freaking out that seemed to work lovely. Thank you kindly.

Any idea why it happens? Seems kinda random and unprovoked.

---

