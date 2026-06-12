---
title: "glxgears doesn't work"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by paeppi.p on 2008-09-16
Hi,

it seems I have the same problem as discussed by 900donuts and Xerp in the thread "3d software dosen't work" of July 23rd.

In order to activate 3D acceleration I have enabled the driver in the hardware driver manager. The following tests yield these results.

> glxinfo | grep rendering
3:direct rendering: Yes

> glxgears
Illegal instruction

I understand Xerp's hint to use an older nVidia driver.
Would that be the solution for my problem? Where can I obtain it?

I appreciate any help.

Cheers,
Peter

See below details about my environment.

Ubuntu 8.04 LTS (Hardy Heron)

> lspci | grep VGA
15:01:05.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

> cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 4
model name	: AMD Athlon(tm) processor
stepping	: 2
cpu MHz		: 1196.698
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
bogomips	: 2395.70
clflush size	: 32

 > glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program,

---

### Post by HousieMousie2 on 2008-09-16
I don't recall what kind of 3D the legacy drivers support, might not be much if any, but they are in multiverse.  Adept, Synaptic and KPackage will each list them, just search for "nvidia-" (omit the quotation marks) and it will show you a long list of drivers, the ones with "legacy" are what you are looking for... like "nvidia-glx-legacy."  Again, not sure if this will help you, but it is worth a shot.

I don't know where the "break point" for nVidia cards is... I use the nvidia-glx-new drivers for a 6800 variety.

Good luck!

---

### Post by alienexplorers on 2008-09-16
First go to synaptic and load envyng-core and envyng-gtk.  Run from Applications -> System Tools -> envyng.  Select to disable and drivers you have loaded.  Since I have the same card as you I choose to do a manual install of the 96.xx.xx driver.  Reboot when complete.  Run from terminal:
> gksudo nvidia-settings
Select the resolution you want and apply it and then save it to xconfiuration file.  Reboot and see what happens.

---

### Post by paeppi.p on 2008-09-16
Thanks to both of you. 

I have followed the steps suggested by alienexplorers. 
With nVidia driver version 96.43.05 now installed, glxgears works perfectly.

I wanted 3D acceleration for the sake of using Google Earth. This works, too.

Cheers,
Peter

---

