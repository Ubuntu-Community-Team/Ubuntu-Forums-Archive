---
title: "can't switch resolution (no driver i think)"
date: 2015-12-10
forum: New to Ubuntu
---

### Post by mf_odin on 2015-12-10
hi, I am totally new to linux, wanted to give ubuntu a shot..
with no long presentation i installed it successfully on my old pc, but the resolution was too small, wanted to change it but it gives me just one resolution witch is 800*600
i head to AMD website and looked for my card driver i found it as a .run file, in installation process it gives me error that this driver needs some dependencies to work properly  but it didn't give me any clue where to head on...

my card is Radeon 2200 HD pro


EDIT : Sorry it's Radeon 2400 HD pro (not 2200)

---

### Post by mastablasta on 2015-12-10
AMD 2200 HD pro uses only open source driver which is part of the kernel.

higher resolution should be available. if nothing else via xrog.conf file, though that one shouldn't be necessary. I have old ATI radeon 9600XT and it finds resolution just fine. could it be that monitor is the issue?!

for starters I would provide some output data so we can see which chip is recognised by OS and such. more info here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

using code tags (the # icon) post the output of:
```
LIBGL_DEBUG=verbose glxinfo
```


you may need to install mesa-utils (should be in software center but here is the command to install it):

```
sudo apt-get install mesa-utils
```

also I can't find 2200 anywhere on the table. does it even exist?

---

### Post by kc1di on 2015-12-10
Hello mf_odin and Welcome to Ubuntu Linux, 

could you enter the following command in a terminal and post the  output here, this should tell us what chipset is being used and will determine the correct driver for your card. 
```
lspci -vvnn | grep VGA
```
also if you can go to the settings control panel under Hardware you should find the additional driver app.  which may install the correct driver for you.

---

### Post by mf_odin on 2015-12-10
hi guys, am sorry for not replying as soon as possible, i did a mistake trying to force the driver installation with --force i ended up rebooting with non graphical desktop, didn't want to ask you other question about it and leaving the main question i decided to reinstall ubuntu again (yes yes windows users mentality XD) ...

ok for Mr : [**[COLOR=#000000]mastablasta[/COLOR]**]("http://ubuntuforums.org/member.php?u=964486")
your command gives me

> 
~$ sudo apt-get install mesa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mesa-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mesa-utils' has no installation candidate



mr [**[COLOR=#000000]kc1d[/COLOR]**]("http://ubuntuforums.org/member.php?u=1839")
 	[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1839")
> 
~$ lspci -vvnn | grep VGA
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV610 [Radeon HD 2400 PRO] [1002:94c3] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+



and doing this

> 
~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV610 [Radeon HD 2400 PRO] [1002:94c3]



---

### Post by mf_odin on 2015-12-10
catch up XD
```

~$ LIBGL_DEBUG=verbose glxinfo
name of display: :0
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/r600_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/r600_dri.so
libGL: Can't open configuration file /home/odin/.drirc: No such file or directory.
libGL: Can't open configuration file /home/odin/.drirc: No such file or directory.
libGL: Using DRI2 for screen 0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV610 (DRM 2.43.0, LLVM 3.6.2)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 11.0.2
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend, 
    GL_AMD_pinned_memory, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trinary_minmax, GL_AMD_vertex_shader_layer, 
    GL_AMD_vertex_shader_viewport_index, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_ARB_ES2_compatibility, 
    GL_ARB_ES3_compatibility, GL_ARB_base_instance, 
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_clip_control, 
    GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_ARB_copy_buffer, GL_ARB_debug_output, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_direct_state_access, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_explicit_attrib_location, 
    GL_ARB_explicit_uniform_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_layer_viewport, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_get_program_binary, GL_ARB_get_texture_sub_image, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_occlusion_query2, 
    GL_ARB_pipeline_statistics_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_sprite, GL_ARB_program_interface_query, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sample_shading, 
    GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_objects, GL_ARB_shader_stencil_export, 
    GL_ARB_shader_subroutine, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_packing, 
    GL_ARB_stencil_texturing, GL_ARB_sync, GL_ARB_texture_barrier, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_buffer_object_rgb32, 
    GL_ARB_texture_buffer_range, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_float, GL_ARB_texture_mirror_clamp_to_edge, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_rectangle, GL_ARB_texture_rg, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_stencil8, 
    GL_ARB_texture_storage, GL_ARB_texture_storage_multisample, 
    GL_ARB_texture_swizzle, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_shader, GL_ARB_vertex_type_10f_11f_11f_rev, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_EXT_abgr, 
    GL_EXT_blend_equation_separate, GL_EXT_draw_buffers2, 
    GL_EXT_draw_instanced, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled, 
    GL_EXT_framebuffer_sRGB, GL_EXT_packed_depth_stencil, GL_EXT_packed_float, 
    GL_EXT_pixel_buffer_object, GL_EXT_polygon_offset_clamp, 
    GL_EXT_provoking_vertex, GL_EXT_shader_integer_mix, GL_EXT_texture_array, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_snorm, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_KHR_context_flush_control, GL_KHR_debug, 
    GL_MESA_pack_invert, GL_MESA_texture_signed_rgba, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_packed_depth_stencil, 
    GL_NV_texture_barrier, GL_OES_EGL_image, GL_OES_read_format, GL_S3_s3tc


OpenGL version string: 3.0 Mesa 11.0.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend, 
    GL_AMD_pinned_memory, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trinary_minmax, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_ES2_compatibility, 
    GL_ARB_ES3_compatibility, GL_ARB_base_instance, 
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_clip_control, 
    GL_ARB_color_buffer_float, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_ARB_copy_buffer, GL_ARB_debug_output, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_explicit_attrib_location, 
    GL_ARB_explicit_uniform_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_get_program_binary, 
    GL_ARB_get_texture_sub_image, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, 
    GL_ARB_internalformat_query, GL_ARB_invalidate_subdata, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multi_bind, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pipeline_statistics_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_robustness, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_objects, 
    GL_ARB_shader_stencil_export, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_stencil_texturing, 
    GL_ARB_sync, GL_ARB_texture_barrier, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_rectangle, GL_ARB_texture_rg, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_stencil8, 
    GL_ARB_texture_storage, GL_ARB_texture_storage_multisample, 
    GL_ARB_texture_swizzle, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_binding, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_polygon_offset_clamp, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shader_integer_mix, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_snorm, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_KHR_context_flush_control, GL_KHR_debug, GL_MESA_pack_invert, 
    GL_MESA_texture_signed_rgba, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fog_distance, 
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, GL_OES_EGL_image, 
    GL_OES_read_format, GL_S3_s3tc, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays


OpenGL ES profile version string: OpenGL ES 3.0 Mesa 11.0.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_APPLE_texture_max_level, GL_EXT_blend_minmax, 
    GL_EXT_color_buffer_float, GL_EXT_discard_framebuffer, 
    GL_EXT_draw_buffers, GL_EXT_map_buffer_range, GL_EXT_multi_draw_arrays, 
    GL_EXT_read_format_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_shader_integer_mix, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888, 
    GL_EXT_texture_rg, GL_EXT_texture_type_2_10_10_10_REV, 
    GL_EXT_unpack_subimage, GL_KHR_context_flush_control, GL_NV_draw_buffers, 
    GL_NV_fbo_color_attachments, GL_NV_read_buffer, GL_NV_read_depth, 
    GL_NV_read_depth_stencil, GL_NV_read_stencil, GL_OES_EGL_image, 
    GL_OES_EGL_image_external, GL_OES_EGL_sync, 
    GL_OES_compressed_ETC1_RGB8_texture, GL_OES_depth24, GL_OES_depth_texture, 
    GL_OES_depth_texture_cube_map, GL_OES_element_index_uint, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
    GL_OES_packed_depth_stencil, GL_OES_rgb8_rgba8, 
    GL_OES_standard_derivatives, GL_OES_stencil8, GL_OES_surfaceless_context, 
    GL_OES_texture_3D, GL_OES_texture_float, GL_OES_texture_float_linear, 
    GL_OES_texture_half_float, GL_OES_texture_half_float_linear, 
    GL_OES_texture_npot, GL_OES_vertex_array_object


480 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x2b6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x2b7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x2b8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x2b9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x2ba 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x2bb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x2bc 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x2bd 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x2be 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x2bf 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x2c0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x2c1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x2c2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x2c3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x2c4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x2c5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x2c6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x2c7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x2c8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x2c9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x2ca 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x2cb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x2cc 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x2cd 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x2ce 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x2cf 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x2d0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x2d1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x2d2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x2d3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x2d4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x2d5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x2d6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x2d7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x2d8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x2d9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x2da 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x2db 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x2dc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x2dd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x2de 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x2df 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x2e0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x2e1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x2e2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x2e3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x2e4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x2e5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x2e6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x2e7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x2e8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x2e9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x2ea 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x2eb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x2ec 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x2ed 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x2ee 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x2ef 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x2f0 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x2f1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x2f2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x2f3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x2f4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x2f5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x2f6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x2f7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x2f8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x2f9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x2fa 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x2fb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x2fc 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x2fd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x2fe 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x2ff 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x300 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x301 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x302 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x303 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x304 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x305 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x306 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x307 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x308 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x309 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x30a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x30b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x30c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x30d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x30e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x30f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x310 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x311 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x312 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x313 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x314 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x315 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x316 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x317 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x318 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x319 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x31a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x31b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x31c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x31d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x31e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x31f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x320 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x321 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x322 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x323 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x324 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x325 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x326 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x327 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x328 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x329 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x32a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x32b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x32c 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x32d 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x32e 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x32f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x330 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x331 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x332 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x333 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x334 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x335 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x336 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x337 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x338 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x339 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x33a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x33b 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x33c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x33d 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x33e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x33f 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x340 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x341 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x342 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x343 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x344 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x345 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x346 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x347 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x348 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x349 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x34a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x34b 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x34c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x34d 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x34e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x34f 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x350 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x351 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x352 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x353 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x354 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x355 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x356 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x357 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x358 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x359 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x35a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x35b 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x35c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x35d 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x35e 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x35f 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x360 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x361 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x362 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x363 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x364 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x365 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x366 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x367 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x368 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x369 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x36a 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x36b 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x36c 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x36d 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x36e 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x36f 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x370 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x371 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x372 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x373 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x374 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x375 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x376 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x377 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x378 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x379 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x37a 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x37b 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x37c 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x37d 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x37e 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x37f 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x380 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x381 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x382 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x383 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x384 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x385 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x386 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x387 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x388 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x389 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x38a 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x38b 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x38c 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x38d 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x38e 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x38f 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x390 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x391 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x392 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x393 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x394 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x395 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x396 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x397 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x398 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x399 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x39a 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x39b 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x39c 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x39d 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x39e 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x39f 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x3a0 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x3a1 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x3a2 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x3a3 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x3a4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x3a5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x3a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x3a7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x3a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x3a9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x3aa 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x3ab 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x3ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x3ad 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x3ae 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x3af 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x3b0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x3b1 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x3b2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x3b3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x3b4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x3b5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x3b6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x3b7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x3b8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x3b9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x3ba 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x3bb 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x3bc 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x3bd 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x3be 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x3bf 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x3c0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x3c1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x3c2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x3c3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x3c4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x3c5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x3c6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x3c7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x3c8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x3c9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x3ca 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x3cb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x3cc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x3cd 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x3ce 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x3cf 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x3d0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x3d1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x3d2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x3d3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x3d4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x3d5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x3d6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x3d7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x3d8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x3d9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x3da 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x3db 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x3dc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x3dd 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x3de 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x3df 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x3e0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x3e1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x3e2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x3e3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x3e4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x3e5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x3e6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x3e7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x3e8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x3e9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x3ea 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x3eb 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x3ec 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x3ed 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x3ee 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x3ef 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x3f0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x3f1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x3f2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x3f3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x3f4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x3f5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x3f6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x3f7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x3f8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x3f9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x3fa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x3fb 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x3fc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x3fd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x3fe 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x3ff 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x400 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x401 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x402 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x403 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x404 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x405 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x406 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x407 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x408 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x409 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x40a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x40b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x40c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x40d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x40e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x40f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x410 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x411 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x412 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x413 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x414 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x415 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x416 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x417 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x418 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x419 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x41a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x41b 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x41c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x41d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x41e 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x41f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x420 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x421 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x422 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x423 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x424 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x425 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x426 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x427 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x428 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x429 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x42a 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x42b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x42c 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x42d 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x42e 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x42f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x430 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x431 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x432 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x433 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x434 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x435 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x436 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x437 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x438 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x439 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x43a 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x43b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x43c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x43d 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x43e 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x43f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x440 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x441 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x442 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x443 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x444 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x445 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x446 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x447 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x448 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x449 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x44a 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x44b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x44c 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x44d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x44e 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x44f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x450 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x451 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x452 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x453 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x454 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x455 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x456 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x457 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x458 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x459 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x45a 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x45b 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x45c 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x45d 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x45e 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x45f 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x460 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x461 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x462 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x463 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x464 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x465 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x466 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x467 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x468 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x469 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x46a 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x46b 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x46c 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x46d 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x46e 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x46f 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x470 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x471 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x472 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x473 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x474 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x475 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x476 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x477 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x478 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x479 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x47a 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x47b 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x47c 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x47d 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x47e 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x47f 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x480 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x481 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x482 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x483 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x484 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x485 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x486 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x487 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x488 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x489 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x48a 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x48b 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x48c 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x48d 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x48e 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x48f 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x490 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x491 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x492 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x05d 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None


600 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x05f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x060 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x061 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x062 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x063 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x064 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x065 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x066 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x067 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x068 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x069 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x06a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x06b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x06c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x06f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x070 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x072 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x073 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x074 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x076 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x077 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x078 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x079 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x07a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x07b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x07c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x07d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x07e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x07f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x080 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x081 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x082 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x083 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x084 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x085 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x086 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x087 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x088 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x089 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x08a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x08b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x08c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x08e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x090 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x091 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x092 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x093 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x094 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x095 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x096 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x099 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x09a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x09c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x09e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a0 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0a7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0a8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0a9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0aa 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ab 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ac 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ad 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ae 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0af 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0b3 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0b4 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0b5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0b6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0b7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0b8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0b9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0ba 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0bb 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0bc 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0bd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0be 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0bf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0c0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0c1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0c2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0c3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0c4 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0c5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0c6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0c7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0c8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0c9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0ca 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0cb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0cc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0cd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0ce 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0cf 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x0d0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0d1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0d2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x0d3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0d4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0d5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x0d6 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0d7 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x0d8 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0d9 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x0da 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0db 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x0dc 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x0dd 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x0de 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x0df 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x0e0 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x0e1 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x0e2 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x0e3 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x0e4 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x0e5 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x0e6 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x0e7 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x0e8 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0e9 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x0ea 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0eb 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x0ec 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0ed 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x0ee 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x0ef 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x0f0 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x0f1 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x0f2 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x0f3 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x0f4 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x0f5 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x0f6 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x0f7 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x0f8 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x0f9 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x0fa 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x0fb 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x0fc 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x0fd 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x0fe 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x0ff 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x100 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x101 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x102 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x103 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x104 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x105 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x106 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x107 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x108 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x109 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x10a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x10b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x10c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x10d 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x10e 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x10f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x110 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x111 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x112 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x113 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x114 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x115 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x116 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x117 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x118 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x119 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x11a 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x11b 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x11c 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x11d 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x11e 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x11f 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x120 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x121 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x122 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x123 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x124 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x125 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x126 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x127 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x128 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x129 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x12a 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x12b 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x12c 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x12d 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x12e 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x12f 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x130 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x131 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x132 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x133 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x134 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x135 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x136 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x137 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x138 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x139 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x13a 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x13b 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x13c 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x13d 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x13e 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x13f 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x140 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x141 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x142 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x143 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x144 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x145 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x146 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x147 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x148 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x149 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x14a 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x14b 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x14c 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x14d 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x14e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x14f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x150  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x151  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x152  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x153  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x154  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x155  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x156  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x157  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x158  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x159  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x15a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x15b  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x15c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x15d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x15e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x15f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x160  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x161  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x162  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x163  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x164  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x165  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x166  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x167  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x168  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x169  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x16a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x16b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x16c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x16d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x16e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x16f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x170  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x171  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x172  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x173  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x174  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x175  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x176  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x177  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x178  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x179  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x17a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x17b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x17c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x17d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x17e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x17f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x180  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x181  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x182  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x183  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x184  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x185  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x186  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x187  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x188  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x189  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x18a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x18b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x18c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x18d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x18e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x18f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x190 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x191 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x192 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x193 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x194 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x195 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x196 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x197 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x198 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x199 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x19a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x19b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x19c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x19d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x19e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x19f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x1a0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x1a1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x1a2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x1a3 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x1a4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x1a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x1a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x1a7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x1a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x1a9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x1aa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x1ab 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x1ac 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x1ad 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x1ae 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x1af 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x1b0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x1b1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x1b2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x1b3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x1b4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x1b5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x1b6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x1b7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x1b8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x1b9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x1ba 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x1bb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x1bc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x1bd 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x1be 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x1bf 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x1c0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x1c1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x1c2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x1c3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x1c4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x1c5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x1c6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1c7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1c8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1c9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1ca 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1cb 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1cc 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1cd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1ce 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1cf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1d0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1d1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1d2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1d3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1d4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1d5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1d6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1d7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1d8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1d9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1da 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1db 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1dc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1dd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1de 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1df 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1e0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1e1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1e2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1e3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1e4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1e5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1e6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1e7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1e8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1e9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1ea 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1eb 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1ec 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1ed 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1ee 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1ef 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1f0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1f1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1f2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1f3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1f4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1f5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1f6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1f7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1f8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1f9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1fa 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1fb 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1fc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1fd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1fe 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1ff 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x200 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x201 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x202 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x203 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x204 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x205 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x206 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x207 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0 16 16 16 16  0 0 Slow
0x208 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x209 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x20a 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x20b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x20c 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  0 0 None
0x20d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0 16 16 16 16  0 0 Slow
0x20e 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x20f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x210 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x211 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x212 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  0 0 None
0x213 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0 16 16 16 16  0 0 Slow
0x214 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x215 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x216 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x217 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x218 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x219 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x21a 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x21b 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x21c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x21d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x21e 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x21f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x220 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  2 1 None
0x221 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x222 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  8 1 None
0x223 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x224 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x225 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x226 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x227 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x228 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x229 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  2 1 None
0x22a 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  4 1 None
0x22b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 16  0  0  0  0  0  8 1 None
0x22c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x22d 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x22e 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x22f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x230 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x231 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x232 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  2 1 None
0x233 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  4 1 None
0x234 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  0  0  0  0  0  8 1 None
0x235 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x236 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x237 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x238 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x239 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x23a 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x23b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  2 1 None
0x23c 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x23d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  8 1 None
0x23e 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x23f 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x240 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x241 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x242 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x243 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0 16 16 16  0  0 0 Slow
0x244 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x245 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x246 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x247 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x248 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  0 0 None
0x249 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0 16 16 16  0  0 0 Slow
0x24a 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x24b 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x24c 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x24d 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x24e 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  0 0 None
0x24f 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0 16 16 16  0  0 0 Slow
0x250 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x251 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x252 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x253 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x254 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x255 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x256 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x257 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x258 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x259 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x25a 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x25b 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x25c 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  2 1 None
0x25d 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x25e 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  8 1 None
0x25f 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x260 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x261 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x262 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x263 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x264 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x265 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  2 1 None
0x266 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  4 1 None
0x267 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 16  0  0  0  0  0  8 1 None
0x268 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x269 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x26a 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x26b 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x26c 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x26d 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x26e 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  2 1 None
0x26f 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  4 1 None
0x270 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  0  0  0  0  0  8 1 None
0x271 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x272 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x273 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x274 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x275 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x276 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x277 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  2 1 None
0x278 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x279 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  8 1 None
0x27a  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x27b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x27c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x27d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x27e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x27f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x280  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x281  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x282  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x283  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x284  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x285  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x286  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x287  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x288  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x289  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x28a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x28b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x28c  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x28d  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x28e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x28f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x290  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x291  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x292  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x293  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x294  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x295  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x296  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x297  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x298  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x299  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x29a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x29b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x29c  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x29d  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x29e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x29f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x2a0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x2a1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x2a2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x2a3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x2a4  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2a5  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2a6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2a7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2a8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2a9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2aa  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2ab  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2ac  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2ad  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2ae  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2af  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x2b0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2b1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2b2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x2b3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2b4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2b5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None



```

---

### Post by mastablasta on 2015-12-11
you could have just purged the fglrx driver and reinstalled the opensource one. no need to reinstall the OS for that.

mesa-utils might be in universe: [http://packages.ubuntu.com/trusty/mesa-utils](http://packages.ubuntu.com/trusty/mesa-utils)

anyway from this data we found out your ship is RV610 which according to this page: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) should have full 3D support. and the next post shows is that is true. I am not sure if xorg.conf file is even generated. but resolution could be changed in that one as well you can try

```
man radeon
```

for instructions.

however, I find it strange that proper resolution is not offered if chip has full support. since you are in reinstalling mood - what happens if you try another version of Ubuntu like Kubuntu or Xubuntu?

---

### Post by mf_odin on 2015-12-11
hi again I wanted to create an Xorg file but after firing X -configure it gives me error thats there is no device found to configure and closed log file this is log file

```

[  1927.333] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[  1927.333] X Protocol Version 11, Revision 0
[  1927.333] Build Operating System: Linux 3.13.0-68-generic i686 Ubuntu
[  1927.333] Current Operating System: Linux odin-desktop 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:38:40 UTC 2015 i686
[  1927.333] Kernel command line: BOOT_IMAGE=/vmlinuz root=/dev/sda10
[  1927.333] Build Date: 12 November 2015  05:33:32PM
[  1927.333] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see http://www.ubuntu.com/support) 
[  1927.333] Current version of pixman: 0.32.6
[  1927.333]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  1927.333] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1927.333] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 11 09:08:28 2015
[  1927.352] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1927.359] (==) No Layout section.  Using the first Screen section.
[  1927.359] (==) No screen section available. Using defaults.
[  1927.359] (**) |-->Screen "Default Screen Section" (0)
[  1927.359] (**) |   |-->Monitor "<default monitor>"
[  1927.360] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  1927.360] (==) Automatically adding devices
[  1927.360] (==) Automatically enabling devices
[  1927.360] (==) Automatically adding GPU devices
[  1927.385] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1927.385]     Entry deleted from font path.
[  1927.385] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1927.385]     Entry deleted from font path.
[  1927.385] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1927.385]     Entry deleted from font path.
[  1927.385] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1927.385]     Entry deleted from font path.
[  1927.385] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1927.385]     Entry deleted from font path.
[  1927.385] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1927.385] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1927.385] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1927.385] (II) Loader magic: 0x802d86c0
[  1927.385] (II) Module ABI versions:
[  1927.385]     X.Org ANSI C Emulation: 0.4
[  1927.385]     X.Org Video Driver: 19.0
[  1927.385]     X.Org XInput driver : 21.0
[  1927.385]     X.Org Server Extension : 9.0
[  1927.386] (II) xfree86: Adding drm device (/dev/dri/card0)
[  1927.388] (--) PCI:*(0:1:0:0) 1002:94c3:174b:e370 rev 0, Mem @ 0xc0000000/268435456, 0xd0020000/65536, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[  1927.388] (II) LoadModule: "glx"
[  1927.403] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1927.459] (II) Module glx: vendor="X.Org Foundation"
[  1927.460]     compiled for 1.17.2, module version = 1.0.0
[  1927.460]     ABI class: X.Org Server Extension, version 9.0
[  1927.460] (==) AIGLX enabled
[  1927.460] (==) Matched fglrx as autoconfigured driver 0
[  1927.460] (==) Matched ati as autoconfigured driver 1
[  1927.460] (==) Matched fglrx as autoconfigured driver 2
[  1927.460] (==) Matched ati as autoconfigured driver 3
[  1927.460] (==) Matched modesetting as autoconfigured driver 4
[  1927.460] (==) Matched fbdev as autoconfigured driver 5
[  1927.460] (==) Matched vesa as autoconfigured driver 6
[  1927.460] (==) Assigned the driver to the xf86ConfigLayout
[  1927.460] (II) LoadModule: "fglrx"
[  1927.466] (WW) Warning, couldn't open module fglrx
[  1927.466] (II) UnloadModule: "fglrx"
[  1927.466] (II) Unloading fglrx
[  1927.466] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  1927.466] (II) LoadModule: "ati"
[  1927.467] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  1927.467] (II) Module ati: vendor="X.Org Foundation"
[  1927.467]     compiled for 1.17.2, module version = 7.5.99
[  1927.467]     Module class: X.Org Video Driver
[  1927.467]     ABI class: X.Org Video Driver, version 19.0
[  1927.467] (II) LoadModule: "radeon"
[  1927.467] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  1927.468] (II) Module radeon: vendor="X.Org Foundation"
[  1927.468]     compiled for 1.17.2, module version = 7.5.99
[  1927.468]     Module class: X.Org Video Driver
[  1927.468]     ABI class: X.Org Video Driver, version 19.0
[  1927.468] (II) LoadModule: "modesetting"
[  1927.468] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1927.468] (II) Module modesetting: vendor="X.Org Foundation"
[  1927.468]     compiled for 1.17.2, module version = 1.17.2
[  1927.468]     Module class: X.Org Video Driver
[  1927.468]     ABI class: X.Org Video Driver, version 19.0
[  1927.468] (II) LoadModule: "fbdev"
[  1927.469] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1927.469] (II) Module fbdev: vendor="X.Org Foundation"
[  1927.469]     compiled for 1.17.1, module version = 0.4.4
[  1927.469]     Module class: X.Org Video Driver
[  1927.469]     ABI class: X.Org Video Driver, version 19.0
[  1927.469] (II) LoadModule: "vesa"
[  1927.469] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1927.469] (II) Module vesa: vendor="X.Org Foundation"
[  1927.469]     compiled for 1.17.1, module version = 2.3.4
[  1927.470]     Module class: X.Org Video Driver
[  1927.470]     ABI class: X.Org Video Driver, version 19.0
[  1927.470] (==) Matched fglrx as autoconfigured driver 0
[  1927.470] (==) Matched ati as autoconfigured driver 1
[  1927.470] (==) Matched fglrx as autoconfigured driver 2
[  1927.470] (==) Matched ati as autoconfigured driver 3
[  1927.470] (==) Matched modesetting as autoconfigured driver 4
[  1927.470] (==) Matched fbdev as autoconfigured driver 5
[  1927.470] (==) Matched vesa as autoconfigured driver 6
[  1927.470] (==) Assigned the driver to the xf86ConfigLayout
[  1927.470] (II) LoadModule: "fglrx"
[  1927.470] (WW) Warning, couldn't open module fglrx
[  1927.470] (II) UnloadModule: "fglrx"
[  1927.470] (II) Unloading fglrx
[  1927.470] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  1927.470] (II) LoadModule: "ati"
[  1927.471] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  1927.471] (II) Module ati: vendor="X.Org Foundation"
[  1927.471]     compiled for 1.17.2, module version = 7.5.99
[  1927.471]     Module class: X.Org Video Driver
[  1927.471]     ABI class: X.Org Video Driver, version 19.0
[  1927.471] (II) LoadModule: "modesetting"
[  1927.471] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1927.471] (II) Module modesetting: vendor="X.Org Foundation"
[  1927.471]     compiled for 1.17.2, module version = 1.17.2
[  1927.471]     Module class: X.Org Video Driver
[  1927.471]     ABI class: X.Org Video Driver, version 19.0
[  1927.471] (II) UnloadModule: "modesetting"
[  1927.471] (II) Unloading modesetting
[  1927.471] (II) Failed to load module "modesetting" (already loaded, 0)
[  1927.471] (II) LoadModule: "fbdev"
[  1927.472] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1927.472] (II) Module fbdev: vendor="X.Org Foundation"
[  1927.472]     compiled for 1.17.1, module version = 0.4.4
[  1927.472]     Module class: X.Org Video Driver
[  1927.472]     ABI class: X.Org Video Driver, version 19.0
[  1927.472] (II) UnloadModule: "fbdev"
[  1927.472] (II) Unloading fbdev
[  1927.472] (II) Failed to load module "fbdev" (already loaded, 0)
[  1927.472] (II) LoadModule: "vesa"
[  1927.472] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1927.472] (II) Module vesa: vendor="X.Org Foundation"
[  1927.472]     compiled for 1.17.1, module version = 2.3.4
[  1927.472]     Module class: X.Org Video Driver
[  1927.472]     ABI class: X.Org Video Driver, version 19.0
[  1927.472] (II) UnloadModule: "vesa"
[  1927.472] (II) Unloading vesa
[  1927.472] (II) Failed to load module "vesa" (already loaded, 0)
[  1927.472] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[  1927.481] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  1927.481] (II) FBDEV: driver for framebuffer: fbdev
[  1927.481] (II) VESA: driver for VESA chipsets: vesa
[  1927.481] (++) using VT number 7


[  1927.488] (II) [KMS] Kernel modesetting enabled.
[  1927.488] (WW) Falling back to old probe method for modesetting
[  1927.488] (WW) Falling back to old probe method for fbdev
[  1927.488] (II) Loading sub module "fbdevhw"
[  1927.488] (II) LoadModule: "fbdevhw"
[  1927.488] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1927.510] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1927.510]     compiled for 1.17.2, module version = 0.0.2
[  1927.510]     ABI class: X.Org Video Driver, version 19.0
[  1927.510] (WW) Falling back to old probe method for vesa
[  1927.510] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  1927.510] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  1927.510] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  1927.510] (==) RADEON(0): Default visual is TrueColor
[  1927.510] (==) RADEON(0): RGB weight 888
[  1927.510] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  1927.510] (--) RADEON(0): Chipset: "ATI Radeon HD 2400 Pro" (ChipID = 0x94c3)
[  1927.510] (II) Loading sub module "dri2"
[  1927.510] (II) LoadModule: "dri2"
[  1927.510] (II) Module "dri2" already built-in
[  1927.510] (II) Loading sub module "exa"
[  1927.510] (II) LoadModule: "exa"
[  1927.510] (II) Loading /usr/lib/xorg/modules/libexa.so
[  1927.523] (II) Module exa: vendor="X.Org Foundation"
[  1927.523]     compiled for 1.17.2, module version = 2.6.0
[  1927.523]     ABI class: X.Org Video Driver, version 19.0
[  1927.523] (II) RADEON(0): KMS Color Tiling: enabled
[  1927.523] (II) RADEON(0): KMS Color Tiling 2D: enabled
[  1927.523] (II) RADEON(0): KMS Pageflipping: enabled
[  1927.523] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[  1927.537] (II) RADEON(0): Output VGA-0 has no monitor section
[  1927.548] (II) RADEON(0): Output DIN has no monitor section
[  1927.560] (II) RADEON(0): Output DVI-0 has no monitor section
[  1927.573] (II) RADEON(0): EDID for output VGA-0
[  1927.573] (II) RADEON(0): Printing probed modes for output VGA-0
[  1927.573] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1927.573] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1927.573] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1927.573] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[  1927.573] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1927.584] (II) RADEON(0): EDID for output DIN
[  1927.596] (II) RADEON(0): EDID for output DVI-0
[  1927.596] (II) RADEON(0): Output VGA-0 connected
[  1927.596] (II) RADEON(0): Output DIN disconnected
[  1927.596] (II) RADEON(0): Output DVI-0 disconnected
[  1927.596] (II) RADEON(0): Using exact sizes for initial modes
[  1927.596] (II) RADEON(0): Output VGA-0 using initial mode 1024x768
[  1927.596] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  1927.596] (II) RADEON(0): mem size init: gart size :1fdee000 vram size: s:20000000 visible:1f9ab000
[  1927.596] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[  1927.596] (==) RADEON(0): DPI set to (96, 96)
[  1927.596] (II) Loading sub module "fb"
[  1927.596] (II) LoadModule: "fb"
[  1927.597] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1927.604] (II) Module fb: vendor="X.Org Foundation"
[  1927.604]     compiled for 1.17.2, module version = 1.0.0
[  1927.604]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1927.604] (II) Loading sub module "ramdac"
[  1927.604] (II) LoadModule: "ramdac"
[  1927.604] (II) Module "ramdac" already built-in
[  1927.604] (II) UnloadModule: "modesetting"
[  1927.604] (II) Unloading modesetting
[  1927.604] (II) UnloadModule: "fbdev"
[  1927.604] (II) Unloading fbdev
[  1927.604] (II) UnloadSubModule: "fbdevhw"
[  1927.604] (II) Unloading fbdevhw
[  1927.604] (II) UnloadModule: "vesa"
[  1927.604] (II) Unloading vesa
[  1927.604] (--) Depth 24 pixmap format is 32 bpp
[  1927.604] (II) RADEON(0): [DRI2] Setup complete
[  1927.604] (II) RADEON(0): [DRI2]   DRI driver: r600
[  1927.604] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[  1927.605] (II) RADEON(0): Front buffer size: 3072K
[  1927.605] (II) RADEON(0): VRAM usage limit set to 463230K
[  1927.605] (==) RADEON(0): DRI3 disabled
[  1927.605] (==) RADEON(0): Backing store enabled
[  1927.605] (II) RADEON(0): Direct rendering enabled
[  1927.605] (II) EXA(0): Driver allocated offscreen pixmaps
[  1927.605] (II) EXA(0): Driver registered support for the following operations:
[  1927.605] (II)         Solid
[  1927.605] (II)         Copy
[  1927.605] (II)         Composite (RENDER acceleration)
[  1927.605] (II)         UploadToScreen
[  1927.605] (II)         DownloadFromScreen
[  1927.605] (II) RADEON(0): Acceleration enabled
[  1927.605] (==) RADEON(0): DPMS enabled
[  1927.605] (==) RADEON(0): Silken mouse enabled
[  1927.605] (II) RADEON(0): Set up textured video
[  1927.605] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[  1927.605] (II) RADEON(0): [XvMC] Extension initialized.
[  1927.605] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1927.606] (--) RandR disabled
[  1927.620] (II) SELinux: Disabled on system
[  1927.663] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  1927.664] (II) AIGLX: enabled GLX_ARB_create_context
[  1927.664] (II) AIGLX: enabled GLX_ARB_create_context_profile
[  1927.664] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[  1927.664] (II) AIGLX: enabled GLX_INTEL_swap_event
[  1927.664] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  1927.664] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[  1927.664] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[  1927.664] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  1927.664] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[  1927.666] (II) AIGLX: Loaded and initialized r600
[  1927.666] (II) GLX: Initialized DRI2 GL provider for screen 0
[  1927.667] (II) RADEON(0): Setting screen physical size to 270 x 203
[  1927.707] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1927.731] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1927.731] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1927.731] (II) LoadModule: "evdev"
[  1927.731] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1927.732] (II) Module evdev: vendor="X.Org Foundation"
[  1927.732]     compiled for 1.17.1, module version = 2.9.2
[  1927.732]     Module class: X.Org XInput Driver
[  1927.732]     ABI class: X.Org XInput driver, version 21.0
[  1927.732] (II) Using input driver 'evdev' for 'Power Button'
[  1927.732] (**) Power Button: always reports core events
[  1927.732] (**) evdev: Power Button: Device: "/dev/input/event1"
[  1927.732] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1927.732] (--) evdev: Power Button: Found keys
[  1927.732] (II) evdev: Power Button: Configuring as keyboard
[  1927.732] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  1927.732] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1927.732] (**) Option "xkb_rules" "evdev"
[  1927.732] (**) Option "xkb_model" "pc105"
[  1927.732] (**) Option "xkb_layout" "fr"
[  1927.738] (II) XKB: reuse xkmfile /var/lib/xkb/server-1CA37FD61409D6C1EDB80880DF2DB1A574556A6A.xkm
[  1927.740] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1927.740] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1927.740] (II) Using input driver 'evdev' for 'Power Button'
[  1927.740] (**) Power Button: always reports core events
[  1927.740] (**) evdev: Power Button: Device: "/dev/input/event0"
[  1927.740] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1927.740] (--) evdev: Power Button: Found keys
[  1927.740] (II) evdev: Power Button: Configuring as keyboard
[  1927.740] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[  1927.740] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  1927.740] (**) Option "xkb_rules" "evdev"
[  1927.740] (**) Option "xkb_model" "pc105"
[  1927.740] (**) Option "xkb_layout" "fr"
[  1927.742] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event5)
[  1927.742] (II) No input driver specified, ignoring this device.
[  1927.742] (II) This device may have been added with another device file.
[  1927.742] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event7)
[  1927.742] (II) No input driver specified, ignoring this device.
[  1927.742] (II) This device may have been added with another device file.
[  1927.743] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event8)
[  1927.743] (II) No input driver specified, ignoring this device.
[  1927.743] (II) This device may have been added with another device file.
[  1927.743] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event9)
[  1927.743] (II) No input driver specified, ignoring this device.
[  1927.743] (II) This device may have been added with another device file.
[  1927.744] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event10)
[  1927.744] (II) No input driver specified, ignoring this device.
[  1927.744] (II) This device may have been added with another device file.
[  1927.745] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event6)
[  1927.745] (II) No input driver specified, ignoring this device.
[  1927.745] (II) This device may have been added with another device file.
[  1927.746] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event2)
[  1927.746] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[  1927.746] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[  1927.746] (**) Logitech USB Optical Mouse: always reports core events
[  1927.746] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event2"
[  1927.800] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc018
[  1927.800] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[  1927.800] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[  1927.800] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[  1927.800] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[  1927.800] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[  1927.800] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[  1927.800] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[  1927.800] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1927.800] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/0003:046D:C018.0001/input/input5/event2"
[  1927.800] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 8)
[  1927.800] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[  1927.800] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[  1927.800] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[  1927.801] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[  1927.801] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[  1927.802] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[  1927.802] (II) No input driver specified, ignoring this device.
[  1927.802] (II) This device may have been added with another device file.
[  1927.804] (II) config/udev: Adding input device Dell Dell USB Keyboard Hub (/dev/input/event3)
[  1927.804] (**) Dell Dell USB Keyboard Hub: Applying InputClass "evdev keyboard catchall"
[  1927.804] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard Hub'
[  1927.804] (**) Dell Dell USB Keyboard Hub: always reports core events
[  1927.804] (**) evdev: Dell Dell USB Keyboard Hub: Device: "/dev/input/event3"
[  1927.804] (--) evdev: Dell Dell USB Keyboard Hub: Vendor 0x413c Product 0x2010
[  1927.804] (--) evdev: Dell Dell USB Keyboard Hub: Found keys
[  1927.804] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as keyboard
[  1927.804] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.1/2-2.1:1.0/0003:413C:2010.0002/input/input6/event3"
[  1927.804] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard Hub" (type: KEYBOARD, id 9)
[  1927.804] (**) Option "xkb_rules" "evdev"
[  1927.804] (**) Option "xkb_model" "pc105"
[  1927.804] (**) Option "xkb_layout" "fr"
[  1927.806] (II) config/udev: Adding input device Dell Dell USB Keyboard Hub (/dev/input/event4)
[  1927.806] (**) Dell Dell USB Keyboard Hub: Applying InputClass "evdev keyboard catchall"
[  1927.807] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard Hub'
[  1927.807] (**) Dell Dell USB Keyboard Hub: always reports core events
[  1927.807] (**) evdev: Dell Dell USB Keyboard Hub: Device: "/dev/input/event4"
[  1927.807] (--) evdev: Dell Dell USB Keyboard Hub: Vendor 0x413c Product 0x2010
[  1927.807] (--) evdev: Dell Dell USB Keyboard Hub: Found absolute axes
[  1927.807] (II) evdev: Dell Dell USB Keyboard Hub: Forcing absolute x/y axes to exist.
[  1927.807] (--) evdev: Dell Dell USB Keyboard Hub: Found keys
[  1927.807] (II) evdev: Dell Dell USB Keyboard Hub: Forcing relative x/y axes to exist.
[  1927.807] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as mouse
[  1927.807] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as keyboard
[  1927.807] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.1/2-2.1:1.1/0003:413C:2010.0003/input/input7/event4"
[  1927.807] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard Hub" (type: KEYBOARD, id 10)
[  1927.807] (**) Option "xkb_rules" "evdev"
[  1927.807] (**) Option "xkb_model" "pc105"
[  1927.807] (**) Option "xkb_layout" "fr"
[  1927.807] (II) evdev: Dell Dell USB Keyboard Hub: initialized for absolute axes.
[  1927.808] (**) Dell Dell USB Keyboard Hub: (accel) keeping acceleration scheme 1
[  1927.808] (**) Dell Dell USB Keyboard Hub: (accel) acceleration profile 0
[  1927.808] (**) Dell Dell USB Keyboard Hub: (accel) acceleration factor: 2.000
[  1927.808] (**) Dell Dell USB Keyboard Hub: (accel) acceleration threshold: 4
[  1931.092] (II) XKB: reuse xkmfile /var/lib/xkb/server-1CA37FD61409D6C1EDB80880DF2DB1A574556A6A.xkm
[  1932.290] (II) XKB: reuse xkmfile /var/lib/xkb/server-7952B8D84CA6B50EB90A86CA7AB3CCAA38ACA27A.xkm
[  1932.379] (II) XKB: reuse xkmfile /var/lib/xkb/server-7952B8D84CA6B50EB90A86CA7AB3CCAA38ACA27A.xkm
[  1934.513] (II) XKB: reuse xkmfile /var/lib/xkb/server-9987A401A2ADE74A295E571FF6D422A4356C204D.xkm

```

wanted to create this Xorg.conf file because i found somewhere else that you can alter the file to add the desired resolution

---

### Post by mastablasta on 2015-12-11
> **mf_odin said:**
> 
wanted to create this Xorg.conf file because i found somewhere else that you can alter the file to add the desired resolution

that's how you would do it.

 unfortunately my knowledge on this is limited, so I will direct you to others with similar issues while someone more knowledgable comes by:
[http://ubuntuforums.org/showthread.php?t=1797811](http://ubuntuforums.org/showthread.php?t=1797811)

[http://ubuntuforums.org/showthread.php?t=2061399](http://ubuntuforums.org/showthread.php?t=2061399)

does aticonfig command still work?

---

### Post by mf_odin on 2015-12-11
thanks a lot mastablasta i SOLVED the problem
to explain what I did for other persons who have the same problem

i used the commands```

odin@odin-desktop:~$ cvt 1280 1024
odin@odin-desktop:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync


```
> 
I get the line (1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync) from previous command


```

odin@odin-desktop:~$ xrandr --addmode DVI-0 1280x1024_60.00
odin@odin-desktop:~$ xrandr --output --mode 1280x1024_60.00

```

the trick here as I understand the graphic card has a VGA and a DVI output, yesterday I did the same lines above, but nothing has changed, when i tap
```

odin@odin-desktop:~$ xrandr -q

```

I found that the mode was added as a DVI-0 even if am using VGA and even If put VGA-0 instead of DVI-0 in the command lines...
Today I plugged my screen using DVI port, the square unknown display (in Screen display) become cyan (was pink yesterday using vga cable), repeated the same lanes and Voilà I am able to switch to 1280x1024

thanks for your time mr mastablasta ):P

fun facts
1 - am a totalloy new to linux world
2 - I don't know even the hierarchy of folders in linux (where programs go where files system go..)
3 - I know only ls and cd in linux command lines (i don't understand what I typed above till now :lolflag: )


[SIZE=5][SIZE=2]4 -[/SIZE][COLOR=#ff0000]** I regret my days using Windows**[/COLOR][/SIZE]

---

