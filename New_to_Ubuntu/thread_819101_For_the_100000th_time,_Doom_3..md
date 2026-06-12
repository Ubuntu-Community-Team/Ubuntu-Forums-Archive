---
title: "For the 100000th time, Doom 3."
date: 2008-06-05
forum: New to Ubuntu
---

### Post by CaptainJamesKirk on 2008-06-05
Hello, I was recently enlightened, by my girlfriends father. I am now a proud Ubuntu 64bit user. I am *kinda* getting used to it. However..
I like to play games, and the main thing which drew me back from Linux was the lack of commercial games. (Even though I've downloaded a few games for Linux.) And then I saw a shining light at the end of the tunnel. DOOM 3 IS LINUX COMPATIBLE! I thought to myself, 'Hell, Even though it's a rather crap game.. It's better than nothing.' I own the game.

I downloaded the .run file. And spent 4 or so hours trying to install it, I downloaded all the 32bit lib files. And it finally installed. However, I cannot load the game. I copied all the .pk4 files from the Doom 3 DVD and it still refuses to load. Just blackscreens then throws me back to the desktop. Any help would be much appreciated!

Thank you!

---

### Post by iaculallad on 2008-06-05
Had you tried reading Ubuntu's Community Doom3 [Documentation]("https://help.ubuntu.com/community/Doom3")?

---

### Post by CaptainJamesKirk on 2008-06-05
Yeah. I don't know where, or how to do the stuff it says about the blackscreen. I've spent awhile googling to try fix this.. :(

---

### Post by Metaleks on 2008-06-05
I don't have the game, but the instructions seem to be pretty straight forward.

> This problem has been reported on Ubuntu Gutsy 7.10 amd64 with the NVIDIA proprietary drivers.

If the screen goes blank after you start Doom3, try starting it with this command:

```
LD_PRELOAD=/usr/lib/libGL.so.1 doom3
```

If it works, you can replace the /usr/local/bin/doom3 symlink with this script and the menu icon should start it properly:

```
#!/bin/sh
LD_PRELOAD=/usr/lib/libGL.so.1 /usr/local/games/doom3/doom3
```


First test if the first command works.  If it does, go into the /usr/local/bin/doom3 directory.  Find the symlink ([symbolic link]("http://en.wikipedia.org/wiki/Symbolic_link"), for short) and replace it with the second box of code.  Save, and run.  Hope this helps!

---

### Post by CaptainJamesKirk on 2008-06-05
Thanks for the help but it refuses to even load a blackscreen now.. Gah. I give up. Thanks!

---

### Post by adam_kimber on 2008-06-05
Don't give up! 

If you start doom3 from a terminal does it spew any error messages? I found when trying to run games and they not working is the fact that the game is expecting 3D graphics acceleration and your desktop currently isn't. 

Quick test to see if you are running with 3D acceleration is to open a terminal type the following.

> glxinfo | grep direct

If the answer is yes then we move on to the next trick :P 

If no. You need to enable the proprietary drivers. To do this Ubuntu menu --> System --> Administration --> Hardware Drivers and enable the driver listed. Probably will ask for a reboot. I know this works for nvidia cards. Not sure about ATI

---

### Post by CaptainJamesKirk on 2008-06-05
Sorry for bringing back an 'old' thread. I just want to get it working.. :P
I did as Adam said. And it said.. 

jamie@jamie-desktop:~$ glxinfo | grep direct 
direct rendering: Yes

I just recently turned off some effects in "Advanced desktop effects settings" and ran the game with the command "LD_PRELOAD=/usr/lib/libGL.so.1 doom3" it loaded up the "Initializing" screen for like a second then booted me back to the desktop? I have nvidia on board gpu. I don't exactly know what the model is. It runs fine in windows.

Anyone with an idea why?

---

### Post by adam_kimber on 2008-06-05
> **CaptainJamesKirk said:**
> 
jamie@jamie-desktop:~$ glxinfo | grep direct 
direct rendering: Yes

This is good. That eliminates a few ideas. Not a problem we are here to help!

OK. How about this. How are you starting the game? From an icon or typing the name in the terminal? 

If via an icon I would like you to start it from a terminal. This way any errors will (hopefully) be shown. Try the following.

1) If the executable to start the game is doom3, start a terminal and type doom3. Paste the results.

2) Say the game is installed in /usr/local/games/doom3/ go to that directory in a terminal and the type ./doom3 to start the game. Paste the results.

3) Do the above but add the LD_PRELOAD thingy at the start. Again paste the results. 

All of this will hopefully produce some error text and we can then see what might be going on to solve your problem. And if 1 person is having a problem I am sure others do.

Can you paste the output of glxinfo too! (man this is going to be lots of text)

---

### Post by CaptainJamesKirk on 2008-06-05
I forgot to add that I tried somethings in the previous post >.>
And then pm'd you what I've tried.

I've tried running it in terminal and through ALT+f2 "run application." 
with a few commands. And it all does the same thing. 
The terminal error is...

idRenderSystem::Shutdown()
Sys_Error: couldn't find game dynamic library

---

### Post by adam_kimber on 2008-06-05
Ah oops. I missed that PM. So when you type doom3 from the prompt you only get the above or you do get something like the following:

If you get the following can you post the entire blurb? I expect its missing a file.....

> me@somecomputer ~ $ doom3
DOOM 1.1.1286 linux-x86 JUN 05 2008 12:00:00
Hostname: blah
Alias: blah
local IP: 127.0.0.2
------ Initializing File System ------
Loaded pk4 /opt/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /opt/doom3/base/pak001.pk4 with checksum 0x28d208f1

---

### Post by CaptainJamesKirk on 2008-06-05
It came up withhhhhh..

I just read it, should I download 'libGL.so.1'? If so, with synaptic?
I downloaded the 32bit libs or something.. I was googling it frantically earlier and a search said it needed 32bit libs or something. (Darn 64bit processor!) So I downloaded them and installed 'em. I got further with the command 'LD_PRELOAD=/usr/lib/libGL.so.1' then just 'doom3'


jamie@jamie-desktop:~$ LD_PRELOAD=/usr/lib/libGL.so.1 doom3
ERROR: ld.so: object '/usr/lib/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored.
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface wlan0 - 192.168.0.8/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/jamie/doom333/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /home/jamie/doom333/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /home/jamie/doom333/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /home/jamie/doom333/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /home/jamie/doom333/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /home/jamie/doom333/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /home/jamie/doom333/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/jamie/doom333/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/jamie/doom333/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /home/jamie/doom333/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/jamie/.doom3/base
/home/jamie/doom333/base
/home/jamie/doom333/base/pak008.pk4 (3 files)
/home/jamie/doom333/base/pak007.pk4 (38 files)
/home/jamie/doom333/base/pak006.pk4 (48 files)
/home/jamie/doom333/base/pak005.pk4 (63 files)
/home/jamie/doom333/base/pak004.pk4 (5137 files)
/home/jamie/doom333/base/pak003.pk4 (4676 files)
/home/jamie/doom333/base/pak002.pk4 (6120 files)
/home/jamie/doom333/base/pak001.pk4 (8972 files)
/home/jamie/doom333/base/pak000.pk4 (2698 files)
/home/jamie/doom333/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce 6150SE nForce 430/PCI/SSE2
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.15
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
...using GL_NV_register_combiners
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using EXT_depth_bounds_test
---------- R_NV20_Init ----------
---------------------------------
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Available.
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfp
glprogs/test.vfp
glprogs/interaction.vfp
glprogs/interaction.vfp
glprogs/bumpyEnvironment.vfp
glprogs/bumpyEnvironment.vfp
glprogs/ambientLight.vfp
glprogs/ambientLight.vfp
glprogs/shadow.vp
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
Regenerated world, staticAllocCount = 0.
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Sys_Error: couldn't find game dynamic library

---

### Post by adam_kimber on 2008-06-05
What happens when you type glxgears into a terminal?

PS I had a sneaking suspicion you were running a 64bit OS. A lot of programs don't work on 64bit Linux and windows for that matter. However the list in linux is decreasing. The problems arise when trying to run 32bit progs on 64bit. 

Have a look at this though. I think it might solve your library problems. [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Once installed run something like getlibs /home/jamie/doom333/base/doom3 or wherever doom3 is installed....

---

