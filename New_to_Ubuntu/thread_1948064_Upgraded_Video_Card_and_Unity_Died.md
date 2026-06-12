---
title: "Upgraded Video Card and Unity Died"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by Digitalxero on 2012-03-27
So I upgraded to an ATI card with 6 DisplayPorts (Old one only had 4 and a DVI so I could only get 5 of my 6 monitors working). Now after jumping though a few hoops of uninstalling the proprietary drivers I was using and installing the open source ones I finally got a desktop back up and running but unity thinks it is using software rendering. Any help getting this working would be great

Bellow is all of the debug output that I think might be needed

```
dgilcrease@ksp-djlinux:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Barts XT [ATI Radeon HD 6800 Series] [1002:6738]

```

```
dgilcrease@ksp-djlinux:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string:  2.1 Mesa 7.11

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

```
dgilcrease@ksp-djlinux:~$ glxinfo
name of display: :5
display: :5  screen: 0
direct rendering: Yes
server glx vendor string: Brian Paul
server glx version string: 1.4 Mesa 7.11
server glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
client glx vendor string: Brian Paul
client glx version string: 1.4 Mesa 7.11
client glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
GLX version: 1.4
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_copy_texture, GL_EXT_paletted_texture, GL_EXT_polygon_offset, 
    GL_EXT_subtexture, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_EXT_compiled_vertex_array, GL_EXT_texture, GL_EXT_texture3D, 
    GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_MESA_resize_buffers, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_SUN_multi_draw_arrays, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_EXT_framebuffer_object, GL_EXT_shared_texture_palette, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_ARB_depth_texture, 
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_depth_clamp, 
    GL_NV_fragment_program, GL_NV_point_sprite, GL_NV_vertex_program1_1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_depth_bounds_test, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_MESA_pack_invert, 
    GL_MESA_ycbcr_texture, GL_ARB_depth_clamp, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_occlusion_query2, GL_ARB_point_sprite, 
    GL_ARB_shading_language_100, GL_ARB_sync, GL_ARB_texture_non_power_of_two, 
    GL_ARB_vertex_buffer_object, GL_ATI_blend_equation_separate, 
    GL_EXT_blend_equation_separate, GL_OES_read_format, 
    GL_ARB_pixel_buffer_object, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_rectangle, GL_ATI_texture_compression_3dc, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_NV_fragment_program_option, GL_APPLE_object_purgeable, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, 
    GL_ATI_texture_mirror_once, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_array, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_env_combine, 
    GL_EXT_texture_sRGB_decode, GL_EXT_timer_query, GL_MESA_texture_array, 
    GL_ARB_copy_buffer, GL_ARB_draw_instanced, GL_ARB_half_float_vertex, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_provoking_vertex, GL_EXT_provoking_vertex, GL_ARB_robustness

96 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x022 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x100 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x101 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x102 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x103 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x104 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x105 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x106 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x107 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x108 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x109 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x110 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x111 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x112 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x113 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x114 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x115 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x116 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x117 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x118 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x119 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x120 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x121 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x122 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x123 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x124 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x125 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x126 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x127 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x128 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x129 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x130 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x131 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x132 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x133 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x134 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x135 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x136 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x137 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x138 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x139 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x140 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x141 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x142 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x143 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x144 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x145 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x146 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x147 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x148 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x149 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x150 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x151 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x152 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x153 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x154 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x155 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x156 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x157 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x158 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x159 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x15a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x15b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x15c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x06f 32 tc  0  32  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16  0  0 0 None

96 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x022 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x100 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x101 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x102 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x103 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x104 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x105 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x106 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x107 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x108 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x109 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x10f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x110 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x111 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x112 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x113 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x114 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x115 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x116 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x117 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x118 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x119 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x11f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x120 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x121 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x122 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x123 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x124 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x125 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x126 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x127 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x128 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x129 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x12f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x130 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x131 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x132 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x133 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x134 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x135 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x136 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x137 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x138 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x139 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x13f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x140 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x141 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x142 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x143 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x144 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x145 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x146 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x147 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x148 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x149 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x14f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x150 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x151 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x152 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x153 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x154 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x155 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x156 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x157 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x158 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x159 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x15a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x15b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x15c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x06f 32 tc  0  32  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None

```

```
dgilcrease@ksp-djlinux:~$ dmesg | grep drm
[    2.412552] [drm] Initialized drm 1.1.0 20060810
[    2.419291] [drm] radeon defaulting to kernel modesetting.
[    2.419293] [drm] radeon kernel modesetting enabled.
[    2.420791] [drm] initializing kernel modesetting (BARTS 0x1002:0x6738 0x1545:0x6870).
[    2.420819] [drm] register mmio base: 0xFEA20000
[    2.420820] [drm] register mmio size: 131072
[    2.424284] [drm] Detected VRAM RAM=2048M, BAR=256M
[    2.424288] [drm] RAM width 256bits DDR
[    2.424920] [drm] radeon: 2048M of VRAM memory ready
[    2.424922] [drm] radeon: 512M of GTT memory ready.
[    2.424952] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.424954] [drm] Driver supports precise vblank timestamp query.
[    2.425032] [drm] radeon: irq initialized.
[    2.425036] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.425642] [drm] Loading BARTS Microcode
[    2.456417] [drm] ring test succeeded in 2 usecs
[    2.456486] [drm] radeon: ib pool ready.
[    2.456589] [drm] ib test succeeded in 0 usecs
[    2.458902] [drm] Radeon Display Connectors
[    2.458903] [drm] Connector 0:
[    2.458904] [drm]   DisplayPort
[    2.458905] [drm]   HPD4
[    2.458907] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    2.458908] [drm]   Encoders:
[    2.458909] [drm]     DFP1: INTERNAL_UNIPHY2
[    2.458910] [drm] Connector 1:
[    2.458910] [drm]   DisplayPort
[    2.458911] [drm]   HPD5
[    2.458912] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    2.458913] [drm]   Encoders:
[    2.458914] [drm]     DFP2: INTERNAL_UNIPHY2
[    2.458915] [drm] Connector 2:
[    2.458916] [drm]   DisplayPort
[    2.458916] [drm]   HPD3
[    2.458917] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[    2.458918] [drm]   Encoders:
[    2.458919] [drm]     DFP3: INTERNAL_UNIPHY1
[    2.458920] [drm] Connector 3:
[    2.458921] [drm]   DisplayPort
[    2.458922] [drm]   HPD1
[    2.458923] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    2.458924] [drm]   Encoders:
[    2.458924] [drm]     DFP4: INTERNAL_UNIPHY1
[    2.458925] [drm] Connector 4:
[    2.458926] [drm]   DisplayPort
[    2.458927] [drm]   HPD2
[    2.458928] [drm]   DDC: 0x6470 0x6470 0x6474 0x6474 0x6478 0x6478 0x647c 0x647c
[    2.458929] [drm]   Encoders:
[    2.458930] [drm]     DFP5: INTERNAL_UNIPHY
[    2.458930] [drm] Connector 5:
[    2.458931] [drm]   DisplayPort
[    2.458932] [drm]   HPD6
[    2.458933] [drm]   DDC: 0x6480 0x6480 0x6484 0x6484 0x6488 0x6488 0x648c 0x648c
[    2.458934] [drm]   Encoders:
[    2.458935] [drm]     DFP6: INTERNAL_UNIPHY
[    2.936057] [drm] Radeon display connector DP-1: No monitor connected or invalid EDID
[    3.416050] [drm] Radeon display connector DP-2: No monitor connected or invalid EDID
[    3.896038] [drm] Radeon display connector DP-3: No monitor connected or invalid EDID
[    4.376037] [drm] Radeon display connector DP-4: No monitor connected or invalid EDID
[    4.490724] [drm] Radeon display connector DP-5: Found valid EDID
[    4.968037] [drm] Radeon display connector DP-6: No monitor connected or invalid EDID
[    4.968120] [drm] Internal thermal controller with fan control
[    4.969261] [drm] radeon: power management initialized
[    5.386462] [drm] fb mappable at 0xC0141000
[    5.386464] [drm] vram apper at 0xC0000000
[    5.386465] [drm] size 8294400
[    5.386466] [drm] fb depth is 24
[    5.386466] [drm]    pitch is 7680
[    5.386515] fbcon: radeondrmfb (fb0) is primary device
[    5.386585] fb0: radeondrmfb frame buffer device
[    5.386586] drm: registered panic notifier
[    5.386598] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:00.0 on minor 0
[    6.253141] [drm] force priority to high
...
[   46.504263] [drm] force priority to high
[   62.579932] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[   62.582918] [drm] force priority to high
...

```

```
dgilcrease@ksp-djlinux:~$ xrandr
Screen 0: minimum 320 x 200, current 5760 x 2160, maximum 16384 x 16384
DisplayPort-0 connected 1920x1080+0+1080 (normal left inverted right x axis y axis) 510mm x 278mm
   1920x1080      60.0*+
   1920x1080i     25.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  
DisplayPort-1 connected 1920x1080+1920+1080 (normal left inverted right x axis y axis) 510mm x 278mm
   1920x1080      60.0*+
   1920x1080i     25.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  
DisplayPort-2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 278mm
   1920x1080      60.0*+
   1920x1080i     25.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  
DisplayPort-3 connected 1920x1080+3840+0 (normal left inverted right x axis y axis) 510mm x 278mm
   1920x1080      60.0*+
   1920x1080i     25.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  
DisplayPort-4 connected 1920x1080+3840+1080 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080      60.0 +   50.0* 
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       50.0     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        60.0  
DisplayPort-5 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 510mm x 278mm
   1920x1080      60.0*+
   1920x1080i     25.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  

```

---

### Post by papibe on 2012-03-30
Hi Digitalxero.

Could you post the content of this file?
```
/etc/X11/xorg.conf
```
Regards.

---

### Post by Digitalxero on 2012-04-02
it is empty

---

### Post by Mark Phelps on 2012-04-02
> **Digitalxero said:**
> it is empty

Not surprising ... since that's not created or used by default anymore.

You should be able to install AMD restricted drivers. Is nothing being offered in Additional Drivers?

---

### Post by Digitalxero on 2012-04-02
They are, but I would prefer to use the OSS versions if possible. If not I'll install the proprietary drivers.

---

### Post by mastablasta on 2012-04-02
> **Digitalxero said:**
> They are, but I would prefer to use the OSS versions if possible. If not I'll install the proprietary drivers.


OSS drivers do not support all features from AMD cards. use proprietary ones from the additional drivers or f they do not perfom adequatly install their latest version manually by downloading them from AMD website.

---

### Post by Digitalxero on 2012-04-02
I know the OSS drivers don't support everything, but they do support hardware rendering for Unity. I don't need all the advanced features for 3d games and such as this is just my work computer.

The main issue is that Unity thinks it is in Software rendering even though the OpenGL renderer string is set to Mesa X11 and all logs I can find say Hardware accelerations is on and active

```
[    17.621] (II) RADEON(0): [DRI2] Setup complete
[    17.621] (II) RADEON(0): [DRI2]   DRI driver: r600
[    17.621] (II) RADEON(0): Front buffer size: 8100K
[    17.621] (II) RADEON(0): VRAM usage limit set to 221119K
[    17.682] (==) RADEON(0): Backing store disabled
[    17.682] (II) RADEON(0): Direct rendering enabled
[    17.690] (II) RADEON(0): Setting EXA maxPitchBytes
[    17.690] (II) EXA(0): Driver allocated offscreen pixmaps
[    17.690] (II) EXA(0): Driver registered support for the following operations:
[    17.690] (II)         Solid
[    17.690] (II)         Copy
[    17.690] (II)         Composite (RENDER acceleration)
[    17.690] (II)         UploadToScreen
[    17.690] (II)         DownloadFromScreen
[    17.690] (II) RADEON(0): Acceleration enabled
[    17.690] (==) RADEON(0): DPMS enabled
[    17.690] (==) RADEON(0): Silken mouse enabled
[    17.705] (II) RADEON(0): Set up textured video
[    17.705] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    17.705] (II) RADEON(0): [XvMC] Extension initialized.

```

and glxgears averages 1000 FPS
```
dgilcrease@ksp-djlinux:~$ glxgears
5087 frames in 5.0 seconds = 1017.320 FPS
5168 frames in 5.0 seconds = 1033.462 FPS
5194 frames in 5.0 seconds = 1038.715 FPS

```

---

### Post by gordintoronto on 2012-04-02
I'm surprised you have not identified the brand and model of your video card -- and by your reluctance to use Additional Drivers.

---

### Post by Digitalxero on 2012-04-03
First post, first bit of debug data identifies the card

ATI Radeon HD 6800 Series

---

### Post by gordintoronto on 2012-04-03
> **Digitalxero said:**
> First post, first bit of debug data identifies the card

ATI Radeon HD 6800 Series

Sorry, that is not a brand and model. It's a chipset, which is shared by dozens of different video cards.

---

