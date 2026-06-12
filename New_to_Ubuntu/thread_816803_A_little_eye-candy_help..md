---
title: "A little eye-candy help."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-03
Alright, well I've kind of established with myself that I can't add any visual effects onto my system. What I was wondering is, can I add the better-looking panels? 
Such as the one in this picture: 
[http://www.supriyadisw.net/wp-content/uploads/ubuntu_osx02.jpg]("http://www.supriyadisw.net/wp-content/uploads/ubuntu_osx02.jpg")

Or are the visual effects intertwined with the ability to change the way the panels look.

---

### Post by PinkFloyd102489 on 2008-06-03
The bar on the bottom is called Avant Window Navigator, or AWN.

---

### Post by adobrakic on 2008-06-03
I've installed it from synaptic, but when I try to open it, all that happens is a black box pops up in the upper left-hand corner of my screen and dissappears.

---

### Post by PinkFloyd102489 on 2008-06-03
You may have to compile from source. There's a few guides floating around on how to do it, especially in Desktop Effects & Customization.

---

### Post by SunnyRabbiera on 2008-06-03
AWN needs compositing, now if you want to use desktop effects they are pre installed with ubuntu.
If you were lead astray we can help you get effects working if at all possible as some graphics cards dont work that well.

---

### Post by adobrakic on 2008-06-03
Ah, yeah I have a ProSavage (or something close to that) graphics card, and I really doubt I can get the effects to work.

---

### Post by SunnyRabbiera on 2008-06-03
sounds obscure, I never even heard of them.

---

### Post by rolnics on 2008-06-03
> **adobrakic said:**
> Ah, yeah I have a ProSavage (or something close to that) graphics card, and I really doubt I can get the effects to work.

Hmmm . . that sounds like an early geforce card to me, but I might be wrong. But I would have thought that you would be able to change the themes of your setup? What's the spec of the pc that might give us more a a clue.

Might see what I can do on that old dell I'm running at the moment, it's only a P3 and graphics is running at 800x600 :( Be interesting to see what it wouldn't do, until fix my other pc.

---

### Post by adobrakic on 2008-06-03
I really don't know a lot about the specs, other than i have 735(about)mb of RAM, and 1.67gHz

---

### Post by philinux on 2008-06-03
You need to post the output of

lspci

---

### Post by adobrakic on 2008-06-03
```
ado@ado-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
ado@ado-desktop:~$ 

```

---

### Post by philinux on 2008-06-03
I think you might be struggling with that gpu card

What does

glxinfo

and 

glxgears

report.

---

### Post by adobrakic on 2008-06-03
glxinfo:
```
ado@ado-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
OpenGL vendor string: S3 Graphics Inc.
OpenGL renderer string: Mesa DRI ProSavageDDR 20061110 AGP 1x x86/MMX+/3DNow!+/SSE
OpenGL version string: 1.2 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_compression, GL_ARB_texture_env_add, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_IBM_texture_mirrored_repeat, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x43 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
Segmentation fault
ado@ado-desktop:~$ 

```

glxgears:
Opens a box with blue, red and green gears spinning, lol.

---

### Post by philinux on 2008-06-03
> **adobrakic said:**
> glxgears:
Opens a box with blue, red and green gears spinning, lol.

What fps does it show?

The glxinfo show direct rendering as no.

---

### Post by adobrakic on 2008-06-03
1918 frames in 5.0 seconds = 383.125 FPS

---

### Post by philinux on 2008-06-03
Try

System>Prefs>appearance>Visual effects

Try ticking normal or extra.

---

### Post by adobrakic on 2008-06-03
It says "Desktop effects could not be enabled."

---

### Post by philinux on 2008-06-03
Yep you're graphics card ain't up to it I'm afraid. However there are some nice themes etc at [http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by adobrakic on 2008-06-03
Yeah, I've been there. But I only know how to use the gtk2.x themes, not really sure about anything else. thanks a lot though. :]

---

