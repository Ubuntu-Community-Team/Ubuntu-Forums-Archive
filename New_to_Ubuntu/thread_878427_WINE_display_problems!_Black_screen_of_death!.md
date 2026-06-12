---
title: "WINE display problems! Black screen of death!"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by SeanLor on 2008-08-02
Greetings -
Not sure if I'm posting in the right area, feel free to waggle your finger if need be. I'm having issues with Wine - any time I run a program, my laptop screen blacks out. I have my TV hooked up via s-video, and whatever game I'm playing shows up there, but the usual monitor shows nothing. After quitting the WINE program, the issue persists until I restart. Any idea why this is going on, & how to fix it? Thanks!

---

### Post by Crafty Kisses on 2008-08-02
That sounds like a possible video card driver issue, have you installed your video card drivers?

Post the following output:
```
glxinfo
```

---

### Post by jualin on 2008-08-02
Try running wine using the terminal by writing > wine and post the results of it on the forums so we can assist you further.

---

### Post by SeanLor on 2008-08-02
Hallo - Codename, the output is:

[code]seanuary@seanuary-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM 4.1.3002
OpenGL version string: 1.4 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
seanuary@seanuary-laptop:~$ 
[code]

---

### Post by jualin on 2008-08-02
I think that Codename was right. It seems like a video card issue. Can you post the results of > lspci

---

### Post by SeanLor on 2008-08-02
Not sure if this is what you were referring to, I'll bet you meant try running a program in wine via terminal, but 'wine' just spat out

seanuary@seanuary-laptop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
seanuary@seanuary-laptop:~$ 

(Apparently I don't know how to use code tags, either, so I skipped that.)

---

### Post by SeanLor on 2008-08-02
Here ye be, good sir, madam, or transgendered being;

seanuary@seanuary-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
seanuary@seanuary-laptop:~$

---

### Post by jualin on 2008-08-02
Your video card seems to be Intel GM965 and [here]("http://www.intellinuxgraphics.org/download.html") is a guide of how to install the drivers for it. Good luck!

---

### Post by johnlvs2run on 2008-08-02
> **jualin said:**
> I think that Codename was right. It seems like a video card issue. Can you post the results of "lspci"

The output from "lspci" is returning a lot of unknown devices.
I've been having to adjust the resolution of the Nvidia video with every reboot.

> xxx@xxx-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075c (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0751 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 SATA controller: nVidia Corporation Unknown device 0584 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0778 (rev a1)
00:12.0 PCI bridge: nVidia Corporation Unknown device 075b (rev a1)
00:13.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
xxx@xxx-desktop:~$

---

### Post by SeanLor on 2008-08-02
Thanks! For fear of sounding like a mook, what is one to do with them there repositories, or alternately how would one install the drivers?

---

### Post by SeanLor on 2008-08-02
John: shma? Say what now? I apologize, but I have no idea what significance that has. Sounds not good; translate into moron for me? ;)

---

### Post by jualin on 2008-08-02
> **johnlvs2run said:**
> The output from "lspci" is returning a lot of unknown devices.
I've been having to adjust the resolution of the Nvidia video with every reboot.

For that you need to install nvidia-settings via Synaptic or via terminal > sudo apt-get install nvidia-settings The run nvida-settings using the terminal as root. > sudo nvidia-settings Then changing the resolution there and saving the Xorg file (Clicking where it says save X org file), then you should be able to log in and log out keeping the same resolution.

---

### Post by jualin on 2008-08-03
> **SeanLor said:**
> Thanks! For fear of sounding like a mook, what is one to do with them there repositories, or alternately how would one install the drivers?

The first step is to install git-core via Synaptic Package Manager or via terminal > sudo apt-get install git-core, and then running the command that Intel suggests (for 3D)> git-clone git://anongit.freedesktop.org/git/mesa/mesa
 (for 2D) > git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
 and then I am guessing is just installing the packages that they suggest 2D driver: xf86-video-intel 2.4.0 release
3D driver: branch mesa_7_0_branch commit 97eb33529ae2f96220eec5238d8d0e9a07ce91d5

*edit* I am doing it right now and after running the > git-clone git://anongit.freedesktop.org/git/mesa/mesa you need to write the package name in that case > branch mesa_7_0_branch commit 97eb33529ae2f96220eec5238d8d0e9a07ce91d5 and then just wait until it finishes

---

### Post by johnlvs2run on 2008-08-03
Sorry, SeanLor, will start a new thread next time.

> **jualin said:**
> Then run nvida-settings using the terminal as root.

> sudo nvidia-settings

Jualin, the 2nd part comes up with an error, and pops up a Nvidia server screen.
Previous attempts from that screen have not yet been successful.

> xxx@xxx-desktop:~$ sudo nvidia-settings

ERROR: Error parsing configuration file '/home/john/.nvidia-settings-rc' on
       line 51: '0/XVideoTextureHue=0' (Unrecognized attribute name).

---

### Post by jualin on 2008-08-03
> **johnlvs2run said:**
> Sorry, SeanLor, will start a new thread next time.



Jualin, the 2nd part comes up with an error, and pops up a Nvidia server screen.
Previous attempts from that screen have not yet been successful.

I saw that your previous tries in another threads were not successful. Do you get the nvidia settings screen? [[IMG]http://img297.imageshack.us/img297/2933/screenshotsu6.th.png[/IMG]](http://img297.imageshack.us/my.php?image=screenshotsu6.png)

---

### Post by johnlvs2run on 2008-08-03
Yes, I get the settings screen and have been successful changing the resolution from there, 
but not at getting anything to stay set.

---

### Post by jualin on 2008-08-03
I had this problem before and I read the solution somewhere. You need to run it as root > sudo nvidia-settings Then you would go to "X Server Display Configuration", change your resolution, press apply, and finally click on "Save to X Configuration File". I am off to bed soon because it's kind of late but if it doesnt work just let me know and I will answer you today or tomorrow. Hope it works!

---

### Post by jualin on 2008-08-03
After this, sometimes you still need to change the resolution using the "Screen Resolution" interface found under System, Preferences.

---

### Post by jualin on 2008-08-03
Also maybe [this]("http://ubuntuforums.org/showpost.php?p=3853781&postcount=2") might help if my suggestion fails.

---

### Post by jualin on 2008-08-03
[This was the website I saw with the original solution]("http://davidwinter.me.uk/articles/2007/07/24/fixing-screen-resolution-with-nvidia-drivers-on-ubuntu/"). I had a similar problem, I didn't know my monitor could support a higher resolution until one day I decided to try nvidia-settings, when I tried it I ran into the same problem that you are running, and decided to look for an answer, and luckily found that one. Good luck!

---

### Post by johnlvs2run on 2008-08-03
Jualin, it worked! 

Thank you very much.  :)

---

### Post by jualin on 2008-08-03
I am very glad to hear that! Remember to update the status of your problem in the other thread that you asked for help, and maybe posting the solution yourself for future people running into the same problem. Good nite!

---

### Post by SeanLor on 2008-08-03
Hokay, still confused = write the pkg name where? I tried copying & pasting that 'branch......." into terminal, no dice, and searching for a pkg of that name in synaptic did nada.

---

### Post by jualin on 2008-08-03
Actually I found that ubuntu has the packages available on the repositories.  So the process is simpler you just have to install the package "xf86-video-intel" using Synaptic or via terminal > sudo apt-get install xf86-video-intel. Hope this helps you.

---

