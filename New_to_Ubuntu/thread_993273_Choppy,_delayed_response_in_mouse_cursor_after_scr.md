---
title: "Choppy, delayed response in mouse cursor after screensaver..."
date: 2008-11-25
forum: New to Ubuntu
---

### Post by RockinDolphin on 2008-11-25
Hey, All!

Okay, my next problem is this: After the computer switches to screen-saver mode, when it comes out of it the mouse cursor will be choppy, slow to react, over-shoots, and all kinds of crazy stuff. Also, the keyboard will act crazy, too, so always have to re-boot the computer after screen-saver. This isn't good...

I looked-up a thread where it seems someone else was having the same problem, but it didn't seem to go anywhere. Someone posted a link to another site for an ATI driver (And I *do* have an ATI Radeon 9200SE card with 128 Meg on-board RAM...), but the site link is no good.

Someone also asked that poster if he had Beryl, or Compiz on his system; that it may be a bug. I *do* have Compiz on my system.

I'm running Ubuntu 8.10 on an older, custom machine with an AMD Duron 1GHz processor, 2 Gig of RAM, Turtle Beach sound card, 320 Gig HD, and ATI Radeom 9200SE vid card with 128 Meg of RAM.

I might add that the graphics for the screen saver is bad. In Linspire, the Euphoria screen saver looked good, but with Ubuntu it seems nothing has changed in the 2-3 years, or whatever, since I tried Ubuntu and had the same problem; you see the wire-frames for the flames, or they're highly fragmented/fractionated/'fractilized'. Does that mean there's practically no ATI support under Ubuntu? 

Thanks in advance for any and all help.

~Kenny

I might add that I'm using a USB mouse and keyboard as my PS2 mouse input is burned-out for some reason, but haven't ever had this problem with Linspire.

---

### Post by Crafty Kisses on 2008-11-25
What are the results of this command?
```
glxinfo
```

---

### Post by RockinDolphin on 2008-11-25
[COLOR="Red"]kenny@kenny-desktop:~$ glxinfo
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.2
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
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
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
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x55 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x56  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x57  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x58  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x59  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x5a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5b  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5c  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5f  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x60  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x61  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x62  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x63  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x65  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

kenny@kenny-desktop:~$ 

[/COLOR]

---

### Post by RockinDolphin on 2008-11-25
Hhhhhhhhmmph...

'Tttttttturns out it doesn't        aaaaaaaa bbbbbbbb ftr have to be after a screen saver, after all...

Iiiiiiiif Iiiiiiii        have ttttttttm ig gon

Iiiiiiiif Iiiiiiii have too many things going on this is the result. Iiiiiiii have to type verrrry slowly in order to make coherent words and sentences, Otherwise, if I type at normal speed, it looks like this:

Tttttttthe lazy bron dog sleptt on top        of thhhhhhhhhhhhhhhukkkkkkkkred ox. 

Tttttttto        be or nottttttttbbbbbbbbthis teeeeeeeeqqqqqqqqutn.

'Oooooooobviously time to re-boot... :(

~```````Kkkkkkkkenny

---

### Post by RockinDolphin on 2008-11-26
Hey, All. 

'Still here with this problem...

I had to switch back to my Linspire drive for the moment. 'Hoping someone can help me figure this out. 'Guess I might have to buy an NVidia card, but can't afford it at the moment... :(

~Kenny

---

### Post by RockinDolphin on 2008-12-12
Is anyone else having this problem? It seems like an interrupt issue...

~Kenny

---

