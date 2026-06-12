---
title: "Firefox is causing my system to reboot!"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-08-10
Any idea why? Searches of Google and this forum have revealed nothing that I can see.

It's a fresh install of Hardy on an older machine (P3 1.0GHz, 256MB) and the Firefox is V.3. Firefox starts fine, but as soon as I try to navigate away from the start page, the machine instantly cuts to a reboot (no shutdown sequence or anything).

This post comes from within Opera, just in case anyone's wondering. :)

Any help is much appreciated! Thank you!

---

### Post by bpowell2005 on 2008-08-10
> **doctorbighands said:**
> Any idea why? Searches of Google and this forum have revealed nothing that I can see.

It's a fresh install of Hardy on an older machine (P3 1.0GHz, 256MB) and the Firefox is V.3. Firefox starts fine, but as soon as I try to navigate away from the start page, the machine instantly cuts to a reboot (no shutdown sequence or anything).

This post comes from within Opera, just in case anyone's wondering. :)

Any help is much appreciated! Thank you!

Okay, it seems like this is my answer to everything lately...but, have you checked to ensure you have enough free disk space? What does "df -h" look like? Is root or home partition completely full? When I filled up my root partition, Firefox would run for a bit, and then close itself out randomly...didn't cause a PC reboot, but was strange behavior.

---

### Post by doctorbighands on 2008-08-10
This machine is using 5GB of a 60GB disk.

---

### Post by bpowell2005 on 2008-08-10
If you run Firefox from the terminal, do you see any error messages?

Do you see anything in /var/log/dmesg or /var/log/messages just before the reboot?

---

### Post by doctorbighands on 2008-08-11
I don't see any funny stuff in those files. /messages reports the reboot after it's happened, but no unusual messages other than that. I'm stumped!

---

### Post by alienexplorers on 2008-08-11
What Add-ons are you running with Firefox.

---

### Post by doctorbighands on 2008-08-11
It's a freshly-installed system, and I haven't added any add-ons. Firefox reports the two installed add-ons as "Firefox (en-GB) 3.0.1" and "Xulrunner (en-GB) 1.9.0.1"

The odd thing is, nothing else on this system is installed using GB English. It's all en-US. I'm not sure why the add-ons are installed that way. A clue, perhaps?

---

### Post by Crafty Kisses on 2008-08-11
Not sure if your running on a desktop or a laptop, if it's just rebooting out of nowhere it could be a overheating issue, but try like Opera or something because Firefox does take a lot of resources.

Post the following output:
```
glxinfo
```

---

### Post by alienexplorers on 2008-08-11
Check this out:
[http://kb.mozillazine.org/Firefox_crashes]("http://kb.mozillazine.org/Firefox_crashes")

---

### Post by doctorbighands on 2008-08-11
> **Codename said:**
> Not sure if your running on a desktop or a laptop, if it's just rebooting out of nowhere it could be a overheating issue, but try like Opera or something because Firefox does take a lot of resources.

Post the following output:
```
glxinfo
```

It's a desktop - I probably should've mentioned that earlier! It can't be an overheat issue, because the random reboot is isolated only to instances of running Firefox. All of the messages I'm typing into the forum right now are done using Opera (which, I'm beginning to believe, is a far superior browser to Firefox for various reasons). I'm starting to lean toward just abandoning Firefox on this system and sticking with Opera. I hate to do that, though, because I'm the type who doesn't like to leave problems unsolved.

The output of "glxinfo," as requested:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x44 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by alienexplorers on 2008-08-11
If this is just a firefox problem you might want to ask your question on:
[http://forums.mozillazine.org/]("http://forums.mozillazine.org/")

---

