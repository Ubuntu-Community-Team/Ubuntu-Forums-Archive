---
title: "OpenGL is apparently borked for Nvidia right now ..."
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xeizo on 2011-09-25
It seems to be a known bug, judging from another thread here. Almost got me insane though. I even tried to install the longtime support 275.28 driver from Nvidia by myself.  I had to disable noexec in tempfs for my SSD to be able to start the install. Not succesful of course, when removing nvidia-current in Ububtu/Kubuntu so does Nouveau kick in and it is almost impossible to remove. Not helped by the new /run hierarchy probably unknown by Nvidia.   Anyway, during my rage I removed most of plymouth and jockey as well and managed to compile 275.28 but was only able to start it once from the commandline under safe boot. OpenGL worked fine with 275.28, but it was impossible to boot normally.  So I installed nvidia-current again, but to my surprise so does OpenGL now work seemingly flawless(glxgears 53345 frames in 5.0 seconds = 10668.949 FPS) and compositing is back up in KDE.  Hopefully this borkiness will soon be solved, in the meantime I only wonder what I did to make OpenGL work again? Did the unsuccesful 275.28-install provide for some missing links? Or was the problem Plymouth or Jockey somehow making OpenGL/compositing dead?

---

### Post by effenberg0x0 on 2011-09-25
Latest proprietary drivers, from NVidia website, 64-bit (280.13), working normally for me on GT9500, GT9600, GTS-450. Dual monitors, vdpau, tested on all of them. 

Regards,
Effenberg

---

### Post by sgage on 2011-09-25
> **effenberg0x0 said:**
> Latest proprietary drivers, from NVidia website, 64-bit (280.13), working normally for me on GT9500, GT9600, GTS-450. Dual monitors, vdpau, tested on all of them. 

Regards,
Effenberg

32-bit 280.13 working fine for me, GeForce 8500 GT.

---

### Post by xeizo on 2011-09-25
> **effenberg0x0 said:**
> Latest proprietary drivers, from NVidia website, 64-bit (280.13), working normally for me on GT9500, GT9600, GTS-450. Dual monitors, vdpau, tested on all of them. 

Regards,
Effenberg

 Well, they did "work" for me too, except OpenGL/compositing(vdpau worked). Mabe you haven't noticed or you're not running a clean install. Try glxgears for starters ...  edit. of course I'm not talking about the proprietary driver, but nvidia-current from the repos(also 280.13) but I thought it was clear.  Also I hope it was clear that they DO work for me now after messing around. But not out of the box.

---

### Post by sgage on 2011-09-25
> **xeizo said:**
> Well, they did "work" for me too, except OpenGL/compositing(vdpau worked). Mabe you haven't noticed or you're not running a clean install. Try glxgears for starters ...  edit. of course I'm not talking about the proprietary driver, but nvidia-current from the repos(also 280.13) but I thought it was clear.  Also I hope it was clear that they DO work for me now after messing around. But not out of the box.

nvidia-current IS the proprietary driver. Nouveau is the open-source driver.

---

### Post by xeizo on 2011-09-25
> **sgage said:**
> nvidia-current IS the proprietary driver. Nouveau is the open-source driver.

 I know. **But effenberg0x0 **wrote"from Nvidias website"which certainly is not the same thing as "nvidia-current"(even though they may have the same version number, in this case 280.13). If that makes things more clear.

---

### Post by sgage on 2011-09-25
> **xeizo said:**
> I know. **But effenberg0x0 **wrote"from Nvidias website"which certainly is not the same thing as "nvidia-current"(even though they may have the same version number, in this case 280.13). If that makes things more clear.

Not really :KS  The point being that nvidia-current is the latest stable version of the proprietary drivers available on the stock Oneiric repos. There may be more recent versions available in some ppa or other, or at the nvidia website. But they're all closed-source and proprietary. Vs. nouveau, which is open-source.

---

### Post by effenberg0x0 on 2011-09-25
Hi. Just tested a fresh install and my previous one. As I mentioned, the 64-bit 280.13 drivers from Nvidia website are working perfectly for me with the three NVidia cards I have at hand (GT9500, GT9600, GTS-450). sgage confirmed 8500. I think its all ok.

 > Try glxgears for starters
LOL. Thanks. Made my day. See below:

```

$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTS 450/PCI/SSE2
OpenGL version string: 4.1.0 NVIDIA 280.13
OpenGL shading language version string: 4.10 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_blend_func_extended, GL_ARB_color_buffer_float, 
    GL_ARB_compatibility, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_indirect, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_ES2_compatibility, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, GL_ARB_gpu_shader5, 
    GL_ARB_gpu_shader_fp64, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_imaging, GL_ARB_instanced_arrays, GL_ARB_map_buffer_range, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_robustness, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_objects, 
    GL_ARB_shader_precision, GL_ARB_shader_subroutine, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_include, 
    GL_ARB_shadow, GL_ARB_sync, GL_ARB_tessellation_shader, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_object_rgb32, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_swizzle, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_64bit, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_texture_type_2_10_10_10_REV, 
    GL_EXT_timer_query, GL_EXT_transform_feedback2, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_EXT_vertex_attrib_64bit, 
    GL_EXT_x11_sync_object, GL_EXT_import_sync_object, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_alpha_test, 
    GL_NV_blend_minmax, GL_NV_blend_square, GL_NV_complex_primitives, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_explicit_multisample, 
    GL_NV_fbo_color_attachments, GL_NV_fence, GL_NV_float_buffer, 
    GL_NV_fog_distance, GL_NV_fragdepth, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_geometry_shader4, 
    GL_NV_gpu_program4, GL_NV_gpu_program4_1, GL_NV_gpu_program5, 
    GL_NV_gpu_program_fp64, GL_NV_gpu_shader5, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_shader_buffer_load, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_lod_clamp, 
    GL_NV_texture_multisample, GL_NV_texture_rectangle, GL_NV_texture_shader, 
    GL_NV_texture_shader2, GL_NV_texture_shader3, GL_NV_transform_feedback, 
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_attrib_integer_64bit, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_OES_depth24, 
    GL_OES_depth32, GL_OES_depth_texture, GL_OES_element_index_uint, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
    GL_OES_packed_depth_stencil, GL_OES_rgb8_rgba8, 
    GL_OES_standard_derivatives, GL_OES_texture_3D, GL_OES_texture_float, 
    GL_OES_texture_float_linear, GL_OES_texture_half_float, 
    GL_OES_texture_half_float_linear, GL_OES_texture_npot, 
    GL_OES_vertex_array_object, GL_OES_vertex_half_float, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

84 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x028 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x029 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x030 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x031 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x032 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x033 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x035 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x037 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x038 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x039 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03b 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x040 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x041 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x042 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x043 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x044 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x045 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x046 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x047 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x048 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x049 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x04a 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04c 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x04e 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x050 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x051 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x052 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x054 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x056 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x057 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x058 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x059 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x023 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x05a 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x05b 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x05c 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x05d 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x05e 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x05f 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x060 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x061 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x062 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x063 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x064 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x065 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x066 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x067 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x068 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x069 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x06a 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x06b 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x06c 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x06d 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x06e 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x06f 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x070 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x071 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x072 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x073 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x074 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon

167 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x075 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x076 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x078 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x079 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x07a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x07b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x07c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x07d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x07e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x080 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x081 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x082 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x083 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x085 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x087 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x089 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x08a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x08b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x08c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x08e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x090 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x091 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x092 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x095 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x096 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x098 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x099 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x09e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a0 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a1 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a2 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a5 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a6 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a7 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a8 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a9 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0aa 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ab 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ac 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ad 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0ae 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0af 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0b0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0b1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b3 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b5 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0b6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0b7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0b8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0b9 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0ba 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0bb 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0bc 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0bd 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0be 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0bf 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c3 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c4 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c5 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c6 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c9  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0ca  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0cb  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0cc  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0cd  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0ce  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0cf  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0d0  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0d1  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0d2  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0d3  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0d4  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d5  0 sg  0  32  0    . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d6  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d7  0 sg  0  32  0    y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d8  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d9  0 sg  0  32  0    . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0da  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0db  0 sg  0  32  0    y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0dc  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0dd  0 sg  0  64  0    . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0de  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0df  0 sg  0  64  0    y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0e0  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e1  0 sg  0 128  0    . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e2  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e3  0 sg  0 128  0    y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e4  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e5  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e6  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e7  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e8  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e9  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0ea  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0eb  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0ec  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ed  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ee  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ef  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0f0  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f1  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f2  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f3  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f4  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f5  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f6  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f7  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f8  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f9  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0fa  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0fb  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0fc  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fd  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fe  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0ff  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x100  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x101  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x102  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x103  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x104  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x105  0 sg  0  16  0    . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x106  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x107  0 sg  0  16  0    y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x108  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x109  0 sg  0  64  0    . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x10a  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x10b  0 sg  0  64  0    y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x10c  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10d  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10e  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10f  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x110  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x111  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x112  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x113  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x114  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x116  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x117  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x118  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x119  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x11a  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x11b  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None

```Regards,
Effenberg

[B]EDIT
[/B]Just tested a fresh one with nvidia-current from standard repos. Same results. All ok.

---

### Post by effenberg0x0 on 2011-09-25
For anyone having any issue with NVidia, I'd recommend a simple purge / reinstall, like:

```

sudo apt-get remove --purge nvclock nvclock-gtk nvclock-qt nvidia-173 nvidia-173-dev nvidia-173-updates nvidia-174-updated-dev nvidia-96 nvidia-96-dev nvidia-cg-toolkit nvidia-common nvidia-current nvidia-current-dev nvidia-current-updates nvidia-current-updates-dev nvidia-settings nvidia-settings-updates && sudo apt-get update && sudo apt-get install nvidia-current. 

```I'd probably do the same to compiz* just in case. Anyway, regarding fresh/non-fresh installs, it doesn't really matter as long as dependencies are met (or not). See the "cheat sheet" for the latest drivers. 

```

nvidia-current
  Depends: x11-common
  Depends: make
  Depends: sed
  Depends: dkms
  Depends: linux-libc-dev
  Depends: libc6-dev
 |Depends: linux-headers-generic
  Depends: <linux-headers>
    linux-headers-3.0.0-10
    linux-headers-3.0.0-10-generic
    linux-headers-3.0.0-11
    linux-headers-3.0.0-11-generic
    linux-headers-3.0.0-11-server
    linux-headers-3.0.0-11-virtual
    linux-headers-3.0.0-12
    linux-headers-3.0.0-12-generic
    linux-headers-3.0.0-12-server
    linux-headers-3.0.0-12-virtual
    linux-headers-3.0.0-7
    linux-headers-3.0.0-7-generic
    linux-headers-3.0.0-9
    linux-headers-3.0.0-9-generic
    linux-headers-3.0.4
  Depends: patch
  Depends: acpid
  Depends: libc6
  Depends: libgcc1
  Depends: libx11-6
  Depends: libxext6
  Depends: libxv1
  Depends: libxvmc1
  Depends: zlib1g
  Depends: <xorg-video-abi-10>
    xserver-xorg-core
  Depends: xserver-xorg-core
  Recommends: nvidia-settings
  Conflicts: <nvidia-180-modaliases>
  Conflicts: <nvidia-180-modaliases:i386>
  Conflicts: <nvidia-185-modaliases>
  Conflicts: <nvidia-185-modaliases:i386>
  Conflicts: <nvidia-current-modaliases>
  Conflicts: <nvidia-current-modaliases:i386>
  Replaces: <nvidia-180-modaliases>
  Replaces: <nvidia-180-modaliases:i386>
  Replaces: <nvidia-185-modaliases>
  Replaces: <nvidia-185-modaliases:i386>
  Replaces: <nvidia-current-modaliases>
  Replaces: <nvidia-current-modaliases:i386>
  Conflicts: nvidia-current:i386

```Effenberg

[B]EDIT
[/B]Just remembered some folks with wrong xorg.conf that could not use glx on alpha 1 or maybe a little later, not sure, can't find the specific thread. Checking xorg.conf / removing it, nvidia-xconfig, sudo *dpkg-reconfigure* -phigh xserver-xorg are probably worth mentioning.

---

### Post by t1497f35 on 2011-09-26
> **xeizo said:**
> ... I even tried to install the longtime support 275.28 driver from Nvidia by myself ....  So I installed nvidia-current again, but to my surprise so does OpenGL now work seemingly flawless...
IMO Nvidia installer can't properly uninstall the nvidia-current, neither nvidia-current can't properly uninstall all libs of the Nvidia installer, so different apps being confused about that might be using different nvidia libs. I noticed this myself, that when I look at /usr/libs I found remains of the "uninstalled" nvidia libs and a few symlinks were broken.

---

### Post by xeizo on 2011-09-26
A few useful tips here in the thread at last, yes, things can get borked. The unawesomeness of uninstalling different Nvidia-drivers packaged or not also came to my attention. That in itself is a bad thing. A removal should be a removal, especially for such an important thing as a video driver. Way too much dependencies on the loose here. 

But the real problem for me was that it was borked from the start, fresh install. Beta 2. No glx whatsoever, but the rest of the driver working(280.13, the packaged one). I'm itchy about video driver issues as they are so essential to modern guis(kwin, compiz, unity 3D ect.). And because I like to run an occasional 3D-game on Linux.

I never had this problem before, not even when running ricotz/xorg-edgers for the main part of Oneirics cycle, the biggest obstacle with ricotz/xorg-edgers was the ABI-changes which killed the driver totally but was easy fixed with noABI. Now I was running vanilla main server.

---

### Post by Sworddragon on 2011-09-26
Say us at which files are /usr/lib32/libGL.so, /usr/lib32/libGL.so.1 and /usr/lib32/libGL.so.1.2 pointing.

---

### Post by xeizo on 2011-09-26
> **Sworddragon said:**
> Say us at which files are /usr/lib32/libGL.so, /usr/lib32/libGL.so.1 and /usr/lib32/libGL.so.1.2 pointing.

Too bad I didn't check that earlier, when things didn't work, but it was interesting anyway because something is bugged even though the driver works:

/usr/lib32/libGL.so => libGL.so.1
/usr/lib32/libGL.so.1 => libGL.so.275.28
and /usr/lib32/libGL.so.1.2 is missing!

It looks the exact same in /usr/lib (I run x64)

So I'm running 280.13 off the repos but are using OpenGL from 275.28(from Nvidias site)! I wonder if I even had any OpenGL at all before, mabe something in the current 280.13 package that forgets to install OpenGL-files? Those who don't use fresh installs, contrary to what I did, may already have OpenGL-files of some version in place and are not visibly affected since OpenGL apparently seems to work cross-version.

Strange. Mabe I should go back to xorg-edgers to have some familiar breakage instead  ;)

---

### Post by Sworddragon on 2011-09-26
You can link /usr/lib32/libGL.so to /usr/lib32/nvidia-current/libGL.so and /usr/lib32/libGL.so.1 to /usr/lib32/nvidia-current/libGL.so.1 to solve this problem.

---

### Post by xeizo on 2011-09-26
> **Sworddragon said:**
> You can link /usr/lib32/libGL.so to /usr/lib32/nvidia-current/libGL.so and /usr/lib32/libGL.so.1 to /usr/lib32/nvidia-current/libGL.so.1 to solve this problem.

And so I did, for both /usr/lib32 and /usr/lib. Now I'm using the matching OpenGL-files:

> OpenGL version string: 3.3.0 NVIDIA **280.13**
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_blend_func_extended, GL_ARB_color_buffer_float,                                      
    GL_ARB_compatibility, GL_ARB_copy_buffer............

Thank's!

---

### Post by xeizo on 2011-09-29
After todays updates, the trick above doesn't work anymore. OpenGL is really, really impossible to start. Something else is borked.

Any idea?

I've removed the driver from Nvidias site and is only running nvidia-current, I've also removed xorg-conf but to no help.

I've seen lots of other threads with Unity 3D, Compiz and GS not running so I guess all this is related. I bet those other folks has Nvidia cards as well.

Mabe it will be more stable if I change to xorg-edgers/ricotz instead ...

---

### Post by Harry33 on 2011-09-29
> **xeizo said:**
> After todays updates, the trick above doesn't work anymore. OpenGL is really, really impossible to start. Something else is borked.

Any idea?

I've removed the driver from Nvidias site and is only running nvidia-current, I've also removed xorg-conf but to no help.

I've seen lots of other threads with Unity 3D, Compiz and GS not running so I guess all this is related. I bet those other folks has Nvidia cards as well.

Mabe it will be more stable if I change to xorg-edgers/ricotz instead ...

If you enable xorg-edgers PPA, you will get xserver 1.11.1 and then nvidia-current will not even work.
With
```
Section "ServerFlags"
    Option         "IgnoreABI" "True"
EndSection

```in xorg.conf helps a lot but still 3D sessions may become difficult to start.

Ricotz Testing PPA (Gnome-shell) is almost the same as Oneiric repo's Gnome-shell ATM.

---

### Post by xeizo on 2011-09-30
I tried xorg-edgers, with noABI of course, not any better so I removed Beta 2 completely and installed todays daily of Kubuntu instead. So far it works! No problem with OpenGL and nvidia-current. 

I never figured out what was wrong, happy that the problem is gone.

---

### Post by xeizo on 2011-10-02
Well, it worked for almost three days using the build from 30/9 and continuosly updating it, but now has todays updates from the main server killed OpenGL once again  :confused:

I really wonder what's going on, I've never encountered this bug in any other distro. Either does the proprietary driver work or not, that's the normal case, but now it is almost fully functional EXCEPT OpenGL aka 3D.

I can at least get compositing going using Xrender, but in exchange for a performance hit. I want my OpenGL back!!!

---

### Post by effenberg0x0 on 2011-10-02
Hey,

Maybe your latest updates messed with those libGL* links again?
ls -lah /usr/lib32/libGL*

It's happening for me frequently. I prefer to use the proprietary drivers, but dist-upgrades install nvidia-current, jockey also brakes nvidia install, etc. Fixing those links every now and then is whats working for me.


This is how it looks for me when the installation is working perfectly (right after proprietary drivers reinstall:
```

[05:11 ][al:AL-DESK:~]
$ cd /usr/lib32

[06:50 ][al:AL-DESK:/usr/lib32]
$ ls -la libGL*
-rw-r--r-- 1 root root    656 2011-09-29 12:03 libGL.la
lrwxrwxrwx 1 root root     15 2011-09-29 19:07 libGL.so -> mesa/libGL.so.1
lrwxrwxrwx 1 root root     15 2011-09-29 12:03 libGL.so.1 -> libGL.so.280.13
-rwxr-xr-x 1 root root 794628 2011-09-29 12:03 libGL.so.280.13
lrwxrwxrwx 1 root root     11 2011-09-29 19:07 libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root     20 2011-09-29 19:07 libGLU.so.1 -> libGLU.so.1.3.071100
-rw-r--r-- 1 root root 460448 2011-08-10 05:28 libGLU.so.1.3.071100

[06:51 ][al:AL-DESK:/usr/lib32]
$ cd ../lib

[06:51 ][al:AL-DESK:/usr/lib]
$ ls -la libGL*
lrwxrwxrwx 1 root root      15 2011-04-02 14:37 libGLC.so.0 -> libGLC.so.0.0.7
-rw-r--r-- 1 root root  122864 2011-04-02 14:37 libGLC.so.0.0.7
-rw-r--r-- 1 root root  484632 2011-08-04 19:57 libGLEW.a
-rw-r--r-- 1 root root  424876 2011-08-04 19:57 libGLEWmx.a
lrwxrwxrwx 1 root root      18 2011-08-04 19:57 libGLEWmx.so -> libGLEWmx.so.1.5.2
lrwxrwxrwx 1 root root      18 2011-08-04 19:57 libGLEWmx.so.1.5 -> libGLEWmx.so.1.5.2
-rw-r--r-- 1 root root  292752 2011-08-04 19:57 libGLEWmx.so.1.5.2
lrwxrwxrwx 1 root root      16 2011-08-04 19:57 libGLEW.so -> libGLEW.so.1.5.2
lrwxrwxrwx 1 root root      16 2011-08-04 19:57 libGLEW.so.1.5 -> libGLEW.so.1.5.2
-rw-r--r-- 1 root root  337808 2011-08-04 19:57 libGLEW.so.1.5.2
-rw-r--r-- 1 root root     654 2011-09-29 12:03 libGL.la
lrwxrwxrwx 1 root root      10 2011-09-29 12:03 libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root      15 2011-09-29 12:03 libGL.so.1 -> libGL.so.280.13
-rwxr-xr-x 1 root root 1025968 2011-09-29 12:03 libGL.so.280.13

[06:51 ][al:AL-DESK:/usr/lib]
$ 

```Updates are also messing with Unity settings here. After every update, I usually have to go into ccsm (CompizConfig Settings Manager) and re-activate OpenGL, Composite and the Unity Plugin, in order to get a normal session.

Regards,
Effenberg

---

### Post by xeizo on 2011-10-02
Thanks, that was a very useful post, I'm positive for some mislinking but I'm not sure which link is the bad guy. Just relinking libGL.so doesn't work anymore, so theres more to it. I'll try to do something intelligent out of your post tomorrow, as it is past midnight where I am and I'm getting sleepy  ):P

btw. here's my borked linkage:
> lrwxrwxrwx 1 root root   34 2011-10-02 23:34 /usr/lib32/libGL.so -> /usr/lib32/nvidia-current/libGL.so
lrwxrwxrwx 1 root root   11 2011-09-30 00:07 /usr/lib32/libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root   20 2011-09-30 00:07 /usr/lib32/libGLU.so.1 -> libGLU.so.1.3.071100
-rw-r--r-- 1 root root 450K 2011-08-10 10:28 /usr/lib32/libGLU.so.1.3.071100


/usr/lib seems to be empty, I guess this could have something to do with the new infamous multiarch support thingy ...

---

### Post by xeizo on 2011-10-03
I installed the exact same driver from Nvidias site on top of nvidia-current and it worked when starting X from the commandline, but after a reboot it's borked again.

Something during boot is done the wrong way, apparently.

OR, could it have something to do with my using a RAM-disk as /tmp, I had to disable it to be able to install as it is noexec. But I enabled it again before reboot. Could it be some boot-scripts missing in action?

---

### Post by effenberg0x0 on 2011-10-03
I'm not sure about your RAM disk. I use one myself and don't see problems directly related to it.

We should have a look at the specific error that makes the X session not start. That would give us some good lead.

We can find it with:
sudo grep -i nvidia /var/log/Xorg.0.log

Regards,
Effenberg

---

### Post by xeizo on 2011-10-03
Here it is, still no OpenGL ...

```
  9856.863] (II) Module glx: vendor="NVIDIA Corporation"
[  9856.863] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[  9856.864] (II) LoadModule: "nvidia"
[  9856.865] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[  9856.867] (II) Module nvidia: vendor="NVIDIA Corporation"
[  9856.868] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011
[  9856.868] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  9856.869] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[  9856.869] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  9856.869] (==) NVIDIA(0): RGB weight 888
[  9856.869] (==) NVIDIA(0): Default visual is TrueColor
[  9856.869] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  9857.563] (II) NVIDIA(GPU-0): Display (Samsung SMB2230H (DFP-0)) does not support NVIDIA 3D
[  9857.563] (II) NVIDIA(GPU-0):     Vision stereo.
[  9857.564] (II) NVIDIA(0): NVIDIA GPU GeForce 9600 GT (G94) at PCI:1:0:0 (GPU-0)
[  9857.564] (--) NVIDIA(0): Memory: 524288 kBytes
[  9857.564] (--) NVIDIA(0): VideoBIOS: 62.94.82.00.00
[  9857.564] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  9857.564] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  9857.564] (--) NVIDIA(0): Connected display device(s) on GeForce 9600 GT at PCI:1:0:0
[  9857.564] (--) NVIDIA(0):     Samsung SMB2230H (DFP-0)
[  9857.564] (--) NVIDIA(0): Samsung SMB2230H (DFP-0): 330.0 MHz maximum pixel clock
[  9857.564] (--) NVIDIA(0): Samsung SMB2230H (DFP-0): Internal Dual Link TMDS
[  9857.594] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[  9857.594] (**) NVIDIA(0):     enabled on all display devices.
[  9857.631] (II) NVIDIA(0): Assigned Display Device: DFP-0
[  9857.631] (==) NVIDIA(0): 
[  9857.631] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  9857.631] (==) NVIDIA(0):     will be used as the requested mode.
[  9857.631] (==) NVIDIA(0): 
[  9857.631] (II) NVIDIA(0): Validated modes:
[  9857.631] (II) NVIDIA(0):     "nvidia-auto-select"
[  9857.631] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[  9857.657] (--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
[  9857.657] (--) NVIDIA(0):     option
[  9857.657] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  9857.662] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  9857.715] (==) NVIDIA(0): Disabling shared memory pixmaps
[  9857.715] (==) NVIDIA(0): Backing store disabled
[  9857.715] (==) NVIDIA(0): Silken mouse enabled
[  9857.715] (**) NVIDIA(0): DPMS enabled
[  9857.716] (II) NVIDIA(0): [DRI2] Setup complete

```

It seems like there is no GLX loading, why?

---

### Post by ventrical on 2011-10-03
Why does it say that your Samsung monitor does not support nvidia  3D graphics or is that a vanilla msg?


..and hence the loopback from the monitor would default to auto select I assume..

---

### Post by effenberg0x0 on 2011-10-03
My log is mainly equal to yours and GLX is loaded normally. There's no important line missing from your as far as I can see.

You shouldn't absolutely need a /etc/X11/xorg.conf to use X anymore, however nvidia-settings may create one for you. Wrong settings in this file could break your session. Can you check if you have this file and what's in it?

```

sudo gedit /etc/X11/xorg.conf (Get the contents, post here)
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo service lightdm start (To check if X session loads without the xorg.conf)

```As a test, I installed the proprietary driver from repos with sudo apt-get install nvidia-current. 

I have noticed that /usr/lib/xorg/modules/drivers/nvidia_drv.so is a soft link to /etc/alternatives/x86_64-linux-gnu_nvidia_drv

```

[10:42 ][al:AL-DESK:~]
$ ls -la /usr/lib/xorg/modules/drivers/nvidia_drv.so
lrwxrwxrwx 1 root root 45 2011-10-02 17:04 /usr/lib/xorg/modules/drivers/nvidia_drv.so -> /etc/alternatives/x86_64-linux-gnu_nvidia_drv

```/etc/alternatives/x86_64-linux-gnu_nvidia_drv is a soft link to /usr/lib/nvidia-current/xorg/nvidia_drv.so

```

[10:42 ][al:AL-DESK:~]
$ ls -la /etc/alternatives/x86_64-linux-gnu_nvidia_drv
lrwxrwxrwx 1 root root 42 2011-10-02 17:04 /etc/alternatives/x86_64-linux-gnu_nvidia_drv -> /usr/lib/nvidia-current/xorg/nvidia_drv.so

```And /usr/lib/nvidia-current/xorg/nvidia_drv.so exists.
```

[10:44 ][al:AL-DESK:~]
$ ls -la /usr/lib/nvidia-current/xorg/nvidia_drv.so
-rw-r--r-- 1 root root 6901792 2011-10-02 14:14 /usr/lib/nvidia-current/xorg/nvidia_drv.so

```Check these links in your setup. As you can see, they're the first NVidia thing X looks for when trying to run.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-10-03
> **ventrical said:**
> Why does it say that your Samsung monitor does not support nvidia  3D graphics or is that a vanilla msg?

I have never noticed that msg before, good eye Ventrical. I looked at 4 PCs here. Maybe there's a pattern. 1 monitor is connected with a standard cable (VGA 15-pin connector) and has this exact message on Xorg.0.log. Others 3 monitors, with DVI/HDMI connections, don't have this message on log.

Regards,
Effenberg

**EDIT**
I may be wrong. Found a PC here that has a good example. This PC has a NVidia 9500 GT connected to one LG 19-inch LCD monitor via RGB Cable and one 40" LCD via HDMI. The Xorg.0.log says:

```

[    33.018] (II) NVIDIA(GPU-0): Display (LG Electronics W1943 (CRT-1)) does not support NVIDIA
[    33.018] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    33.077] (II) NVIDIA(GPU-0): Display (AOC D42H831 (DFP-1)) does not support NVIDIA 3D
[    33.077] (II) NVIDIA(GPU-0):     Vision stereo.

```

---

### Post by xeizo on 2011-10-03
I use DVI, and the monitor has HDMI as well, which is connected to my Windows-box. But I guess the "3D not supported" message isn't about 3D as in 3D-games but 3D as in movies with Goggles .... (you need a 120Hz refreshrate for that).

Anyway, I tried the tips above, all of them. At best I got the nvidia-driver totally dead and replaced by nouveau.

So I started a new and installed the driver from nvidias site once again(I had to disable the RAM-disk for that to be possible). But this time I didn't enable the RAM-disk before rebooting and voila! 3D/OpenGL/compositing works once again. So, the installer must store some executables and/or scripts in the RAM-disk, the executables being non executable as I use the "noxec" option and the scripts vanishing as soon as the current is disconnected during reboot.

Right now I wonder how I should configure my RAM-disk for not killing Nvidia OpenGL everytime I reboot???

My /etc/fstab looks like this, any smart change I could make to it?

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=9560b02e-9e71-4a40-babb-xxxxxxxxxx /               ext4    noatime,discard,data=ordered,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2a7ec007-1007-4806-8ae9-xxxxxxxxxx none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#tmpfs /tmp tmpfs nodev,nosuid,noexec,mode=1777 0 0
```The tmpfs line is currently uncommented, hence the driver is working, but I sure would like it commented as not to cause unnecessary wear to my SSD.

edit. My new xorg.0.log now when everything is working(except RAM-disk):
```
[     6.118] (II) Module glx: vendor="NVIDIA Corporation"
[     6.119] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[     6.120] (II) LoadModule: "nvidia"
[     6.120] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[     6.126] (II) Module nvidia: vendor="NVIDIA Corporation"
[     6.129] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011
[     6.129] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     6.135] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[     6.141] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     6.141] (==) NVIDIA(0): RGB weight 888
[     6.141] (==) NVIDIA(0): Default visual is TrueColor
[     6.141] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     6.141] (**) NVIDIA(0): Option "TwinView" "0"
[     6.141] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[     7.766] (II) NVIDIA(GPU-0): Display (Samsung SMB2230H (DFP-0)) does not support NVIDIA 3D
[     7.766] (II) NVIDIA(GPU-0):     Vision stereo.
[     7.767] (II) NVIDIA(0): NVIDIA GPU GeForce 9600 GT (G94) at PCI:1:0:0 (GPU-0)
[     7.767] (--) NVIDIA(0): Memory: 524288 kBytes
[     7.767] (--) NVIDIA(0): VideoBIOS: 62.94.82.00.00
[     7.767] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     7.767] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[     7.767] (--) NVIDIA(0): Connected display device(s) on GeForce 9600 GT at PCI:1:0:0
[     7.767] (--) NVIDIA(0):     Samsung SMB2230H (DFP-0)
[     7.767] (--) NVIDIA(0): Samsung SMB2230H (DFP-0): 330.0 MHz maximum pixel clock
[     7.767] (--) NVIDIA(0): Samsung SMB2230H (DFP-0): Internal Dual Link TMDS
[     7.798] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[     7.798] (**) NVIDIA(0):     enabled on all display devices.
[     7.834] (II) NVIDIA(0): Assigned Display Device: DFP-0
[     7.834] (II) NVIDIA(0): Validated modes:
[     7.834] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[     7.834] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[     7.857] (--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
[     7.857] (--) NVIDIA(0):     option
[     7.857] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[     7.863] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[     7.936] (==) NVIDIA(0): Disabling shared memory pixmaps
[     7.936] (==) NVIDIA(0): Backing store disabled
[     7.936] (==) NVIDIA(0): Silken mouse enabled
[     7.937] (**) NVIDIA(0): DPMS enabled
[     7.937] (II) NVIDIA(0): [DRI2] Setup complete 
```

---

### Post by xeizo on 2011-10-03
I changed the last line of my /etc/fstab:
```
#tmpfs /tmp tmpfs nodev,nosuid,noexec,mode=1777 0 0
```which didn't work commented, to:
```
tmpfs /dev/shm tmpfs defaults,nosuid,noexec,rw 0 0 
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
```instead. And so far it seems persistent. God knows what more bugs it will introduce ;) Or is it right?

It seems that my /etc/fstab was to blame for this whole thread, even though it's not fully conclusive yet, interesting ...

---

### Post by ventrical on 2011-10-03
Nope , nope !! You can veiw 3d images (3dmovies) with most svga with 3d glasses or using the crosseyed method.

[http://www.youtube.com/user/TerryH1984?feature=pyv&ad=7994960868&kw=3D#p/u/0/cvShotHl1As](http://www.youtube.com/user/TerryH1984?feature=pyv&ad=7994960868&kw=3D#p/u/0/cvShotHl1As)

That warning  about your monitor means what it says.. (I'm quite sure). However I think that the montitor(s) in question have embedded tools for mode-set and of  the monitor is not pre-set  (or auto default) then it could be blocking a signal from the monitor to the nvidia card. 

  I am just curious as if  those mointors will render 3d on other graphics cards other than nvidia.

 As an audio/video instructional development tech I've seen this happen so many times... always check the hardware first for these mode-sets. There are lots of surprises :)

edit..

Yes , yes .. your right about the Three DEE!!!gaming.

 But I still think somethings wring with monitor settings.

---

