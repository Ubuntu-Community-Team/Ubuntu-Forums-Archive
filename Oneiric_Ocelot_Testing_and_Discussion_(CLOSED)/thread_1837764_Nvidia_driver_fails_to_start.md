---
title: "Nvidia driver fails to start"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Hideaki on 2011-09-02
I just did a clean install of Ubuntu 11.10 Beta. I tried to install the Nvidia-current driver using Jockey but I just booted back into Unity 2D using Nouveu. When I run nvidia-settings I get an error saying the nvidia driver is not active, and to try running nvidia-xconfig.

Running nvidia-xconfig and rebooting stops X from starting up. Manually attempting to start X just gives an error saying the nvidia kernel module could not be loaded. 
Uninstalling and re-installing does nothing(I tried using jockey, synaptic, and apt), and using nvidia-current-update causes the exact same results.

Output for lspci | grep VGA

```
01:00.0 VGA compatible controller: nVidia Corporation GF104 [GeForce GTX 460] (rev a1)

```

Is there an issue with the current nvidia packages? Everything was running correctly on 11.04.

---

### Post by Hideaki on 2011-09-02
Some more info.

Important part of Xorg.0.log:
```

[   741.720] (II) LoadModule: "nvidia"
[   741.720] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   741.721] (II) Module nvidia: vendor="NVIDIA Corporation"
[   741.721]    compiled for 4.0.2, module version = 1.0.0
[   741.721]    Module class: X.Org Video Driver
[   741.723] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[   741.725] (EE) NVIDIA:     system's kernel log for additional error messages.
[   741.726] (II) UnloadModule: "nvidia"
[   741.726] (II) Unloading nvidia
[   741.726] (EE) Failed to load module "nvidia" (module-specific error, 0)

```

dkms status output:
```

nvidia-current, 280.13, 3.0.0-9-generic, x86_64: installed

```

I really don't understand what is going on. Everything seems to be configured correctly, the system just refuses to load the nvidia module.

---

### Post by dino99 on 2011-09-02
better to remove xorg.conf

sudo apt-get install --reinstall dkms nvidia-current-updates

---

### Post by Hideaki on 2011-09-02
I just tried that, didn't change a thing. It still loads nouveu.

Current xorg.conf file:
```

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection

```

Adding Driver "nvidia" stops X from starting up, removing the xorg.conf file entirely gives the same result as with the above xorg.conf settings.

---

### Post by cariboo on 2011-09-02
From your error message it says that the nvidia module isn't being loaded. Did you try to load the module manually:

```
sudo modprobe nvidia
```

If the module gets loaded correctly you won't see any messages.

if that doesn't work. Open a terminal and type:

```
sudo apt-get --reinstall nvidia-current
```

and watch the output to see if it builds properly and gets loaded.

---

### Post by Hideaki on 2011-09-02
I just did a complete re-install of 11.10 Beta 1, then installed nvidia-current-updates as normal and got the exact same result.

sudo modprobe nvidia:
```

FATAL: Module nvidia not found.

```

sudo modprobe nvidia-current-updates:
```

FATAL: Error inserting nvidia_current_updates (/lib/modules/3.0.0-9-generic/updates/dkms/nvidia-current-updates.ko): No such device

```

Reinstalling gives no errors. The module builds fine.
```

hideaki@Yurippe:~$ sudo apt-get install --reinstall nvidia-current-updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/55.2 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 119359 files and directories currently installed.)
Preparing to replace nvidia-current-updates 280.13-0ubuntu2 (using .../nvidia-current-updates_280.13-0ubuntu2_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current-updates ...
Processing triggers for man-db ...
Setting up nvidia-current-updates (280.13-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-updates-280.13 DKMS files...
Building only for 3.0.0-9-generic
Building for architecture x86_64
Building initial module for 3.0.0-9-generic
Done.

nvidia-current-updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-9-generic/updates/dkms/

depmod....

DKMS: install Completed.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-9-generic
W: Possible missing firmware /lib/firmware/nouveau/fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409c for module nouveau

```

---

### Post by Neo40 on 2011-09-02
I have the same problem. :(

---

### Post by cariboo on 2011-09-02
@Hideaki, you can ignore the nouveau firmware errors, do things work now?

---

### Post by Hideaki on 2011-09-02
> **cariboo907 said:**
> @Hideaki, you can ignore the nouveau firmware errors, do things work now?

Nope, exact same results.

@Neo40: What nVidia card do you have? Is it a GTX460 by any chance?

---

### Post by 23dornot23d on 2011-09-02
I just loaded the latest updates in

  to see what happens and it runs ok on a Nvidia 9300 GS M ......

[**SCREENSHOT**]("http://img801.imageshack.us/img801/9610/screenshot20at202011090.jpg")

was hoping it would do the same here so I could work out what was happening ..... 

Gnome shell is still working after a aptitude safe-upgrade too .....

Conky is a little messed up - but it does this from system to system ..... 
the Time Fonts SIZE has gone extremely small though its usually the biggest on the display..

---

### Post by Hideaki on 2011-09-02
> **23dornot23d said:**
> I just loaded the latest updates in

  to see what happens and it runs ok on a Nvidia 9300 GS M ......

[**SCREENSHOT**]("http://img801.imageshack.us/img801/9610/screenshot20at202011090.jpg")

was hoping it would do the same here so I could work out what was happening ..... 

Gnome shell is still working after a aptitude safe-upgrade too .....

Conky is a little messed up - but it does this from system to system ..... 
the Time Fonts SIZE has gone extremely small though its usually the biggest on the display..

You are way ahead of us. Your drivers are loading fine. The issue I'm running into is that the nvidia drivers won't load at all.

[http://imageshack.us/photo/my-images/820/screenshot20at202011090.png/](http://imageshack.us/photo/my-images/820/screenshot20at202011090.png/)

---

### Post by 23dornot23d on 2011-09-02
I did take screenshots as they were loading to try to see if there was anything odd happening ..... but
other than a directory name change all seems normal ...... this is 64 bit ...

[IMG]http://img10.imageshack.us/img10/7824/loadgg.jpg[/IMG]


Just ensure the things you need are there ...... the current kernel headers etc .... search on kernel in synaptic look for 3.0.0-9
just to be sure they loaded in ok .........

also try this as cariboo said and post the output .... there was a stage where we were having to re-install straight after
a install ...... but I thought that was fixed now .....

```

sudo apt-get --reinstall nvidia-current

```

---

### Post by Hideaki on 2011-09-02
> **23dornot23d said:**
> I did take screenshots as they were loading to try to see if there was anything odd happening ..... but
other than a directory name change all seems normal ...... this is 64 bit ...

[IMG]http://img10.imageshack.us/img10/7824/loadgg.jpg[/IMG]


Just ensure the things you need are there ...... the current kernel headers etc .... search on kernel in synaptic look for 3.0.0-9
just to be sure they loaded in ok .........

also try this as cariboo said and post the output .... there was a stage where we were having to re-install straight after
a install ...... but I thought that was fixed now .....

```

sudo apt-get --reinstall nvidia-current

```

3.0.0-9 headers are installed. I posted the output you asked for already, check a few posts back. Everything installs correctly.

I've also tried adding the xorg-edgers PPA to install the latest nvidia beta drives, didn't change a thing, same issue.

---

### Post by 23dornot23d on 2011-09-02
Have a look at this thread ..... [[COLOR=Red]**LINK**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1813224&highlight=nvidia+headers")

Towards the end is the answer that I used this was a while back now when the 3.0.0-7 kernel was out
and my Nvidia card was not working ..... giving similar results that you are seeing now ......

It basically boiled down to blacklisting the Nouveau drivers ...... but its worth having a look through.

Sometimes we cannot be positive of what exactly did fix a problem .

Maybe tomorrows upgrade may fix it who knows ....

But if you go to the end of the threads in the link I have provided ..... there may lie a solution.

It certainly seems very similar - from what you have posted ......

---

### Post by Neo40 on 2011-09-03
> **Hideaki said:**
> Nope, exact same results.

@Neo40: What nVidia card do you have? Is it a GTX460 by any chance?


I have a laptop with NVIDIA GeForce Go 6150

---

### Post by Hideaki on 2011-09-03
> **23dornot23d said:**
> Have a look at this thread ..... [[COLOR=Red]**LINK**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1813224&highlight=nvidia+headers")

Towards the end is the answer that I used this was a while back now when the 3.0.0-7 kernel was out
and my Nvidia card was not working ..... giving similar results that you are seeing now ......

It basically boiled down to blacklisting the Nouveau drivers ...... but its worth having a look through.

Sometimes we cannot be positive of what exactly did fix a problem .

Maybe tomorrows upgrade may fix it who knows ....

But if you go to the end of the threads in the link I have provided ..... there may lie a solution.

It certainly seems very similar - from what you have posted ......

That did it! Thanks for the help!

I added 
```

blacklist nouveau

```
to /etc/modprobe.d/blacklist.conf

Rebooted and the nvidia drivers loaded fine! I figured nouveau was already blacklisted since the same line appears in /etc/modprobe.d/nvidia-graphics-drivers.conf, but it seems like that file is not being read correctly at the moment.

---

### Post by 23dornot23d on 2011-09-03
Glad that sorted it for you ..... :)

---

