---
title: "Graphics Unknown?"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-08-02
when I go under System Settings>Details>Graphics

It says graphics driver unknown.

I have a dell laptop that has intel 3000 graphics as well as a Nvidia Ge force GT 525M 525M graphics card.

What Can I do to fix this? I tried downloading a driver and installing it but it didn't go well.

---

### Post by anewguy on 2012-08-02
I would try going to additional drivers.  It needs an internet connection.  It should tell you after a little while if a graphics driver is available - if so, be sure to enable it (it will take a while).

---

### Post by blade4 on 2012-08-02
Download the latest drivers from the x-swat ppa 

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```  
```
sudo apt-get update 
```
```
sudo apt-get install nvidia-settings nvidia-graphics-drivers nvidia-current 
```

Hope this helps 

Cheers

---

### Post by mastablasta on 2012-08-03
> **TheMTtakeover said:**
>  
I have a dell laptop that has intel 3000 graphics as well as a Nvidia Ge force GT 525M 525M graphics card.
.
is this Nvidia Optimus technology? if so, you need bumblebee and even with that one it might not work.

---

### Post by NikTh on 2012-08-03
Hi , 
same here. 
Do not bother of what this window says. Probably a bug . 
Trust the terminal. 
```
lspci -nnk | grep -iA2 vga
/usr/lib/nux/unity_support_test -p
```My results ```
VGA compatible controller [0300]: **Intel** Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0601]
    **Kernel driver in use: i915**
``````
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI **Intel(R)** Ironlake Mobile 
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

Thanks

---

### Post by Frogs Hair on 2012-08-03
If using a proprietary driver the graphics card information will be displayed in the Nvidia X Sever Settings , ATI , or Intel counter part . The same may be true for the monitor settings.

---

### Post by 3177 on 2012-08-03
please post the output of```
lspci
```

---

### Post by idoitprone on 2012-08-03
it is probably optimus

> sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia bbswitch

---

### Post by gordintoronto on 2012-08-03
> **TheMTtakeover said:**
> when I go under System Settings>Details>Graphics

It says graphics driver unknown.

I have a dell laptop that has intel 3000 graphics as well as a Nvidia Ge force GT 525M 525M graphics card.

What Can I do to fix this? I tried downloading a driver and installing it but it didn't go well.

"Graphics driver unknown" is normal, ignore it.

What version of Ubuntu?

+1 to Bumblebee.

---

### Post by cprofitt on 2012-08-03
> **TheMTtakeover said:**
> when I go under System Settings>Details>Graphics

It says graphics driver unknown.

I have a dell laptop that has intel 3000 graphics as well as a Nvidia Ge force GT 525M 525M graphics card.

What Can I do to fix this? I tried downloading a driver and installing it but it didn't go well.


Your drivers are included with the kernel. For  this reason you do not have to install any proprietary drivers via  'Additional Drivers'.
  If you would like you can add the following:[INDENT]   ```
sudo apt-get install mesa-utils
``` [/INDENT]This will enable information to be displayed about your drivers in System Information.
  I have never bothered though so it is totally optional to do so.

---

