---
title: "ATI + Envyng"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-08-29
The installation of the ATI driver went smooth. After reboot still no luck. fglrxinfo still gives me MESA. The ATI catalyst control center tells me:
[[img]http://bildr.no/thumb/246584.jpeg[/img]](http://bildr.no/view/246584)

Meaning the driver is in installed and detected but aren't enabled. Can anyone give me some help from here on. I can't seem to get the other guides to work for my card (god knows (if he exists) that I have read and tried more than a few guides for ATI on Ubuntu/linux). Guess I'm just on small step away from finally making it.

---

### Post by Crafty Kisses on 2008-08-29
Post the results of > glxinfo

---

### Post by peakshysteria on 2008-08-29
Thanks man.

```
glxinfo
```
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
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
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

---

### Post by Crafty Kisses on 2008-08-29
Have you checked the Restricted Drivers Manager to see if a driver is in there?

---

### Post by peakshysteria on 2008-08-29
The driver is there. But not in use/not checked and marked red. But all guides says this is normal after install. Not sure if it should be enabled there anyway. There is no doubt that the driver is installed. It's just not in use.
```
sudo aticonfig --initial -f
```gives me:
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3

---

### Post by Crafty Kisses on 2008-08-29
Try reconfiguring X and try again:```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by peakshysteria on 2008-08-29
```
sudo dpkg-reconfigure -phigh xserver-xorg
```is the right command in Hardy as far as I know. But it gives me:
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080829105731

```

(and now I'm really late for work.......) be back tonight to see if there are some other way to make this work...

---

### Post by Crafty Kisses on 2008-08-29
OK please post back, I appreciate it. :)

---

### Post by peakshysteria on 2008-08-29
> **peakshysteria said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```is the right command in Hardy as far as I know. But it gives me:
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080829105731

```


Like I said; it doesn't work. Not possible to reconfigure X. And Xorg is blank for some strange reason? How is that even possible?

---

### Post by Crafty Kisses on 2008-08-29
Did you backup your X.org? If you did you can use your backup.

---

### Post by peakshysteria on 2008-08-29
Sorry. I'm not to good with the terminal or Xorg. As mentioned in my third post there are some strange issues where a backup is mentioned. But how can I get it? And why do I need to? Also as mentioned above it doesn't help to run the reconfigure command. I only get a strange error.

Will it really replace the MESA driver and use the Envyng installed ATI driver? This is beyond me. Any chance you could explain this for me in layman's terms?

---

### Post by cbrigstocke on 2008-08-31
I'm having the same problem.  I've compiled drivers from scratch before, but would like to switch to a more automated method. So I would also appreciate some help. :-)

btw, I'm using my own custom kernel.  My dvd-rom doesn't work quite right with the ubuntu kernel.

---

### Post by cbrigstocke on 2008-08-31
I've done some fooling around with envyng and it installed perfectly to the ubuntu kernel although I was using my own kernel.  It doesn't look like envyng will work for me, unless there's some option I don't know about.

---

### Post by peakshysteria on 2008-09-01
If I reboot my machine it takes me a coupla hours of uninstalling and reinstalling the ATI driver to get the right resolution. Once again I'm back with the right resolution (it even detects the brand of my LCD) after finally once again making it through an Envyng ATI driver install process:
[[img]http://bildr.no/thumb/248185.jpeg[/img]](http://bildr.no/view/248185)

But like when I started this thread I'm still not running it apparently. fglrxinfo still says MESA.

AMD CCC says:
[[img]http://bildr.no/thumb/248186.jpeg[/img]](http://bildr.no/view/248186)

What can I do to make my Hardy run the allready installed ATI driver? Why doesn't Hardy detect and use the installed ATI driver? Can someone explain what's happening here? I can see that I'm not alone. But I still haven't found a solution for this exact problem.

xorg after latest rebooting and reinstalling via Envyng:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Driver		"fglrx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

:confused:

---

### Post by cbrigstocke on 2008-09-01
I've read somewhere that if you have the package xserver-xgl installed, it could cause the mesa driver to be used.  If it is installed, try uninstalling it and see what it does.

[Here's]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers") where I read this.

---

### Post by peakshysteria on 2008-09-02
Yeah I also heard that. I've actually also thought about it. I know that howto (since I've tried it several times without making it). But I would like compiz to work afterwards. And this most surely will break it. Also there is the dreaded whitescreen of death threat. Can anyone verify this recommendation? [Forlongs blog]("http://forlong.blogage.de/entries/796/comments") also mentions the same thing. But that is from Feisty. So not sure it will work on Hardy. As you all can see I'm a bit reluctant to just plunge into it blindfolded. But thanks for suggesting it anyway.

---

### Post by peakshysteria on 2008-09-03
*BUMP*

Hate to do it, but i can't believe that I'm the only one in here that have installed the ATI driver with Envyng and still seeing the dreaded MESA when running fglrxinfo in terminal.

There is no doubt that the driver is installed. But it's not in use. fglrxinfo gives me:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)


```

---

### Post by peakshysteria on 2008-09-05
Once again, hate to do it:

***BUMP***

---

### Post by peakshysteria on 2008-09-09
***bump***
:(

---

### Post by Shinger on 2008-09-10
ive got also the same problems with the ATI drivers..

problem with envyng is.. is that it uses ati drivers 8.4 and if you visit the website of envy the developer(s) spends alot of time in testing and developing Nvidia drivers havent seen abit about ati drivers.

So envyng isnt gonna solve the problem.

Ive installed the atidrivers through envyng, ive did it with restricted hardware drivers.. ive even downloaded the drivers from ati site and installed it manually.

I tried to install ubuntu 7.10 to see if i got it worked right there but with no succes.

So it must be the ati drivers it self.

Ive got the problem sinds 8.5 and if i install envyng (with 8.4 drivers i get in ubuntu but get problem with my lcd screen.

Info hardware

videocard: HIS ATI Radeon X1950 PRO 512 AGP
screen: Samsung SyncMaster T220 (orginal resolution 1680x1050)

---

### Post by peakshysteria on 2008-09-10
If I'm not mistaken Envy now installs the 8.6 version of the driver. But the latest version is version 8.8 (released Aug. 20, 2008). As mentioned even though the driver is installed it is not running since fglrxinfo still gives me the dreaded MESA.

But strangely enough there are some differences to my system. My Xerox LCD now properly goes into sleep mode. Which it didn't do before installing the driver. Also now rebooting my machine doesn't give me screen resolution troubles. I've always had big problems with the resolution after installing the ATI driver on my system no matter which method I've tried. In addition the catalyst control center is working. And it correctly recognizes my Xerox display (which Ubuntu don't manage to do without the driver). :confused:

But it still would be really nice to experience the driver and compiz. Now I can't run any desktop effects. Playing video is really crappy etc....

---

### Post by peakshysteria on 2008-09-14
***bump***

---

### Post by peakshysteria on 2008-09-18
Hate to do it. But roaming around goole have left me with no choice.

***BUMP***

---

### Post by markbuntu on 2008-09-18
OK, first, DO NOT USE ENVY. The reason you are defaulting to MESA is, you either have xserver-xgl installed or envy has failed to load the fglrx kernel modules which is a common problem with envy. xserver-xgl will cause the ati driver fglrx to fail and revert to mesa. It must be removed.

If you are having problems removing the driver you installed with envy, you can try to force downgrade it in Synaptic and then you can remove it.

If you have any of the newer ati cards, 48xx series, 3100 series, you need the ati driver 8.7 or better. These are not supported in earlier drivers. The best way to install the latest driver is here though some people have had success lately just running the downloaded installer:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

This has not yet been updated for the 8.9 driver but will be very soon.
The relase notes for the ati drivers are here, make sure your card is listed before trying to use the driver:

Release notes for 8.9

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html)

Release notes for 8.8

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html)

Release notes for 8.7

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html)

Release Notes for 8.6

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

Release notes for 8.5

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html)

---

### Post by peakshysteria on 2008-09-18
Thanks for posting. As you can see beneath my post(s) I have an ATI X700 EXCALIBUR PRO (256 MB). Which is supported well by ATI. And no the problem is not to remove the driver installed with Envyng. I have done that more than once. This time (as mentioned above) several changes have happened to my system after installing the driver (via Envyng) even though the driver is not in use apparently :confused:

Also using the installer from ATI gives me the same MESA problem (I haven't tried the latest installer. 8.8 didn't rok in my end). And as mentioned I have tried the wiki page. But using the terminal when it comes to the ATI driver is beyond me. I'm still not too comfortable with the terminal. So I can't seem to make it through the wiki howto. I'll try it once again when it upgrades to the latest driver. And I really hope they split it into a 32 bit and a 64 bit howto instead of adding 64 bit extra command line tips before and or after each step.

---

### Post by markbuntu on 2008-09-18
Did you remove xserver-xgl?
That is critical to getting the driver to work and may be all you need to do.

---

### Post by peakshysteria on 2008-09-18
I know the wiki pages tells us to [Removing Mesa drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide"). I haven't done that since I want to run Compiz if I get my system to use the driver. Also I'm not sure I can use the wiki method since I've installed the driver via Envyng.

---

### Post by markbuntu on 2008-09-19
Compiz will run just fine without xserver-xgl when you are using fglrx. But fglrx will not run with xserver-xgl installed. It just will not. Much older versions of the ati proprietary driver needed xserver-xgl to run compiz but the new drivers will not run properly if xserver-xgl is installed. They will default to mesa and horrible performance which is exactly what you are doing.

---

### Post by peakshysteria on 2008-09-20
Okey. I'll check the wiki pages for a method on removing xserver-xgl as soon as they are up again. Looks like they are down for the time being. I guess they are upgrading :)

is this the command:
```
sudo apt-get --purge remove xserver-xgl
```

---

### Post by anewguy on 2008-09-20
Yep, that should do it.  Another addition to this thread: I have an ATI 9250 and with Envy I had to tell it to use an older version (back in June ?? it was 1 version back) of the driver, not the newest one.  The newest one would not work.

Also, once you have removed xserver-glx and reinstalled your driver, you will also want to install the advanced desktop settings manager - the package is compizconfig-settings-manager if I remember correctly.  This will give you the "Advanced Desktop Effects Settings" option under system/preferences -> where you configure what you want compiz to do (such as the cube and it's behaviour).

---

### Post by peakshysteria on 2008-09-20
Ok. So I remove xserver-glx then reinstall the driver via Envyng? If this is so, what driver will I be running after removing xserver-glx before reinstalling the driver? (afraid of loosing my GUI/desktop. Not to good with the terminal...)

---

### Post by markbuntu on 2008-09-20
You should not need to renistall the driver, just remove xserver-xgl and reboot or do ctl-alt-backspace to reset the x server (be sure to close your applications to avoid losing anything before doing that).

---

### Post by peakshysteria on 2008-09-21
Thanks man. Tried it and it didn't work at all.
```
sudo apt-get remove xserver-xgl
```
gave me:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xgl is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Strange. What does this mean?
```
fglrxinfo

```still gives me:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

---

### Post by anewguy on 2008-09-21
Okay, this is a dumb question, but what happens when you do the following in a terminal:

compiz --replace <enter>


:)

---

### Post by peakshysteria on 2008-09-21
Lol, it gives me **the white screen of death**. Only way to get my desktop back is to restart X with Ctrl+Backspace. This is very strange.

---

### Post by new guy 222234 on 2008-09-21
Can anyone help me? I have windows XP and just down loaded off the internet Linus ubuntu 8.04.  How do I switch to that operating system?  How do I do it goeing foward?  How do I get rid of windows XP?  Please help.  My email if needed is [email]akeithline@mindspring.com[/email]

---

### Post by anewguy on 2008-09-21
> **new guy 222234 said:**
> Can anyone help me? I have windows XP and just down loaded off the internet Linus ubuntu 8.04.  How do I switch to that operating system?  How do I do it goeing foward?  How do I get rid of windows XP?  Please help.  My email if needed is [email]akeithline@mindspring.com[/email]

You need to search these forums for your answers, and not post in this thread as it is not related to your questions.  Please post your own thread.

---

### Post by anewguy on 2008-09-21
> **peakshysteria said:**
> Lol, it gives me **the white screen of death**. Only way to get my desktop back is to restart X with Ctrl+Backspace. This is very strange.

I'm going to assume that's because the glxinfo returns no for direct rendering.

What does your xorg.conf file look like?  Post it here. EDIT: I'm curious if load GLX is there.

Have you reviewed the /var/log/xorg.xxxxxxxx log files? (There may be several - like xorg.0.log for current, xorg.0.log.old)

Sorry if dumb questions - I remember fighting to get this to work as well but everything went great when I switched to the ATI 9250 card.

Dave :)

---

### Post by anewguy on 2008-09-21
Also found a post in the compiz forum (separate from these Ubuntu forums) that said with the X700 SE (don't know how that compares to your card) they used aiglx and the open source drivers to run compiz.

---

### Post by peakshysteria on 2008-09-21
**glxinfo:**

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
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

**/xorg.conf:**

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

Not sure if this is important but hear goes anyway **glxinfo |grep vendor** gives:

```
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: www.mesa3d.org

```

---

### Post by anewguy on 2008-09-21
Make a backup copy of your xorg.conf file, then try adding these to it:

Section "DRI"
        Mode 0666
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection


See if it makes any difference.

dave :)

---

### Post by peakshysteria on 2008-09-21
Hmm, smells like Gentoo magic. I'll look into it. Thanks man.

---

### Post by sdowney717 on 2008-09-23
seriously bump this!
I have same exact problem. Using an x1300, I always get mesa.
compiz gives white screen of death.
I tried using the ATI driver even built packages, they install but they dont work.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

this guide seems to me to work with certain older cards.
It does not work for an x1300 ATI 256 mb AGP

---

### Post by sdowney717 on 2008-09-23
IMO, this issue is serious enough that it should be happening to everyone. BUT, I dont think that most people are even aware they are running mesa drivers.

---

### Post by markbuntu on 2008-09-23
The fix for these problems has already been posted in this thread, post 24.

---

### Post by peakshysteria on 2008-09-24
> **markbuntu said:**
> The fix for these problems has already been posted in this thread, post 24.

Markbuntu I appreciate the help. But as you can see by my post [#33]("http://ubuntuforums.org/showthread.php?t=904253&page=4") this is not right. removing xserver-xgl wasn't possible on my system because it isn't installed :confused:

---

### Post by markbuntu on 2008-09-24
There is another thing you can try since you are unwilling to use the guide I pointed you to.

Remove the driver you got with envy (Envy will do that for you) and use Applications/Add/Remove to get the ATI binary X.Org driver and the ATI Catalyst Control Center. Just start typing them in the search box and they will show up.

Let me know how you make out with that and what version driver you end up with.

---

### Post by peakshysteria on 2008-10-14
hey markbuntu. Reinstalled Ubuntu last night. Changed from 64 bit to 32 bit (since my better half bit**ed me about the java problems and our bank). Anyway after a clean install I thought I should give the howto a spin once more. And everything checked out very nicely actually. I can't believe it. Everything is running smoother than ever (Compiz, the ATI driver, Java, Flash, SAMBA, my ports, Deluge, Amsn (been buggy for a week now)). Not as fast as my 64 bit. But I'll manage until next year anyways. Thanks a lot you people for helping me out. I gues I've done so much changes back and forth that Envy didn't want to work. Anyway no use for it now :)

 fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO
OpenGL version string: 2.1.7979 Release

:)

---

### Post by aNvII on 2009-06-21
Please help me!
I'm installed the envyng on ubuntu 9.04.
I'm installed the ATI display drivers and when i rebootet the computer all was different.
I cannot logg in the ubuntu beacose i don't see my logg in screen.All is colorfull.Is this beacose of resolution or what.
Please help me!


:(:(:(:(:(:(:(

---

### Post by markbuntu on 2009-06-21
DO NOT USE ENVY TO INSTALL ATI DRIVERS!!!!

Envy will install the wrong driver or misinstall the driver and not install the kernel modules.

Boot into recovery mode and use the fix x option. When you get back to the desktop use envy again and remove the driver completely.

What ati card do you have?

---

### Post by bongofinga on 2009-06-23
> **markbuntu said:**
> DO NOT USE ENVY TO INSTALL ATI DRIVERS!!!!

Envy will install the wrong driver or misinstall the driver and not install the kernel modules.

Boot into recovery mode and use the fix x option. When you get back to the desktop use envy again and remove the driver completely.

What ati card do you have?

Hi markbuntu, i'm in the same mess aswell!!! I'm having a problem with 9.04, whilst upgading the buggy video drivers it's all gone wrong. I've tried the xorg fix and also tried envyng, perhaps unwittingly after reading your previous post. It's mostly black screens but occasionaly a mess of colour like a scramble of what was the last thing in the video buffer. I was going to try the fix in post number 39 of this thread; 
[http://ubuntuforums.org/showthread.php?t=766699&page=4](http://ubuntuforums.org/showthread.php?t=766699&page=4)
but then i realised it was for good old hardy which i never had problem with, along with intrepid!! My spec is as follows;

Laptop: Acer Travelmate 7520
Video Card: ATI Radeon Xpress 1250
CPU: AMD Turion 64 X2 Mobile Technology TL-58 1.9Ghz
RAM: 2 Gb

Please help!! I miss Ubuntu and i can't handle this windows tripe!

Regards, bongofinga

---

