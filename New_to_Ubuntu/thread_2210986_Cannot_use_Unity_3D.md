---
title: "Cannot use Unity 3D"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by dovydas2 on 2014-03-13
I have a very bad performance on my ubuntu 13.10.
Running ```
/usr/lib/nux/unity_support_test -p
``` gives me
```
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
OpenGL version string:  2.1 Mesa 10.2.0-devel


Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes
Unity 3D supported:       no

```

It seems that Ubuntu thinks I am using VMware, but I am not, it is completely installed on my hard drive. How can I fix it to use proper graphics drivers?
I am using laptop with graphics cards:
```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev ff)

```

---

### Post by Bashing-om on 2014-03-13
dovydas2; Hi !

You have a "GF108M [GeForce GT 630M]" with optimus technology and running the open source "Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits) " driver. UHM .. maybe perhaps try a couple of Proprietary driver alternatives ?
There is this:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
However to consider, as many advise having better results in release 13.10 with Nvidia-Prime :
Versions 13.10/14.04 -> BumbleBee must be purged !
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

Keep in mind that to date Nvidia does not support linux with that optimus technology, no driver obtained from the Nvidia web site will work.
Your 630M is an Intel/Nvidia hybrid card, and it is not officially supported by Nvidia. See this link here for installing the drivers: Switchable laptop graphics issues on Ubuntu 12.04?
[http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310](http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310)

That is older info, but may still apply.

But hey !
[INDENT][INDENT]our developers are working
[INDENT][INDENT]hard to fill that gap
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Frogs Hair on 2014-03-13
Hello and Welcome 

Are there drivers available in Software Sources  >Additional Drivers ?  I can't tell if the vendor string is a  incorrect identification or not.  


Possibly Related. [http://askubuntu.com/questions/268569/ubuntu-12-04-detect-notebook-driver-as-vmware](http://askubuntu.com/questions/268569/ubuntu-12-04-detect-notebook-driver-as-vmware)

---

### Post by dovydas2 on 2014-03-13
Sadly none of the above solutions worked. Even when I installed Nvidia drivers, it still shows I use ```
Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
```

Frogs Hair, Yes, I can choose Nvidia or nouveau drivers, but it doesn't change anything, It still shows I use the same drivers.

By the way, forgot to mention that when booting Ubuntu, I get message ```
drm_pci_agp_init *ERROR* Cannot initialize the agpgart module
``` and then it still boots, I think it might be related and then it uses ```
Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
``` as a fallback.. But I am newbie on ubuntu, so I am not sure...

---

### Post by monkeybrain20122 on 2014-03-13
> **Frogs Hair said:**
> Hello and Welcome 

Are there drivers available in Software Sources  >Additional Drivers ?  I can't tell if the vendor string is a  incorrect identification or not.  




This is an Optimus machine, so never mind 'Additional Drivers' it wouldn't work. Bumblebee is the only way to go, but with bumblebee you need to install the driver in special way. Unfortunately (or rather, fortunately) I have never had an Optimus machine so I can't give more details.

P.S. For 13.10 there is also Nvidia-prime. Nvidia-prime doesn't do switching, just use the Nvidia card all the time so is prone to overheating while bumblebee allows switching on demand.

---

### Post by dovydas2 on 2014-03-13
Is there any way to completely restore the default Ubuntu graphics drivers? I can live without Nvidia graphics card, I just need the Intel card to work properly

---

### Post by monkeybrain20122 on 2014-03-13
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

You may also want to check out Bumblee's mailing list and related forum posts here. I am sorry that I can't be more specific, never used it myself.

---

### Post by Frogs Hair on 2014-03-13
A different flavor such as Xubuntu or Lubuntu would be an alternative unless you have your heart set on Unity. On the current installation gnome-session-flashback would be alternative.

---

### Post by monkeybrain20122 on 2014-03-13
> **Frogs Hair said:**
> A different flavor such as Xubuntu or Lubuntu would be an alternative unless you have your heart set on Unity. On the current installation gnome-session-flashback would be alternative.

Well graphic will still be problematic whatever DE he uses. It is a graphic driver problem, not that OP has a weak system that needs to run a light DE. The intel card alone should support Unity but because of Optimus the correct driver can't be installed. I would strongly suggest trying out bumblebee or Nvidia-prime. There is nothing to lose.

---

### Post by Frogs Hair on 2014-03-13
Xubuntu , Lubuntu and Flashback don't use Compiz and have lesser graphics requirements and are possible alternatives if the above suggestion doesn't work.

---

### Post by monkeybrain20122 on 2014-03-13
> **Frogs Hair said:**
> Xubuntu , Lubuntu and Flashback don't use Compiz and have lesser graphics requirements and are possible alternatives if the above suggestion doesn't work.

Less graphic requirement for the desktop, but if the underlying system is not working properly it will probably show somewhere (videos, games etc) so installing a plain de when the system is capable of a lot more is not the solution IMO. I have heard good things about bumblebe though I have never used it. If I have an optimus machine to mess with I will definitely try it first.

---

### Post by dovydas2 on 2014-03-13
Sorry for delay, had problems when I got black screen and couldn't do anything.
As of DE, previously I had Ubuntu running perfectly, then I decided to install Nvidia drivers and then all these problems started to happen. Then I did a lot of things from various tutorials to fix it, but neither of them helped. Tried to install bumblebee,  Nvidia-prime but I still get lags everywhere, from moving windows to simple jQuery animations in websites. After installing Nvidia-prime, in graphics settings it shows VESA: Intel® Sandybridge/Ivybridge Graphics as my graphics card driver, which I think is still not correct, BUT in terminal it is still showing the old one:
```
OpenGL vendor string:   VMware, Inc.OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
OpenGL version string:  2.1 Mesa 10.2.0-devel


Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       no



```

I even did upgrade to Ubuntu 14.04 alpha, still the same.
I am sure fresh reinstall would fix it, as it was working fine before, but I have lots of info and programs installed which I don't want to lose..

P.S. I am not sure, but this line ```
OpenGL vendor string:   VMware, Inc.
``` is as it should be? It mentions VMware, which is used to virtual mount, but I have Ubuntu installed on hard drive, so why does it think I am using VMware?

---

### Post by Yellow Pasque on 2014-03-14
> then I decided to install Nvidia drivers and then all these problems started to happen
So you need to uninstall the nvidia drivers to get back to having working intel graphics. How did you install the nvidia driver?

---

### Post by dovydas2 on 2014-03-15
Solved it by reinstalling Ubuntu, now it shows this and it is working great.
```
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string:  3.0 Mesa 9.2.1


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

---

### Post by Yellow Pasque on 2014-03-15
Now that you have working intel graphics, you can install bumblebee to increase your battery life (and use the nvidia GPU for demanding stuff like games).

---

### Post by dovydas2 on 2014-03-15
> **Temüjin said:**
> Now that you have working intel graphics, you can install bumblebee to increase your battery life (and use the nvidia GPU for demanding stuff like games).
Yeah, installed it and it is working great, thanks.

---

