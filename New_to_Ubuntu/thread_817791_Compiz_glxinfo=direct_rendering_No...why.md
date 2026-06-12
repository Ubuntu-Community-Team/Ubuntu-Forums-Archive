---
title: "Compiz: glxinfo=direct rendering: No...why?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by pryan75 on 2008-06-03
Hello,

I am trying to get direct rendering working on my machine all in an effort to run Compiz. glxinfo yields a segmentation fault and glxgears yields a 2077fps. I have a Dell Dimension 3000 with onboard Intel video....but I installed a ATI Radeon 9250 (PCI). I tried ENVY and it didn't work. I tried to install ATI proprietary drivers...and I can't get the driver to appear in the Hardware Drivers section. I'm not sure what else I can do?

```
patrick@pryan75:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

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
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
Segmentation fault

```

And glxgears...if it's any help:
```

patrick@pryan75:~$ glx gears
bash: glx: command not found
patrick@pryan75:~$ glxgears
2898 frames in 5.0 seconds = 578.892 FPS
3140 frames in 5.0 seconds = 625.195 FPS
3060 frames in 5.0 seconds = 611.033 FPS
2660 frames in 5.0 seconds = 529.074 FPS
1900 frames in 5.1 seconds = 370.722 FPS
1780 frames in 5.0 seconds = 355.587 FPS
4820 frames in 5.0 seconds = 962.680 FPS
4840 frames in 5.0 seconds = 961.605 FPS
4820 frames in 5.0 seconds = 962.927 FPS
7980 frames in 5.0 seconds = 1595.246 FPS
10398 frames in 5.0 seconds = 2077.899 FPS
9320 frames in 5.0 seconds = 1861.680 FPS
6520 frames in 5.0 seconds = 1296.318 FPS
6020 frames in 5.0 seconds = 1202.514 FPS
12146 frames in 5.0 seconds = 2427.482 FPS
9040 frames in 5.0 seconds = 1799.141 FPS
4160 frames in 5.0 seconds = 831.781 FPS
1960 frames in 5.0 seconds = 390.947 FPS
980 frames in 5.1 seconds = 193.426 FPS
980 frames in 5.0 seconds = 194.691 FPS
2400 frames in 5.0 seconds = 478.443 FPS
2040 frames in 5.1 seconds = 400.455 FPS
1800 frames in 5.0 seconds = 358.484 FPS
1560 frames in 5.1 seconds = 307.450 FPS
1740 frames in 5.0 seconds = 346.258 FPS
1680 frames in 5.0 seconds = 335.660 FPS
1260 frames in 5.0 seconds = 250.532 FPS
2940 frames in 5.0 seconds = 586.456 FPS
2960 frames in 5.0 seconds = 589.490 FPS
2920 frames in 5.0 seconds = 580.890 FPS
5860 frames in 5.0 seconds = 1170.558 FPS
10500 frames in 5.0 seconds = 2098.329 FPS
11600 frames in 5.0 seconds = 2311.597 FPS
9423 frames in 5.0 seconds = 1884.400 FPS
12120 frames in 5.0 seconds = 2421.436 FPS
8740 frames in 5.0 seconds = 1745.426 FPS

```

Any help would be appreciated.

Patrick

---

### Post by bryncoles on 2008-06-05
i have this issue too. i get this:

```
$ glxinfo | grep direct 
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```

and have no proprietary drivers in system->admin->hardware drivers. i have a packardbell r4360, with a 1.30GHz Intel(R) Celeron(R) M processor. i just wanna know if ill get any benefit from enabling direct rendering / if i even can do direct rendering!

---

### Post by starcannon on 2008-06-05
With Direct Rendering you get smoother page scrolling and video playback, and also then will likely have the option to turn on desktop effects if you wish.

@Pryan you have an ATi R200 , I'm no ATi expert, but I'm pretty sure I've seen this card solved, you'll have to hunt the boards a bit.

Heres a link I found that may be of use Pryan:

[http://ubuntuforums.org/showthread.php?t=515573&highlight=ati+r200](http://ubuntuforums.org/showthread.php?t=515573&highlight=ati+r200)

@bryncoles what video card do you have?

---

### Post by bryncoles on 2008-06-05
hi starcannon... erm... not sure what graphics card it is...! how would i check?

*edit*

sysinfo tells me its 

'intel corporation 82852/855GM integrated graphics device (rev 02) (prog-if 00 [VGA controller]). 

which means nothing to me!

---

### Post by starcannon on 2008-06-05
Still reading around in the forums that 855GM has been made to work and have direct rendering, I've read that much; however I still haven't found the magic "how to guide" that says how they got it working. I would likely try going into synaptic package manager, and reinstalling xserver-xorg-video-intel.

I'll keep hunting around google and these forums, if I find something I'll post it here by editing this message.

---

### Post by bryncoles on 2008-06-05
cool, i appreciate your efforts! and sorry to pryan75 for hijacking your thread!

---

### Post by prshah on 2008-06-05
> **pryan75 said:**
> 
```
patrick@pryan75:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
Segmentation fault

```

Patrick

> **bryncoles said:**
> i have this issue too. i get this:

```
$ glxinfo | grep direct 
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```


Oohh patrik: segfault; not nice.

Anyway, request you both to post outputs for ```

LIBGL_DEBUG=verbose glxinfo
cat /var/log/Xorg.0.log | grep -i -A 3 -B 3 "(ee)"
cat /var/log/Xorg.0.log | grep -i "(==)"
export | grep -i libgl

```

---

### Post by bryncoles on 2008-06-05
hi prshah, thanks for joining us! 

heres the info you requested:

```
$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_packed_pixels, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x66 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

and

```
cat /var/log/Xorg.0.log | grep -i -A 3 -B 3 "(ee)"
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  5 20:27:03 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
```

and

```
cat /var/log/Xorg.0.log | grep -i "(==)"
Markers: (--) probed, (**) from config file, (==) default setting,
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  5 20:27:03 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) FontPath set to:
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) AIGLX enabled
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(==) intel(0): Using EXA for acceleration
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(==) Depth 24 pixmap format is 32 bpp
(==) intel(0): VideoRam: 131072 KB
(==) intel(0): Write-combining range (0xb0000000,0x8000000)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
```

and finally, 

```
export | grep -i libgl
declare -x LIBGL_ALWAYS_INDIRECT="1"
```

if its possible, would you be able to tell me what each of those commands just did? or point me to a reference manual / web page which will explain? im trying to learn whats happening as i go along, then i can give back as much as i get. 

thanks again!

---

### Post by st33med on 2008-06-05
Intel video cards do not do direct rendering. That is to say, they are just there for video output and a few other things. In other words...

[SIZE="4"]They
Suck[/SIZE]

Of course, compiz SHOULD launch without any additions anymore, but in case it still does not:
```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace
```

---

### Post by st33med on 2008-06-05
> **pryan75 said:**
> Hello,
 I have a Dell Dimension 3000 with onboard Intel video....but I installed a ATI Radeon 9250 (PCI). I tried ENVY and it didn't work. I tried to install ATI proprietary drivers...and I can't get the driver to appear in the Hardware Drivers section.

Wait, what? What did you do, install a new motherboard?

In any case, ATI drivers are not very good with compiz as well. Driver support from ATI sucks.

---

### Post by prshah on 2008-06-05
> **st33med said:**
> Intel video cards do not do direct rendering. 

Of course, compiz SHOULD launch without any additions anymore, but in case it still does not:
```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace
```

Intel cards _do_ direct rendering, and do it well; but they still _suck_ performance wise when compared to nVidia cards. ATI are plagued with driver problems, from what I understand, but are otherwise good.

In any case, with direct rendering, you _will_ get a substantial performance boost.

My understanding is that LIBGL_ALWAYS_INDIRECT is useful for ATI cards only; I may be wrong. I'm using intel, and have no call for LIBGL_ALWAYS_INDIRECT. My compiz runs perfectly and smoothly.

Is there any particular reason you've put LIBGL_ALWAYS_INDIRECT in? Or has it been in always?

---

### Post by bryncoles on 2008-06-06
its just always been like that! i didnt even realise until i saw the 'export | grep -i libgl' command in another post (ist the 10000th time doom post). then i started to wonder if it should be indirect, or could be some other way. ha ha, six months ive been using my system this way!

thing is, i have no idea how to toggle it to use direct rendering. should i run 

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace
```? i am not sure because i do get the desktop effects as things are. 

thanks to one and all for the suggestions and input!

---

### Post by oedha on 2008-06-06
> **st33med said:**
> Intel video cards do not do direct rendering. That is to say, they are just there for video output and a few other things. In other words...

[SIZE=4]They
Suck[/SIZE]

Of course, compiz SHOULD launch without any additions anymore, but in case it still does not:
```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace
```

Intel is not that sucks anyway.....compiz works well on my 915M and 8258 too.....which intel is suck anyway

---

### Post by oedha on 2008-06-06
> **st33med said:**
> Wait, what? What did you do, install a new motherboard?

In any case, ATI drivers are not very good with compiz as well. Driver support from ATI sucks.

This one too, compiz works well on RV505 and radeon xpress 1250
i just have to install xorg-driver-fglrx
no need to go to ATi site.......

---

### Post by prshah on 2008-06-06
> **bryncoles said:**
> 
thing is, i have no idea how to toggle it to use direct rendering. should i run 

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace
```? 



Try:
```
LIBGL_ALWAYS_INDIRECT=0 compiz --replace
```

or
```

export LIBGL_ALWAYS_INDIRECT=0
compiz --replace
```

The first is temporary, the second will persist across reboots.

---

### Post by bryncoles on 2008-06-06
oooh, that was exciting! i got the following output:

```
$ LIBGL_ALWAYS_INDIRECT=0 compiz --replace

Checking for Xgl: not present. 
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

what next? shall i go and have a look at  /apps/compiz/plugins/scale/allscreens/options/initiate_edge?

---

### Post by prshah on 2008-06-06
> **bryncoles said:**
> 

what next? shall i go and have a look at  /apps/compiz/plugins/scale/allscreens/options/initiate_edge?

Yes, but look at it through gconf-editor.

You know,I really shouldn't be messing around here without knowing more about your setup. Can you press Alt+F2 and run ```
gksudo displayconfig-gtk
``` then click on the "Graphics Card" tab and report which driver is in use?

Can you also show me what the terminal says when you give these commands in the terminal```

unset LIBGL_ALWAYS_INDIRECT
glxinfo | grep direct
LIBGL_DEBUG=verbose glxinfo
```

---

### Post by bryncoles on 2008-06-06
gksudo displayconfig-gtk tells me 

intel -experimental modesetting driver for linux

and when i look at /apps/compiz/plugins/scale/allscreens/options/initiate_edge, its just has '[]' after it. 

interseting! also- since trying LIBGL_ALWAYS_INDIRECT=0 compiz --replace, my windows all have an 'aura' around them!

anyway - heres what you asked for

```
unset LIBGL_ALWAYS_INDIRECT
``` (thats right, that one does nothing in the terminal.)

```
$ glxinfo | grep direct
direct rendering: Yes
```

thats new - im now direct rendering! hurrah!

```
$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 1.9.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
libGL error: 
Can't open configuration file /etc/drirc: No such file or directory.
libGL error: 
Can't open configuration file /home/bryn/.drirc: No such file or directory.
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
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x66 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

thats interesting that its now direct rendering though. we must be getting somewhere! i just wonder what my error messages, and the extra boarders around my menus are all about...

---

### Post by prshah on 2008-06-06
> **bryncoles said:**
> 
intel -experimental modesetting driver for linux

```
unset LIBGL_ALWAYS_INDIRECT
``` (thats right, that one does nothing in the terminal.)
```
$ glxinfo | grep direct
direct rendering: Yes
```
we must be getting somewhere! i just wonder what my error messages, and the extra boarders around my menus are all about...

OK I was wrong about the LIBGL_ALWAYS_INDIRECET=0 thingy; you have to _unset_ LIBGL_ALWAYS_INDIRECT for it to work in direct mode.

Here's a nice stunt; (To be done in terminal)```

export LIBGL_ALWAYS_INDIRECT=0
glxgears
unset LIBGL_ALWAYS_INDIRECT
glxgears
INTEL_BATCH=1 glxgears

```

Let each glxgears run for about 30~45 secs; Any improvements with direct rendering?

You can ignore the error messages in the verbose output. The dark blue aura around menus is normal; I get it too.

---

### Post by bryncoles on 2008-06-06
hmmm, thats all very interesting! heres the output i just got:

```
bryn@bryn-laptop:~$ export LIBGL_ALWAYS_INDIRECT=0
bryn@bryn-laptop:~$ glxgears
2576 frames in 5.0 seconds = 512.804 FPS
2540 frames in 5.0 seconds = 504.161 FPS
2540 frames in 5.0 seconds = 504.589 FPS
2540 frames in 5.0 seconds = 505.213 FPS
2540 frames in 5.0 seconds = 505.296 FPS
2540 frames in 5.0 seconds = 505.173 FPS
2540 frames in 5.0 seconds = 505.002 FPS
2540 frames in 5.0 seconds = 504.601 FPS
2540 frames in 5.0 seconds = 505.266 FPS
2540 frames in 5.0 seconds = 504.609 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 53108 requests (35 known processed) with 0 events remaining.
bryn@bryn-laptop:~$ unset LIBGL_ALWAYS_INDIRECT
bryn@bryn-laptop:~$ glxgears
2503 frames in 5.0 seconds = 500.439 FPS
2544 frames in 5.0 seconds = 508.747 FPS
2542 frames in 5.0 seconds = 508.227 FPS
2542 frames in 5.0 seconds = 508.395 FPS
2543 frames in 5.0 seconds = 508.578 FPS
2542 frames in 5.0 seconds = 508.220 FPS
2502 frames in 5.0 seconds = 500.372 FPS
2493 frames in 5.0 seconds = 498.582 FPS
2526 frames in 5.0 seconds = 505.041 FPS
2524 frames in 5.0 seconds = 504.742 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 80521 requests (80520 known processed) with 2 events remaining.
bryn@bryn-laptop:~$ INTEL_BATCH=1 glxgears
2679 frames in 5.0 seconds = 535.768 FPS
2661 frames in 5.0 seconds = 532.145 FPS
2658 frames in 5.0 seconds = 531.580 FPS
2236 frames in 5.0 seconds = 447.103 FPS
2240 frames in 5.0 seconds = 447.926 FPS
2008 frames in 5.0 seconds = 401.496 FPS
2264 frames in 5.0 seconds = 452.769 FPS
1980 frames in 5.0 seconds = 395.990 FPS
2142 frames in 5.0 seconds = 428.377 FPS
2027 frames in 5.0 seconds = 405.046 FPS
2111 frames in 5.0 seconds = 421.833 FPS
1785 frames in 5.0 seconds = 356.968 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 80543 requests (80050 known processed) with 0 events remaining.
bryn@bryn-laptop:~$ 
```

i was quite surprised at that last one - it started strong and then went all... well... naff!

i dont really mind the aura around the menus, but its around the gnome-panels (top  and bottom) too... looks a little glitchy!

oh yeah, and i let the computer just sit and do its glxgears thing for each of the commands - didnt use it for anything else, so ive no idea why theres that performance tail off at the end of the last command!

---

### Post by prshah on 2008-06-06
> **bryncoles said:**
> hmmm, thats all very interesting! heres the output i just got:
i dont really mind the aura around the menus, but its around the gnome-panels (top  and bottom) too... looks a little mglitchy!

Err I have no auras around the gnome panels. Maybe you should do the unset thing, then restart, give the export | grep... command, ensure that always_indirect is still unset, and then compiz --replace; as well as glxgears. Hope you get a nice performance boost.

---

### Post by bryncoles on 2008-06-06
sorry, just to be a little dumb for a moment... i should do 

```
unset LIBGL_ALWAYS_INDIRECT
```

then restart, followed by 

```
export | grep -i libgl
```

and 

```
LIBGL_ALWAYS_INDIRECT=0 compiz --replace
```

and finish it off with glxgears?

im already experiencing better frame rates, so something's working well for me at least! if the restart resets the gnome panels then we'll have a winner!

---

### Post by bryncoles on 2008-06-06
well, there are two outcomes i have now! one is increased performance (hurrah!) the other is i have effed up my screen resolution! oops! its now 'zoomed in', so everything is too big, and i cant make it smaller!

system-> preferences-> screen resolution only gives me two choices - 1012x768, or 1400x1050! neither of these is right (im on a laptop with a wide screen monitor). 

the resolution should be 1280x800, and i need to affect the change to the boot screen too. 

if anyone can help me sort out the screen resolution, then ill be a happy camper!

and config editor/desktop/gnome/screen/default/o says that the screen resolution is 1280x800... so i think i just need to add that option somewhere else...

looking at this thread

```
http://ubuntuforums.org/showthread.php?t=631526
``` specifically spacepilots post at the bottom, it seems i have three xorg files now - one called xorg.conf, and xorg.conf1 and xorg.conf20080109141902. whats up with that?

following that has given me partial success anyway... i added my screen resolution to the xorg.conf file, and now i have the correct aspect ration (1280x800), but im still zoomed in!

any idea whats wrong / how to fix it?

*edit*

its alright... i managed to fix the screen! i booted from the live cd and just copied the xorg.conf file from there onto my file system. now... to see if im still direct rendering heh heh heh...

---

