---
title: "Video problem... hardware or software?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Cysten on 2008-11-12
Hey I'm having problems watching DVDs on an old laptop I just bought and installed intrepid on.

Compaq Presario 1700
700 Mhz
256 MB Ram
Rage Mobility P/M AGP 2x

I have the ATI driver enabled in xorg.conf.
The problem is when I try to play a DVD on the system it is horrendously slow. Is this do to the fact that I have a crappy system or is this a software problem? If software problem how can I fix?

---

### Post by ajmorris on 2008-11-12
hi there,
what video player are you trying to use?
And can you please post the output of ```
sudo glxinfo
```
This command will tell us if your ati driver is activated.


AJ

---

### Post by Cysten on 2008-11-13
The player I am using is the default player totem in 8.10. Okay here it is.

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, 
    GL_ATI_separate_stencil, GL_IBM_multimode_draw_arrays, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_program_debug, 
    GL_MESA_resize_buffers, GL_MESA_texture_array, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_fragment_program, 
    GL_NV_light_max_exponent, GL_NV_point_sprite, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x22 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x3c 32 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None

32 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x3d  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x3e  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x3f  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x40  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x41  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x42  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x43  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x44  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x45  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x46  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x47  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x48  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x49  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x4a  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x4b  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x4c  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x4d  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x4e  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x4f  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x50  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x51  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x52  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x53  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x54  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x55  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x56  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x57  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x58  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x59  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x5a  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x5b  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x5c  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow

---

### Post by ajmorris on 2008-11-15
your ati drivers are not active. You are using mesa. can you post your /etc/X11/xorg.conf file please?
The easiest way for you to set the drivers though, is using sudo dpkg-reconfigure -phigh xserver-xorg

Changing to fglrx instead of mesa, may not fix your issue, but it is a good start, as in most case you will always want to use the accelerated glx drivers, instead of the generic.



AJ

---

### Post by Cysten on 2008-11-17
I executed that command you gave me, I am still having the same problem. Here is my Xorg.cong file:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

It seems to have reverted back to its original format since you had me execute that command.

---

### Post by nixscripter on 2008-11-18
Did you run it without gdm/kdm running? Try again, except this time log out, drop into the console (Cntl-Alt-F1), log in there, and ```
sudo /etc/init.d/gdm stop
```

Then try it.

---

### Post by halitech on 2008-11-18
> **Cysten said:**
> Hey I'm having problems watching DVDs on an old laptop I just bought and installed intrepid on.

Compaq Presario 1700
700 Mhz
[COLOR="Red"]256 MB Ram[/COLOR]
Rage Mobility P/M AGP 2x

I have the ATI driver enabled in xorg.conf.
The problem is when I try to play a DVD on the system it is horrendously slow. Is this do to the fact that I have a crappy system or is this a software problem? If software problem how can I fix?

I hope you went with Xubuntu instead of Ubuntu cause with only 256meg of ram (and I'm guessing probably 4 meg going to the video card) you are seriously under powered to run Ubuntu, let alone trying to play videos

---

### Post by Cysten on 2008-11-18
Still didn't work. I think at this point its just a hardware problem. I think Halitech is right.

---

