---
title: "nvidia-common installed, but have intel graphics"
date: 2011-06-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-06-23
I'm having some minor video problems, i have intel graphics.  In searching for a solution i made this discovery.
```
aptitude search nvidia
p   nvidia-173                                             - NVIDIA binary Xorg driver, kernel module and VDPAU library       
p   nvidia-173-dev                                         - NVIDIA binary Xorg driver development files                      
p   nvidia-185-libvdpau-dev                                - Transitional package for nvidia-185-libvdpau-dev                 
p   nvidia-96                                              - NVIDIA binary Xorg driver, kernel module and VDPAU library       
p   nvidia-96-dev                                          - NVIDIA binary Xorg driver development files                      
p   nvidia-96-kernel-source                                - Transitional package for nvidia-glx-96-kernel-source             
p   nvidia-cg-toolkit                                      - Cg Toolkit - GPU Shader Authoring Language                       
i   nvidia-common                                          - Find obsolete NVIDIA drivers                                     
p   nvidia-current                                         - NVIDIA binary Xorg driver, kernel module and VDPAU library       
p   nvidia-current-dev                                     - NVIDIA binary Xorg driver development files                      
p   nvidia-glx-96                                          - Transitional package for nvidia-glx-96                           
p   nvidia-glx-96-dev                                      - Transitional package for nvidia-glx-96-dev                       
p   nvidia-settings                                        - Tool of configuring the NVIDIA graphics driver                   
v   nvidia-va-driver                                       -                                                    
```

nvidia-common is installed, Trying to remove it however
```
sudo apt-get remove nvidia-common
[sudo] password for buzzmandt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kubuntu-desktop nvidia-common
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 246 kB disk space will be freed.
Do you want to continue [Y/n]? 

```
It wants to remove kubuntu-desktop.

Is this a bug?


```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

```

---

### Post by Harry33 on 2011-06-23
No it is not a bug, but it is irritating.
You obviously do not need nvidia-common, but the desktop meta package depends on it.
You get rid of this only by uninstalling the desktop meta package.

---

### Post by buzzmandt on 2011-06-23
> **Harry33 said:**
> No it is not a bug, but it is irritating.
You obviously do not need nvidia-common, but the desktop meta package depends on it.
You get rid of this only by uninstalling the desktop meta package.

Thanks Harry.  Well, it's a bug if you ask me :confused:

---

### Post by Harry33 on 2011-06-23
> **buzzmandt said:**
> Thanks Harry.  Well, it's a bug if you ask me :confused:

Well sort of.
However, Ubuntu is full of similar adjustments.
There are a lot of meta packages out there.

---

### Post by cariboo on 2011-06-23
I wish people would get over the idea that a package that is installed, that they don't use is bothersome. I could see if you had a teeny hard drive, and space was a problem, but a full install still takes less than 5GiB, even a 10GiB hard drive is more than enough space for a useful installation.

What about all the small utilities in /usr/bin that many people never use, should we get rid of them too?

---

### Post by 3rdalbum on 2011-06-24
'nvidia-common' is installed to find obsolete versions of the Nvidia driver that could possibly cause problems.

It's quite necessary to prevent breakage on some people's systems, and takes up all of 188 kilobytes. If you had a 20MB HDD it would be a bit of a  nuisance, but then you wouldn't be running Ubuntu on a disk that small.

---

