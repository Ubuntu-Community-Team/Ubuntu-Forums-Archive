---
title: "Computer Games Very Slow"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by adfgvx on 2012-04-05
Hello everybody,

I am very new to Ubuntu, and Linux in general. I have been a long-time user of Windows XP, but I switched to Ubuntu 10.04 Lucid a few days ago.

I downloaded the game Nibbles from the Ubuntu Software Center, and it is very slow. One time today that game worked perfectly, but all the other times I've tried it, the frame rate was very slow, about 1 frame per second or less. I also downloaded Neverball, which has a slightly different problem: it runs smoothly for a few seconds, then everything freezes for a few seconds, then starts running smoothly again. I tried adjusting all the options in the Options menu as low as they could go; before I did this, the game would be frozen more than it would run, but with these settings, the game runs for slightly longer intervals than it is frozen. I also downloaded Blender (for 3D modeling and animating), and I cannot get past the splash screen.

I suspect that the problem is somehow related to programs that use OpenGL, because I know that Neverball and Blender use OpenGL, and I suspect that Nibbles does, too. Here is some commands I ran in the terminal to get some information, just in case it helps:

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:           432        422         10          0         11        173
-/+ buffers/cache:        237        195
Swap:         1265         22       1243

$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

$ grep processor /proc/cpuinfo
processor    : 0
model name    : Intel(R) Celeron(R) M processor         1.50GHz

$ glxgears
r300: DRM version: 2.0.0, Name: ATI RC410, ID: 0x5a62, GB: 2, Z: 1
r300: GART size: 29 MB, VRAM size: 64 MB
r300: AA compression: NO, Z compression: NO, HiZ: NO
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
602 frames in 5.0 seconds
576 frames in 5.0 seconds
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 2973 requests (2973 known processed) with 0 events remaining.

$ glxinfo
name of display: :0.0
r300: DRM version: 2.0.0, Name: ATI RC410, ID: 0x5a62, GB: 2, Z: 1
r300: GART size: 29 MB, VRAM size: 64 MB
r300: AA compression: NO, Z compression: NO, HiZ: NO
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RC410
OpenGL version string: 2.1 Mesa 7.11-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_copy_buffer, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_half_float_pixel, 
    GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query2, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture3D, GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_EXT_vertex_array, GL_OES_EGL_image, 
    GL_OES_read_format, GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

96 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xf1 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf2 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf3 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf4 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf5 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf6 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf7 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xf8 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xf9 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xfa 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xfb 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xfc 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xfd 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xfe 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xff 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x100 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x101 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x102 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x103 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x104 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x105 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x106 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x107 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x108 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x109 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x10a 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x10b 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x10c 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x10d 24 tc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x10e 24 tc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x10f 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x110 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x111 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x112 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x113 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x114 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x115 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x116 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x117 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x118 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x119 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x11a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x11b 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x11c 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x11d 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x11e 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x11f 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x120 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x121 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x122 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x123 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x124 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x125 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x126 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x127 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x128 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x129 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x12a 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x12b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x12c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x12d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x12e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x12f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x130 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x131 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x132 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x133 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x134 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x135 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x136 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x137 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x138 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x139 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x13a 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x13b 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x13c 24 dc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x13d 24 dc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x13e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x13f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x140 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x141 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x142 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x143 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x144 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x145 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x146 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x147 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x148 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x149 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x14a 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x14b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x14c 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x14d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x60 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

144 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x61  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x62  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x63  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x64  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x65  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x66  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x67  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x68  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x69  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x6a  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x6b  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x6c  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x6d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x6f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x70  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x71  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x72  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x73  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x74  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x75  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x76  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x77  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x78  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x79  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x7a  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x7b  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x7c  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x7d  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x7e  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x7f  0 tc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x80  0 tc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x81  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x82  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x83  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x84  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x85  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x86  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x87  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x88  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x89  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x8a  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x8b  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x8c  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x8d  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x8e  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x8f  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x90  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x91  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x92  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x93  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x94  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x95  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x96  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x97  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x98  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x99  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x9a  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x9b  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x9c  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x9d  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0x9e  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0x9f  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0xa0  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0xa1  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0xa2  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0xa3  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0xa4  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0xa5  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0xa6  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0xa7  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0xa8  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0xa9  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xaa  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xab  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xac  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xad  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xae  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xaf  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xb0  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xb1  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xb2  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xb3  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xb4  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xb5  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xb6  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xb7  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xb8  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xb9  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xba  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xbb  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xbc  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xbd  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xbe  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xbf  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc0  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xc1  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc2  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc3  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc4  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc5  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc6  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc7  0 dc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xc8  0 dc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xc9  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xca  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xcb  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xcc  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xcd  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xce  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xcf  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xd0  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xd1  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xd2  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xd3  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd4  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd5  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd6  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd7  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd8  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd9  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0xda  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0xdb  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0xdc  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0xdd  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0xde  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0xdf  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0xe0  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xe1  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0xe2  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xe3  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0xe4  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xe5  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0xe6  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0xe7  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0xe8  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0xe9  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0xea  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0xeb  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0xec  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0xed  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0xee  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0xef  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0xf0  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
```

---

### Post by gandalf3 on 2012-04-05
well, if it is a OpenGl problem, i don't know what to do. but it looks to me that you have a memory problem.. (i believe this works in 10.04..) 
see if you can open the System Monitor, go under "resources" watch memory usage while opening never ball, etc.
hope this helps!

---

### Post by terrykiwi83 on 2012-04-05
> **gandalf3 said:**
> well, if it is a OpenGl problem, i don't know what to do. but it looks to me that you have a memory problem.. (i believe this works in 10.04..) 
see if you can open the System Monitor, go under "resources" watch memory usage while opening never ball, etc.
hope this helps!
Agreeing with gandalf3 here.

I to would be inclined to say its down to your physical memory:

```

 total       used       free     shared    buffers     cached Mem:         
 432        422         10          0         11        173

```

If the above is a representation of your memory at IDLE then I dread to think what it would be at full load.

My suggestion, upgrade the RAM

---

### Post by mastablasta on 2012-04-06
also your GPU chip does nto have good linux support.:
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

 
you could try to upgrade the drivers usign Edgers PPA and see if that helps.
 
Upgrading RAM or using a lighter DE version (Xubuntu= XFCE, Lubuntu=LXDE)is also an option.

---

### Post by adfgvx on 2012-04-07
I tried installing Xubuntu, but that didn't help.

I forgot to say earlier that when I had Windows, I had no problem playing games. Both FlightGear and Blender worked fine.

---

### Post by d4m1r on 2012-04-07
Wow, 1.5Ghz Celeron, 400MB RAM, and 64MB Video card? No wonder games are not running very slow on that machine ](*,)

You need to either upgrade your PC or stay away from games. No offence, but with that hardware, you should stick to browser based games ONLY.

---

### Post by terrykiwi83 on 2012-04-07
> **d4m1r said:**
> Wow, 1.5Ghz Celeron, 400MB RAM, and 64MB Video card? No wonder games are not running very slow on that machine ](*,)

You need to either upgrade your PC or stay away from games. No offence, but with that hardware, you should stick to browser based games ONLY.
  
+1, fully agree

---

### Post by gandalf3 on 2012-04-08
> I tried installing Xubuntu, but that didn't help.

I forgot to say earlier that when I had Windows, I had no problem playing games. Both FlightGear and Blender worked fine.
hmm..
i used to have about 1GB of ram and playing flight gear on windows 7 i only got about 5-10 fps.. (in Ubuntu, i could get 20 fps if i started it before opening any other programs)
i got two more GB of ram and now it's much better, glued to frame rate limiter, usually on 30. (in both windows and Ubuntu)
no idea why it worked on that low memory in XP.. 
FYI, this is on an old Pentium 4 3.2GHZ

---

### Post by quicklearner on 2012-08-16
My system is quite  fast for such games. But its awfully slow. I takes about 30 seconds after I press Ctrl+N to start a game. When I make it fullscreen, the game freezes for about 1 minutes!

My machine
Intel core 2 duo 2.8GHz. 
8GB DDR2 RAM
Nvidia GTS 250 GPU (With nouveau driver)

Could you tell me what is the reason?

I'll do some farther research though. But is there any known problem?

---

### Post by anewguy on 2012-08-16
> **quicklearner said:**
> My system is quite  fast for such games. But its awfully slow. I takes about 30 seconds after I press Ctrl+N to start a game. When I make it fullscreen, the game freezes for about 1 minutes!

My machine
Intel core 2 duo 2.8GHz. 
8GB DDR2 RAM
Nvidia GTS 250 GPU (With nouveau driver)

Could you tell me what is the reason?

I'll do some farther research though. But is there any known problem?

Start your own thread for your question.  It's rude jumping into a thread with another question.

---

### Post by quicklearner on 2012-08-16
> **anewguy said:**
> Start your own thread for your question.  It's rude jumping into a thread with another question.

I dont know how its rude. But I think this thread is completely relevant. I have the same game and same issue. More over I have more information. 

Beside if I create a new thread, dont you think someone will tell me to read this thread?

---

### Post by anewguy on 2012-08-16
> **quicklearner said:**
> I dont know how its rude. But I think this thread is completely relevant. I have the same game and same issue. More over I have more information. 

Beside if I create a new thread, dont you think someone will tell me to read this thread?

You asked a NEW question about gameS - plural. You provided no help to the poster.  The idea is to post HELP or post your own thread.  That's why it's rude - it's called hijacking a thread.  Either post help or open a new thread - simple as that.

Oh, and you can report me if you want.

---

