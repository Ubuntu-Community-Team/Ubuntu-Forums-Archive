---
title: "graphical display issue NVIDA - have tried guides and failed"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by blackbird3150 on 2008-07-13
So i recently bought a new computer. I bought ubuntu 64 bit on it
Intel core 2 e8500
4 gig ram
evga 9800gtx
p35 mobo
Ubuntu will not allow me to change the resolution of my monitor.
I downloaded the latest drivers from nvidia (Nvidia-linux-x86_64-173.14.09.pkg2)
I have done the guide located here:
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)
Also, when i boot it says low graphics mode, and even if i configure it, it does not stay any higher than 800x600, and on my 24" monitor thats enormous.
I have confirmed that i have x86_64 bit ubuntu installed.
Any thoughts? Anything information i can add?
As a side note, when i ran the nvidia driver setup, it forced me to compile the kernel. not sure if that is normal.
Thanks,
blackbird

---

### Post by PmDematagoda on 2008-07-13
Right after installing the Nvidia driver, are you able to start the X-Server properly with:-
```
sudo /etc/init.d/gdm start
```
?

---

### Post by drs305 on 2008-07-13
Others have had success with the 9800GTX.

Install EnvyNG:
```
sudo aptitude install envyng-gtk
```

Start it: System Tools, EnvyNG

Select Nvidia > Automatic > Apply. Note: the driver listed (173.14.05) appears to be older than the one you downloaded and installed but, as I mentioned, others have had success with it.

If that doesn't work, then try running it manually but with the same drivers ticked.

Reboot for the drivers to take effect.

---

### Post by blackbird3150 on 2008-07-13
After installing and i do what you recommended

> **PmDematagoda said:**
> Right after installing the Nvidia driver, are you able to start the X-Server properly with:-
```
sudo /etc/init.d/gdm start
```
?

I get the x-server to run... properly, in my definition no, because it seems like the nvidia drivers are being ignored. So yes the x-server does start, it starts in low graphics mode. and it runs in 800x600.
hopefully that answers your question.

---

### Post by blackbird3150 on 2008-07-13
> **drs305 said:**
> Others have had success with the 9800GTX.

Install EnvyNG:
```
sudo aptitude install envyng-gtk
```

Start it: System Tools, EnvyNG

Select Nvidia > Automatic > Apply. Note: the driver listed (173.14.05) appears to be older than the one you downloaded and installed but, as I mentioned, others have had success with it.

If that doesn't work, then try running it manually but with the same drivers ticked.

Reboot for the drivers to take effect.


I tried what you suggested... kind of. I ran envy and tried to install drivers -failed. then i was like well maybe i should uninstall what i have. i did that and it restarted
then this menu came up, something about graphical modes? 
0-6 with different codes and i was supposed to choose one of them (i can't remember what else they said or i would paste them)
i chose 0, and it displayed in 1920x1200 resolution. It also detects that i have the gateway '2000' 24" monitor
so the problem seems to be mostly solved.
Is that menu during boot something i should worry about?
thanks!

---

### Post by drs305 on 2008-07-13
> **blackbird3150 said:**
> 
Is that menu during boot something i should worry about?
thanks!

The menu option should be a one-time event.

Uninstalling the previous driver is something I would have expected Envy to do - I'll have to remember that...

If your issue is solved please mark it so via "Thread Tools" or continue asking questions if you are still not satisfied with your video.

---

### Post by blackbird3150 on 2008-07-13
> **drs305 said:**
> The menu option should be a one-time event.

Uninstalling the previous driver is something I would have expected Envy to do - I'll have to remember that...

If your issue is solved please mark it so via "Thread Tools" or continue asking questions if you are still not satisfied with your video.

Just to clarify, i uninstalled the driver through envy. I'll leave this up for an hour or so and then do the thread tools thing you requested, so to make sure there is no misunderstanding with what envy did.

Also, it seemed that, at least in my mind, there is no driver installed, because the last thing i did was uninstall, I never actually reinstalled. I'm satisfied with the video resolution at the moment, so unless someone thinks this is a problem or if there is something i should check i'm going to leave it as is and consider it solved.

EDIT: i restarted and it says "Undefined video mode number: 31f
Press <enter> to see video modes avialable or scan to scan.
After about 10 seconds it continued booting, and it seems to be fine

---

### Post by drs305 on 2008-07-13
Thanks for the clarification on the envy installation.

The "Undefined video mode number: 31f" may go away if you edit grub's menu.lst and change the vga setting to another value. One suggestion I've read about if you don't know the number is to set it to 'normal' so the line would look like:
```
# defoptions=splash quiet vga=normal
```. 

Since I don't know the values and cannot guarantee the above, I would try changing the vga option via StartUp-Manager. These settings only apply to the grub menu display:
```
sudo aptitude install startupmanager
```
System, Administration, StartUp-Manager > Boot Options and set a different resolution. That will automatically change the values to the above line in menu.lst.

If you would prefer to edit the line yourself, by playing with SUM these are the values I get:
8 bit:
640x480
800x600   # defoptions=splash quiet vga=771
1024x768  # defoptions=splash quiet vga=773
1280x1024 # defoptions=splash quiet vga=775
1600x1200 # defoptions=splash quiet vga=796

---

### Post by blackbird3150 on 2008-07-13
So something is still very wrong.
Every time i boot i still get that i mentioned earlier about the Undefined video mode number: 31f
Now my resolution is stuck at 1600x1200.
The reason i ran into the actual problem is because i tried installing the visual effects of compiz (i think its called) and so i installed the manager for that and restarted.
the machine booted to 800x600.
For some reason i am convinced that the nvidia drivers aren't actually installed because the last thing i did with envy was uninstall them.
how can i check if they are installed?

---

### Post by PmDematagoda on 2008-07-13
Post the output of:-
```
glxinfo
```
also before doing anything, did you install the Nvidia drivers through Hardware Drivers by any chance?

---

### Post by blackbird3150 on 2008-07-13
> **PmDematagoda said:**
> Post the output of:-
```
glxinfo
```
also before doing anything, did you install the Nvidia drivers through Hardware Drivers by any chance?

I don't know what you mean by hardware drivers, sorry i'm still kinda new to linux. the first thing i did after installing unbuntu was go to the nvidia site, download the latest driver NVIDIA-Linux-x86_64-173.14.09-pkg2.run and tried to install per instructions on the website. it didn't work, i got a 'no compiled kernel' error and it wasn't able to compile it. so i searched and updated the kernel, and ran it again. then the installation 'worked.' worked meaning that i was forced to use 'low graphics mode.' everything since then is posted above.
the output of glxinfo is:
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x52 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

EDIT: so when referring to what i was talking about before in the 31f problems at boot, it gives me a list of options, 0-6 with an associated colsxrows, which really don't mean a whole lot to me.
its always 80x(something) starting at around 25 and going to 60 maybe.

---

### Post by PmDematagoda on 2008-07-13
From the glxinfo output, you aren't using the Nvidia driver, about "updating" the kernel, could you please elaborate on that?

---

### Post by blackbird3150 on 2008-07-13
Well, if i remember correctly it said it needed to compile the kernel, and it asked if i wanted to get it from ftp nvidia (didn't work). So then i looked up the error and realized i was missing a library. so i 'installed' the library, and then it was able to compile the kernel.

---

### Post by PmDematagoda on 2008-07-13
Did you allow the Nvidia installer to configure the X-Server by any chance? If so, try doing:-
```
sudo modprobe nvidia
```
and post the results here.

---

### Post by blackbird3150 on 2008-07-13
So i tried installing the drivers again, just for kicks. and the same issue i was referring to occured:
no precompiled kerl was found... installer needs to compile one...
so i let it.

and when i go sudo modprobe nvidia
nothing appears

---

### Post by PmDematagoda on 2008-07-13
After doing the modprobe, did you try starting the X-Server? Also can you post the output of:-
```
cat /etc/X11/xorg.conf
```

---

### Post by blackbird3150 on 2008-07-13
I found the nvidia installer logs, they don't mean anything to me, but i thought i might post them in case they meant something to someone else.

In my latest attempt to install the drivers, it said 'completed' but would not allow me to go higher than 1600x1200 (my res is 1920x1200)

---

### Post by blackbird3150 on 2008-07-13
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Jun  5 00:08:24 PDT 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1920x1200"
    HorizSync       31.5 - 74.5
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BoardName      "vesa"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1600 1200
        Depth       24
        Modes      "800x600@60" "1024x768@60" "800x600@56" "1280x960@60" "640x480@60" "1280x1024@60" "1400x1050@60" "1600x1200@60"
    EndSubSection
EndSection

I see that 1920x1200 is not in the list.. should i try and add it? how would i do that?

---

### Post by blackbird3150 on 2008-07-13
Now when i do glxinfo i get this long list:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GTX/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 173.14.09
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_bindable_uniform, GL_EXT_depth_bounds_test, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXTX_framebuffer_mixed_formats, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color, 
    GL_NV_depth_buffer_float, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc, 
    GL_NV_texture_env_combine4, GL_NV_texture_expand_normal, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_NV_vertex_program2, GL_NV_vertex_program2_option, 
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap, 
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
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x31 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x32 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x33 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x42 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x49 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x4c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x4e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x4f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x54 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x56 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x57 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x60 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x61 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x63 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x64 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x65 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x66 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x67 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x68 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x69 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x6a 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x6b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x6c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x6d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x6e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x6f 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x70 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x71 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x72 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon

---

### Post by PmDematagoda on 2008-07-13
Do:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and see if that makes any improvement.

Edit:- From the new glxinfo, it seems that the Nvidia driver is now working, is it?

---

### Post by blackbird3150 on 2008-07-13
Yes the nvidia driver is working, i can go system tools > nvidia settings now as well
however, like i said the correct resolution is not being displayed as a viable option.
also, when i boot up,
that error mode still appears that i mention earlier
finally,
when i get to the ubuntu login screen, the screen is HUGE, however it only displays part of it at time, and it won't move the screen if i move my cursor to side, so its like i have to login without being able to see what i'm typing.

---

### Post by PmDematagoda on 2008-07-13
You should be able to specify a resolution with Nvidia-Settings:-
```
gksudo nvidia-settings
```
did you try that?

---

### Post by blackbird3150 on 2008-07-13
> **PmDematagoda said:**
> Do:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and see if that makes any improvement.

Edit:- From the new glxinfo, it seems that the Nvidia driver is now working, is it?

this brought me back to where i started from. i.e. 800x600 unchangeable resolution. glxinfo now displays the old configuration, meaning its not using the nvidia driver.

I reverted back to the old xorg file from nvidia, so at least its at 1600x1200 for the moment.

---

### Post by blackbird3150 on 2008-07-13
> **PmDematagoda said:**
> You should be able to specify a resolution with Nvidia-Settings:-
```
gksudo nvidia-settings
```
did you try that?

When i was referring to it wouldn't allow me to display in 1920x1200, it wasn't listed in the list. and when i tried to specify that resolution it threw and error.

---

