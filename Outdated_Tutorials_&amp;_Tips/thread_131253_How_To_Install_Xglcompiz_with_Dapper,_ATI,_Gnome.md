---
title: "How To: Install Xgl/compiz with Dapper, ATI, Gnome"
date: 2006-02-16
forum: Outdated Tutorials &amp; Tips
---

### Post by mattisking on 2006-02-16
HEY: Ignore this... it's too outdated and no longer really relevant. Besides, there are far newer packages than what's in Dapper right now and this thread won't get you there. THIS, however, worked perfectly for me: [http://www.compiz.net/viewtopic.php?id=389]("http://www.compiz.net/viewtopic.php?id=389")




Many people have contributed to this, some more than others as I've picked up the pieces I needed to make this work from through-out these forums. 
But, in particular: terrax, JoWilly, and poofyhairguy

1. Get your xorg.conf setup properly. The main thread has more than enough information on this. Follow it paying attention to the ATI differences that are well noted.

Just to be clear however, these instructions are targeted for those people using the ATI Proprietary Driver ("fglrx"). This is configured in your xorg.conf. If you're using "ati" that's not going to work for you. If you're using "radeon" then this is theoretically possible (radeon is the OSS driver targeted more - for now - for your lower end Radeon cards, in particular the 9000/9200/9250)... but I wasn't able to get it to work with my lower end PC that uses the 9200. In both cases, there are known/outstanding bugs with both sets of drivers that require work arounds described below. 

To make sure you are "accelerated", running with the new driver, try typing fglrxinfo in a terminal and see what you get. If it talks about ATI then awesome... if it talks about Mesa, you still don't have your driver setup properly (xorg.conf).

**For ATI do not enable composite in xorg.conf, xgl does not need it.

2. Install all the new stuff from the Dapper universe repository... this includes xserver-xgl, compiz, libgl1-mesa, libgl1-mesa-dri, libglitz1, libglitz-glx1 and any dependencies.

3. Modify /etc/gdm/gdm.conf-custom - For most this file is generally full of empty stubs.  Look for the one called [servers] and do this:

```
[servers] 
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

```

4. Modify /etc/gdm/gdm.conf to change your display:
```
#0=Standard
1=Standard

```

** You may have noticed in both steps 3 and 4 that we're using Display 1 instead of 0... this is due to a bug in the current proprietary ATI driver and this is the workaround.

5. Another bug in the driver... And for video, there is a bug with xv, so we want to start "gstreamer-properties" and tell it not to use xv for video. (This is the same as starting "Multimedia Systems Selector", a Preferences application that is currently hidden in your menu system)

6. Modify your session ("Menu System" -> "Preferences" -> "Sessions") by adding in the following two items:
```
gnome-window-decorator *(must be on top, start first) *
compiz --replace gconf
```

7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order:
```
gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```
It MUST be in this order as there are dependencies between them. If you've already been playing with this from earlier debs - maybe from battlehorse, or maybe you rolled your own - this is an important step because it's very likely in the wrong order. Most people that are missing certain plugins or are missing things like "alt-switch" will find they need to correct this and restart.

8. To get around the problem with <Shift> and <Backspace> enter this in your terminal whenever you login:
```
xmodmap /usr/share/xmodmap/xmodmap.<language>
```
where <language> refers to your country's code. For the US, it would be:
```
xmodmap /usr/share/xmodmap/xmodmap.us
```

Once everything is running along happily, this is a good appendix for the commands for using the nifty stuff compiz gives you:
[http://en.opensuse.org/Compiz]("http://en.opensuse.org/Compiz")

That's about as easy as I can make it. Good luck.

**Some Issues**
[LIST]
[*]This is a wonderful resource for looking into your video card/driver: [http://en.opensuse.org/Xgl]("http://en.opensuse.org/Xgl")
[*]It appears that you might need a 9800 or better ATI right now.
[*]It appears there may be problems with Mobility users (laptops)
[*]The latest compiz package may have a bug that doesn't put the necessary gconf settings in place. One possible work-around is to install the battlehorse v1 deb for compiz, then update to the universe deb.
[/LIST]

**UPDATES: **
I just got this tip for slightly lower end Radeon's like this user's 9600se:

1) sudo gedit /etc/gdm/gdm.conf
2) Go to line 198 and change:
GdmXserverTimeout=10 
to 
GdmXserverTimeout=50

---

### Post by poofyhairguy on 2006-02-16
Excellent. I will make one for Nvidia. Thanks!

---

### Post by Bou on 2006-02-16
[QUOTE=mattisking]To make sure you are "accelerated", running with the new driver, try typing fglrxinfo in a terminal and see what you get. If it talks about ATI then awesome... if it talks about Mesa, you still don't have your driver setup properly (xorg.conf).[/QUOTE]

OK, I did a fresh install just to follow this guide from the ground up so... I installed the fglrx driver and set it to xorg.conf

> Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

I installed the packages, too, though I can't find either libgl-mesa nor libgl-mesa-dri at the repos: I do find libgl1-mesa and libgl1-mesa-dri... are those the correct names?

I modified gdm.conf-custom too:

> [servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer 
flexible=true

And gdm.conf as well:

> [servers]
# These are the standard servers.  You can add as many you want here and they
# will always be started.  Each line must start with a unique number and that
# will be the display number of that server.  Usually just the 0 server is
# used.
#0=Standard
1=Standard

---

### Post by Bou on 2006-02-16
But then, when I try to reboot, I get the following messages:

[IMG]http://img119.imageshack.us/img119/7996/fallo24fu.jpg[/IMG]

[IMG]http://img119.imageshack.us/img119/6193/fallo36me.jpg[/IMG]

I didn't even add the dnome-window-manager and compiz stuff to the session startup. Why can this be caused?

---

### Post by vaskark on 2006-02-16
I have a Radeon 9200 SE 128Mb card with acceleration enabled. I followed your instructions up until Step 6. Xgl is running, I'm in gnome but it is sooo slow. I do step 6 and my screen goes black (although I can still see/move my mouse cursor). Also, both Xgl AND Xorg appear to be running. Is this normal? And is my card too low-end for this maybe? I'm on a P4 3GHz with 512 Mb RAM.

---

### Post by aamukahvi on 2006-02-16
You should change your name to mattisGOD, thank you (and the credited others). Got it finally working on my R9500 :KS 

My keyboard layout seems to have changed from FI to US. How can I switch back? :-k

---

### Post by MrRoboto on 2006-02-16
I can't get Xgl to work. I get the following error:

Couldn't open RGB_DB '/usr/share/X11/rgb'

any ideas?

---

### Post by golfie on 2006-02-16
Like all previous times I tried: Can someone give me the final answer how to handle this problem. I installed the latest fglrx driver from the ati site.

And with fglrxinfo I get:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc. 
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5642 (8.22.5)

So that's ok. But when I want to run compiz I always get this error message:

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

I also got them from the self-compiled version. But with the packages from the repos I still get this message. When I type glxinfo i get:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5642 (8.22.5)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None

And no GLX_EXT_texture_from_pixmap? I saw more people have this problem, but how can it be solved, since also many people have compiz working on their ati card. My card is actually a ATI Mobility Radeon 9700?

---

### Post by risbac on 2006-02-16
> Also, both Xgl AND Xorg appear to be running. Is this normal?

Yes it is, Xgl runs on top of Xorg. Nothing to worry about

---

### Post by risbac on 2006-02-16
To everybody and in order to answer faster to your problems, it would be useful to provide also:

1 your graphic card model and which driver are you using (really using, check with glxinfo which driver is loaded)
2 where did you install from ? (compile, internet deb, repo?)
3 how do you run Xgl ? (in a terminal, from modification in gdm?)
4 copy your Xgl launch command
5 copy your compiz launch command

Thanks in advance!

---

### Post by poyner on 2006-02-16
awesome! thanks so much for this. It's working a treat. 

I do have a couple of questions though. 
1. I don't seem to be able to set transperancy. when I right click on windows I don't get any opacity options. I read somewhere that you need to have transset installed but I already have this. Any other ideas of what could be wrong? 

2. in gconf editor I don't seem to have the menu plugin installing correctly. Could there be a reason for this? could it be related to my other problem above? 

3. What is the 'super' key to get zoom going? 

4. in the nvidia thread someone has posted about not needing to add the plugins to the startup line as they can get them from gconf. is this the same for ati cards? 

5. is there any way to slowly turn the cube and pause half way?

---

### Post by risbac on 2006-02-16
Answer to poyner:

1. yes you need to install transset, no it's not enough : ) Didn't find the solution for this for the moment in the forums, so it's a half answer only, sorry.

2. same, so no answer this time

3. the Windows key. They should have called it "evil key", everybody would have understood ... ;-)

4. Yes. If you define the plugins in your gconf, no need to specify them in the launch command. But it's not done by default, you need to edit your gconf!

5. Pause halfway ? To admire the landscape and take some pics ? ;-) You should be able to set this in the plugin menu from gconf that you don't have yet. So answer to 2 should answer to 5 maybe.

---

### Post by Bou on 2006-02-16
OK, There we go:

1 your graphic card model and which driver are you using (really using, check with glxinfo which driver is loaded)

-ATI Technologies Inc RV280 [Radeon 9200 PRO]

-I don't know what you exactly mean, so I'll post the whole glxinfo output.

> name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1041 (X4.3.0-8.21.7)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_ATI_element_array,
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None

2 where did you install from ? (compile, internet deb, repo?)

Repo. I installed the packages recommended on this thread, except for libgl-mesa and libgl-mesa-dri, which I didn't find. Instead, I installed libgl1-mesa and libgl1-mesa-dri. I don't know if that's what I should have done.

3 how do you run Xgl ? (in a terminal, from modification in gdm?)

Modification in gdm. Just like the guide specifies. Read my post above to see the modifications.

4 copy your Xgl launch command

There's no command.

5 copy your compiz launch command

I couldn't even try loading compiz, since Xgl won't load.

Thanks for any help.

---

### Post by risbac on 2006-02-16
Bou, this guide is for the fglrx driver of ATI cards. It says that the Radeon driver MIGHT work, but it's not sure at all. And you are using this radeon driver apparently:

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1041 (X4.3.0-8.21.7)
```

I'm quite sure that in your xorg.conf you have a "radeon" driver specified. 

So it would be better to first install the fglrx driver, then you can try again to run Xgl.

---

### Post by aamukahvi on 2006-02-16
Almost everything is working nice and dandy. Even my keyb is back to FI, somehow :) But I can't move my dialog windows without using the Alt key. All other windows move by just dragging the title bar. Move plugin is loaded.

So, how to move dialogs by their title bars?

---

### Post by .k2600. on 2006-02-16
[QUOTE=golfie]Like all previous times I tried: Can someone give me the final answer how to handle this problem. I installed the latest fglrx driver from the ati site.

And with fglrxinfo I get:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc. 
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5642 (8.22.5)

So that's ok. But when I want to run compiz I always get this error message:

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

I also got them from the self-compiled version. But with the packages from the repos I still get this message. When I type glxinfo i get:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5642 (8.22.5)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None

And no GLX_EXT_texture_from_pixmap? I saw more people have this problem, but how can it be solved, since also many people have compiz working on their ati card. My card is actually a ATI Mobility Radeon 9700?[/QUOTE]


Same here.. Installed fglrx (8.22.5) and everything from repos, tried gdm.config and gdm.config-custom altering, tried running with different combos of Xgl and compiz from terminal - always the same:

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

The card is Radeon 9800 pro... Xgl can start from terminal, but not from gdm, it just displays same error message like Bou posted earlier. Anyone?

---

### Post by risbac on 2006-02-16
> Xgl can start from terminal, but not from gdm, it just displays same error message like Bou posted earlier. Anyone?

Did you try both in display 0 and display 1?

Display 0 should be default in gdm.conf. Then in gdm.conf-custom, make sure you don't try to run Xgl on 1!

Also, please post the error message you have from Xgl. You need first to be able to start Xgl from gdm, then you can have a beer, relax an hour, and try compiz.

---

### Post by Bou on 2006-02-16
[QUOTE=risbac]Bou, this guide is for the fglrx driver of ATI cards. It says that the Radeon driver MIGHT work, but it's not sure at all. And you are using this radeon driver apparently:

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1041 (X4.3.0-8.21.7)
```

I'm quite sure that in your xorg.conf you have a "radeon" driver specified. 

So it would be better to first install the fglrx driver, then you can try again to run Xgl.[/QUOTE]

Not really, here's my corg.conf:

> Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

I have packages xorg-driver-fglrx version 6.9.0-8 and fglrx-kernel-source version 8.21.7 installed, too. If there's no other package I should install, I don't know what to say.

---

### Post by risbac on 2006-02-16
Ok Bou, so you are using fglrx apparently.
Can you post your gdm.conf-custom then?

---

### Post by Bou on 2006-02-16
Sure, I'll copy both .conf and -custom

> [servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer 
flexible=true

> [servers]
# These are the standard servers.  You can add as many you want here and they
# will always be started.  Each line must start with a unique number and that
# will be the display number of that server.  Usually just the 0 server is
# used.
#0=Standard
1=Standard

And, well, the error I get, again.

[IMG]http://img119.imageshack.us/img119/7996/fallo24fu.jpg[/IMG]

---

### Post by risbac on 2006-02-16
Bou, locate Xgl please, confirm us it's really in /usr/bin... It could be in /usr/local/bin.

---

### Post by aamukahvi on 2006-02-16
And Bou, the screencap on your post seems to indicate that you have the :1 there twice i.e. /usr/bin/Xgl :1 :1. Get rid of the other :1. Good luck! Xgl really rocks.

---

### Post by spotk on 2006-02-16
Hi all, 
since yesterday, i manage to get thouse famouses Xgl and compiz working on my setup but with no luck...

here is the setup: 
Ati X700 with fglrx module rebuilt from latest ati driver : 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5642 (8.22.5)


xgl-server , compiz and libs from repos. 

when i try to launch xgl , either with gdm stuff or with scripts, it fails loading... 
and each time xgl is loaded, fglrxinfo reports mesa drivers instead of Ati one...

here is my xorg Modules and device section: 

```

Section "Device"
    Identifier                          "ATIX700"
    Driver                              "fglrx"
    BusID "PCI:1:0:0"    # vendor=1002, device=5652
EndSection

Section "Module"
    #Load   "GLcore"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection



```


And here is the gdm stuff used to launch : 
 
/etc/gdm/gdm.conf is modified with 1=Standard
```


[servers]
# Override display 0 to use Xgl.
1=Xgl

[server-Xgl]
name=Xgl server
command=/usr/local/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true


```

If anybody can give me a reason why Mesa is used when Xgl launched ... 

Thanks in advance
Spotk

---

### Post by Bou on 2006-02-16
[QUOTE=risbac]Bou, locate Xgl please, confirm us it's really in /usr/bin... It could be in /usr/local/bin.[/QUOTE]

I'm so dumb. I was sure I had installed xserver-xgl, but I hadn't.

The thing is, now that the packaged is installed -I double-checked the other ones- Gnome seems to start, but the screen is all screwed up and I can only see lots of colors and the mouse cursor.

Is that supposed to happen? Do I have to add "gnome-window-decorator" and "compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher" for this not to happen, or have they nothing to do?

Thanks and sorry.

EDIT: aamukahvi, you can see my gdm.conf-custom above, there's no repeated :1 (I looked for it too)

---

### Post by aamukahvi on 2006-02-16
[QUOTE=Bou]I'm so dumb. I was sure I had installed xserver-xgl, but I hadn't.

The thing is, now that the packaged is installed -I double-checked the other ones- Gnome seems to start, but the screen is all screwed up and I can only see lots of colors and the mouse cursor.

Is that supposed to happen? Do I have to add "gnome-window-decorator" and "compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher" for this not to happen, or have they nothing to do?

Thanks and sorry.

EDIT: aamukahvi, you can see my gdm.conf-custom above, there's no repeated :1 (I looked for it too)[/QUOTE]
Ok, I noticed that, too, but figured that maybe you copied that from a FAQ or  something ;) As for the garbled up screen, that shouldn't happen. Once Xgl is installed and configured, everything should be pretty normal. Then starting gnome-window-decorator and compiz just add the icing on the cake, so to say :mrgreen:

---

### Post by risbac on 2006-02-16
> Is that supposed to happen?

I don't think so... You can run Xgl without running Compiz. I think it's better to go step by step, run Xgl first, then run Compiz. Apparently your Xgl is not running so fine... Do you have a specific configuration? Like dual monitor?

---

### Post by Bou on 2006-02-16
[QUOTE=risbac]I don't think so... You can run Xgl without running Compiz. I think it's better to go step by step, run Xgl first, then run Compiz. Apparently your Xgl is not running so fine... Do you have a specific configuration? Like dual monitor?[/QUOTE]

Nope. Fresh install, nothing special. No dual monitors, no nothing.

---

### Post by zasf on 2006-02-16
I personally discourage running Xgl as primary xserver, since not stable at all. Morevore it's good to test it "the consolle way", see my howto [http://battlehorse.homelinux.net/w/Wiki.jsp?page=HowToXglATI](http://battlehorse.homelinux.net/w/Wiki.jsp?page=HowToXglATI).

---

### Post by MrRoboto on 2006-02-16
here we are!

I got Xgl running after installing the latest ATI drivers.

Xgl starts fine, the problem is compiz:

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

I own a 9200 Pro

solutions?

---

### Post by DeeZiD on 2006-02-16
@Mr. Roboto

You could try to recompile glitz from cvs.
The newest update contains some fixes for this bug ;)


regards Dennis

---

### Post by risbac on 2006-02-16
> solutions?

Did you insist? And sudo it? Personnaly, I need a few attempts to be able to run Compiz on my i850 card... And I think I need a sudo.

---

### Post by gravious on 2006-02-16
I have followed this tutorial and compiz segfaults with with message
 compiz.real[5648]: segfault at 0000000000000000 rip 00002aaaab7c47b3 rsp 00007fffff9f1358 error 4

I also have strange artefacts being drawn with Xgl loaded.

---

### Post by MrRoboto on 2006-02-16
thanx for the info.
which is the right --prefix?

---

### Post by risbac on 2006-02-16
Try ```
sudo compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher --replace
```

Then run gnome-window-decorator

---

### Post by aamukahvi on 2006-02-16
[QUOTE=risbac]Try ```
sudo compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher --replace
```[/QUOTE]
Why sudo?

---

### Post by risbac on 2006-02-16
>Why sudo?

I wish I knew : ) It just didn't work when I tried without... But maybe I didn't try enough?

---

### Post by MrRoboto on 2006-02-16
[QUOTE=risbac]Try ```
sudo compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher --replace
```

Then run gnome-window-decorator[/QUOTE]

with sudo nothing change

---

### Post by Denton on 2006-02-16
Hi, I have ATI X200 IGP, xgl/compiz/glitz from repos, fglrx driver and I changed the symling /etc/X11/X to point to /usr/bin/Xgl.
Everything is running fine, but when I try to start totem or open any directory with nautilus, system will freeze. It happened also when I started Xgl with modified /etc/gdm/gdm.conf-custom without changed /etc/X11/X symlink.
Is it possible to fix the freeze problem?

---

### Post by didit on 2006-02-16
[QUOTE=Bou]I'm so dumb. I was sure I had installed xserver-xgl, but I hadn't.

The thing is, now that the packaged is installed -I double-checked the other ones- Gnome seems to start, but the screen is all screwed up and I can only see lots of colors and the mouse cursor.

Is that supposed to happen? Do I have to add "gnome-window-decorator" and "compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher" for this not to happen, or have they nothing to do?

Thanks and sorry.

EDIT: aamukahvi, you can see my gdm.conf-custom above, there's no repeated :1 (I looked for it too)[/QUOTE]

I think your problem is exactly the same with mine. I have ATI M9000 in my laptop. I install Xgl etc from the repro. I even fresh install my Ubuntu from the begining beforehand. What I get is a distorted screen. After digging Google to find some clues, I get some from [http://gentoo-wiki.com/HOWTO_XGL](http://gentoo-wiki.com/HOWTO_XGL) and It is pretty sad that a solution is unkown :(

---

### Post by .k2600. on 2006-02-16
[QUOTE=risbac]Did you try both in display 0 and display 1?

Display 0 should be default in gdm.conf. Then in gdm.conf-custom, make sure you don't try to run Xgl on 1!

Also, please post the error message you have from Xgl. You need first to be able to start Xgl from gdm, then you can have a beer, relax an hour, and try compiz.[/QUOTE]

Sure, i tried both, error message from Xgl is exactly the same one as seen on photos earlier in post. Except when i start it with "0" from gdm all i get is gray screen with hourglass and nothing happens after that .... If i start it from terminal - compiz says it missing GLX_EXT... and no managable screens found.

---

### Post by Bou on 2006-02-16
[QUOTE=didit]I think your problem is exactly the same with mine. I have ATI M9000 in my laptop. I install Xgl etc from the repro. I even fresh install my Ubuntu from the begining beforehand. What I get is a distorted screen. After digging Google to find some clues, I get some from [http://gentoo-wiki.com/HOWTO_XGL](http://gentoo-wiki.com/HOWTO_XGL) and It is pretty sad that a solution is unkown :([/QUOTE]

It's weird, because I get it WITHOUT using compiz.

---

### Post by aamukahvi on 2006-02-16
[QUOTE=risbac]>Why sudo?
I wish I knew : ) It just didn't work when I tried without... But maybe I didn't try enough?[/QUOTE]
Hehe, mysterious. Maybe it's got something to do with the phase of the moon? :p

---

### Post by MrRoboto on 2006-02-16
i've instaled the new glitz from cvs but no luck

---

### Post by MadMan2k on 2006-02-16
its not glitz its compiz and the compiz from the repositories already contains a fix for that..

---

### Post by MrRoboto on 2006-02-16
[QUOTE=MadMan2k]its not glitz its compiz and the compiz from the repositories already contains a fix for that..[/QUOTE]


whatever... compiled and installed... no luck

---

### Post by qrlgftrt on 2006-02-16
[QUOTE=Denton]Hi, I have ATI X200 IGP, xgl/compiz/glitz from repos, fglrx driver and I changed the symling /etc/X11/X to point to /usr/bin/Xgl.
Everything is running fine, but when I try to start totem or open any directory with nautilus, system will freeze. It happened also when I started Xgl with modified /etc/gdm/gdm.conf-custom without changed /etc/X11/X symlink.
Is it possible to fix the freeze problem?[/QUOTE]

wait for new ati drivers that support xgl and for xgl itself to be more stable...
which knowledgeable people on the forums expect to happen in 3-12 months...
same problems here, it crashes also on resize (ati mobility x600)

---

### Post by kro on 2006-02-16
[QUOTE=didit]I think your problem is exactly the same with mine. I have ATI M9000 in my laptop. I install Xgl etc from the repro. I even fresh install my Ubuntu from the begining beforehand. What I get is a distorted screen. After digging Google to find some clues, I get some from [http://gentoo-wiki.com/HOWTO_XGL](http://gentoo-wiki.com/HOWTO_XGL) and It is pretty sad that a solution is unkown :([/QUOTE]

damned ... i've got the same problem with my T40p (ATI Fire GL inside)
I wish the next version of ocmpiz will solve the bug ...

---

### Post by aamukahvi on 2006-02-16
[QUOTE=qrlgftrt]wait for new ati drivers that support xgl and for xgl itself to be more stable...
which knowledgeable people on the forums expect to happen in 3-12 months...
same problems here, it crashes also on resize (ati mobility x600)[/QUOTE]
Weird. Maybe the drivers are more stable for the R9500? Mine hasn't crashed once. Not resizing, not nautilus, not totem, not anything. Just one unfortunate Shift + Backspace :p

I have everything from the repos, including the drivers. i386/k7.

---

### Post by mattisking on 2006-02-16
[QUOTE=vaskark]I have a Radeon 9200 SE 128Mb card with acceleration enabled. I followed your instructions up until Step 6. Xgl is running, I'm in gnome but it is sooo slow. I do step 6 and my screen goes black (although I can still see/move my mouse cursor). Also, both Xgl AND Xorg appear to be running. Is this normal? And is my card too low-end for this maybe? I'm on a P4 3GHz with 512 Mb RAM.[/QUOTE]

I'm still trying to work out the 9200. My secondary PC is a very moderate P4 1.2 Celeron with a Radeon 9200 128 MB. I don't know what kind of overhead Xgl adds to my processor... but my understanding is that Xgl is supposed to "move" the rendering to my video card's 3D hardware so if my Dapper runs great without Xgl (which it does) then theoretically, as long as the video card is up to it, then it should run fine-ish, even on my lower end machine. (It rocks on my high end machine). Unlike you I have so far NOT been able to get my lower end machine with the 9200 to use the fglrx driver for some reason. It just won't... not accelerated anyway. Our 9200 is not meant for use by the fglrx driver... we're supposed to use the "radeon" driver which SPECIFICALLY supports the 9200/9250 (and I think the 9000) for acceleration. There are some pending bugs on the todo list and I honestly think once they are solved, we might get this working properly.

So, I think, though I will continue to try, that you may be out of luck for now with the 9200.

---

### Post by mattisking on 2006-02-16
[QUOTE=spotk]
[server-Xgl]
name=Xgl server
command=**/usr/local/bin/Xgl** :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
[/code]
[/QUOTE]

should be:
```
command=**/usr/bin/Xgl** :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer

```

---

### Post by mattisking on 2006-02-16
[QUOTE=Denton]Hi, I have ATI X200 IGP, xgl/compiz/glitz from repos, fglrx driver and I changed the symling /etc/X11/X to point to /usr/bin/Xgl.
Everything is running fine, but when I try to start totem or open any directory with nautilus, system will freeze. It happened also when I started Xgl with modified /etc/gdm/gdm.conf-custom without changed /etc/X11/X symlink.
Is it possible to fix the freeze problem?[/QUOTE]

Did you try the suggested change in Multimedia Systems Selector for video? Maybe that is related? It's in the "How To"

---

### Post by mattisking on 2006-02-16
[QUOTE=MrRoboto]here we are!

I got Xgl running after installing the latest ATI drivers.

Xgl starts fine, the problem is compiz:

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

I own a 9200 Pro

solutions?[/QUOTE]

That error, I believe is related to missing patches from MESA. You have some options I think.

First, either use battlehorse debs (they work well) or the universe debs. Don't mix and match. If you tried previously with the battlehorse debs, and want to switch to the universe released ones, make sure you remove (completely - with synaptic or --purge with apt-get) the "mesa" deb (that's exactly how it would show up) and the "xserver" deb... again, don't mess with the xserver-whatever packages but if you installed from battlehorse there will be a plain "xserver" package that needs to be removed to install xserver-xgl from universe.

Another option... switch TO battlehorse debs. Remove universe debs, in particular, xserver-xgl and compiz (the others can stay I think) and install the compiz, mesa, and xserver battlehorse debs. His How-To can help you fix the script changes to get the paths right.

---

### Post by unf on 2006-02-16
unf@~$ compiz.real: Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

Running ATI 9600
direct rendering : yes 

Lagging like hell :)

---

### Post by .k2600. on 2006-02-16
[QUOTE=unf]unf@~$ compiz.real: Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

Running ATI 9600
direct rendering : yes 

Lagging like hell :)[/QUOTE]

I got that one - while trying to use mesa libs from battlehorse with everything else from repos ...

---

### Post by zachtib on 2006-02-16
ok, im trying again from a fresh install.

should I use the repo fglrx drivers, or the 8.22.5 from ati.com?

and should I use the repo debs or the battlehorse debs?

I know both can work, someone just give me a recommendation

---

### Post by mcduck on 2006-02-16
Thanks for this great how-to. I got Compiz running on a fresh Breezy in 20 minutes :D

I have Radeon 9600 XT, and I installed everything from the repositories. Everything seems fairly stable (about Windows-like stable ;)).

Only thing not working is adjusting window transparency. [This]("http://en.opensuse.org/Compiz") guide tells to right-click windows's titlebar and select 'Opacity', only I don't have such option. But everyhing looks so sweet anyway so that's not a serious problem.

---

### Post by aamukahvi on 2006-02-16
[QUOTE=zachtib]ok, im trying again from a fresh install.

should I use the repo fglrx drivers, or the 8.22.5 from ati.com?

and should I use the repo debs or the battlehorse debs?

I know both can work, someone just give me a recommendation[/QUOTE]
I have R9500 and everything from repo. WORKS. Videos are a bit laggy (totem-xine). No crashes.

---

### Post by firetux on 2006-02-16
> It appears there may be problems with Mobility users (laptops)

What kind of problems? I have an acer 5024WLMi (x700 mobility):(

---

### Post by aamukahvi on 2006-02-16
[QUOTE=mcduck]Only thing not working is adjusting window transparency. [This]("http://en.opensuse.org/Compiz") guide tells to right-click windows's titlebar and select 'Opacity', only I don't have such option.[/QUOTE]
Same here.

---

### Post by mattisking on 2006-02-16
Yeah, I don't have the Opacity either. I'll look into that this evening.

---

### Post by mattisking on 2006-02-16
[QUOTE=firetux]What kind of problems? I have an acer 5024WLMi (x700 mobility):([/QUOTE]

Have you tried it? It doesn't hurt to try and just undo the changes if it doesn't work by undoing the gdm.conf and gdm.conf-custom changes. I only listed this because I have heard from more than one user of problems getting this to work on their X700 or higher mobility. That doesn't mean it won't work for you.

---

### Post by risbac on 2006-02-16
ATI AIW9600 Pro / PIV 2.8Ghz / 1Go
Dapper, Xgl from repo, fglrx driver
Xgl is running with a modified gdm.conf & -custom
I would have said quite stable, but my post was just deleted with a crash : )

To start Compiz, I had to remove "gconf" from the command line. 

> compiz decoration move resize place switcher wobbly fade minimize cube rotate zoom scale --replace

If I add gconf anywhere in the command, it's failing. I don't know why. All the other plugins are working fine, be careful with the order, you can't change it the way you want, there are some dependencies (some plugins must be loaded before others).

No need of any sudo, you can forget about my previous advise.

So far, it's very smooth, I will talk about the stability after some tests.

---

### Post by mattisking on 2006-02-16
[QUOTE=risbac]
To start Compiz, I had to remove "gconf" from the command line. 
[/QUOTE]

Could you check something for me? Use the gconf editor and go to apps. Is there an entry for compiz? There have been reports (I have also seen this on my lower end PC) that sometimes compiz is missing from gconf which would indicate a possible bug in the compiz package. Theoretically, if it IS missing for you, then using the gconf option WOULD fail.

If it IS missing and you have a moment, try uninstalling compiz (completely), install the battlehorse deb (the first one) and see if compiz is now listed under apps with the gconf editor. If it IS, then make the changes from the How-To (putting in the correct order), Upgrade your compiz to the package in universe, add gconf back into your compiz startup command and reboot to see if it starts working with gconf included.

---

### Post by risbac on 2006-02-16
No prob. Yes I have a compiz entry in gconf, but nothing about "plugins" anywhere. I wanted to play with the settings, but except "general", nothing else... 

I have the latest compiz from the repo I think (0.0.2-4).

---

### Post by Goon on 2006-02-16
I've followed the tutorial and it (almost) works. Xgl starts, I've got my desktops on a cube but I can't launch any application through the menu. Any idea?

I've used battlehorse packages, maybe I forgot to clean something?

---

### Post by risbac on 2006-02-16
I can't remember who asked, but to move the dialog windows, you can't grab the title bar and move them. The other solution for the moment is to hold the ALT key and move the window by clicking anywhere on it, just like the usual way.

---

### Post by mattisking on 2006-02-16
[QUOTE=Goon]I've used battlehorse packages, maybe I forgot to clean something?[/QUOTE]

It's possible. I can drag windows without any trouble. However, the battlehorse debs, in general, install under opt and usr/local/bin so as long as none of your config stuff points to the wrong place you should be ok. There may be left over garbage in gconf maybe?

---

### Post by mattisking on 2006-02-16
[QUOTE=risbac]No prob. Yes I have a compiz entry in gconf, but nothing about "plugins" anywhere. I wanted to play with the settings, but except "general", nothing else... 
I have the latest compiz from the repo I think (0.0.2-4).[/QUOTE]

If you don't mind trying it out, could you do as I suggested anyway then? I'm curious about trying to get the proper gconf settings in there. On my primary PC I started with battlehorse debs and then switched to Universe as packages became available and I had no trouble... but on my lower end PC I went straight from the repositories and there are no compiz options listed at all under gconf. I will test this myself later on today after work when I'm home but that will be quite a while.

---

### Post by firetux on 2006-02-16
[QUOTE=mattisking]Have you tried it? It doesn't hurt to try and just undo the changes if it doesn't work by undoing the gdm.conf and gdm.conf-custom changes. I only listed this because I have heard from more than one user of problems getting this to work on their X700 or higher mobility. That doesn't mean it won't work for you.[/QUOTE]


I didn't try it yet. 
Its good to know that I can simply undo the changes, probably I'll try it tomorrow, I have plenty of time tomorrow to troubleshoot.:) 

btw: thanks a lot for the guide, its exactly what I've been waiting for to try XGL.

---

### Post by zachtib on 2006-02-16
[QUOTE=didit]I think your problem is exactly the same with mine. I have ATI M9000 in my laptop. I install Xgl etc from the repro. I even fresh install my Ubuntu from the begining beforehand. What I get is a distorted screen. After digging Google to find some clues, I get some from [http://gentoo-wiki.com/HOWTO_XGL](http://gentoo-wiki.com/HOWTO_XGL) and It is pretty sad that a solution is unkown :([/QUOTE]

same problem, same card.  which fglrxdrivers are you running, and from where?
also, if i try starting compiz without as many plugins, it does start, but the whole screen is black.  however, I can tell that some things are working

---

### Post by mattisking on 2006-02-16
[QUOTE=zachtib]same problem, same card.  which fglrxdrivers are you running, and from where?
also, if i try starting compiz without as many plugins, it does start, but the whole screen is black.  however, I can tell that some things are working[/QUOTE]

Try just using one or two ... leave out gconf. Maybe just wobbly... though I think wobbly requires something now that it didn't use to.

---

### Post by fluxin on 2006-02-16
Can anyone else confirm that the application open animation runs very poorly under Xgl, I've disabled all of the animations under gconf, but I can't stop the wastebasket animation. Anyone else have this problem?

---

### Post by aamukahvi on 2006-02-16
[QUOTE=fluxin]Can anyone else confirm that the application open animation runs very poorly under Xgl, I've disabled all of the animations under gconf, but I can't stop the wastebasket animation. Anyone else have this problem?[/QUOTE]
Yes, exactly the same one... And no, can't stop the wastebasket animation.

---

### Post by zachtib on 2006-02-16
[QUOTE=mattisking]Try just using one or two ... leave out gconf. Maybe just wobbly... though I think wobbly requires something now that it didn't use to.[/QUOTE]

now compiz is thowing the non power of two textures errors again...
ill try some more later, but i have a paper due in less than 24 hours, and I kinda haven't started yet

---

### Post by .k2600. on 2006-02-16
Well, I got xgl to boot with gdm, but compiz still gives: 

GLX_EXT_texture_from_pixmap is missing
Failed to manage screen: 0
No managable screens found on display :1.0

So as an experiment i tried glxcompmgr, found a deb for ubuntu somewhere, and
guess what? Same thing:

Couldn't allocate color
Failed to manage screen: 0
No managable screens found on display:1.0

(everything from repos, fglrx 8.22.5, r9800pro ....)
Any ideas?

---

### Post by mattisking on 2006-02-16
Sorry k2600... all I can say is that the problem you are having is VERY common and listed all over google. Anything I've read so far seems to indicate some enum differences between Xgl and mesa. Since I'm using only Universe packages and it works fine I can only think of a couple of scenarios:
1) You have left over pieces on your system from attempts to build and install it yourself in which case a clean install might be something to consider.
2) Somehow universe and battlehorse debs are interfering with one another. If you're using universe debs and at one time used the battlehorse debs, go into synaptic and COMPLETELY remove the battlehorse ones... and vice versa if you're using the battlehorse debs instead of the universe ones.
3) There may be (and likely are) still bugs in the packaging that aren't quite worked out yet and only manifest in certain configurations and situations. A clean install from the beginning is your best bet..

Ultimately this is incredibly cool but still riddled with bugs and work-arounds and no matter how awesome it will be in the future, right now it's really just a novelty until it's had much more time to mature... so reinstalling just for this is only something to consider if you really have the time (and the data backups) to make it worthwhile.

---

### Post by born_confused on 2006-02-16
Ok, not working here either

fglrx 8.22.5

Without the xgl server fglrx loads fine, with it I see this in a printout of dmesg

```
[4314113.570000] [fglrx:firegl_umm_init] *ERROR* UMM area already initialized!
[4314113.570000] [fglrx:firegl_unlock] *ERROR* Process 10875 using kernel context 0
[4314168.547000] [fglrx:firegl_lock_free] *ERROR* lock was not held by 1! (*lock=0x00000000)
[4314168.547000] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!
[4314170.826000] [fglrx:firegl_umm_init] *ERROR* UMM area already initialized!
[4314170.826000] [fglrx:firegl_unlock] *ERROR* Process 10903 using kernel context 0

```

My gdm.conf-custom looks like this

```

[servers]
1=Xgl

[server-Xgl]
name = Xgl server
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible = true

```

finally, the gdm.conf bit looks like this
```

[servers]
# These are the standard servers.  You can add as many you want here and they
# will always be started.  Each line must start with a unique number and that
# will be the display number of that server.  Usually just the 0 server is
# used.
#0=Standard
1=Standard

```

Slightly below that I see

```

[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0
flexible=true
# Indicates that the X server should be started at a different process
# priority.  Values can be any integer value accepted by the setpriority C
# library function (normally between -20 and 20) with 0 being the default. For
# highly interactive applications, -5 yields good responsiveness. The default
# value is 0 and the setpriority function is not called if the value is 0.

```

ps ax shows this ...

```

10902 ?        S      0:03 /usr/bin/Xgl :1 :1 -fullscreen ...i took out the rest

```

---

### Post by fluxin on 2006-02-16
Can you check to see if you have a .Xsession anywhere on your computer?

```

sudo updatedb
locate .Xsession

```

I'm using locate because I'm unsure of permissions. If you find any rename it .Xsessionbak or something along those lines, then try it.

[QUOTE=born_confused]Ok, not working here either

fglrx 8.22.5

Without the xgl server fglrx loads fine, with it I see this in a printout of dmesg

```
[4314113.570000] [fglrx:firegl_umm_init] *ERROR* UMM area already initialized!
[4314113.570000] [fglrx:firegl_unlock] *ERROR* Process 10875 using kernel context 0
[4314168.547000] [fglrx:firegl_lock_free] *ERROR* lock was not held by 1! (*lock=0x00000000)
[4314168.547000] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!
[4314170.826000] [fglrx:firegl_umm_init] *ERROR* UMM area already initialized!
[4314170.826000] [fglrx:firegl_unlock] *ERROR* Process 10903 using kernel context 0

```

My gdm.conf-custom looks like this

```

[servers]
1=Xgl

[server-Xgl]
name = Xgl server
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible = true

```

finally, the gdm.conf bit looks like this
```

[servers]
# These are the standard servers.  You can add as many you want here and they
# will always be started.  Each line must start with a unique number and that
# will be the display number of that server.  Usually just the 0 server is
# used.
#0=Standard
1=Standard

```

Slightly below that I see

```

[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0
flexible=true
# Indicates that the X server should be started at a different process
# priority.  Values can be any integer value accepted by the setpriority C
# library function (normally between -20 and 20) with 0 being the default. For
# highly interactive applications, -5 yields good responsiveness. The default
# value is 0 and the setpriority function is not called if the value is 0.

```

ps ax shows this ...

```

10902 ?        S      0:03 /usr/bin/Xgl :1 :1 -fullscreen ...i took out the rest

```[/QUOTE]

---

### Post by born_confused on 2006-02-16
just checked, no nothing, I did a restart and that error message seems to have gone. However, fglrxinfo says "Error: unable to open display:0".

---

### Post by zachtib on 2006-02-16
you have to 
```
fglrxinfo -display :1
```

---

### Post by born_confused on 2006-02-16
I see, well it says
```


fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

now the question is, without xgl fine, with xgl no

and this 

/usr/bin/Xgl :1 :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer -auth /var/lib/gdm/:1.Xauth -nolisten tcp vt

repeated :1

---

### Post by fluxin on 2006-02-16
In regards to the wastebasket opening, I removed the applet from the bottom bar, and enabled the desktop icon

```

gconf-editor
/apps/nautilus/desktop/trash_icon_visible

```

Double clicking the desktop icon does not cause the animation to happen, this is such a minor thing, but with everything moving so smoothly it's sad to see that poor animation happening

---

### Post by mattisking on 2006-02-16
**born_confused**

The stuff you see further down is overridden by the settings in gdm.conf-custom.

At any rate, let's see your xorg.conf and what video card do you have?

---

### Post by born_confused on 2006-02-16
[QUOTE=mattisking]**born_confused**

The stuff you see further down is overridden by the settings in gdm.conf-custom.

At any rate, let's see your xorg.conf and what video card do you have?[/QUOTE]

I have a radeon 9600 256mb

and heres my xorg.conf file

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "gb"
        Option      "XkbVariant" "uk"
        Option      "XkbOptions" "qwerty"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "17'' LCD"
        HorizSync    28.0 - 50.0
        VertRefresh  43.0 - 75.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
        Monitor    "17'' LCD"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection



```

---

### Post by fluxin on 2006-02-16
can you do a 
```

grep 'Xgl :1' * -R'

```
in /etc/gdm and in your home directory

---

### Post by .k2600. on 2006-02-16
[QUOTE=mattisking]Sorry k2600... all I can say is that the problem you are having is VERY common and listed all over google. Anything I've read so far seems to indicate some enum differences between Xgl and mesa. Since I'm using only Universe packages and it works fine I can only think of a couple of scenarios:
1) You have left over pieces on your system from attempts to build and install it yourself in which case a clean install might be something to consider.
2) Somehow universe and battlehorse debs are interfering with one another. If you're using universe debs and at one time used the battlehorse debs, go into synaptic and COMPLETELY remove the battlehorse ones... and vice versa if you're using the battlehorse debs instead of the universe ones.
3) There may be (and likely are) still bugs in the packaging that aren't quite worked out yet and only manifest in certain configurations and situations. A clean install from the beginning is your best bet..

1 and 2 are not an option since i didn't install anything else than debs from repos, and upgraded them. Reinstalled them too, nothing helps. But thanks for your trouble. 

P.S.
One more thing - aticonfig didn't do much to my xorg.conf beside
messing with refresh rates so I manually added stuff concerning DDX part, and there was a screen:0 or 1 line in there... Anyone?

---

### Post by born_confused on 2006-02-16
sure

results from home 

```

grep 'Xgl :1' * -R

```

results from /etc/gdm
```

 grep 'Xgl :1' * -R
gdm.conf-custom:command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer


```

---

### Post by loulou on 2006-02-16
sorry for my English .....


I use compiz + Xgl on thinkpad T42p (Ati Fire GL T2)

with the fglrx from repository (6.xxx) no pb to use compiz
but with the driver 8.22.5 it's not possible.
I obtain "non power of two textures errors"

Someone try to use a glistz with fglrx patch, maybe this can accelerate XV for movie ???

---

### Post by mattisking on 2006-02-16
**born_confused**

You may have set yourself up with the fglrx driver but it's not using it for accelerated desktop. It might be that the fglrx driver isn't compatible with your card which means you would theoretically need to use the radeon driver (open source driver) instead. Unfortunately I have been unable to make it work with the radeon driver. The clue is in the response to fglrxinfo you reported:
```
fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

If you look at the how-to you should see that if acceleration is working properly you should get a message in the vendor string about ATI, not Mesa. That's why it's not working for you. I will be looking into this more in depth this evening as my seconday PC has a 9200. I plan to trying to get it running with fglrx (couldn't before) and also with the "radeon" driver again.

---

### Post by born_confused on 2006-02-16
[QUOTE=mattisking]**born_confused**

You may have set yourself up with the fglrx driver but it's not using it for accelerated desktop. It might be that the fglrx driver isn't compatible with your card which means you would theoretically need to use the radeon driver (open source driver) instead. Unfortunately I have been unable to make it work with the radeon driver. The clue is in the response to fglrxinfo you reported:
```
fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

If you look at the how-to you should see that if acceleration is working properly you should get a message in the vendor string about ATI, not Mesa. That's why it's not working for you. I will be looking into this more in depth this evening as my seconday PC has a 9200. I plan to trying to get it running with fglrx (couldn't before) and also with the "radeon" driver again.[/QUOTE]

matt, I dont know, if I startx without xgl, everything works fine, it shows fglrx on fglrxinfo, 3d works great, and Ive always used fglrx and play nexuiz regularly, it works fine. Perhaps it isnt set up for it, but ATI say it is, mtippett of ati says it is, and others who have used it say it is.

Ive yet to find someone who has managed it successfully with a 9600. I guess Ill just have to wait.

---

### Post by zachtib on 2006-02-16
[QUOTE=born_confused]matt, I dont know, if I startx without xgl, everything works fine, it shows fglrx on fglrxinfo, 3d works great, and Ive always used fglrx and play nexuiz regularly, it works fine. Perhaps it isnt set up for it, but ATI say it is, mtippett of ati says it is, and others who have used it say it is.

Ive yet to find someone who has managed it successfully with a 9600. I guess Ill just have to wait.[/QUOTE]

exact same here
fglrx reports correctly in a normal X.org session, but in Xgl it says mesa

---

### Post by born_confused on 2006-02-16
[QUOTE=zachtib]exact same here
fglrx reports correctly in a normal X.org session, but in Xgl it says mesa[/QUOTE]

well heres another odd thing

```

lsmod | grep fglrx
fglrx                 454476  7
agpgart                34888  2 fglrx,sis_agp

```

fglrx in use? strange ...

---

### Post by aamukahvi on 2006-02-16
[QUOTE=born_confused]I have a radeon 9600 256mb

and heres my xorg.conf file

```

yada yada

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" **0 0**
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

yada yada

```[/QUOTE]
Remove those zeroes and tell me if it works ;)

---

### Post by born_confused on 2006-02-16
removed the zeros, still no unfortunately

just tried to rmmod fglrx, well ...

ERROR: Module fglrx is in use

---

### Post by fluxin on 2006-02-16
Is anyone able to run glxgears while in Xgl? I have everything accelerated but glxgears doesn't work at all, just checking to see if that's correct

---

### Post by david.cab on 2006-02-16
[QUOTE=zachtib]exact same here
fglrx reports correctly in a normal X.org session, but in Xgl it says mesa[/QUOTE]
I've been having exacly the same problem with a X700 Mobile.
Just can't figure out why Xgl doesn't like my fglrx driver... :confused:

---

### Post by fluxin on 2006-02-16
same here, but I'm not sure that's a problem, I could be wrong though

---

### Post by fluxin on 2006-02-16
[QUOTE=born_confused]sure

results from home 

```

grep 'Xgl :1' * -R

```

results from /etc/gdm
```

 grep 'Xgl :1' * -R
gdm.conf-custom:command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer


```[/QUOTE]
Here we go
Restart the computer
when GDM comes up goto a terminal (Alt-F1)
do a 
sudo /etc/init.d/gdm stop
wait
do a 
killall Xorg
killall Xgl
just in case
now do a 
sudo apt-get --reinstall install libgl1-mesa

See if that works

---

### Post by born_confused on 2006-02-16
[QUOTE=fluxin]Here we go
Restart the computer
when GDM comes up goto a terminal (Alt-F1)
do a 
sudo /etc/init.d/gdm stop
wait
do a 
killall Xorg
killall Xgl
just in case
now do a 
sudo apt-get --reinstall install libgl1-mesa

See if that works[/QUOTE]

unfortunately no, thanks for the help, but I may leave it a while ... Ill see

---

### Post by born_confused on 2006-02-16
just confirm, using dappers repositories, what is the LD_LIBRARY_PATH i am supposed to specify? seeing as fglrx seems to be in use, perhaps its just reporting wrong? I dont know ... 

what library is it supposed to see?
If its the mesa libraries why is it when I slocate mesa, not a single one of the results look like library files.

---

### Post by macmasterxiv on 2006-02-16
I'm having the same problem. fglrx in xorg and mesa in xgl. I'm not sure if this matters but I'm using a deb created by the ati-installer v8.22.5

---

### Post by fluxin on 2006-02-16
don't use a LD_LIBRARY_PATH or set it to /usr/lib

---

### Post by born_confused on 2006-02-16
[QUOTE=fluxin]don't use a LD_LIBRARY_PATH or set it to /usr/lib[/QUOTE]

neither?

well, I get the somewhat common error 

GLX_EXT_texture_from_pixmap is missing
Failed to manage screen: 0
No managable screens found on display :1

---

### Post by fluxin on 2006-02-16
Just for fun, stop GDM goto a promp and issue a
apt-get update 
apt-get --reinstall install xserver-xgl compiz libgl1-mesa libgl1-mesa-dri libglitz1 libglitz-glx1

---

### Post by born_confused on 2006-02-16
[QUOTE=fluxin]Just for fun, stop GDM goto a promp and issue a
apt-get update 
apt-get --reinstall install xserver-xgl compiz libgl1-mesa libgl1-mesa-dri libglitz1 libglitz-glx1[/QUOTE]

fun? lol

did that, nope, no difference

---

### Post by mattisking on 2006-02-16
Sorry guys. I've been away for a bit and I think I may have mislead you in that last bit. I must have misread myself. born_confused, if fglrxinfo properly identifies itself WITHOUT Xgl running but then reports Mesa WHEN it's running... that is normal. This is because Xgl is currently hard coded to Mesa in this way. You still have to have the fglrx driver working properly FIRST but then it's normal to see Mesa... Let's see if I can find the quote...

---

### Post by born_confused on 2006-02-16
[QUOTE=mattisking]Sorry guys. I've been away for a bit and I think I may have mislead you in that last bit. I must have misread myself. born_confused, if fglrxinfo properly identifies itself WITHOUT Xgl running but then reports Mesa WHEN it's running... that is normal. This is because Xgl is currently hard coded to Mesa in this way. You still have to have the fglrx driver working properly FIRST but then it's normal to see Mesa... Let's see if I can find the quote...[/QUOTE]

Oh thats fantastic, because then it makes sense
FGLRX is in use while, Xgl is running, and can be removed once its turned off

Now, compiz ... Im using the dapper repositories
if i dont specify paths then it complains that GLX_EXT_texture_from_pixmap is missing. However if I specify the libGL, fglrx one, it complains about support for non power of two textures missing.

---

### Post by born_confused on 2006-02-16
Well looked into the libraries in this website

[http://battlehorse.homelinux.net](http://battlehorse.homelinux.net)

and in the mesa library there exists libGLw.so

I did an slocate on mine, it doesnt exist ...

at the same time mine has libGLEW.so which doesnt seem to exist in the other sites mesa lib.

---

### Post by macmasterxiv on 2006-02-16
In the case of accel then, Xgl works fine, however it does seem very sluggish; whenever I run the compiz command (with all the extra stuff, after the gnome-window-decorator) all my window borders and panel bars disappear.

---

### Post by captcanuk on 2006-02-16
Here's the low down on ATI and XGL.

Radeon 8x00 and 9[012]00 should probably use the open source driver.

Everyone else, install the driver from repository or download the installer and generate debs ([http://wiki.cchtml.com](http://wiki.cchtml.com) ; click on Ubuntu on the right and follow the full installation guide).

Before you proceed, make sure you have accelerated 3D by typing fglrxinfo and seeing ATI as the vendor.

Install all the fun stuff listed before (glitz, compiz, XGL, libmesa, ...).

Press ctrl-alt-f1 to drop to console and log in as root.
Type: /etc/init.d/gdm stop
to shutdown GDM.

Then type the following to launch Xgl:
/usr/local/bin/Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &

You can now launch glxcompmgr and metacity or just compiz.

If you are having problems with missing extensions, one of two things is wrong - both related to libGL.so.1.2.

How does Xgl work?  It's a fully functioning top layer that launches X within itself and handles the calls.  What does this mean? It means it uses the 3D driver so it requires a working 3D Driver.

When XGL is running (right now at least), all the OpenGL calls are rerouted through software GL (Mesa).  This requires you to point the application you are starting to the correct libmesa installed libGL.  DO NOT MOVE your libGL's around if your 3D driver is working.  Instead, once inside Xgl, set the LD_LIBRARY_PATH before you launch the app like so:
LD_LIBRARY_PATH=/usr/lib  /usr/bin/compiz gconf cube zoom wobbly

If you are having troubles with missing MESA extensions, then type:
locate libGL.so.1.2
and set the LD_LIBRARY_PATH from above to each of the directories that contain that file and try launching compiz or glxcompmgr.  Also make sure that each of the directories you do that with also have 2 symlinks pointing to libGL.so.1.2 - one name "libGL.so" and one name "libGL.so.1".

Because of the usage of Mesa libGL, typing fglrxinfo from inside Xgl results in Mesa as the renderer (expected!).

I also found that one of the older tutorials stated you should copy the /usr/lib/libGL.so.1.2.fglrx to a new directory and set the LD_LIBRARY_PATH to that new directory (try this if all else fails).


Now I just have to figure out why compiz won't draw my window decorations via gnome-window-decorator and why my shortcut keys aren't actually activating expose/zoom/rotate like they once did!

---

### Post by born_confused on 2006-02-16
well, taking on board what you have said, I have tried specifying the fglrx libGL.so.1.2 as mentioned earlier

this is what I get specifying the /usr/lib where theres another libGL.so.1.2

```

/usr/lib$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1

/usr/lib$ glxinfo -display :1 | grep GLX_EXT_texture_from_pixmap
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap


```

and with the fglrx path

```

compiz.real: Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1

```

---

### Post by zachtib on 2006-02-16
upgrade to fglrx 8.22.5, still n oluck.  tried the fglrx-glitz package from  battlehorse, no good.   this is really startingto annoy me. cant wait to go home this weekend and try this on my nvidia computer

---

### Post by .k2600. on 2006-02-17
Look at this command output:

glxinfo | grep GL_EXT_texture
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,

There is no GLX_EXT_texture_pixmap. Running 8.22.5 with ati's libGL.so.1.2 ... ??
And libgl1-mesa points to same place: /usr/lib/libGL.so.1.2 where ati installer put it's libGL.so.1.2. Tried
manually replacing it with one from libgl1-mesa - result is that xgll won't start anymore...

---

### Post by aamukahvi on 2006-02-17
[QUOTE=born_confused]just confirm, using dappers repositories, what is the LD_LIBRARY_PATH i am supposed to specify? seeing as fglrx seems to be in use, perhaps its just reporting wrong? I dont know ... 

what library is it supposed to see?
If its the mesa libraries why is it when I slocate mesa, not a single one of the results look like library files.[/QUOTE]
I told you to remove the zeroes because I don't have them in my conf. Sorry it didn't work.
LD_LIBRARY_PATH? I didn't specify any library paths and it works just fine.
Are you sure you changed the 0 to 1 in gdm.conf? Like this:
#0=Standard
1=Standard

---

### Post by mattisking on 2006-02-17
Guys.... updates to mesa and xserver-xgl have been accepted. It's just a matter of time until they hit the repos, probably sometime today. There are some comments in the updates that seem like they may fix this problem for some of you, so stay tuned.

---

### Post by aamukahvi on 2006-02-17
[QUOTE=mattisking]Guys.... updates to mesa and xserver-xgl have been accepted. It's just a matter of time until they hit the repos, probably sometime today. There are some comments in the updates that seem like they may fix this problem for some of you, so stay tuned.[/QUOTE]
Nice. What does the MANUALDEPWAIT state mean on Xgl_i386? Is it waiting until Mesa is built? Or some other dependencies? EDIT: I guess not. Mesa is already built.

---

### Post by thekiller on 2006-02-17
I tried to install the latest fglrx driver from ati's website, and first it complained about not been able to find a matchin directory 'x700' for the current xorg server (7.0.0, of course). I corrected that according to the help given within the error and overrode it with 'x690' (xorg6.9.0). I preferred the automatic install, and from the gui it seemed like everything was installed. However, when i checked the logs, it complained about not been able to pre-compile the kernel module. I overlooked that, and instead tried to use "aticonfig" as was suggested in ATI's gui. And waala, no aticonfig found !!!
I used the same installer over 5 times, to get aticonfig recognized. Eventually, I had that available after 5-6 tries. And when I ran it, it just said "Found a fglrx device section in /etc/X11/xorg.conf" and that was it. I checked xorg.conf and there were fancy ati weirdo thingies written all over my xorg.conf which made me think, it indeed did something. Anyway, I rebooted yada yada yada....installed everything else needed for my 3D to work, but the damn thing didnt work. Am i cursed or what ? lol....I tried both Nvidia (of course the older version) and ATI (9000 Radeon), and my eventual step using both these methods was to :

apt-get remove ... .... .... .... .... .... .... .... ....

---

### Post by cantas on 2006-02-17
Hi,
is compiz working with Mobility 9000?
I installed it, everything seems to be fine, but all I get is a Gnome desktop (after login) which is completely messed up, and it reminds me of the same problem there is between radeonfb and fglrx (the desktop is split into many tiles and they are all mixed up).

Any clue?

Stefano

---

### Post by zachtib on 2006-02-17
[QUOTE=cantas]Hi,
is compiz working with Mobility 9000?
I installed it, everything seems to be fine, but all I get is a Gnome desktop (after login) which is completely messed up, and it reminds me of the same problem there is between radeonfb and fglrx (the desktop is split into many tiles and they are all mixed up).

Any clue?

Stefano[/QUOTE]

not for me, yet

---

### Post by Bou on 2006-02-17
[QUOTE=mattisking]updates to mesa... seem like they may fix this problem for some of you[/QUOTE]

Is the mesa update for us who can't even start Xgl, or for compiz only?

---

### Post by aamukahvi on 2006-02-17
I just installed the new mesa and the desktop seems to respond better. Snappier.

EDIT: Also tried on my other comp w/ R8500. No dice. Just a garbled screen with lots of odd bright colours.

---

### Post by MrRoboto on 2006-02-17
[QUOTE=aamukahvi]I just installed the new mesa and the desktop seems to respond better. Snappier.[/QUOTE]


interesting...

but I get this stupid error!

E: /var/cache/apt/archives/libgl1-mesa_6.4.1-0ubuntu6_i386.deb: impossibile creare `./usr/lib/libGL.so.1.2'

---

### Post by aamukahvi on 2006-02-17
[QUOTE=MrRoboto]interesting...

but I get this stupid error!

E: /var/cache/apt/archives/libgl1-mesa_6.4.1-0ubuntu6_i386.deb: impossibile creare `./usr/lib/libGL.so.1.2'[/QUOTE]
Have you tried removing and reinstalling the package? You have installed everything from the repos, right?

---

### Post by MrRoboto on 2006-02-17
[QUOTE=aamukahvi]Have you tried removing and reinstalling the package? You have installed everything from the repos, right?[/QUOTE]

yes I did, but if I click ok it will try to remove half of the system :D

---

### Post by fluxin on 2006-02-17
do a apt-get --reinstall install, that will keep it from removing everything!

---

### Post by MrRoboto on 2006-02-17
[QUOTE=fluxin]do a apt-get --reinstall install, that will keep it from removing everything![/QUOTE]

did already... same error :(

---

### Post by superm1 on 2006-02-17
Updated mesa libs still doesn't help this problem:
```

supermario@portablemario:~$ compiz --replace
 compiz.real: Support for non power of two textures missing
```

---

### Post by Corrosionx on 2006-02-17
I tried everything here, and finally everything stopped working, my aptitude has problems with libfreetype.so.6 and libgtk2.0 and libgtk2.0-bin are ruined, immodules gives me errors when doing dpkg --configure -a

... man that's gonna be cool when it works but now it's hair pulling time...

---

### Post by CHUCKYCHUCK on 2006-02-17
hi ! i'm not a dapper drake user, but i just would like to know if xgl will be able to run on my computer

P4 3Ghz
512 Ram
ATI M 9700 128 Mb

it was said that we should have a 9800 card minimum, but do you think it's gonna run on my laptop ??

thank you

---

### Post by aamukahvi on 2006-02-17
[QUOTE=CHUCKYCHUCK]hi ! i'm not a dapper drake user, but i just would like to know if xgl will be able to run on my computer

P4 3Ghz
512 Ram
ATI M 9700 128 Mb

it was said that we should have a 9800 card minimum, but do you think it's gonna run on my laptop ??

thank you[/QUOTE]
That should work just fine. I have the R9500 and everything is smooth except "starting apps animation" (can be disabled) and videos. Oh, and resizing. But that's common to all ATI cards because of the drivers.

---

### Post by fluxin on 2006-02-17
Not only common to ATI, All the cards have slow resizing basically. I don't think that the 9500 is really any slower in regards to anything, it's just some of the small quirks that happen with Xgl, (the slow animation, movies, etc...) You are disabling XV video acceleration so it's going to be slow (unless your cpu can handle it)

---

### Post by CHUCKYCHUCK on 2006-02-17
[QUOTE=aamukahvi]That should work just fine. I have the R9500 and everything is smooth except "starting apps animation" (can be disabled) and videos. Oh, and resizing. But that's common to all ATI cards because of the drivers.[/QUOTE]

thx,
now we just have to hope that ati will release better drivers ... :)

bye

---

### Post by fluxin on 2006-02-17
Anyone able to run gnome-xchat under Xgl?

---

### Post by aamukahvi on 2006-02-17
[QUOTE=fluxin]Not only common to ATI, All the cards have slow resizing basically. I don't think that the 9500 is really any slower in regards to anything, it's just some of the small quirks that happen with Xgl, (the slow animation, movies, etc...) You are disabling XV video acceleration so it's going to be slow (unless your cpu can handle it)[/QUOTE]
I stand corrected :) The xv-problem is actually my main gripe. I hate switching back to metacity just to watch the weekly episode of LOST. 8-[

---

### Post by fluxin on 2006-02-17
Have you disabled XV under gstreamer-properties? If not try that, you won't be pumping textures through XV to xgl then, it might help a bit.

---

### Post by aamukahvi on 2006-02-17
[QUOTE=fluxin]Have you disabled XV under gstreamer-properties? If not try that, you won't be pumping textures through XV to xgl then, it might help a bit.[/QUOTE]
Yes, I did that when enabling Xgl. Since then I've tried all possible settings but they're no different.

---

### Post by fluxin on 2006-02-17
So is anyone able to run any 3d apps once compiz is running under xgl? i.e. fgl_glxgears, glxgears, etc...

---

### Post by aamukahvi on 2006-02-17
[QUOTE=fluxin]So is anyone able to run any 3d apps once compiz is running under xgl? i.e. fgl_glxgears, glxgears, etc...[/QUOTE]
fgl_glxgears doesn't seem to start, and glxgears doesn't show the gears, just black background.

---

### Post by fluxin on 2006-02-17
okay, same thing here

---

### Post by born_confused on 2006-02-17
well, just upgraded, same problem exactly, its something else. I tried compiz without the LD_ stuff ... same thing

I just dont get it ... Xgl loads, it seems to be using fglrx, I see the mesa extension in glxinfo, yet it still complains about it

---

### Post by fluxin on 2006-02-17
I stand slightly corrected, it appears that with an Nvidia card you can keep XV
[QUOTE=aamukahvi]I stand corrected :) The xv-problem is actually my main gripe. I hate switching back to metacity just to watch the weekly episode of LOST. 8-[[/QUOTE]

---

### Post by Rob2687 on 2006-02-17
Has anyone gotten this to work with older ATI cards using the open source "radeon" drivers?
The suse page says it kinda works but with no Pbuffer or FBO support. Everytime I try to start it, it says
> Fatal server error:
no screens found


---

### Post by mattisking on 2006-02-18
I'm going to try again this weekend on my lower end system that includes a Radeon 9200. If I get anywhere with it, all of that will be added to the "How To".

---

### Post by mattisking on 2006-02-18
[QUOTE=superm1]Updated mesa libs still doesn't help this problem:
 compiz.real: Support for non power of two textures missing[/QUOTE]

The How-To was recently updated... take a look at the line for launching Xgl in the gdm.conf-custom file in the How-To. I've changed the last parameter from perror to fbo... something that others have shown seems to work more often for some users. I tried it myself and didn't notice much. It's worth a shot anyway.

---

### Post by superm1 on 2006-02-18
[quote=mattisking]The How-To was recently updated... take a look at the line for launching Xgl in the gdm.conf-custom file in the How-To. I've changed the last parameter from perror to fbo... something that others have shown seems to work more often for some users. I tried it myself and didn't notice much. It's worth a shot anyway.[/quote]

You should have seen the look on my face when I read this post, i was so happy to *maybe* have a fix.  Unfortunately it still doesn't go. :(

I did see you also mentioned that many laptop users are having issues.  Do you know why its effecting laptop users (and not desktop in that matter).  I have a Fire GL T2 128 in my lappie that I use with dapper.

---

### Post by melalcoolique on 2006-02-18
Few words about Xgl and ATI 9200 with "radeon" driver.

1) glxinfo returns me i've _no_ direct rendering. Doh. My login screen (GDM) appears slowly. Through, Gnome and some effects are really smooth. My CPU load is quite high when moving a window (between 20 and 8O%).

2) I've a black screen with Totem and GSTreamer.

3) I noticed I've two compiz running. Running? Hmm not really, one is zombie and the second one is called compiz.real.

4) My keyboard scheme mess up. I tried the following command but so i lose shortcuts for "exposé" and "cube" and some others.

```
xmodmap /usr/share/xmodmap/xmodmap.fr
```

5) The cursor theme is not "Human" anymore but the default black Xorg

Any of you could confirm these issues with open radeon drivers. Any tips or tricks? Thank you. Xgl just kick a*s. :mrgreen:

---

### Post by Meta on 2006-02-18
I been having similar problems to what other people have posted and recently have gotten everything to work now. I have a laptop with a Fire GL Mobility T2. I was able to install Xgl and compiz from the repositories and install the latest fglrx drivers which showed up properly under xorg but not Xgl using fglrxinfo. Apparently this is normal I found out. compiz needs the patched mesa libraries but needs the xorg on display 93 to load the fglrx dri modules. Using the mesa libraries from the repositories compiz always complaining about a missing GLX_EXT_texture_from_pixmap extension. Also any opengl application showed an empty window (i.e. glxgears). To get around this I install the mesa library from battlehorse [[http://battlehorse.homelinux.net/w/Wiki.jsp?page=Xgl]](http://battlehorse.homelinux.net/w/Wiki.jsp?page=Xgl]). Then after setting the LD_LIBRARY_PATH=/opt/mesa/lib, I was able to run compiz and gnome-window-decorator and other opengl programs. However the first time I needed to not include the gconf option to compiz since none of the plugins would load. I had to do it by the command line.

compiz --replace  decoration wobbly fade cube minimize rotate zoom scale move resize place menu &

After that I was able to setup the gconf with gconfig-editor. There is some guides to this on the battlehorse site. 

Once in a while compiz will still complain about the missing extension but this appears to go away after several tries. I have not been able to start compiz without setting the LD_LIBRARY_PATH to the other mesa package. This leads me to believe the version in the repository is not equivalent.

After getting things to work compiz and Xgl run great. :p The performance and stability appear to be good. Opengl apps like glxgears appear to be slower then with the fglrx libraries in use. I hope someone finds this helpful or points out something that I an not doing correctly.

---

### Post by mattisking on 2006-02-18
Very good infor Meta. I'm glad you managed to get it working for you. The other thread focused on Nvidia cards mentions running compiz multiple times to get it to work... maybe I should add something along those lines but I've never had that problem. It's always worked or not worked for me.

---

### Post by Jonq on 2006-02-18
does any ati x700 users able to run this thing ? i'm keep getting texture missing message, tried everything on forums none of them work, I hope we can find a solution for that asap :D

---

### Post by micampe on 2006-02-18
phew, I went through the painful registration (required birthday?!) just to post this, please appreciate the effort.

If you get the "compiz.real: GLX_EXT_texture_from_pixmap is missing" message, you need to LD_PRELOAD the Mesa libGL.so, because fglrx overwrites it. If you made the debian packages (which you should) it is in /usr/share/fglrx/diversions/, otherwise you need to get it somehow (for example reinstalling the libgl1-mesa package).

For details: [http://micampe.it/2006/02/18/ubuntu-fglrx-xgl-compiz-and-missing-glx_ext_texture_from_pixmap](http://micampe.it/2006/02/18/ubuntu-fglrx-xgl-compiz-and-missing-glx_ext_texture_from_pixmap)

---

### Post by Benjamin_Lebsanft on 2006-02-18
I installed compiz from universe but I don't have any gconf options. /apps doesn't list compiz. This is on amd64, is there something I can do?

---

### Post by aamukahvi on 2006-02-18
Try running compiz once without the gconf, but with all the plugins.
```
compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```
I kinda remember someone saying that would help. :-k

---

### Post by Mysling on 2006-02-18
Hello all! ;) 

This is my first post to this forum. I just wanna say thank you for all the help, everything is now working topnotch, except from the video-playback.. Im gonna be sticking around to help people as much as i can, the same way you helped me.  :D 

Just one question.. The one thing that will make video playback better, is for ati to release new drivers, right? If so, guess i'll just have to wait..

---

### Post by oelph on 2006-02-18
[QUOTE=aamukahvi]Try running compiz once without the gconf, but with all the plugins.
```
compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```
I kinda remember someone saying that would help. :-k[/QUOTE]

I can confirm this works. I had no compix options in gconf-editor but after running manually its now there.

Something I'm noticing - when moving windows, it sometimes takes a while for them to 'unblur' and look crisp again. One time the window didn't unblur at all leaving me thinking my eyesight was going!! :D  Anyone else found this?

---

### Post by firetux on 2006-02-18
> 6. Modify your session ("Menu System" -> "Preferences" -> "Sessions") by adding in the following two items:
"gnome-window-decorator" (must be on top, start first)
"compiz --replace gconf"


I dont really understand this: do I need to add these items to "startup progs"?

---

### Post by Benjamin_Lebsanft on 2006-02-18
[QUOTE=oelph]I can confirm this works. I had no compix options in gconf-editor but after running manually its now there.

Something I'm noticing - when moving windows, it sometimes takes a while for them to 'unblur' and look crisp again. One time the window didn't unblur at all leaving me thinking my eyesight was going!! :D  Anyone else found this?[/QUOTE]
I tried but it doesn't work as compiz doesn't start because XGL isn't running due to some RGB error already mentionend in this thread. Does anyone know a solution for this?

Couldn't open RGB_DB '/usr/share/X11/rgb'

---

### Post by oelph on 2006-02-18
[QUOTE=firetux]I dont really understand this: do I need to add these items to "startup progs"?[/QUOTE]

It confused me a bit too. Go to System | Preferences | Sessions. Then click the Startup Programs tab. Click add and type 'compiz --replace gconf' and ok. Click Add again and type 'gnome-window-decorator' and ok. That should do it in the right order. My startup programs look like this:

gnome-window-decorator
compiz --replace gconf
gnome-power-manager
gnome-volume-manager --sm-disable

Obviously the last two lines aren't needed for Xgl/Compiz but just for completeness.

---

### Post by Benjamin_Lebsanft on 2006-02-18
[QUOTE=oelph]It confused me a bit too. Go to System | Preferences | Sessions. Then click the Startup Programs tab. Click add and type 'compiz --replace gconf' and ok. Click Add again and type 'gnome-window-decorator' and ok. That should do it in the right order. My startup programs look like this:

gnome-window-decorator
compiz --replace gconf
gnome-power-manager
gnome-volume-manager --sm-disable

Obviously the last two lines aren't needed for Xgl/Compiz but just for completeness.[/QUOTE]

my list is always ordered alphabetical no matter in which order i put the programs in

---

### Post by aamukahvi on 2006-02-18
[QUOTE=oelph]Something I'm noticing - when moving windows, it sometimes takes a while for them to 'unblur' and look crisp again. One time the window didn't unblur at all leaving me thinking my eyesight was going!! :D  Anyone else found this?[/QUOTE]
do this (from nvidia howto and god knows how many other threads ;)):

Run the command:
gconf-editor

Now go to:
apps>compiz>general>screen0>option

Then turn off the "detect_refresh_rate" option.
Then set the "refresh_rate" to 60

---

### Post by david.cab on 2006-02-18
[QUOTE=Jonq]does any ati x700 users able to run this thing ? i'm keep getting texture missing message, tried everything on forums none of them work, I hope we can find a solution for that asap :D[/QUOTE]
I have a X700 and I've been able to run Xgl and compiz. I had no problems with missing textures.
The only problem I had was that compiz woudn't work. Then I tried removing the 'gconf' option when running it and it worked fine, wobbly and cube effects and all.
Now the only problem remaining is Xgl crashing every 2 minutes or so... :???:

---

### Post by born_confused on 2006-02-18
[QUOTE=micampe]phew, I went through the painful registration (required birthday?!) just to post this, please appreciate the effort.

If you get the "compiz.real: GLX_EXT_texture_from_pixmap is missing" message, you need to LD_PRELOAD the Mesa libGL.so, because fglrx overwrites it. If you made the debian packages (which you should) it is in /usr/share/fglrx/diversions/, otherwise you need to get it somehow (for example reinstalling the libgl1-mesa package).

For details: [http://micampe.it/2006/02/18/ubuntu-fglrx-xgl-compiz-and-missing-glx_ext_texture_from_pixmap](http://micampe.it/2006/02/18/ubuntu-fglrx-xgl-compiz-and-missing-glx_ext_texture_from_pixmap)[/QUOTE]

Tried that earlier, I appreciate the post. As stated earlier, I get 

```

compiz.real: Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1


```

---

### Post by var on 2006-02-18
I can't find the "apps/compiz/general/all screens/options" in gconf-editor.
how can I fix it?

thanks. :)

---

### Post by oelph on 2006-02-18
Thanks aamukahvi.

Var see the replies on page 16.

---

### Post by born_confused on 2006-02-18
Does this look right? Direct Rendering: No?
```

 DISPLAY=:1 glxinfo | more
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon


```

---

### Post by spotk on 2006-02-18
[QUOTE=born_confused]Does this look right? Direct Rendering: No?
[/QUOTE]
I'me affraid that not...

Direct Rendering: No  , is ok, but as in my case (X700) 
GL_{NV,EXT,ARB}_texture_rectangle or the GL_ARB_texture_non_power_of_two extension
is missing from your glxinfo report, and as you know compiz will complain about that. 

One question : **can success users report if they have this extension loaded while Xgl running **?

i've tested every Driver and mesa libs ( ubuntu fglrx driver, Ati latest one, ubuntu last mesa libs , battlehorse mesa libs) and never have this f... extension loaded under Xgl. 

Cheers 

Spotk

---

### Post by aamukahvi on 2006-02-18
[QUOTE=spotk]One question : **can success users report if they have this extension loaded while Xgl running **?[/QUOTE]
I would like to help, but I can't get glxinfo running. Any suggestions?

---

### Post by realjenius on 2006-02-18
Ok, I'm having problems; I'll document here what I have done so far. Let me prefix this by saying that I'm still fairly new to Ubuntu, so I may be missing some obvious things.

I *believe* that my problems are probably coming from the fact I'm using a Mobility (which has been marked as being a potential problem for this approach), however I just want to post here for a sanity check.

I can get XGL running, but it is *very* *slow*.

I have the drivers from ATI's website installed, I'm not sure if those are 'fglrx', or not - they certainly report properly. If not, it would be nice if someone could point me to some instructions for reverting the ATI drivers and getting the FGLRX variety installed. 

Ok, first, my Xorg.conf - Note that even though step 1 is to change Xorg.conf, I did not change this from the default configuration from aticonfig --initial because I couldn't find anything to change based on the three threads:
```

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

(...)

Section "Device"
        Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "ATI Graphics Adapter 0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

```

Here is some additional output -
**fglrxinfo:**
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5642 (8.22.5)

```

**glxinfo:**
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5642 (8.22.5)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None

```

Ok, so far so good. Now, **I pulled everything down from the repository:**
```

:~$ sudo apt-get install xserver-xgl compiz libgl1-mesa libgl1-mesa-dri libglitz1 libglitz-glx1
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
compiz is already the newest version.
libgl1-mesa is already the newest version.
libgl1-mesa-dri is already the newest version.
libglitz1 is already the newest version.
libglitz-glx1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Now I'm ready to try the GDM part of the install. I have tried a configuration on display 0 and display 1; only display 1 worked at all.
**gdm.conf**
```

1=Standard
#0=Standard
...
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0

```

**gdm.conf-custom**
```

[servers]
1=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

```

**XGL is installed in /usr/bin/Xgl, and it does work; just poorly!**

Ok, now I restart.

At this point my *gut* feeling is that the CPU is doing all of my rendering. My sys-monitor shows the CPU spiking to 100% any time I move, scroll, etc. Here is some diagnostics:

**ps ax**
```

 4066 ?        R      0:06 /usr/bin/Xgl :1 :1 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -auth /var/lib/gdm/:1.Xauth -nolisten tcp vt7
(...)
 4088 tty7     SLs+   1:08 /usr/bin/Xorg vt7 -auth /tmp/.Xgl-auth-5VgMFE -nolisten tcp -dpms -v -s 0 :93 -terminate

```

**fglrxinfo AFTER XGL startup**
```

~$ fglrxinfo
Error: unable to open display :0

```

**glxinfo AFTER XGL startup**
```

~$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
   GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon


```

This print out leads me to believe that I've reverted in some fashion to the Mesa drivers.

Any thoughts/help would of course be appreciated!

---

### Post by jasay on 2006-02-18
[QUOTE=aamukahvi]I would like to help, but I can't get glxinfo running. Any suggestions?[/QUOTE]
Probably not helpful, but glxinfo takes a long time to run for in Xgl (~30s).  Maybe you just don't give it long enough?:-k Also if you run it from the virtual terminal or whatever alt-ctrl-f1 is called you may need to do something like ```
DISPLAY=:1 glxinfo
```

---

### Post by aamukahvi on 2006-02-18
realjenius:

Modify your gdm.conf-custom. You have a line there like this:
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:**fbo**
It should read:
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:**pbuffer**

---

### Post by aamukahvi on 2006-02-18
[QUOTE=jasay]Probably not helpful, but glxinfo takes a long time to run for in Xgl (~30s).  Maybe you just don't give it long enough?:-k Also if you run it from the virtual terminal or whatever alt-ctrl-f1 is called you may need to do something like ```
DISPLAY=:1 glxinfo
```[/QUOTE]
Hehe, seems that 10s was too long for me. I ran it a couple of times but I figured it had stalled so I killed it. ;) Here's the output:
```
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon
```
I am running Compiz at good framerates, definitely HW-accelerated.

---

### Post by superm1 on 2006-02-18
[quote=aamukahvi]
```
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon
```[/quote]
So it would appear that this [SIZE=1]GL_ARB_texture_non_power_of_two really isn't even shown during correct usage.  I wonder how compiz manages to use it then?

Can you repeat with
[/SIZE]```
DISPLAY=:1 LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 glxinfo
```[SIZE=1]
[/SIZE]

---

### Post by realjenius on 2006-02-18
aamukahvi,

Thanks for the quick response. I have changed the command to use 'pbuffer'; unfortunately it's still slow as all get-out.

---

### Post by born_confused on 2006-02-18
strange, doing the LD_PRELOAD on glxinfo shows it

```

DISPLAY=:1 LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
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
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_logic_op,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATIX_texture_env_combine3, GL_HP_occlusion_test,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square,
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


```

The question is, is it possible to append onto Xgl, and how so?

---

### Post by aamukahvi on 2006-02-18
Here's my libGL:
```
$ locate libGL /usr/lib/xorg/modules/extensions/libGLcore.so
/usr/lib/libGLU.so.1.3.060401
/usr/lib/libGL.so.1.2
/usr/lib/libGLU.so.1
/usr/lib/libGL.so.1
/usr/lib/libGLEW.so.1.3.1
/usr/lib/fglrx/libGL.so.1.xlibmesa
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/lib/libGLEW.so.1.3

```

I tried two times, first with /usr/lib/fglrx/libGL.so.1.2.xlibmesa but I didn't get ATI as client. Then I tried with /usr/lib/libGL.so.1.2 which reported ATI. Output:
```
**$ DISPLAY=:1 LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa glxinfo**
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
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
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_logic_op,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATIX_texture_env_combine3, GL_HP_occlusion_test,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square,
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

**$ DISPLAY=:1 LD_PRELOAD=/usr/lib/libGL.so.1.2 glxinfo**
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon

```

---

### Post by superm1 on 2006-02-18
I was just looking through compiz sources to see what its really saying is going on when this error is reported.

Apparantly the Support for non power of two textures can mean 3 different things.

1) Actually doesn't support GL_ARB_non_power_of_two_textures
2) Doesn't support at least one of : GL_NV_texture_rectangle, GL_EXT_texture_rectangle, or GL_ARB_texture_rectangle.
3) For some external reason, the call to determine extensions is being returned as Null before even checking for extensions.

I may just start rebuilding compiz with my own debugging info to figure out which of these is actually the case.

For those curious, I determined that it could be any of these 3 by looking in compiz/src/screen.c at this subsection:
```

    glExtensions = (const char *) glGetString (GL_EXTENSIONS);
    if (strstr (glExtensions, "GL_NV_texture_rectangle")  ||
        strstr (glExtensions, "GL_EXT_texture_rectangle") ||
        strstr (glExtensions, "GL_ARB_texture_rectangle"))
        s->textureRectangle = 1;

    s->textureNonPowerOfTwo = 0;
    if (strstr (glExtensions, "GL_ARB_texture_non_power_of_two"))
        s->textureNonPowerOfTwo = 1;

    if (!(s->textureRectangle || s->textureNonPowerOfTwo))
    {
        fprintf (stderr, "%s: Support for non power of two textures missing\n",
                 programName);
        return FALSE;
    }
```

---

### Post by superm1 on 2006-02-18
[quote=aamukahvi]Here's my libGL:
```
**$ DISPLAY=:1 LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa glxinfo**
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
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
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_logic_op,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATIX_texture_env_combine3, GL_HP_occlusion_test,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square,
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

**$ DISPLAY=:1 LD_PRELOAD=/usr/lib/libGL.so.1.2 glxinfo**
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon

```[/quote]
So in conclusion here, glxinfo by default is using the /usr/lib/libGL.so.1.2 which explains why these extensions aren't enabled for ATI's GL in Xgl.  When using the newer mesa, all of these "missing" extensions are indeed being loaded.  Even on my non functioning compiz box, I get all the required extensions loaded with an LD_PRELOAD.  Compiz still refuses to agree with this though.

---

### Post by Mysling on 2006-02-18
[QUOTE=realjenius]I *believe* that my problems are probably coming from the fact I'm using a Mobility (which has been marked as being a potential problem for this approach), however I just want to post here for a sanity check.[/QUOTE]

This is not gonna help much really, just want to tell that i got mine working with a R9700Mobility.. Maybe there's different kinds og R9700's. Once i got the driver working with the right output from fglrxinfo, i just followed this howto step by step, and i didn't encounter any problems. 

Maybe a fresh install of dapper would help?

---

### Post by zachtib on 2006-02-18
[QUOTE=Mysling]This is not gonna help much really, just want to tell that i got mine working with a R9700Mobility.. Maybe there's different kinds og R9700's. Once i got the driver working with the right output from fglrxinfo, i just followed this howto step by step, and i didn't encounter any problems. 

Maybe a fresh install of dapper would help?[/QUOTE]
How recently did you do this? i havent tried since the latest updates were added to dapper, about to try again, radeon M9000

---

### Post by Mysling on 2006-02-18
Just yesterday.. Had alot of problems getting my drivers working, but this howto did the trick: 

[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)

Says for 9500 or higher though, you might have to find another way.

---

### Post by beskyddaren on 2006-02-18
Just for the record, I'm on a laptop with the ati mobiliti 9700(9800) chip, and everything works great, including no sign of any slow resizes.

My only woe is not being able to play enemy territory (it launches in a window and spits out probably a single frame every two seconds ;-))

---

### Post by born_confused on 2006-02-18
I dont know how much this means but

```

glewinfo | grep rectangle
GL_ARB_texture_rectangle:                                      OK
GL_EXT_texture_rectangle:                                      OK
GL_NV_texture_rectangle:                                       OK

```

```

glewinfo | grep non_power
GL_ARB_texture_non_power_of_two:                               OK

```

---

### Post by macmasterxiv on 2006-02-18
I've been having the non_power error also and here is what I got:
```
jm@jmbox:~ $ glewinfo | grep rectangle
GL_ARB_texture_rectangle:                                      MISSING
GL_EXT_texture_rectangle:                                      OK
GL_NV_texture_rectangle:                                       MISSING

```
```
jm@jmbox:~ $ glewinfo | grep non_power
GL_ARB_texture_non_power_of_two:                               MISSING

```

I ran all of these commands under the standard xorg. For the record I have a 9800 Pro:
```
jm@jmbox:~ $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5642 (8.22.5)
```

Could OpenGL 2.0 be the issue?

---

### Post by superm1 on 2006-02-18
If your going to test with glewinfo, be sure to LD_PRELOAD the right library first.
(/usr/share/fglrx/diversions/libGL.so.1.2)

---

### Post by macmasterxiv on 2006-02-18
[QUOTE=superm1]If your going to test with glewinfo, be sure to LD_PRELOAD the right library first.
(/usr/share/fglrx/diversions/libGL.so.1.2)[/QUOTE]

Just did that, same results.

---

### Post by born_confused on 2006-02-18
[QUOTE=superm1]If your going to test with glewinfo, be sure to LD_PRELOAD the right library first.
(/usr/share/fglrx/diversions/libGL.so.1.2)[/QUOTE]

yeah, my results were due to doing so.

---

### Post by born_confused on 2006-02-18
Nevermind ...

---

### Post by Tharna on 2006-02-18
[QUOTE=superm1]I was just looking through compiz sources to see what its really saying is going on when this error is reported.

Apparantly the Support for non power of two textures can mean 3 different things.

1) Actually doesn't support GL_ARB_non_power_of_two_textures
2) Doesn't support at least one of : GL_NV_texture_rectangle, GL_EXT_texture_rectangle, or GL_ARB_texture_rectangle.
3) For some external reason, the call to determine extensions is being returned as Null before even checking for extensions.

I may just start rebuilding compiz with my own debugging info to figure out which of these is actually the case.

For those curious, I determined that it could be any of these 3 by looking in compiz/src/screen.c at this subsection:
[/QUOTE]

I was having the same *non power of two* problem. Inspired by superm1's background work I tried to build compiz commenting a bit of that out, and got it working (at least in some level, wasnt able to build decoration, so didnt do much testing). Maby others could continue from here, and I'll go to sleep.

---

### Post by macmasterxiv on 2006-02-18
[QUOTE=macmasterxiv]Could OpenGL 2.0 be the issue?[/QUOTE]

Well, it isn't, I just tried the fglrx 8.20.8 driver which was the last one before opengl 2.0 support. The same extensions were missing.

---

### Post by superm1 on 2006-02-18
I've never built a deb from source, so I had a bit of trouble learning about how to get build-deps going and the correct commands to actually build a source deb.  It seems that it is failing in both the cases for the test.  Actually the call for glGetString is only returning:
```
GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_multi_draw_arrays GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_SGIS_texture_border_clamp GL_SUN_multi_draw_arrays
```

So, now the real problem is - why does compiz when supplied with the correct libGL still claim that library doesn't contain the necessary extensions?

---

### Post by macmasterxiv on 2006-02-18
[QUOTE=superm1]So, now the real problem is - why does compiz when supplied with the correct libGL still claim that library doesn't contain the necessary extensions?[/QUOTE]

I'm not sure compiz is at fault here. Whenever I run Xgl without it, the user interface is incredibly slow as in not even mesa acceleration 2d or 3d. Just the standard metacity max/minimize effects peg the cpu and take 3 seconds to complete. I don't think compiz will perform a miracle and miraculously speed up the ui while turning effects on. Something else is wrong here, at least in my case.

---

### Post by born_confused on 2006-02-18
[QUOTE=macmasterxiv]I'm not sure compiz is at fault here. Whenever I run Xgl without it, the user interface is incredibly slow as in not even mesa acceleration 2d or 3d. Just the standard metacity max/minimize effects peg the cpu and take 3 seconds to complete. I don't think compiz will perform a miracle and miraculously speed up the ui while turning effects on. Something else is wrong here, at least in my case.[/QUOTE]

hmm, true, as you said metacity is incredibly slow on Xgl

---

### Post by lulin on 2006-02-18
I did a fresh install today from a daily build install cd and followed the howto. Everything went fine, except that including wobbly in the plugins always crashes my system after some seconds/minutes. I'm using a 9600,

---

### Post by Zek on 2006-02-18
hello,

Everything works fine for me, except opengl.

here is the log :

```

22:26 nicolas@Tux ~% fglrxinfo
Error: unable to open display :0
zsh: exit 255   fglrxinfo

23:14 nicolas@Tux ~% echo $DISPLAY
:1.0
23:14 nicolas@Tux ~%

```

how do i modify the display from 0 to 1 in fglrx ?

thanks

---

### Post by born_confused on 2006-02-18
[QUOTE=Zek]hello,

Everything works fine for me, exept opengl.

here is the log :

```

22:26 nicolas@Tux ~% fglrxinfo
Error: unable to open display :0
zsh: exit 255   fglrxinfo

23:14 nicolas@Tux ~% echo $DISPLAY
:1.0
23:14 nicolas@Tux ~%

```

how do i modify the display from 0 to 1 ?

thanks[/QUOTE]

generally its DISPLAY=:1 for fglrxinfo fglrxinfo -display :1

---

### Post by Zek on 2006-02-18
Thanks :)

---

### Post by realjenius on 2006-02-18
Thanks for the responses Mysling and others - it's good to hear the mobility can run it even if only in some configurations.

It looks like maybe I do have the wrong drivers installed; using the binary-driver howto, did you install them via the repo, or from the ATI website?

---

### Post by realjenius on 2006-02-18
[QUOTE=macmasterxiv]I'm not sure compiz is at fault here. Whenever I run Xgl without it, the user interface is incredibly slow as in not even mesa acceleration 2d or 3d. Just the standard metacity max/minimize effects peg the cpu and take 3 seconds to complete. I don't think compiz will perform a miracle and miraculously speed up the ui while turning effects on. Something else is wrong here, at least in my case.[/QUOTE]

I'm having this same problem with XGL - the max/min effects are extraordinarily slow for me too - it has prevented me from moving forward at all.

Someone else mentioned that they installed the binary drivers from the Wiki binary driver how-to - that's probably my next step...

---

### Post by concept10 on 2006-02-18
I need some advice/help from one of you guys.  I want to get this installed but not sure which direction to proceed.  I have a HP latop ze5570 with an ATI card.

lspci: 0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 340M

I'm not sure if this will work with XGL. Someone enlighten me, please!

I have been using the default "ati" drivers on Breezy, and I tried to install and reconfigure to the fglrx drivers from Seveas' repo.  It did'nt work for me. :cry:   I got these errors from /var/log/Xorg.0.log:

(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found

:confused: 

Suggestions anyone??  Thanks in advance.

---

### Post by born_confused on 2006-02-18
Well, I reinstalled Dapper. And ... it works. It looks so good, no slow down, the Shadows really help. I just need to get used to it now

---

### Post by .k2600. on 2006-02-19
Did a fresh install, Xorg 7.0 and fglrx 8.22.5 and xgl/compiz from repo, could someone explain this:

root@box:~# glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
---cut

So, finally, there's texture_from_pixmap, but compiz still gives:

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

And when i try LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 compiz.real ....
then power_of_two_textures is missing?

---

### Post by Mysling on 2006-02-19
[QUOTE=realjenius]It looks like maybe I do have the wrong drivers installed; using the binary-driver howto, did you install them via the repo, or from the ATI website?[/QUOTE]

I used those from the repo: sudo apt-get install xorg-driver-fglrx. They should be just fine. I don't think you will get better performance using those from the ATI website.

---

### Post by Shutdownrunner on 2006-02-19
I exactly followed the instructions from the first post, but I get the following problems.
-After modifying gdm.conf, gdm-custom.conf,  fglrxinfo says that I don't have direct rendering and so on. Even if if try fglrxinfo --display :1, it still shows that I have indirect mesa...
-Issuing compiz --replace..... causes strange things. The screen looks as if I tried to watch encrypted TV without a decoder. If I don't issue compiz --replace... nothing happens, no cool effects and GNOME works just terribly slow.

I have Radeon 9000 PRO. I don't know. Maybe my xorg.conf is to blame, but you wrote that if fglrxinfo is ok, then no changes to xorg.conf are required.

---

### Post by aamukahvi on 2006-02-19
[QUOTE=Shutdownrunner]I have Radeon 9000 PRO. I don't know. Maybe my xorg.conf is to blame, but you wrote that if fglrxinfo is ok, then no changes to xorg.conf are required.[/QUOTE]
I think it's the drivers. My R8500 has exactly the same symptoms, but R9500 works fine.

---

### Post by zafar on 2006-02-19
[QUOTE=.k2600.]Did a fresh install, Xorg 7.0 and fglrx 8.22.5 and xgl/compiz from repo, could someone explain this:

root@box:~# glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
---cut

So, finally, there's texture_from_pixmap, but compiz still gives:

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

And when i try LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 compiz.real ....
then power_of_two_textures is missing?[/QUOTE]

I'm getting the exact same problem.. I don't know what else to try.

---

### Post by d3x7r0 on 2006-02-19
Has anyone gotten a radeon 9600pro 256mb to work? It keeps giving me mesa when I type in fglrxinfo in the console :cry:

---

### Post by macmasterxiv on 2006-02-19
I GOT IT WORKING! I was having the non_power bug and after reinstalling dapper with a daily cd, it now works! Previously I was on a breezy-upgraded dapper.

---

### Post by born_confused on 2006-02-19
[QUOTE=d3x7r0]Has anyone gotten a radeon 9600pro 256mb to work? It keeps giving me mesa when I type in fglrxinfo in the console :cry:[/QUOTE]

Yup, I do, use the fglrx drivers in repo. Use a clean dapper. :-#

---

### Post by d3x7r0 on 2006-02-19
I'm using a clean dapper and the repo version :cry: 

Just formated again, gonna try it one more time :?

EDIT:
> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Still the same :(

---

### Post by sephiroth_4 on 2006-02-19
GREAT TUTORIAL!~!  But I screwed up!


Step 6...I put the quotes in....
I couldn't see the compiz in the gconf-editor so I rebooted...
Machine locks @ login splash.
I assume the quotes have something to do with it ;)
What do I do now to get rid of those quotes and the lockups?

---

### Post by firetux on 2006-02-19
Undo the changes you made in /etc/gdm/gdm.conf-custom.

---

### Post by sephiroth_4 on 2006-02-19
Thank you for the quick reply!

So boot with rescue cd and vi those changes in /etc/gdm/gdm.conf-custom?

THANKS AGAIN!

edit...it worked!

BUT....how do I now get rid of the ugly "gnome-win..." and "comiz --repl..." in the sessions options of the sessions editor as the buttons are grey'd out...and I need to re apply those changes in the gdm.conf..

---

### Post by born_confused on 2006-02-19
[QUOTE=d3x7r0]I'm using a clean dapper and the repo version :cry: 

Just formated again, gonna try it one more time :?

EDIT:


Still the same :([/QUOTE]

Write down the exact steps you took

---

### Post by zafar on 2006-02-19
Shouldn't an updated breezy to dapper with all updates be the same as a daily dapper?..
Can one of you who moved to a clean dapper install poke around some of the packages like mesa and  the driver and see if you notice anything different than you remember with your breezy upgraded to dapper?

---

### Post by d3x7r0 on 2006-02-19
ok let's see:
- install dapper flight 4
- upgrade-manager
- sudo apt-get install xorg-driver-fglrx
- sudo nano -w /etc/X11/xorg.conf
- changed driver to fglrx
- ctrl + alt + backspace (restart gnome)
- fglrxinfo

And it gives the same result... I've tried a couple of variations like downgrading the kernel to -14 instead of -15 (that comes in the cd), login in single-user mode to do the steps... you name it. Can't get what's wrong and from the looks of this thread I'm not the only 9600 user with this sort of issue :(

---

### Post by firetux on 2006-02-19
[QUOTE=sephiroth_4]Thank you for the quick reply!

So boot with rescue cd and vi those changes in /etc/gdm/gdm.conf-custom?

THANKS AGAIN!

edit...it worked!

BUT....how do I now get rid of the ugly "gnome-win..." and "comiz --repl..." in the sessions options of the sessions editor as the buttons are grey'd out...and I need to re apply those changes in the gdm.conf..[/QUOTE]

I just ignored sessions, its greyed out here too. 
You could also have rebooted with the rescue option in grub and used "nano -w file.name" (I think nano is easier than vi). 
Just undo all changes, normally undoing gdm.conf-custom is enough.

---

### Post by sephiroth_4 on 2006-02-19
ok...I hate to do this...
BUT
in the gconf-editor, i don't have the compiz in apps.  I ran the app as mentioned on page 16, but to no avail.  The services did start up though in the current session I am assuming since it's now listed there.

When Compiz with all options is run, I get compiz.real: No composite extension and then nothing happens.

---

### Post by guyhersh on 2006-02-19
Hey,

  Thanks for the guide! Although I'm having a little problem.  I'll review what I did.

1. Installed DapperFlight4 from scratch.
2. Modified sources.list file to check universe repositorys.
3. Ran apt-get update, and apt-get upgrade
4. Installed fglrx ati drivers from ubuntu repository.
5. installed all files neccessary listed in step 2 of your guide
6. Followed guide exactly EXCEPT compiz wasnt in gconf-config so i had to run this manually "compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher " and then i was able to edit it in gconf-config.

During that session when i started compiz manually, Xgl worked great.

Then i added "gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher" to active_plugins (didnt see a plugins) under "apps/compiz/general/all screens/options"

It now freezes before signin or while loggin in most of the time.  And the time I did get in, there were no toolbars around the windows or anything and I had to run compiz manually again.

Any ideas?

Guy

---

### Post by arrowes on 2006-02-19
Hi, Thanks for all

I have a problem with Xgl, first of all I do this:

1. Installed DapperFlight4
2. Changed the sources and upgraded
3. Installed the ati drivers (I have a Radeon 9600)
4. Steps 1 to 4. I try to start Xgl from gdm but I only see a grey screen and then crashes.

The log shows it:

(EE) fglrx(0): === [R200DALSetControllerConfigForRemap] === CWDDC ControllerSetConfig failed: 6 - 0

Any idea?

---

### Post by jscat on 2006-02-19
Thanks for the how-to. Followed it step by step and works great. The only issue I had was gconf-editor not showing compiz, but that was fixed by the help on page 16 and a reboot. Thanks again.

---

### Post by sephiroth_4 on 2006-02-19
[QUOTE=jscat]Thanks for the how-to. Followed it step by step and works great. The only issue I had was gconf-editor not showing compiz, but that was fixed by the help on page 16 and a reboot. Thanks again.[/QUOTE]


NOooooo....  I'm gonna try to do some damage, if that doesn't work I'm starting over.
If I come up with anything...I'll be glad to post.

---

### Post by rahmza on 2006-02-19
Hey, forgive me if this problem has been stated here already, but I can't seem to find any information on it. Whenever I use Xgl, it will freeze when opening some programs. Sometimes it happens on gdm before I can even enter a login. Sometimes it will go log all the way in and then freeze when opening a program (firefox oftentimes does it). When it does freeze the entire system locks up and I can't switch to a terminal or anything to do anything. 

I'm using a Gateway M460XL Laptop. My fglrxinfo when not running Xgl gives this
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.5582 (8.21.7)
```

I followed the full guide at the beginning, except I took out the loading of compiz and gnome-window-decorator and instead added them to a script like in the nvidia guide. I'm also using the latest universe debs.

Any ideas on the problem or the fix?

---

### Post by qrlgftrt on 2006-02-19
[QUOTE=rahmza]
```

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.5582 (8.21.7)
```
Any ideas on the problem or the fix?[/QUOTE]

Hi,
i have the same card and the same problems, on several xgl versions. if you can live without nautilus, firefox and resizing windows, you will be fine...

if there is a fix out there i would like to hear about it, too

---

### Post by guyhersh on 2006-02-19
rahmza, I'm having the same problem.  Some times freezes at login, sometimes DURING login.  If I do get in it also freezes usually when I start Firefox, and ALWAYS when I click the Exit door shut down icon in the upper right.

Note: I'm using a mobility Radeon x700

Note #2: I'm getting really pissed cuz I cant enjoy the effects on my Desktop OR Laptop.  Desktop has x850xt which doesnt work with proprietary fglrx driver (even though release notes say so, many other people have this problem), and now my laptop's video card freezes.

I'm not very happy with ATi ATM..

---

### Post by Kevin on 2006-02-20
Well you had me scared there with the warning about Mobility users, since after using it for a while on nVidia on my desktop, I can't go without it :) But it works flawlessly on my mobility radeon 9600 (the laptop is a Gateway m505)

Everything except videos at anything other than 100% scaling... is there a solution to that yet?

---

### Post by zachtib on 2006-02-20
still getting the corrupted screen when i start compiz, ati m9000

---

### Post by zasf on 2006-02-20
[QUOTE=qrlgftrt]if you can live without nautilus, firefox and **resizing** windows, you will be fine...[/QUOTE]

Have you tried to run compiz without the resize plugin enabled?

It's just a hint, I experience the same problems, but had very few time to test it myself.

---

### Post by Roybotnik on 2006-02-20
Hi,
I got xgl and compiz working great on my 9600 mobility after following this guide(thanks!!), but I'm noticing a couple problems and wondering if these are normal.

When I start an app, there is no animation aside from a laggy black outline of the window shooting up, and in order to run compiz I have to use sudo.

Anyone have a clue how to fix these problems?  Dunno if these are just known bugs, but thanks for your help =)

---

### Post by Vinterstum on 2006-02-20
Hiya guys,

A couple of things to try if you're having problems:

If 3D acceleration doesn't work but there's no error messages (and fglrxinfo displays ATI), try doing:

export LIBGL_DEBUG=verbose
glxgears

And see if there are any error messages printed out. In my case (Breezy-updated Dapper, with messed up fglrx), I had to copy fglrx_dri.o from something like /usr/share/dri to /usr/X11R6/lib/dri. I don't remember the exact paths, but if there is a complaining error message, you'll figure it out :)


Secondly:
The recipe in the first post didn't work for me (X300 Mobility).
What did work:

*Create an init file somewhere. Say, /usr/bin/startxgl.sh. The init file should be executable, and contain something like:
```

#!/bin/bash

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:fbo & sleep 2 && DISPLAY=:1 gnome-session

```


*Create a file called /usr/share/xsessions/xgl.desktop, containing:
```
[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/path/to/init/file/here
Icon=
Type=Application

```

You still need to start compiz and gnome-window-decorator yourself at some point (for example using the method in the original post).

Oh, the above will basically make Xgl appear as a Session option on the login screen (where you select between GNOME, KDE, etc).

EDIT: Updated info after a bit more testing.

---

### Post by qrlgftrt on 2006-02-20
[QUOTE=zasf]Have you tried to run compiz without the resize plugin enabled?

It's just a hint, I experience the same problems, but had very few time to test it myself.[/QUOTE]

yes, it did not work very well. I don't remember exactly, but either it kept crashing on resizing or I couldn't resize at all. For now, I'm just updating xgl time after time and wait for the bugs to disappear

---

### Post by Roybotnik on 2006-02-20
I just installed the compiz update that came out today, and now gnome-window-decorator doesn't work =O.  Compiz still works but since there arent any window decorations it's kinda useless =X.

---

### Post by locohijo on 2006-02-20
> Hey, forgive me if this problem has been stated here already, but I can't seem to find any information on it. Whenever I use Xgl, it will freeze when opening some programs. Sometimes it happens on gdm before I can even enter a login. Sometimes it will go log all the way in and then freeze when opening a program (firefox oftentimes does it). When it does freeze the entire system locks up and I can't switch to a terminal or anything to do anything.

I do also experienced the same with my X600, but it seems that the problem just happened lately after some updates as when I first configured XGL on it, I was able to play for almost about 5 hrs without any problem before I shut down my machine.  

I did tried disabling compiz and then used metacity but still I encountered the same problem, I don't believe that there were any recent upgrades to the fglrx driver.  Could it be caused by XGL? or fglrx? or both? :-k 

I'll try a fresh install of Flight 4 tomorrow morning and will see how things will get by.

---

### Post by baddduh on 2006-02-20
I have glx and compiz installed and everything works fine.
I only don't know how I can make windows transprant and also don't know how I can adapt the percentage en the size of the shade under the windows, can someone explain this to me?

---

### Post by zafar on 2006-02-20
[QUOTE=Roybotnik]I just installed the compiz update that came out today, and now gnome-window-decorator doesn't work =O.  Compiz still works but since there arent any window decorations it's kinda useless =X.[/QUOTE]

```
sudo apt-get install compiz-gnome
```

They apparently seperated the decorators into compiz-kde and compiz-gnome.

---

### Post by fangorious on 2006-02-20
Still with todays compiz update I still don't have any gconf keys. I tried running it manually without the gconf plugin, but I sitll got the error about 

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

I'm using an Ati Mobility FireGL v5000 with the binary fglrx drivers v 8.22.5 installed using mlomker's HOWTO which works fine without the xgl/compiz stuff. When I try running the xgl+compiz stuff, I don't get a window manager or nautilus. Yesterday I didn't even get a panel, so it's improving, but still not really usable. For me.

---

### Post by DeeZiD on 2006-02-20
@fangorious:
As an ATi-user you should start compiz on screen 1.

DISPLAY=:1 compiz --replace .........


regards Dennis

---

### Post by superm1 on 2006-02-20
[quote=fangorious]Still with todays compiz update I still don't have any gconf keys. I tried running it manually without the gconf plugin, but I sitll got the error about 

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

I'm using an Ati Mobility FireGL v5000 with the binary fglrx drivers v 8.22.5 installed using mlomker's HOWTO which works fine without the xgl/compiz stuff. When I try running the xgl+compiz stuff, I don't get a window manager or nautilus. Yesterday I didn't even get a panel, so it's improving, but still not really usable. For me.[/quote] Using xorg-driver-fglrx from the ATI release doesn't add a certain symlink that a lot of people are missing.
```

sudo ln -s /usr/share/fglrx/diversions/libGL.so.1.2 /usr/lib/fglrx/libGL.so.1.2.xlibmesa
```

---

### Post by fangorious on 2006-02-20
> 
Using xorg-driver-fglrx from the ATI release doesn't add a certain symlink that a lot of people are missing.
```
sudo ln -s /usr/share/fglrx/diversions/libGL.so.1.2 /usr/lib/fglrx/libGL.so.1.2.xlibmesa
```


That at least got nautilus working so I now have a desktop drawn and get a context menu from right-clicking on it. But I still don't get a window manager :(

> 
As an ATi-user you should start compiz on screen 1.

DISPLAY=:1 compiz --replace .........


I thought the error indicated that it tried display 1 and couldn't find a useable screen. I tried updating the startup command in gnome-session-properties to include the --display flag (I don't use the gconf option because I don't have any gconf keys for compiz). Speaking of which, no matter what order I enter startup programs, it always reorders them. they're not alphabetical, but it reorders them the same order every time. See the screenshot for details.

```

compiz --replace --display :1 decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher

```

That didn't help. So after in a gnome-terminal I did this 

```

[justin@justinxp ~]
$ pidof compiz
[justin@justinxp ~]
$ pidof gnome-window-decorator
5093
[justin@justinxp ~]
$ pkill gnome-window-decorator
[justin@justinxp ~]
$ pidof gnome-window-decorator
5093
[justin@justinxp ~]
$ kill -9 5093
[justin@justinxp ~]
$ killall gnome-window-decorator
gnome-window-decorator: no process killed
[justin@justinxp ~]
$ gnome-window-decorator

[1]+  Stopped                 gnome-window-decorator
[justin@justinxp ~]
$ bg
[1]+ gnome-window-decorator &
[justin@justinxp ~]
$ compiz --replace --display :1 gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
[justin@justinxp ~]
$ compiz.real: Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1

[justin@justinxp ~]
$ DISPLAY=:1 --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
bash: --replace: command not found
[justin@justinxp ~]
$
[justin@justinxp ~]
$ DISPLAY=:1 compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
[justin@justinxp ~]
$ compiz.real: Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1

[justin@justinxp ~]
$ DISPLAY=:1 compiz --replace  decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
[justin@justinxp ~]
$ compiz.real: Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1

[justin@justinxp ~]
$ pidof compiz
[justin@justinxp ~]
$ pidof gnome-window-decorator
5218

```

---

### Post by jwolf on 2006-02-20
[QUOTE=superm1]Using xorg-driver-fglrx from the ATI release doesn't add a certain symlink that a lot of people are missing.
```

sudo ln -s /usr/share/fglrx/diversions/libGL.so.1.2 /usr/lib/fglrx/libGL.so.1.2.xlibmesa
```[/QUOTE]


Thank you this helped enormously. I've now got gnome up and running without corrupting the display, however, I now realize why things are running so choppy. 
```

$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Well, now I know why things are going so slow. Under X without Xgl, I have no trouble running fglrx (e.g. it displays ATI as the vendor string). What might be changing when moving to Xgl?

---

### Post by born_confused on 2006-02-20
rather than --display isnt it supposed to be

DISPLAY=:1 compiz blah blah blah

---

### Post by franzrogar on 2006-02-20
Hi all,

After trying 1.001 times with 1.002 different methods, the only one that worked for me is [this](http://www.ubuntuforums.org/showpost.php?p=753120&postcount=228). I can load Gnome over Xgl :D 

My system:
ATI RADEON 9200 RV280 128DDR
xorg fglrx
All debs needed are from universe repo.

But (always there's a *but* :cry:  ) I've the following problems:

- Xgl server loads fine (with Gnome) but it's so *s l o w* Any chance to speed it up?
- When I try to load Compiz I get a nice *black* screen (but I can see the cursor :-k and interact with *hidden* stuff but I can't see it :???: ) No matter how many options I selected :-? 

The Xorg.0 says nothing interesting:
```

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
         for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON 9200 (RV280 5961) found
(WW) fglrx(0): board is an unkown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported:8
(II) fglrx(0): Acceleration enabled

```

I've configured the screen to 1.

Any idea?

---

### Post by oelph on 2006-02-20
[QUOTE=jwolf]
```

$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Well, now I know why things are going so slow. Under X without Xgl, I have no trouble running fglrx (e.g. it displays ATI as the vendor string). What might be changing when moving to Xgl?[/QUOTE]

Its a real shame that we haven't cracked this yet :(  So many people seem to be stuck on this one.

---

### Post by fangorious on 2006-02-20
**born_confused**
> 
rather than --display isnt it supposed to be

DISPLAY=:1 compiz blah blah blah


I tried that in a terminal, scroll down the last code chunk in my post for all the commands I tried, no help. 

I setup /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom just like the first post says.

---

### Post by d3x7r0 on 2006-02-20
[QUOTE=oelph]Its a real shame that we haven't cracked this yet :(  So many people seem to be stuck on this one.[/QUOTE]
I've been looking into the issue and it looks like the module fglxr_agp is failing to load at boot and that is making dri fail... I've tried to load agpgart, ati-agp, via-agp... you name it. Yet nothing seemed to help :(

I've looked arround the rage3D foruns and a few of these issues have been raised over time and most have been fixed by simply reeinstalling the system or the driver but I can't get it to work...

If anyone wants more info to try and sort it out feel free to ask :cry:

---

### Post by bencrouse on 2006-02-20
im getting the same problem as jwolf, using the latest fgrlx drivers from ati's site and a 9700 radeon.  whenever im using Xorg without Xgl, my fglrxinfo output is the ATI string, whenever I enter Xorg with Xgl, I get the MESA stuff, and its really slow.  Anybody have a hint on what's causing this?
Thanks
ben

EDIT: So this is a bug?

---

### Post by d3x7r0 on 2006-02-20
[QUOTE=bencrouse]im getting the same problem as jwolf, using the latest fgrlx drivers from ati's site and a 9700 radeon.  whenever im using Xorg without Xgl, my fglrxinfo output is the ATI string, whenever I enter Xorg with Xgl, I get the MESA stuff, and its really slow.  Anybody have a hint on what's causing this?
Thanks
ben

EDIT: So this is a bug?[/QUOTE]
It's meant to be that way, it looks like xgl is hard coded into mesa so it will report mesa when running... Our problem is it's reporting mesa when xgl is NOT running... :(

---

### Post by bencrouse on 2006-02-20
wait...are you sure?

jwolf is reporting the same problem:

> Well, now I know why things are going so slow. Under X without Xgl, I have no trouble running fglrx (e.g. it displays ATI as the vendor string). What might be changing when moving to Xgl?

---

### Post by sephiroth_4 on 2006-02-20
[QUOTE=sephiroth_4]NOooooo....  I'm gonna try to do some damage, if that doesn't work I'm starting over.
If I come up with anything...I'll be glad to post.[/QUOTE]

My install with a x600 in my HP zd8000 beasty lappy failed miserably...

I started over and with an nvidia card (el cheapo 6600GT in an old p4 tower) and loaded it without any problems.  
poor ati....

---

### Post by Fedup on 2006-02-20
What happened to glitz?
I now get
```
paul@flight4:~/Desktop$ sudo apt-get install glitz
Reading package lists... Done
Building dependency tree... Done
Package glitz is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package glitz has no installation candidate

```

:-k

*EDIT* - Well - I've no idea what's going on. After a dist-upgrade Glitz still seems to be missing, but - compiz now works :) 
Yaayyyyy!!!

---

### Post by eth8686 on 2006-02-20
[QUOTE=bencrouse]im getting the same problem as jwolf, using the latest fgrlx drivers from ati's site and a 9700 radeon.  whenever im using Xorg without Xgl, my fglrxinfo output is the ATI string, whenever I enter Xorg with Xgl, I get the MESA stuff, and its really slow.  Anybody have a hint on what's causing this?
Thanks
ben

EDIT: So this is a bug?[/QUOTE]
I've got a 9700Pro and am using the fglrx driver from the repos (xorg-driver-fglrx) and it's working very well! fglrxinfo does show Mesa but it still is really fast and nice! :D

Try installing the repo fglrx driver, maybe that might help!

---

### Post by jwolf on 2006-02-20
[QUOTE=d3x7r0]It's meant to be that way, it looks like xgl is hard coded into mesa so it will report mesa when running... Our problem is it's reporting mesa when xgl is NOT running... :([/QUOTE]


Well, that's not exactly my problem. When I am running X without xgl it *appears* that fglrx is working properly. However, when I add xgl to the mix, and then restart x, something breaks the fglrx driver. 

My guess is that it is tied to forcing xgl to run on display :1 as opposed to :0. I would guess that perhaps something is hardcoded in xgl that requires operation on display :0. On the other hand, I could just be guessing. 

Hopefully, this problem is resolved with the next ati driver release.

---

### Post by Fedup on 2006-02-20
Arrrrgh! 
I reboot after playing with Compiz for a few hours, and now get

```
paul@flight4:~$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

again. I thought things where going too easily (for a change) :rolleyes: 

...Excuse me for a while whilst I kick my computer down the stairs :mad: :mad:

---

### Post by concept10 on 2006-02-20
[QUOTE=oelph]Its a real shame that we haven't cracked this yet :(  So many people seem to be stuck on this one.[/QUOTE]

I don't know how relevant this could be to this issue, but here's something I found while debugging my problems a couple of days ago.

First off, some history: I attempted to install the proprietary "fglrx" ATI drivers from Seveas' repository to replace the original "ati" binary drivers that are installed by default.  The driver worked, but video was not normal at all, I traced the problem to DRI (Direct Rendering).  

My laptop has this graphics chipset (from lspci): 0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

I could not find any information anywhere stating that this chipset was supported by the "fglrx" drivers.

Using this page [http://dri.freedesktop.org/wiki/DriTroubleshooting#head-fd0412cece2b6aa5b7c6ee47f228c402787a8a57]("http://dri.freedesktop.org/wiki/DriTroubleshooting#head-fd0412cece2b6aa5b7c6ee47f228c402787a8a57")

I was able to put my system back together again, getting off the Mesa software rendering stuff and back on DRI.  I basically made a symlink to fix my system.

That page takes paitence, but pay attention to the Userspace section.

Here it is if you don't want to go there:

**Userspace setup**

Next, look at a GL program. Set the environment variable LIBGL_DEBUG to verbose, i.e. setenv LIBGL_DEBUG verbose for csh-based shells or export LIBGL_DEBUG=verbose for bash-based shells. Run glxinfo, which should be included with X.Org. At the top it should show libGL trying to load the driver-specific hardware rendering library, like:

libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/radeon_dri.so.

If it isn't doing that, you have replaced your X.Org-provided libGL with some other libGL, or it's finding an old libGL from somewhere. Run ldd /usr/X11R6/bin/glxinfo and see which libGL it's finding. Make sure it's the one in /usr/X11R6/lib/libGL, or a link in /usr/lib to the one in /usr/X11R6/lib. You shouldn't have any libMesaGL* on your system.

If the driver complains about unresolved symbols:

libGL error: dlopen /usr/X11R6/lib/modules/dri/radeon_dri.so failed
   (/usr/X11R6/lib/modules/dri/radeon_dri.so: undefined symbol: _glapi_noop_enable_warnings)

then your libGL is out of sync with your DRI drivers. Because APIs change, you typically need a libGL from the latest X.Org release to run DRI drivers, and sometimes you need a libGL from X.Org CVS for the latest drivers. Reinstall both your drivers and your libGL from sources from the same date.

If you get:

libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering

then you are trying to run as a user that doesn't have permission to use the DRI (root is the default allowed user). To let all users access the DRI, add the following section to your xorg.conf:

Section "DRI"
    Mode 0666
EndSection

If you get (the driver name may vary):

libGL error: dlopen /usr/X11R6/lib/modules/dri/r200_dri.so failed \
(libexpat.so.1 : cannot open shared object file: No such file or directory)
libGL error: unable to find driver: r200_dri.so

then make sure that you have libexpat.so.1 installed. Binary snapshots now come with a statically linked libexpat, so this should no longer be a problem.

If you get (the driver name may vary):

libGL error: dlopen /usr/X11R6/lib/modules/dri/r200_dri.so failed \
(r200_dri.so : cannot open shared object file: No such file or directory)

then make sure you have compiled the appropriate dri module for your card. It it could be either in a separate file (r200_dri.so in this case), or bundled in libGL.so. Edit xc/config/cf/host.def and make sure you list at least your driver (if not all available) in a line:\ \

#define BuildXF86DRI YES
/* 2D accel drivers are: ati mga glint s3virge sis savage nv tga rendition tdfx vga i810 sunffb sunleo suncg6 suncg3 suncg14 suntcx */
#define XF86CardDrivers ati
/* the next line DriDrivers defines dri modules. Valid choices: gamma i810 i915 mach64 mga r128 radeon r200 tdfx savage sis ffb
   ati is not a valid DriDriver name. For new Radeon cards use r200 instead. */
#define DriDrivers radeon r200

If you have a 3dfx card and it's complaining about libglide3, or there are glide errors, you need to install the correct glide for your card as provided by your distribution.

If you are using a radeon and it complains about the module versions and maybe fails on an assertion, you need to update your DRM as in the instructions above.

If you've made it this far, glxinfo should be printing direct rendering: Yes and direct rendering for native GL programs should be working. Make sure that you are running at reasonable settings for your card, and maybe adjust your expectations of speed.

If you are experiencing trouble using GL with any program, maybe setting more [WWW]environment variables may help you.

---

### Post by KOnsumer on 2006-02-20
```
~$ DISPLAY=:1 glxinfo
name of display: :1.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  0  0  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  0  0  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  0  0  0 24  8  0  0  0  0  1 0 None
0x2f 32 tc  0 32  0 r  .  .  8  8  0  0  0  0  0  0  0  0  0  1 0 None
~$

```
What is wrong? What can i do?

---

### Post by fluxin on 2006-02-20
JWolf: it's slow when you login, but what happens when you start 
gnome-window-decorator & compiz --replace gconf? 
It should be slow until you start those.

---

### Post by Tea on 2006-02-20
Hi,

Im using a ATI 7500. Will it be possible to get this to workm on this old a video card? The rest of my system is decent (1.6Pm, 512mb). 

Thanks.

---

### Post by Fedup on 2006-02-20
*oops*.

---

### Post by Fedup on 2006-02-20
*double post*

---

### Post by Fedup on 2006-02-20
It gets stranger and stranger... after threatening the PC with a clean format and reinstall of Windows I backtracked my steps somewhat, uninstall KDM and went back to GDM... and compiz is working again :eek: 

Not sure if its a path issue or if KDM is broken (I noticed a while back that using KDM to log in makes all the fonts too small in KDE using the NVidia drivers), but at least things are working again for me.

Now, all I need to figure out it how to get compiz working correctly with KDE and I'm happy.. wish me luck - I feel I may need it.

---

### Post by Lars A E on 2006-02-20
[QUOTE=locohijo]I do also experienced the same with my X600, but it seems that the problem just happened lately after some updates as when I first configured XGL on it, I was able to play for almost about 5 hrs without any problem before I shut down my machine.  

I did tried disabling compiz and then used metacity but still I encountered the same problem, I don't believe that there were any recent upgrades to the fglrx driver.  Could it be caused by XGL? or fglrx? or both? :-k 

I'll try a fresh install of Flight 4 tomorrow morning and will see how things will get by.[/QUOTE]
I also have the probblem with hard lock ups. A few small gnome applications will open, but once I start evolution, nautilus or other larger apps, the system freezes. 
Hopefully someone will figure this one out too :)

---

### Post by guyhersh on 2006-02-20
fangorious

I'm having the exact same problem as you know.  I had Xgl working with the fglrx from the ubuntu repository, but it froze often.  So I updated to the latest fglrx drivers from ati, and I get these Diagonal distortions, and no Xgl effects.

At first the desktop wouldn't fully load, and then I did that libGL.so thing like you did, and the desktop loaded, but theres no windows around the programs, and no Xgl effects.

Sooo until we get a fix for the lastest ati drivers, try reverting to the ubuntu fglrx drivers in the meantime for Xgl to work.

Also, with the old drivers with working Xgl AND new drivers where Xgl doesnt work, when I ran fglrxinfo on display1, it said it was using Mesa drivers, so I don't think that is really a problem.

Hit me up on AIM if anyone has any ideas or wants to troubleshoot @ GuyHersh.


Guy

---

### Post by EstevaoSoares on 2006-02-20
Hi Folks...


I'm in a terrible disaster here with xgl. 

The install was ok, no major problems, no errors, gconf-editor reconize compiz perfect. 

I`ve instaled all required debs plus gnome-compiz , all from repo. 
I'm using fglrx driver from the Repo, not ATI. 

I did this on a fresh Flight 4 install... 

After install, I reboot, GDM starts fine, when I enter with login/pass the system halts... freezes. 
I have no clue what to do? 

Someone could please, helpe on that?

Thanks a lot !

---

### Post by guyhersh on 2006-02-20
[QUOTE=EstevaoSoares]Hi Folks...


I'm in a terrible disaster here with xgl. 

The install was ok, no major problems, no errors, gconf-editor reconize compiz perfect. 

I`ve instaled all required debs plus gnome-compiz , all from repo. 
I'm using fglrx driver from the Repo, not ATI. 

I did this on a fresh Flight 4 install... 

After install, I reboot, GDM starts fine, when I enter with login/pass the system halts... freezes. 
I have no clue what to do? 

Someone could please, helpe on that?

Thanks a lot ![/QUOTE]

Mine froze during login often too, probably 2/5 times I get passed login without it freezing.  This was when I used the ATi drivers from repo.  Now I have drivers from ATi, and it doesn't freeze as often, but Xgl doesn't work worth crap.

Xgl is alpha, Dapper is alpha, there is gonna be problems, got to accept it.

Guy

---

### Post by Vinterstum on 2006-02-20
[QUOTE=EstevaoSoares]Hi Folks...


I'm in a terrible disaster here with xgl. 

The install was ok, no major problems, no errors, gconf-editor reconize compiz perfect. 

I`ve instaled all required debs plus gnome-compiz , all from repo. 
I'm using fglrx driver from the Repo, not ATI. 

I did this on a fresh Flight 4 install... 

After install, I reboot, GDM starts fine, when I enter with login/pass the system halts... freezes. 
I have no clue what to do? 

Someone could please, helpe on that?

Thanks a lot ![/QUOTE]


That was the exact same problem I had. Which I solved using the method I posted about three pages back.

---

### Post by DanVarga on 2006-02-20
I am having problems with getting gconf-editor to recognize compiz.  Anyone know of a fix?

---

### Post by jwolf on 2006-02-20
[QUOTE=fluxin]JWolf: it's slow when you login, but what happens when you start 
gnome-window-decorator & compiz --replace gconf? 
It should be slow until you start those.[/QUOTE]

Actually, I have narrowed my problem down to compiz itself. I can start X+Xgl now and have it run (albeit without a window manager), but as soon as I try to start compiz, the entire screen becomes garbled.

This is solved by switching to a console and executing a sudo killall compiz.real, which restores my desktop. 

Any ideas why compiz is freaking out? I'm so close to figuring this out, it's frustrating the heck out of me!

---

### Post by jwolf on 2006-02-20
[QUOTE=DanVarga]I am having problems with getting gconf-editor to recognize compiz.  Anyone know of a fix?[/QUOTE]

I am pretty sure compiz needs to run successfully at least once before it appears in the menu (at least that was the case for me).

---

### Post by xavatar on 2006-02-20
Yeahie i got mine working in less than an hour...
However after half an hour I crashed down, and it seems to have some troubles with my version of fglrx (kernel 2.6.15-14). So where to report bugs ??

BTW if you don't want to mess with gdm, you can create xserverrc and run xserver from a tty as root
```
$echo "/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo" > .xserverrc
```

It's nice, the exposé-like features are so cool! but i couldn't find what they call the "super" key ... as i am using a french keyboard... Any clues on this ?

---

### Post by Hobbes on 2006-02-20
Well I am in the same boat as a few people seem to be. When I run Xgl by adding the lines to my gdm.conf and gdm.conf-custom, I will login and everything crawwwls along.  but if I get out and get back into to a normal xserver, everything is fine.  I looked back a few pages and couldn't find any reason for this, it could be somewhere in the middle of the 27 pages and I missed it,  if so a link or even page # would be great.

BTW I'm using 9800 pro, fglrx driver (from repo), and my roomate has a stupid 6600 gt and is spinning his cube in my face :)

Regards.

P.S. **xavatar**, the super key is the "windows" key at least on english keyboards, otherwise u can change the shortcut.

---

### Post by Rob2687 on 2006-02-20
The Super key is the Windows Start button.

---

### Post by EstevaoSoares on 2006-02-20
[QUOTE=Vinterstum]That was the exact same problem I had. Which I solved using the method I posted about three pages back.[/QUOTE]



Sorry about my dumbness but I did everything you wrote and even this way I couldn't realize what to do. 

After all that steps I suppose to get xgl working after my next boot (or restarting gdm) ? 



Many thanks !

---

### Post by guyhersh on 2006-02-20
[QUOTE=Vinterstum]Hiya guys,

A couple of things to try if you're having problems:

If 3D acceleration doesn't work but there's no error messages (and fglrxinfo displays ATI), try doing:

export LIBGL_DEBUG=verbose
glxgears

And see if there are any error messages printed out. In my case (Breezy-updated Dapper, with messed up fglrx), I had to copy fglrx_dri.o from something like /usr/share/dri to /usr/X11R6/lib/dri. I don't remember the exact paths, but if there is a complaining error message, you'll figure it out :)


Secondly:
The recipe in the first post didn't work for me (X300 Mobility).
What did work:

*Create an init file somewhere. Say, /usr/bin/startxgl.sh. The init file should be executable, and contain something like:
```

#!/bin/bash

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:fbo & sleep 2 && DISPLAY=:1 gnome-session

```


*Create a file called /usr/share/xsessions/xgl.desktop, containing:
```
[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/path/to/init/file/here
Icon=
Type=Application

```

You still need to start compiz and gnome-window-decorator yourself at some point (for example using the method in the original post).

Oh, the above will basically make Xgl appear as a Session option on the login screen (where you select between GNOME, KDE, etc).

EDIT: Updated info after a bit more testing.[/QUOTE]


THIS GUIDE WORKS GREAT!!! 

Xgl worked okay with the fglrx from the Ubuntu repo, then I upgraded to the latest ATi drivers to see if it helped at all, and Xgl was all screwed up, so I decided to follow this guide.

Not only did it get rid of *some* of my freezing problems, windows not displaying, display corruption, and many other problems, I can CHOOSE whether I want my session to be default Gnome OR Xgl.

ANYONE having problems, undo the edits that you made to gdm.conf and gdm.conf-custom and try this guide. (Make sure you do everything else listed on the front page)

Also, to make the startxgl.sh executable, use this after you create the file :
```

chmod 755 /usr/bin/startxgl.sh

```

But yah, works great. Thanks!

Guy

---

### Post by xavatar on 2006-02-21
I've got a trouble with that way of launching xgl
It should be run as root but launched from gdm it runs as normal user

I can put a nopasswd sudo but that does not really satisfy me

Any idea ?

---

### Post by Vinterstum on 2006-02-21
[QUOTE=EstevaoSoares]Sorry about my dumbness but I did everything you wrote and even this way I couldn't realize what to do. 

After all that steps I suppose to get xgl working after my next boot (or restarting gdm) ? 



Many thanks ![/QUOTE]

After you've done this, you should be able to go to the Login screen (gdm), click Options down in the left corner, click Choose Session and then select 'Xgl' :)

[quote=guyhersh]But yah, works great. Thanks!

Guy[/quote]

No problem :)

[quote=xavatar]
I've got a trouble with that way of launching xgl
It should be run as root but launched from gdm it runs as normal user

I can put a nopasswd sudo but that does not really satisfy me

Any idea ?[/quote]

Uhm Xgl doesn't have to be run by root, just by your normal user.

---

### Post by danmagicman7 on 2006-02-21
Alright, here is my...story.

Basically, the past 3 days I have spent trying to get a consistent pattern of getting fglrx drivers to work.  I found a good guide, reinstalled xorg, and everything would work.

Once I started to do *any* xgl stuff, upon reboot, fglrxinfo would bring up nothing errors that it couldn't find the current view, and I would have no hardware accelleration.  So, Cntrl+Alt+F1 I go, and I learned that the sudo dpkg-reconfigure xserver-xorg command then a startx would bring everything happily running in 3D acceleration.  Problem is, whenever I did a startx, I wasn't in XGL, I was just in plain ol' Xwindows.

So, I was pulling my hair out thinking I *was* in xgl after I did the xorg reconfigure and startx, when I was in fact not in it after all.  No wonder the compiz stuff wouldn't work!

Anyone else having the same dillema?

---

### Post by Entity on 2006-02-21
[QUOTE=sephiroth_4]ok...I hate to do this...
BUT
in the gconf-editor, i don't have the compiz in apps.  I ran the app as mentioned on page 16, but to no avail.  The services did start up though in the current session I am assuming since it's now listed there.

When Compiz with all options is run, I get compiz.real: No composite extension and then nothing happens.[/QUOTE]

I get the same problem here on a Powerbook G4 17" with ATI 9600 Pro using the radeon driver (*compiz.real: No composite extension*).

I also don't have compiz in gconf neither.

---

### Post by Vinterstum on 2006-02-21
[QUOTE=Entity]I get the same problem here on a Powerbook G4 17" with ATI 9600 Pro using the radeon driver (*compiz.real: No composite extension*).

I also don't have compiz in gconf neither.[/QUOTE]

Compiz needs to run successfully to add them, it seems.
That error message, from what I've been able to gather, just means that Xgl isn't currently running.

---

### Post by danmagicman7 on 2006-02-21
There's a fix for the no composite extension in the Nvidia guide.

---

### Post by Hobbes on 2006-02-21
Wow, doing the method above:

> 
*Create an init file somewhere. Say, /usr/bin/startxgl.sh. The init file should be executable, and contain something like:
```

#!/bin/bash Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:fbo & sleep 2 && DISPLAY=:1 gnome-session

```

*Create a file called /usr/share/xsessions/xgl.desktop, containing:
```

[Desktop Entry] Encoding=UTF-8 Name=XGl Exec=/path/to/init/file/here Icon= Type=Application

```

You still need to start compiz and gnome-window-decorator yourself at some point (for example using the method in the original post).

Oh, the above will basically make Xgl appear as a Session option on the login screen (where you select between GNOME, KDE, etc).


Fixed my problems.  By the way the infamous No composite extension found error, at least for me, was caused when I was trying to run compiz when I wasn't actually in Xgl.  You do not need to add the composite section listed elsewhere to your X.org.  That will make the error message go away but doesn't actually fix the problem.

And like people have been saying, running compiz successfully once (try just compiz --replace    first) will add the setting to your gconf, access it and add plugins listed in order at beginning of this thread, and that is how I at least got it all to run.

Also a bug mentioned somewhere else is that the wobbly effect glitches if you are not a refresh rate of 60 Hz, either switch to that refresh rate or add a system monitor to your gnome panel and change its settings to an update interval of 50 ms. (this will have the added bonus of you being able to see how xgl doesn't tax you're cpu!)

Thanks everyone!

P.S. can somebody remind me what the actual code and quote tags are so I can edit this post and fix them :)

---

### Post by guyhersh on 2006-02-21
they are "[Quote]" and "[code]"

Theres little buttons on the top when you create the message

---

### Post by DrSturgeon on 2006-02-21
Success!  At least partly...

I highly recommend the above method of creating a seperate session (selectable from gdm login) to run XGL--it makes debugging a lot less of a headache.

If compiz won't start (for me it was the error about two non-something textures), make absolutely sure the versions of the xorg fglrx driver and the fglrx kernel module match.  Today my system automatically got the new xorg driver, but didn't upgrade to kernel 2.6.15-16, and they mismatched, and then fglrx stopped working.  Once that was corrected...success!

Except that every time I open an application, there's about a 50% chance that the system will hard freeze.  So it's still pretty much unusable, but it's pretty cool when it does work.

I'm assuming this is just a bug proving the unstability of an alpha release, but if not, anyone know how to fix it?

Thinkpad t43
Mobility Radeon x300

Thanks to everyone on this thread who's sharing advice and experiences.  This is why open source is so much fun :-)

---

### Post by rjtd on 2006-02-21
I cannot get this to work with ATI9200.
Any luck with this? I just get a black screen after running compiz :(

---

### Post by jecos on 2006-02-21
[QUOTE=mattisking]If you don't mind trying it out, could you do as I suggested anyway then? I'm curious about trying to get the proper gconf settings in there. On my primary PC I started with battlehorse debs and then switched to Universe as packages became available and I had no trouble... but on my lower end PC I went straight from the repositories and there are no compiz options listed at all under gconf. I will test this myself later on today after work when I'm home but that will be quite a while.[/QUOTE]

I can confirm that repository Compiz doesn't add anything to gconf, but weirdly enough it worked on my other pc fine

---

### Post by Odice on 2006-02-21
Yep, its doesn't add it. In the howto, says that i must install the "battlehorse debs" but, what are those?

---

### Post by DrSturgeon on 2006-02-21
[QUOTE=jecos]I can confirm that repository Compiz doesn't add anything to gconf, but weirdly enough it worked on my other pc fine[/QUOTE]


This is the way it seemed to work for me:  You have to start compiz once with gconf and all other plugins:

```
compiz --replace gconf and all the other plugins
```

When that works successfully, it will add the stuff to gconf for all those plugins.

---

### Post by DrSturgeon on 2006-02-21
And my guess (but it's only a guess) about all the warnings about switching from the battlehorse debs to the normal ones is that compiz will only create the gconf keys if they don't already exist.  So if battlehorse compiz created them once, normal compiz won't create them, except then the plugins are listed in a different order, so the battlehorse keys won't work with the normal compiz.

---

### Post by jwolf on 2006-02-21
[QUOTE=Odice]Yep, its doesn't add it. In the howto, says that i must install the "battlehorse debs" but, what are those?[/QUOTE]

[http://battlehorse.homelinux.net/w/Wiki.jsp?page=Xgl](http://battlehorse.homelinux.net/w/Wiki.jsp?page=Xgl)

---

### Post by EstevaoSoares on 2006-02-21
[QUOTE=Vinterstum]After you've done this, you should be able to go to the Login screen (gdm), click Options down in the left corner, click Choose Session and then select 'Xgl' :)
[/QUOTE]

Hi again... 

What I must do if I can't choose on Session? Nothing different appears there after all that steps... could point me something? 

Thanks a lot!

---

### Post by zachtib on 2006-02-21
this is exciting
after upgrading to fglrx 8.22.5 from the repos., and a 686 kernel
fglrxinfo now properly reports that it is accelerated with the fglrx driver, instead of mesa FROMWITHIN XGL

---

### Post by zachtib on 2006-02-21
however, i still cannot start compiz, radeon mobility 9000
im getting the corrupted display bug

---

### Post by Portanoo on 2006-02-21
argh **** ATI....

sorry for my English i'm poor frenchie

after upgrade of Dapper maybe 2hours ago, and install of Ati driver 8.22 Xgl and compiz are boken.

pb with the driver ATI 8.22 don't have "non power of two texture" now for me it's DON'T Buy ATI Card they are to bad with them drivers for linux.


Now i'll try a install manual of driver 6.xxx

---

### Post by Odice on 2006-02-21
Ok i did the fix founded on the battlehorse page (start xgl first and a xterm, and then start compiz) and now compiz is in the gconf, but everytime i start to login into de system, the system freeze, so i follow the alternative guida given here in the page 23 and it works, now y can enter to gnome with xgl enabled (bi the trick of using startglx.sh, and run compiz by hand), the problem is that my pc freeze when i open firefox, or dillo :( I don't know what is it (it happens even with just XGL loaded no compiz)

My Card is a Ati Radeon x700pro, and im using the fgrlx drive from the repos.

---

### Post by danios on 2006-02-21
Hallo!
I've a ati x700. i instalt all schown on the first page and after problems with compiz in gconf editor, it suddenly was listed there. and WOW it woked. But then i updated my fresh installed flight 4 with synaptic and after reboot. Nothing worked anymore :cry:  I checkt the configs and i coudn't find changes. Now i tried the whole day fixing it but it don't work!!! i can't remember which driver i had bevore which worked!? but if it will run again (and i know it must) i never update my system again.... cause i felt in love with this eyecandy...\\:D/

---

### Post by Roybotnik on 2006-02-21
Add me to the list of people having trouble with XGL and compiz with the new ATI drivers that just went on the repos today.  Go ATI.

9600 Mobility

---

### Post by macmasterxiv on 2006-02-21
[QUOTE=Roybotnik]Add me to the list of people having trouble with XGL and compiz with the new ATI drivers that just went on the repos today.  Go ATI.

9600 Mobility[/QUOTE]

I think everyone is gonna have problems because the linux-restricted package hasn't been updated so the kernel module is still at 8.21.7

---

### Post by sephiroth_4 on 2006-02-21
[QUOTE=Entity]I get the same problem here on a Powerbook G4 17" with ATI 9600 Pro using the radeon driver (*compiz.real: No composite extension*).

I also don't have compiz in gconf neither.[/QUOTE]


Sorry cheif...I've moved to the dark side with nvidia.  For testing, it just works, and for gaming the 7800 GTX is still a beast.  I would love to run my 12" pb with this stuff, but ati...pffffft, poor ati.  Tiger reigns on the pb...maybe xagl will come sooner rather than later.
Thanks for the guide again PHG!!!!!!!! This stuff is like a extra men code in contra, once you know it, you know it (for those who don't know, up up down down left right left right b a start) ;);) :-D 
Good luck!  THANKS!!!!!!!  UBUNTU FORUMS AND SUPPORT ARE THE BEST!!!!!!!!!!!!!!

---

### Post by Odice on 2006-02-21
Ive fix the problems, no i justo have random freezes.

-Download from repos the files you need.
-Do the tick on the page 23 (the one who uses xsession to launch xgl, justo have to add that you need to chmod 755 the startxgl.sh)
-Add to sessions the gnome-window-decorator, and the compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher 
-Start GDM and in option init the session with Xgl in the menu.

And tada there it is, just remember not to do the gmd.conf and stuf edition, they are not needed.

Ok, greets to all and thanks to all

---

### Post by nhwk64 on 2006-02-21
I've been having problems with Xorg going to a black screen and completely locking X, if I use the fglrx driver, and I ctrl+alt+backspace to quit X (This seems to be just a problem with the ati driver and xorg, not related to xgl etc). I searched around and other people had this problem, and it seems that something to do with the kernel agp driver is causing the issue.

Anyone else had this problem?

---

### Post by Portanoo on 2006-02-21
I will stay on breez because compiz + Xgl works fine and no surprise with a simple dist-upgrade.

Xgl is not very dependent of Xorg 7

---

### Post by macmasterxiv on 2006-02-21
Just to let people know, I've got this running on a **Radeon 7500** with the open source radeon driver. Pretty much all you have to do is follow this guide except replace all instances where the screen is changed to 1, keeping the default 0 since it doesn't have the fglrx problems. The performance is surprisingly good and the only real issue is a transparency bug. Also, make sure you are running in 24 bit color if your login screen colors are inverted/messed up.

---

### Post by anno on 2006-02-21
[QUOTE=macmasterxiv]Just to let people know, I've got this running on a **Radeon 7500** with the open source radeon driver. Pretty much all you have to do is follow this guide except replace all instances where the screen is changed to 1, keeping the default 0 since it doesn't have the fglrx problems. The performance is surprisingly good and the only real issue is a transparency bug. Also, make sure you are running in 24 bit color if your login screen colors are inverted/messed up.[/QUOTE]

That is good news. Not sure if it would work on my IGP 340M card though. Had a try yesterday, but the background kept covering the windows. If you would be kind enough to elaborate for the poor "radeon" dependent ones, i would be happy. What kind of transparency problem/bug did you have? Which howto did u use? 

Thankful and hopeful.

---

### Post by coder_cotton on 2006-02-22
[QUOTE=Hobbes]Wow, doing the method above:



Fixed my problems.  By the way the infamous No composite extension found error, at least for me, was caused when I was trying to run compiz when I wasn't actually in Xgl.  You do not need to add the composite section listed elsewhere to your X.org.  That will make the error message go away but doesn't actually fix the problem.

And like people have been saying, running compiz successfully once (try just compiz --replace    first) will add the setting to your gconf, access it and add plugins listed in order at beginning of this thread, and that is how I at least got it all to run.

Also a bug mentioned somewhere else is that the wobbly effect glitches if you are not a refresh rate of 60 Hz, either switch to that refresh rate or add a system monitor to your gnome panel and change its settings to an update interval of 50 ms. (this will have the added bonus of you being able to see how xgl doesn't tax you're cpu!)

Thanks everyone!

P.S. can somebody remind me what the actual code and quote tags are so I can edit this post and fix them :)[/QUOTE]
i'm still unable to run even "compiz --replace" without the no composite extension error.

---

### Post by Xylene on 2006-02-22
I personally can't get it going. No matter what debs I install for compiz the entries in gconf-editor don't show up. Then, someone, I don't know what I did, even after reediting the files back to their original state, XGL kept trying to run and slowed my X server down to a halt. I believe I got it back to the original state, though.

Using the fglxr ATi driver on a 9800 XT.

---

### Post by coder_cotton on 2006-02-22
[QUOTE=Xylene]I personally can't get it going. No matter what debs I install for compiz the entries in gconf-editor don't show up. Then, someone, I don't know what I did, even after reediting the files back to their original state, XGL kept trying to run and slowed my X server down to a halt. I believe I got it back to the original state, though.

Using the fglxr ATi driver on a 9800 XT.[/QUOTE]
i'm having the same problem regarding compiz entries not showing up in gconf-editor.
 
to my credit, the nvidia 6800 amd64 box right next to me is up and running xgl nicely, i just can't get past this no composite extension error.  i'm on a amd64 compaq laptop w/ the ati m200 chipset, ati drivers are accelerated fine in regular gnome session.  here's some console output...
```
jason@jason:~$ ps aux | grep Xgl
root     21349  0.0  0.5   8800  2600 ?        S    21:23   0:00 /usr/X11R6/bin/ Xgl
root     21350  0.0  2.4  14080 11092 ?        S    21:23   0:04 /usr/bin/Xorg - auth /tmp/.Xgl-auth-3qRdXt -nolisten tcp -dpms -v -s 0 :93 -terminate
jason    23688  0.0  0.1   3064   764 pts/1    S+   22:52   0:00 grep Xgl
jason@jason:~$ ps aux | grep Xgl
root     21349  0.0  0.5   8800  2600 ?        S    21:23   0:00 /usr/X11R6/bin/Xgl
root     21350  0.0  2.4  14080 11092 ?        S    21:23   0:04 /usr/bin/Xorg -auth /tmp/.Xgl-auth-3qRdXt -nolisten tcp -dpms -v -s 0 :93 -terminate
jason    23694  0.0  0.1   2932   744 pts/1    R+   22:52   0:00 grep Xgl
jason@jason:~$ compiz
compiz: No composite extension
jason@jason:~$ compiz --replace
compiz: No composite extension
jason@jason:~$ thefuture
compiz: No composite extension
jason@jason:~$ gnome-window-decorator, Failed to load shadow images

jason@jason:~$

```

---

### Post by Xylene on 2006-02-22
Hrm, apparently compiz isn't even installed!

```
root@athlon:/home/anthony/Desktop# dpkg -i compiz_0.0.3-1_i386.deb (Reading database ... 61770 files and directories currently installed.)
Preparing to replace compiz 0.0.3-1 (using compiz_0.0.3-1_i386.deb) ...
Unpacking replacement compiz ...
Setting up compiz (0.0.3-1) ...
root@athlon:/home/anthony/Desktop#

```

```
root@athlon:/home/anthony/Desktop# compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher --replace
bash: compiz: command not found
root@athlon:/home/anthony/Desktop#

```

When using the battlehorse debs I found compiz in /opt/fdo/bin/compiz but I get the error about composite then. I removed that compiz install and installed the one from the Dapper repos but it still doesn't add the entries to gconf-editor.

I also apparently don't have gnome-window-decorator nor can I install it.

---

### Post by nhwk64 on 2006-02-22
[QUOTE=coder_cotton]ii'm on a amd64 compaq laptop w/ the ati m200 chipset, ati drivers are accelerated fine in regular gnome session. [/QUOTE]

Have you updated your ati fglrx today, and does acceleration still work? I believe I was getting Xorg to run accelerated yesterday, but today after (I think) an updated xorg-driver-fglrx, my Xorg.0.log complains of kernel module version mismatches. (I'm using an ati card too, and the amd64-generic kernel)

---

### Post by Xylene on 2006-02-22
Does compiz not work with 8.22.5 or something?

---

### Post by Laterix on 2006-02-22
I managed to get this work on my laptop with Radeon 9600 mobility.... but then I broke it. :( I tried to change different window decoration, because I'm not too happy with this default semi-transparent theme. Is it even possible to use other themes with XGL+compiz? Are the window shadows part of the window-decorator?

I just reinstalled my dapper... hopefully I manage to get it back... can't live without anymore. :)

EDIT: Well, of course I doesn't work as well as before :( Everything else is fine, but there is no window decorations. Actually the command "gnome-window-decorator" doesn't even exists. What I'm missing here?

Here is what I get when I execute compiz
```

late@bumba:~$ compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher --replace
compiz.real: Couldn't load plugin 'libgconf.so'
compiz.real: Couldn't load plugin 'libmenu.so'

```

Ok, I was missing **gnome-compiz** -package. Now I have window decarations as well. Everything seems to be working now... but dare I boot this computer ever again....

Someone asked about this **Box effect** when executing a program from panel launcher. For me it really lags and that's why I disabled it. You can disable this effect with **gconf-editor**. Go **/apps/panel/global** and remove tick from **enable_animations** box.

---

### Post by Tapir on 2006-02-22
I symlinked from /etc/X11/X to the Xgl, but when i reboot i can only see a black screen and a cursor showing a clock, which remains there (probably forever).  The KDM login screen won't show.

When  run Xgl in a Window from KDE it starts properly and also compiz. 

Anyone else with the same Problem? I'm using all the debs from the universe on an ATI X600 with fglrx.

Regards,

Tapir

---

### Post by JeRa on 2006-02-22
[QUOTE=DrSturgeon]Success!  At least partly...
...
Except that every time I open an application, there's about a 50% chance that the system will hard freeze.  So it's still pretty much unusable, but it's pretty cool when it does work.

I'm assuming this is just a bug proving the unstability of an alpha release, but if not, anyone know how to fix it?

Thinkpad t43
Mobility Radeon x300
[/QUOTE]
I have the same problem, NEC Versa P550 with Mobility X300...everything works fine, but I don't even get the chance to run compiz as opening the KDE menu crashes Xgl :( I use the method described on page 23, but no luck as to this moment.

---

### Post by EstevaoSoares on 2006-02-22
[QUOTE=nhwk64]Have you updated your ati fglrx today, and does acceleration still work? I believe I was getting Xorg to run accelerated yesterday, but today after (I think) an updated xorg-driver-fglrx, my Xorg.0.log complains of kernel module version mismatches. (I'm using an ati card too, and the amd64-generic kernel)[/QUOTE]


Same for me... but it worked after a sudo apt-get dist-upgrade and a second reboot. 

Dist-upgrade on Dapper Flight4 right now will upgrade its kernel. 


See ya!

---

### Post by Vinterstum on 2006-02-22
[QUOTE=coder_cotton]i'm having the same problem regarding compiz entries not showing up in gconf-editor.
 
to my credit, the nvidia 6800 amd64 box right next to me is up and running xgl nicely, i just can't get past this no composite extension error.  i'm on a amd64 compaq laptop w/ the ati m200 chipset, ati drivers are accelerated fine in regular gnome session.  here's some console output...
...
[/QUOTE]

Xgl shouldn't be running as root, but as your regular user ('jason' in your case).

---

### Post by Vinterstum on 2006-02-22
[QUOTE=Tapir]I symlinked from /etc/X11/X to the Xgl, but when i reboot i can only see a black screen and a cursor showing a clock, which remains there (probably forever).  The KDM login screen won't show.

When  run Xgl in a Window from KDE it starts properly and also compiz. 

Anyone else with the same Problem? I'm using all the debs from the universe on an ATI X600 with fglrx.

Regards,

Tapir[/QUOTE]

Xgl isn't a replacement for the regular X server, it's -supposed- to run on top of it.

---

### Post by Roybotnik on 2006-02-22
[QUOTE=Vinterstum]Xgl isn't a replacement for the regular X server, it's -supposed- to run on top of it.[/QUOTE]

He's referring to the guide located on the Ubuntu wiki.  It says to symlink /usr/bin/Xgl to /etc/X11/X.  It doesn't work with radeons because of the fglrx problems.

---

### Post by JeRa on 2006-02-22
[QUOTE=Vinterstum]Xgl shouldn't be running as root, but as your regular user ('jason' in your case).[/QUOTE]
Vinterstum, you seem to have the exact same videocard as I have (ATI Radeon Mobility X300), did you experience any freeze problems? I have followed your instructions which lead to the same problem: my system freezes whenever I open a new window or menu.

---

### Post by seanodonnell on 2006-02-22
Anyone had any luck with an ATI MOBILITY FireGL V3200 ?

I cant get xgl to start, unless I remove dri from my xorg.conf.
If I do and then I attempt to start compiz, etc

I get the non_power bug, and no manageable screens found.

Anyone have any suggestions?

thanks

Sean

---

### Post by William the Conquerer on 2006-02-22
I've got that same card in my Thinkpad T43p (the firegl v3200) and I think I got the oss ati fglrx driver working at one time, but I just went through the steps here: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) to install fglrx drivers...  it works, BUT I do not get hardware acceleration and sudo fglrxinfo just gives me stuff about mesa...  I have not been able to get Xgl and compiz to work (I'm using kde btw and I had to apt-get install gdm and just use that to boot into Xgl) so I could boot to Xgl, but not use compiz and it was the same no manageable screens stuff...  SO, I don't know what to tell you, but I'm definitely searching for the same problem, have you found anything different?  btw, I have Load "dri" enabled in xorg.conf and it seems to work...

---

### Post by Xylene on 2006-02-22
I finally got it working on my 9800 XT. I have to run that script, thefuture for window decorations to show up, but besides that, works great.

---

### Post by twisted_steel on 2006-02-22
I got it working with my 9600 XT using the XGl session. It couldn't get the fglrx acceleration working properly until today when a kernel update fixed it.

This is on my desktop which is running Dapper.

---

### Post by frozdsolid on 2006-02-22
[QUOTE=JeRa]Vinterstum, you seem to have the exact same videocard as I have (ATI Radeon Mobility X300), did you experience any freeze problems? I have followed your instructions which lead to the same problem: my system freezes whenever I open a new window or menu.[/QUOTE]


I have a thinkpad T43 with the mobility radeon x300, and i encountered the same freeze problems when i was using self compiled packages. Mind you, I tried this with all  the day compiz was released. Have you tried it with the latest packages from the repository since dapper flight 4 was released? I'm wondering if the freezing issues have been resolved.

---

### Post by William the Conquerer on 2006-02-22
[QUOTE=twisted_steel]It couldn't get the fglrx acceleration working properly until today when a kernel update fixed it.[/QUOTE]

are you using the open source fglrx from: [http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html), were you able to just apt-get it and use the restricted modules or (and I'm not sure if this even exists) did you use the official ati fglrx driver...  was it just the kernel update or was it also a restricted modules update (that has the fglrx module).

---

### Post by zachtib on 2006-02-22
can someone tell me what this means: 

```
zach@notapowerbook:~$ export LIBGL_DEBUG=verbose
zach@notapowerbook:~$ glxgears
libGL: XF86DRIGetClientDriverName: 8.22.5 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.22.5 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0

zach@notapowerbook:~$ fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.22.5 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.22.5 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: FireMV 2400 PCI DDR Generic
OpenGL version string: 1.3.1050 (X4.3.0-8.22.5)

zach@notapowerbook:~$

```

I copied the dri drivers as iunstructed in this post: [http://ubuntuforums.org/showthread.php?p=753120&highlight=mobility#post753120](http://ubuntuforums.org/showthread.php?p=753120&highlight=mobility#post753120)
did i put them in the wrong place? where should i have copied them to?

ATI Mobility Radeon 9000, btw

---

### Post by EstevaoSoares on 2006-02-22
Hi folks!

That's more good news! 

I've got it working and.. man, it's so beautiful :D  

But I've got a big halt on system on I try to access xterm from gnome bar. If I try from gnome-menu it goes fine.


Someone knows how to get my Terminal Transparent? 

I'm so glad folks :D 


My system. 

Notebook compat V2000
Turion64 1.6
ATI Radeon Xpress 200M 128 Shared 

Good luck for everyone... I just need to learn how to manage this right now!

---

### Post by nhwk64 on 2006-02-22
Got Xgl and dri acceleration working back today with the dist-upgrade, but back to the problem I was having before:

fglrxinfo -display :1 shows
Error: couldn't find RGB GLX visual!

glxgears shows
Error: couldn't get an RGB, Double-buffered visual

grep -i glx /var/log/Xorg.1.log shows
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
(II) Loading extension GLX

Anyone have any idea? There is a bit of screen corruption happening when Xgl is running, also.


Edit: found this in my xorg log:

(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)

---

### Post by EstevaoSoares on 2006-02-22
Something I could see now is that when I minimize some window It can't be find on the bar anymore and I can't maximize it... Any Ideias?

---

### Post by eeclark on 2006-02-22
[QUOTE=mattisking]
7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order:
```
gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```
It MUST be in this order as there are dependencies between them. If you've already been playing with this from earlier debs - maybe from battlehorse, or maybe you rolled your own - this is an important step because it's very likely in the wrong order. Most people that are missing certain plugins or are missing things like "alt-switch" will find they need to correct this and restart.
[/QUOTE]

On this item you might want to clarify by stating it is actually "right click on the active_plugins key and select Edit Key..." instead of just stating "adjust 'plugins'".

---

### Post by EstevaoSoares on 2006-02-22
Guys,


Something I realize is that with the new compiz / gnome-compiz  the gconf-editor (with no compiz) problem was solved. 

In my first try with an old compiz it didn't appear on gconf-edtir even after typing compiz --replace on terminal. 
Now, with the new from repo everything was there. 

That's it. 

Good luck u folks

---

### Post by seanodonnell on 2006-02-22
> I've got that same card in my Thinkpad T43p (the firegl v3200) and I think I got the oss ati fglrx driver working at one time, but I just went through the steps here: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) to install fglrx drivers... it works, BUT I do not get hardware acceleration and sudo fglrxinfo just gives me stuff about mesa... I have not been able to get Xgl and compiz to work (I'm using kde btw and I had to apt-get install gdm and just use that to boot into Xgl) so I could boot to Xgl, but not use compiz and it was the same no manageable screens stuff... SO, I don't know what to tell you, but I'm definitely searching for the same problem, have you found anything different? btw, I have Load "dri" enabled in xorg.conf and it seems to work...

I have had mixed results on the dri/no dri thing. Depends which days updates i am on. I have gotten Xgl to start, but never gotten past the no manageable screens stuff. Im going to keep trying every few days, If I have any success I will let you know 

Sean

---

### Post by twisted_steel on 2006-02-22
[quote=William the Conquerer]are you using the open source fglrx from: [http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html]("http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html"), were you able to just apt-get it and use the restricted modules or (and I'm not sure if this even exists) did you use the official ati fglrx driver... was it just the kernel update or was it also a restricted modules update (that has the fglrx module).[/quote]

I am using the fglrx driver from the Dapper repositories.  I imagine it may have been the restricted modules update that fixed it (both the kernel and restricted modules were updated when I last ran Synaptic).

---

### Post by eeclark on 2006-02-23
```
edward@smallville:~$ glxinfo |grep rendering
direct rendering: No
```

is that normal for Xgl?

Using ATI "fglrx" driver.
Seems fast enough, though.

---

### Post by Vinterstum on 2006-02-23
[QUOTE=JeRa]Vinterstum, you seem to have the exact same videocard as I have (ATI Radeon Mobility X300), did you experience any freeze problems? I have followed your instructions which lead to the same problem: my system freezes whenever I open a new window or menu.[/QUOTE]

Yeah, I get freezes once in a while. Not as often as you do, though, no idea why :(. But often enough that I don't use Xgl normally. I chalked it down to issues with fglrx itself, so we might just have to wait it out.

---

### Post by JeRa on 2006-02-23
[QUOTE=Vinterstum]Yeah, I get freezes once in a while. Not as often as you do, though, no idea why :(. But often enough that I don't use Xgl normally. I chalked it down to issues with fglrx itself, so we might just have to wait it out.[/QUOTE]
I noticed that the fglrx driver tends to crash even when using the normal Xorg server instead of Xgl when switching between screens or logging out; hopefully ATI will release a new driver soon with bigger changes than 'fglrx is now able to read more than 22 lines from the config!!'. Quite annoying since I receive no error or warning at all; maybe AGP related?

---

### Post by Zek on 2006-02-23
> ```
edward@smallville:~$ glxinfo |grep rendering
direct rendering: No
```

is that normal for Xgl?

Using ATI "fglrx" driver.
Seems fast enough, though.

Same here :

```

nicolas@Tux:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.2 (2.0.5642 (8.22.5))
```

```
nicolas@Tux:~$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.2 (2.0.5642 (8.22.5))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon
nicolas@Tux:~$
```

No direct rendering but opengl works fine.

---

### Post by rawler on 2006-02-23
Jera, frozdsolid: I'm also on a T43 with an ATI X300 running FGLRX. For me it crashes to the extent of being unusable. A bit sad, since each time I turn on Xgl gives me a little smile on my face. :) (Until the laptop dies on me, of course ;) )

---

### Post by husher on 2006-02-23
I just wanted to confirm that this works exceedingly well on my notebook which has an ATI Mobility Radeon 9700 graphics chip.  If anyone knows of a database or list I should add this setup to, let me know.

Thanks for all the info and the hard work!

---

### Post by christophsky on 2006-02-23
Has anyone been able to get XGL+compiz to work with Mobility Radeon 9000? I can get Xglserver to run (it's very slow) but when I issue the compiz command (with options of course) my screen becomes heavily corrupted. I know others with this card have reported similar experiences. So, does anyone know of a workaround? Thanks! 

BTW, I have XGL working flawlessly on another machine with a geforce 6800. The effects are simply stunning...

---

### Post by didit on 2006-02-23
For ati 9000, you should use 'radeon' driver. For detail: 
[http://www.ubuntuforums.org/showthread.php?t=129505&page=19]("http://www.ubuntuforums.org/showthread.php?t=129505&page=19")

---

### Post by christophsky on 2006-02-23
Thanks didit. Somehow I missed that while searching.

---

### Post by macmasterxiv on 2006-02-23
[QUOTE=anno]That is good news. Not sure if it would work on my IGP 340M card though. Had a try yesterday, but the background kept covering the windows. If you would be kind enough to elaborate for the poor "radeon" dependent ones, i would be happy. What kind of transparency problem/bug did you have? Which howto did u use? 

Thankful and hopeful.[/QUOTE]

Getting **radeon** driver to work:

1.  make sure you have direct rendering enabled in glxinfo.

2.  edit the xorg.conf and make sure that GLcore is commented out, but leave dri and glx enabled in the modules section. Also make sure the **color is set for 24 bit to avoid inverted colors/corruption.**

3.  edit the gdm.conf-custom file like so: ```
[servers] 
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

** Make sure to leave the regular gdm.conf alone, default settings are fine.

Now it's the same as the fglrx howto.

4.  Modify your session ("Menu System" -> "Preferences" -> "Sessions") by adding in the following two items:
```
gnome-window-decorator (must be on top, start first)
compiz --replace gconf
```

5.  Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order:

```
gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```

The transparency bug is when the background sometimes shows thorough the windows at points.

---

### Post by oceanelement on 2006-02-23
[QUOTE=husher]I just wanted to confirm that this works exceedingly well on my notebook which has an ATI Mobility Radeon 9700 graphics chip.  If anyone knows of a database or list I should add this setup to, let me know.

Thanks for all the info and the hard work![/QUOTE]

If you could write up something on how you did it that would be greatly appreciated. I have a 9700 as well. The main problem at the for my computer is that in gconf-editor compiz is not showing up :( 

oceanelement

---

### Post by guyhersh on 2006-02-23
[QUOTE=oceanelement]If you could write up something on how you did it that would be greatly appreciated. I have a 9700 as well. The main problem at the for my computer is that in gconf-editor compiz is not showing up :( 

oceanelement[/QUOTE]

To get it to show up, be running IN Xgl (you'll probably be windowless) and run the command "compiz --replace somethin something" that is on Pg 16 of this thread.

It ONLY went into gconf-editor AFTER i ran that command WHILE i was running Xgl, then restarted.

hope that helps.

Guy

---

### Post by joflow on 2006-02-24
Trying to install...r9500

I'm having the no compriz in gconf-editor problem but the command on page 16 doesn't fix it.  It starts compiz (and I get to see all the sweet effect with no borders) but it doesn't add compiz to my gconf-editor.  Any ideas?

---

### Post by joflow on 2006-02-24
[QUOTE=joflow]Trying to install...r9500

I'm having the no compriz in gconf-editor problem but the command on page 16 doesn't fix it.  It starts compiz (and I get to see all the sweet effect with no borders) but it doesn't add compiz to my gconf-editor.  Any ideas?[/QUOTE]

When I run compiz from the terminal I also get this error:

compiz.real: Couldn't load plugin 'libmenu.so'

but as I've said...all the effects work (cube, wobbly,expose)

---

### Post by joflow on 2006-02-24
gnome-compiz fixed the problem.

---

### Post by oceanelement on 2006-02-24
Ok, I think I know *where* the problem begins. When I try to do a manual compiz command,

> $ compiz -- blah blah etc. 

the output is the following

> $ compiz.real couldn't open display 

I have the latest ATI driver and I glx is working. When I first tried to get compiz working the gconf-editor never showed compiz under apps. This problem still persists. Any suggestions? 

Oceanelement

---

### Post by joflow on 2006-02-24
[QUOTE=oceanelement]Ok, I think I know *where* the problem begins. When I try to do a manual compiz command,



the output is the following



I have the latest ATI driver and I glx is working. When I first tried to get compiz working the gconf-editor never showed compiz under apps. This problem still persists. Any suggestions? 

Oceanelement[/QUOTE]


install gnome-compiz.  Its in the repos.

---

### Post by xavatar on 2006-02-24
For those that still have problems, here are my config files


* /usr/share/xsessions/xgl.desktop:
```

[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh 1
Icon=
Type=Application

```

* /usr/bin/startxgl.sh
```

#!/bin/bash

echo ">Starting XGL at Display: $1"
echo "========= XGL ============"
Xgl -fullscreen :$1 -ac -accel xv -accel glx:pbuffer &
sleep 5

echo "======= COMPIZ ==========="
DISPLAY=:$1 LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib/ compiz --replace decoration wobbly fade switcher minimize cube rotate zoom scale move resize place &
sleep 3

echo "====== DECORATIONS ======="
DISPLAY=:$1 gnome-window-decorator &
sleep 3

echo "======= GNOME ============"
DISPLAY=:$1 setxkbmap -model pc105 -layout fr -variant basic
DISPLAY=:$1 gnome-session

#echo "======= LOGOUT ============"
#killall Xgl
# Adding the line above,if you can't logout Gnome correctly.

```

*/etc/X11/xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "extmod"

# This loads the DBE extension module.

#    Load        "dbe"   # Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
#    SubSection  "extmod"
#      Option    "omit xfree86-dga"   # don't initialise the DGA extension
#    EndSubSection

EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
    Option "ZAxisMapping"   "4 5"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
        Driver          "fglrx"

# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver$# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "(null)"
    Option "HSync2"                     "unspecified"
    Option "VRefresh2"                  "unspecified"
    Option "ScreenOverlap"              "0"
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4150
    Screen 0
EndSection

Section "Monitor"
        Identifier      "LS902U"
        Option          "DPMS"
        HorizSync       30-96
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
        Monitor         "LS902U"
        DefaultDepth    24
    #Option "backingstore"

        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Everything work great for me and i can log using GDM...
Though be sure to delete /tmp/.X1-lock before running and don't forget to
chmod a+x /usr/bin/startxgl.sh

Good luck

---

### Post by dlpfmVfH on 2006-02-24
[quote=xavatar]For those that still have problems, here are my config files


* /usr/share/xsessions/xgl.desktop:
```

[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh 1
Icon=
Type=Application

``` 
* /usr/bin/startxgl.sh
```

#!/bin/bash

echo ">Starting XGL at Display: $1"
echo "========= XGL ============"
Xgl -fullscreen :$1 -ac -accel xv -accel glx:pbuffer &
sleep 5

echo "======= COMPIZ ==========="
DISPLAY=:$1 LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib/ compiz --replace decoration wobbly fade switcher minimize cube rotate zoom scale move resize place &
sleep 3

echo "====== DECORATIONS ======="
DISPLAY=:$1 gnome-window-decorator &
sleep 3

echo "======= GNOME ============"
DISPLAY=:$1 setxkbmap -model pc105 -layout fr -variant basic
DISPLAY=:$1 gnome-session

#echo "======= LOGOUT ============"
#killall Xgl
# Adding the line above,if you can't logout Gnome correctly.

``` 

Everything work great for me and i can log using GDM...
Though be sure to delete /tmp/.X1-lock before running and don't forget to
chmod a+x /usr/bin/startxgl.sh

Good luck[/quote]

I tried it your way, because it seems easy and a good idea to have a choice .
But I can't get it working...
I get kicked back at gdm-login...

been fiddling around and I can't seem to get it working correctly..

If I start from the command line with this code:
```

#!/bin/bash
sudo killall gdm
sudo killall Xgl &
sudo killall Xorg &
wait
sleep 2
sudo /usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
DISPLAY=:1 gnome-window-decorator &
DISPLAY=:1 compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
sleep 4
DISPLAY=:1 gnome-settings-daemon &
DISPLAY=:1 gnome-panel &
DISPLAY=:1 nautilus &
sleep 8

```

It works.. but not from gdm with your files..

---

### Post by fangorious on 2006-02-24
I tried the startxgl.sh/xgl.desktop route with the Ati binary fglrx driver manually built. That crashed on login while drawing the desktop background. The gnome splash screen came and went, and I got a popup about a disk being 95% full, then the background started to display, and was immediately deformed as though a window was being dragged around and the screen was being redrawn quickly enough. Then everything froze. Mouse pointer was unresponsive, ctrl-alt-del didn't reboot, ctl-alt-backspace didn't kill X. Using the gdm.conf[-custom] route I could get gnome and gnome-window-decorator running but compiz wouldn't start, the message about not finding a manageable screen/display (yes I tried starting it with both --display and with DISPLAY=:1, no effect from either).

So I tried going with the build of the binary driver in the repos (since it's up to 8.22.5 now). The drivers work for plain old X with dri. But Xgl hangs right away using them. And I can't seem to go back to using manually built drivers. The final step of 'module-assistant a-i fglrx) to get the kernel module fails. One thing that catches my eye with the repo drivers is the version numbers seem to indicate being built against xorg 6.9.0. 

```

[justin@justinxp ~]
$ dpkg -l xorg-driver-fglrx
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  xorg-driver-fg 6.9.0-8.22.5+2 Video driver for ATI graphics accelerator

```

---

### Post by fungi on 2006-02-25
compiz and glx are running quite nicley on 9550

but..

- theme selector crashes whenevr i change wigits or icons ( but the new settins are applied )
-frozen-bubble is transparent (unless you put a black terminal behind it )
-vlc has no window borders ( alt click any where to move the window )

thanks for the how-to.

peace

---

### Post by xavatar on 2006-02-25
[QUOTE=aboe]I tried it your way, because it seems easy and a good idea to have a choice .
But I can't get it working...
I get kicked back at gdm-login...

been fiddling around and I can't seem to get it working correctly..

If I start from the command line with this code:
```

#!/bin/bash
sudo killall gdm
sudo killall Xgl &
sudo killall Xorg &
wait
sleep 2
sudo /usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
DISPLAY=:1 gnome-window-decorator &
DISPLAY=:1 compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
sleep 4
DISPLAY=:1 gnome-settings-daemon &
DISPLAY=:1 gnome-panel &
DISPLAY=:1 nautilus &
sleep 8

```

It works.. but not from gdm with your files..[/QUOTE]

Well that's strange, i've no extra repo except PLF, nothing compiled from source and it work as a charm with my radeon 9600.

Do you get an error message complaining about the session that was too short ?

xavatar

---

### Post by dlpfmVfH on 2006-02-25
yes it complaines about it.

---

### Post by zasf on 2006-02-25
[QUOTE=fangorious]```

[justin@justinxp ~]
$ dpkg -l xorg-driver-fglrx
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  xorg-driver-fg 6.9.0-8.22.5+2 Video driver for ATI graphics accelerator

```[/QUOTE]

Is newest ATI driver (8.22.5) reported to work with xgl?

---

### Post by xavatar on 2006-02-25
[QUOTE=aboe]yes it complaines about it.[/QUOTE]

Have you tried setting a longer sleep after Xgl start ?

---

### Post by dlpfmVfH on 2006-02-25
[quote=xavatar]Have you tried setting a longer sleep after Xgl start ?[/quote] 
that helped a lot...

I have renamed it a bit: startxgl-gnome

my new code looks like:
```
#!/bin/bash

echo ">Starting XGL at Display: $1"
echo "========= XGL ============"
Xgl -fullscreen :$1 -ac -accel xv:pbuffer -accel glx:pbuffer &
[COLOR=Red]sleep 6[/COLOR]

echo "======= COMPIZ ==========="
DISPLAY=:$1 LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib/ compiz --replace gconf decoration wobbly fade switcher minimize cube rotate zoom scale move resize place &
sleep 3

echo "====== DECORATIONS ======="
DISPLAY=:$1 gnome-window-decorator &
sleep 3

echo "======= GNOME ============"
DISPLAY=:$1 setxkbmap -model pc105 -layout us -variant basic
DISPLAY=:$1 gnome-session

#echo "======= LOGOUT ============"
#killall Xgl
# Adding the line above,if you can't logout Gnome correctly.
``` 

and for XFCE4 : startxgl-xfce4
```
#!/bin/bash

echo ">Starting XGL at Display: $1"
echo "========= XGL ============"
Xgl -fullscreen :$1 -ac -accel xv -accel glx:pbuffer &
sleep 6

echo "======= COMPIZ ==========="
DISPLAY=:$1 LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib/ compiz --replace gconf decoration wobbly fade switcher minimize cube rotate zoom scale move resize place &
sleep 4

echo "====== DECORATIONS ======="
DISPLAY=:$1 gnome-window-decorator &
sleep 4

echo "======= XFCE4 ============"
DISPLAY=:$1 xfce4-session

#echo "======= LOGOUT ============"
#killall Xgl
# Adding the line above,if you can't logout Gnome correctly.
``` 


All is working now.

---

### Post by giosquad on 2006-02-25
Hi folks,
 thanks to all you I  have tried Xgl and compiz after spend long time with fglrx, I tried with radeon open source driver and works for a while, seems that for my radeon 9000pro and 9000 series there is a problem with fglrx that I have and that must be corrected: 
[http://gentoo-wiki.com/XGL#Whole_distortion]("http://gentoo-wiki.com/XGL#Whole_distortion")

Have someone of you the same problem with fglrx?

Moreover there is an other strange thing with latest fglrx installed from dapper repository with restricted modules package, direct rendering is ok, but:

```

gio@kubalien:~$ export LIBGL_DEBUG=verbose
gio@kubalien:~$ fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.22.5 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.22.5 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:2:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 PRO DDR Generic
OpenGL version string: 1.3.1050 (X4.3.0-8.22.5)


```

What could I do to correct glapi fallback?

Thanks,
Giordano

---

### Post by fangorious on 2006-02-25
> 
Is newest ATI driver (8.22.5) reported to work with xgl?


A bunch of people in this thread have said they have it working with the drivers in the repos, which are at v 8.22.5.

---

### Post by dlpfmVfH on 2006-02-25
I got Xgl and compiz working with everything from the repos. 
so yes.

the repo version is: 6.90-8.22.5+2.6.15.6-1(dapper)

---

### Post by hentaidan on 2006-02-25
Working on:

ATI Radeon 9550 128mb, with all the latest from the repos.

Had no apps/compiz in gconf so tried with battlehorse instructions (using repo), but was no go, so retried with tutorial here, and compiz had appeared in gconf, but no plugins. Removed any entries from gnome-session-properties as it seems to be having problems with me atm, freezing, messing up orders. Aside from a short wait before login screen at an oldstyle black and white grid wallpaper, nothing changed so have to run: ```
gnome-window-decorator
``` and ```
sudo compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher --replace
``` after login.

Zero crashes or freezes. Lags a bit when moving windows. (No transparency). Zoom, cube, all working BEAUTIFULLY!!!

Thank-you!!! \\:D/

---

### Post by poyner on 2006-02-26
Hi all,
I've had XGL+compiz working for a while now but I still haven't managed to get any transparency love. Are others also having problems with this? If you've managed to get it working what did you do? Any assistance appreciated. 

Poyner

Edit: OK I've done a bit of playing. I have transset installed using apt-get. I can go to a terminal and type in transset .7 (for example) and then click on a window and it will set the transperancy of that window to 70%.... This is pretty cool.... but how do I get a dropdown list when right clicking on the titlebar? Or isn't this implemented properly yet?

---

### Post by oceanelement on 2006-02-26
[QUOTE=risbac]ATI AIW9600 Pro / PIV 2.8Ghz / 1Go
Dapper, Xgl from repo, fglrx driver
Xgl is running with a modified gdm.conf & -custom
I would have said quite stable, but my post was just deleted with a crash : )

To start Compiz, I had to remove "gconf" from the command line. 



If I add gconf anywhere in the command, it's failing. I don't know why. All the other plugins are working fine, be careful with the order, you can't change it the way you want, there are some dependencies (some plugins must be loaded before others).

No need of any sudo, you can forget about my previous advise.

So far, it's very smooth, I will talk about the stability after some tests.[/QUOTE]


You're move on taking out gconf worked for me as well. This maybe a good tip for others. My main symptom in the beginning with compiz was that it did not want to show up in my gconf-editor. I did two fresh installs to get compiz working. After taking the *gconf* out it worked like a charm. Now it boots up with my system \\:D/ 

oceanelement

---

### Post by lawngn0mex on 2006-02-26
I followed the steps in the fist post....


Direct Rendering is off.. can't figure out how to enable it.
fglxr I'm using from the repos.. along with xgl and compiz.

I'm just getting an insane amount of hardlocking... any suggestions on where I can look to it's souirce.. or something that people have had luck with?

Kernel 2.6.15-16-k7 


everything installed from the repos.

x800xl  pci-e

running compiz off of startup programs in gnome, along with the gnome-window-decorator

compiz decoration move resize place switcher wobbly fade minimize cube rotate zoom scale --replace

---

### Post by Athauglas on 2006-02-26
Hey all.

Has anyone tried installing this on a thinkpad?  I'm using a T43, and so far I've got nothing.

I had noticed a few things before going back to Breezy, though: 

- fglrx works well.  fglrxinfo normally reports the correct driver's in use, and the right GPU.  But, as soon as I install xgl (and make the appropriate changes to gdm.conf and .conf-custom) I get the following: "Error: unable to open display :0"  Shortly after the system will lock up, and once that happens, I cant start normally at all.

-after being installed, compiz doesn't have an entry in the gconf editor, so I cant follow the instructions to change the effects, etc.  I have no idea if this is even a problem since everything is pretty well hosed before then, and I've only gotten that far once out of half a dozen tries.

-when the system did start with xgl, there was a long pause on the old style black/white background before the login screen appeared.  When it fails, it does so the same way each time - the login screen will flash, and then a blank white screen will appear with just the cursor, and "..." where the text box would be.  At that point the system is unresponsive and has to be powered off.


So, while this is really beyond my ability, it looks like I have at least one big issue, and that is xgl isn't happy with some of the hardware hardware present.  It'd be nice to find a solution but none of the threads (including this one) cover anything like what's happening here.  I'll include some details in case someone has an idea: 

IBM Thinkpad T43, 2687-DDU
512mb system memory
Mobility X300 with 64mb dedicated mem
Pentium M 750

Everything was done on a clean install using Dapper flight 4 disc, made current using software update, switched to the 686 kernel... um.. swap partition is about 1GB.. i dunno what else might be relevant.

Thanks :)

---

### Post by eeclark on 2006-02-26
my best success was to install from Flight 4 and use the method on this thread that shows you how to create an XGl session rather than modding the gdm files.

---

### Post by palomar on 2006-02-27
[QUOTE=Athauglas]
-when the system did start with xgl, there was a long pause on the old style black/white background before the login screen appeared.  When it fails, it does so the same way each time - the login screen will flash, and then a blank white screen will appear with just the cursor, and "..." where the text box would be.  At that point the system is unresponsive and has to be powered off.
[/QUOTE]
I have the same problems with that long spause on the login screen. Also when I try command like 'fglrxinfo -display :1', 'glxinfo' or 'glxgears' there is a long pause before the command will be executed. 
Another little annoyance is when I start an application from a panel it starts slow. I don't know how to describe exactly, but I can see the window being build up from increasing black rectangles. It's only when I click icons in the panel. When I start an app. from the Gnome menu it does start quickly.

My specs:
Athlon64 2800
Radeon 9800SE
Installed Dapper and XGL/ati drivers from repository this morning, so everything is up to date.

 fglrxinfo -display :1 displays that I'm using ATI drivers. Besides the problems I mentioned above, all graphical effects are running very smoothly.

DOes anyone have a sollution for this?

---

### Post by strawman on 2006-02-27
Same on my system.  From the panel i also have those expanding lines, not from the menu.  It also appears that DRI is off but it was functioning before, maybe Xgl can't use dri.

Using Hp nc8000 laptop with mobility radeon 9600.

everything runs pretty smooth but it does use a lot more of the cpu

---

### Post by mcduck on 2006-02-27
[QUOTE=palomar]
Another little annoyance is when I start an application from a panel it starts slow. I don't know how to describe exactly, but I can see the window being build up from increasing black rectangles. It's only when I click icons in the panel. When I start an app. from the Gnome menu it does start quickly.
[/QUOTE]Open configuration editor, browse to apps/panel/global and unmark 'enable_animations'..

---

### Post by aamukahvi on 2006-02-27
palomar & strawman:

Start gconf. Navigate to /apps/panel/global. Turn off enable_animations.

ed: seems I'm too slow.

---

### Post by palomar on 2006-02-27
Thanks, that worked :)

But I have another problem: when I try an 'OpenGL'-related command like 'fglrxinfo -display :1', 'glxinfo' or 'glxgears' there is a long pause before the command will be executed. What can I try tol solve it?

Their is also still a hige delay when starting X-server. For about 30 seconds I see the ' classic'  X black-white raster with a mouse cursor in it.

---

### Post by MaZiNgA on 2006-02-27
Hi I'm using XGL with an ATI IGP 345M but the desktop is veeeeery slow and has many glitches too! Can ayone help? I'm using the "radeon" driver and 3D is enabled.

---

### Post by MeijUbuntu on 2006-02-27
Well, after lot's of frustration with my ATI X600 card, i decide to buy me a Nvidia 6600GT.

Froms scratch all works well !

It's a bad thing that ATi doesn't support and maintain there Linux drivers well.

Thnx

P.S. Who wan;t to buy a ATI X600 ??? :D :D :D

---

### Post by strawman on 2006-02-27
Hey, thanks that did the trick

---

### Post by bugmenot on 2006-02-28
Well, finally got it working with my Mobility Radeon 9700 :) 
How can i take screenshots of the 3d cube? When using the std. screenshot prog i only see the active desktop...

---

### Post by DeeZiD on 2006-02-28
You can do that with gimp or ksnapshot :)


regards Dennis

---

### Post by jsgaarde on 2006-02-28
Hi.
I have installed everything alright, and everything seems to work alright, almost :-k 
The only problem seems to be that the wobling windows don't seem to wobble finished. 
How so you ask?
Well, if i start dragging a window the window wobbles smoothly around while moving the mouse around continiously. If I suddenly hold the mouse cursor still the wobling also freezes. That doesn't look very cool at all.
Does anybody else experience the same?

Best regards 
Jakob Simon-Gaarde

---

### Post by Athropos on 2006-03-01
[QUOTE=jsgaarde]
Well, if i start dragging a window the window wobbles smoothly around while moving the mouse around continiously. If I suddenly hold the mouse cursor still the wobling also freezes. That doesn't look very cool at all.
Does anybody else experience the same?
[/QUOTE]

I experience this also. Some windows seem more subject to this, especially terminal windows. I don't have this problem with mplayer windows for example.

---

### Post by oceanelement on 2006-03-01
[QUOTE=Athropos]I experience this also. Some windows seem more subject to this, especially terminal windows. I don't have this problem with mplayer windows for example.[/QUOTE]

Im not experiencing that problem at all. It could be because I have my compiz setup slightly different than what this thread. 

Using ATI radeon 9700 mobility with compiz-gnome from repository.

I did everything this thread has suggested for the ati setup except one thing: using the hack from poofyhairyguy "thefuture" in his thread.

---

### Post by hentaidan on 2006-03-01
[QUOTE=jsgaarde]Hi.
Well, if i start dragging a window the window wobbles smoothly around while moving the mouse around continiously. If I suddenly hold the mouse cursor still the wobling also freezes. That doesn't look very cool at all.[/QUOTE]

Quoting Hobbes from earlier in the thread...:

> Also a bug mentioned somewhere else is that the wobbly effect glitches if you are not a refresh rate of 60 Hz, either switch to that refresh rate or add a system monitor to your gnome panel and change its settings to an update interval of 50 ms. (this will have the added bonus of you being able to see how xgl doesn't tax you're cpu!)

Dan

---

### Post by GazaM on 2006-03-01
Unfortunately my ATI equipped machine suffers from complete lockup/freezing with Xgl, so it's unusable for me there. I'm writing this from a PC with an old GeForce2 MX and Xgl/compiz is running rock solid. Pretty disappointing not to be able to run this on my main machine though, anybody know what's causing these lockups? I know others here have mentioned it as well. Hoping a fix is available, as I'm blown away by the effects, as are my friends and family... some of them really are good for usability, such as the window minimising effect and the zoom effect.

---

### Post by oceanelement on 2006-03-01
I just did an update and some errors came up with the error. Now the x server keeps trying to boot up with no luck. i suspect is has to do something with the way xgl is put into the system. Anyone else experiencing the same problem?

---

### Post by Lux Perpetua on 2006-03-02
[QUOTE=Athauglas]Hey all.

Has anyone tried installing this on a thinkpad?  I'm using a T43, and so far I've got nothing.
[/QUOTE]I actually installed Xgl and Compiz on my Thinkpad T43p, and it "worked." By "worked" here I mean there were about 30 minutes of bliss and drooling at the translucency and jello-like windows, but apparently I just got lucky that one time. Every other time, X locked hard before I could even log into GDM. I had to go back to X.org/Metacity to be able to use my system again. 
[QUOTE=Athauglas]
-after being installed, compiz doesn't have an entry in the gconf editor, so I cant follow the instructions to change the effects, etc.  I have no idea if this is even a problem since everything is pretty well hosed before then, and I've only gotten that far once out of half a dozen tries.
[/QUOTE]I had that problem, but there is a way to fix this. I think you need to run compiz once to add the gconf entry. I followed this: [http://battlehorse.homelinux.net/w/Wiki.jsp?page=HowToXglATI](http://battlehorse.homelinux.net/w/Wiki.jsp?page=HowToXglATI)
[QUOTE=Athauglas]
-when the system did start with xgl, there was a long pause on the old style black/white background before the login screen appeared.  When it fails, it does so the same way each time - the login screen will flash, and then a blank white screen will appear with just the cursor, and "..." where the text box would be.  At that point the system is unresponsive and has to be powered off.
[/QUOTE]
I too am acquainted with the flash and the beautiful snowy screen of icy Xgl death :-) It happened almost every time, but once it actually let me log in and mess around for a few minutes before cutting me off.

---

### Post by tukster on 2006-03-02
[QUOTE=Lux Perpetua]
I too am acquainted with the flash and the beautiful snowy screen of icy Xgl death :-) It happened almost every time, but once it actually let me log in and mess around for a few minutes before cutting me off.[/QUOTE]


same here, random lockups, even before loading windowdecorator and compiz.
can anyone help.


heres some info:

> 
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Generic
OpenGL version string: 2.0.5642 (8.22.5)


> 
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2



```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"hr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. R423 5F57 [Radeon X800XT (PCIE)]"
	Driver		"fglrx"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. R423 5F57 [Radeon X800XT (PCIE)]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by fusionfd on 2006-03-02
w00t!!!  I finally got it.  Dell 6000 with ATI X300 (128MB PCIe).  Works great, not so stable (launched Gnomebaker and it locked up hard).  I have a terminal (with a true transparent title bar) and a browser open now and its rocking.  I just ran the compiz command without the sudo or the gconf reference as stated in an earlier post.

let me know if you have question.  I'm gonna try and stablize it over the weekend and run this way full time.

wobbly windows rock.  ;-)

---

### Post by d3x7r0 on 2006-03-02
I just want to know why I can't have 3D accelerated graphics in my radeon 9600PRO :'(

I did everything right and I keep getting mesa... dsmeg keeps saying something about the agp module failing and still no acceleration... Tried loading different agp kernel modules, tried a couple of clean installs and still no go...

Damn my asus p4v800D-x motherboard I suppose :'(

---

### Post by nhwk64 on 2006-03-02
[QUOTE=GazaM]Unfortunately my ATI equipped machine suffers from complete lockup/freezing with Xgl, so it's unusable for me there. I'm writing this from a PC with an old GeForce2 MX and Xgl/compiz is running rock solid. Pretty disappointing not to be able to run this on my main machine though, anybody know what's causing these lockups? I know others here have mentioned it as well. Hoping a fix is available, as I'm blown away by the effects, as are my friends and family... some of them really are good for usability, such as the window minimising effect and the zoom effect.[/QUOTE]

It seems like an ATI specific bug in either xgl or fglrx, so I guess we'll just have to wait for newer versions of either to come out and see if it fixes it. I haven't heard anyone mention ways to debug it, since nothing shows up in the logs it seems.

---

### Post by danmagicman7 on 2006-03-03
I think it would be great if someone made a new, sticky thread when this happens.

Most ATI users are at a standstill until XGL is updated.

---

### Post by Melvil on 2006-03-03
Xgl runs great on my ATI Radeon Mobility 9600 using fglrx and the 686 kernel.

Just had a lockup a few minutes ago while an OpenGL screensaver was running, it was the first freeze in the last two days I've been using Xgl.

---

### Post by Entity on 2006-03-03
...

---

### Post by lipido on 2006-03-04
My experiences in several PCs (all ATI) with Drake XGL/Compiz are:

I used the same procedure to install the 3D desktop:
- Ubuntu install CD daily compiled 2006/03/01
- Install fglrx (apt-get install xorg-driver-fglrx).
- Install xgl/compiz with the procedure at the top of this thread and the one in the page 23.


**1. Laptop Acer Ferrari 3000: ATI Mobility Radeon 9200. (OpenGL detected: ATI 9000 DDR Generic)**
- Fglrx: OK
- Xgl/Compiz: Impossible to get it working. When compiz starts I get a whole distortion in the screen. I think that is a jam of pieces of images in the card's memory because I see different things and I can recognize some content.

**2. Laptop Acer Travelmate 4100: ATI Mobility Radeon X700 128Mb.**
- Fglx: OK
- Xgl/Compiz: It works some secs, but then it freezes hard.

**3. Desktop PC with ATI Radeon 9550 128Mb**
- Fglx: OK
- Xgl/Compiz: It works! (no freezes! eye-candy! :cool: ). However, I can observe that when I move a window with wobbly, after release it, if I leave the mouse, the wobbly effect becames slow, (0.5 fps! aprox), I have to keep moving the mouse. To solve it I have to maintain an app with movement in the screen (video, xmms, etc), (in other side of the cube it works too). :-k 

**4. Desktop PC with ATI Radeon 9800Pro 128Mb**
- Fglx: OK.
- XGl/Compiz: The same, same, same as in point 3 (including the wobbly bug!).

**5. Desktop PC with ATI Radeon X300 128Mb**
- Fglx: OK.
- Xgl/compiz: The same, same, same as in point 2.


Conclusions:
- ATI 9550 or better works fine (with the wobbly strange behaviour).
- ATI X series (X300, X700) freezes after several seconds. (When it works, before the freeze, I have observed that the strange wobbly behaviour is not present).
- ATI 9200 doesnt work (fglrx yes, Xgl starts, but compiz shows a whole distorted screen).

I have read many posts and that some people got the freezes in X series.

Any Ideas?

---

### Post by xkcdmagic8 on 2006-03-04
Ferrari 4000 (4005 lol) works:

fglrx: works fine (i guess - didnt have to do much)

Xgl: all works, freezes hard with GDM so i boot into console and run Xgl from there with terminal and then start gnome-session - works. Everything works, i can launch firefox BUT if i click on the taskbar (application bar) watever on the bottom it just stops - all dead need to reboot.

---

### Post by lipido on 2006-03-05
Your graphics card is an ATI x series, right?

My hypothesis: ATI x series = freezes hard randomly.

---

### Post by lawngn0mex on 2006-03-06
[QUOTE=lipido]Your graphics card is an ATI x series, right?

My hypothesis: ATI x series = freezes hard randomly.[/QUOTE]


My x800xl locks hard with XGL. I just dist-upgraded.. and things seem pretty smooth though.. so here's to hoping that some driver issues are fixed.. It seems to be snappier.

---

### Post by LJunkie on 2006-03-06
[QUOTE=lipido]Your graphics card is an ATI x series, right?

My hypothesis: ATI x series = freezes hard randomly.[/QUOTE]

Has anyone of the poor ones with ATI x series tried the fglrx-builtin agp driver? Maybe I am wrong but it seems to me that the module provided in universe doesn't support the ati internal driver. Is that right?
I tried to compile the driver from source but didn't succeed.

---

### Post by tukster on 2006-03-06
yes well for now, X series = random lockups.
i have tried everything to no avail.

mine is x800xt with fglrx.
anyone had any success with drivers from ati?

---

### Post by lipido on 2006-03-06
[QUOTE=lawngn0mex]My x800xl locks hard with XGL. I just dist-upgraded.. and things seem pretty smooth though.. so here's to hoping that some driver issues are fixed.. It seems to be snappier.[/QUOTE]

I'm gonna try this! :-k

---

### Post by tukster on 2006-03-06
dist-upgrade, 
well maybe its smoother cause we have a new fglrx driver in repo.
dunno if it helps with lockups

---

### Post by dragoncow2 on 2006-03-06
Wow, compiz/xgl is really cool! :o)

The only problems I run into is when running the xserver-xgl (with or without compiz), random crap doesn't display correctly. That's about the best I can describe it..firefox pages sometimes blend into highly-unreadable-slanty-font-land, and other random problems like that. Not too bad though, it gets worse when compiz is run, but not by much. It isn't quite usable, but it's damn cool! (cube and all).  (nvidia go5700)

---

### Post by lipido on 2006-03-06
I've just performed a dist-upgrade. After 5 minutes I get a hard freeze again with xgl/compiz. (ati x700). Remember: Ati x series = freeze.

Is there anybody with an ati x series who works with xgl/compiz with no problems? I only can work with my ATI 9550 and 9800pro. :confused:

---

### Post by jasay on 2006-03-06
[QUOTE=lipido]I've just performed a dist-upgrade. After 5 minutes I get a hard freeze again with xgl/compiz. (ati x700). Remember: Ati x series = freeze.

Is there anybody with an ati x series who works with xgl/compiz with no problems? I only can work with my ATI 9550 and 9800pro. :confused:[/QUOTE]
Sorry to say that my x300 has never made it more than 30 minutes--and usually more like 10--without a hard freeze.:(

---

### Post by PeArL PaNdA on 2006-03-07
[QUOTE=jasay]Sorry to say that my x300 has never made it more than 30 minutes--and usually more like 10--without a hard freeze.:([/QUOTE]

I have a Radeon X300SE in my Dell GX280 and it mostly crashes in GDM already, so before Compiz is loaded.

And I have a X200 in my MSI S270 laptop, where I can login, but it crashes whenever I try to run "very heavy" software like minsweeper or mahjong ;)

Also there's a bug that when I lock my X session, while running Xgl and I start using it again, I don't have to type my password again, instead it just gives me all my open programs without window decoration. Not very good security I'd say.

---

### Post by Viriiguy on 2006-03-07
Ok I am a bit of a dumb dumb I suppose. But I have skimmed thru this thread several times and found no mention of this "MAin" thread that tells how to set up my xorg.conf file for an ATI 9600.

I have been afraid to install anything out of fear I will break it before I can fix it :D

Could someone kindly point me to this thread with the directions for setting up my xorg.conf file? From then I just follow the directions on the first page right?

Thank you,
Randy

---

### Post by mega on 2006-03-07
X300 here, prior to today it locked up randomly 1-5 minutes into a session


now gdm does not even start

---

### Post by julipanno on 2006-03-07
Thanks for the Howto. I've got it running wonderfully on my Inspiron 9200 laptop with ATI Radeon Mobility 9800 (detected as 9700). I run dapper and use the proprietary fglrx-drivers from the repository. 

My only problem is that the socalled 'super'-key doesn't work at all.  

A possibly related thing is that gThumb crashes when I choose fullscreen-mode, but I'm not sure if compiz has anthing to do with this.


Stian

---

### Post by jasay on 2006-03-07
[QUOTE=Viriiguy]Ok I am a bit of a dumb dumb I suppose. But I have skimmed thru this thread several times and found no mention of this "MAin" thread that tells how to set up my xorg.conf file for an ATI 9600.

I have been afraid to install anything out of fear I will break it before I can fix it :D

Could someone kindly point me to this thread with the directions for setting up my xorg.conf file? From then I just follow the directions on the first page right?

Thank you,
Randy[/QUOTE]This one? [http://www.ubuntuforums.org/showthread.php?t=132406](http://www.ubuntuforums.org/showthread.php?t=132406)

---

### Post by WhO_KnOwS on 2006-03-08
Got a problem... I have everything installed (no errors), did everything according to the howto and I get no eye candy :cry: 
I have 3d acceleration, and glxinfo reports that xgl is running. But for some reason compiz is not running it seems. And if I try to run it manually it doesn't start.
Also, I have no compiz entry in gconf.
I tried the packages from both apt-get and the ones from battlehorse. I even installed all the mesa debs...
What am I missing? (tell me if you need more info - I'll provide it gladly)

---

### Post by Jengu on 2006-03-08
Well, I would really like to try with the new drivers, but I can't get gdm to load Xgl. No matter what settings I put in /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom, ps aux | grep X always shows that /usr/bin/X is running instead of /usr/bin/Xgl.

Has anyone managed to get the new 8.23.7 ati drivers working with Xgl/compiz?

---

### Post by setenza on 2006-03-08
Hi,

I have fully upgraded the new ATI drivers to version 2.23.7

> dmartone@setenza-lnx:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5695 (8.23.7)

> dmartone@setenza-lnx:~$ glxgears -printfps
16568 frames in 5.0 seconds = 3313.412 FPS
21449 frames in 5.0 seconds = 4287.488 FPS
21204 frames in 5.0 seconds = 4240.779 FPS
21335 frames in 5.0 seconds = 4241.441 FPS


XGL/Compiz work fine a little more speed and rendering is a bit faster.

Sorry for my english i'm french

---

### Post by apoclypse on 2006-03-09
It worked first try for me, however I seem to have trouble with gnome it taked forever to start and when it does it doesn't load the panel. 

The little that I did get to use was incredible, I almost fell out of my chair. I didn't expect it to be this polished. Its still rough but its very usable.

---

### Post by getaceres on 2006-03-09
It doesn't work for me, no matter what I try:

First I tried with the method posted in the first page, but there's no apps/compiz/general/all screens/options section in my gconf so it didn't work (XGL was working, I think but I cannot init compiz). Then, I tried with the tutorial at [http://www.rage3d.com/board/showthread.php?t=33847510](http://www.rage3d.com/board/showthread.php?t=33847510) but again, it didn't work. Everytime I start compiz I loose the window decoration (by the way, I'm vanyar in this post).
Then I tried with the method of xsession in page 23 of this post but when I run this session I get a black screen and nothing more, and I have to reset.
Is it really so difficult to make it work? I'm the only one who finds it impossible to make it work?

---

### Post by setenza on 2006-03-09
[QUOTE=getaceres]It doesn't work for me, no matter what I try:

First I tried with the method posted in the first page, but there's no apps/compiz/general/all screens/options section in my gconf so it didn't work (XGL was working, I think but I cannot init compiz). Then, I tried with the tutorial at [http://www.rage3d.com/board/showthread.php?t=33847510](http://www.rage3d.com/board/showthread.php?t=33847510) but again, it didn't work. Everytime I start compiz I loose the window decoration (by the way, I'm vanyar in this post).
Then I tried with the method of xsession in page 23 of this post but when I run this session I get a black screen and nothing more, and I have to reset.
Is it really so difficult to make it work? I'm the only one who finds it impossible to make it work?[/QUOTE]

Hi,

Test with this method, to add compiz in gconf. Don't start an XGL sessions, start a xorg sessions. 

Method point 4 start xgl rootless :

[http://gentoo-wiki.com/HOWTO_XGL#Running_Xgl](http://gentoo-wiki.com/HOWTO_XGL#Running_Xgl)

After that you have the compiz in gconf.

---

### Post by WhO_KnOwS on 2006-03-09
[QUOTE=setenza]Hi,

Test with this method, to add compiz in gconf. Don't start an XGL sessions, start a xorg sessions. 

Method point 4 start xgl rootless :

[http://gentoo-wiki.com/HOWTO_XGL#Running_Xgl](http://gentoo-wiki.com/HOWTO_XGL#Running_Xgl)

After that you have the compiz in gconf.[/QUOTE]

Using this method I get:

```
root@Damage-Inc:/home/peter# Xgl :1 -ac -accel glx:pbuffer -accel xv:pbuffer
X Error of failed request:  BadLength (poly request too large or internal Xlib l ength error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  1 (X_GLXRender)
  Serial number of failed request:  94
  Current serial number in output stream:  95
root@Damage-Inc:/home/peter# LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib/ DISPL AY=:1 compiz gconf
root@Damage-Inc:/home/peter# DISPLAY=:1 gnome-window-decorator
compiz.real: Couldn't open display :1

(gnome-window-decorator:5309): Gtk-WARNING **: cannot open display:

```

---

### Post by setenza on 2006-03-09
That's a problem with your drivers try a "fglrxinfo" what the result ??

---

### Post by Fudgie on 2006-03-09
I've tried running Xgl with the new drivers on my X300 (Not from gdm, had to start Xorg manually and do everything from an xterm), and I was totally disappointed to get a hard-lockup within 2 minutes of use. The fglrx driver makes it extremely cumbersome to try different options as well, as after having started X once the machine will freeze on the next attempt. 

Bleh, shame on you ATI.

Fudgie

---

### Post by WhO_KnOwS on 2006-03-09
[QUOTE=setenza]That's a problem with your drivers try a "fglrxinfo" what the result ??[/QUOTE]

That's the funny part. I have direct rendering... Proof:

```
root@Damage-Inc:/home/peter# fglrxinfo -display :1 ## had to specify :1 cause :0 is empty ;)
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 2.0.5642 (8.22.5)


```

---

### Post by setenza on 2006-03-09
Try with proprietary drivers from ATI 8.23.7 ....

---

### Post by WhO_KnOwS on 2006-03-09
No juice... :cry:

---

### Post by Jengu on 2006-03-09
I tried loading Xgl/Compiz with the session trick instead of editing gdm.conf, but only on display 1. That manages to get me into gnome, but compiz still refuses to take control of the windows. 8.23.7 drivers give me no luck with Xgl so far :/

---

### Post by skit on 2006-03-09
Hello, 

Sorry if my english is a little ... bad

I have a ATI Radeon 9200 and i have done exactly what the tutorial said, then because i was getting it soo slow and did not have flgrxinfo information i changed everything to display=0 and now everything is working just fine ... however i have problem ... I can find the /apps/compiz/... in gconfg-editor so I have everything working fine, but just whitout the effects zoom and everything on ...

Can you please please help me ?

[]'s

---

### Post by getaceres on 2006-03-09
I made a fresh install of Ubuntu Dapper Flight 4 and followed the instructions on the page 23. Now I'm running XGL.

---

### Post by Ocxic on 2006-03-09
I went throught the guide, and everyhting seemed to go well but when i try to run compiz i get this
```

admin@ubuntu-Bennett:~$ compiz
admin@ubuntu-Bennett:~$ compiz.real: No composite extension

```
whats up with that??? is there a way to fix it?
how can i tell if xgl is running?

---

### Post by setenza on 2006-03-09
[QUOTE=Ocxic]I went throught the guide, and everyhting seemed to go well but when i try to run compiz i get this
```

admin@ubuntu-Bennett:~$ compiz
admin@ubuntu-Bennett:~$ compiz.real: No composite extension

```
whats up with that??? is there a way to fix it?
how can i tell if xgl is running?[/QUOTE]


Xgl is not running if you have this error

---

### Post by lipido on 2006-03-09
[QUOTE=skit]Hello, 

Sorry if my english is a little ... bad

I have a ATI Radeon 9200 and i have done exactly what the tutorial said, then because i was getting it soo slow and did not have flgrxinfo information i changed everything to display=0 and now everything is working just fine ... however i have problem ... I can find the /apps/compiz/... in gconfg-editor so I have everything working fine, but just whitout the effects zoom and everything on ...

Can you please please help me ?

[]'s[/QUOTE]

I can't get Xgl work with display 0, it shows the mouse clock forever. When I read your post I hope I can definitively get my 9200 working, but I only get a whole distorted screen when I start compiz (with display 1, and with display 0, Xgl hangs with the mouse clock).:???:

---

### Post by skit on 2006-03-09
I have just formatted my machine, just wanna know after i run the tutorial i get stuck because i cannot find (probably because it really doesn't exists ... in gconf-editor ... apps > compiz ... How can this happen ? It really isn't there ...

=/

[]'s

---

### Post by setenza on 2006-03-09
[QUOTE=skit]I have just formatted my machine, just wanna know after i run the tutorial i get stuck because i cannot find (probably because it really doesn't exists ... in gconf-editor ... apps > compiz ... How can this happen ? It really isn't there ...

=/

[]'s[/QUOTE]

After you have successfully started XGL, execute in a terminal :

compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher

And they add compiz in gconf

---

### Post by JLTB on 2006-03-10
Well I just got this stuff installed.  No major problems.  However, I wasn't expecting how crazy this compiz stuff really is!!  I'm am completely speachless.  I thought my ubuntu box was the ugly one in the corner (the nice mac mini I have at work is the 'real' GUI computer).  I really don't know what to say ... have I been under a rock for a few months or something??

Good job suse, novell (and of course ubuntu packagers!)!!!  I'll be able to convert many more friends to ubuntu with just a few minutes of seeing XGL and Compiz! :-D

---

### Post by skit on 2006-03-10
Now i have the ati drivers problem ... they won't load correctly and fglrxinfo gives me MESA Driver ...

=/

---

### Post by Ocxic on 2006-03-10
read back a few page or do a search i read in this thread it should say that if it's working, i think... it's in here somewhere

---

### Post by typoEDR on 2006-03-10
I have a question regarding this wacky little software:  Some functions (resize, opacity) do not appear to function.  I've followed the guide quite closely (actually several guides, since I screwed up twice) and put the plugins in a certain order, but some of the functions aren't working at all.

Also, what is the 'super-key' or whatever it's called?  I assumed it was the Windows key, but it isn't doing anything.

Thanks.

---

### Post by wousser on 2006-03-10
does anybody know how to get it work again with the new 8.23.7 drivers? xgl works but compiz doesnt start.
ahh, and in X fglrxinfo gives correct info about ati, but in Xgl it gives the mesa stuff..

---

### Post by Melvil on 2006-03-10
[QUOTE=skit]Now i have the ati drivers problem ... they won't load correctly and fglrxinfo gives me MESA Driver ...

=/[/QUOTE]

fglrx gives me NO driver.... "Error: unable to open display :0"

is there a way to revert to the old version?

---

### Post by apoclypse on 2006-03-10
everything works great so far. I'm using the packages provided in one of the threads here it on the first page called new compiz or soemthing. So far everything works great. My only question is, is it normal for xgl to take 5 minutes to start? I also can't seem to logoff, the gnome panel just seems to freeze so I've been killing the x server to drop out. Is there a workaround or is this the way it works for the moment?

---

### Post by QUASAR_FREAK on 2006-03-10
[QUOTE=apoclypse]everything works great so far. I'm using the packages provided in one of the threads here it on the first page called new compiz or soemthing. So far everything works great. My only question is, is it normal for xgl to take 5 minutes to start? I also can't seem to logoff, the gnome panel just seems to freeze so I've been killing the x server to drop out. Is there a workaround or is this the way it works for the moment?[/QUOTE]

The 5 min delay never happen to me, the freeze on logoff yes but stop with the last update.

---

### Post by Aschi on 2006-03-11
Does this whole XGL and Compiz stuff work on a mobility x300 128mb as well (smoothly)?

---

### Post by Jengu on 2006-03-11
[QUOTE=Aschi]Does this whole XGL and Compiz stuff work on a mobility x300 128mb as well (smoothly)?[/QUOTE]

Assuminng the fglrx drivers support your card (I think they do but check) it should be more than capable of handling Xgl and Compiz.

---

### Post by eMuNiX on 2006-03-11
Can't quite seem to get this running but I do have the latest drivers and 3D working:-
```
emunix@linux:~$ Xgl :1 -ac -accel glx:pbuffer -accel xv:pbuffer
Couldn't open RGB_DB '/usr/share/X11/rgb'
_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/linux:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
FreeFontPath: FPE "/usr/lib/X11/fonts/misc/" refcount is 2, should be 1; fixing.

```
```
emunix@linux:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5695 (8.23.7)

```

My xorg.conf only shows 1 display device, it used to show 2:-

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "LS902U"
	HorizSync    30.0 - 96.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "LS902U"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

---

### Post by apoclypse on 2006-03-11
It seems when I updated the packahes the dalt went away. i can now  restart my pc from gnome, but when I logout it still freezes and when I log back im after killing the xserver I get a panel alreay running type error. However these little things are to be expected, I'm just so surprised at how stable it is. It works really well. Now if inly they can fix video playback specifically the wmv files which have a weird doubling uninterlaced look to them, and my tv card has to be in capture mode as overlay doesn't work. Is there a fix for this or is this to be expected?

---

### Post by Fudgie on 2006-03-12
[QUOTE=typoEDR]I have a question regarding this wacky little software:  Some functions (resize, opacity) do not appear to function.  I've followed the guide quite closely (actually several guides, since I screwed up twice) and put the plugins in a certain order, but some of the functions aren't working at all.
[/QUOTE]

Make sure the plugins are active in gconf as well, not just on the command line. If you add gconf on the command line, compiz will ignore all other plugins specified there, and ONLY read from gconf.

[QUOTE=typoEDR]Also, what is the 'super-key' or whatever it's called?  I assumed it was the Windows key, but it isn't doing anything.
[/QUOTE]

It is the windows key, make sure you have a 105 key keyboard set up, not 101/102 keys.

---

### Post by wolfchri on 2006-03-12
Hello folks,

my dumb question, not meant to provocate: 

Did anybody ever get xgl up and running by just using the [official XGLHowTo]("https://wiki.ubuntu.com/XglHowto")? If not, why is there such a crap in the Wiki that makes you think xgl is a thing of a little apt-get install ???

I would very much like to simply delete this Howto (but do not dare...) because it is obviously far away from being a help - according to all the xgl threads here. I am still not even close to get xgl working, after following the HowTo step by step.

Or is there some magic between the lines in the HowTo article that I have not read?

Otherwise I would suggest to deactivate that page until xgl has in fact become a matter of an apt-get install xyz.

---

### Post by recover82 on 2006-03-12
Quick question about the "Shift+Backspace" bug.  

I know that when you login you can issue 
"xmodmap /usr/share/xmodmap/xmodmap.us" (us being my region) via terminal and fix the bug with "Shift+Backspace"..the fix works great actually..but I shouldn't have to enter it every time I log in.  

Can I add that command to my "Sessions" along side gnome-window-decorator and compiz replace gconf commands?  I would just try.. but I'm not at that box right now.  I'm just trying to get a list of things to do when I do have access.  

Thanks for any input.

::recover82::

---

### Post by Fudgie on 2006-03-12
[QUOTE=wolfchri]Did anybody ever get xgl up and running by just using the [official XGLHowTo]("https://wiki.ubuntu.com/XglHowto")? If not, why is there such a crap in the Wiki that makes you think xgl is a thing of a little apt-get install ???
[/QUOTE]

If you have an nvidia card, it's pretty much just apt-get install. Otherwise, you need to fiddle quite a bit for limited results.

---

### Post by Fudgie on 2006-03-12
[QUOTE=Aschi]Does this whole XGL and Compiz stuff work on a mobility x300 128mb as well (smoothly)?[/QUOTE]

Works on an ATI X300 SE for 1-10 minutes depending on luck and how much you try to do other than wobble windows. :-) ATI needs to fix their drivers, or someone needs to sit down and write around the hard-freeze that occurs on most highend ATI cards.

---

### Post by wolfchri on 2006-03-12
Fudgie,

I have an NVidia 6600GT.... :-? 

Still, the HowTo does not work, the only thing I get is that my Gnome task bar is vanishing. Sorry, but that is far away from being useful, at least for me. 

Here is my hardware:

[http://librarian.launchpad.net/1693217/lspci.txt](http://librarian.launchpad.net/1693217/lspci.txt)

and it is not working although I am trying since Dapper Flight 4, and I am not considering myself a complete noob, coming from Gentoo :-)

---

### Post by Fudgie on 2006-03-12
Ah. **That** howto. Sorry, I've never gotten that way of launching Xgl to work, I've always just replaced X with Xgl in /etc/gdm/gdm.conf in the [server-Standard] section, and disabled DRI, GLCore & Composite in xorg.conf. Never had any problems on any of my machines running the nvidia driver as long as I had working DRI up front. 

([http://mr.fudgie.org/index.php/2006/02/16/tiny-ubuntu-dapper-nvidia-xgl-howto/](http://mr.fudgie.org/index.php/2006/02/16/tiny-ubuntu-dapper-nvidia-xgl-howto/) is how I always do it when setting it up for friends)

---

### Post by recover82 on 2006-03-12
[QUOTE=recover82]I know that when you login you can issue 
"xmodmap /usr/share/xmodmap/xmodmap.us" (us being my region) via terminal and fix the bug with "Shift+Backspace"..the fix works great actually..but I shouldn't have to enter it every time I log in.  

Can I add that command to my "Sessions" along side gnome-window-decorator and compiz replace gconf commands?  I would just try.. but I'm not at that box right now.  I'm just trying to get a list of things to do when I do have access.  
[/QUOTE]

I finally got to my box and for anyone else curious about this it does work.

---

### Post by loftx on 2006-03-12
Hi all, I've got Xgl/Compiz working but for some reason, all windows don't seem to remember their position and start in the top left corner - the only one which doesn't seems to be beep-media-player.

Is anyone experiancing this or have any solutions? I had a look through most of this thread but couldn't see anything.

Spec:
AMD 2200 Athalon
Radeon 9600 with fglrx driver from repos
Dapper flight 5
Xgl compiz and supporting packages from repos
Transparancy plugin for compiz.

Thanks,

Tom

---

### Post by Melvil on 2006-03-12
[QUOTE=loftx]Is anyone experiancing this or have any solutions? I had a look through most of this thread but couldn't see anything.[/QUOTE]

Sort of...[this problem](http://ubuntuforums.org/showpost.php?p=817724&postcount=173) is bugging me

---

### Post by loftx on 2006-03-12
> Is there some (official) site where I can post bugs related to Xgl/compiz?

Right now all applications start at screen location (0, -30), so the titlebar and menubar are "above" the screen and I have to move the window down first to see the contents.

Originally that did happen to me, I think it was the first time I got compiz working, but somehow it moved it down to starting at (0,0) I think on the second time I tried running it. It also put a window decorations (with title) around my gnome panel which moved it down so I couldn't actually see the main panel, though this fixed itself too.

I assumed this was something i'd done wrong rather than a bug ;)

---

### Post by JLTB on 2006-03-12
My windows also often started with their taskbars under the top gnome task bar.  After the first few windows had opened it quit happening.

Keep in mind that <Alt> keyboard shortcut will let you grab windows anywhere to move them so this isn't too big of a deal.

So far I've gotten XGL + Compiz going on 3 computers: AMD 64 3500 w/ ATI 9600 XT, AMD 64 3500 w/ Nvidia 6600 GT, and my pokey old Duron 950 w/ GForce 4 MX (which owns by the way.. . the computer is literally faster and more responsive after installing XGL, makes sense when you think about it).

Apparently a lot of people are having hardware issues with this.  So far everything has installed without a hitch for me (no offence intended anyone).

My advice, get DRI going on your card very smoothy first before trying this howto (obvious yes, but it burns me all the time too).

---

### Post by mbozo on 2006-03-13
Hi,

I've tried to start Xgl with the "gdm-howto".
Xgl fires up, but I'm not able to run compiz - it only replies with:
"compiz.real: Support for non power of two textures missing"

But if I revert to the original gdm configuration, and then run Xgl with:
"sudo /usr/bin/Xgl :1 -ac -accel glx:pbuffer -accel xv:fbo &"

Then I'm able to run compiz with:
"DISPLAY=:1 compiz -display :1 --replace gconf"

See attached screenshot.

Any suggestions?

---

### Post by loftx on 2006-03-13
Something else I've just noticed - gconf won't let me add "menu" to the active_plugins string list - after I can add it to the values list in the dialog box - but when I press ok it doesn't add it to the string. Anyone know why this is and what problems it might cause?

---

### Post by eeclark on 2006-03-13
[QUOTE=loftx]Something else I've just noticed - gconf won't let me add "menu" to the active_plugins string list - after I can add it to the values list in the dialog box - but when I press ok it doesn't add it to the string. Anyone know why this is and what problems it might cause?[/QUOTE]

I have the same problem...posted it but no one ever responded. GL.

---

### Post by Mr Frosti on 2006-03-13
Throwin' in my two cents on the chance Google crawls this site:

I have an ATI X300 mobile, and can confirm several issues with Xgl at this point. Even without compiz running, Xgl consistantly hard locks when Nautilus is initiated from within Xgl. Without Nautilus running, I do not experience any other stability issues when running it inside of a regular Gnome session as outlined below. The gnome-theme-manager crashes when switching themes, but this is to be expected. If I start Xgl using the HOWTO from Mattisking, my system reliably hardlocks at anywhere between 2 seconds and 2 minutes after the login screen appears. If I create a new "Xsession" file as outlined by Guyhersh, I have the same results. That HOWTO is here: [http://www.ubuntuforums.org/showthread.php?t=131253&page=28]("http://www.ubuntuforums.org/showthread.php?t=131253&page=28")

For those who have installed the compiz package, but do not have the entries in gconf-editor, I have a work around. I have exported the "apps->compiz" branch, and uploaded it. Anyone who is missing these entries, extract this package in "~/.gconf/apps/". 

Also, version "0.0.5-0ubuntu4" of compiz does not appear to support the "libcube" module (at least not for me), which fails other modules in the dependency tree. The other failed modules are "zoom" and "rotate". Also, I have not had any luck in adding the opacity module outlined in the Howto below. I would recommend taking these entries out of gconf-editor under the plugins section if you are experiencing issues: [http://ubuntuforums.org/showthread.php?t=132063&highlight=compiz+opacity]("http://ubuntuforums.org/showthread.php?t=132063&highlight=compiz+opacity")

Now, these are the steps that I follow to start Xgl with stability. Open up a terminal and type in: 

```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:fbo & sleep 2 && DISPLAY=:1 gnome-terminal
```

This will initiate Xgl in fullscreen mode, with hardware acceleration on display 1 (resolves ATI driver bug). It will also open a terminal for you once it is finished loading. In this terminal, type the following:

```
compiz --replace gconf
```

This will start the compiz composite manager. Watch for any error messages on loading the modules. Once this finishes, add the window decorations by typing in:

```
gnome-window-decorator
```

==TROUBLESHOOTING==

[LIST]
[*]Check to make sure that you have 3D acceleration by typing in "fglrxinfo" into a terminal. You should see "OpenGL vendor string: ATI Technologies Inc.". If not, resolve that issue first. 

[*]The original HOWTO by Mattisking asks the user to edit their /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom files. With the new method, these alterations should be taken out. 

[*]If Xgl is hard locking your system before you can start compiz, follow the logs for the system by entering in the command:

> sudo tail -f /var/log/syslog

[*]If you are running Xgl and/or compiz, but are not seeing the fancy results everyone is describing, then check to make sure you have the following packages installed:

compiz (0.0.5-0ubuntu4)
compiz-gnome (0.0.5-0ubuntu4)
xserver-xgl (7.0.0-0ubuntu3)
[/LIST]

Good luck all, and I hope this helps shed some light!

**Update: This information has migrated to a wiki here: [http://wiki.ubuntu.com/xglati]("http://wiki.ubuntu.com/xglati")**

---

### Post by wylie348 on 2006-03-14
Oddly enough I get a proper login screen, but a black screen (with white mouse_pointer) when I get in to gnome.  Cannot see anything, but things appear to be running?!  
Only way back in is to disable changes in cust-conf.
Anyone else having this trouble?
(Using ATI9200 radeon, with working flgrx)

---

### Post by nhwk64 on 2006-03-14
[QUOTE=Mr Frosti]Throwin' in my two cents on the chance Google crawls this site:

I have an ATI X300 mobile, and can confirm several issues with Xgl at this point. Even without compiz running, Xgl consistantly hard locks when Nautilus is initiated from within Xgl. Without Nautilus running, I do not experience any other stability issues when running it inside of a regular Gnome session as outlined below. The gnome-theme-manager crashes when switching themes, but this is to be expected. If I start Xgl using the HOWTO from Mattisking, my system reliably hardlocks at anywhere between 2 seconds and 2 minutes after the login screen appears. If I create a new "Xsession" file as outlined by Guyhersh, I have the same results. That HOWTO is here: [http://www.ubuntuforums.org/showthread.php?t=131253&page=28]("http://www.ubuntuforums.org/showthread.php?t=131253&page=28")
[/QUOTE]

I just tried your suggestion, but it locked up as I was testing the menu items in firefox after about 5-10 seconds :( (X800 card)

---

### Post by Mr Frosti on 2006-03-14
This forum is getting difficult to read, so I have moved the information to a wiki page located here: 

[http://wiki.ubuntu.com/xglati]("http://wiki.ubuntu.com/xglati")

Feel free to append to this guide - my goal is to provide an easier location to troubleshoot issues

---

### Post by janko on 2006-03-15
Awesome, I followed the first-post how to, and now I have a Linux box that makes the difference!!!
So far I've tried software like "The GIMP", Gaim, Firefox, and everything seems to work perfectly. My hardware is a Pentium M 1,6 Centrino mounting a Mobility Radeon 9700 64Mb Video Ram dedicated and 512 RAM.
My only problem right now is that annoing lagging pseudo animation that has nothing to do with Xgl. It's that slow rectangle that comes up when I start an application clicking on an icon on the top panel or bottom panel. Is there a way to even eliminate that bad animation?

---

### Post by Don_DiZzLe on 2006-03-15
> Ensure that the newly installed compiz package has placed the correct entries in the gconf-editor. To check, type in a terminal "gconf-editor". A window will pop-up with a tree view in the left pane. Double-click "apps". If you see "compiz" under "apps", then the needed entries appear to exist. If you do not see a "compiz" folder, then please download and extract the package below into the "~/.gconf" directory.

* [WWW] [http://ubuntuforums.org/attachment.php?attachmentid=7039&d=1142311054](http://ubuntuforums.org/attachment.php?attachmentid=7039&d=1142311054) 

Where can I find this "~/.gconf" directory?

---

### Post by loftx on 2006-03-15
[QUOTE=Don_DiZzLe]Where can I find this "~/.gconf" directory?[/QUOTE]
It's a hidden directory in your home directory. If you're using nautilus go to your home directory and press CTRL+H (or View-> Hidden files from the menu) and you'll be able to see it

---

### Post by mcduck on 2006-03-15
[QUOTE=janko]
My only problem right now is that annoing lagging pseudo animation that has nothing to do with Xgl. It's that slow rectangle that comes up when I start an application clicking on an icon on the top panel or bottom panel. Is there a way to even eliminate that bad animation?[/QUOTE]
Open Configuration Editor (run gconf-editor if you haven't got it in menu), browse to apps/panel/global and unmark 'enable_animations'. That should do it :)

---

### Post by janko on 2006-03-15
Thanks a lot mcduck, does anyone know if there's any possibility to make work again applications that use opengl while i'm using a desktop running XGL? For example i'd like to play again with America's army... or maybe is there a way to tell the program I'm executing that has to run on screen 1 or something like that?

---

### Post by faethon on 2006-03-15
Just registered after I decided to share my story on installing the Xgl/compiz eyecandy:

I did a fresh install of ubuntu dapper drake, using flight 5 CD. After following the ATI howto in the start post (I have a 9700 Pro) I had some small problems: 

At first, there were no compiz entries in the gconf editor. I decided to reboot. After that the entries were present (since compiz was started at the reboot) so I could continue with the setup of the entries in gconf. After a subsequent reboot (not needed but I did it anyways) I did not see any window decorations at all. Turned out that in my session, the gnome-window-decoration was not at the top of the list. Adding this to the top of the session startup programs solved the problem. 

Rebooted the machine and lo and behold! All eye candy working! I noticed some slugishness with the wobbly effect though and also the 'startup' animations seemed to be extremely slow. I switched the enable-animation off using gconf-editor (apps->panel->global) and the slow animation was gone and also the wobbly effect was much smoother!! 

After that I decided to install the opacity with the nice mousescroll keybinding. I used the information in this thread: [http://ubuntuforums.org/showthread.php?t=132063&highlight=opacity+compiz](http://ubuntuforums.org/showthread.php?t=132063&highlight=opacity+compiz) and had the opacity running in no time and bound to my mousewheel

I needed to change my keyboard layout to 105 keys setup to get the zooming function to work (using 'superkey - right_mouse' combo).

I did not have any lockups (so far).

Slugishness of wobbly is solved by unticking detect_refreshrate and setting refreshrate to 60 in gconf-editor apps->compiz->general->screen0->options

---

### Post by Fudgie on 2006-03-16
[QUOTE=loftx]Something else I've just noticed - gconf won't let me add "menu" to the active_plugins string list - after I can add it to the values list in the dialog box - but when I press ok it doesn't add it to the string. Anyone know why this is and what problems it might cause?[/QUOTE]

There is no menu plugin, so maybe that's the reason? ;)

---

### Post by loftx on 2006-03-16
Yeah, I did eventually find this out :)  Though it's still in the walkthrough at the top of the thread.

---

### Post by kotzkroete on 2006-03-16
It worked fine for me before, but since I reinstalled dapper it doesn't work. When I start 
```
compiz decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher --replace gconf
```
ubuntu says: 

compiz.real: Couldn't load plugin 'libmenu.so'
compiz.real: Couldn't load plugin 'libgconf.so'

With all effects, exept tilebars. And when I try to start 
```
gnome-window-decorator
```
I get this:

bash: gnome-window-decorator: command not found

---

### Post by Fudgie on 2006-03-16
gnome-window-decorator is in the compiz-gnome package. Make sure you install that one as well.

---

### Post by kotzkroete on 2006-03-16
thx...it works...But Why do I get

compiz.real: Couldn't load plugin 'libmenu.so' ?

---

### Post by Fudgie on 2006-03-16
There is no menu plugin, so remove it from the active_plugins setting in gconf (apps/compiz/allscreens/options or something like that)

---

### Post by kotzkroete on 2006-03-16
But what is the menu plugin? What does it? 
BTW: Is there a tutorial how to give the top and bottom of the cube a texture? Would be cool.

---

### Post by badcow on 2006-03-16
Yeah ~~~~ I make it!\\:D/ 

My card is Mobility Radeon 9200 (32M) on a Compaq x1000 laptop, using "radeon" driver.

But there is a problem that Xgl cannot run under 1280x800 which is best fit for my LCD monitor, it will fail with "no screens found". Someone said this problem can be solved by using driconf to enable large texture support. But I cannot make it even I use driconf, maybe my setting is wrong, I hope someone can help me or post the right drirc file.

[http://gentoo-wiki.com/HOWTO_XGL#no_screens_found]("http://gentoo-wiki.com/HOWTO_XGL#no_screens_found")

---

### Post by cbudden on 2006-03-16
Hello.  I followed the ATI howto on the wiki and get this output:

```

cbudden@ubuntu:~$ compiz --replace gconf
cbudden@ubuntu:~$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

```

Fglrxinfo reports ATI (latest driver from ati.com)

I have tried the XGL live CD and that works fine.  
Any idea on how i could fix this problem?

Thanks

---

### Post by badcow on 2006-03-16
[QUOTE=cbudden]Hello.  I followed the ATI howto on the wiki and get this output:

[code]
cbudden@ubuntu:~$ compiz --replace gconf
cbudden@ubuntu:~$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0
[code]

Fglrxinfo reports ATI (latest driver from ati.com)

I have tried the XGL live CD and that works fine.  
Any idea on how i could fix this problem?

Thanks[/QUOTE]

Are you sure the Xgl is already running ? Just run " ps ax|grep Xgl " to confirm it.

When I first met this problem after I follow the first post method, it is because I run X server by "startx", not by gdm, so the Xgl command line in gdm.conf-custom will not start at all.

---

### Post by cbudden on 2006-03-16
This what we are looking for?
```

cbudden@ubuntu:$ ps ax|grep Xgl
 6616 pts/0    SL     0:00 Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:fbo
 6650 pts/1    S+     0:00 grep Xgl

```

---

### Post by Fudgie on 2006-03-16
[QUOTE=cbudden]Hello.  I followed the ATI howto on the wiki and get this output:

```

cbudden@ubuntu:~$ compiz --replace gconf
cbudden@ubuntu:~$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

```

Fglrxinfo reports ATI (latest driver from ati.com)

I have tried the XGL live CD and that works fine.  
Any idea on how i could fix this problem?

Thanks[/QUOTE]

ATI diverts the Mesa libGL to an ATI one, so you need to do a
LD_PRELOAD=/path/to/old/mesa/libGL.so compiz --replace gconf

I don't remember where it ends up of the top of my head, but a locate libGL.so and looking for the one that's ~400kb instead of ~600kb should do the trick.

---

### Post by badcow on 2006-03-16
[QUOTE=cbudden]This what we are looking for?
```

cbudden@ubuntu:$ ps ax|grep Xgl
 6616 pts/0    SL     0:00 Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:fbo
 6650 pts/1    S+     0:00 grep Xgl

```[/QUOTE]

Sorry for my mistake, if Xgl isn't running, compiz wil complain of "composite extension", not "GLX_EXT_texture_from_pixmap is missing"

And this HOWTO file is very useful for troubleshooting :
[http://gentoo-wiki.com/HOWTO_XGL#GLX_EXT_texture_from_pixmap_is_missing]("http://gentoo-wiki.com/HOWTO_XGL#GLX_EXT_texture_from_pixmap_is_missing")

---

### Post by cbudden on 2006-03-16
[QUOTE=Fudgie]ATI diverts the Mesa libGL to an ATI one, so you need to do a
LD_PRELOAD=/path/to/old/mesa/libGL.so compiz --replace gconf

I don't remember where it ends up of the top of my head, but a locate libGL.so and looking for the one that's ~400kb instead of ~600kb should do the trick.[/QUOTE]




Thanks, it was in /usr/share/fglrx/diversions

---

### Post by cbudden on 2006-03-16
Has anyone got a problem using gdesklets and XGL?

edit 

Ok, after a reboot, when I do ld_preload..... compiz --replace gconf it just removes the window decorations and doesn't start compiz.  I try typing in gnome-window-decorations but nothing happens to the windows.  What am I missing?

Edit

My fault, I was doing --replace gconf and then following on with plugins.  Now with just compiz plugins... it works.  Thanks guys

---

### Post by krea on 2006-03-16
I'm stuck at step 7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order

I dont have the compiz option under apps/
and I have it installed I believe:
```
$sudo apt-get install xserver-xgl compiz libgl1-mesa libgl1-mesa-dri libglitz1 libglitz-glx1
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
compiz is already the newest version.
libgl1-mesa is already the newest version.
libgl1-mesa-dri is already the newest version.
libglitz1 is already the newest version.
libglitz-glx1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
any help? thx

---

### Post by badcow on 2006-03-16
[QUOTE=krea]I'm stuck at step 7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order

I dont have the compiz option under apps/
and I have it installed I believe:

any help? thx[/QUOTE]

Have a try on the newest compiz:
[http://www.ubuntuforums.org/showthread.php?t=139265]("http://www.ubuntuforums.org/showthread.php?t=139265")

---

### Post by cbudden on 2006-03-17
I also found that if I am in XGL, and run the following, I get the compiz section in gconf:
```

compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place switcher

```

---

### Post by rahab on 2006-03-17
Hi there,

Now my problem is not related to getting Xgl/compiz stuff to work, but
to get rid of it :) 
I played around with it a few days and now all those little annoying things which do not work properly yet make me wanna go back to good old plane xorg/metacity.
And that´s the point! 
I commented out the changes in gdm.conf/gdm.conf-custom and removed compiz and gnome-window-decoration from gnome-session autostart.
But now I´m left without any windowmanger. Metacity is not running when i log on, so i got no window-decoration, no workplace-switcher, no keyboard-shortcuts, etc.
Of course i can start metacity manually or add it to gnome-session for autostarting, but i don´t know if that is the right way to do it.
I cannot remember metacity showing up in gnome-session autostart before switching to xgl/compiz. 
Anyone got a clue here ???

And by the way,
does anyone know how to get the new composition abilities of the latest 2.14 metacity to work? on the gnome.org website it says, that metacity know can manage opacity, fading, etc itself. But how to activate?

---

### Post by RaptorRaider on 2006-03-17
[QUOTE=krea]I'm stuck at step 7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order

I dont have the compiz option under apps/
and I have it installed I believe:
```
$sudo apt-get install xserver-xgl compiz libgl1-mesa libgl1-mesa-dri libglitz1 libglitz-glx1
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
compiz is already the newest version.
libgl1-mesa is already the newest version.
libgl1-mesa-dri is already the newest version.
libglitz1 is already the newest version.
libglitz-glx1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
any help? thx[/QUOTE]
Same problem here.
Neither the oldest ("battlehorse v1") nor the newest compiz package seem to make a difference; doesn't the problem lie at gconf-editor?

Running it manually doesn't work either (since it's not in "gconf"?):
```
jonathan@doe:~$ gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
[1] 8083
[2] 8084
jonathan@doe:~$ gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension
```

---

### Post by badcow on 2006-03-17
[QUOTE=RaptorRaide]

Running it manually doesn't work either (since it's not in "gconf"?):
```
jonathan@doe:~$ gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
[1] 8083
[2] 8084
jonathan@doe:~$ gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension
```[/QUOTE]

It seems that Xgl has not run yet. Did you run "startx" or "gdm" to start X server ?

---

### Post by RaptorRaider on 2006-03-17
For some reason it is working now.

Lots of stuff seems broken though.
GDM is acting strange. Firefox is acting strange. Evolution suffers from the problem described below.

Many, many applications (those from the "System" menu + Evolution?) have a titleless title bar which cannot be moved (so the window can't be moved, though the bar is transparant). Neither do these apps appear in the bottom bar (which lists active apps). This bottom bar is also acting strange with apps which do appear.

Also Opacity isn't working. Edit: Nevermind, it **is** working; shortcuts are different than listed.

Anyone else having similar problems?

Overall though, this stuff is quite amazing.

---

### Post by vendetta red on 2006-03-17
[QUOTE=RaptorRaider]
Running it manually doesn't work either (since it's not in "gconf"?):
```
jonathan@doe:~$ gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
[1] 8083
[2] 8084
jonathan@doe:~$ gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension
```[/QUOTE]

I have XGL/Compiz working fine on my PC with an Nvidia card, but I am trying to help a friend with an ATI 9800 Pro get it working and after following the guide and tinkering a bit, it is still giving this error everytime. Although for him, compiz is showing up in gconf.

Is there a way to make sure XGL is running for him? Or are there any other ideas as to why this is happening?

---

### Post by badcow on 2006-03-17
[QUOTE=vendetta red]I have XGL/Compiz working fine on my PC with an Nvidia card, but I am trying to help a friend with an ATI 9800 Pro get it working and after following the guide and tinkering a bit, it is still giving this error everytime. Although for him, compiz is showing up in gconf.

Is there a way to make sure XGL is running for him? Or are there any other ideas as to why this is happening?[/QUOTE]

You can try "ps ax | grep Xgl " in a terminal to see whether Xgl is running or not. Another way, while no X server is running, you could run just " /usr/bin/Xgl :1 " in a console to see whether the Xgl can run up.

---

### Post by unf on 2006-03-18
I have problem with my mouse its too fast. Videos are not working I tried xv xv:fbo xv:pbuffer?

---

### Post by ICEM4N on 2006-03-18
Hi, i get the 
"compiz.real : Couldn't find the display" error ...
And it do nothing
 i try all i imagine about it... i don't know what is wrong

ATI Mobility Radeon 9200 (over Compaq PresarioR3245EA)
fglrx driver installed (and working fine)

I put the "1" in gdm.conf and -custom ...

Thanks

---

### Post by spiritz on 2006-03-18
I've been stuggling to get my video ouput working but with no luck so far.
Is anyone actually able to make work XGL+COMPIZ video playing with an ATI hardware?

I'm using recent compiz with XGL from dapper's repos.

Both mplayer & vlc are unable to ouput using GL or GL2, it just makes the freeze. XV ouput is fine as long as it's not full screen; Fullscreen rises cpu use to its maximum. 

btw I'm using 
sudo Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer&

---

### Post by blankSWFC on 2006-03-18
I got Xgl working on my System.  But something seems wrong.  I have an ATI radeon 9550 256mb on an Athlon XP 3200+/nForce 2 Ultra 400.


It runs and most of it works well, but some of the effects are very shuddery/jerky.  Particularly the windows wobble when you let go of the windows from dragging it around the desktop.  It is also noticable on the menu fade-ins.

However, some effects work perfectly with not jerkyness... such as the cude effect when switching desktops and pressing F12 to display on the opened windows next to each other on screen, which also workes perfectly at full speed.



Heres what i did to get it working from a fresh install... maybe i missed something or did something wrong?

I installed the fglrx driver first, since the one from the ATI site wouldn't let me install (moaning about the Xserver being above v6.9), i used apt-get.
```
sudo apt-get install fglrx-driver
```

I replaced the "ati" bit in the xorg.conf file with fglrx, and rebooted.  

I run fglrxinfo, and it returns all the correct info about ATI.  no mention of Mesa.


Then i get Xgl installed...
```
sudo apt-get install xserver-xgl compiz compiz-gnome libgl1-mesa libgl1-mesa-dri libglitz1 libglitz-glx1
```

I added...
```
[servers] 
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
```
to the /etc/gdm/gdm.conf-custom file.

And, changed my /etc/gdm/gdm.conf file to show...
```
#0=Standard
1=Standard
```


I rebooted the machine, and it loaded up Gnome, then from a terminal I run...
```
gnome-window-decorator
```

...and from another terminal i run...
```
compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```


As i put at the top of this post, it works, but *some* effects are very shuddery where as other more complex ones are perfectly smooth.  I can't put my finger on it, so maybe i did something wrong during the install?

Any help would be aprechiated. As all effects work perfectly on the Kororaa Live CD.

---

### Post by neoflight on 2006-03-19
[QUOTE=mattisking]6. Modify your session ("Menu System" -> "Preferences" -> "Sessions") by adding in the following two items:
```
gnome-window-decorator *(must be on top, start first) *
compiz --replace gconf
```

[/QUOTE]


I have a problem !!!!!

I cannot edit/delete the entry in the sessions window.(its in the wrong order now)... Its not highlighted..!! please have a look at the screenshot.... last time i rebooted and got a white screen and had to do a fresh install of dapper due to the same :confused: issue......help!!!!!!!!!!!!!

---

### Post by charlesalexander on 2006-03-19
I tried to follow the guide:  
   1) Even after installing Compiz I don't have a compiz entry in gconf-editor
   2) My Compiz version is 0.0.2... seems a little low as I saw mention of 0.0.5

Output of my fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Generic
OpenGL version string: 2.0.5695 (8.23.7)


Have I done everything correctly?

---

### Post by badcow on 2006-03-19
[QUOTE=ICEM4N]Hi, i get the 
"compiz.real : Couldn't find the display" error ...
And it do nothing
 i try all i imagine about it... i don't know what is wrong

ATI Mobility Radeon 9200 (over Compaq PresarioR3245EA)
fglrx driver installed (and working fine)

I put the "1" in gdm.conf and -custom ...

Thanks[/QUOTE]

I recommend use the open source driver ("ati" or "radeon") for ATI Mobility Radeon 9200 to run Xgl+compiz, at least for this time. I have tried to use fglrx driver for my 9200 (compaq Presario x1000), and Xgl can run slowly in fullscreen (1280x800), but compiz will mess up the whole screen, and other people also reported it as that. Now I use the open source driver, Xgl and compiz can run without error, all the effects work fine. But it is a pity that Xgl only can run with this driver in 1024x640 for my 1280x800 screen.:cry:

---

### Post by scpike on 2006-03-19
It seems like x300 card = random lockups all the time...
if anyone has had any luck getting stability on this card please post what you did.

does the radeon driver work for the card? fglrx is completely unstable with XGL

---

### Post by Fudgie on 2006-03-19
[QUOTE=neoflight]I have a problem !!!!!

I cannot edit/delete the entry in the sessions window.(its in the wrong order now)... Its not highlighted..!! please have a look at the screenshot.... last time i rebooted and got a white screen and had to do a fresh install of dapper due to the same :confused: issue......help!!!!!!!!!!!!![/QUOTE]

It doesn't matter if you run compiz before gnome-window-decorator.

---

### Post by Fudgie on 2006-03-19
[QUOTE=scpike]It seems like x300 card = random lockups all the time...
if anyone has had any luck getting stability on this card please post what you did.

does the radeon driver work for the card? fglrx is completely unstable with XGL[/QUOTE]

I've read that some people have had success with the radeon driver and an X300, but it requires the latest cvs mesa, dri, drm, xorg, etc. Also loading fglrx and then unloading it before loading radeon seems to give some people better luck. I've been meaning to try this myself, but haven't found the time yet.:mad:

---

### Post by blankSWFC on 2006-03-19
If its useful, installing compiz-0.0.5 fixed all my problems with my Radeon 9550 (same chip as 9600).

No lockups or instability after 24 hours of almost contsant use.

I also put on the latest ati drivers from the ati site, and installed using the command...
```
X_VERSION=x690 sudo ./ati-driver-installer-8.23.7-i386.run
```


The compiz i'm using is from a cutom DEB that someone on this forum put together, and is attached to one of the posts somewhere in the section.  

I used them as the Battlehorse Debs broke the Cube plugin, but these ones worked.

If anyone wants them and can't find the debs i used then let me know.

---

### Post by chokes on 2006-03-19
hum okay  i hva istalled all the stuff for compiz and XGL but... im blocked here:

7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order:
Code:

gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher

hum i did'nt find compiz ... and i dont know why...

---

### Post by musther on 2006-03-19
Ok, why can't I delete or edit sessions in System -> Preferences -> Sessions

I can see them, but the delete and edit buttons are unavailable.

---

### Post by kwaanens on 2006-03-20
[QUOTE=chokes]hum okay  i hva istalled all the stuff for compiz and XGL but... im blocked here:

7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order:
Code:

gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher

hum i did'nt find compiz ... and i dont know why...[/QUOTE]

I have the exact same problem. In the first post it says that this is probably a bug, but I've tried 4 different compiz-versions and neither gets me "compiz" in gconf-edior.

- Ketil

---

### Post by blankSWFC on 2006-03-20
[QUOTE=kwaanens]I have the exact same problem. In the first post it says that this is probably a bug, but I've tried 4 different compiz-versions and neither gets me "compiz" in gconf-edior.

- Ketil[/QUOTE]
It seems to be a bug with the new Compiz debs.

I had the same problem, but to get the Compiz section to appear in the gconf-editor, remove your current verison of compiz, and install one of the older compiz verisions from here [http://battlehorse.homelinux.net/w/Wiki.jsp?page=Xgl](http://battlehorse.homelinux.net/w/Wiki.jsp?page=Xgl) .  

I used the compiz from the 7th of Feb, but i think any will work.

Then remove the compiz you just installed with dpkg and then re-install the compiz packages that you were using before.  You will find that the Compiz section will have appeared in the gconf-editor.

---

### Post by kwaanens on 2006-03-20
[QUOTE=blankSWFC]It seems to be a bug with the new Compiz debs.

I had the same problem, but to get the Compiz section to appear in the gconf-editor, remove your current verison of compiz, and install one of the older compiz verisions from here [http://battlehorse.homelinux.net/w/Wiki.jsp?page=Xgl](http://battlehorse.homelinux.net/w/Wiki.jsp?page=Xgl) .  

I used the compiz from the 7th of Feb, but i think any will work.

Then remove the compiz you just installed with dpkg and then re-install the compiz packages that you were using before.  You will find that the Compiz section will have appeared in the gconf-editor.[/QUOTE]

Nope, no luck. Tried with the Feb. 7th version, and even rebooted to be sure. No such thing in gconf-editor.

- Ketil

---

### Post by jocko on 2006-03-20
[QUOTE=kwaanens]Nope, no luck. Tried with the Feb. 7th version, and even rebooted to be sure. No such thing in gconf-editor.

- Ketil[/QUOTE]

Have you tried the one from [this]("http://www.ubuntuforums.org/showthread.php?t=139265") thread?
The tarball without 'src' in the filename contains all the .debs needed to get compiz running.

---

### Post by TB2 on 2006-03-20
Same here, trying on a **dapper flight 5**... compiz not showing up in gconf-editor. Also tried removing the package from the repository, installing the one from battlehorse, removing it, and reinstalling gompiz-gnome from the repository. Btw the package installer tells me that the version from battlehorse is tagged newer than the one from the repository. Starting compiz manually also doesnt work, altough Xgl is running. Also, until now window drawing is extremly slow and laggy. I also notice that the windows are somehow splittet in two half diagonally from the lower left to the upper right corner while being drawn. I think thats caused by Xgl running that slow.

Hardware is i386 / ATI 9600pro

edit: Also the debs in the tar jocko just postet dont work for me. They installed properly, but still no compiz in gconf-editor

---

### Post by acruxksa on 2006-03-21
Just FYI,
I followed the directions on [http://www.tectonic.co.za/view.php?id=916]("http://www.tectonic.co.za/view.php?id=916") and everything seems to be working well on my Dell I9200 (w/ati9700).  Video playback in MPlayer is still a work in progress, but everything else seems to work ok.  I did have to add the "resize" plugin after following the instructions, but am not sure why, I think when I cut/pasted it I left out the resize plugin.  Anyway things seem to run pretty smoothly and I'm now looking for info to put backgrounds on the top and bottom of the cube.  I disabled xv in gstreamer and tweaked mplayer a bit and things seem better, but i'm still not able to watch video fullscreen.

---

### Post by timmy334 on 2006-03-21
i am not getting the "shiver" effect when I grab a window while using Xgl as the xserver, however I get it when I run Xgl in a nested xserver. What gives? Anybody know how to correct that?

---

### Post by julipanno on 2006-03-21
> I'm now looking for info to put backgrounds on the top and bottom of the cube.
I tried entering the path to an svg-file in the cube plugin's settings in gconf, but nothing happened. I also had problems changing the color of the top and the bottom of the cube; I can enter a color hex, but it just pops back to the default.

> I disabled xv in gstreamer and tweaked mplayer a bit and things seem better, but i'm still not able to watch video fullscreen.
I also have a Dell I9200, and watch movies fullscreen in Xine with no problems.


Stian

---

### Post by massivevoid on 2006-03-23
[QUOTE=RaptorRaider]For some reason it is working now.

Lots of stuff seems broken though.
GDM is acting strange. Firefox is acting strange. Evolution suffers from the problem described below.

Many, many applications (those from the "System" menu + Evolution?) have a titleless title bar which cannot be moved (so the window can't be moved, though the bar is transparant). Neither do these apps appear in the bottom bar (which lists active apps). This bottom bar is also acting strange with apps which do appear.

Also Opacity isn't working. Edit: Nevermind, it **is** working; shortcuts are different than listed.

Anyone else having similar problems?

Overall though, this stuff is quite amazing.[/QUOTE]

I having the same problem. No "Close" "Minimize" "Maximize" buttons on top right window. Terminal stays "glued" to the top left screen, also without those buttons. Every window I open has no title bar.

On top of that, it freezes at the GUI login screen...or it will freeze when it loads to the desktop. I actually cannot get back in because of the freezing and I have to do a hard reboot. So, now I have to reinstall Dapper. :-| 

Awesome features, but testing needs to continue. I looked over at the NVIDIA thread and they have the worst bugs gone.

I hope we can solve these issues. :) 

-William

---

### Post by Fudgie on 2006-03-24
[QUOTE=massivevoid]On top of that, it freezes at the GUI login screen...or it will freeze when it loads to the desktop. I actually cannot get back in because of the freezing and I have to do a hard reboot. So, now I have to reinstall Dapper. :-| 
[/QUOTE]

Just get the boot menu from grub, select one of the recovery mode kernels, enter your root password when prompted and fix your config. (I often just do a 'chmod -x /etc/init.d/gdm' to stop gdm from launching, then 'chmod +x /etc/init.d/gdm' to enable it again later on). Ctrl-D when you're done to continue booting.

---

### Post by TB2 on 2006-03-24
As told, i've got the problem, that i can't start compiz, like some others here, and also there is no compiz entry in the cgonf-editor. I just tried a fglrxinfo, and now that was strange: It doesnt talk about mesa, nore about ati, it just tells me "Error: unable to open display :0"

I followed the tutorial, and checked my gdm.conf and gdm-conf-custom for typos, and there arent any. Is there something special about the two devices listed in the xorg.conf? There's a "ATI Technologies, Inc. RV350 AP [Radeon 9600]" entry, and a "ATI Graphics adapter 0" entry. I think that after I installed the proprietary ati driver, and initialized it, the first adapter still used "ati" and the second one was changed to "fglrx". I manually switched to "fglrx" so that both devices run that driver. The ati control center doesn't work eighter, offering no FireGL stuff.

I also reinstalled the driver with no succes. I'm completely sure, that everything is configred the way, the tutorial tells.

Any ideas?

---

### Post by philcolbourn on 2006-03-24
I can't run fglrx (compaq evo n620c ati mobility m7 7500). I can and do run radeon driver and DRI seems to be on so I thought I would see if any xgl stuff would work.

It does but...
1. mouse cursor is missing. it is very hard to navigate around the screen.
2. screen does not redraw properly. when the invisible mouse moves over something it redraws.
3. glxinfo says that I am no longer running DRI (with xgl off, DRI is on)
4. menu popups work and I guess the wobbly plugin is working since the popups wobble.
5. window switching is great - the OS-X switch user effect of a rotating cube. even on my setup it is smooth and fast and impressive.
6. transparency seems to be working but the srceen is so messed up due to the lack of redraws it is hard to tell.
7. At one point I had the login screen and a X session on the same screen - weird

I followed the instructions at the begining of this thread to the letter, but I needed to reboot after installing compiz so that the basic compiz gconf stuff is available for editting (probably a X restart would have done).

---

### Post by raketti on 2006-03-26
Tried to get Xgl working, but... Here's my xsession-errors, so if someone could point out what to do :/

[http://koti.mbnet.fi/tone/xsession-errors.txt](http://koti.mbnet.fi/tone/xsession-errors.txt)

If you need some more info, then please ask, cause I don't know where to look from.

And my videocard is Ati Radeon 9600 128MB
[I]
Edit: I have Dapper Flight-5 installed

Edit2: Got it working :D Dunno what I did :D But...[/I]

---

### Post by milpool on 2006-03-26
help! I just upgraded and my xgl/compiz broke! everything was working fine and running smoothly and such. until I upgraded, restarted and now I have no title bar (maximize, close, etc.) And cannot move windows around. I did not change anything. I think I had this problem when I was first installing it, but I cannot remember what I did to fix it. If anyone can provide any help it would be greatly appreciated thank you very much.

---

### Post by The Warlock on 2006-03-26
So I installed everything according to the directions and I've got the newerest packages from that special repository and everything is working great except for one thing: For some reason, gdm tries to start twice. Now, with the fglrx drivers, when GDM starts on top of itself I get major problems with artifacts and such. If I kill all the gdm processes (from a tty) and then just start it once, I get into Gnome just fine and everything works perfectly. 

Anyone know what could be causing this?

---

### Post by TB2 on 2006-03-26
For all those that have problems getting compiz to start altough Xgl runs fine and everything looks good, it's most likely that your driver - probably fglrx - isn't installed correctly.

Because "fglrxinfo" will give you an error, check with: ```
fglrxinfo -display :1.0
```If it talks about Mesa, that's bad, and that's why compiz won't start. This thread may be useful, altough it wasn't for me :/ 
[http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283)

---

### Post by thieummm on 2006-03-27
You forgot to mention compiz-gnome in the list of package to install (this package contains gnome-window-decorator).

---

### Post by Shadou on 2006-03-27
[QUOTE=mattisking]Many people have contributed to this, some more than others as I've picked up the pieces I needed to make this work from through-out these forums. 
But, in particular: terrax, JoWilly, and poofyhairguy

1. Get your xorg.conf setup properly. The main thread has more than enough information on this. Follow it paying attention to the ATI differences that are well noted.

Just to be clear however, these instructions are targeted for those people using the ATI Proprietary Driver ("fglrx"). This is configured in your xorg.conf. If you're using "ati" that's not going to work for you. If you're using "radeon" then this is theoretically possible (radeon is the OSS driver targeted more - for now - for your lower end Radeon cards, in particular the 9000/9200/9250)... but I wasn't able to get it to work with my lower end PC that uses the 9200. In both cases, there are known/outstanding bugs with both sets of drivers that require work arounds described below. 

To make sure you are "accelerated", running with the new driver, try typing fglrxinfo in a terminal and see what you get. If it talks about ATI then awesome... if it talks about Mesa, you still don't have your driver setup properly (xorg.conf).

**For ATI do not enable composite in xorg.conf, xgl does not need it.

2. Install all the new stuff from the Dapper universe repository... this includes xserver-xgl, compiz, libgl1-mesa, libgl1-mesa-dri, libglitz1, libglitz-glx1 and any dependencies.

3. Modify /etc/gdm/gdm.conf-custom - For most this file is generally full of empty stubs.  Look for the one called [servers] and do this:

```
[servers] 
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

```

4. Modify /etc/gdm/gdm.conf to change your display:
```
#0=Standard
1=Standard

```

** You may have noticed in both steps 3 and 4 that we're using Display 1 instead of 0... this is due to a bug in the current proprietary ATI driver and this is the workaround.

5. Another bug in the driver... And for video, there is a bug with xv, so we want to start "gstreamer-properties" and tell it not to use xv for video. (This is the same as starting "Multimedia Systems Selector", a Preferences application that is currently hidden in your menu system)

6. Modify your session ("Menu System" -> "Preferences" -> "Sessions") by adding in the following two items:
```
gnome-window-decorator *(must be on top, start first) *
compiz --replace gconf
```

7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order:
```
gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```
It MUST be in this order as there are dependencies between them. If you've already been playing with this from earlier debs - maybe from battlehorse, or maybe you rolled your own - this is an important step because it's very likely in the wrong order. Most people that are missing certain plugins or are missing things like "alt-switch" will find they need to correct this and restart.

8. To get around the problem with <Shift> and <Backspace> enter this in your terminal whenever you login:
```
xmodmap /usr/share/xmodmap/xmodmap.<language>
```
where <language> refers to your country's code. For the US, it would be:
```
xmodmap /usr/share/xmodmap/xmodmap.us
```

Once everything is running along happily, this is a good appendix for the commands for using the nifty stuff compiz gives you:
[http://en.opensuse.org/Compiz]("http://en.opensuse.org/Compiz")

That's about as easy as I can make it. Good luck.

**Some Issues**
[LIST]
[*]This is a wonderful resource for looking into your video card/driver: [http://en.opensuse.org/Xgl]("http://en.opensuse.org/Xgl")
[*]It appears that you might need a 9800 or better ATI right now.
[*]It appears there may be problems with Mobility users (laptops)
[*]The latest compiz package may have a bug that doesn't put the necessary gconf settings in place. One possible work-around is to install the battlehorse v1 deb for compiz, then update to the universe deb.
[/LIST]

**UPDATES: **I will be trying a few new things this evening (US, EST) and will post any more updates at that time.[/QUOTE]


mattisking, would you be able to reference this post or the details of it somewhere in your post? It fixes the lockup issues for users of ATI pci-express cards - [http://www.ubuntuforums.org/showthread.php?t=150854](http://www.ubuntuforums.org/showthread.php?t=150854)

thanks :)

---

### Post by Kiphaas7 on 2006-03-27
I finally got it working, because it didn't show up in gconfig. I simply followed the instructions below in terminal.

Only problem is, I lost my menubars, meaning I can't move shit. Using the latest compiz package from quinnstorm.

So my question is:

-Does it have anything to do with the gnome-window-decorator? If so, what is meant in the startpost by making sure it is started first, by entering it first in sessions or by making sure it is on top of the list?

-Or, does it have anything to do with the order of the compiz effects? Because in the post below there is a different order then in the startpost. (startpost says: ```
decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```)

-Or something else.

Sorry, really tired now, after reading +/-100 pages in various threads trying to get compiz to work.

Well, off to a clean install, and hopefully to do it right this time.


[QUOTE=risbac]ATI AIW9600 Pro / PIV 2.8Ghz / 1Go
Dapper, Xgl from repo, fglrx driver
Xgl is running with a modified gdm.conf & -custom
I would have said quite stable, but my post was just deleted with a crash : )

To start Compiz, I had to remove "gconf" from the command line. 

```
compiz decoration move resize place switcher wobbly fade minimize cube rotate zoom scale --replace 
```

If I add gconf anywhere in the command, it's failing. I don't know why. All the other plugins are working fine, be careful with the order, you can't change it the way you want, there are some dependencies (some plugins must be loaded before others).

No need of any sudo, you can forget about my previous advise.

So far, it's very smooth, I will talk about the stability after some tests.[/QUOTE]

---

### Post by zcacmjw on 2006-03-30
[QUOTE=The Warlock]So I installed everything according to the directions and I've got the newerest packages from that special repository and everything is working great except for one thing: For some reason, gdm tries to start twice. Now, with the fglrx drivers, when GDM starts on top of itself I get major problems with artifacts and such. If I kill all the gdm processes (from a tty) and then just start it once, I get into Gnome just fine and everything works perfectly. 

Anyone know what could be causing this?[/QUOTE]

I think I've got something similar, except gdm crashes as it's starting the second time.

Xgl works fine from the console and there's no evidence in the logs that gdm's actually starting Xgl before crashing and locking up the entire pc (even ssh access)

---

### Post by cornelius2 on 2006-03-30
I got xgl/compiz working without crashing on Mobility X300, fglrx driver v8.23.7 on Dapper Flight 5. However, I have one annoying problem. Xgl seems to have high cpu usage (60-70%) while I'm rotating the cube, moving the windows, etc. ](*,)   

EDIT: It does this when a large portion of the screen changes in general (during compiz effects and also during scrolling in Firefox). Yes, Xgl has high cpu usage while scrolling a page rather than Firefox itself. I also observed that during video playback, again Xgl uses the large portion of cpu cycles instead of the video player itself.

I read that Xgl should use very little cpu itself. So, does anybody know how to get Xgl to use the gpu instead of cpu? I would appreciate any ideas to fix this issue.

I have this problem with the xgl and compiz from universe repositories and also with xgl 7.0.0-0ubuntu5 and compiz 0.0.7-0ubuntu13.

By the way, output of glxinfo says there is no direct rendering on display :1. Is this the problem? If so, how can I fix this?
```
$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 1.2 (2.0.5695 (8.23.7))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon
```

And fglrxinfo says:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5695 (8.23.7)

$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 1.2 (2.0.5695 (8.23.7))
```

And my xorg.conf is:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad" "CorePointer"
	Option	    "Clone" "off"
	Option	    "Xinerama" "off"
EndSection

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	# Outer			(52,46-995,728)	Observed bounding box
	# Probably really	(0,0-1000,750)	Bezel covers some active area
	# Inner			(100,100-950,670) Outside this is a corner tap
	# speed: MinSpeed if slow, MaxSpeed if fast.  With driver 0.13.5,
	# units were different and 0.65, 0.15 were my preferred values.
	# A = AccelFactor.  Then dS = A * dP * dP but limited by 
	# {Min,Max}Speed * dP.  Packets come out a time dT apart, where we can 
	# only guess what dT is.  Empirically, A = 0.05 gives a speed of about 
	# 1.0, i.e. 1 pixel per pad unit, if you cross the pad in 1 second.
	# packets, scrolling continues until you tap.  0 -> disable.
	# Alps pad poorly gives Z (compared to Synaptics), so this scaling
	# is not used.  Speed may be screen pixels/sec.
	# tap inside with N fingers.  0 -> nothing, 1 = left button, 
	# 2 = middle button, 3 = right button.  The Alps pad cannot distinguish
	# multiple fingers.
	# Unlike the Synaptics pad, on a tap the Alps pad sends one single
	# packet (hardware detection) with Z=16 followed 100 msec later by one 
	# in the exact same place with Z=0.  (Never < 90 msec, always < 110
	# msec.)  (There's a kernel patch to kludge around this.)
	# In order for a tap to be recognized:
	# Touch and release must be no more distant than this (pad units)
	# NOTE! Change to 210 with Alps hardware tap patch mentioned above.
	# jimc uses 110 without the patch.
	# be long enough so you can see the button change color.
	# edge, 2 = top right corner, etc. around the edge of the pad up to
	# 8 = top left corner.
	Option	    "InputFashion" "Mouse"
	Option	    "Name" "AlpsPS/2 ALPS TouchPad"
	Option	    "Vendor" "Sysp"
	Option	    "Protocol" "imps/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "Buttons" "8"
	Option	    "ZAxisMapping" "4 5 6 7"
	# Allows synclient to configure the driver in real time.
	Option	    "SHMConfig" "on"
	# Corners of Alps Glidepoint touchpad: 
	Option	    "TopEdge" "100"
	Option	    "BottomEdge" "600"
	Option	    "LeftEdge" "100"
	Option	    "RightEdge" "860"
	# "Speeds" are in screen pixels per pad unit.  Ratio scales with finger
	Option	    "MaxSpeed" "0.8"
	Option	    "MinSpeed" "0.4"
	# dS = change in screen pixels; dP = change in pad units per "packet"; 
	Option	    "AccelFactor" "0.03"
	# X or Y pad motion for each scroll event (simulated button)
	Option	    "VertScrollDelta" "25"
	Option	    "HorizScrollDelta" "25"
        # If scroll speed (events/sec) is above this value for 4 successive
	Option	    "CoastingSpeed" "3.0"
	# Edge motion speed scales with Z axis (pressure).  However, the
	Option	    "EdgeMotionMinZ" "65"
	Option	    "EdgeMotionMaxZ" "80"
	Option	    "EdgeMotionMinSpeed" "150"
	Option	    "EdgeMotionMaxSpeed" "150"
	# True -> use for normal movement, false -> only for dragging.
	Option	    "EdgeMotionUseAlways" "off"
	# What happens when you tap the {Left,Right}{Top,Bottom} corner or
	Option	    "LBCornerButton" "2"
	Option	    "LTCornerButton" "0"
	Option	    "RBCornerButton" "3"
	Option	    "RTCornerButton" "0"
	Option	    "TapButton1" "1"
	Option	    "TapButton2" "3"
	Option	    "TapButton3" "0"
	# If Z axis is above FingerHigh -> touch.  Below FingerLow -> release.
	Option	    "FingerHigh" "15"
	Option	    "FingerLow" "10"
	# (Note: defaults for the next 3 come out to 220 180 180 for Synaptics)
	Option	    "MaxTapMove" "200"
	# Release must follow touch no longer than this (msec)
	Option	    "MaxTapTime" "210"
	# Second tap must follow release this closely to recognize double tap.
	Option	    "MaxDoubleTapTime" "150"
	# How long between emulated button-down and button-up events.  Should
	Option	    "ClickTime" "100"
	# If physical buttons 1 and 3 are hit within this time, do button 2.
	Option	    "EmulateMidButtonTime" "150"
	# 0 = enable, 1 = disable completely, 2 = only tapping is disabled
	Option	    "TouchpadOff" "0"
	# On -> drag continues until you tap a second time.
	Option	    "LockedDrags" "off"
# These features are not turned on.
	Option	    "GuestMouseOff" "off"
	Option	    "CircularScrolling" "off"
	# Angle in radians for each scroll event
	Option	    "CircScrollDelta" "0.2"
	# Where do you touch to start circular scroll?  0 -> any edge, 1 = top 
	Option	    "CircScrollTrigger" "0"
	Option	    "PalmDetect" "off"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseInternalAGPGART" "no"
	Option		"KernelModuleParm" "agplock=0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerFlags"
	Option	    "AllowMouseOpenFail"
# Resize and Rotate extension, allows screen geometry changes on the fly.
	Option	    "RandR" "on"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by kakashi on 2006-03-31
> 
7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order:
Code:

gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher



this is the step i can't do. i simply don't see compiz in thhe gconf-editor. 
also if i restart gdm (without doing this and the following steps bad things happen everytime i open a window. 
using dapper 5.

---

### Post by cornelius2 on 2006-03-31
[QUOTE=kakashi]this is the step i can't do. i simply don't see compiz in thhe gconf-editor. 
also if i restart gdm (without doing this and the following steps bad things happen everytime i open a window. 
using dapper 5.[/QUOTE]

Try running compiz like this:
```
compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```

I wasn't putting gconf in the arguments, and I couldn't see compiz in gconf settings. When I ran it with gconf argument like above, it solved that problem for me.

---

### Post by Tymon on 2006-04-03
[QUOTE=kakashi]this is the step i can't do. i simply don't see compiz in thhe gconf-editor. 
also if i restart gdm (without doing this and the following steps bad things happen everytime i open a window. 
using dapper 5.[/QUOTE]

Exact same problem here. I can fire up compiz using the --replace gconf stuff and all but then all window borders disappear, every windows just docks at the top left of the screen and I don't see any effects of compiz (no wobbly windows, no expose clone, not anything).

I wonder what is stopping compiz from showing up in the gconf editor. I also have a PC with an nvidia card, I also installed Ubuntu on that PC and followed the nvidia guide for Xgl and all works fine, and compiz shows up in the gconf editor like it should.

---

### Post by Fudgie on 2006-04-03
[QUOTE=Tymon]Exact same problem here. I can fire up compiz using the --replace gconf stuff and all but then all window borders disappear, every windows just docks at the top left of the screen and I don't see any effects of compiz (no wobbly windows, no expose clone, not anything).

I wonder what is stopping compiz from showing up in the gconf editor. I also have a PC with an nvidia card, I also installed Ubuntu on that PC and followed the nvidia guide for Xgl and all works fine, and compiz shows up in the gconf editor like it should.[/QUOTE]

That's because Compiz is killing Metacity or whatever other window manager you're running, and then failing to start up leaving you without a window manager. I need to
```

LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 compiz --replace gconf 

```
to get it running on my ATI setup.

---

### Post by Tymon on 2006-04-03
I don't have the libGL.so.1.2 files. Which package do they come with?

---

### Post by zachtib on 2006-04-03
any update on getting this to work with an ATI Radeon Mobility 9000?

I was getting the corrupted screen bug a while ago.

What driver, etc should I use?

---

### Post by Fudgie on 2006-04-04
[QUOTE=Tymon]I don't have the libGL.so.1.2 files. Which package do they come with?[/QUOTE]

libgl1-mesa

---

### Post by superm1 on 2006-04-04
Some time ago, back when compiz/xgl were released a whole lot of people encountered this bug about no support for non-power of two textures when using fglrx drivers.  I was one of the people to encounter this, and have nearly everything but wipe the box.  

I have reinstalled every library I could think of that would be related to Xgl, glitz, mesa-gl,mesa-glu, fglrx.  I know that 3D acceleration works as I play nwn in xorg regular.  Also fglrxinfo gives me the correct results.  Anyone who had this problem and resolved it - can you speak up and say what you did?

Relavent Symlinks
```
supermario@portablemario:~$ ls -alh /usr/lib/fglrx/libGL.so.1.2.xlibmesa
lrwxrwxrwx 1 root root 40 2006-02-20 12:32 /usr/lib/fglrx/libGL.so.1.2.xlibmesa -> /usr/share/fglrx/diversions/libGL.so.1.2
supermario@portablemario:~$ ls -alh /usr/share/fglrx/diversions/
total 400K
drwxr-xr-x 2 root root   80 2006-03-30 22:09 .
drwxr-xr-x 3 root root   80 2006-02-18 01:19 ..
-rw-r--r-- 1 root root 398K 2006-03-23 10:04 libGL.so.1.2
```

Fgrlxinfo (in xorg)
```
supermario@portablemario:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FIREGL T2 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.5755 (8.23.7)
```


/etc/gdm/gdm.conf-custom
```
.
.
.

[servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).
1=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :1 -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true


```


/etc/X11/xorg.conf
```
.
.
.
Section "Device"
        Identifier  "ATI Technologies, Inc. FireGL Mobility T2 (M10 NT)"
        Driver      "fglrx"
#       Option      "PowerState" "1"
#       Option      "VideoOverlay" "on"
#       Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. FireGL Mobility T2 (M10 NT)"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
.
.
.
```

---

### Post by Fudgie on 2006-04-05
I've had that problem when I've tried running Xgl directly. The only way I've been able to get it to work, is start Xorg normally, then Xgl :1 ... on top of that at a later time.

---

### Post by Tymon on 2006-04-05
[QUOTE=Fudgie]I've had that problem when I've tried running Xgl directly. The only way I've been able to get it to work, is start Xorg normally, then Xgl :1 ... on top of that at a later time.[/QUOTE]

That's exactly what I'm doing, but that takes away the experience I think.

---

### Post by Tychondriax on 2006-04-06
Hello people, I'm new on this forum (sorry for my bad english... :P ), and I'm trying to have my first steps in the world of ubuntu, so I'm pretty newbie on linux... :)

I've tried to follow this howto to install Xgl on my laptop, but I had many problems... 
First of all, I've a Compaq Presario R4000 laptop, Amd Sempron 1.8 GHz, 384 MB RAM + 128 Mb shared with graphic card, an Ati Radeon xpress 200M.

I've installed the latest release of Dapper on previous Breezy  and then latest fglrx drivers (that are working fine... :D)

Then I've installed all the packages needed for Xgl, and I followed this tutorial, but I had the following problems...

If I reboot after having changed server options on gdm.conf and gdm.conf-custom, Xgl seems to load, but then it freezes after loading few icons and only sometimes panels, and if i try to open a window, it appears without borders and stucks in the top left corner, covering the application menu... and however no one of the effects works... It's only much slower... :???: 

If I try to start only Xgl from command line, I have this error... 
```
/usr/local/bin/Xgl: line 18: /opt/fdo/bin/gnome-window-decorator: No such file or directory
/usr/local/bin/Xgl: line 19: /opt/fdo/bin/compiz: No such file or directory
gnome-session: you're already running a session manager

```
I've searched on hd, but /opt folder doesn't contain other folders but those one of firefox and kde3

Then I've tried to launch compiz from command line, but this time i had this error:
```
dominic@TycLinux:~$ compiz.real: No composite extension
```

Last i've also tried to launch gnome-window-decorator, and, suprise, another error:
```
gnome-window-decorator, Failed to load shadow images
```

So there are three possibilities:
1. I've forgotten something (but I'm pretty sure having followed this tutorial step by step)
2. I need other packages or to modify other parameters
3. my laptop hates me :lol:

Can u help me please? thx... :D

---

### Post by p47 on 2006-04-06
Hello Everybody, I hope ypu can understandme my englis is very bad jo !

I have some problems in with the gconf-editor I was maked all that the manual said but in that step I had problems because I can't see all the files only when I enter to gconf-editor I can see apps folder, but I don't have compiz.........

Can you help me with this ?
And I have the least question: in the step when you go to ("Menu System" -> "Preferences" -> "Sessions") . ok My ubutu is in spanish but the howto said me that I  have to add this:

gnome-window-decorator
compiz --replace gconf
But is this in with part ?
is this in session options or in start programs ?
Yesteday when I type this in the sessions options never could quit this...
Thank&#347; alot
Regards

---

### Post by yellow beard on 2006-04-07
Ive got it working under breezy but im having a few problems. Nothing too major.
This is what my xorg.conf looks like

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "AOC Spectrum"
	Option	    "DPMS"

EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
	HorizSync     30-72
	VertRefresh   50-130
	# V-freq: 70.00 Hz  // h-freq: 70.15 KHz
	Modeline "1280x960" 125.14  1280 1344 1496 1784   960  960  963 1002
	# V-freq: 80.00 Hz  // h-freq: 72.61 KHz
	Modeline "1152x864" 117.91  1152 1216 1360 1624   864  864  867  907 
	# V-freq: 85.00 Hz  // h-freq: 68.79 KHz
	Modeline "1024x768" 97.40  1024 1072 1192 1416   768  768  771  809
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Monitor    "AOC Spectrum"
	DefaultDepth     24

EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

I know ive got somthing wrong in there becuase the ati control panal doesnt work and if i try run fglrxinfo i get it says Error: unable to open display : 0. Also when i quit a opengl game i get a huge res with half of the screen unusuable.

---

### Post by yellow beard on 2006-04-07
Also this is what i have in my gdm.conf

```

#0=Standard
1=Xgl
#1=Standard

[server-Xgl]
name=Xgl server
command=/usr/X11R6/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
```

Not sure if i should have #1 uncommented or not?

---

### Post by Tychondriax on 2006-04-07
Ok, i've tried to solve compiz problem by putting the following lines at the end of xorg.conf (even if you said it was'n necessary with fglrx drivers):
```
Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```
But in this case fglrx driver deactivates by itself :-? , and switch to mesa driver...
and however if I try to execute compiz, i get the three famous error lines... :)

---

### Post by dr_d on 2006-04-10
[QUOTE=Fudgie]That's because Compiz is killing Metacity or whatever other window manager you're running, and then failing to start up leaving you without a window manager. I need to
```

LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 compiz --replace gconf 

```
to get it running on my ATI setup.[/QUOTE]


I've got XGL running on my I9400 laptop (nvidia), but I'm getting the same problem. Window boarders are not showing, and I can't move windows around the screen.

Could you please clarify on the solution? Is LD_PRELOAD a command?

Those who recommended  starting Xorg normally, then Xgl :1 ... on top of that at a later time, could you please explain exactly how to do this?

Much appreciated.

---

### Post by Fudgie on 2006-04-10
[QUOTE=dr_d]I've got XGL running on my I9400 laptop (nvidia), but I'm getting the same problem. Window boarders are not showing, and I can't move windows around the screen.

Could you please clarify on the solution? Is LD_PRELOAD a command?

Those who recommended  starting Xorg normally, then Xgl :1 ... on top of that at a later time, could you please explain exactly how to do this?

Much appreciated.[/QUOTE]

If you can't move windows and don't have borders, you're not running compiz. What's the error you get when you try starting compiz? Nvidia doesn't need the LD_PRELOAD hack, and it doesn't need to be started on :1 either.

---

### Post by Fudgie on 2006-04-10
[QUOTE=Tychondriax]Ok, i've tried to solve compiz problem by putting the following lines at the end of xorg.conf (even if you said it was'n necessary with fglrx drivers):
```
Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```
But in this case fglrx driver deactivates by itself :-? , and switch to mesa driver...
and however if I try to execute compiz, i get the three famous error lines... :)[/QUOTE]

fglrx doesn't allow accelerated opengl along with compositing. You don't need that extension in xorg.conf, as Xgl has it's own built in compositing implementation.

---

### Post by dr_d on 2006-04-10
pls disregard - moved to nvidia thread

---

### Post by forbmj on 2006-04-12
[QUOTE=mattisking]Many people have contributed to this, some more than others as I've picked up the pieces I needed to make this work from through-out these forums. 
But, in particular: terrax, JoWilly, and poofyhairguy

1. Get your xorg.conf setup properly. The main thread has more than enough information on this. Follow it paying attention to the ATI differences that are well noted.

Just to be clear however, these instructions are targeted for those people using the ATI Proprietary Driver ("fglrx"). This is configured in your xorg.conf. If you're using "ati" that's not going to work for you. If you're using "radeon" then this is theoretically possible (radeon is the OSS driver targeted more - for now - for your lower end Radeon cards, in particular the 9000/9200/9250)... but I wasn't able to get it to work with my lower end PC that uses the 9200. In both cases, there are known/outstanding bugs with both sets of drivers that require work arounds described below. 

To make sure you are "accelerated", running with the new driver, try typing fglrxinfo in a terminal and see what you get. If it talks about ATI then awesome... if it talks about Mesa, you still don't have your driver setup properly (xorg.conf).

**For ATI do not enable composite in xorg.conf, xgl does not need it.

2. Install all the new stuff from the Dapper universe repository... this includes xserver-xgl, compiz, libgl1-mesa, libgl1-mesa-dri, libglitz1, libglitz-glx1 and any dependencies.

3. Modify /etc/gdm/gdm.conf-custom - For most this file is generally full of empty stubs.  Look for the one called [servers] and do this:

```
[servers] 
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

```

4. Modify /etc/gdm/gdm.conf to change your display:
```
#0=Standard
1=Standard

```

** You may have noticed in both steps 3 and 4 that we're using Display 1 instead of 0... this is due to a bug in the current proprietary ATI driver and this is the workaround.

5. Another bug in the driver... And for video, there is a bug with xv, so we want to start "gstreamer-properties" and tell it not to use xv for video. (This is the same as starting "Multimedia Systems Selector", a Preferences application that is currently hidden in your menu system)

6. Modify your session ("Menu System" -> "Preferences" -> "Sessions") by adding in the following two items:
```
gnome-window-decorator *(must be on top, start first) *
compiz --replace gconf
```

7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order:
```
gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```
It MUST be in this order as there are dependencies between them. If you've already been playing with this from earlier debs - maybe from battlehorse, or maybe you rolled your own - this is an important step because it's very likely in the wrong order. Most people that are missing certain plugins or are missing things like "alt-switch" will find they need to correct this and restart.

8. To get around the problem with <Shift> and <Backspace> enter this in your terminal whenever you login:
```
xmodmap /usr/share/xmodmap/xmodmap.<language>
```
where <language> refers to your country's code. For the US, it would be:
```
xmodmap /usr/share/xmodmap/xmodmap.us
```

Once everything is running along happily, this is a good appendix for the commands for using the nifty stuff compiz gives you:
[http://en.opensuse.org/Compiz]("http://en.opensuse.org/Compiz")

That's about as easy as I can make it. Good luck.

**Some Issues**
[LIST]
[*]This is a wonderful resource for looking into your video card/driver: [http://en.opensuse.org/Xgl]("http://en.opensuse.org/Xgl")
[*]It appears that you might need a 9800 or better ATI right now.
[*]It appears there may be problems with Mobility users (laptops)
[*]The latest compiz package may have a bug that doesn't put the necessary gconf settings in place. One possible work-around is to install the battlehorse v1 deb for compiz, then update to the universe deb.
[/LIST]

**UPDATES: **I will be trying a few new things this evening (US, EST) and will post any more updates at that time.[/QUOTE]
I did everything as the first one told me on my laptop T43 ATI x300, but I couldn't see any thing except the following error message: 

compiz.real: No composite extension

gnome-window-decorator, Failed to load shadow images

so what can I do?

---

### Post by superm1 on 2006-04-12
[quote=dr_d]I've got XGL running on my I9400 laptop (nvidia), but I'm getting the same problem. Window boarders are not showing, and I can't move windows around the screen.

Could you please clarify on the solution? Is LD_PRELOAD a command?

Those who recommended  starting Xorg normally, then Xgl :1 ... on top of that at a later time, could you please explain exactly how to do this?

Much appreciated.[/quote]
Take a look at the contents of /usr/bin/compiz and you'll see why you shouldn't need to LD_PRELOAD:
```
supermario@portablemario:~$ cat /usr/bin/compiz
#!/bin/bash

if [ -f /usr/lib/nvidia/libGL.so.1.2.xlibmesa ]; then
        LD_PRELOAD=/usr/lib/nvidia/libGL.so.1.2.xlibmesa compiz.real $@ & exit;
fi

if [ -f /usr/lib/fglrx/libGL.so.1.2.xlibmesa ]; then
        LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz.real $@ & exit;
fi

compiz.real $@ & exit;

```
```

supermario@portablemario:~$ ls -alh /usr/lib/fglrx/

total 79K
drwxr-xr-x   2 root root  88 2006-02-20 12:32 .
drwxr-xr-x 183 root root 80K 2006-04-12 11:18 ..
lrwxrwxrwx   1 root root  40 2006-02-20 12:32 libGL.so.1.2.xlibmesa -> /usr/share/fglrx/diversions/libGL.so.1.2
```

```
supermario@portablemario:~$ ls -alh /usr/share/fglrx/diversions/
total 400K
drwxr-xr-x 2 root root   80 2006-03-30 22:09 .
drwxr-xr-x 3 root root   80 2006-02-18 01:19 ..
-rw-r--r-- 1 root root 398K 2006-03-23 10:04 libGL.so.1.2
```

```
supermario@portablemario:~$ dpkg-divert --list | grep fglrx
diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx
```

Understand better now?

---

### Post by anodizer on 2006-04-16
[QUOTE=forbmj]I did everything as the first one told me on my laptop T43 ATI x300, but I couldn't see any thing except the following error message: 

compiz.real: No composite extension

gnome-window-decorator, Failed to load shadow images

so what can I do?[/QUOTE]

I'm having the same problem. Xgl appears to be running though:
```
ps ax | grep Xgl
 4631 ?        S      0:00 /usr/bin/Xgl :1 :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer -auth /var/lib/gdm/:1.Xauth -nolisten tcp vt7
 5754 pts/0    S+     0:00 grep Xgl
```

So where's the problem? I red same pages back that if you load composite extension with xorg you bypass this problem but don't actually solve it.

---

### Post by tokez on 2006-04-16
I think I have correctly installed XGL/compiz using this guide, however nothing loads when I run the gdm.

I go to my root terminal and type sudo /etc/init.d/gdm start and it goes to the screen right before my login screen and "loads" forever.

Here is my gdm.conf

```

# GDM Configuration file.  You can use gdmsetup program to graphically
# edit this, or you can optionally just edit this file by hand.  Note that
# gdmsetup does not tweak every option here, just the ones most users
# would care about.  Rest is for special setups and distro specific
# tweaks.  If you edit this file, you should run:
# /etc/init.d/gdm reload or /etc/init.d/gdm restart

# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Some of these are commented out but still show their default values.
# If you wish to change them you must remove the '#' from the beginning of
# the line.  The commented out lines are lines where the default might
# change in the future, so set them one way or another if you feel
# strongly about it.
#
# Have fun! - George

[daemon]
# Automatic login, if true the first local screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain
# amount of time
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30

# The gdm configuration program that is run from the login screen, you should
# probably leave this alone
#Configurator=/usr/sbin/gdmsetup --disable-sound --disable-crash-dialog

# The chooser program.  Must output the chosen host on stdout, probably you
# should leave this alone
#Chooser=/usr/lib/gdm/gdmchooser

# The greeter for local (non-xdmcp) logins.  Change gdmlogin to gdmgreeter to
# get the new graphical greeter.
Greeter=/usr/lib/gdm/gdmgreeter

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
#RemoteGreeter=/usr/lib/gdm/gdmlogin

# Launch the greeter with an additional list of colon seperated gtk 
# modules. This is useful for enabling additional feature support 
# e.g. gnome accessibility framework. Only "trusted" modules should
# be allowed to minimise security holes
#AddGtkModules=false
# By default these are the accessibility modules
#GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener

# Default path to set.  The profile scripts will likely override this
DefaultPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
# Default path for root.  The profile scripts will likely override this
RootPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

# If you are having trouble with using a single server for a long time and
# want gdm to kill/restart the server, turn this on
#AlwaysRestartServer=false

# User and group used for running gdm GUI applicaitons.  By default this
# is set to user gdm and group gdm.  This user/group should have very
# limited permissions and access to ony the gdm directories and files.
User=gdm
Group=gdm

# To try to kill all clients started at greeter time or in the Init script.
# doesn't always work, only if those clients have a window of their own
#KillInitClients=true
LogDir=/var/log/gdm
# You should probably never change this value unless you have a weird setup
PidFile=/var/run/gdm.pid
# Note that a post login script is run before a PreSession script.
# It is run after the login is successful and before any setup is
# run on behalf of the user
PostLoginScriptDir=/etc/gdm/PostLogin/
PreSessionScriptDir=/etc/gdm/PreSession/
PostSessionScriptDir=/etc/gdm/PostSession/
DisplayInitDir=/etc/gdm/Init
# Distributions:  If you have some script that runs an X server in say
# VGA mode, allowing a login, could you please send it to me?
#FailsafeXServer=
# if X keeps crashing on us we run this script.  The default one does a bunch
# of cool stuff to figure out what to tell the user and such and can
# run an X configuration program.
XKeepsCrashing=/etc/gdm/XKeepsCrashing
# Reboot, Halt and suspend commands, you can add different commands
# separated by a semicolon and gdm will use the first one it can find
RebootCommand=/sbin/shutdown -r now "Rebooted from gdm menu."
HaltCommand=/sbin/shutdown -h now "Halted from gdm menu."
SuspendCommand=/usr/sbin/pmi action sleep
HibernateCommand=/usr/sbin/pmi action hibernate
# Probably should not touch the below this is the standard setup
ServAuthDir=/var/lib/gdm
# This is our standard startup script.  A bit different from a normal
# X session, but it shares a lot of stuff with that.  See the provided
# default for more information.
BaseXsession=/etc/gdm/Xsession
# This is a directory where .desktop files describing the sessions live
# It is really a PATH style variable since 2.4.4.2 to allow actual
# interoperability with KDM.  Note that <sysconfdir>/dm/Sessions is there
# for backwards compatibility reasons with 2.4.4.x
SessionDesktopDir=/etc/X11/sessions/:/etc/dm/Sessions/:/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/
# This is the default .desktop session.  One of the ones in SessionDesktopDir
DefaultSession=default.desktop
# Better leave this blank and HOME will be used.  You can use syntax ~/ below
# to indicate home directory of the user.  You can also set this to something
# like /tmp if you don't want the authorizations to be in home directories.
# This is useful if you have NFS mounted home directories.  Note that if this
# is the home directory the UserAuthFBDir will still be used in case the home
# directory is NFS, see security/NeverPlaceCookiesOnNFS to override this behaviour.
UserAuthDir=
# Fallback if home directory not writable
UserAuthFBDir=/tmp
UserAuthFile=.Xauthority
# The X server to use if we can't figure out what else to run.
StandardXServer=/usr/X11R6/bin/X
# The maximum number of flexible X servers to run.
#FlexibleXServers=5
# And after how many minutes should we reap the flexible server if there is
# no activity and no one logged on.  Set to 0 to turn off the reaping.
# Does not affect Xnest flexiservers.
#FlexiReapDelayMinutes=5
# the X nest command
Xnest=/usr/X11R6/bin/Xnest -br -audit 0 -name Xnest
# Automatic VT allocation.  Right now only works on Linux.  This way
# we force X to use specific vts.  turn VTAllocation to false if this
# is causing problems.
FirstVT=7
VTAllocation=true
# Should double login be treated with a warning (and possibility to change
# vts on linux and freebsd systems for console logins)
#DoubleLoginWarning=true
# Should a second login always resume the current session and
# switch vts on linux and freebsd systems for console logins
#AlwaysLoginCurrentSession=true

# If true then the last login information is printed to the user before
# being prompted for password.  While this gives away some info on what
# users are on a system, it on the other hand should give the user an
# idea of when they logged in and if it doesn't seem kosher to them,
# they can just abort the login and contact the sysadmin (avoids running
# malicious startup scripts)
#DisplayLastLogin=false

# Program used to play sounds.  Should not require any 'daemon' or anything
# like that as it will be run when no one is logged in yet.
SoundProgram=/usr/lib/gdmplay

# These are the languages that the console cannot handle because of font
# issues.  Here we mean the text console, not X.  This is only used
# when there are errors to report and we cannot start X.
# This is the default:
#ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh

# This determines whether gdm will honor requests DYNAMIC requests from
# the gdmdynamic command.
#DynamicXServers=false

# This determines whether gdm will send notifications to the console
#ConsoleNotify=true

[security]
# If any distributions ship with this one off, they should be shot
# this is only local, so it's only for say kiosk use, when you
# want to minimize possibility of breakin
AllowRoot=false
# If you want to be paranoid, turn this one off
AllowRemoteRoot=false
# This will allow remote timed login
AllowRemoteAutoLogin=false
# 0 is the most restrictive, 1 allows group write permissions, 2 allows all
# write permissions
RelaxPermissions=0
# Check if directories are owned by logon user.  Set to false, if you have, for
# example, home directories owned by some other user.
CheckDirOwner=true
# Number of seconds to wait after a bad login
#RetryDelay=1
# Maximum size of a file we wish to read.  This makes it hard for a user to DoS
# us by using a large file.
#UserMaxFile=65536
# If true this will basically append -nolisten tcp to every X command line,
# a good default to have (why is this a "negative" setting? because if
# it is false, you could still not allow it by setting command line of
# any particular server).  It's probably better to ship with this on
# since most users will not need this and it's more of a security risk
# then anything else.
# Note: Anytime we find a -query or -indirect on the command line we do
# not add a "-nolisten tcp", as then the query just wouldn't work, so
# this setting only affects truly local sessions.
DisallowTCP=true
# By default never place cookies if we "detect" NFS.  We detect NFS
# by detecting "root-squashing".  It seems bad practice to place
# cookies on things that go over the network by default and thus we
# don't do it by default.  Sometimes you can however use safe remote
# filesystems where this is OK and you may want to have the cookie in your
# home directory.
#NeverPlaceCookiesOnNFS=true

# XDMCP is the protocol that allows remote login.  If you want to log into
# gdm remotely (I'd never turn this on on open network, use ssh for such
# remote usage that).  You can then run X with -query <thishost> to log in,
# or -indirect <thishost> to run a chooser.  Look for the 'Terminal' server
# type at the bottom of this config file.
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave
# out on the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only
# allow local access is another alternative but not the safest.
# Firewalling port 177 is the safest if you wish to have xdmcp on.
# Read the manual for more notes on the security of XDMCP.
Enable=false
# Honour indirect queries, we run a chooser for these, and then redirect
# the user to the chosen host.  Otherwise we just log the user in locally.
#HonorIndirect=true
# Maximum pending requests
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time
#MaxSessions=16
# Maximum wait times
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single
# host.  This is now set at 2 since if the server crashes then gdm doesn't
# know for some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way
#Port=177
# Willing script, none is shipped and by default we'll send
# hostname system id.  But if you supply something here, the
# output of this script will be sent as status of this host so that
# the chooser can display it.  You could for example send load,
# or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]
# The specific gtkrc file we use.  It should be the full path to the gtkrc
# that we need.  Unless you need a specific gtkrc that doesn't correspond to
# a specific theme, then just use the GtkTheme key
#GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc

# The GTK+ theme to use for the gui
GtkTheme=Human
# If to allow changing the GTK+ (widget) theme from the greeter.  Currently
# this only affects the standard greeter as the graphical greeter does
# not yet have this ability
AllowGtkThemeChange=true
# Comma separated list of themes to allow.  These must be the names of the
# themes installed in the standard locations for gtk themes.  You can
# also specify 'all' to allow all installed themes.  These should be just
# the basenames of the themes such as 'Thinice' or 'LowContrast'.
GtkThemesToAllow=Human,HighContrast,HighContrastInverse,LowContrast

# Maximum size of an icon, larger icons are scaled down
#MaxIconWidth=128
#MaxIconHeight=128

[greeter]
# Greeter has a nice title bar that the user can move
#TitleBar=true
# Configuration is available from the system menu of the greeter
ConfigAvailable=false
# Face browser is enabled.  This only works currently for the
# standard greeter as it is not yet enabled in the graphical greeter.
Browser=false
# The default picture in the browser
#DefaultFace=/usr/share/pixmaps/nobody.png
# User ID's less than the MinimalUID value will not be included in the
# face browser or in the gdmselection list for Automatic/Timed login.
# They will not be displayed regardless of the settings for
# Include and Exclude.
MinimalUID=1000
# Users listed in Include will be included in the face browser and in
# the gdmsetup selection list for Automatic/Timed login.  Users
# should be separated by commas.
#Include=
# Users listed in Exclude are excluded from the face browser and from
# the gdmsetup selection list for Automatic/Timed login.  Excluded 
# users will still be able to log in, but will have to type their
# username.  Users should be separated by commas.  
Exclude=bin,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,gdm,postgres,pvm,rpm
# By default, an empty include list means display no users.  By setting
# IncludeAll to true, the password file will be scanned and all users 
# will be displayed except users excluded via the Exclude setting and
# user ID's less than MinimalUID.  Scanning the password file can be
# slow on systems with large numbers of users and this feature should 
# not be used in such environments.  The setting of IncludeAll does
# nothing if Include is set to a non-empty value.
IncludeAll=true
# If user or user.png exists in this dir it will be used as his picture
#GlobalFaceDir=/usr/share/pixmaps/faces/
# File which contains the locale we show to the user.  Likely you want to use
# the one shipped with gdm and edit it.  It is not a standard locale.alias file,
# although gdm will be able to read a standard locale.alias file as well.
LocaleFile=/etc/gdm/locale.conf
# Logo shown in the standard greeter
#Logo=/usr/share/pixmaps/gdmDebianLogo.xpm
# The standard greeter should shake if a user entered the wrong username or
# password.  Kind of cool looking
#Quiver=true
# The Actions menu (formerly system menu) is shown in the greeter, this is the
# menu that contains reboot, shutdown, suspend, config and chooser.  None of
# these is available if this is off.  They can be turned off individually
# however
SystemMenu=true
# The Actions in the Actions menu require the root password
SecureSystemMenu=false
# Should the chooser button be shown.  If this is shown, GDM can drop into
# chooser mode which will run the xdmcp chooser locally and allow the user
# to connect to some remote host.  Local XDMCP does not need to be enabled
# however
#ChooserButton=true
# Welcome is for all console logins and RemoteWelcome is for remote logins
# (through XDMCP).
# DefaultWelcome and DefaultRemoteWelcome set the string for Welcome
# to "Welcome" and for DefaultWelcome to "Welcome to %n", and properly
# translate the message to the appropriate language.  Note that %n gets
# translated to the hostname of the machine.  These default values can
# be overridden by setting DefaultWelcome and/or DefaultRemoteWelcome to
# false, and setting the Welcome and DefaultWelcome values as desired.
# Just make sure the strings are in utf-8 Note to distributors, if you
# wish to have a different Welcome string and wish to have this
# translated you can have entries such as "Welcome[cs]=Vitejte na %n".
DefaultWelcome=true
DefaultRemoteWelcome=true
#Welcome=Welcome
#RemoteWelcome=Welcome to %n
# Don't allow user to move the standard greeter window.  Only makes sense
# if TitleBar is on
#LockPosition=false
# Set a position rather then just centering the window.  If you enter
# negative values for the position it is taken as an offset from the
# right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0
# Xinerama screen we use to display the greeter on.  Not for true
# multihead, currently only works for Xinerama.
#XineramaScreen=0
# Background settings for the standard greeter:
# Type can be 0=None, 1=Image, 2=Color
#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true
BackgroundColor=#523921
# XDMCP session should only get a color, this is the sanest setting since
# you don't want to take up too much bandwidth
#BackgroundRemoteOnlyColor=true
# Program to run to draw the background in the standard greeter.  Perhaps
# something like an xscreensaver hack or some such.
#BackgroundProgram=
# if this is true then the background program is run always, otherwise
# it is only run when the BackgroundType is 0 (None)
#RunBackgroundProgramAlways=false
# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
# example) and more failsafe then those supplied by scripts so distros should
# use this rather then just running an xterm from a script.
#ShowGnomeFailsafeSession=true
#ShowXtermFailsafeSession=true
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode where
# the session saving stuff is disabled in GDM
#ShowLastSession=true
# Always use 24 hour clock no matter what the locale.
#Use24Clock=false
# Use circles in the password field.  Looks kind of cool actually,
# but only works with certain fonts.
UseCirclesInEntry=true
# Do not show any visible feedback in the password field. This is standard
# for instance in console, xdm and ssh.
#UseInvisibleInEntry=false
# These two keys are for the new greeter.  Circles is the standard
# shipped theme.  If you want gdm to select a random theme from a list
# then provide a list that is delimited by /: to the GraphicalThemes key and 
# set GraphicalThemeRand to true.  Otherwise use GraphicalTheme and specify
# just one theme.
GraphicalTheme=Human
#GraphicalThemes=circles/:happygnome
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false
# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font
# to be used when displaying the contents of the file.
#InfoMsgFont=Sans 24
# If SoundOnLogin is true, then the greeter will beep when login is ready
# for user input.  If SoundOnLogin is a file and the greeter finds the
# 'play' executable (see daemon/SoundProgram) it will play that file
# instead of just beeping
SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav
# If SoundOnLoginSuccess, then the greeter will play a sound (as above)
# when a user successfully logs in
#SoundOnLoginSuccess=false
#SoundOnLoginSuccessFile=
# If SoundOnLoginFailure, then the greeter will play a sound (as above)
# when a user fails to log in
#SoundOnLoginFailure=false
#SoundOnLoginFailureFile=

# The chooser is what's displayed when a user wants an indirect XDMCP
# session, or selects Run XDMCP chooser from the system menu
[chooser]
# Default image for hosts
#DefaultHostImg=/usr/share/pixmaps/nohost.png
# Directory with host images, they are named by the hosts: host or host.png
HostImageDir=/usr/share/hosts/
# Time we scan for hosts (well only the time we tell the user we are
# scanning actually, we continue to listen even after this has
# expired)
#ScanTime=4
# A comma separated lists of hosts to automatically add (if they answer to
# a query of course).  You can use this to reach hosts that broadcast cannot
# reach.
Hosts=
# Broadcast a query to get all hosts on the current network that answer
Broadcast=true
# Set it to true if you want to send a multicast query to hosts.
Multicast=false
# It is an IPv6 multicast address.It is hardcoded here and will be replaced when
# officially registered xdmcp multicast address of TBD will be available
#Multicast_Addr=ff02::1
# Allow adding random hosts to the list by typing in their names
#AllowAdd=true

[debug]
# This will enable debugging into the syslog, usually not neccessary
# and it creates a LOT of spew of random stuff to the syslog.  However it
# can be useful in determining when something is going very wrong.
Enable=false

[servers]
# These are the standard servers.  You can add as many you want here
# and they will always be started.  Each line must start with a unique
# number and that will be the display number of that server.  Usually just
# the 0 server is used.
#0=Standard
#1=Standard
1=Xgl
# Note the VTAllocation and FirstVT keys on linux and freebsd.
# Don't add any vt<number> arguments if VTAllocation is on, and set FirstVT to
# be the first vt available that your gettys don't grab (gettys are usually
# dumb and grab even a vt that has already been taken).  Using 7 will work
# pretty much for all linux distributions.  VTAllocation is not currently
# implemented on anything but linux and freebsd.  Feel free to send patches.
# X servers will just not get any extra arguments then.
#
# If you want to run an X terminal you could add an X server such as this
#0=Terminal -query serverhostname
# or for a chooser (optionally serverhostname could be localhost)
#0=Terminal -indirect serverhostname
#
# If you wish to run the XDMCP chooser on the local display use the following
# line
#0=Chooser

## Note:
# is your X server not listening to TCP requests?  Perhaps you should look
# at the security/DisallowTCP setting!

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 
flexible=true

# To use this server type you should add -query host or -indirect host
# to the command line
[server-Terminal]
name=Terminal server
# Add -terminate to make things behave more nicely
command=/usr/X11R6/bin/X -br -audit 0 -terminate
# Make this not appear in the flexible servers (we need extra params
# anyway, and terminate would be bad for xdmcp choosing).  You can
# make a terminal server flexible, but not with an indirect query.
# If you need flexible indirect query server, then you must get rid
# of the -terminate and the only way to kill the flexible server will
# then be by Ctrl-Alt-Backspace
flexible=false
# Not local, we do not handle the logins for this X server
handled=false

# To use this server type you should add -query host or -indirect host
# to the command line
[server-Chooser]
name=Chooser server
command=/usr/X11R6/bin/X -br -audit 0
# Make this not appear in the flexible servers for now, but if you
# wish to allow a chooser server then make this true.  This is the
# only way to make a flexible chooser server that behaves nicely.
flexible=false
# Run the chooser instead of the greeter.  When the user chooses a
# machine they will get this same server but run with
# "-terminate -query hostname"
chooser=true

[server-Xgl]
name=Xgl server
command=/usr/X11R6/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

```

and here is my xorg.conf

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Radeon 9700 (R300)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Radeon 9700 (R300)"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

```

please help me find this problem. thanks.

---

### Post by procras on 2006-04-17
Great thread. I eventually got compiz and Xgl working.

My hardware: ABIT AV8-3rd eye, AMD-FX60, Radeon X800XT PE, 

Packages
compiz 0.0.2-4ubuntu2
compiz-gnome 0.0.2-4ubuntu2
xserver-xgl 7.0.0-0ubuntu4
transset 0.1.0+cvs.20041114-0ubuntu2

3 main problems I had

1) 64 bit distro
2) No sign of options for compiz in gconf-editor
3) Transparency
4) Zoom

I was using the 64 bit distro but couldnt make progress untill I reinstalled with the i386 distro. I tried the koororaa 0.2 live cd and this showed me that Xgl and compiz would work on my hardware, so I then tried the i386 dapper flight 6 CD and did a clean install and followed this thread.

In item 2 of the opening post you also need to install compiz-gnome with compiz. I think that things have changed in the repository since the thread started.

Transparancy will not work for me, as it did in with the koororaa live cd. I found that if I installed transset 
$ sudo apt-get install transset
I can change transparancey by running transset from a terminal 
$ transset 0.5
eg. 0.5 for 50%. The arrow changes to a cross and then you can click on the window you want to change the transparancey of. Not as nice as <alt> scroll wheel but it works.

Zoom did not work for me due to a problem with my super key. As instructed I entered 
$ xmodmap /usr/share/xmodmap/xmodmap.uk
(maybe got this wrong?) and then I had to set the keyboard options 
System->Preferences->Keyboard->Layout Options->Alt/Win key behaviour
<*> Super is mapped to the Win-keys (default)

---

### Post by echoderek on 2006-04-17
Just want to know any X1400 success?

---

### Post by kakashi on 2006-04-17
[QUOTE=procras]Great thread. I eventually got compiz and Xgl working.

My hardware: ABIT AV8-3rd eye, AMD-FX60, Radeon X800XT PE, 

Packages
compiz 0.0.2-4ubuntu2
compiz-gnome 0.0.2-4ubuntu2
xserver-xgl 7.0.0-0ubuntu4
transset 0.1.0+cvs.20041114-0ubuntu2

3 main problems I had

1) 64 bit distro
2) No sign of options for compiz in gconf-editor
3) Transparency
4) Zoom

I was using the 64 bit distro but couldnt make progress untill I reinstalled with the i386 distro. I tried the koororaa 0.2 live cd and this showed me that Xgl and compiz would work on my hardware, so I then tried the i386 dapper flight 6 CD and did a clean install and followed this thread.

In item 2 of the opening post you also need to install compiz-gnome with compiz. I think that things have changed in the repository since the thread started.

Transparancy will not work for me, as it did in with the koororaa live cd. I found that if I installed transset 
$ sudo apt-get install transset
I can change transparancey by running transset from a terminal 
$ transset 0.5
eg. 0.5 for 50%. The arrow changes to a cross and then you can click on the window you want to change the transparancey of. Not as nice as <alt> scroll wheel but it works.

Zoom did not work for me due to a problem with my super key. As instructed I entered 
$ xmodmap /usr/share/xmodmap/xmodmap.uk
(maybe got this wrong?) and then I had to set the keyboard options 
System->Preferences->Keyboard->Layout Options->Alt/Win key behaviour
<*> Super is mapped to the Win-keys (default)[/QUOTE]

[QUOTE=krye]That would be... 128 megabytes = 134 217 728 bytes[/QUOTE]

my setup resembles your very closely so its nice to know you got it working.
mine is an opteron 165,x800gt,dfi nf4 sli. 

i was wondering did ubuntu configure your grahpics correctly or not upoon install ? lasty thing did kororaa 0.2 work for you cuz on mine it logged into gnome and THEN crashed.

---

### Post by gmc on 2006-04-17
[QUOTE=echoderek]Just want to know any X1400 success?[/QUOTE]

I tried this morning without much success, though to be honest the information on getting Xgl/compiz working is very fragmented through out the forums and I probably missed something important.

---

### Post by motivez on 2006-04-18
[QUOTE=procras]Great thread. I eventually got compiz and Xgl working.

My hardware: ABIT AV8-3rd eye, AMD-FX60, Radeon X800XT PE, 

Packages
compiz 0.0.2-4ubuntu2
compiz-gnome 0.0.2-4ubuntu2
xserver-xgl 7.0.0-0ubuntu4
transset 0.1.0+cvs.20041114-0ubuntu2

3 main problems I had

1) 64 bit distro
2) No sign of options for compiz in gconf-editor
3) Transparency
4) Zoom

I was using the 64 bit distro but couldnt make progress untill I reinstalled with the i386 distro. I tried the koororaa 0.2 live cd and this showed me that Xgl and compiz would work on my hardware, so I then tried the i386 dapper flight 6 CD and did a clean install and followed this thread.

In item 2 of the opening post you also need to install compiz-gnome with compiz. I think that things have changed in the repository since the thread started.

Transparancy will not work for me, as it did in with the koororaa live cd. I found that if I installed transset 
$ sudo apt-get install transset
I can change transparancey by running transset from a terminal 
$ transset 0.5
eg. 0.5 for 50%. The arrow changes to a cross and then you can click on the window you want to change the transparancey of. Not as nice as <alt> scroll wheel but it works.

Zoom did not work for me due to a problem with my super key. As instructed I entered 
$ xmodmap /usr/share/xmodmap/xmodmap.uk
(maybe got this wrong?) and then I had to set the keyboard options 
System->Preferences->Keyboard->Layout Options->Alt/Win key behaviour
<*> Super is mapped to the Win-keys (default)[/QUOTE]


I'd be very interested in seeing you write an updated installation / configuration guide.. Thought about doing it? 

I have been unable to get it to work in 2 weeks despite trying many of the posted methods, but I know it can work because karoraa's works fine, smooth, etc for me.

---

### Post by dreamsINdigital on 2006-04-18
Yeah, someone should write an updated guide or start a wiki.  I'm having trouble getting Xgl/Compiz to work again after I reinstalled Ubuntu.

---

### Post by mschievano on 2006-04-18
no success in xorg 7 e ati x1600 Pci-EX (Dapper 64 bit) ](*,)

---

### Post by procras on 2006-04-18
[QUOTE=kakashi]my setup resembles your very closely so its nice to know you got it working.
mine is an opteron 165,x800gt,dfi nf4 sli. 

i was wondering did ubuntu configure your grahpics correctly or not upoon install ? lasty thing did kororaa 0.2 work for you cuz on mine it logged into gnome and THEN crashed.[/QUOTE]

On the initail install ubuntu choose the ati driver for me.

I then ensured that I had installed the linux-restricted-modules-386 package.
Entered fglrx in /etc/modules
Used ati-config --initial
Reboot

And fglrx was working nicely for me.
:D

kororaa 0.2 worked for me, no crash on login, I just used the standard kernel nothing fancy and it worked!

---

### Post by procras on 2006-04-18
[QUOTE=echoderek]Just want to know any X1400 success?[/QUOTE]

For compiz and Xgl you need fglrx on the newer ati cards. Problem is that ati have only recently added support for X1000 + cards to fglrx.

fglrx 8.23.7 is in linux-restricted-modules, at the moment and the newer
8.24.8 is available for download from ati. I have not seen any reports of compiz Xgl and the newer fglrx driver as of yet.

---

### Post by motivez on 2006-04-18
SUCCESS!

I gave up on 64bit version, installed i386, and followed this guide: 
[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916) .. The .Xsession script is what did it, I believe. 

I followed this thread up to the point where it told me to edit gdm.conf / gdm.conf-custom, (So I still have 0=Standard in there !) and now everything is working fantastically .. :)

ATI Radeon 9700 Pro, 8.23.7, packages from universe (the ones listed in this thread, not on the other guide)

The guide suggested using this script instead of modifying global settings:

```

#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME 
exec gnome-session

```

Works great!

---

### Post by echoderek on 2006-04-19
my card is x1400 and have already setup fglrx8.24.8. I think it is ok then I tried install xgl. I can get into X but the system becomes quite slow and usually it will freeze soon after boot. So I think this newer driver maybe conflict with xgl somewhere. 
If anybody makes X1000+ card and this ner driver works well, please post here to let us know:KS

---

### Post by tokez on 2006-04-19
[QUOTE=echoderek]my card is x1400 and have already setup fglrx8.24.8. I think it is ok then I tried install xgl. I can get into X but the system becomes quite slow and usually it will freeze soon after boot. So I think this newer driver maybe conflict with xgl somewhere. 
If anybody makes X1000+ card and this ner driver works well, please post here to let us know:KS[/QUOTE]

there must be some problem with the 8.24 driver, because everything i try to do with installing xgl seems to fail. followed so many different guides and changed some things around to no avail.
i use the radeon 9700 pro (r300) with the new 8.24 fglrx driver and it isnt working. i might try it with the 8.23 driver for a comparion and report back.

---

### Post by getaceres on 2006-04-20
I had 8.23 drivers with XGL working and have updated it to 8.24. I had to remove the linux-restricted-drivers in order to enable 3d acceleration but now it works exactly like 8.23 drivers, not better or worse.

---

### Post by SiMoNsAyS on 2006-04-20
refer to [http://www.ubuntuforums.org/showpost.php?p=939848&postcount=8](http://www.ubuntuforums.org/showpost.php?p=939848&postcount=8) :)

---

### Post by jc87 on 2006-04-20
I followed the tutorial , and the problem is that after step 6 & reboot now i enter at Ubuntu but right after the panel´s  appear the image on the screen get´s all screwed and weird.

I have a Ati Radeon 9250 , a working xorg.conf with fglrx in Dapper  (i have a hint that must be some bug in the drivers , similar problem with kororaa live-cd), anyway i would like to know how to undo step 6 in text mode (which file to edit).

Thanks in advanced.

---

### Post by jordiR on 2006-04-22
I've just updated my xsever-xgl to the version 7.0.0-0buntu15, but this doesn't start. It can't load the wacom driver. I've been searching for the ubuntu13 deb to try it but I can't find the file anywhere. So can somebody please post the file or a link to the file?

---

### Post by John64 on 2006-04-25
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

I get this error when i try to launch compiz on an X1800XT with a functioning FGLRX

---

### Post by massivevoid on 2006-04-25
I'm in a pickle. Been having problems with Xgl and GDM.

[http://www.ubuntuforums.org/showthread.php?t=164949](http://www.ubuntuforums.org/showthread.php?t=164949)

---

### Post by Laterix on 2006-04-26
Compiz is really slow with the latest ATI drivers and latest XGL+QuinnStorm Compiz packages. With fglrx_info I get this
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.5755 (8.24.8)

```
Is this normal? I mean DRI missing thing. Same thing with glxgears.
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
12260 frames in 5.0 seconds = 2432.115 FPS
24160 frames in 5.0 seconds = 4824.374 FPS
24168 frames in 5.0 seconds = 4820.970 FPS
24414 frames in 5.0 seconds = 4878.679 FPS

```

For example rotating cube gets my CPU to 80% usage. (Pentium M 14.GHz) and window resize is really really really slow. :(

---

### Post by sharperguy on 2006-04-27
hmm

I followed the tutorial

HOwever im not sure how to get gnome-window-decorator to start first

also compiz does not show up in gconf-editor

now when i reboot gdm does not start and i have to hit ctrl+arlt+backspace, log in and type startx just to get into x. Then compiz or gnome-window-decorator do not start.

I am using the latest fglrx from ubuntu repository

My  card is a radeon 8500

Any ideas?

---

### Post by WillFerrellLuva on 2006-04-28
Hi,

I followed to tutorial today to try to get this working, however when I start gconf-editor compiz is not in apps.

I tried to reboot and I get a mesh screen and a mouse that is busy.  Nothing else happens.  So inorder to boot back in I changed my "/etc/gdm/gdm.conf" file back to "0=Standard
#1=Standard"

Someone in this thread said that trying " compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher" might work.  So i tried that from a terminal and it said " compiz.real: No composite extension"  I dont know if that is because i changed my "/etc/gdm/gdm.conf" file back or what.

Can anybody help me please?  This looks really awesome and I would like it to work!

---

### Post by jocko on 2006-04-28
[QUOTE=WillFerrellLuva]Hi,

I followed to tutorial today to try to get this working, however when I start gconf-editor compiz is not in apps.

I tried to reboot and I get a mesh screen and a mouse that is busy.  Nothing else happens.  So inorder to boot back in I changed my "/etc/gdm/gdm.conf" file back to "0=Standard
#1=Standard"

Someone in this thread said that trying " compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher" might work.  So i tried that from a terminal and it said " compiz.real: No composite extension"  I dont know if that is because i changed my "/etc/gdm/gdm.conf" file back or what.

Can anybody help me please?  This looks really awesome and I would like it to work![/QUOTE]

The instructions in this how to doesn't work with newer xgl-versions. Try using the method from [this]("http://compiz.ed3n.com/viewtopic.php?pid=2175#p2175") post instead.

---

### Post by WillFerrellLuva on 2006-04-29
Hi,

Thanks for the info.  I got it working!! Its awesome!!

---

### Post by edeuxk on 2006-04-30
can anyone tell me how to add the GdmXserverTimeout to gdm so i can start gdm in xgl, the problem now is that gdm terminates the xgl session after 10 seconds but xgl takes longer to start up. Gentoo and fedora core already have it but i couldnt find it for ubuntu

---

### Post by mauriciorossi on 2006-05-07
[QUOTE=jc87]I followed the tutorial , and the problem is that after step 6 & reboot now i enter at Ubuntu but right after the panel´s  appear the image on the screen get´s all screwed and weird.

I have a Ati Radeon 9250 , a working xorg.conf with fglrx in Dapper  (i have a hint that must be some bug in the drivers , similar problem with kororaa live-cd), anyway i would like to know how to undo step 6 in text mode (which file to edit).

Thanks in advanced.[/QUOTE]
i thought that was a problem like only i had
i wanna know how to fix that too :-(

---

### Post by PrimoTurbo on 2006-05-07
Yeah I have the same issue that most people have compiz does not show in the gconf-editor.

---

### Post by Zak Skjaveland on 2006-05-07
can u make a script of it plz

---

### Post by madchicken on 2006-05-08
[QUOTE=edeuxk]can anyone tell me how to add the GdmXserverTimeout to gdm so i can start gdm in xgl, the problem now is that gdm terminates the xgl session after 10 seconds but xgl takes longer to start up. Gentoo and fedora core already have it but i couldnt find it for ubuntu[/QUOTE]

Edit the file /etc/gdm/gdm.conf at line 198 and set the timeout to a greater value (i.e. 50).

Bye

---

### Post by xpmaniac4ever on 2006-05-13
Can anyone tell me if Xgl can be installed on a ATi Radeon 7000 ?

---

### Post by RobNyc on 2006-05-14
[QUOTE=xpmaniac4ever]Can anyone tell me if Xgl can be installed on a ATi Radeon 7000 ?[/QUOTE]

ANd Radeon X1600 Pro

---

### Post by Päkä on 2006-05-14
"The latest compiz package may have a bug that doesn't put the necessary gconf settings in place. One possible work-around is to install the battlehorse v1 deb for compiz, then update to the universe deb."

I can't seem to find compiz from gconf, so what now? I think I need a very detailed advises for this one :mrgreen:

---

### Post by yatt on 2006-05-14
I followed the same guide I followed last time I installed XGL/Compiz. Compiz does not execute at the start. I opened a terminal and tried toexecute compiz and got this in return:
```
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1
```

Anyone got a fix?

---

### Post by golfie on 2006-05-17
Strange before I could start xgl and compiz.. But now I end up with a gray screen and only the mouse cursor. I already changed the timeout to 50. But still it doesn't start gdm with xgl. Where should I look to see what causes this problem?

---

### Post by fiero_ka on 2006-05-17
I had same problems after a system  update.. But I reverted back to original gdm configuration and followed this [link]("http://compiz.net/viewtopic.php?pid=2175#p2175")
and it worked. I have an ATI X700 Mobility radeon.

---

### Post by gmc on 2006-05-17
[QUOTE=RobNyc]ANd Radeon X1600 Pro[/QUOTE]

I've got it working on my Acer 5672 with an X1400 mobile chipset if that's any indication.

Gord

---

### Post by chadwick359 on 2006-05-17
Hey there everybody, just popped in to let you know that I'm going to be looking over the thread to see what people are having problems with, and will be updating my Howto to fit with the latest packages/fixes/workarounds. Sorry that i dissappeared for a while, but I'll try to keep the this more up to date now. !st update should be tonight.

---

### Post by nhwk64 on 2006-05-17
I decided to update all the relevent packages, and now it's broken. It just waits at the gray X screen forever, like what happens if you try and run xgl on display 0. Anyone have any ideas? My xorg log shows everything initialized ok.

---

### Post by PingunZ on 2006-05-18
I got stuck on step 6
I'm in the session thing, but in what tab do I have to add the 2 things ( don't blame me for being new :D ) 
Nice HowTo btw ;)

Grtz PingunZ

---

### Post by nhwk64 on 2006-05-18
I decided to update all the relevent packages, and now it's broken. It just waits at the gray X screen forever, like what happens if you try and run xgl on display 0. Anyone have any ideas? My xorg log shows everything initialized ok.

---

### Post by namit on 2006-05-20
I have an ATI 9000 i think in my dell latitude D600 1.6 Centreno

Do you thik i can run this?

I tried a while ago but failed just got an error blue screen staying that x server could not start

---

### Post by lir on 2006-05-21
thats odd...
i've installed on my laptop the same way i install xgl+compiz on my desktop
but in my laptop i dont see compiz in gconf-editor in appz...

any ideas what i could be missing?
i need access to it so i can switch some keys...

thanks.
(runing dapper flight 7)

---

### Post by FuzzyFiz on 2006-05-22
+1  I can't see the compiz to, and know end up with grey screen which looks like  
goingto open in a minute but never opens :)

---

### Post by FuzzyFiz on 2006-05-22
in my laptop i dont see compiz in gconf-editor in appz...
any ideas what i could be missing?
and know it's broken. It just waits at the gray X screen forever, like what happens if you try and run xgl on display 0. Anyone have any ideas? My xorg log shows everything initialized ok.

thanks.
(runing dapper drake beta)[/QUOTE]

---

### Post by golfie on 2006-05-23
Bump:  Now I can finally start xgl and start gdm. But I have the following problem. There is window borders. After I login I start gnome-window-decorator and compiz --replace gconf. No error messages but still no window borders. Also in ps ax no compiz running. I have an ATI Mobility Radeon 9700. What can be the problem?

---

### Post by nixon on 2006-05-24
I've just fired Dapper up on my laptop, and have found the same as others.. no compiz showing up under apps int gconf? anyone got any ideas?

---

### Post by denjin on 2006-05-24
[QUOTE=nixon]I've just fired Dapper up on my laptop, and have found the same as others.. no compiz showing up under apps int gconf? anyone got any ideas?[/QUOTE]
I have the exact same problem.  No compiz under apps, and also I never get it to log in when I have XGL turned on.  I just have a GLCore error in the gdm log file and get a grey screen with the spinning cursor thing.  x600 here.

---

### Post by 0b1ivion on 2006-05-25
I had the no compiz in apps problem with the version in official repo. Then I heard in other thread using xgl.compiz.info repo and did an "apt-get remove --purge compiz" which solved the problem. But by following the HOWTO, I still can't get the darn thing working.:( Reboot to x login and the busy mouse kept spinning forever. Maybe there are too many going-ons after the original HOWTO was written?

---

### Post by dejitarob on 2006-05-29
Yea the Ubuntu packaged xgl and compiz were not working for me on an x600 mobility (not showing up in gconf) so I used [this guide]("http://compiz.net/viewtopic.php?id=389&p=1") on the compiz forums. I'm now able to log in and mess around with some stuff but every now and then it kicks me back out to GDM for no reason at all. I'm going to wait until development matures a bit before I waste more time trying to get it working. Besides wobbly windows, transparency and a big 3d cubed desktop don't really strike me as that useful.

Also, to get your windows' borders back when not in XGL try 'metacity --replace'.

---

### Post by nhwk64 on 2006-05-30
[QUOTE=denjin]I have the exact same problem.  No compiz under apps, and also I never get it to log in when I have XGL turned on.  I just have a GLCore error in the gdm log file and get a grey screen with the spinning cursor thing.  x600 here.[/QUOTE]

Have you tried the packages from this page? [http://compiz.net/viewtopic.php?id=389](http://compiz.net/viewtopic.php?id=389)

I'm using these, and I have a very nice gset-compiz utility in my accessories submenu.

---

### Post by RobNyc on 2006-05-31
I have an X1600 PRO 512mb, I followed the wiki but when I log in it just stays there after 10secs it logs me back out

---

### Post by nalgene on 2006-06-01
I'm tyring to find this can some point out were i cant find it in my gdm.conf


4. Modify /etc/gdm/gdm.conf to change your display:
Code:

#0=Standard 1=Standard

thx..

---

### Post by kriding on 2006-06-01
```
7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order:
Code:

gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher


```

I tried to set this, however, I don't have Compiz under 'apps'. I have it installed from the synaptic package manager. Everything else in the HOWTO went ok, it's just this one item. Can anyone help?

---

### Post by w.f.voogd on 2006-06-01
[QUOTE=kriding]
I tried to set this, however, I don't have Compiz under 'apps'. I have it installed from the synaptic package manager. Everything else in the HOWTO went ok, it's just this one item. Can anyone help?[/QUOTE]

Maybe you have to restart X?

I myself cant seem to get Xgl orking properly, when i restart X i get just a black X, no gdm login... :(

---

### Post by MeneK on 2006-06-01
It seems that I have some problem with the gconf plugin. I can start xgl + compiz from a tty using these commands:

```

sudo /etc/init.d/gdm stop
sudo /usr/bin/Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
sleep 10
DISPLAY=:1 gnome-window-decorator &
DISPLAY=:1 compiz --replace 
DISPLAY=:1 gnome-session &
DISPLAY=:1 compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &

```

But without gconf I can't get any gsudo app to work, and if I add "gconf" to any of the compiz lines, it gets locked. Is anybody having the same problem??

Thanks!

---

### Post by nemesa on 2006-06-02
[QUOTE=kriding]```
7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order:
Code:

gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher


```

I tried to set this, however, I don't have Compiz under 'apps'. I have it installed from the synaptic package manager. Everything else in the HOWTO went ok, it's just this one item. Can anyone help?[/QUOTE]


I have the same problem... :(

---

### Post by nemesa on 2006-06-02
[QUOTE=jocko]The instructions in this how to doesn't work with newer xgl-versions. Try using the method from [this]("http://compiz.ed3n.com/viewtopic.php?pid=2175#p2175") post instead.[/QUOTE]

Thank you I will check it...

---

### Post by souki on 2006-06-02
you have to run compiz once before it appears under gconf/apps

the first time, run "compiz --replace gconf"

---

### Post by gforce811 on 2006-06-02
Alright, I made it through step 6, restarted my machine (I don't remember if it prompted me to do so or if i just did) and now when it boots, it gives me a black and white matted screen.  

I'm very confused, because I can't get back into the system to fix anything.

Thanks for your help.

---

### Post by clov on 2006-06-02
[QUOTE=souki]you have to run compiz once before it appears under gconf/apps

the first time, run "compiz --replace gconf"[/QUOTE]

I have the same problem ( no compiz under gconf/apps) tried "compiz --replace gconf" and the result was:
```

compiz.real: No composite extension

```

and then still no  compiz under gconf/apps! Can anyone help?
thkx!

---

### Post by gusx on 2006-06-02
same here, i've had this problem forever...

Everything works fine till step 7. No compiz entry in gconf-editor

Pretty sad, i never got to make XGL work on Ubuntu :(

---

### Post by tokez on 2006-06-02
[QUOTE=gusx]same here, i've had this problem forever...

Everything works fine till step 7. No compiz entry in gconf-editor

Pretty sad, i never got to make XGL work on Ubuntu :([/QUOTE]

dont give it up yet. i had a lot of trouble gettin it going and finally success hit me in the form of a different howto.

i suggest trying to follow this guide of creating an xgl session in gdm so you dont have to replace and change the gdm confs.

go here - [http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)

thats the best guide i have found so far -- and its the only one that works for me

---

### Post by pesachzon on 2006-06-03
Hi, I followed the guide exactly but for some reason gdm doesn't start xgl (xorg starts normally). And the bigger problem is when I try to start Xgl from the console the screen goes black and the whole system hangs (I have to press the reset button).

I have an ati 9200se. fglrx is working normally:

> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)


Anyone knows what can be the problem? Which logs can I look at to know what's going on?

Also, for some reason I don't have a compiz section in gconf :-(

Thanks

---

### Post by imjustabill on 2006-06-03
[QUOTE=acruxksa]Just FYI,
I followed the directions on [http://www.tectonic.co.za/view.php?id=916]("http://www.tectonic.co.za/view.php?id=916") and everything seems to be working well on my Dell I9200 (w/ati9700).  Video playback in MPlayer is still a work in progress, but everything else seems to work ok.  I did have to add the "resize" plugin after following the instructions, but am not sure why, I think when I cut/pasted it I left out the resize plugin.  Anyway things seem to run pretty smoothly and I'm now looking for info to put backgrounds on the top and bottom of the cube.  I disabled xv in gstreamer and tweaked mplayer a bit and things seem better, but i'm still not able to watch video fullscreen.[/QUOTE]

If you're having prolblems with the instructions on the main page, I'd recommend trying this method. Don't have to muck around in all your config files, and its a lot easier.

---

### Post by Xylene on 2006-06-03
I seemed to have gotten everything working, except launching applications is extremely slow, along with resizing windows. 

When launching a window (only from the gnome-panel) I see a blue border expanding in about three steps and then the application launches.

Resizing windows are just slow.

Could any if it have to do with this:
```
anthony@athlon:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 XT Generic
OpenGL version string: 2.0.5814 (8.25.18)

anthony@athlon:~$

```

I am running XGL as a session.

---

### Post by kkovach on 2006-06-03
[QUOTE=imjustabill]If you're having prolblems with the instructions on the main page, I'd recommend trying this method. Don't have to muck around in all your config files, and its a lot easier.[/QUOTE]

I tried this method and everything seemed to go smoothly.  However, it looks like my compiz always ends up defunct, and I'm not able to see/do any of the fun stuff.

username@hostname:~$ ps auxww | grep -i compiz
username   4751  0.0  0.0      0     0 ?        Z    17:42   0:00 [compiz] <defunct>
username   4853  0.0  0.0   3944   908 pts/0    R+   17:42   0:00 grep -i compiz

I tried modifying gdm.conf to wait longer as I saw in some other thread when I googled for 'defunct compiz' but that doesn't seem to help.  I've not been able to find any other info on this.  Any help would be appreciated.  Thanks.

- Kevin

---

### Post by napsy on 2006-06-03
I configured xgl like in the first post but it doesn't work. GDM won't show up after I restart it. The cursor shows bussy but no login prompt. I checked fglrx and it shows an ATI card (not mesa). What's wrong? 
Using radeon 9200se.

---

### Post by Polymira on 2006-06-03
I've followed directions here...

When i log in as my user, I don't get any of the xgl affects, but when i login as root, I do...

What would cause this?

---

### Post by Polymira on 2006-06-04
Ok, so I got it working (don't ask me how)...


I can do the 3d cube effect, wobbly windows, etc...

But i cannot do transparency!! I want transparency when moving windows, as well as being able to do something like ctrl+shift+mousewheel to do it on the fly...

How do I go about setting this up?

Daper Drake
ati x700 mobility

---

### Post by Xylene on 2006-06-04
[QUOTE=Polymira]Ok, so I got it working (don't ask me how)...


I can do the 3d cube effect, wobbly windows, etc...

But i cannot do transparency!! I want transparency when moving windows, as well as being able to do something like ctrl+shift+mousewheel to do it on the fly...

How do I go about setting this up?

Daper Drake
ati x700 mobility[/QUOTE]
As long as the proper plugins are loaded you should be able to use <alt>+scrollwheel after clicking a window.

---

### Post by Fox_PT on 2006-06-04
i just got this:

fox@FOX:~/Desktop$ fglrxinfo
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18

what's the matter?
i'm a 64 bit user with a radeon9800xt

---

### Post by epegzz on 2006-06-04
hi everyone :-)

My Xgl/compiz works pretty well with Ati 9600 / Dapper / Gnome
I made everything like posted here:
[http://www.compiz.net/viewtopic.php?id=205](http://www.compiz.net/viewtopic.php?id=205)

( the first HowTo I found )


But now I have a problem:
everytime I reboot, any compiz-settings are gone.
I tried it with gset-compoz an directly by using gconf-editor.
everything works well... ..until I reboot. After booting any gconf-values are set to default again :-(

Any ideas?

daniel

---

### Post by JeremyHarrison on 2006-06-04
I have finally got it working. Wow, I've seen the special effects in Vista (that, if the world is *lucky*, they'll see sometime next year) and these are much more impressive. The switch from screen to screen is amazing!

Here's my question. I like the wobbly effect for the windows but it's making me a little sea sick when it appears in all my menus and tool tips. Is there a way to supress it for everything but windows or it is all or nothing?

Edit: Whoa! Maybe I did something wrong but these effects seem to be as buggy as they are beautiful! I haven't been able to keep my system up and running for more than about 30 minutes. It just keeps crashing. Has anyone got Xgl and Compiz running in a way that doesn't keep crashing? If I am having terrible problems with it, is that a sign that I must have done something wrong, or is that just the state of the engine at this time?

---

### Post by epegzz on 2006-06-04
[QUOTE=JeremyHarrison]
Edit: Whoa! Maybe I did something wrong but these effects seem to be as buggy as they are beautiful! I haven't been able to keep my system up and running for more than about 30 minutes. It just keeps crashing. Has anyone got Xgl and Compiz running in a way that doesn't keep crashing? If I am having terrible problems with it, is that a sign that I must have done something wrong, or is that just the state of the engine at this time?[/QUOTE]

Hey :-)

try to disable some plugins. I disabled dock, bs, wobbly, state, widget, miniwin
and than it was stable.

( only when I reboot, each disabled plugin gets enabled again.. see my prev post](*,)  :D )

---

### Post by Päkä on 2006-06-05
I'm not sure why most guides are so complicated..maby they work better, dunno. This is a link to a wery simple guide to install compiz+xgl:
[http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2/]("http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2/")
This works on both ati and nvidia and even has a failsafe included :cool:

---

### Post by JeremyHarrison on 2006-06-05
I did try shutting down most of the plug ins but still it keep crashing. I would bump me right out to the login page and shut down all of my applications. 

Also, it is true that all ACPI functionality is gone once you are using Xgl and Compiz? Trying to suspend crashed my computer. 

It's amazing this stuff is out now in an early workable state. It will be very interesting to see how much it has evolved by the time Vista is released. I really think that the effects capable with Xgl/Compiz are more stunning than both Vista and OS X. (Though OS X has the advantage of being as solid as a rock.) And, appart from totally wacko effects like wobbly and rain, most of what Xgl/Compiz does is actually more usable than what the standard operating system allows. The task switching allows you to see the task you are switching to much clearer, fading the background windows allows you to focus on what you are currently working on, etc. This will be an incredible product when it is into its second and third release.

---

### Post by Nomearod on 2006-06-05
I have one question abou XGL:

If I install XGL under gnome, it will allways use XGL after boot? For exemple, can I boot only gnome without xgl and play games?

---

### Post by JeremyHarrison on 2006-06-05
Nomearod,

You should be able to choose Xgl the way you would any session from the Options button in the login page. It will ask if you want this to be the default from now on and even if you answer yes, you can always select Gnome as your session later.

Now I have another question. All of my windows, when I run Compiz are opening in the top right corner of the screen with the min/max/close controls above the level of the screen itself. I can right click their icon in the program list and select Move to get them down but its a real pain to do this every time. Anyone else had this problem and know what I can do to fix it?

---

### Post by Lucas[PL] on 2006-06-05
[QUOTE=vaskark]I have a Radeon 9200 SE 128Mb card with acceleration enabled. I followed your instructions up until Step 6. Xgl is running, I'm in gnome but it is sooo slow. I do step 6 and my screen goes black (although I can still see/move my mouse cursor). Also, both Xgl AND Xorg appear to be running. Is this normal? And is my card too low-end for this maybe? I'm on a P4 3GHz with 512 Mb RAM.[/QUOTE]

Hello 
Sorry for me English.

I had this problem I found solution in "UBUNTU.PL".
this is link (text is in Polish language)
[http://forum.ubuntu.pl/printview.php?t=7421&start=0&sid=fd81f5c000b1a8c55c01f50b88c7c0ea](http://forum.ubuntu.pl/printview.php?t=7421&start=0&sid=fd81f5c000b1a8c55c01f50b88c7c0ea)

but I used packages form ubuntu...

---

### Post by JeremyHarrison on 2006-06-05
In the further adventures of working with Xgl/Compiz - I'm glad to report the more I use it the LESS it is crashing. Not that I did anything to fix it, it just seems to have settled down. In answer to my earlier question, in case anyone else wants only their windows to wobble and not their menus...

If you are using Gset-Compiz (can't remember where I got it from but it is a must for setting the properties of your compiz effects - if you can't find it message me and I will find out for you where you can get it) click Plug-ins, go to the Wobbly tab and remove any checks in "Unknown" row. This is found in the bottom box that lists what items should have what effects.

---

### Post by Choad on 2006-06-05
i dont unerstand step 6

i tried this howto before and it completely broke my system and i had to reinstall.... step 6 is rather ambiguous

clicking system>preferences>sessions brings up a panel with 3 tabs on, so where do i add those lines? also, it says to make sure one of them is "on top" but yet there is no way of shifting the order (unless you just add and remove them in the correct order, but that seems kinda stupid)

also, in gconf-editor  i dont have an apps>compiz at all

help?

---

### Post by v8YKxgHe on 2006-06-05
> i dont unerstand step 6

i tried this howto before and it completely broke my system and i had to reinstall.... step 6 is rather ambiguous

clicking system>preferences>sessions brings up a panel with 3 tabs on, so where do i add those lines? also, it says to make sure one of them is "on top" but yet there is no way of shifting the order (unless you just add and remove them in the correct order, but that seems kinda stupid)

also, in gconf-editor i dont have an apps>compiz at all

help?

Agreed, it's a little confusing - and I also don't have apps/compiz, Also ( to first post ) what do you mean download the battlefish v1 debs?

---

### Post by napsy on 2006-06-05
I have an ATI card. When I run X with composite extension enabled and try to run compiz, the following message shows up:
> $ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
But without composition:
> $ compiz.real: No composite extension

What's wrong?

---

### Post by napsy on 2006-06-05
Well, I fixed this with LD_PRELOAD. And compiz somehow loaded, but. The widgets don't refresh. Instead, there's always a black shadow when moving. You practically can't see any widgets, not the panel or anything else. Just the black window shadow. But still, the whobble effect seems to work.

Any ideas to fix this?

---

### Post by jaywhy13 on 2006-06-05
I followed the instructions on page 1 to the letter. However, nothing happens when I login. No errors or anything, just no XGL. 

I even tried another way that creates your own session, so there's an XGL option... no XGL.

I run fgl_glxgears so I know that 3d acceleration works... any advice.... 

ATI x1400, Dapper, used installation instructions on first page of thread

---

### Post by nemesa on 2006-06-06
AlexC_:
[QUOTE=souki]you have to run compiz once before it appears under gconf/apps

the first time, run "compiz --replace gconf"[/QUOTE]

---

### Post by Choad on 2006-06-06
[QUOTE=nemesa]AlexC_:[/QUOTE]
ahhhh cheers for that, but what about my other question....

---

### Post by Choad on 2006-06-06
[QUOTE=nemesa]AlexC_:[/QUOTE]
i get 

compiz.real: no composite extension

:(

---

### Post by La_Frenezo on 2006-06-06
Hi!

I exactly followed the instructions of the HOWTO. I installed all the packages from synaptic BUT at 7) where it is told to browse apps/COMPIZ/general/all screens/options, I didn't find an entry for compiz. However I did a reboot, and now I get nothing but a grey window with a cursor.

Can anyone tell me what happened?

Thanks in advance!

---

### Post by nemesa on 2006-06-06
I've followed this great guide:

[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

It works great now, I'm testing it...

Note, that the fglrx drivers sometimes freeze the system when you logout... so try to reboot (i don't know what kind of problem you have, I'm just guessing)...

---

### Post by nemesa on 2006-06-06
:grin: :grin: 
sorry... I don't read your post trimly...

You should try the suggested guide..

---

### Post by Choad on 2006-06-06
[QUOTE=La_Frenezo]Hi!

I exactly followed the instructions of the HOWTO. I installed all the packages from synaptic BUT at 7) where it is told to browse apps/COMPIZ/general/all screens/options, I didn't find an entry for compiz. However I did a reboot, and now I get nothing but a grey window with a cursor.

Can anyone tell me what happened?

Thanks in advance![/QUOTE]
you have the exact same problem as me!

to get back the old system log in to recovery mode and delete (or comment out with an "#") the stuff you entered in /etc/gdm/gdm.conf-custom and switch back the 0=Standard thing in /etc/gdm/gdm.conf

basically just undo the changes you made to the text files, but you can leave the /etc/X11/xorg.conf alone because that is obviously working fine for you

you will have your old xserver back then

---

### Post by Choad on 2006-06-06
[QUOTE=nemesa]I've followed this great guide:

[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

It works great now, I'm testing it...

Note, that the fglrx drivers sometimes freeze the system when you logout... so try to reboot (i don't know what kind of problem you have, I'm just guessing)...[/QUOTE]
THANKYOU!!!

fully recomend that tutorial! so much easier and it works!

---

### Post by Choad on 2006-06-06
[QUOTE=Choad]THANKYOU!!!

fully recomend that tutorial! so much easier and it works![/QUOTE]
ok, for some reason i only have shadows on the right hand edge of a window.... this is very odd

anyone got any ideas?

---

### Post by Choad on 2006-06-06
[QUOTE=Choad]ok, for some reason i only have shadows on the right hand edge of a window.... this is very odd

anyone got any ideas?[/QUOTE]
also, some windows ignore the theme and have a blue window border and can't be dragged...

... but this was true of other xgl boxes i have used...

the shadow thing is disapointing tho. it looks ugly, and thats not what xgl is about!

---

### Post by La_Frenezo on 2006-06-06
[QUOTE=Choad]
to get back the old system log in to recovery mode and delete (or comment out with an "#") the stuff you entered in /etc/gdm/gdm.conf-custom and switch back the 0=Standard thing in /etc/gdm/gdm.conf
[/QUOTE]

But how can I edit them under the command line? "Vi" and "pico" don'T show me anything when I write "sudo vi /DIRECTORY".

---

### Post by Choad on 2006-06-06
[QUOTE=La_Frenezo]But how can I edit them under the command line? "Vi" and "pico" don'T show me anything when I write "sudo vi /DIRECTORY".[/QUOTE]
recovery mode logs you in as root, so just

```
 nano /etc/gdm/whatever
```

---

### Post by nemesa on 2006-06-06
[QUOTE=Choad]also, some windows ignore the theme and have a blue window border and can't be dragged...

... but this was true of other xgl boxes i have used...

the shadow thing is disapointing tho. it looks ugly, and thats not what xgl is about![/QUOTE]

:( 
I don't have problems like you (yet)... It's working great and it's quite stable after I've disabled "wobbly" (it was slow). And I haven't got video playback issues (yet...) (I've disabled xv through gstreamer-properties)

---

### Post by cristianrosa on 2006-06-06
[QUOTE=napsy]I configured xgl like in the first post but it doesn't work. GDM won't show up after I restart it. The cursor shows bussy but no login prompt. I checked fglrx and it shows an ATI card (not mesa). What's wrong? 
Using radeon 9200se.[/QUOTE]
I have exactly the same problem, how can i detect what is wrong? i just cant find anything in the logs.
Suggestions? Napsy how did you solve this issue?
Thanks

---

### Post by gborzi on 2006-06-06
I managed to get xgl working on my ati radeon mobility 7500 using the open source radeon driver. The hard part of the task was to get an appropriate xorg.conf to see a working xgl. To this end I booted my laptop with kororaa 0.2 and saved xorg.conf. Then I changed the fonts part of the file and followed the wiki.
My configuration file is available [here]("http://ubuntuforums.org/showthread.php?t=179454&highlight=xgl+radeon+7500").

---

### Post by zappa on 2006-06-07
Nice how-to, but for some reason compiz did not appear in gconf-editor. Only after a reboot in some kind of a desktop without borders :)

---

### Post by RaverDK on 2006-06-07
Any one tryed XGL on a Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) GFX Card?

Coud be nice having this running on my laptop :-P

---

### Post by jaywhy13 on 2006-06-07
[QUOTE=nemesa]I've followed this great guide:

[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

It works great now, I'm testing it...

Note, that the fglrx drivers sometimes freeze the system when you logout... so try to reboot (i don't know what kind of problem you have, I'm just guessing)...[/QUOTE]

Yeah, that was a GREAT guide indeed. It works for me on Gnome. However, has anyone got Xgl to run on kde? I used the method that creates the .Xsession file to load Xgl on default and ALSO made one or 2 additions to xorg.conf:
	Option	"UseFBDev"	"true"
	Option 	"UseInternalAGPGART"	"no"
	Option	"KernelModuleParm"	"agplock=0"
This prevented ATI from touching itself and hanging up the hardware on me after a couple of seconds.  Don't remember the site that I got that site.

I have Ubuntu Dapper, ATI x1400.. my .Xsession looks like so:
#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME
exec gnome-session

When I replace gnome-win.. with kde-window-decorator and gnome-session with start-kde, my windows don't have borders???? Any suggestions???

---

### Post by lawngn0mex on 2006-06-08
[QUOTE=nemesa]I've followed this great guide:

[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

It works great now, I'm testing it...

Note, that the fglrx drivers sometimes freeze the system when you logout... so try to reboot (i don't know what kind of problem you have, I'm just guessing)...[/QUOTE]


Great find! 

I'm having stability issues though: 
> 
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

The last error message was:

System exception: IDL:Bonobo/GeneralError:1.0 : Child process did not give an error message, unknown failure occurred

GNOME will still try to restart the Settings Daemon next time you log in.


---

### Post by EstevaoSoares on 2006-06-09
Hi Folks... 

Again... 

I changed my notebook, now I own an Acer 5672. 

I'm running XGL in less than 15min. 
It's a AWESOME difference from the first time I've tried with my old notebook. 

Thanks for this tutorial.

Very very useful.

---

### Post by ModusOperandi on 2006-06-09
> Originally Posted by nemesa I've followed this great guide:  [http://www.tectonic.co.za/view.php?id=916]("http://www.tectonic.co.za/view.php?id=916")  It works great now, I'm testing it...  Note, that the fglrx drivers sometimes freeze the system when you logout... so try to reboot (i don't know what kind of problem you have, I'm just guessing)...  I followed that guide to the letter, and it runs v e r y  s l o w l y... I have the fglrx installed and working, giving me full opengl acceleration. A rough outline of my system:  3.0 GHz P4 w/ HT, ATi Radeon X850 Pro AGP, 2.5 GB RAM, 17&quot; CRT 1280 X 1024 @ 60 Hz.  Any ideas as to what could be causing such bad performance?

---

### Post by lawngn0mex on 2006-06-09
[QUOTE=ModusOperandi]I followed that guide to the letter, and it runs v e r y  s l o w l y... I have the fglrx installed and working, giving me full opengl acceleration. A rough outline of my system:  3.0 GHz P4 w/ HT ATi Radeon X850 Pro AGP 2.5 GB RAM 17" CRT 1280 X 1024 @ 60 Hz.  Any ideas as to what could be causing such bad performance?[/QUOTE]

run "top" from a terminal window... what's eating up all of your resources? I'm using an x800xl and it's quite fast.

---

### Post by ShadowofLeaves on 2006-06-09
I installed compiz the corect way however the picture on the bottem of the cube is just a color and not the image that i selected.  How can i fix this problem?:confused:

---

### Post by ModusOperandi on 2006-06-09
[quote=lawngn0mex]run &quot;top&quot; from a terminal window... what's eating up all of your resources? I'm using an x800xl and it's quite fast.[/quote]   Actually, it works fine now. Thanks, though.

---

### Post by lawngn0mex on 2006-06-09
okay.. I've figured out my stability problem... that I posted about a few posts up..

i'll only get crashes if I shift-backspace 
I have a habit of keeping shift held down when backspacing keys I used shift to make such as #! :-\

---

### Post by DJ_Cyberdance on 2006-06-11
Nice guide, but i got stuck when starting gconf-editor: There is no entry namend compiz in apps.

When rebooting, I just get the grey X background, I have to switch back the gconf files in /etc/gdm to get it working again, but even then compiz does not show up.

There is another package available, compiz-gnome, but even with this one it didn't work.

I'm using the ATI proprietary driver 8.25.18 on a Mobility X700. Anyone got a clue how to get over this step?

Edit:
I also tried running this one manually from the console:
```

sudo compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher

```
I tried with and without sudo, with and without gconf and I always had this:

compiz.real: No composite extension

I am not quite sure if this does matter or not...?

Another problem that already has been mentioned is how to determine the order of compiz and gnome-window-decorator as this window seems to be alphabetically ordered.

---

### Post by kriding on 2006-06-11
I cant get this to work. I've followed all the howto's but nothing!

---

### Post by Slicedbread on 2006-06-11
```
gnome-window-decorator (must be on top, start first) 
compiz --replace gconf
```

How do make sure one of them starts before the other? They are sorted by alphabetical order on mine and when I add them to startup programs, the gdm hangs indefinitely.

---

### Post by RavenOfOdin on 2006-06-11
I tried enabling composite before I saw this HOWTO and ended up with a junky splash screen interspersing itself with my desktop; making all sorts of garbage until I went to terminal and took that out of xorg.conf, then restarted X.

I'll reboot and try this.

(EDIT: After trying the Xsession file mods from above - they're in my Xsession file right above "exit 0" - and correcting the "Standard" line, I'm now in GNOME, but there are a few problems:

1. Draw and redraw are VERY slow, as are window darkenings which take place on gksu and "Quit" menu calls. GNOME basic operations are fine though.
2. OpenGL does not work. ATI control panel shows drivers as unavailable and glxinfo on 1:0 shows Mesa drivers. All OpenGL screensavers, rather than being slower than molasses, completely and utterly fail to load. 
3. Borders around windows are gone (I don't know if this is an intended effect or not.)
4. Bringing up windows is slow and leaves a yellow trail of redrawn window outline where the window should be.

My gdm.conf, gdm-custom.conf and Xsession are modified, and I have the gnome-window-decorator in my "Sessions" startup center.  I might take that latter one out seeing as both are already called by Xsession.

---

### Post by RavenOfOdin on 2006-06-12
[QUOTE=.k2600.]I got that one - while trying to use mesa libs from battlehorse with everything else from repos ...[/QUOTE]

I've got your "support for non power of two" error as well, and I'm running an ATI Radeon 9200 SE.

---

### Post by yellow beard on 2006-06-15
Hi. I tried doing the 2nd way of installing xgl from this page
[http://www.compiz.net/viewtopic.php?id=389]("http://www.compiz.net/viewtopic.php?id=389")

When i log in i have no borders. Ive tried typing this in the terminal
```
gnome-window-decorator &  compiz --replace gconf miniwin decoration transset wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &
```

But i get an error. Im sure alot of people had this problem. What do i do?

---

### Post by yellow beard on 2006-06-15
Fixed it. Turns out the wrong drivers were loaded.

---

### Post by syxbit on 2006-06-15
could someone explain what xgl/compiz is exactly?
i did a fresh install of dapper, and then installed ati drivers ?
could i benefit from this ?
thanks

---

### Post by Patrick-Ruff on 2006-06-16
I got the same error that Bou guy got... what should I do?

---

### Post by jfbilodeau on 2006-06-18
Good day All,

I've been trying to get Xgl+Compiz working for a couple of days now... No luck!

I'm using Dapper 64 with an ATI 200M. fglrx is working, and I have hardware acceleration. I've tried both method to get Xgl working, but none of them work for me. I've gone thought every how-to's I could find, but nothing works. I'm hoping someone has a bit of wisdom to share on how to get Xgl working on my machine!

The only error messages I can find is:

"No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295" in Xorg.1.log

Any suggestions?

Thanks in advance!

EDIT: I should clarify that Xgl works, but no DRI. The log says DRI works, but glxinfo or fglrxinfo both report that DRI is not active...

J-F

---

### Post by yellow beard on 2006-06-18
[QUOTE=syxbit]could someone explain what xgl/compiz is exactly?
i did a fresh install of dapper, and then installed ati drivers ?
could i benefit from this ?
thanks[/QUOTE]

[http://youtube.com/watch?v=1n-6oEcAZ80&search=xgl%20novell]("http://youtube.com/watch?v=1n-6oEcAZ80&search=xgl%20novell")

---

### Post by chele on 2006-06-20
Now working using the free ati/radeon driver from xorg on a ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```
# /etc/X11/xorg.conf 

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
# removed as i found a note that it gets loaded anyway, and breaks Xgl
# from http://www.thinkwiki.org/wiki/R300
# 3D dri tweaks
#    Load "GLcore"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
    Driver        "ati"
    BusID        "PCI:1:0:0"
# option added to force lcd discovery
         Option "MonitorLayout" "LVDS,NONE"

    Option      "AGPMode"       "4" 
    Option     "RenderAccel" "true"
    Option     "AGPFastWrite" "off"
    Option     "DynamicClocks" "on"
    Option         "XAANoOffscreenPixmaps"
    Option        "HWCursor"        "true"
    Option        "EnableDepthMoves"    "true"
    Option        "ColorTiling"        "false"
    Option            "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
# option added to specify true screen size
         DisplaySize     304 228
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1600x1200"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1600x1200"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1600x1200"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1600x1200"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1600x1200"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1600x1200"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Extensions"
#          Option  "Composite" "Enable"
EndSection

```

```
 sudo vi /usr/bin/startxgl.sh

#!/bin/bash
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME
exec gnome-session
```

---

### Post by Orval on 2006-06-22
Yes! I've xgl and compiz up and running. Looks great and faster than I expected. However, OpenOffice is very, very slow and it crashes after a minute or so. Is there a way to solve this? If I cannot use OpenOffice than using my computer is pretty pointless. :rolleyes:

---

### Post by damagedspline on 2006-06-24
I've managed to run XGL on a foss radeon IGP340M - i've posted a very short howto at the aiglx forum:
[http://www.ubuntuforums.org/showpost.php?p=1175948&postcount=963]("http://www.ubuntuforums.org/showpost.php?p=1175948&postcount=963")

I'll try some more tweaks to xorg.conf, gdm.conf-custom, based on stuff that's in this forum... (should i open a new forum for foss drivered radeons?)

---

### Post by greenbmw530i on 2006-06-25
Hey guys, I was doing fine with getting Xgl on my laptop, and before I went ahead with finishing Compiz, I decided to do a reboot (just for the heck of it), much to my dismay, I recieved this warning in full screen when my laptop rebooted:
```
[4294707.013000] serial8250: too much work for irq4
```I have a ATI Mobility Radeon 9600/9700 series card and from what I've read, it's supposed to work fine with Xgl/Compiz.

I used this ubuntu HowTo to set up Xgl: [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl) I made sure I followed everything and did everything for ATI (not for Nvidia) I chose "Method B: Make Xgl Your Standard Display Server" instead of method A (which, in hindsight, wasn't a very good idea considering where it got me)

This was the Compiz HowTo I used:[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz) I installed the packages "compiz," "gnome-compiz," and "gset-compiz" and all of their dependencies. I went to the next step in the Compiz HowTo:
```
gnome-window-decorator &
``` and that gave me a "...NULL invalid" error. That is when I decided to restart.

Please tell me where I'm going wrong; I'd really like to enjoy xgl/compiz.

Thanks a lot,
Mike

---

### Post by johlin on 2006-06-28
I'm having problems. I followed all of the instructions except for the 2 last steps about the keyboard (they shouldn't matter anyway).

Compiz didn't show up in gconf so I found another respository for it, I don't remember the exact name of it and I cant' check because I'm writing this using Windows but it was something with a Q as the first letter.
After that, it showed up in the gconf editor.

I added the options in the gdm.conf and -custom-files twice (they disappeared when I reinstalled compiz) and to the session manager (but I didn't do as this guide said the last time, I did as the novel site said.

Both times, when rebooting and gdm was starting, first I just see something distorted blue, then the screen blinks, shows something more distorted, blinks, shows the login window, blinks, shows the terminal and repeats that 3 or 4 times. After that, I get the error window where it says reconfigure and restart blabla.
When I login and startx, gnome boots fine as usual (but with no fancy effects).

I'll post info tomorrow when I've booted into Ubuntu again (tell me what to post), but does anyone have an idea of what the problem might be?

---

### Post by greenbmw530i on 2006-06-28
@ johlin:
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) helped me tremendously. I'd say start from scratch (but I'm no expert :wink:) and follow that HowTo. Make sure you get rid of any changes you made from previous xgl/compiz howtos (I just reformatted since I didn't have any important documents) before you embark on the compiz.net howto.

Good luck!

---

### Post by johlin on 2006-06-29
[QUOTE=greenbmw530i]@ johlin:
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) helped me tremendously. I'd say start from scratch (but I'm no expert :wink:) and follow that HowTo. Make sure you get rid of any changes you made from previous xgl/compiz howtos (I just reformatted since I didn't have any important documents) before you embark on the compiz.net howto.

Good luck![/QUOTE]

Thanks.
I've decided to reformat, but with kubuntu this time. I like KDE better. But the first steps should still be the same.

---

### Post by anonym0us on 2006-06-30
help!!.. i installed xgl with the instruction from compiz. the installation itself was pretty smooth.. when i reboot, i could still see the login screen. i entered the username password and enter, the screen seemed to load, i could see the mouse pointer with the busy icon, the screen is showing only some background color, then it stuck.. i waited for around 5 minutes and it stayed the same.. i hav tried the second howto in compiz so that i hav two sessions, gnome and xgl. the xgl is shown on the session option.. but when i entered, the screen goes black n it seems to load for awhile, but then i was back to the login screen.. for reference, i am using acer 5204 laptop with ati x700 graphic card.. the 3d accelerator driver i used is xorg-driver-fglrx from the repos with linux kernel version 2.6.15.23-i386

---

### Post by mem on 2006-06-30
can we get an updated guide on how to do an ubuntu/ATI/xgl install? I really really really dont want to read through 50+ pages with 100 different ways / things to try to get it to work...

---

### Post by Eversmann on 2006-07-01
[QUOTE=anonym0us]help!!.. i installed xgl with the instruction from compiz. the installation itself was pretty smooth.. when i reboot, i could still see the login screen. i entered the username password and enter, the screen seemed to load, i could see the mouse pointer with the busy icon, the screen is showing only some background color, then it stuck.. i waited for around 5 minutes and it stayed the same.. i hav tried the second howto in compiz so that i hav two sessions, gnome and xgl. the xgl is shown on the session option.. but when i entered, the screen goes black n it seems to load for awhile, but then i was back to the login screen.. for reference, i am using acer 5204 laptop with ati x700 graphic card.. the 3d accelerator driver i used is xorg-driver-fglrx from the repos with linux kernel version 2.6.15.23-i386[/QUOTE]

Same problem here, i get stuck after enter username/password, it shows my wallpaper and then it gets stuck on the busy pointer of the mouse, i have to hard reboot. Using X200, tested with 8.24, 8.25, 8.26, don't know if its a driver problme or an xgl problem.

---

### Post by Dubbayoo on 2006-07-01
[QUOTE=mem]can we get an updated guide on how to do an ubuntu/ATI/xgl install? I really really really dont want to read through 50+ pages with 100 different ways / things to try to get it to work...[/QUOTE]

amen

---

### Post by Eversmann on 2006-07-01
Hey, running 2.6.15-23 no more hangs after login (at least, looks like).

---

### Post by rutger83 on 2006-07-02
Well people, after too much trying, I'm giving up: just ordered a nvidia card today! Screw ATI, the drivers aren't what they should be...

I have an onboard Radeon Xpress200, and the random crashes remain. Using Compiz/Xgl after 5-10 minutes. Without I've managed to go a whole day without crashing sometimes, but the problem remains. I have the impression it's a matter of applications.

The amd64 version (I have dual boot) is worse: same problems.

I tried almost all drivers out there, the latest ati drivers (8.26-18) with latest linux kernel 6.15-25 won't help. Some earlier versions are more stable.


Tomorrow I'll have a rock solid nvidia powered pc. Just wanted to share that ;)

---

### Post by danitxu on 2006-07-13
After 2 days trying two methods to get compiz running, not at all. My data:

* ATI X300SE, PCI Express, 128 Mb

*  kernel 2.6.15.26-686

*  driver fglrx 8.26.18-1. I downloaded it from ati web page:
[https://support.ati.com/ics/support/KBAnswer.asp?questionID=1643](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1643)
, then generated and installed the .deb packages. The kernel module was installed normally (by means of [http://www.ubuntu-es.org/node/19975](http://www.ubuntu-es.org/node/19975))
In dmesg I see some messages like:
	fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at...
, but I'm ignoring them cause fgl_glrxgears is drawing 3D ok.

* /etc/X11/xorg.conf: I think it's ok. No error in /var/log/Xorg.0.log

* Xgl: I think it's ok.  fglrxinfo says:
   display: :0.0  screen: 0
   OpenGL vendor string: ATI Technologies Inc.
   OpenGL renderer string: RADEON X300/X550 Series Generic
   OpenGL version string: 2.0.5879 (8.26.18

, and fgl_glrxgears is giving about 245 FPS

Running fireglcontrolpanel it says Radeon X300/X550 (RV370 5B60)

I installed Xgl in two ways:
a) As indicated in this page, inside gdm - gnome (/etc/gdm/gdm.conf-custom,...)
b) With a script (called in another type of session by means of  /usr/share/xsession/gnome-xgl.desktop)
    #!/bin/bash
    Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer &
    sleep 2
    DISPLAY=:1
    gnome-session

* compiz: I installed it two ways:
a) As indicated in this page.
b) With a script called gnome-compiz.sh (invoked manually in a xterm console):
    #!/bin/bash
    #export DISPLAY=:1
    gnome-window-decorator &
    compiz --replace gconf  &
The error is:
    compiz.real: No composite extension
And if I don't comment the DISPLAY line, I get this error:
    Can't use gconf-dump plugin with gconf plugin

BTW, I've seen that compiz is a script that LD_PRELOADs the correct 
/usr/lib/fglrx/libGL.so.1.2.xlibmesa


After running compiz in all of the indicated ways, (this web page's included), all my window bars dissappear and no compiz is found if I do ps -Af | grep compiz.

My questions are:
1) Is it possible to have compiz with this card? Anybody got it?
2) If the answer is yes, what am I doing bad? Anyone with it is possible to write me( jdanitxu AT gmail.com )

      Thanks a lot in advance

---

### Post by ico on 2006-07-15
Hi all,

I've installed Xgl on a 15-inch MBP (judging from the whine/heat issues, probablly the first batch that came off the line) and here's the bizzare situation:

*I am running latest dapper with all updates (2.6.15-26-686 kernel, 8.26.18 ATI driver and latest quinn packages for Compiz & co.)

*Xgl works great (used the first method from the compiz website with slight modifications)

*glxinfo says "direct rendering: No" even though I am getting 5000+ fps on glxgears

*when running anything that requires DRI, I get the message "XFree86-DRI missing on :1.0," (please see below for the verbose glxinfo output) however all the symlinks point to right places, namely:

1) /usr/X11R6/lib/libGL.so and its variations all point to /usr/lib/fglrx/<name of the ati's libGL.so>, I've checked this by comparing creation/modification dates after installing fglrx driver
2) /usr/X11R6/lib/modules/dri has working symlinks to the same /usr/lib/modules/dri/ folder with ati's dri files which I've also checked for creation/modification dates in order to ensure that they were updated during fglrx install

*The bizzare thing is that glxgears work, but fgl_glxgears do not reporting:
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Error: couldn't get fbconfig

*OpenGL gnome-screensaver works fine, but blender crashes when entering "play" mode.

*xorg.conf is to the best of my knowledge properly set up (GLcore is commented out since glx module starts it anyhow), although I am not sure about the fglrx settings other than the "Composite" being disabled.

Does anyone have any ideas why is this so? Is this expected behaviour?

Any assistance is most appreciated!

Thank you very much!

Best wishes,

Ico


---------

---

### Post by ico on 2006-07-15
to improve legibility I've added another post with attachments (cannot seem to be able to delete this one, though, my apologies for leaving clutter around)...

---

### Post by ico on 2006-07-15
Here are relevant logs:

Again, thank you for your help!

Best wishes,

Ico

---

### Post by Jolly Roger on 2006-07-15
I tried to setup XGL and Compiz yesterday with the guide at [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389). I followed all the directions as best as I could. I got through all the directions and restarted Ubuntu as directed from the guide. Once Ubuntu was starting up again I got the error:

170098.890320/Scheduling while Atomic/0x009480/Xorg

I'm using an ATI x800 GTO2 video card and I am runnig Dapper. 

Does anyone know what this means and how I could fix it? I can't even get into Ubuntu right now so I have to use my Windows drive.

---

### Post by dranger003 on 2006-07-18
For anyone getting something like this:
[FONT="Courier New"]
170098.890320/Scheduling while Atomic/0x009480/Xorg[/FONT]

Simply add the option "noinotify" to your kernel boot options in /boot/grub/menu.lst:

[FONT="Courier New"]kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro quiet splash noinotify[/FONT]

If you shutdown GDM you get the msg again but it will eventually stop as opposed to having them non stop until a reboot occurs when the option is not present.

---

### Post by mrojas73 on 2006-08-13
I have the latest ATI drivers 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5946 (8.27.10)

This is a compaq Presario V2000 with an ATI Xpress 200M video card.  If I want to use XGL without lockups, the machine has to be restarted.  For example, if I turn it off and then back on and try to logon right away, it will lock up.  If instead of login on I restart and then logon, it works just fine.  Regular Gnome sessions work great at any timel.

Marco.

---

### Post by bhohe on 2006-08-17
sadly your page isn´t online any more:

[http://micampe.it/2006/02/18/ubuntu-fglrx-xgl-compiz-and-missing-glx_ext_texture_from_pixmap](http://micampe.it/2006/02/18/ubuntu-fglrx-xgl-compiz-and-missing-glx_ext_texture_from_pixmap)

---

### Post by GregaS on 2006-08-17
I have KDE and I installed xgl. If I select xgl session at KDM everything is working fine but everything is VERY slow. I guess this is because direct rendering is disabled. I tried sudo dpkg-reconfigure xserver-xorg but without success. If I start x server direct rendering is enabled (i can play enemy territory). Does anyone have any ideas what to do? BTW I have ati radeon 9600xt.

---

### Post by mrojas73 on 2006-08-17
> **GregaS said:**
> I have KDE and I installed xgl. If I select xgl session at KDM everything is working fine but everything is VERY slow. I guess this is because direct rendering is disabled. I tried sudo dpkg-reconfigure xserver-xorg but without success. If I start x server direct rendering is enabled (i can play enemy territory). Does anyone have any ideas what to do? BTW I have ati radeon 9600xt.

Can you post your /etc/X11/xorg.conf file and
/etc/modules?

I assume that you tried to install your drivers and changed from ati to fglrx driver in your xconfig file?

---

### Post by GregaS on 2006-08-17
Here:

> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "si"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "V770+"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor    "V770+"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
fglrx
fuse


BTW if I run KDE normally then everything is ok but if I run it as xgl session then direct rendering is disabled.

---

### Post by orbital on 2006-08-18
I see there's a lot of updates for compiz so I was wondering is there a way to know about the new plugins etc i could use?

---

### Post by GregaS on 2006-08-22
Can anyone help?

---

### Post by crhall on 2006-09-01
Not sure what I've done here.... or even if it was me....

I had it all running great. I did some updates. Now, it starts fine, but I have no window borders, so drag and drop won't work and things are positioned strange on the screen. Could it be a setting in gset-compiz?

Or should I attempt to rip it all out and try again?

---

### Post by crhall on 2006-09-01
Looks like it was just the 'state' plugin.

All great now.
woohoo!

---

### Post by mrojas73 on 2006-09-02
> **crhall said:**
> Looks like it was just the 'state' plugin.

All great now.
woohoo!

I am glad you got it working, it would be nice if you could describe how you solved the problem.  It may help some one else!

---

### Post by strabes on 2006-09-06
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

This guide worked for me perfectly. Make sure you pay attention at the end though, there's some extra stuff you have to do because of the ATI card.

I don't know how to get my plugins to show up in gconf-editor though. Does anyone else have this problem?

---

### Post by montag451 on 2006-09-15
I'm using a Radeon Mobility X1600 on an Acer TravelMate 8200 laptop, and XGL works fine for me. The only problems I've run into so far are the inability to use some desktop shortcut keys and attempting to change XGL's restart button-combo from SHIFT+BACKSPACE to something I'm less likely to hit by accident.

---

### Post by Silver Comet on 2006-09-17
I'm running on  mobility ati 9700 128mb card, when I load up I get a crosshatch of grey and white (grey lines white boxes) and then it goes for the normal theme. After this everything seems fine, but no XGL effects (if I change desktops or move my GAIM window around etc). I then try loading ffb2 or any other window, and the crosshatch comes back taking over the whole screen. Rolling over the buttons in the navbars etc restores most of them for that square.

Opened up this window in XGL via ffbeta2 (I'm using dapper) and trying to reply in this box, xgl suddenly takes 97% process power and the whole thing goes veeeery slow, so had to log out just to type this (I have xgl set up as a seperate session) can't remember if I used this guide, 90% sure I did though..life has been so hectic it's hard to tell.

P.S
It does not look like it is in my screenshots, it's the same hatching but in white and grey, and you can see the individual windows fine, screenshots for some reason blur the whole load in to cross hatching.

Sorry if this issue has already been covered, in such a rush I was only able to check the first few pages with a glance over

EDIT

Ok so i should probably include some of the details.
xorg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
glxinfo:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5814 (8.25.18)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None

```

---

### Post by LinuxConvert on 2006-09-19
Hi people!

I used the tutorial from this page: [http://www.compiz.net/topic-389-1.html](http://www.compiz.net/topic-389-1.html) and it worked for me. However, the XGL session refuses to start for any other user on my machine (I tried all this as another user in a attempt to not break things for my main user). It flatly refuses to start, after the GDM login it tells me that my session only lasted less than 10 seconds, therefore some error had occured. So right now I'm able to use XGL on an extra user's account but not my main one. Any help is very much appreciated.

My PC is an AMD Sempron 2600+ with an ATI Radeon 9550 running Ubuntu Dapper.

Thanks in advance.

---

### Post by LinuxConvert on 2006-09-20
Hi guys.

After a little bashing around, I suspect that the problem lay in the fact that I did those "root" instructions/actions as a USER with temporary admin rights. So those files still belonged to the USER, not to ROOT and thus it would only work for that particular user and not for everyone else. That seems to me to be the only possible explanation.

In accordance with that theory, I redid the steps (excluding actually installing the packages) as my main user and it worked like a charm. Can someone figure this out and maybe explain it better? I'm no Linux guru so all I can say is what I suspect is the case.

Anyway, XGL/Compiz is now working very well for me. Thanks for the guide.

LS

---

### Post by parradux on 2006-10-09
I'am having problems with installing the librarys. Specifcally this one: compiz. 

Can someone tell me how to install it when I do sudo apt-get install compiz I get this message: 

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
E: Broken packages


And when I try to install compiz-plugins I get that the CSM dependency does not exist.

---

### Post by RobNyc on 2006-11-20
Well we're using edgy now, the instructions still work for edgy too ? 
Last time I had XGL, I had it running with fglrx and beryl and it would crash too much I was told xgl does that

---

### Post by dmber on 2006-12-12
how do i find out my video card model and driver info?

thanks a lot!

---

### Post by raul_ on 2006-12-13
I can't open [www.compiz.net](www.compiz.net)

Is the link broken?

---

### Post by dziki on 2006-12-15
try [http://forum.go-compiz.org/](http://forum.go-compiz.org/) :)

---

### Post by raul_ on 2006-12-15
Thanks. I'm already running Beryl =)

---

### Post by SolaceDisparaged on 2007-03-27
is there an updated tutorial somewhere? compiz.net seems to be down..
I did this once before but when testing vista, it ate my linux drive...so i'm reinstalling it, but i can't remember what i did, it was nearly 6 months ago..

---

