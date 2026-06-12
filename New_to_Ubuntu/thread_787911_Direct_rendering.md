---
title: "Direct rendering"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by dankster117 on 2008-05-09
I have a inspiron 1501 with an ATI mobility card I was wondering if anyone out there can assist me on getting direct rendering enabled so I can start to run some games when I type "glxinfo"I get

```
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by hermes0710 on 2008-05-09
I suppose you haven't installed the restricted drivers. Go to System>Administration>Hardware Drivers. There must be an entry for your ATI. Tick to enable it (internet connection is required) and after the installation completes reboot (you will be prompted to do so)


(If you are not on Hardy, then instead of Hardware Drivers you will find it in Restricted Drivers Manager)

---

### Post by dankster117 on 2008-05-09
system>administrator>hardware drivers> "ati restricted drivers in use"

---

### Post by hermes0710 on 2008-05-09
And enabled??? Is the checkbox ticked?

---

### Post by Catalyst2Death on 2008-05-09
two preliminary things:

I assume that you've already tried the restricted device manager, and it appears to be working, and secondly I assume that you are NOT using compiz.  **If compiz is enabled you will not have true direct rendering!!!!**

that being said.  I have always been able to get it to work using the gutsy install guide (on hardy as well)

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

for the record. The new xorg updates have changed how the xorg.conf file is structured.  However, the edits outlined in the install guide for the main driver install are still valid.  I have not tried any other edits, so I can't confirm them. USE AT YOUR OWN RISK.

and whenever possible, make sure to edit things manually... its more work but in the end you know what you changed so if something goes wrong you know where to go looking!

if at all possible try and get the driver in the ubuntu repositories working.  It will save you trouble in the long run, and there is nothing wrong with the restricted driver.  (In gutsy the restricted driver was quite outdated)

---

### Post by dankster117 on 2008-05-09
yes it is.

---

### Post by dankster117 on 2008-05-09
well i just recently removed compiz from my system to try to fix the problem i am using hardy heron

---

### Post by dankster117 on 2008-05-09
bump

---

### Post by Saint Angeles on 2008-05-09
try my super duper ATI tutorial...

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

---

### Post by dankster117 on 2008-05-09
```
 sudo sh ati[tab]
```
```
sh: Can't open ati[tab]
```

---

### Post by Catalyst2Death on 2008-05-09
[tab] means press tab on the keyboard... so type ati and the press tab...

---

### Post by dankster117 on 2008-05-09
I press tab... it uhh beeps

---

### Post by Catalyst2Death on 2008-05-09
that means you haven't downloaded/don't have the required file for that command


I would recommend using the unofficial install guide that I linked earlier.  The gutsy install is almost identical to the hardy install:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

personally, I'm more comfortable with the gutsy install method, and it works if your careful.  In either case the last section of the hardy install may apply to you...

---

