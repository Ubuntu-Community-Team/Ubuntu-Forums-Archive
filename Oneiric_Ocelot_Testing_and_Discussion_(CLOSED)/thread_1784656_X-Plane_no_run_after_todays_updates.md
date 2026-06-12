---
title: "X-Plane no run after todays updates"
date: 2011-06-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-06-17
I updated this morning using sudo aptitude update && sudo aptitude safe-upgrade and after seeing it was not a complete update rebooted into recover and did fix broken packages.

 When I got back to the desktop I see unity is working but my Nvidia setting is missing from the launchpad because Nvidia current was removed in the fix broken packages. I look in synaptic to reinstall Nvidia current and it wants to remove all kinds of stuff so backed out of there.

X-Plane is looking for libGL.so.1 so is that part of Nvidia current?

```

bill@billsim-1110-64:~/X-Plane_9.70$ ldd ./X-Plane-i686
	linux-gate.so.1 =>  (0xf77c0000)
	libGL.so.1 => not found
	libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7731000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7722000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7607000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf75ff000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf75e5000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf75e1000)
	libm.so.6 => /lib32/libm.so.6 (0xf75bb000)
	libc.so.6 => /lib32/libc.so.6 (0xf745d000)
	/lib/ld-linux.so.2 (0xf77c1000)
	libGL.so.1 => not found
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7372000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7354000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf733b000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf7331000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf732d000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7326000)
bill@billsim-1110-64:~/X-Plane_9.70$ 


``` 

```

bill@billsim-1110-64:~/X-Plane_9.70$ date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p
Fri Jun 17 07:45:51 EDT 2011
Ubuntu oneiric (development branch)
Linux 3.0-0-generic
unity 3.8.16
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV92
OpenGL version string:  2.1 Mesa 7.10.3

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

Unity supported:          yes
bill@billsim-1110-64:~/X-Plane_9.70$

``` 

Thanks Bill

---

### Post by ronacc on 2011-06-17
libgl.so is part of libgl1-mesa-dev . After update and removal of nvidia-current that is still installed on my sys . but question , x-plane ? I don't see that in synaptic , what is it .

edit : google found it for me . looks like it needs opengl so it may not run on an UN-accelerated desktop .

---

### Post by sparker256 on 2011-06-17
> **ronacc said:**
> libgl.so is part of libgl1-mesa-dev . After update and removal of nvidia-current that is still installed on my sys . but question , x-plane ? I don't see that in synaptic , what is it .

edit : google found it for me . looks like it needs opengl so it may not run on an UN-accelerated desktop .

I did get to run by running the following commands.
```

cd /usr/lib32
sudo ln -s libGL.so libGL.so.1

```
Wow I usually get between 100 - 150 FPS. With this driver is less than 1 so I will have to wait until the nvidia current gets updated.

Bill

---

