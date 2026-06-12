---
title: "IntelHD4000 problems"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by jonathan24 on 2014-02-14
Hi, I'm new to this site, so I say, hello. :)


Now on to my problem, which is a major problem for me, since many apps that rely on this refuse to work or even attempt to open.

My Ubuntu version is 12.04

I'm not really sure how to explain it since I'm pretty new to ubuntu, but know somewhat how to get around.

I typed this into terminal 'glxinfo | grep direct'

And it came out with 'Error: couldn't find RGB GLX visual or fbconfig'
 
I have no idea what this means or how I can fix it. So if anyone is willing to help me out I will be very gratful. :)

---

### Post by mikewhatever on 2014-02-14
Let us see the output of <sudo lshw -C display>.
Can you also explain why you are interested in the glxinfo output along the way.

---

### Post by jonathan24 on 2014-02-14
> **mikewhatever said:**
> Let us see the output of <sudo lshw -C display>.
Can you also explain why you are interested in the glxinfo output along the way.



I was interested in that output, because somewhere I was looking for a solution said that if the output showed FPS(Frames Per Second) my GFX is working properly.



Here is the output of 
[COLOR=#000000]
```
<sudo lshw -C display>.


[/COLOR]*-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:3000(size=64)
```


The resources parameter means how many MB the GFX has, correct? If so, then the size must mean how many MB it is, correct? If this is true then it must be using a proprietary driver, since my IntelHD4000 is supposed to be 256MB, if I'm not mistaken.

---

### Post by Yellow Pasque on 2014-02-14
Post your /var/log/Xorg.0.log  (use [ code ][ /code ] tags).

> **jonathan24 said:**
> The resources parameter means how many MB the GFX has, correct? If so, then the size must mean how many MB it is, correct?
Actually, I'm pretty sure it means 64-bit memory bus...

> If this is true then it must be using a proprietary driver
There is no proprietary driver for Intel GPU's (not counting the rebadged PowerVR garbage found on older Atoms).

---

### Post by jonathan24 on 2014-02-14
```
sudo: /var/log/Xorg.0.log: command not found
```


> **Temüjin said:**
> There is no proprietary driver for Intel GPU's (not counting the rebadged PowerVR garbage found on older Atoms).


The CPU I am using is a 1.8GHZ Intel Pentium4 Dual-Core.

---

### Post by mikewhatever on 2014-02-14
> **jonathan24 said:**
> I was interested in that output, because somewhere I was looking for a solution said that if the output showed FPS(Frames Per Second) my GFX is working properly.

...a solution for what? What is the problem?
> 
Here is the output of [COLOR=#000000]<sudo lshw -C display>.

[/COLOR]*-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:3000(size=64)


Looks good. The GPU is correctly recognized, and the correct driver is loaded.

> **Temüjin said:**
> 
...

There is no proprietary driver for Intel GPU's (not counting the rebadged PowerVR garbage found on older Atoms).

Actually, PowerVR GPUs are pretty decent, even with a non-free driver. Apple and Samsung don't seem to complain anyway. Intel is the only vendor, afaik, that couldn't get the driver right for any platform (Linux, Windows), and didn't even care.

---

### Post by jonathan24 on 2014-02-14
If the GPU is not the case, It must be an issue with OpenGL or DirectX.



EDIT: I just did input this code into terminal to check OpenGL version and this is what came about.


```
 glxinfo | grep "OpenGL version"

Error: couldn't find RGB GLX visual or fbconfig
Error: couldn't find RGB GLX visual or fbconfig

```

---

### Post by mikewhatever on 2014-02-14
Looks like there is a problem with glxinfo, not sure what's wrong though.

---

### Post by jonathan24 on 2014-02-14
Thanks for all your help guys. I figured out the problem. 

Somehow my laptop got Nvidia drivers installed and it was trying to use the Nvidia, and the Intel drivers were conflicting with it.

What I did was un-install the Nvidia drivers using 

```
[FONT=Ubuntu Mono]sudo apt-get purge nvidia*

Then removed Xorg.conf
[/FONT]
sudo rm /etc/X11/xorg.conf


Then completely re-installed Xorg


sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64

Then re-configured xorg.


sudo dpkg-reconfigure xserver-xorg

And finished it all off with asudo reboot
```



And this is what glxinfo shows now.


```
glxinfoname of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_INTEL_swap_event, 
    GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string: 3.0 Mesa 9.2.0
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
    GL_3DFX_texture_compression_FXT1, GL_AMD_draw_buffers_blend, 
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_APPLE_object_purgeable, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_ES2_compatibility, 
    GL_ARB_ES3_compatibility, GL_ARB_blend_func_extended, 
    GL_ARB_color_buffer_float, GL_ARB_copy_buffer, GL_ARB_debug_output, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_objects, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_storage, GL_ARB_texture_storage_multisample, 
    GL_ARB_texture_swizzle, GL_ARB_timer_query, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_window_pos, 
    GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_envmap_bumpmap, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, GL_EXT_draw_buffers2, 
    GL_EXT_draw_instanced, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_multisample_blit_scaled, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod_bias, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_transform_feedback, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_texture_array, GL_MESA_texture_signed_rgba, 
    GL_MESA_window_pos, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_primitive_restart, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_OES_EGL_image, GL_OES_read_format, 
    GL_S3_s3tc, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays


20 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x020 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x021 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x08e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x090 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x091 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x092 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x094 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x097 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x098 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x099 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x09a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x05d 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None


44 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x060  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x064 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x065 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x066 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x067 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x068  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x069  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x06a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x06c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x06d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x06e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x06f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x070 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x071 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x072 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x073 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x074  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x075  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x076  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x077  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x078  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x07a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x080 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x081 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x082  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x083  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x084  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x085  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x087 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x089 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None

```

---

