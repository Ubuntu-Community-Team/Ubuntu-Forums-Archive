---
title: "problems with graphics"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Philip Hammer on 2008-11-05
I have just recently installed ubuntu 8.10. the 3d graphics are not working at all. The screen just shows lines across the bottom of the screen instead of the graphics. I have i810 integrated graphics. any help would be appreciated.

---

### Post by phidia on 2008-11-06
I don't know if it will work for you but you can try booting in recovery mode and entering > xfix there.

You can also try opening a commandline (Alt+Ctrl+F1) and entering > sudo dpkg-reconfigure -phigh xserver-xorg

Let us know how those work.

---

### Post by Philip Hammer on 2008-11-06
I am new to ubuntu. I am not sure how to boot in recovery mode. I tried the second solution, but it didn't improve the graphics.

---

### Post by Crafty Kisses on 2008-11-06
What are the results of this command?
```
glxinfo
```

---

### Post by Philip Hammer on 2008-11-06
Here is the output to glxinfo:

philip@philip-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Keith Whitwell
OpenGL renderer string: Mesa DRI i810E 20050821 x86/MMX/SSE
OpenGL version string: 1.2 Mesa 7.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_compression, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x22 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x3c 32 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None

16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x3d  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x3e  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x3f  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x40  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x41  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x42  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x43  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x44  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x45  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x46  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x47  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x48  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x49  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x4a  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x4b  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x4c  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow

philip@philip-desktop:~$

---

### Post by mapes12 on 2008-11-06
A last resort may be to follow this HowTo:

[http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

Best wishes.

---

