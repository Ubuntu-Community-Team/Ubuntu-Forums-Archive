---
title: "Installing 8.04 Nvidia drivers!"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by djowtlawz on 2008-04-27
Hi I finally got Hardy Heron to work and I am now trying to install the Nvidia drivers. I have done this before in 7.10 Gutsy Gibbon without a hitch. Now I get an error about missing kernels and it looks something like this

> ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.

I have installed some kernel files in the synaptic but none of them work. Help is there anything I can do?

---

### Post by Perfect Storm on 2008-04-27
Any reason why you don't use the nvidia that comes (via synaptic, restricted) Ubuntu?

---

### Post by djowtlawz on 2008-04-27
> **Artificial Intelligence said:**
> Any reason why you don't use the nvidia that comes (via synaptic, restricted) Ubuntu?

I don't trust them because in 7.10 they never worked and kept restarting my computer.

edit: I tried installing them to no avail. It keeps telling me my grafx card cannot be detected.

---

### Post by Perfect Storm on 2008-04-27
ok.

Install **xserver-xorg-dev**

---

### Post by jacob01 on 2008-04-27
i noticed that the drivers from synaptic and the restricted drivers are not as fast as the latest nvidia drivers from the site

---

### Post by milia on 2008-04-27
> **djowtlawz said:**
> Hi I finally got Hardy Heron to work and I am now trying to install the Nvidia drivers. I have done this before in 7.10 Gutsy Gibbon without a hitch. Now I get an error about missing kernels and it looks something like this


I have installed some kernel files in the synaptic but none of them work. Help is there anything I can do?

**First of all**, [[COLOR="Red"]read this sticky[/COLOR]](http://www.nvnews.net/vbulletin/showthread.php?t=72490) from nvidia news forum (the **"Debian GNU/Linux or [K]Ubuntu with Xorg 7.x"** section)


---------------------------------


Have you installed the appropriate **linux-headers** packages ?

**[COLOR="Red"]Beware[/COLOR]**, they [COLOR="Red"]***must***[/COLOR] be the same version as the version you get by typing

```
uname -a
```


Also, if you've installed the above headers that match with your current 
kernel, installing the drivers is easy if you find the location of the headers, using mlocate or slocate to find the correct path.
 It will propably be something like */usr/src/linux-headers-yours_kernel_version*.

```
milia@Archimedes:~$ uname -a
Linux Archimedes 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

milia@Archimedes:~$ mlocate linux-headers
```

And I get lines like the following:

```

.
.
.
/usr/src/linux-headers-2.6.24-16-generic/scripts/mod/empty.o
/usr/src/linux-headers-2.6.24-16-generic/scripts/mod/file2alias.c
/usr/src/linux-headers-2.6.24-16-generic/scripts/mod/file2alias.o
/usr/src/linux-headers-2.6.24-16-generic/scripts/mod/mk_elfconfig
/usr/src/linux-headers-2.6.24-16-generic/scripts/mod/mk_elfconfig.c
/usr/src/linux-headers-2.6.24-16-generic/scripts/mod/modpost
.
.
.
```

Afterwards you just type in a console:
```

sudo sh NVIDIA-Linux*.sh --kernel-source-path /usr/src/linux-headers-yours_kernel_version
```

,where NVIDIA-Linux*.sh is the shell script you've downloaded from
Nvidia's site and it should install the drivers.

I've installed the latest 173.08 (beta) Nvidia drivers on my 32bit Ubuntu 8.04, but no luck again...

Before doing the above mentioned, I tried the nvidia-glx-new drivers + the properiarty (restricted drivers etc), but no luck either.

**Since none of the above worked for me,** maybe you should do a bit googling first. I'm sure someone will have posted something similar for
Gutsy 7.10, which methodology will work in 8.04 as well.

---

### Post by djowtlawz on 2008-04-27
This clears things up a freaking ton. Because although I have the latest kernel *.24.16, I've been only able to load ubuntu with the old kernel *.24.14. This clears things up alot. I never realised they were connected in that manner.

Thanks! Time to try it out now

---

### Post by djowtlawz on 2008-04-27
Seems I have a problem. I am booting with the *24.14 kernel and I cannot install the *24.14 linux headers because it says its using the latest version already (*24.16)

---

### Post by milia on 2008-04-28
> **djowtlawz said:**
> Seems I have a problem. I am booting with the *24.14 kernel and I cannot install the *24.14 linux headers because it says its using the latest version already (*24.16)

You could uninstall the headers of the kernel you don't use
and then install the ones that match with your current kernel:

```
sudo apt-get purge linux-headers-*24.16
sudo apt-get install linux-headers-*24.16
```

---

### Post by djowtlawz on 2008-04-28
Solved, thx ^

---

### Post by milia on 2008-04-30
> **djowtlawz said:**
> Solved, thx ^

Great :D

You could now put a "[SOLVED]" at the start of the title of your thread :).

---

