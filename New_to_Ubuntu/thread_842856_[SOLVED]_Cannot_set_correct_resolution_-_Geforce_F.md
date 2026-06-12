---
title: "[SOLVED] Cannot set correct resolution - Geforce FX 5500 &amp;lt;-[DVI]-&amp;gt; 20.1&amp;quot; LCD"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by suprfish on 2008-06-27
The D-Sub input to my LCD screen (20.1", 1680 x 1050 normal res) broke recently, fortunately I found that both my video card (Geforce FX 5500) and my screen both have DVI-I inputs, so I went and got a DVI-DVI cable and it works, except that now I cannot set it to the proper resolution (1680 x 1050), it is stuck at 1280 x 1024. Even though there is a mode for 1680 x 1050 in my xorg.conf, it does not appear in System > Preferences > Screen Resolution.

Thanks for any help!

Various outputs:

```

~$ lsmod | grep nvidia

nvidia               7825536  38 
i2c_core               24832  3 lm90,nvidia,i2c_viapro
agpgart                34760  2 nvidia,via_agp

```

```

~$ glxinfo

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
OpenGL renderer string: GeForce FX 5500/AGP/SSE/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x71 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x82 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x83 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x84 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x85 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x86 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x87 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x89 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8b 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x8c 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x8d 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8e 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x90 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x91 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x92 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x93 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x94 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x95 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x96 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x97 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x98 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon

```

```

~$ cat /etc/X11/xorg.conf

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Sceptre"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"Sceptre"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by PinkFloyd102489 on 2008-06-27
Download nvidia-settings and run it as root. Set the resolution using that.

---

### Post by suprfish on 2008-06-27
> **PinkFloyd102489 said:**
> Download nvidia-settings and run it as root. Set the resolution using that.

There is not an option for 1680 x 1050 in the display configuration tab :(

---

### Post by suprfish on 2008-06-27
Now, I did this:

```

~$ sudo dpkg-reconfigure xserver-xorg

```

And now xorg.conf looks like this:

```
 
# comments snipped
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
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
EndSection

```

Is this odd?

---

### Post by suprfish on 2008-06-27
OK now it seems to be messed up a bit (low graphics mode on reboot). I will restore the previous xorg.conf... :(

---

### Post by suprfish on 2008-06-27
It is now back to 1280 x 1024... Any ideas, anyone?

---

### Post by avtolle on 2008-06-27
Try```
gksudo displayconfig-gtk
```select your monitor if it is listed (note the options for both the vendor and the model), check to be sure your graphics card is detected, apply and see if that will help you.

---

### Post by flytripper on 2008-06-27
all i can think of is to use nvidia-settings but seeings as you havent got the entry for the resolution you want i dunno. sorry

---

### Post by suprfish on 2008-06-27
> **avtolle said:**
> Try```
gksudo displayconfig-gtk
```select your monitor if it is listed (note the options for both the vendor and the model), check to be sure your graphics card is detected, apply and see if that will help you.

The vendor (Sceptre) wasn't listed, so I put it to Generic 1680 x 1050 and ticked the 'Widescreen resolution' box. All it did was set the screen back to 1280 x 1024 after flickering for a bit.

After googling for a bit I found [this]("http://forums.nvidia.com/index.php?showtopic=9618&pid=401356&st=0&#entry401356") forum post, it seems to match my problem exactly. About 5 posts down the OP appears to have found a solution under Windows; how can I do this in Ubuntu?

I'll take a stab at it in a few...

---

### Post by suprfish on 2008-06-27
I haven't tried the above mentioned Windows solution, but after restarting my computer the desktop resolution is now correct, but the screen resolution is not (I have to scroll to see all of the screen). At least we are getting somewhere!

Ideas?

---

### Post by suprfish on 2008-06-27
My xorg.conf has changed again, I guess because of the displayconfig-gtk or the nvidia-settings... anyway, I made some more changes (commented out 'Section Screen' and 'Section Monitor' are is the old), I'll try them now...

```

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

#Section "Monitor"
#	Identifier	"Sceptre"
#	Vendorname	"Generic LCD Display"
#	Modelname	"LCD Panel 1680x1050"
#	Horizsync	31.5-65.5
#	Vertrefresh	56.0 - 65.0
#  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
#  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
#  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
#  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
#  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
#  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
#  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
#  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
#	Gamma	1.0
#EndSection

#Section "Screen"
#	Identifier	"Default Screen"
#	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
#	Monitor		"Sceptre"
#	Defaultdepth	24
#	SubSection "Display"
#		Depth	24
#		Virtual	1680	1050
#		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
#	EndSubSection
#EndSection

Section "Monitor"
Identifier	"Sceptre"
EndSection

Section "Screen"
Identifier	"Default Screen"
Device		"nVidia Corporation NV34 [GeForce FX 5500]"
Monitor		"Sceptre"
Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by suprfish on 2008-06-27
Ok that set it back to 1280 x 1024... changing it back :(

---

### Post by suprfish on 2008-06-27
Bump/recap

I cannot set my display (20.1" LCD) to the correct resolution, but I was able to set my desktop to the correct resolution (1680 x 1050).

**I found [this]("http://forums.nvidia.com/index.php?showtopic=9618&pid=401356&st=0&#entry401356") solution (5 posts down) for nearly the exact same problem in Windows, how can I apply it in Ubuntu?**

Help is appreciated!

---

### Post by suprfish on 2008-06-27
I've spent a bit on #ubuntu and most probably it is a problem with xorg.conf. I've commented out the 'virtual' setting in section "Screen" sub-section "Display" and that has made both the desktop and display resolutions to be 1280 x 1024. I'm going to take a break for the day, here's the plan for tomorrow:

1). See if I can work out [this]("http://forums.nvidia.com/index.php?showtopic=9618&pid=401356&st=0&#entry401356") solution.
2). Make the changes suggested [here]("http://www.linuxforums.org/forum/linux-desktop-x-windows/9010-virtual-desktop-size-wrong-fedora-mandrake-10-0-a.html").
3). If the above failed, I'll buy a D-Sub (VGA) to DVI converter and see if that works.

Any ideas/suggestions are greatly appreciated! I am getting somewhat desperate. :(

---

### Post by hopelessone on 2008-06-27
I used ENVY to fix my problems...worked 

```
sudo dpkg-reconfigure xserver-xorg
```

Then

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by suprfish on 2008-06-27
> **hopelessone said:**
> I used ENVY to fix my problems...worked 

```
sudo dpkg-reconfigure xserver-xorg
```

Then

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

What were the 'symptoms' of your problems? Were they like this? I will give it a shot.

---

### Post by suprfish on 2008-06-27
Nope, didn't change anything :[.

---

### Post by suprfish on 2008-06-27
Alright I have messed things up quite a bit, I'm going to do a reinstall of 8.04, maybe that'll do something...

---

### Post by suprfish on 2008-06-28
I now have a clean install, with the nvidia driver enabled. It's still at 1280 x 1024. Here's the xorg.conf now:

```

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
EndSection

```

After this, I did displayconfig-gtk, set it to 1680x1050; now the desktop resolution is correct, but the display is not. This is going in circles... anyone, any ideas??

---

### Post by suprfish on 2008-06-28
Looking at my Xorg.0.log file (/var/log), I've found this interesting bit:

```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 (NV34) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.04
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
(--) NVIDIA(0):     SceptreX20WG-Naga (DFP-0)
(--) NVIDIA(0): SceptreX20WG-Naga (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): SceptreX20WG-Naga (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1680x1050@60"; removing.
(WW) NVIDIA(0): No valid modes for "1600x1024@60"; removing.
(WW) NVIDIA(0): No valid modes for "1440x900@60"; removing.
(WW) NVIDIA(0): No valid modes for "800x600@56"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x800@60"
(II) NVIDIA(0):     "1280x720@60"
(II) NVIDIA(0):     "1280x768@60"
(II) NVIDIA(0):     "800x600@60"
(**) NVIDIA(0): Virtual screen size configured to be 1680 x 1050
(--) NVIDIA(0): DPI set to (79, 65); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[5] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[6] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[16] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[21] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[23] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[25] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[26] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[27] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[28] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "1280x800@60"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.

```

Current xorg.conf

```

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0

	modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
	modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
	modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes	"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen 0 	"Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "device" # 
	Identifier	"device1"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection

Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "ServerFlags"
EndSection

```

Helllllllllppppp

---

### Post by suprfish on 2008-06-28
bump

what configuration tools are available for nvidia cards?

---

### Post by suprfish on 2008-06-28
bump/recap:

I have set the desktop resolution correctly (1680 x 1050), but the display resolution is stuck at 1280 x 1024. It is like having a small "window" into my desktop; I must scroll in order to see all of it. I have a nvidia Geforce FX 5500 connected to a 20.1" LCD screen via DVI. When they were connected with D-Sub (VGA), it worked fine. 

Somehow, I need to set the display resolution to be 1680 x 1050. I believe this is done through the GPU (video card), but in nvidia-settings there is no 1680 x 1050 setting, it is capped at 1280 x 1024.

There is a very similar situation [here]("http://forums.nvidia.com/index.php?showtopic=9618") where the poster finds a solution under Windows. Can this be applied in my situation? HOWWWWWWWWWw

---

### Post by suprfish on 2008-06-28
Is there anything like a nvidia control panel in linux besides nvidia settings?

---

### Post by suprfish on 2008-06-28
Here are a couple of screenshots to illustrate the problem (nvidia-settings)

[IMG]http://img187.imageshack.us/img187/5039/screenshotnvidiaxserverpx1.png[/IMG]

The "Screen" (desktop) resolution is 1680 x 1050...

[IMG]http://img410.imageshack.us/img410/3826/screenshotnvidiaxserveraq6.png[/IMG]

but the display's resolution is capped at 1280 x 1024.
Any ideas, anyone?? :confused:

---

### Post by suprfish on 2008-06-28
Alright, I am all out of ideas. This problem seems to be "unsolvable" under Linux as of June 28 08; the culprit: bad hardware vendor support?
I am going to go and buy a D-Sub/DVI cable, that should probably work.

---

### Post by forger on 2008-06-28
That's weird, I have a 17" CRT screen that goes up to 1600x1024 (MSI nVidia 7300GT :)

1) What you could try is change the resolution manually through nvidia-settings (displayconfig-gtk is still bad)
```
sudo nvidia-settings
```
Head to "x server display configuration" > advanced > Panning: 1680x1050 > "Save to X configuration" > Quit. Then menu System > Quit > Log out and log in again.


2) If that didn't fix it, can you give me the full name of your nvidia card? Is it a pci-express card? What's your motherboard's vendor/model?
Post back the output of this: ```
lspci -vnn
```

3) Are you on an envy nvidia driver now?

4) Maybe nvidia capped it at a lower resolution because it's an older card?
Contact their support, do this and follow the instructions: ```
sudo nvidia-bug-report.sh
```

---

### Post by suprfish on 2008-06-28
1. no luck :[, just sets both the display res and desktop res to 1280 x 1024
2. Nvidia Geforce FX 5500 (256 mb), KT600 Dragon Ultra, PCI
```

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge [1106:3189] (rev 80)
	Subsystem: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge [1106:3189]
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI Bridge [1106:b198] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: e4000000-e5ffffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Capabilities: <access denied>

00:09.0 Ethernet controller [0200]: D-Link System Inc RTL8139 Ethernet [1186:1300] (rev 10)
	Subsystem: D-Link System Inc DFE-530TX+ 10/100 Ethernet Adapter [1186:1301]
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at 9000 [size=256]
	Memory at e6000000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
	Subsystem: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149]
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at 9400 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9c00 [size=8]
	I/O ports at a000 [size=4]
	I/O ports at a400 [size=16]
	I/O ports at a800 [size=256]
	Capabilities: <access denied>

00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE [1106:0571]
	Flags: bus master, medium devsel, latency 32, IRQ 17
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at ac00 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at b000 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at b400 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at b800 [size=32]
	Capabilities: <access denied>

00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at bc00 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. USB 2.0 [1106:3104]
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at e6001000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
	Subsystem: VIA Technologies, Inc. DFI KT600-AL / Soltek SL-B9D-FGR Motherboard [1106:3227]
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>

00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
	Subsystem: VIA Technologies, Inc. Soyo KT-600 Dragon Plus (Realtek ALC 650) [1106:4552]
	Flags: medium devsel, IRQ 19
	I/O ports at c000 [size=256]
	Capabilities: <access denied>

00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
	Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235 [1106:0102]
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at c400 [size=256]
	Memory at e6002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5500] [10de:0326] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. GeForce 5500 256 MB [1682:2034]
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 20
	Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	[virtual] Expansion ROM at e5000000 [disabled] [size=128K]
	Capabilities: <access denied>

```

3. Not the Envy version, no.

4. I had suspected this, but then I found the forum thread where the poster seems to have found a solution under Windows, but I cannot find a way to do the same thing with Linux.

---

### Post by forger on 2008-06-28
1) Can you also attach **/var/log/Xorg.0.log** ?

2) I've searched with google at forums, and most of them recommend recreating a new xorg.conf:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
check if it works without nvidia driver, the default one should be "vesa"

3) There was another way, but I can't really remember it, you add some values in xorg.conf about custom horizontal and vertical syncs using "Modeline".

You must find specification for your monitor and add "Modeline".
You can create the modelines using **videogen** (in ubuntu repositories) or **gtf**, but that's about it from my behalf :)

Here's your specification: [http://www.sceptre.com/products/lcd/Specifications/spec_x20wg_Naga.htm](http://www.sceptre.com/products/lcd/Specifications/spec_x20wg_Naga.htm)
and here: [http://ge.ubuntuforums.com/showthread.php?t=679298](http://ge.ubuntuforums.com/showthread.php?t=679298)
(The manual of your monitor ought to have more)

An example with gtf:
```

$ gtf 1680 1050 60

```
should output something like:
> 
  # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

You have to stick that modeline in your /etc/X11/xorg.conf :)

Don't forget to **try both nvidia** and **vesa** drivers - for example:
> Section "Device"
...
	Driver		"vesa"

or
> Section "Device"
...
	Driver		"nvidia"

You have an example of xorg.conf with modeline here:
[http://ubuntuforums.org/archive/index.php/t-354383.html](http://ubuntuforums.org/archive/index.php/t-354383.html)

4) As a last resort, try and find something here: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

P.S. I think that you have the same problem as this person: [http://ubuntuforums.org/showthread.php?t=326211](http://ubuntuforums.org/showthread.php?t=326211)

---

### Post by suprfish on 2008-06-28
1. I've got the D-Sub/DVI cable plugged in at the moment, and it seems to be working fine. When I had the DVI cable in, the log looked like [this]("http://ubuntuforums.org/showpost.php?p=5280320&postcount=20") (clipped a bit).

2. Regenerating the xorg.conf file would make it simply fall back to 1280 x 1024 for both the display and desktop resolutions. Vesa would break it :[

3. displayconfig generated these modelines; the Nvidia driver would just discard the ones higher than 1280x1024 (see log in #1).

4. I'll try this sometime later, but I think that the problem must be with the nvidia driver :(, so I've filed a bug report with them. In the thread you referenced to having the same problem the poster was able to solve it using an updated Intel driver. 

Just a side note: I had a Windows partition on this computer before I did a clean install of Ubuntu. I booted into it once to see whether it had the same problem, which it did. I assume that had I followed the solution given in the Windows forum thing that it would have been fixed; I didn't try, however :oops:.

Thanks for your help :D

---

### Post by gn2 on 2008-06-28
Try manually editing xorg.conf monitor section to show these different horiz + vert values.

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
        HorizSync     30.0 - 130.0
        VertRefresh   50.0 - 100.0

---

### Post by forger on 2008-06-29
well.. let's hope nvidia fixes it, I think the problem is with the driver as well

---

### Post by suprfish on 2008-07-02
After correspondence with a Nvidia tech, the problem has been solved (thanks Ronald Hui)! Add the following line to the screen section of your xorg.conf:
```
Option "ModeValidation" "NoMaxPClkCheck"
```

Woo Hoo! :popcorn:

---

### Post by atomspace on 2008-09-05
So now can you get all available resolutions out of your DVI port, as compared to the VGA port? I've read that the Geforce FX 5500, in ubuntu, doesn't offer all of the highest resolutions out of the dvi port that they do out of the vga port, by default; and to get these higher resolutions out the dvi port takes some tinkering.

Did this fix enable all resolutions available on the vga port to be usable on the dvi port? I ask because I have this card en-route to me, for use in a htpc, and I would like to get 1920 x 1080 out of the dvi port to run to my hdtv, and am curious if this fix with allow me to do so.

Also, was adding...

Option "ModeValidation" "NoMaxPClkCheck"

...to xorg.conf the only thing you did to fix it, or was that in addition to any previous changes to xorg.conf?

Thanks a lot for the info

---

### Post by suprfish on 2008-09-06
> **atomspace said:**
> So now can you get all available resolutions out of your DVI port, as compared to the VGA port? I've read that the Geforce FX 5500, in ubuntu, doesn't offer all of the highest resolutions out of the dvi port that they do out of the vga port, by default; and to get these higher resolutions out the dvi port takes some tinkering.

Did this fix enable all resolutions available on the vga port to be usable on the dvi port? I ask because I have this card en-route to me, for use in a htpc, and I would like to get 1920 x 1080 out of the dvi port to run to my hdtv, and am curious if this fix with allow me to do so.

Also, was adding...

Option "ModeValidation" "NoMaxPClkCheck"

...to xorg.conf the only thing you did to fix it, or was that in addition to any previous changes to xorg.conf?

Thanks a lot for the info

Apart from setting the monitor up as a widescreen at 1680x1050 (displayconfig-gtk), adding that line to xorg.conf was all I did. I think it should work for 1920 x 1080, just add the appropriate modelines (displayconfig-gtk) if it doesn't automatically (which you'll see it complain about in Xorg.0.log)

---

### Post by Oysterville on 2009-01-05
> **suprfish said:**
> After correspondence with a Nvidia tech, the problem has been solved (thanks Ronald Hui)! Add the following line to the screen section of your xorg.conf:
```
Option "ModeValidation" "NoMaxPClkCheck"
```

Woo Hoo! :popcorn:

After poking around the last hour, THIS fixed it for me.  Thanks!

---

### Post by yanaek on 2009-11-30
how is it possible?
[http://www.nvidia.com/page/pg_20040109440047.html](http://www.nvidia.com/page/pg_20040109440047.html)
nvidia says that FX can't display resolutions higher than 1600x1200 through DVI

well, anyway it works ;) but i was confused a bit with this option, it looks like PCIk , and it should be PClk  (with small "L" letter)

---

