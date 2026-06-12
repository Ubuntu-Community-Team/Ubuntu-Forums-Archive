---
title: "[SOLVED] video...........of course"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by metallicamike on 2008-11-12
so i upgraded to intrepid from hardy, absolutely love it no problems....except one. Streaming video SUCKS in firefox!!!! it never was like this at first, but all of the sudden streaming video is now as choppy as a pig in a butcher shop! it mostly just does this in youtube or southpark studios, not much in any other website. wats the deal? especially after it didnt do this at first, then just started out of no where!

---

### Post by patrickballeux on 2008-11-12
> **metallicamike said:**
> so i upgraded to intrepid from hardy, absolutely love it no problems....except one. Streaming video SUCKS in firefox!!!! it never was like this at first, but all of the sudden streaming video is now as choppy as a pig in a butcher shop! it mostly just does this in youtube or southpark studios, not much in any other website. wats the deal? especially after it didnt do this at first, then just started out of no where!

Ibex is using Flash 10, which should work better.

* Disable Compiz (if enabled), on ATI card, that's generally the problem
* Make sure that your sound is properly configured (Set everthing to Pulseaudio or everything to ALSA sound card).  You will see if it is working better (System - Preferences - Sound)
* Is Totem/Mplayer playing your videos nicely?

Make sure that you have updated to the latest...

Let me know!

---

### Post by metallicamike on 2008-11-12
i have everything updated....but i do hav compiz on, but that cant be wat makes the difference cuz it worked fine with it. Also it is the video not sound, although everything is set to ALSA, and idk wat my video card is sooo......but anyway, totem does play nicely, except fullscrenn messes up by the bar on the bottom and the leave fullscreen button on the top make the screen white and black in that area, and wen i pause it the only way to get it bak is to move the window around...which is a little strange lol, then it flashes bak on

---

### Post by ajmorris on 2008-11-12
hi there,
could you please post the output of the following commands from a terminal:
```
sudo lspci
```this will give us an idea of your hardware
and ```
sudo glxinfo
```this will give us an idea of the glx modules (i.e. an nvidia or ati accelerated graphics driver) - if any - that are loaded into your X session.

AJ

---

### Post by metallicamike on 2008-11-12
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

```

and the other one

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 865G 20061102 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.2
OpenGL extensions:
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_separate_stencil, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6a 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

36 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x6b  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6c  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6d  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6e  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6f  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x70  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x71  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x72  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x73  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x74  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x75  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x76  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x77  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x78  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x79  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7c  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7d  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x7e  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x7f  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x80  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x81  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x82  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x83  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x84  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x85  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x86  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x87  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x88  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x89  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8a  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8c  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8e  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```

---

### Post by patrickballeux on 2008-11-12
> **metallicamike said:**
> i have everything updated....but i do hav compiz on, but that cant be wat makes the difference cuz it worked fine with it. Also it is the video not sound, although everything is set to ALSA, and idk wat my video card is sooo......but anyway, totem does play nicely, except fullscrenn messes up by the bar on the bottom and the leave fullscreen button on the top make the screen white and black in that area, and wen i pause it the only way to get it bak is to move the window around...which is a little strange lol, then it flashes bak on

From your other post, you have an intel graphic card.  So Compiz can be an issue with the Flash player.  Simple disable it for testing purpose to see if it gets better (System - Preferences - Appearances  (Last tab...))

As for Alsa, there was a problem in Intrepid when Flash was playing sounds, it was using the Alsa Plugin thru Pulseaudio instead of using Pulseaudio Directly.  And since there was a library problem (Have to find that post) with the sound playing in Pulseaudio, video from Flash was freezing/stutering ...

Make sure also that Flash settings are to use you accelerated graphic card (right click on any flash applet, 1st tab in the settings has to be checked).

But as I said, try without Compiz, this will tell us if you graphic card is involdved or not...

---

### Post by ajmorris on 2008-11-13
you have an intel card, yet are using the mesa graphics drivers. These drivers can cause very poor performance, including what you are experiencing.
You will want to install the i810 driver, and set it to be used (whether by means of manually adding it to /etc/X11/xorg.conf or using sudo dpkg-reconfigure xserver-xorg or gksudo displayconfig-gtk)

AJ

---

### Post by metallicamike on 2008-11-13
i figured it out, my cousin set compiz to everything for window animations to be random, and thats what was causing it, so compiz can still be turned on, its just i cant have the animation bbe random. thanks for the help tho reeeeeeeaaaalllllllyyy appreciate it!

---

### Post by metallicamike on 2008-12-01
turns out that wasnt it.

---

### Post by metallicamike on 2008-12-22
bump

---

### Post by metallicamike on 2008-12-22
bump

---

### Post by nhasian on 2008-12-22
did you try disabling compiz as patrickballeux suggested?

also in firefox type in the url:

```
about:plugins
``` 

what does it say for *Shockwave Flash*?

> **metallicamike said:**
> turns out that wasnt it.

---

### Post by metallicamike on 2008-12-22
yes and that works but i cant stand to have them off.

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r15

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by metallicamike on 2008-12-22
bump

---

### Post by nhasian on 2008-12-22
thats great news.  now we know the issue is with your video adaptor.  You can replace it with an inexpensive nVidia video card and that should resolve your issue.

PS I'm assuming you've already tried the i810 driver and it did not resolve your problem?

---

### Post by metallicamike on 2009-01-04
i have intrepid so i cant use that, i have the intel driver now and a mod on it so it is good now. thanks everyone!

---

### Post by jnewm on 2009-03-02
Hi all, metallicamike, I'm having the same problem with an Intel 82865G card.  How did you switch to Intel driver, and what mods did you use?
Thanks!

---

### Post by metallicamike on 2009-03-02
this is alink to another thread that i started where my problems were solved. Hope this helps

---

### Post by metallicamike on 2009-03-03
ok, that sucks that it didn't show up:?#-o:lolflag:
here [http://ubuntuforums.org/showthread.php?t=983200](http://ubuntuforums.org/showthread.php?t=983200)

---

