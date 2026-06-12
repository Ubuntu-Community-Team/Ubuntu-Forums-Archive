---
title: "Compiz-Fusion won't start in Hardy"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Kosimo on 2008-04-23
Hello!

A fresh new Hardy RC up to date, everything works quite well (even if not perfectly; PuseAudio still have some serious problems)... 
But what really sucks is the impossibility to enable compiz-fusion.  

I could run compiz fusion in my laptop since Fesity with no issues at all, (Radeon Mobility 9200)     But here in Hardy, when I try to enable, it says that Compiz can't be enabled.  

This is what I get after glxinfo: 

```
laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x57 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```


Any idea guys?

Thank you!

---

### Post by Ub1476 on 2008-04-23
What's the output you get by launching compiz from terminal? Direct rendering works so that shouldn't be a problem..

---

### Post by Kosimo on 2008-04-23
> **Ub1476 said:**
> What's the output you get by launching compiz from terminal? Direct rendering works so that shouldn't be a problem..

I also think so... But: This is what I get after "compiz" in terminal

```
$ compiz
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by Ub1476 on 2008-04-23
Are you sure ATI 9200 with the ATI driver works in an AIGXL session? You might have to install the fglrx driver to enable Compiz. You can also try to install XGL and use the ati driver, but I wouldn't recommend it..

If the card has been blacklisted for some reason (and yet shows no error in terminal..?), run compiz with this command:

```
compiz SKIP_CHECK=YES
```

---

### Post by Kosimo on 2008-04-23
> **Ub1476 said:**
> Are you sure ATI 9200 with the ATI driver works in an AIGXL session? You might have to install the fglrx driver to enable Compiz. You can also try to install XGL and use the ati driver, but I wouldn't recommend it..

If the card has been blacklisted for some reason (and yet shows no error in terminal..?), run compiz with this command:

```
compiz SKIP_CHECK=YES
```

I'm not using Ati Drivers at all, I'm using the default open source MESA drivers from Hardy.    It always run with no problems in Feisty and Gutsy. Just installing and working. Here in Hardy is where I get this error.

BTW: This is a video I made with this laptop in Feisty times: [http://youtube.com/watch?v=9ljGLu0LHSQ](http://youtube.com/watch?v=9ljGLu0LHSQ)

---

### Post by Ub1476 on 2008-04-23
Still tried the skip check option?

Ati, radeon and vesa are all open-source drivers. I believe they work for cards earlier than x800, but my x1400 has to use the new fglrx drivers to function "properly" (they don't yet really..).

You can see what driver is by opening "Screens and Graphics". It's probably hidden so you would have to edit the menus to show it.

Or just:

```
cat /etc/X11/xorg.conf
```

---

### Post by Kosimo on 2008-04-23
> **Ub1476 said:**
> Still tried the skip check option?

Ati, radeon and vesa are all open-source drivers. I believe they work for cards earlier than x800, but my x1400 has to use the new fglrx drivers to function "properly" (they don't yet really..).

You can see what driver is by opening "Screens and Graphics". It's probably hidden so you would have to edit the menus to show it.

Or just:

```
cat /etc/X11/xorg.conf
```


Hmmm... What I get is: 

```
cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbVariant"	"cat"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"

```

Isn't this a bug maybe?

---

### Post by Kosimo on 2008-04-23
Up!   

Any help guys?

---

### Post by myfigurefemale on 2008-04-23
since it sounds like it's your drivers that are the problem, try this:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

it detects and installs driver for you, updated to work with hardy.

---

### Post by Kosimo on 2008-04-24
up!  :(

---

### Post by ptelder on 2008-04-25
It's in [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/201330"). They say it won;t be fixed until at least Intrepid. In the meantime ATI chipsets in laptops have been blacklisted. You can try adding ```
SKIP_CHECKS=yes
``` to /etc/xdg/compiz/compiz-manager. Unfortunately that'll disable every other sanity check compiz does, but it brings the wobblies back.

---

### Post by Kosimo on 2008-04-25
> **ptelder said:**
> It's in [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/201330"). They say it won;t be fixed until at least Intrepid. In the meantime ATI chipsets in laptops have been blacklisted. You can try adding ```
SKIP_CHECKS=yes
``` to /etc/xdg/compiz/compiz-manager. Unfortunately that'll disable every other sanity check compiz does, but it brings the wobblies back.


Wow...

Shhhh*t !!!!   


Anyway... 


Thanks dude.. :(

---

