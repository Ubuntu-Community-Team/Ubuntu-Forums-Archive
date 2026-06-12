---
title: "Relative Performance - Version 14.04 - Ubuntu, Xubuntu, Lubuntu"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-04-21
I just installed the 14.04 versions of Ubuntu, Xubuntu, and Lubuntu on a USB hard disk.

The computer uses a nine year old motherboard with 2.66 GHz Celeron D CPU, 1G RAM, and SIS 661FX Motherboard graphics.  The graphics appear to have only 32MB of RAM that is apparently part of main memory.

Lubuntu works very nicely.  Xubuntu seems a little sluggish.  Ubuntu is so slow that it is not usable.  I can type way ahead in the text editor.  Everything is very slow to open, use, or shut down.

Any thoughts on the Ubuntu problem?  Is this simply the result of having a lower performance single core CPU with small cache combined with limited memory and on-board graphics?

Thanks for any thoughts.

---

### Post by Frogs Hair on 2014-04-21
Based on your graphics Lubutu would be the best choice. I did see a recent thread regarding sis graphics and will post the link when I find it again . ;)

[http://ubuntuforums.org/showthread.php?t=2215422&highlight=sis+graphics](http://ubuntuforums.org/showthread.php?t=2215422&highlight=sis+graphics)

[http://ubuntuforums.org/showthread.php?t=2130640&highlight=sis+graphics](http://ubuntuforums.org/showthread.php?t=2130640&highlight=sis+graphics)

---

### Post by KAWill70 on 2014-04-21
Thanks for passing along the two helpful links.  I also found a Ubuntu thread addressing a similar situation which was resolved by moving to a gnome metacity desktop.

[http://askubuntu.com/questions/450555/very-slow-graphics-performance-after-upgrade-12-04-14-04](http://askubuntu.com/questions/450555/very-slow-graphics-performance-after-upgrade-12-04-14-04)

I just added 500 MB memory to the motherboard and will see if that helps.  A memory test is currently running on that computer.  The two memory modules were not identical and for that reason I had only used the 1 GB module.  I think the risk is quite low as they have very similar specifications.

---

### Post by KAWill70 on 2014-04-21
Here is an update.  Adding 500 MB of memory did not have any noticeable effect.

I just discovered the commands listed below and it appears that my system is being software rendered.

If anyone is aware of a solution to that please let me know.

```
kent@kent-desktop:~$ lspci -k | grep -A3 VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
	Subsystem: Gigabyte Technology Co., Ltd SiS661FX GUI 2D/3D Accelerator

kent@kent-desktop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  2.1 Mesa 10.1.0

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
kent@kent-desktop:~$

```

---

### Post by ibjsb4 on 2014-04-21
> I also found a Ubuntu thread addressing a similar situation which was resolved by moving to a gnome metacity desktop.
 
I run a gnome-metacity desktop and I think its still too heavy for what you have.  Replacing compiz with metacity really cuts back on system demand, but the gnome packages you will run are inturn resource demanding and will drag your system down.

---

### Post by Braden_McCloskey on 2014-04-21
I hope I don't get some heat for saying this, but have you tried Elementary OS? I don't have a really old computer to test it on, but on my 4 year old laptop Elementary outperforms even Lubuntu.

---

### Post by KAWill70 on 2014-04-22
Thanks all for the help.  It does look like Lubuntu is my best choice with the older hardware.  Ubuntu might run a lot better if it was not software rendering as shown in the code that I posted.

I had not heard of Elementary OS and will look into it.  A few months ago I did try Bodhi Linux which may be along similar lines.  It ran very fast.

---

### Post by mastablasta on 2014-04-22
with a 32mb gpu lubuntu is the way to go. maybe xubuntu but not with default theme and setup.

---

### Post by William_Spickler on 2014-04-23
Same problem. Ubuntu 14.04 really creeps along but Ubuntu 12.04 was fine.
Hardware: Dell Dimension 3000, Pentium 4 at 2.8 Mhz with 1.2 Gb memory.
Graphics: Integrated Intel 82865G.
I've tried looking for a new graphics driver etc. but no joy.
When looking at system settings: Cog wheel on top right indicates - Gallium 0.4 on llvmpipe.
Cog wheel in launcher indicates - Intel® 865G x86/MMX/SSE2
I dont understand two different graphics settings.

I can't see going to a light weight OS when Ubuntu 12.04 worked fine.
It sounds like this may be a bug in 14.04.

Any suggestions before I go back to 12.04? Thanks.

Bill

---

### Post by KAWill70 on 2014-04-23
Here is a link to another thread I started that mentions 3D Drivers.  Apparently they were never available for SIS Graphics so that may be a large part of my problem.  The Unity desktop requires a 3D driver with the result that the 2D driver is used along with software rendering.

[http://ubuntuforums.org/showthread.php?t=2218977&p=12998591#post12998591](http://ubuntuforums.org/showthread.php?t=2218977&p=12998591#post12998591)

The key for Unity may be running the Unity_Support_Test and seeing the results similar to what I posted in the thread above.

---

### Post by William_Spickler on 2014-04-23
Well, it looks like the same problem.  I got the exact results that you showed in the other thread.

bill-ubuntu1@bill-ubuntu1:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  2.1 Mesa 10.1.0


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
bill-ubuntu1@bill-ubuntu1:~$ 

Someone may have an answer.

Bill

---

### Post by KAWill70 on 2014-04-23
Bill - I also hope we can learn more about Unity 3D support.  If your integrated i82865G graphics is older technology it may have insufficient memory and we also don't know if the drivers are 3D.

I just tested Ubuntu 14.04 on a brand new Win 7 computer with motherboard graphics and it ran extremely well.  Ubuntu was installed on an external USB disk.  Graphics was Intel HD 4600 and apparently has 1696 MB graphics memory versus 32 MB on my Linux computer.  The Win 7 computer does pass all of the Unity_Support_Test results.

There is an interesting subject called Swappiness which apparently can improve performance considerably in some cases.  It reduces the use of virtual memory on disk. I was hoping that would be a help but perhaps not if the 3D driver is the main issue.

---

