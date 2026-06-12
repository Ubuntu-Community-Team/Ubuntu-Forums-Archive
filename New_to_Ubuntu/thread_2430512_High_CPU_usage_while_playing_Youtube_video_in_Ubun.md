---
title: "High CPU usage while playing Youtube video in Ubuntu 18.04 using Chrome/FF"
date: 2019-11-03
forum: New to Ubuntu
---

### Post by budan1976 on 2019-11-03
Hi,

I am new in Linux(Ubuntu) and have installed Ubuntu 18.04 in my dual boot laptop recently. My system detail is as below - 

[https://i.stack.imgur.com/9urR2.png](https://i.stack.imgur.com/9urR2.png)

Driver/GPU details --

[https://i.stack.imgur.com/CTmBC.png](https://i.stack.imgur.com/CTmBC.png)

And

[https://i.stack.imgur.com/ZyRt7.png](https://i.stack.imgur.com/ZyRt7.png)

Chrome GPU --

```
[COLOR=#000000][FONT=sans-serif]**Graphics Feature Status**


[LIST]
[*]Canvas: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]Flash: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]Flash Stage3D: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]Flash Stage3D Baseline profile: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]Compositing: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]Multiple Raster Threads: [COLOR=#008000]Enabled[/COLOR] 
[*]Out-of-process Rasterization: [COLOR=#FF0000]Disabled[/COLOR] 
[*]Hardware Protected Video Decode: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]Rasterization: [COLOR=#808000]Software only. Hardware acceleration disabled[/COLOR] 
[*]Skia Renderer: [COLOR=#808000]Disabled[/COLOR] 
[*]Video Decode: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]Viz Display Compositor: [COLOR=#008000]Enabled[/COLOR] 
[*]Viz Hit-test Surface Layer: [COLOR=#008000]Enabled[/COLOR] 
[*]WebGL: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]WebGL2: [COLOR=#008000]Hardware accelerated[/COLOR] 
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Driver Bug Workarounds**


[LIST]
[*]adjust_src_dst_region_for_blitframebuffer 
[*]clear_uniforms_before_first_program_use 
[*]count_all_in_varyings_packing 
[*]disable_post_sub_buffers_for_onscreen_surfaces 
[*]exit_on_context_lost 
[*]msaa_is_slow 
[*]rely_on_implicit_sync_for_swap_buffers 
[*]scalarize_vec_and_mat_constructor_args 
[*]disabled_extension_GL_KHR_blend_equation_advanced 
[*]disabled_extension_GL_KHR_blend_equation_advanced_coherent 
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Problems Detected**


[LIST]
[*]Clear uniforms before first program use on all platforms: [124764]("http://crbug.com/124764"), [349137]("http://crbug.com/349137")
*Applied Workarounds: [COLOR=#808000]clear_uniforms_before_first_program_use[/COLOR]* 
[*]Mesa drivers in Linux handle varyings without static use incorrectly: [333885]("http://crbug.com/333885")
*Applied Workarounds: [COLOR=#808000]count_all_in_varyings_packing[/COLOR]* 
[*]Disable partial swaps on Mesa drivers (detected with GL_RENDERER): [339493]("http://crbug.com/339493")
*Applied Workarounds: [COLOR=#808000]disable_post_sub_buffers_for_onscreen_surfaces[/COLOR]* 
[*]Always rewrite vec/mat constructors to be consistent: [398694]("http://crbug.com/398694")
*Applied Workarounds: [COLOR=#808000]scalarize_vec_and_mat_constructor_args[/COLOR]* 
[*]On Intel GPUs MSAA performance is not acceptable for GPU rasterization: [527565]("http://crbug.com/527565")
*Applied Workarounds: [COLOR=#808000]msaa_is_slow[/COLOR]* 
[*]Disable partial swaps on Mesa drivers (detected with GL_VERSION): [339493]("http://crbug.com/339493")
*Applied Workarounds: [COLOR=#808000]disable_post_sub_buffers_for_onscreen_surfaces[/COLOR]* 
[*]adjust src/dst region if blitting pixels outside framebuffer on Linux Intel: [664740]("http://crbug.com/664740")
*Applied Workarounds: [COLOR=#808000]adjust_src_dst_region_for_blitframebuffer[/COLOR]* 
[*]Disable KHR_blend_equation_advanced until cc shaders are updated: [661715]("http://crbug.com/661715")
*Applied Workarounds: [COLOR=#808000]disable(GL_KHR_blend_equation_advanced)[/COLOR], [COLOR=#808000]disable(GL_KHR_blend_equation_advanced_coherent)[/COLOR]* 
[*]Some drivers can't recover after OUT_OF_MEM and context lost: [893177]("http://crbug.com/893177")
*Applied Workarounds: [COLOR=#808000]exit_on_context_lost[/COLOR]* 
[*]Avoid waiting on a egl fence before swapping buffers and rely on implicit sync on Intel GPUs: [938286]("http://crbug.com/938286")
*Applied Workarounds: [COLOR=#808000]rely_on_implicit_sync_for_swap_buffers[/COLOR]* 
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Version Information**

[TABLE="width: 1889"]
[TR]
[TD]**Data exported**[/TD]
[TD]2019-11-03T09:49:27.112Z[/TD]
[/TR]
[TR]
[TD]**Chrome version**[/TD]
[TD]Chrome/78.0.3904.87[/TD]
[/TR]
[TR]
[TD]**Operating system**[/TD]
[TD]Linux 5.0.0-32-generic[/TD]
[/TR]
[TR]
[TD]**Software rendering list URL**[/TD]
[TD]https://chromium.googlesource.com/chromium/src/+/20c21f4010010f32462ea8e1d6af30cef66d48c8/gpu/config/software_rendering_list.json[/TD]
[/TR]
[TR]
[TD]**Driver bug list URL**[/TD]
[TD]https://chromium.googlesource.com/chromium/src/+/20c21f4010010f32462ea8e1d6af30cef66d48c8/gpu/config/gpu_driver_bug_list.json[/TD]
[/TR]
[TR]
[TD]**ANGLE commit id**[/TD]
[TD]66e0feec40dc[/TD]
[/TR]
[TR]
[TD]**2D graphics backend**[/TD]
[TD]Skia/78 a40a8a58755f952280cac9dfdcbf761aa7d29a52[/TD]
[/TR]
[TR]
[TD]**Command Line**[/TD]
[TD]/usr/bin/google-chrome-stable --flag-switches-begin --enable-oop-rasterization --ignore-gpu-blacklist --flag-switches-end[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Driver Information**

[TABLE="width: 1889"]
[TR]
[TD]**Initialization time**[/TD]
[TD]34[/TD]
[/TR]
[TR]
[TD]**In-process GPU**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Passthrough Command Decoder**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Sandboxed**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**GPU0**[/TD]
[TD]VENDOR = 0x10de, DEVICE= 0x134d[/TD]
[/TR]
[TR]
[TD]**GPU1**[/TD]
[TD]VENDOR = 0x8086, DEVICE= 0x5916 *ACTIVE*[/TD]
[/TR]
[TR]
[TD]**Optimus**[/TD]
[TD]true[/TD]
[/TR]
[TR]
[TD]**AMD switchable**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Driver vendor**[/TD]
[TD]Mesa[/TD]
[/TR]
[TR]
[TD]**Driver version**[/TD]
[TD]19.2.1[/TD]
[/TR]
[TR]
[TD]**GPU CUDA compute capability major version**[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]**Pixel shader version**[/TD]
[TD]4.50[/TD]
[/TR]
[TR]
[TD]**Vertex shader version**[/TD]
[TD]4.50[/TD]
[/TR]
[TR]
[TD]**Max. MSAA samples**[/TD]
[TD]16[/TD]
[/TR]
[TR]
[TD]**Machine model name**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Machine model version**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**GL_VENDOR**[/TD]
[TD]Intel Open Source Technology Center[/TD]
[/TR]
[TR]
[TD]**GL_RENDERER**[/TD]
[TD]Mesa DRI Intel(R) HD Graphics 620 (Kaby Lake GT2)[/TD]
[/TR]
[TR]
[TD]**GL_VERSION**[/TD]
[TD]4.5 (Core Profile) Mesa 19.2.1[/TD]
[/TR]
[TR]
[TD]**GL_EXTENSIONS**[/TD]
[TD]GL_3DFX_texture_compression_FXT1 GL_AMD_conservative_depth GL_AMD_depth_clamp_separate GL_AMD_draw_buffers_blend GL_AMD_gpu_shader_int64 GL_AMD_multi_draw_indirect GL_AMD_query_buffer_object GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_stencil_export GL_AMD_shader_trinary_minmax GL_AMD_texture_texture4 GL_AMD_vertex_shader_layer GL_AMD_vertex_shader_viewport_index GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_APPLE_object_purgeable GL_ARB_ES2_compatibility GL_ARB_ES3_1_compatibility GL_ARB_ES3_2_compatibility GL_ARB_ES3_compatibility GL_ARB_arrays_of_arrays GL_ARB_base_instance GL_ARB_blend_func_extended GL_ARB_buffer_storage GL_ARB_clear_buffer_object GL_ARB_clear_texture GL_ARB_clip_control GL_ARB_compressed_texture_pixel_storage GL_ARB_compute_shader GL_ARB_conditional_render_inverted GL_ARB_conservative_depth GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_cull_distance GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_derivative_control GL_ARB_direct_state_access GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_indirect GL_ARB_draw_instanced GL_ARB_enhanced_layouts GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_layer_viewport GL_ARB_fragment_shader GL_ARB_fragment_shader_interlock GL_ARB_framebuffer_no_attachments GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_get_program_binary GL_ARB_get_texture_sub_image GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64 GL_ARB_gpu_shader_int64 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_indirect_parameters GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multi_draw_indirect GL_ARB_occlusion_query2 GL_ARB_parallel_shader_compile GL_ARB_pipeline_statistics_query GL_ARB_pixel_buffer_object GL_ARB_point_sprite GL_ARB_polygon_offset_clamp GL_ARB_post_depth_coverage GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_query_buffer_object GL_ARB_robust_buffer_access_behavior GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_seamless_cubemap_per_texture GL_ARB_separate_shader_objects GL_ARB_shader_atomic_counter_ops GL_ARB_shader_atomic_counters GL_ARB_shader_ballot GL_ARB_shader_bit_encoding GL_ARB_shader_clock GL_ARB_shader_draw_parameters GL_ARB_shader_group_vote GL_ARB_shader_image_load_store GL_ARB_shader_image_size GL_ARB_shader_objects GL_ARB_shader_precision GL_ARB_shader_stencil_export GL_ARB_shader_storage_buffer_object GL_ARB_shader_subroutine GL_ARB_shader_texture_image_samples GL_ARB_shader_texture_lod GL_ARB_shader_viewport_layer_array GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_stencil_texturing GL_ARB_sync GL_ARB_tessellation_shader GL_ARB_texture_barrier GL_ARB_texture_buffer_object GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_buffer_range GL_ARB_texture_compression_bptc GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map_array GL_ARB_texture_filter_anisotropic GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_transform_feedback_instanced GL_ARB_transform_feedback_overflow_query GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_64bit GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ATI_blend_equation_separate GL_ATI_texture_float GL_EXT_abgr GL_EXT_blend_equation_separate GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_polygon_offset_clamp GL_EXT_provoking_vertex GL_EXT_shader_framebuffer_fetch GL_EXT_shader_framebuffer_fetch_non_coherent GL_EXT_shader_integer_mix GL_EXT_shader_samples_identical GL_EXT_texture_array GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_sRGB GL_EXT_texture_sRGB_R8 GL_EXT_texture_sRGB_decode GL_EXT_texture_shadow_lod GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array_bgra GL_EXT_vertex_attrib_64bit GL_IBM_multimode_draw_arrays GL_INTEL_conservative_rasterization GL_INTEL_performance_query GL_INTEL_shader_atomic_float_minmax GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent GL_KHR_context_flush_control GL_KHR_debug GL_KHR_no_error GL_KHR_parallel_shader_compile GL_KHR_robust_buffer_access_behavior GL_KHR_robustness GL_KHR_texture_compression_astc_ldr GL_KHR_texture_compression_astc_sliced_3d GL_MESA_framebuffer_flip_y GL_MESA_pack_invert GL_MESA_shader_integer_functions GL_MESA_texture_signed_rgba GL_NV_compute_shader_derivatives GL_NV_conditional_render GL_NV_depth_clamp GL_NV_fragment_shader_interlock GL_NV_packed_depth_stencil GL_NV_texture_barrier GL_OES_EGL_image GL_S3_s3tc[/TD]
[/TR]
[TR]
[TD]**Disabled Extensions**[/TD]
[TD]GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent[/TD]
[/TR]
[TR]
[TD]**Disabled WebGL Extensions**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Window system binding vendor**[/TD]
[TD]SGI[/TD]
[/TR]
[TR]
[TD]**Window system binding version**[/TD]
[TD]1.4[/TD]
[/TR]
[TR]
[TD]**Window system binding extensions**[/TD]
[TD]GLX_ARB_create_context GLX_ARB_create_context_no_error GLX_ARB_create_context_profile GLX_ARB_create_context_robustness GLX_ARB_fbconfig_float GLX_ARB_framebuffer_sRGB GLX_ARB_multisample GLX_EXT_create_context_es_profile GLX_EXT_create_context_es2_profile GLX_EXT_fbconfig_packed_float GLX_EXT_framebuffer_sRGB GLX_EXT_import_context GLX_EXT_libglvnd GLX_EXT_no_config_context GLX_EXT_texture_from_pixmap GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGIX_visual_select_group GLX_INTEL_swap_event[/TD]
[/TR]
[TR]
[TD]**Window manager**[/TD]
[TD]GNOME Shell[/TD]
[/TR]
[TR]
[TD]**XDG_CURRENT_DESKTOP**[/TD]
[TD]ubuntu:GNOME[/TD]
[/TR]
[TR]
[TD]**GDMSESSION**[/TD]
[TD]ubuntu[/TD]
[/TR]
[TR]
[TD]**Compositing manager**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Direct rendering version**[/TD]
[TD]DRI3[/TD]
[/TR]
[TR]
[TD]**Reset notification strategy**[/TD]
[TD]0x8252[/TD]
[/TR]
[TR]
[TD]**GPU process crash count**[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]**System visual ID**[/TD]
[TD]33[/TD]
[/TR]
[TR]
[TD]**RGBA visual ID**[/TD]
[TD]392[/TD]
[/TR]
[TR]
[TD]**gfx::BufferFormats supported for allocation and texturing**[/TD]
[TD]R_8: not supported, R_16: not supported, RG_88: not supported, BGR_565: not supported, RGBA_4444: not supported, RGBX_8888: not supported, RGBA_8888: not supported, BGRX_8888: not supported, BGRX_1010102: not supported, RGBX_1010102: not supported, BGRA_8888: not supported, RGBA_F16: not supported, YVU_420: not supported, YUV_420_BIPLANAR: not supported, P010: not supported[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Compositor Information**

[TABLE="width: 1889"]
[TR]
[TD]**Tile Update Mode**[/TD]
[TD]One-copy[/TD]
[/TR]
[TR]
[TD]**Partial Raster**[/TD]
[TD]Enabled[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**GpuMemoryBuffers Status**

[TABLE="width: 1889"]
[TR]
[TD]**R_8**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**R_16**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RG_88**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGR_565**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBA_4444**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBX_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBA_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGRX_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGRX_1010102**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBX_1010102**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGRA_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBA_F16**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**YVU_420**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**YUV_420_BIPLANAR**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**P010**[/TD]
[TD]Software only[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Display(s) Information**

[TABLE="width: 1889"]
[TR]
[TD]**Info**[/TD]
[TD]Display[2785062953156674] bounds=[0,0 1920x1080], workarea=[0,27 1920x985], scale=1, external.[/TD]
[/TR]
[TR]
[TD]**Color space information**[/TD]
[TD]{primaries_d50_referred: [[0.5984, 0.3641], [0.3691, 0.5730], [0.1738, 0.1693]], transfer:IEC61966_2_1, matrix:RGB, range:FULL}[/TD]
[/TR]
[TR]
[TD]**SDR white level in nits**[/TD]
[TD]80[/TD]
[/TR]
[TR]
[TD]**Bits per color component**[/TD]
[TD]8[/TD]
[/TR]
[TR]
[TD]**Bits per pixel**[/TD]
[TD]24[/TD]
[/TR]
[TR]
[TD]**Refresh Rate in Hz**[/TD]
[TD]120[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Video Acceleration Information**



[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Log Messages**


[LIST]
[*][2317:2317:1103/090935.689927:ERROR:sandbox_linux.cc(369)] : InitializeSandbox() called with multiple threads in process gpu-process. 
[*][2317:2317:1103/090935.973557:ERROR:buffer_manager.cc(488)] : [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command 
[*][2317:2317:1103/091025.091043:ERROR:buffer_manager.cc(488)] : [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command 
[*][2317:2317:1103/091042.780214:ERROR:buffer_manager.cc(488)] : [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command 
[*][2317:2317:1103/091052.644895:ERROR:buffer_manager.cc(488)] : [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command 
[*][2317:2317:1103/091115.395199:ERROR:buffer_manager.cc(488)] : [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command 
[*][2317:2317:1103/091126.119403:ERROR:buffer_manager.cc(488)] : [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command 
[/LIST]
[/FONT][/COLOR]
```


When I play youtube video in Firefox/Chrome in only one tab I see the CPU usage is increasing massively


I have tried installing Chromium and no difference in cpu usage. Also  I think there is one process which is web content and that goes to high  as well.


  I have done necessary checks/turn off like plugins/extension/hardware acceleration in Chrome and FF but nothing works. 


  Any help is highly appreciated.

Thanks,
Raj

---

### Post by Autodave on 2019-11-03
This is a common complaint about FF and Chromium.  Personally, the only extension that I use is uBlock.  That tends to reduce some of the usage.

---

### Post by CatKiller on 2019-11-03
> **budan1976 said:**
> When I play youtube video in Firefox/Chrome in only one tab I see the CPU usage is increasing massively


I have tried installing Chromium and no difference in cpu usage. Also  I think there is one process which is web content and that goes to high  as well.

Firefox and Chrome both refuse to use hardware acceleration on Linux. You can turn the settings on, and they'll say they're using hardware acceleration, but they aren't. The version of Chromium in the repositories *also* refuses to use hardware acceleration, but there is a [custom build with a PPA](https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html) that has it re-enabled.

Even when you've got hardware acceleration working in the browser generally, you won't have hardware acceleration for YouTube unless your hardware is able to accelerate the VP8/VP9 that YouTube uses. You may only actually have hardware for decoding H.264, in which case you can use [an extension](https://chrome.google.com/webstore/detail/h264ify/aleakchihdccplidncghkekgioiakgal) to request H.264-encoded versions instead.

---

