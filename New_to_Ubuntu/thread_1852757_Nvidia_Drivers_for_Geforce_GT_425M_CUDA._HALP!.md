---
title: "Nvidia Drivers for Geforce GT 425M CUDA. HALP!"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by osc1882 on 2011-09-30
So I bought a laptop at costco with a intell CPU and a ATI GPU and found out that I was all out of luck because Ubuntu doesn't support these two things together. Awesome. So I took it back and bought another laptop online with a Nvidia GPU because Nvidia has never let me down. I bought it with over night shipping because I'm flying out of state in two days (the reason I'm buying the laptop to start with.)

The laptop is a MSI FX603 and the GPU it's using is "Geforce GT425M CUDA". I picked this laptop because I've never had a Geforce not work with the nvidia drivers... untell today. Before I bought the laptop I did a search for the GPU and ubuntu and found this review [http://www.phoronix.com/scan.php?page=article&item=nvidia_gt425_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_gt425_winlin&num=1) So hell someone got it to work so I thought it it would be safe.

It will allow me to install the drivers, even the latest drivers from a PPA but when you go to proprietary drivers it says that the drivers are install but not in use. Also after you install the drivers and reboot it informs you that your hardware does not work with Unity so it bumps me back to classic gnome. 

I'm dying here guys. I have to get the all sorted out before monday in two days so if anyone can fix this I would love them forever and ever. It drives me insane that there seems to be no way of knowing ahead of time if a laptop will work with Ubuntu. I don't know if I can even take the laptop back (bought it on amazon) and even if I did I wouldn't know what in the world to buy to replace it and... I don't have the time for it I have to leave the state. Please help. 

Oh and so far the wifi is disabled even tho the laptop has wifi. But I was saving that for next.

---

### Post by osc1882 on 2011-09-30
Anyone?

---

### Post by jawilljr on 2011-09-30
This is how I install NVidia drivers:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo update
sudo apt-get install nvidia-current libvdpau1
```

Type those 3 commands in a terminal, and hopefully no errors then reboot.

Jerry

---

### Post by osc1882 on 2011-09-30
I tried those commands and it did not give me a error but it did not work ether. It still says under proprietary drivers that the drivers are install but not in use.

---

### Post by jawilljr on 2011-09-30
> **osc1882 said:**
> I tried those commands and it did not give me a error but it did not work ether. It still says under proprietary drivers that the **drivers are install but not in use**.

That is a bug.

Does unity work now?

Also what is the output of:

```
glxinfo
```

Jerry

---

### Post by osc1882 on 2011-09-30
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
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
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile GEM 20100330 DEVELOPMENT 
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_copy_buffer, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_seamless_cube_map, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_rg, GL_ARB_texture_swizzle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, GL_EXT_draw_buffers2, 
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
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_texture_swizzle, 
    GL_EXT_timer_query, GL_EXT_vertex_array_bgra, GL_EXT_vertex_array, 
    GL_OES_EGL_image, GL_OES_read_format, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_object_purgeable, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_envmap_bumpmap, 
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_texture_signed_rgba, GL_MESA_window_pos, 
    GL_MESA_ycbcr_texture, GL_NV_blend_square, GL_NV_depth_clamp, 
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_NV_vertex_program1_1, GL_NV_vertex_program, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x074 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x078  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slo

and no it doesn't. Sadly.

---

### Post by osc1882 on 2011-09-30
nvidia-settings when ran gives me a error message saying you seem to not be using the nvidia X driver and to run nvidia-xconfig to fix the problem but when i try to run that command it says there is no such command.

---

### Post by jawilljr on 2011-09-30
Is this an optimus machine?

Please post output of:

```
lspci | grep VGA
```

Jerry

---

### Post by osc1882 on 2011-09-30
Just googled it and yes it is a Optimus and here is the out put

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df0 (rev a1)

---

### Post by wildmanne39 on 2011-09-30
Hi, here is a link that may help, start with post 26.
[http://ubuntuforums.org/showthread.php?p=11277247#post11277247](http://ubuntuforums.org/showthread.php?p=11277247#post11277247)
That card is not support well in ubuntu yet.

If the link does not work, you can disable the nvidia card and use the built in intel.

Also if you installed more then one driver then you probably have at least 2 installed, you should open synaptic and type in nvidia and check.

The link is the only use I can be on that nvidia card, I swish I new more about it but I do not.
Thank you

---

### Post by osc1882 on 2011-09-30
How do I go about using only the intel?

---

### Post by wildmanne39 on 2011-09-30
Hi, you can just uninstall the drivers for the nvidia card, I think that will do it, but I do not know if you will be able to run unity with the intel, but you should be able to since it is a new computer.

However people have had issues with 3d with some intel cards so you will just have to try it and see.
Thank you

---

### Post by osc1882 on 2011-09-30
Oh and this page [http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660) has a update on the top of the page that says that these guys [https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable) have gotten it to work. 

I'm going to give it a go I think.

---

### Post by wildmanne39 on 2011-09-30
Hi, also further down the page in that first link it says that the intel card works fine on its own if you do not install any nvidia drivers, so it looks like you do have a fall back option.
Thank you

---

### Post by carrarin on 2011-09-30
try the bumblebee project... er, i should proabably have checked your link bfore i posted this... er goodluck!

---

### Post by Dougie187 on 2011-09-30
Have you tried installing the drivers from nvidia's packages? As opposed to pre-build .debs from ppa's or ubuntu's repository?

You can download them here
64bit - [http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html](http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html)
32bit - [http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html](http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html)

They are actually really easy to install (and un-install). Basically, just make sure that you don't have any nvidia drivers installed before you do this.

Go to your login screen. Press Ctrl+Alt+F1 and log in in the terminal. They type
```
sudo service gdm stop
```

Then move the package that you downloaded to /usr/share/nvidia-common and make sure it's executable with
```
sudo chmod a+x NVIDIA*.run
```

Then, just run it.
```
sudo ./NVIDIA*.run
```

Accept the license, and have it install the 32 bit opengl libraries, and [bold]DON'T HAVE IT WRITE A NEW xorg.cong[/bold].

After it finishes, all you have to do is type
```
sudo service gdm start && exit
```

It should bring you back to a login screen, and have the driver all set up for you. If you want to remove the driver, get back to the terminal again, and stop gdm like we did above, and they type

```
sudo nvidia-uninstall
```

Hopefully that helps.

(EDIT) - I don't know if this will help you or not. But, I figured it would be worth a shot, since nvidia supports this driver for this specific card. But I think the issue is with optimus rather than the card, at least from what the other links say.

---

