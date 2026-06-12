---
title: "Linux 3.0.0 in VirtualBox"
date: 2011-06-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by fabricator4 on 2011-06-17
I just let my VM install of Oneiric upgrade to the 3.0.0 kernel and it is now well broken.  Does anyone know if this is a purely VirtualBox problem or is there something else going on?

Chris

---

### Post by collisionystm on 2011-06-17
> **fabricator4 said:**
> I just let my VM install of Oneiric upgrade to the 3.0.0 kernel and it is now well broken.  Does anyone know if this is a purely VirtualBox problem or is there something else going on?

Chris


It is Oneiric. Same happend to mine. That's what happens when you are using an UNSTABLE version!!! 

Cheers

---

### Post by coffeecat on 2011-06-17
My virtual Oneiric is not broken - it's running with the latest 3.0.1 kernel and it was running with the 3.0.0 kernel. But I have lost the ability to boot into Unity 3d. Whichever I choose at the login screen I get taken to Unity 2d. I don't think it was the 3.0 kernel that did this. I'm fairly sure that I was still getting 3d with the 3.0.0 kernel yesterday, so I don't know what has broken 3d.

That's with VirtualBox 4.0.8, by the way.

**EDIT**: Just ran this is virtual Oneiric:

```
$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.3

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no
```Pity. It was working. :(

---

### Post by fabricator4 on 2011-06-17
Thanks guys, I was worried that VirtualBox was having issues with the 3.0 kernel.

Chris

---

### Post by coffeecat on 2011-06-17
Well....

I must admit that weird things happen in VirtualBox. I decided to re-install Oneiric in VB using this morning's daily alternate 64-bit ISO that I had successfully used to install to my laptop earlier today. The good news is that the install + booting into the installed desktop to update and then reboot and install guest-additions took less than half-an-hour. The other good news is that it was working (sort-of) with both the 3.0.0 and 3.0.1 kernels. The bad news (for me) is that I still can't get into 3d Unity. The weird news is that most of the icons are missing from the launcher. Just 4 - workspace switcher, Applications, Files & Folders and Trash. They were all there from the same ISO on my laptop.

:-k

---

### Post by Peter09 on 2011-06-20
> The bad news (for me) is that I still can't get into 3d Unity. The weird news is that most of the icons are missing from the launcher. Just 4 - workspace switcher, Applications, Files & Folders and Trash. They were all there from the same ISO on my laptop.

 
Yes, I have the same problems, I'm hoping some future upgrade will reslove it.

---

### Post by coffeecat on 2011-06-20
> **Peter09 said:**
> Yes, I have the same problems, I'm hoping some future upgrade will reslove it.

Thanks for posting that. I'm glad I'm not alone. I've tried re-installing into VirtualBox 2-3 times since with fresher dailies just to see what happens, and I'm still missing most of the launchers. Since they're not missing from my conventional laptop install I wonder if VirtualBox is eating them.

---

### Post by Peter09 on 2011-06-20
I did consider whether dropping down to Unity 2D used a different configuration file setup - therefore not picking up any 3d setup that existd

---

### Post by coffeecat on 2011-06-20
That's an interesting thought. I've just looked at my laptop Oneiric setup which was installed from the same ISO that's giving the lack of icons problem in VirtualBox. Logging into Unity 3d reveals the standard 10 + trash default icons together with a gnome-terminal launcher I had added. In Unity 2d in the same system, there are just the default 10 + trash launchers. So clearly there is a different configuration setup, but 2d Unity is not lacking the icons my VirtualBox 2d Unity is.

I was thinking about copying whatever configuration file(s) deal with this from my laptop Oneiric into my VB one, to see what happens. Except that I don't know where the configurations are for Unity 2d. I've looked in the hidden folders in home but couldn't see anything. Any ideas?

---

### Post by fabricator4 on 2011-06-22
> **coffeecat said:**
> Well....

I must admit that weird things happen in VirtualBox. I decided to re-install Oneiric in VB using this morning's daily alternate 64-bit ISO that I had successfully used to install to my laptop earlier today. The good news is that the install + booting into the installed desktop to update and then reboot and install guest-additions took less than half-an-hour. The other good news is that it was working (sort-of) with both the 3.0.0 and 3.0.1 kernels. The bad news (for me) is that I still can't get into 3d Unity. The weird news is that most of the icons are missing from the launcher. Just 4 - workspace switcher, Applications, Files & Folders and Trash. They were all there from the same ISO on my laptop.

:-k

I did a re-install of alpha 1 in VirtualBox.  When it updated it got the 3.0.1 kernel which appears to be working fine.  I haven't tried Unity 3D yet, but Unity 2D seems to be coming along well compared to the release that was available when 11.04 came out.

---

### Post by jerrrys on 2011-06-22
kernel 3o1 working fine in xubuntu guest.

---

### Post by nilarimogard on 2011-06-23
To get Unity 3D to work in VirtualBox, install alpha 1 and don't upgrade any X related packages.

---

