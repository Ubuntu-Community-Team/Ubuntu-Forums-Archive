---
title: "openGL not working, BadRequest error"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by dransom90 on 2013-01-20
I'm trying to run an openGL program but I keep getting this message:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  34 ()
  Serial number of failed request:  34
  Current serial number in output stream:  33

What is going on and how do I fix it?  Thanks for your help!

---

### Post by NikTh on 2013-01-20
Hi ,
more informations will help to solve the problem.. 

Open a terminal and apply the commands 
```
lsb_release -rcd ; uname -r
lspci -nnk | grep -iA2 vga
sudo apt-get install mesa-utils
glxinfo | grep -i render
``` 

 _Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")
 

Thanks

---

### Post by dransom90 on 2013-01-20
Here's what I got after applying those commands:
```

Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
3.2.0-36-generic

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
	Subsystem: Hewlett-Packard Company Device [103c:30cc]
	Kernel driver in use: i915

Reading package lists... Done
Building dependency tree       
Reading state information... Done
mesa-utils is already the newest version.
mesa-utils set to manually installed.
The following package was automatically installed and is no longer required:
  wine-gecko1.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965GM x86/MMX/SSE2
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 


```

---

### Post by NikTh on 2013-01-21
I cannot see any specific problem , your card seems to recognized correctly and driver loaded correctly. 

What about openGL version ? 

Give the results of this command 
```
/usr/lib/nux/unity_support_test -p
``` 
Thanks

---

### Post by dransom90 on 2013-01-22
```

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 8.0.4

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

### Post by NikTh on 2013-01-22
Maybe that program you attempted to run  , wants later version of OpenGL ? 

For example , steam for Linux (If I remember correctly) wants OpenGL > = 3.0 to run properly. 

Thanks

---

### Post by dransom90 on 2013-01-22
Sorry for a stupid question but what's the best way to update openGL?

---

### Post by NikTh on 2013-01-23
> **dransom90 said:**
> Sorry for a stupid question but what's the best way to update openGL?

I think you cannot. Someone will correct me If I'm wrong , but I think you cannot update the OpenGL (except if you are a developer maybe). 

OpenGL is hardware and driver specific , so Intel made this driver (i915) to support for the specific card of yours the OpenGL 2.1. 

I have an Intel Ironlake in my Laptop and I have the same problem , I mean I cannot use OpenGL > of 2.1 (even with latest devel - MESA). 

So is not mesa problem , is Intel's problem , or if you are a developer (know programming.. etc) you can re-write the driver (i915) for your card to use newer OpenGL version. (Intel's driver is Open Source so the code is available). 

Thanks

---

