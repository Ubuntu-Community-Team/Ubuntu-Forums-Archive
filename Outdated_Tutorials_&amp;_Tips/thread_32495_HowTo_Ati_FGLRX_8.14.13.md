---
title: "HowTo: Ati FGLRX 8.14.13"
date: 2005-05-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Jesus Franco on 2005-05-08
This is my first how to.

I wanted better performance out of my ati video card, and I know we all do. ATI is working *hard* to imporve thier drivers. The latest ones released on 05/09/05 is version 8.14.13, I belive these are the ones that the next version of Ubuntu will use. Unless of course ATI makes a newer one. Anyway the ones in the repository are version 8.8.25 witch is pretty behind. I think ATI wont release a newer version unless they had a good reson. I think the newest ones have improved performance for OpenGL etc. I tried to make it as simple and n00b friendly as possible. It looks like alot but it really isnt. It can be done in about 5 mins tops. It just that I talk alot of jiberish. Excuse me :p

NOTE: These drivers require Linux-Kernel-Headers for your running kernel. Open up Synaptic and make sure they are installed.

_**Step 1:**_ Open up a terminal window (Applications>System Tools>Terminal)

**_Step 2:_** In the terminal windows type the following ```
# wget http://www2.ati.com/drivers/linux/ati-driver-installer-8.14.13.run 
# sudo sh ./ati-driver-installer-8.14.13.run 
``` Press enter. Pick Install Driver. Then Click the Automatic Installation.When it is finished exit.

**_Step 3:_** Now type ```
# sudo gedit /etc/X11/xorg.conf 
```
In your xorg.conf file make sure that under Section "Module" the following lines are listed
```
 
 Load "dri"
 Load "glx"

```
Now look for Section "Device" And make sure that it looks like the following
```
 
 Identifier  "Radeon"
 Driver  "fglrx"
 Option  "UseInternalAGPGART" "no" 
 BusID  "PCI:3:0:0"

```
Its okay if your Identifier is different and if your BusID is different aswell. But make sure your Driver says "fglrx" and that you have the "Option              "UseInternalAGPGART" "no" " Right below it.

Now look for another section. Most of the time this is the last one listed.
```
 
Section "DRI"
 Mode 0666
EndSection

```

If it is not on your config Make Sure You Add It.

Reboot and it should work! :grin:

If it does not work make sure you check out this post [HERE](http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87) 
Enjoy :D

Links:
[Original how to by teumima](http://ubuntuforums.org/showthread.php?t=22496)
[My website  :razz: ](http://www.jesusfranco.3qhost.com)

---

### Post by Petrush on 2005-05-08
Somehow i don't get it to work, have been trying to get these to work before your howto but no success.

Following your steps, i get an warning at the make.sh script:
[FONT=Courier New]Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
build succeeded with return value 0[/FONT]

It seems to succeed to make some kind of .ko file that is installable, but when i try to use it, it only ends up using the mesa drivers (according to fglrxinfo).

regards,

---

### Post by Jesus Franco on 2005-05-08
Do not know if this helps man. But tell me if it does.

```
sudo apt-get install build-essential
``` 
I think it should help. After all the error is during compiling

---

### Post by twigsby on 2005-05-08
I get the same error as Petrush

```
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-k7/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6. x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-k7'
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.c md for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-k7'
build succeeded with return value 0
duplicating results into driver repository...
done.

``` 

There is no hidden .libfglrx_ip.a.GCC3.cmd file in the 2.6.x folder.  :-|

---

### Post by clb137 on 2005-05-08
hi there can you help I get to the end and i get this message

clinton@ubuntu:/lib/modules/fglrx$ sudo sh make_install.sh
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko): Operation not permitted
failed.


thanks


clinton

---

### Post by atze on 2005-05-08
Hi
I have finde out how to resolve the problem:

check this url:

[http://ubuntuforums.org/archive/index.php/t-24763.html](http://ubuntuforums.org/archive/index.php/t-24763.html)

**6. sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME** and it works  :grin:

---

### Post by twigsby on 2005-05-08
[QUOTE=atze]Hi
I have finde out how to resolve the problem:

check this url:

[http://ubuntuforums.org/archive/index.php/t-24763.html](http://ubuntuforums.org/archive/index.php/t-24763.html)

**6. sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME** and it works  :grin:[/QUOTE]
 Excellent, although I still got the error message when makeing the modules, the drivers installed properly and 3d Acceleration works. 

My glxgears score went up from around 1800 to 2500 and UT2004 Onslaught doesn't pause anymore. :)

---

### Post by ZarathustraDK on 2005-05-08
Hey, absolute newbie here.

I've tried this howto and it didn't work, then I figured I would try downloading the packages with synaptic (for the "easiest, but not so certain, way; ie. downloading the xorg-driver-fglrx+fglrx-control(I think that was their names)+something else that I already had (from other ATI-howto's if you wonder :)

BUT!

I get an error message saying :

(Translated from danish)
E: /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb:  tries to overwrite '/usr/X11R6/bin/fgl_glxgears', which also is in the package fglrx-6-8-0

So how do you get synaptic to force an overwrite? The part of the package mentioned is already there, but there's some other crucial thing it need to install in order to install the xorg-driver-fglrx.

He...seems stupid to be derailed by such a simplicity after I managed to recover from an X-related commandline crash (*COUGH* with some memorized help from this howto*COUGH*). ](*,) 

Any ideas?

EDIT : It seems whatever action that should make the /lib/modules/2.6.10-5-386/kernel/video directory didn't work (the dir isn't there). Which action is responsible for making that dir?

EDIT 2 : Nevermind, did the commandline thing. Basically removing all of the fglrx-packages with synaptic, and thereafter installing all the "linux-restricted-modules-2.6.10-5-386" and "xorg-driver-fglrx" modules from the commandline as described.

Finally! :-) very nice with 1800-2000 FPS

Next stop "Gaming on Hoary", to try and find out where the sound went :)

---

### Post by Petrush on 2005-05-08
ok! 

added the build-essentials, 
followed [http://ubuntuforums.org/archive/index.php/t-24763.html](http://ubuntuforums.org/archive/index.php/t-24763.html)
i.e. removed old fglrx before (beware X not starting!)
moved the kernelfile to home (i find this a bit strange)

it gave same error when bulding (the *.cmd file missing), but the drivers seems to work (using it now), get the new version from fglrxinfo.

Thanks!

---

### Post by Jesus Franco on 2005-05-08
I wish I could help you guys.  :| 
But I am not a guru nor do i now what exactly those problems are. It works for me. And all I did was explain how I did it in a easy way. Sorry. Maybe someone else here knows how to fix those problems.

---

### Post by dewey on 2005-05-08
I'm getting problems on ```
cd /lib/modules/fglrx
sudo sh make_install.sh
```

It looks like this, bad grammar and all. ```
[fglrx:firegl_stub_register]*ERROR* Unable to the open some already present DRM kernel Module!
```

I also get the```
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-k7/kernel/drivers/video/fglrx.ko): Operation not permitted
failed.
``` Error.  I tried one of the fixes posted already.

ok, I've tracked the problem to missing the fglrx.ko file, how do I get it?  Note: This is from a clean install

---

### Post by Jesus Franco on 2005-05-09
I belive you all are getting these problems because you dont have the ones from the respository installed. Before you do the guide do the following.
```
sudo apt-get install linux-restricted-modules-<your-kernel-version> xorg-driver-fglrx
```

Sorry that I forgot to mention I didnt do this on a clean install. Maybe that has something to do with it.  ](*,) 

First post edited.  :?

---

### Post by dolny on 2005-05-09
I had no problems with the installation described in the 1st post but the games can't initialize OpenGL :(

---

### Post by dewey on 2005-05-09
Okay, I was very tired last try and forgot I had already moved my .ko file.... I have X starting now, getting ~1144 fps in glx gears.  Is this normal for my machine... AMD64 3000+ (using k7 x86 kernel) 512mb ddr 2100, 128mb Radeon 9200SE/T ?  It seems pretty low.

Also, I get an enormously large output from glxinfo.
```
dewey@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.5010 (X4.3.0-8.12.10)
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

```

---

### Post by SWAT on 2005-05-09
I cant get it to work. I keep getting only the MESA drivers  ](*,) I used this howto step-by-step in a terminal (no Gnome running), and it still doesnt work. My 'information':
* Ubuntu 686 kernel
* I installed drivers according to this howto and it worked [http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10)
* Then I tried to upgrade using this howto (because of UT2004 bug fix in the drivers)
* Now Im stuck with the MESA drivers and somehow I cant bring myself to reinstall Ubuntu because of some evil driver problem.

I keep getting the MESA drivers @ fglrxinfo  ](*,) Please help...

edit: my glxinfo looks like the same as the glxinfo from dewey

---

### Post by Jesus Franco on 2005-05-10
[QUOTE=SWAT]I cant get it to work. I keep getting only the MESA drivers  ](*,) I used this howto step-by-step in a terminal (no Gnome running), and it still doesnt work. My 'information':
* Ubuntu 686 kernel
* I installed drivers according to this howto and it worked [http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10)
* Then I tried to upgrade using this howto (because of UT2004 bug fix in the drivers)
* Now Im stuck with the MESA drivers and somehow I cant bring myself to reinstall Ubuntu because of some evil driver problem.

I keep getting the MESA drivers @ fglrxinfo  ](*,) Please help...

edit: my glxinfo looks like the same as the glxinfo from dewey[/QUOTE]

Does your device section have the following option?
```
Option "UseInternalAGPGART" "no"
```

---

### Post by SWAT on 2005-05-10
Yes, I've manually edited the xorg.conf file and that setting is set to no. Although someone on #ATI suggested I use the fglrx-config tool, I edited it manually. I did this because the ATI drivers also worked before, without the config tool and there are a lot of warnings on ubuntuforums.org to NOT use the ATI config tool.
Any thoughts on what else could be the problem?
In a ideal situation (with 'old' ATI drivers installed) should this howto also work? (doing a driver-update)

---

### Post by Jesus Franco on 2005-05-10
I did this while having the drivers from the repository installed. And it worked without any problems.

---

### Post by dolny on 2005-05-10
My output: 

```
dolny@milkshake:/lib/modules/fglrx/build_mod$ sudo sh make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6
.x modules
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.10-5-686'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `agp_find_supported
_device':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6526: warning: unused variable `
cap_ptr'
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6507: warning: `agp_check_suppor
ted_device' defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_put
minor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:508: warning: `inter_module_p
ut' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:510: warning: `inter_module_u
nregister' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_reg
ister':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:530: warning: `inter_module_r
egister' is deprecated (declared at include/linux/module.h:577)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:561: warning: `inter_module_p
ut' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2660: warning: initialization
 from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_vm_map':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2721: warning: `remap_page_ra
nge' is deprecated (declared at include/linux/mm.h:773)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2788: warning: `remap_page_ra                                                                                                  nge' is deprecated (declared at include/linux/mm.h:773)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2825: warning: `remap_page_ra                                                                                                  nge' is deprecated (declared at include/linux/mm.h:773)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_uninit                                                                                                  ':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3157: warning: `inter_module_                                                                                                  put' is deprecated (declared at include/linux/module.h:582)
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.c                                                                                                  md for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.10-5-686'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
==============================
dolny@milkshake:/lib/modules/fglrx/build_mod$

```

:(

I installed fglrx packages and got further (to the moment described above). Going to work on this more.

---

### Post by dolny on 2005-05-10
**OH MY GOD! IT WORKS!!!**

After following the tutorial + moving the fglrx etc. - thanks for this thread and replies!
I spent 3 days following diff tutorials! THANKS! :D

---

### Post by NoTiG on 2005-05-10
I think i have a slight problem. I followed the directions exactly (except replacing the filename with the 64 bit one since im doing the 64 bit driver) ... everything went without error. I restarted and all... BUt when i run glxgears... it lists as 144 FPS . i think that is low right??????? And when I run tuxracer.... the fps is so slow it is unplayable. so i believe something is wrong. I opened up /etc/X11/xorg.config again after to see that i was using the fglrx driver and the changes are still there... so what is wrong??? BTW im using an ATI 9600 Mobility , on a amd64 300 .. with 512mb of ram.

---

### Post by Jesus Franco on 2005-05-10
Do you have your kernel headers? I mean the right ones. The ones for your 64bit kernel.  :neutral: 

I really dont know how some people get errors. Ati's site offers very limited documentation on these isssues if any.

---

### Post by Monchy on 2005-05-10
Well everything went off without a hitch, 2123.800 FPS in glxgears. The only problem now is that i'm seemingly stuck on 1280 x 1024 @60hz which is a killer for my eyes(can't change res. via System > Prefs > Screen Res). Is that normal or is there a fix for that?

---

### Post by Jesus Franco on 2005-05-10
When using the drivers you have to edit change your screen resolution by editing your X.Org config file.

---

### Post by motionsiren on 2005-05-10
Would this driver bundle work with my very old ATI card?

```
VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
```

---

### Post by Monchy on 2005-05-10
[QUOTE=Jesus Franco]When using the drivers you have to edit change your screen resolution by editing your X.Org config file.[/QUOTE]

Ok did that and it boots up in 1152 for me :). Any idea if that problem will be fixed with the next set of drivers or?

---

### Post by Chromance on 2005-05-10
Will these ATI drivers 8.12.10 work for a ATI mobility Radeon 9600/9700 series
cards?

Chromance

---

### Post by SWAT on 2005-05-11
Yes.... problem solved. 
I removed the 'old' fglrx, by using Synaptic. Then I used the howto in THIS thread and JUST BEFORE compiling you need to do **sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME**. Then it still compiles with an error, but it works fine  :)

---

### Post by rince on 2005-05-11
[QUOTE=Chromance]Will these ATI drivers 8.12.10 work for a ATI mobility Radeon 9600/9700 series
cards?
[/QUOTE]

I couldn't get it to work with my Mobility Radeon. Everything works fine util the kernel module install script tries to load the module.
Then i get the following error:

> 
[fglrx:firegl_init] *ERROR* Device not found!
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko): No such device


---

### Post by cwestpha on 2005-05-18
ok, that was a stupid question. I already had the package. -.-

P.S.
I tried SWAT's way and it worked. Except what I did was wipe out the linux package along with the drivers. Then just followed the directions, adding his command in the proper place of course, to the original instructions.
Dont care if some of that is unnececary becuase it works fine now.

---

### Post by slipp3dstr3am on 2005-05-18
[QUOTE=rince]I couldn't get it to work with my Mobility Radeon. Everything works fine util the kernel module install script tries to load the module.
Then i get the following error:[/QUOTE]


that is the same error that i'm getting ....

---

### Post by LinxNew on 2005-05-18
Hi,

sorry for my newbie question, but I have this error :

user@localhost:/lib/modules/fglrx/build_mod$ sudo sh make.sh
make.sh: line 46: gcc: command not found
make.sh: line 52: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h

I'm little bit  :-? 

What's wrong ?

I see, and I have installed 'Non-free Linux 2.6.10 modules on 386'

---

### Post by LinxNew on 2005-05-19
it's all ok.

---

### Post by rimmer on 2005-05-19
Been lookin for this for a week !
50% improvement in fps, cool thanks.

---

### Post by Lars A E on 2005-05-19
I spent a considerable amount of time getting 3d acceleration working with the old fglrx driver. Installing the new driver went very smooth. Unfortunately direct rendering was lost. So, now I'ts back to the good old one... Btw, my card is X300 mobility.

---

### Post by vannguyen0 on 2005-05-19
I have an IBM T43 w/ a Mobilitiy Radeon X300.  I did everything to install the FGLRX drivers.  But when I reboot my laptop, the screen goes black when trying to startx.  I changed my xorg.conf to go back to the ati drivers and I'm able to boot up.  I did a lspci and found this:

0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
**0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5460**
0000:02:00.0 Ethernet controller: Broadcom Corporation: Unknown device 167d (rev 11)
0000:04:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
0000:04:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

does that mean I can't use the FGLRX drivers??  I can post my xorg.conf if needed... but it's pretty much like everyone's in here.  any info will help.  thanks

---

### Post by Lars A E on 2005-05-20
> I have an IBM T43 w/ a Mobilitiy Radeon X300. I did everything to install the FGLRX drivers. But when I reboot my laptop, the screen goes black when trying to startx. I changed my xorg.conf to go back to the ati drivers and I'm able to boot up. I did a lspci and found this:  0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03) 0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03) 0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) 0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03) 0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) 0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) 0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) 0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) 0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) 0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3) 0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03) 0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) 0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03) 0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03) 0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03) 0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5460 0000:02:00.0 Ethernet controller: Broadcom Corporation: Unknown device 167d (rev 11) 0000:04:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d) 0000:04:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)  does that mean I can't use the FGLRX drivers?? I can post my xorg.conf if needed... but it's pretty much like everyone's in here. any info will help. thanks 
Adding the following line to the "Device" section in my xorg.conf solved my initial problems with the fglrx-driver:
```
Option "MonitorLayout" "LVDS,STV"
```
As mentioned, the newest version won't give me acceleration so I use the version that is found in the repositories.

---

### Post by vannguyen0 on 2005-05-20
[QUOTE=Lars A E]Adding the following line to the "Device" section in my xorg.conf solved my initial problems with the fglrx-driver:
```
Option "MonitorLayout" "LVDS,STV"
```
As mentioned, the newest version won't give me acceleration so I use the version that is found in the repositories.[/QUOTE]

When you went back to the version that was in the repositories, did that give you 3D acceleration?  What kind of frame rates were you getting with glxgears and fgl_glxgears?

---

### Post by vannguyen0 on 2005-05-20
[QUOTE=Lars A E]Adding the following line to the "Device" section in my xorg.conf solved my initial problems with the fglrx-driver:
```
Option "MonitorLayout" "LVDS,STV"
```
As mentioned, the newest version won't give me acceleration so I use the version that is found in the repositories.[/QUOTE]

**ok.  vanilla install w/ repository's fglrx drivers.  when i have the radeon drivers, here's how it detects my monitor:**

(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): LVDS port is not in connector table, added in.
(II) RADEON(0): Connector0: DDCType-0, DACType-1, TMDSType--1, ConnectorType-1
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(**) RADEON(0): MonitorLayout Option: 
	Monitor1--Type AUTO, Monitor2--Type AUTO

(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 0
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- Proprietary
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- NONE
 DDC Type  -- NONE




**when i have the fglrx drivers loaded (w/ Option "MonitorLayout" "LVDS,STV") (monitor blacks out while trying to start X):**

(II) fglrx(0): I2C bus "DDC" initialized.
(II) fglrx(0): Connector Layout from BIOS -------- 
(II) fglrx(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(WW) fglrx(0): Invalid Monitor type specified for 2nd port 
(**) fglrx(0): MonitorLayout Option: 
	Monitor1--Type LVDS, Monitor2--Type STV

(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 3 with Monitor Type 0
(II) fglrx(0): Primary head:
 Monitor   -- LVDS
 Connector -- None
 DAC Type  -- Unknown
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) fglrx(0): Secondary head:
 Monitor   -- NONE
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) fglrx(0): 
(**) fglrx(0):  Screen Overlap 0 pixel
(WW) fglrx(0): Only single display is connected, DesktopOption will be ignored




[B]Why is fglrx detecting my secondary head as my primary DAC type?  Here's my xorg.con:
[/B]
Section "Monitor"
  Identifier   "Generic Monitor"
  ModelName    "THINKPAD 1400X1050 LCD PANEL"
  Option       "DPMS"
  VendorName   "IBM"
EndSection

Section "Device"
   Identifier                          "ATI Technologies, Inc. Radeon Mobility M300 (M22) 5460 (PCIE)"
   Driver                              "radeon"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
   #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
   Option "no_accel"                   "no"
   Option "no_dri"                     "no"
# === misc DRI settings ===
   Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
   Option "DesktopSetup"               "0x00000200"
   Option "MonitorLayout"	       "LVDS,STV"
#   Option "MonitorLayout"              "AUTO, AUTO"
   Option "IgnoreEDID"                 "off"
   Option "HSync2"                     "unspecified"
   Option "VRefresh2"                  "unspecified"
   Option "ScreenOverlap"              "0"
# === TV-out Management ===	
   Option "NoTV"                       "yes"
   Option "TVStandard"                 "NTSC-M"
   Option "TVHSizeAdj"                 "0"
   Option "TVVSizeAdj"                 "0"
   Option "TVHPosAdj"                  "0"
   Option "TVVPosAdj"                  "0"
   Option "TVHStartAdj"                "0"
   Option "TVColorAdj"                 "0"
   Option "GammaCorrectionI"           "0x06419064"
   Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
   Option "Capabilities"               "0x00000000"
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
   Option "UseFastTLS"                 "2"
   Option "BlockSignalsOnLock"         "on"
   Option "UseInternalAGPGART"         "no"
   Option "ForceGenericCPU"            "no"
   BusID "PCI:1:0:0"    # vendor=1002, device=4e50
   Screen 0
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Device          "ATI Technologies, Inc. Radeon Mobility M300 (M22) 5460 (PCIE)"
       Monitor         "Generic Monitor"
       DefaultDepth    24
       SubSection "Display"
               Depth           1
               Modes           "1400x1050"
       EndSubSection
       SubSection "Display"
               Depth           4
               Modes           "1400x1050"
       EndSubSection
       SubSection "Display"
               Depth           8
               Modes           "1400x1050"
       EndSubSection
       SubSection "Display"
               Depth           15
               Modes           "1400x1050"
       EndSubSection
       SubSection "Display"
               Depth           16
               Modes           "1400x1050"
       EndSubSection
       SubSection "Display"
               Depth           24
               Modes           "1400x1050"
       EndSubSection
EndSection

---

### Post by Lars A E on 2005-05-21
Unfortunately I'm far from beeing a guru when it comes to xorg configuration. I can't give you any further advice. 
The old fglrx gives me 3d accel with ~1250 fps in glxgears and ~250 fps in fgl_glxgears.

Here's my xorg.conf. It contains some tweaks from different howto's. Most of wich were necessary to get x up and running.
```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load 	"GLcore"
	# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	#Driver		"ati"
	
	Driver "fglrx"
	# If X refuses to use the screen resolution you asked for,
	# uncomment this; see "Bugs and Workarounds" for details.
	#Option "NoDDC"
	Option "MonitorLayout" "LVDS,STV"

	# === Video Overlay for the Xv extension ===
	Option "VideoOverlay" "on"

	# === OpenGL Overlay ===
	# Note: When OpenGL Overlay is enabled, Video Overlay
	# will be disabled automatically
	Option "OpenGLOverlay" "off"

	# === Use internal AGP GART support? ===
	# If OpenGL acceleration doesn't work, try using "yes" here
	# and disable the kernel agpgart driver.
	#Option "backingstore" "true"
	Option "UseInternalAGPGART" "no"

	# You don't actually need this next BusID bit - unless maybe you have dual monitors?
	# I've removed it from mine (single monitor only) and all is well.
	# I think it's a leftover from fxglrconfig - doh!
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1680x1050" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1680x1050" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1680x1050" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1680x1050" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1680x1050" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1680x1050" "1280x800" "960x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by JimmyJazz on 2005-05-21
[QUOTE=SWAT]I cant get it to work. I keep getting only the MESA drivers  ](*,) I used this howto step-by-step in a terminal (no Gnome running), and it still doesnt work. My 'information':
* Ubuntu 686 kernel
* I installed drivers according to this howto and it worked [http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10)
* Then I tried to upgrade using this howto (because of UT2004 bug fix in the drivers)
* Now Im stuck with the MESA drivers and somehow I cant bring myself to reinstall Ubuntu because of some evil driver problem.

I keep getting the MESA drivers @ fglrxinfo  ](*,) Please help...

edit: my glxinfo looks like the same as the glxinfo from dewey[/QUOTE]

I am stuck with MESA drivers to, even when I try to go back to the old driver

---

### Post by Curlydave on 2005-05-21
</boot/vmlinuz>   ... This is my kernal, right? It seem sto work, but then it says it can't find package linux restricted modules.

How do I fix this?

---

### Post by sapo on 2005-05-21
It worked here.. but i had to do 2 things:

```

sudo /etc/init.d/gdm stop
sudo apt-get remove fglrx-6-8-0
sudo mv /lib/modules/MYKERNELVERSION/drivers/video/fglrx.ko /home/user/backup/

```

hehe let me explain...

i Dont know why but even loading the module my Direct Rendering wasnt working... so  removed the old fglrx kernel module, and made everything again after UNINSTALLING the ubuntu fglrx package....

I dont know why it happened but i seemed that the new driver wasnt overwriting the old one and was having some conflits.. it just worked when i FULLY removed the ubuntu fglrx driver and compiled the new one.

---

### Post by Sneseglarn on 2005-05-24
[QUOTE=Chromance]Will these ATI drivers 8.12.10 work for a ATI mobility Radeon 9600/9700 series
cards?

Chromance[/QUOTE]


YES, i just got them working, but it was a pain, check DMESG and /var/log/Xorg.0.log , and /var/log/messages for fails, and just google it, after 3 hours i finally got it working..

---

### Post by jtwadsworth on 2005-05-25
I followed this HOWTO exactly to the letter on a fresh install of Ubuntu Hoary.  Everything seemed to install without errors, but I still get Mesa instead of fglrx.  The problem is that the kernel is not the right version!?  Note when I load the headers Synaptic seems to load two versions.  I did this without updating Hoary with the autoupdate applet.

Here is my Xorg.0.log error.  Please someone help me with this it has been 3 weeks now trying everything I know how to get this to work.  Whatever I try next need I do another clean install?  Synaptic shows both the xorg-driver-fglrx 8.8.25 is installed as well as fglrx-6-8-0 version 8.12.20-2.  Is this the problem?  The 8.8.25 is installed in the first line of this HOWTO.

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8d1d000 at 0xb7db4000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


Please help this is killing my move to Linux.

jtw

---

### Post by brj on 2005-05-25
hi,

i had them working as well, frame rate has increased but i never managaged to get a picture on the dvi-output of my ati9200. analog-output was ok.

jakob

---

### Post by jarno on 2005-05-25
[QUOTE=brj]

i had them working as well, frame rate has increased but i never managaged to get a picture on the dvi-output of my ati9200. analog-output was ok.

[/QUOTE]

I can't get picture out of dvi with fglrx-drivers neither. I gues it is a bug in the driver.

--
    /jarno

---

### Post by foxy123 on 2005-05-25
[QUOTE=jtwadsworth]I followed this HOWTO exactly to the letter on a fresh install of Ubuntu Hoary.  Everything seemed to install without errors, but I still get Mesa instead of fglrx.  The problem is that the kernel is not the right version!?  Note when I load the headers Synaptic seems to load two versions.  I did this without updating Hoary with the autoupdate applet.

Here is my Xorg.0.log error.  Please someone help me with this it has been 3 weeks now trying everything I know how to get this to work.  Whatever I try next need I do another clean install?  Synaptic shows both the xorg-driver-fglrx 8.8.25 is installed as well as fglrx-6-8-0 version 8.12.20-2.  Is this the problem?  The 8.8.25 is installed in the first line of this HOWTO.

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8d1d000 at 0xb7db4000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


Please help this is killing my move to Linux.

jtw[/QUOTE]


try to remove all fglrx packages with synaptic and then start it over again... please check also if you have the same kernel headers as your kernel...

---

### Post by jtwadsworth on 2005-05-25
The kernal / headers are identical matches.  I redid everything and still get the same error.

jtw

---

### Post by asmodeas on 2005-05-28
[QUOTE=Sneseglarn]YES, i just got them working, but it was a pain, check DMESG and /var/log/Xorg.0.log , and /var/log/messages for fails, and just google it, after 3 hours i finally got it working..[/QUOTE]

Shouldnt take longer than 10 minutes.
Here for anyone wanting to install the latest ati dirvers for the mobility 9800, this is  based on heaps of other peoples guides that gets ati drivers working

You need to install the headers for your kernel,use synaptic or whatever.
Ensure that there are no other fglrx drivers installed, might be under xorg drivers,
but the ones that are in the repositories for ubuntu 5.04 keep locking up inspiron 9100s  with the mobility 9800. Make sure you remove all previous fglrx drivers completely.
Oh depending on what kernel your using modify some of the lines below with the kernel version, i had been using 2.6.10-5-386 but i have since changed to the 686 smp kernel. Download the linux driver from ati, then follow below.

~$ sudo apt-get install build-essential
//ensures you have compilers installed
~$ sudo alien fglrx_6_8_0-8.12.10-1.i386.rpm
//wherever you downloaded your linux driver,converts the rpm to a deb package
~$ sudo cp /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so.1.2.backup
~$ sudo rm /usr/X11R6/lib/libGL.so.1.2
//makes a backup and deletes original, cause will be installing different version
//the force overwrite below doesnt seem to always work for the above file
~$ sudo dpkg -i --force-overwrite fglrx-6-8-0_8.12.10-2_i386.deb
~$ sudo mv /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko $HOME
//change this to whatever kernel you use, dont know why you have to do this
~$ cd /lib/modules/fglrx/build_mod/
~$ sudo chmod 777 make.sh 
~$ sudo ./make.sh 
~$ cd ..
~$ sudo chmod 777 make_install.sh
~$ sudo ./make_install.sh
~$ sudo dpkg-divert --package fglrx --add /usr/X11R6/lib/libGL.so.1.2
//dont know why ya have to do this either, but saw it as reccommended, but dont //know what it does
~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
//backup your /etc/X11/xorg.conf file


--------modify your xorg.conf----------
1. Run fglrxconfig from terminal as a normal user in your home folder, this will save
xorg.conf in your home folder. (em dont mind people saying do not run this, it has been improved in the latest drivers, and wasnt that scary in the previous drivers, just annoying, but make sure you backup your original xorg.conf before running this)
2. Default all the options in fglrxconfig, or change as you need
3. After running xorgconfig comment out the section like below in your /etc/X11/xorg.conf



#Section "Device"
#	Identifier	"ATI Technologies, Inc. Radeon Mobility 9800 (M18 JN)"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection



4. Add the section shown below from your xorg.conf in your home folder to /etc/X11/xorg.conf



Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
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
    Option "UseFastTLS"                 "1"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
#    BusID "PCI:1:0:0"    # no device found at config time
    Screen 0
EndSection


5. Change the line
Identifier                          "ATI Graphics Adapter"
to
Identifier	"ATI Technologies, Inc. Radeon Mobility 9800 (M18 JN)" 
or whatever your adapter is named
6.Save your /etc/X11/xorg.conf file.


---------------finished editing xorg.conf--------------------------

-Ctrl alt f2
-login
~$ sudo killall gdm
~$ startx

-bring up a terminal
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9800 Generic
OpenGL version string: 1.3.5010 (X4.3.0-8.12.10)

~$ glxgears
18581 frames in 5.0 seconds = 3716.200 FPS
38866 frames in 5.0 seconds = 7773.200 FPS

~$ fgl_glxgears
3700 frames in 5.0 seconds = 740.000 FPS
4312 frames in 5.0 seconds = 862.400 FPS
4417 frames in 5.0 seconds = 883.400 FPS
4465 frames in 5.0 seconds = 893.000 FPS


Runs ut2004 very smoothly at highest settings and resolution 1680x1050

---

### Post by jtwadsworth on 2005-05-29
I did all this and the kernel is the correct version.  Xorg.0.log says all is well but I still get a black screen when X starts!  This is killing me I have reinstalled now about 15 times.

jtw

---

### Post by clb137 on 2005-05-29
[QUOTE=jtwadsworth]I did all this and the kernel is the correct version.  Xorg.0.log says all is well but I still get a black screen when X starts!  This is killing me I have reinstalled now about 15 times.

jtw[/QUOTE]


Sorry to hear this,  the only thing different i have done is manually move the old fglrx.ko to my home drive (mv /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko) every thing else as the guide states restarted and it works no more messa its ATI


good luck 

clinton

---

### Post by jtwadsworth on 2005-05-29
I have tried yet again.  All is well with installation and according to the log but X still yields a black screen.  I guess I am doomed until Breezy comes out or I buy another vidcard.

jtw

---

### Post by Serus on 2005-05-30
I'm getting an error when I try to do the sudo sh make.sh. This happends regardless if I try the move option on page 3 of this post or not. Here's what I'm getting:

```
:/lib/modules/fglrx/build_mod$ sudo sh make.sh
make.sh: line 46: gcc: command not found
make.sh: line 52: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
ln: `./libfglrx_ip.a.GCC': File exists
make: *** [libfglrx_ip.a.GCC] Error 1
build failed with return value 2
``` 

Any ideas would be helpful.

I'm using an ATI x850xt AGP 256MB card on a P4 3.0 with a 19" sony LCD. not sure if any of that is relavent or not. I've been trying to get this going for a few days no with no success. I've attempted several of the tutorials I've found (I think 4 so far) with no success.

---

### Post by jerrybme on 2005-05-31
[QUOTE=Serus]

```

/bin/sh: gcc: command not found
/bin/sh: gcc: command not found

``` 
[/QUOTE]

You need to install the GNU C compiler "gcc" Do a search in Synaptic & you'll find it.
Cheers,
Jerry

---

### Post by hasenkamp on 2005-05-31
sorry I'm extremely newbie...

I got the message below:

$sudo sh make.sh
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h

What can I do?

Thanks.

---

### Post by poofyhairguy on 2005-05-31
[QUOTE=Serus]
Any ideas would be helpful.
[/QUOTE]

DO this in terminal:

sudo apt-get install build-essential

---

### Post by Serus on 2005-06-01
Awsome, I got past the "sudo sh make.sh" without any errors.

However, when I got to do the "sudo sh make_install.sh" I get the following information/errors:

```
- creating symlink
-recreating module dependency list
-trying a sample load of the kernel module
[fglrx:firegl_init] *ERROR Device not found!
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/char/drm/fglrx.ko): No such device
failed.
``` 


I've been following this how-to to the T.  This is off of a fresh Ubuntu install with the latest version. I have done the update of linux-restricted-modules, build-essential, the xorg-driver-fglrx, and the drivers from the ATI site.

I read somewhere that the above error means that the video card isn't supported, but I was also told that the X850XT *is* supported by the ATI drivers. 

Not sure where to go from here..Thanks again for the help!

---

### Post by poofyhairguy on 2005-06-01
[QUOTE=Serus]Awsome, I got past the "sudo sh make.sh" without any errors.

However, when I got to do the "sudo sh make_install.sh" I get the following information/errors:

```
- creating symlink
-recreating module dependency list
-trying a sample load of the kernel module
[fglrx:firegl_init] *ERROR Device not found!
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/char/drm/fglrx.ko): No such device
failed.
``` 


I've been following this how-to to the T.  This is off of a fresh Ubuntu install with the latest version. I have done the update of linux-restricted-modules, build-essential, the xorg-driver-fglrx, and the drivers from the ATI site.

I read somewhere that the above error means that the video card isn't supported, but I was also told that the X850XT *is* supported by the ATI drivers. 

Not sure where to go from here..Thanks again for the help![/QUOTE]


try this:

sudo modprobe fglrx

---

### Post by Serus on 2005-06-01
I get the same error when I "sudo modprobe fglrx"

```
[fglrx:firegl_init] *ERROR Device not found!
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/char/drm/fglrx.ko): No such device
``` 

When I reboot I get a crash because of the "fglrx" line in the xorg.conf, the one that replaced "ati"

---

### Post by Janne on 2005-06-02
This is the 3rd day im trying to get these ATI drivers installed. This how-to was looking good until the 6th step. Now this is what happens. Anybody got an idea? Im getting a bit desperate as I'd like to be playing UT2004 already :(

```
janne@ruoska:~ $ cd /lib/modules/fglrx/build_mod/
janne@ruoska:/lib/modules/fglrx/build_mod $ sudo sh make.sh
make.sh: line 46: gcc: command not found
make.sh: line 52: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
```

Im a total *nix newbie also, been using this for about 4 days now. If it's any help here is my *glxinfo* also.

```
janne@ruoska:~ $ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
janne@ruoska:~ $
```

---

### Post by nehalem on 2005-06-02
I'm getting the same problem with the same results...

Anyone have anymore ideas?

---

### Post by Jesus Franco on 2005-06-02
Please install your linux headers and build-essential
I dont get the errors some people get. I never get them. I've installed them 3 times. On 3 different computers and never have I got a problem.  :| 

If all else fails use the package in the repositories, its better than nothing.

---

### Post by clb137 on 2005-06-02
Hi, ALL

I Have tried to get the latest drivers working and I did manage to get them going,  however i have tried that many different ways in the end I am not too sure what actually finally dd the trick.

Then after a few days it all crashed, so i started with a fresh install and this time i followed the instruction in this link [http://ubuntulinux.org/wiki/BinaryDriverHowto](http://ubuntulinux.org/wiki/BinaryDriverHowto)  and presto 3d working in less than 1 min,  the glxgears out was just the same,  so what I am saying is;   Is all the effort and pain worth the end result, when you can use the packages in the repos???????

Any comment are more than welcome as We Are ALL still learning

thanks

clinton bennett

---

### Post by clb137 on 2005-06-02
By the way that is ;glxgears output; sorry for the spelling, or at least checking it before i posted it ,,    and yes dd means did 

thanks

clinton

---

### Post by nehalem on 2005-06-02
[QUOTE=Serus]I get the same error when I "sudo modprobe fglrx"

```
[fglrx:firegl_init] *ERROR Device not found!
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/char/drm/fglrx.ko): No such device
``` 

When I reboot I get a crash because of the "fglrx" line in the xorg.conf, the one that replaced "ati"[/QUOTE]

Oops, meant to say I'm getting this same problem.  For the record I have verified that I have build essentials and the restricted modules and headers (vmware required this and i have that installed) for my kernel version.

In my case I have used the fglrx in the repository in the past with great success.  I just reinstalled hoary and this time, for whatever reason, X keeps locking up.  I thought it would be a nice chance to upgrade the to latest.

I have a laptop w/ the 9200 radeon mobility.  I'm not sure if this is officially supported but the repository version just used teh 9000 mobility stuff for it.

---

### Post by Serus on 2005-06-04
I guess nobody has any ideas for the above fatal error?

---

### Post by Alex[RM-UK] on 2005-06-05
Wow, Thank you VERY much it all works very well. In addition to your guide, I also downloaded the ATI Control Center by doing this:

```
sudo apt-get install fglrx-control
```

Then restarted X, and now I have the control panel for it. But one question about it - How do I edit my OpenGL settings? To adjust AA, AF etc? 

Thank!

---

### Post by Curlydave on 2005-06-05
[QUOTE='Alex[RM-UK]']Wow, Thank you VERY much it all works very well. In addition to your guide, I also downloaded the ATI Control Center by doing this:

```
sudo apt-get install fglrx-control
```

Then restarted X, and now I have the control panel for it. But one question about it - How do I edit my OpenGL settings? To adjust AA, AF etc? 

Thank![/QUOTE]

I've posted several threads asking about this and have been trying to figure this out on IRC for some time... No answer.

---

### Post by Curlydave on 2005-06-05
> E: Couldn't find package linux-restricted-modules

On the first step. And I've done everything to find the restricted modules. I've got them. I've ran commands that dled them. In fact, I dled them for just about every kernel version, but it still says that I don't have them.

PS: do these drivers improve the abysmal performance over the packaged ones?

---

### Post by simianMiscreant on 2005-06-05
I lost hardware acceleration when I upgraded the driver, so I'd like to downgrade to the one in the Hoary repository. Can someone tell me how to do this?

---

### Post by clb137 on 2005-06-05
[QUOTE=atze]Hi
I have finde out how to resolve the problem:

check this url:

[http://ubuntuforums.org/archive/index.php/t-24763.html](http://ubuntuforums.org/archive/index.php/t-24763.html)

**6. sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME** and it works  :grin:[/QUOTE

Hi It says it works but it does NOT move the file, the only way I could get it to work was move the file manually,

then my machine locked up, so it went back to the dirver in the repositrys and it workd a treat even full 3d,
not sure what the deal is


clinton

---

### Post by bastya_elvtars on 2005-06-06
Did exactly as you specified, also tried the binary drivers' site, the debian howto and apt-getting the xorg-driver (as specified in the wiki). Still there are these MESA extensions and make me go mad because I cannot play tuxracer. :P

(ATI Radeon 9200 SE)

The distro is nice and fast on the other hand, I love it.

-- // edit

It also complains of incompatible kernel module. Maybe my installed kernel source is wrong? Sorry but I am even more linux-nobish when it comes to peripherals.   ](*,)

---

### Post by Merc248 on 2005-06-06
Has anyone gotten XVideo/YUY2 to work fine with these drivers?  I can't get it to work at all with tvtime at least:

> Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/merc248/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

It worked fine with the 8.8.25 drivers in the Ubuntu repositories. :x

---

### Post by clb137 on 2005-06-06
[QUOTE=bastya_elvtars]Did exactly as you specified, also tried the binary drivers' site, the debian howto and apt-getting the xorg-driver (as specified in the wiki). Still there are these MESA extensions and make me go mad because I cannot play tuxracer. :P

(ATI Radeon 9200 SE)

The distro is nice and fast on the other hand, I love it.

-- // edit

It also complains of incompatible kernel module. Maybe my installed kernel source is wrong? Sorry but I am even more linux-nobish when it comes to peripherals.   ](*,)[/QUOTE]


Hi there
WHich one did you try???????

did you un-install all before starting??
have you edited your sources.list to make it up to date with all the repositories???

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

have fun

clinton

---

### Post by bastya_elvtars on 2005-06-06
[QUOTE=clb137]Hi there
WHich one did you try???????

did you un-install all before starting??
have you edited your sources.list to make it up to date with all the repositories???

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

have fun

clinton[/QUOTE]

 Yeah, upgraded. Tried the latest rpm's conversion to deb, the xorg-driver fglrx, and also [this site](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html).

I edited the source list according to that howto, that was my very first step. And yes, I uninstalled all previous drivers.

---

### Post by Jesus Franco on 2005-06-06
I've been reading up on these drivers in other forums aswell. And they are having problems with the newest Xorg and the 2.6.11 and 2.6.12 kernels. Make sure you are yousing Hoary and are using the 2.6.10-5 kernel in the repository. I dont know why these drivers are having problems with the newest versions but they are.

As for the x11 and xv video overlays. They dont seem to work well if at all in these drivers. Make sure you configure every application that uses them to use gl instead. Or it its avaliable gl2 for better quality.  :razz: 

Lets wait for Breezy to fix some problems or for the new drivers that are rumored to come out soon.  :grin:

---

### Post by bastya_elvtars on 2005-06-07
```
Linux version 2.6.10-5-686-smp (buildd@rothera) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 SMP Fri May 20 15:10:39 UTC
2005
```

(Runing on a P4 3000).

What I wanted to ask: I installed the 2.6.10 kernel's source, should I install linux-patch-ubuntu-2.6.10 too and only build my modules afterwards?

---

### Post by vannguyen0 on 2005-06-09
ATI just release Linux x86 Drivers for XFree86 / X.Org Version 8.14.13 today.  Has anyone tried it???  I've yet to get version 8.12 to work with my IBM ThinkPad T43 w/ a Mobility X300 card.  I'm going to go home and give it a shot tonight!!

---

### Post by Jesus Franco on 2005-06-09
I'll be installing the newest drivers. I'll post a howto when Im done. If it works.

I'll be using the installer  :smile:

---

### Post by Jesus Franco on 2005-06-09
Updated the how to! It works! And these drivers are ALOT better. Screensavers dont use as much memory. Racer is smoother and so is quake3  :-P

---

### Post by Serus on 2005-06-09
In the release notes for the new drivers it says they added support for x850xt cards. Might have been my problem all along.

I just attempted to install it with the installer with no success. Maybe it's cause I've messed around too much and need to do a reinstall. 

During the install, it said I have glibc v2.1, and in the readme it says that version 2.2 or 2.3 is required. Not sure how to update glibc to a newer version.

When I "sudo modprobe fglrx" I get the same error:

```
[fglrx:firegl_init] *ERROR* Device not found!
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/char/drm/fglrx.ko): No such device
``` 

Might be time for me to just give up and format for Windows again..UGH!

---

### Post by Jesus Franco on 2005-06-09
These drivers allow for on the fly resolution changes in the kde control panel. Dont know if it works in the gnome display properties since I dont use gnome anymore.  [-X

---

### Post by TheStyle on 2005-06-09
Ok, total linux noob here. So I followed the instructions in the OP on my clean install of HH 5.04 (for amd64). 

I haven't encountered any sort of error messages, but I have gone from only being able to get 7 or so FPS out of any kind full screen 3D, to not being able to display 3d at all.

Before when I would test one of the 3D screen savers, I would get 5 to 10(max) FPS. Now I just get a blank screen.

Any help on fixing this would be great.

Thanks.

PS: I have a AIW 9800 pro

[edit: Oh yeah, and the ATI icon in my applications menu doesn't seem to do any thing when I click on it]

---

### Post by nehalem on 2005-06-10
Trying to install the new driver but no success.  In the log file it reads this:

> [Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
In file included from /lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:125:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:56:48: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:57:6: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:58:41: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:508: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:510: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:530: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:577)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:561: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2647: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_uninit':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3185: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.

I'm still pretty new at this so I don't really understand what's going on enough to troubleshoot most things.  Any help is appreciated.

---

### Post by vannguyen0 on 2005-06-10
I've installed the latest version ATI put out today.  I'm actually able to boot into KDE this time, but I get horrible fps in glxgears.  I checked my /var/log/Xorg.0.log and found this:

(II) fglrx(0): [drm] loaded kernel module for "fglrx" driver
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8c1d000
(II) fglrx(0): [drm] mapped SAREA 0xf8c1d000 to 0xb7d7d000
(II) fglrx(0): [drm] framebuffer handle = 0xc0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8c1d000 at 0xb7d7d000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x03ff0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1408,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1408,1050) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 1050)
(II) fglrx(0): Largest offscreen area available: 1408 x 7138
(**) Option "dpms"
(**) fglrx(0): DPMS enabled


this is the part that concerned me most:
[B](WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work[/B]

I'm using:
Linux 2.6.10-5-686 

and downloaded the appropriate headers.  Any idea why I'm getting this error??  I used the ATI installer.

---

### Post by Jesus Franco on 2005-06-10
For those that seem to get a good install but cant load the moduels. Do the following.

***NOTE: Where you see 2.6.10-5-686 replace it with your running kernel. If you do not know run "uname -r" without quotes from the command line. ***
```

cd /lib/modules/fglrx
sudo sudo cp fglrx.ko /lib/modules/2.6.10-5-686/
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/
sudo mkdir /lib/modules/2.6.10-5-686/kernel/video
sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/video
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/video
sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/drivers/video
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/drivers/video
sudo mkdir /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx
sudo sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx
sudo mkdir /lib/modules/2.6.10-5-686/kernel/drivers/misc
sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc
sudo mkdir /lib/modules/2.6.10-5-686/kernel/drivers/misc/video
sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc/video
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc/video
sudo mkdir /lib/modules/2.6.10-5-686/kernel/drivers/misc/fglrx
sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc/fglrx
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc/fglrx

```

Alternativealy you can simply do the following
For Gnome
```
 sudo nautilus
```

For KDE
```
 sudo konqueror 
```

And you can make the dictories and copy the files manually and graphically (might be easier for n00bs.)


It seems for some bizarre reasons. Different applications and different systems in general search for the driver in different locations. Doing the above will make sure no matter were it looks. The driver will be there for it!  :grin:

---

### Post by vannguyen0 on 2005-06-10
[QUOTE=Jesus Franco]For those that seem to get a good install but cant load the moduels. Do the following.

***NOTE: Where you see 2.6.10-5-686 replace it with your running kernel. If you do not know run "uname -r" without quotes from the command line. ***
```

cd /lib/modules/fglrx
sudo sudo cp fglrx.ko /lib/modules/2.6.10-5-686/
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/
sudo mkdir /lib/modules/2.6.10-5-686/kernel/video
sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/video
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/video
sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/drivers/video
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/drivers/video
sudo mkdir /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx
sudo sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx
sudo mkdir /lib/modules/2.6.10-5-686/kernel/drivers/misc
sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc
sudo mkdir /lib/modules/2.6.10-5-686/kernel/drivers/misc/video
sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc/video
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc/video
sudo mkdir /lib/modules/2.6.10-5-686/kernel/drivers/misc/fglrx
sudo cp fglrx.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc/fglrx
sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/drivers/misc/fglrx

```[/QUOTE]


ok.  that did the trick.  i checked the Xorg.0.log and found that acceleration is enabled.  but X does not start.  i only get a black screen.  i checked ATI's readme and found this:

```

X Fails to Load on Systems with Linux Kernel Version 2.6.x

This information applies to the following system configurations:

    * Linux kernel version 2.6.x
    * Any ATI Linux driver 

A blank screen may appear momentarily when X starts to load. The following error message (or similar) may appear on the text console or in /var/log/XFree86.0.log:
(EE) fglrx(0): [agp] unable to acquire AGP, error ""xf86_ENODEV""xf86_ENODEV""

This is not a problem with the display driver.

Version 2.6 kernels require a second kernel module in addition to agpgart, which should be named similar to the manufacturer of your motherboard AGP chipset. This error message should occur if the other agp module is not loaded.

This issue can be worked around as follows:

   1. First make sure that agpgart is loading properly.
   2. To find out which AGP controller your motherboard uses, issue the following command: lspci | grep AGP
   3. To find a list of AGP related kernel modules installed on your machine, issue the following command and look for a module (*.ko file) that suits your AGP Controller: ls /lib/modules/`uname -r`/kernel/drivers/char/agp
   4. Use the modprobe command (as root) to load the module. For example: On a motherboard using a VIA® AGP Controller, you would load the via-agp.ko using modprobe as follows (notice that the trailing .ko is omitted): modprobe via-agp

Check the modprobe manpage for more information on loading kernel modules.

   5. To verify that the AGP module is already loaded, run lsmod as root. With the X server running and the connection established, the usage count of this module must be greater than zero. 

If you cannot find a suitable agp module for your motherboard, then you may want to upgrade to the latest version of the Linux kernel, or check your motherboard manufacturer's website for more information.

```

Although I did not see an error message similar to (EE) fglrx(0): [agp]....  I did an lsmod and found that I'm running:

agpgart and intel_agp


Anyone else having problems w/ ATI Mobility X300?

---

### Post by bastya_elvtars on 2005-06-10
I used the installer. It is slow as hell. And:

[IMG]http://160.114.118.82/hmm.jpg[/IMG]

---

### Post by skylark on 2005-06-10
Hi everyone,

I'm a new Ubuntu user - just installed the Hoary AMD64 varient on my new machine. 

I followed the suggestions in this thread (I stumbled into most problems people encountered), but even though X seems to load fine and DRI seems to be enabled I keep getting this:
$ glxinfo
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

I cant get any openGL stuff working.

Any suggestions?  ](*,)

---

### Post by Serus on 2005-06-10
I tried the above copying method, but I still get the same fatal error unable to locate device thing...Not sure what the hell is goin on, but this is the exact reason why linux isn't mainstream. I've spent I don't know how much time on this, just to see if games run better under linux than windows, and I can't even get as far as linux knowing what video card I've got. I give up, time to go back to windows..

---

### Post by dlpfmVfH on 2005-06-10
tried the installer, it says it installs everything ok, I got the control panel but no module...

looked in /lib/modules/fglrx...and it's empty...

tried the build_mod map,....couldn't run sudo sh make.sh....gives an error:
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
Makefile:50: *** gemengde implicite en normale regels.  Stop.
build failed with return value 2

so something is wrong...

running Linux ubuntu 2.6.11-1-k7 #1 Fri Feb 11 14:16:27 UTC 2005 i686 GNU/Linux

the new driver should work with the 2.6.11

so what am I doing wrong??

---

### Post by Jesus Franco on 2005-06-10
[QUOTE=bastya_elvtars]I used the installer. It is slow as hell. And[/QUOTE]

Do Follow these insturctions 
[HERE](http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87) 
That should help.

**-----------------------------------------------------------------------------------------------**

[QUOTE=skylark]Hi everyone,
$ glxinfo
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
[/QUOTE]

Do this.
```

cd /usr/X11R6/lib
sudo ln -s libGL.so.1.2 libGL.so.1
sudo ln -s libGL.so.1.2 libGL.so

```
That should fix everything for you.

**--------------------------------------------------------------------------------------------**

[QUOTE=aboe]tried the installer, it says it installs everything ok, I got the control panel but no module...

looked in /lib/modules/fglrx...and it's empty...

tried the build_mod map,....couldn't run sudo sh make.sh....gives an error:
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
Makefile:50: *** gemengde implicite en normale regels.  Stop.
build failed with return value 2

so something is wrong...

running Linux ubuntu 2.6.11-1-k7 #1 Fri Feb 11 14:16:27 UTC 2005 i686 GNU/Linux

the new driver should work with the 2.6.11

so what am I doing wrong??[/QUOTE]

It seems you are missing either your kernel headers. Make sure they are the right ones. Or build-essential.

Hope that helps you guys out.  :grin:

---

### Post by dlpfmVfH on 2005-06-11
did install the headers and the source of the kernel 2.6.11-1-k7 and also for the 2.6.10-5-k7

could it be gcc related??

---

### Post by Antipop on 2005-06-11
OK, now I'm starting to get really fed up with ati+linux -combination. I've had this same problem all the way from the beginning and have had no help from any HowTo's whatsoever. Installing and configurating goes always as planned but when it comes to starting X, the same problem always occurs when the driver is determined "fglrx". If I put "ati" or "radeon" instead of "fglrx" I can get the X to start but without any hope of 3D acceleration. Check the log below and my xorg.conf below that and please help if you can, thank you.

```

X Window System Version 6.8.2 (Ubuntu (static) 6.8.2-10 20050405154308 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux HELLHOLE 2.6.10-5-386 #1 Tue Jun 7 08:26:42 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
OS Kernel: Linux version 2.6.10-5-386 (buildd@rothera) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Jun 7 08:26:42 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 11 11:11:54 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Server Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "ATI Graphics Adapter"
(**) |-->Input Device "Mouse1"
(**) |-->Input Device "Keyboard1"
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xfree86"
(**) XKB: rules: "xfree86"
(**) Option "XkbModel" "pc101"
(**) XKB: model: "pc101"
(**) Option "XkbLayout" "fi"
(**) XKB: layout: "fi"
(==) Keyboard: CustomKeycode disabled
(**) FontPath set to "/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/75dpi/:unscaled,/usr/X11R6/lib/X11/fonts/100dpi/:unscaled,/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/"
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(**) Extension "Composite" is enabled
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1043,80ac rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 1043,80ac rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 1043,80ac rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 1043,80ac rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 1043,80ac rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,0c11 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,0c11 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,0c11 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0c:0: chip 10de,006d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,006e card 1043,809a rev a3 class 0c,00,10 hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 01:07:0: chip 1102,0004 card 1102,1002 rev 04 class 04,01,00 hdr 80
(II) PCI: 01:07:1: chip 1102,7003 card 1102,0060 rev 04 class 09,80,00 hdr 80
(II) PCI: 01:07:2: chip 1102,4001 card 1102,0010 rev 04 class 0c,00,10 hdr 80
(II) PCI: 01:0b:0: chip 1095,3112 card 1095,6112 rev 01 class 01,04,00 hdr 00
(II) PCI: 02:01:0: chip 10b7,9201 card 1043,80ab rev 40 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 1002,4e44 card 1002,0002 rev 00 class 03,00,00 hdr 80
(II) PCI: 03:00:1: chip 1002,4e64 card 1002,0003 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000bfff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:12:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe1ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xe2000000 - 0xe3ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(--) PCI:*(3:0:0) ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro] rev 0, Mem @ 0xd0000000/27, 0xe3000000/16, I/O @ 0xd000/8
(--) PCI: (3:0:1) ATI Technologies Inc Radeon R300 [Radeon 9700 Pro] (Secondary) rev 0, Mem @ 0xd8000000/27, 0xe3010000/16

----------------------------------------------------------------------------------

(II) VESA: driver for VESA chipsets: vesa
(II) VGA: Generic VGA driver (version 4.0) for chipsets: generic
(II) DUMMY: Driver for Dummy chipsets: dummy
(II) FBDEV: driver for framebuffer: fbdev, afb
(II) v4l driver for Video4Linux
(II) Primary Device is: PCI 03:00:0
(EE) No devices detected.

Fatal server error:
no screens found

```


```


Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection


Section "Files"

    RgbPath	"/usr/X11R6/lib/X11/rgb"

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection


Section "ServerFlags"

#    Option "NoTrapSignals"

#    Option "DontZap"

#    Option "Dont Zoom"

#    Option "DisableVidModeExtension"

#    Option "AllowNonLocalXvidtune"

#    Option "DisableModInDev"

#    Option "AllowNonLocalModInDev"

EndSection

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"Keyboard"

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

#    Option "XkbModel"   "pc102"

#    Option "XkbModel"   "microsoft"
#

#    Option "XkbLayout"  "de"

#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
#    Option "XkbOptions" "ctrl:swapcaps"

#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc101"
    Option "XkbLayout"	"fi"

EndSection

Section "InputDevice"

# Identifier and driver

        Identifier "Mouse1"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "IMPS/2"
        Option "Buttons" "5"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "100"
	Option "SendCoreEvents" "true"


#    Option "Protocol"   "Xqueue"


#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

#    Option "Emulate3Buttons"	 "no"
#    Option "Emulate3Timeout"    "50"

#    Option "ChordMiddle"

EndSection



# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5 - 91.1
    VertRefresh 60 - 85
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"


    Chipset     "4146"
    Driver      "vga"

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
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
    Option "backingstore" 		"true"
    Option "UseInternalAGPGART"		"no"
    Option "ForceGenericCPU"            "no"
    BusID                               "PCI:3:0:0"
#    vendor=1002 
#    device=4146
    Screen 0
EndSection

Section "Extensions"
    Option "Composite"			"On"
EndSection 

Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

    Screen "Screen0"

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

Section "DRI"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

### EOF ###

```

---

### Post by AlvaroBF on 2005-06-11
Hello,

I installed the ati drivers a lot of times.

```
alvaro@ubuntu:~$ sudo sh ati-driver-installer-8.14.13.run
``` 

Ok, done

I open the ATI Control Panel and

```
Driver does not provide the FireGL X11 Extensions!
Panel Component will operate only partially
``` 

>_< I only see Information and TV out.

and in /lib/modules/fglrx

```
alvaro@ubuntu:/lib/modules/fglrx$ ls
build_mod  make_install.sh
alvaro@ubuntu:/lib/modules/fglrx$
``` 

```
alvaro@ubuntu:/lib/modules/fglrx$ sudo sh make_install.sh
*** WARNING ***
Tailored kernel module for fglrx not present in your system.
You must go to /lib/modules/fglrx/build_mod subdir
and execute './make.sh' to build a fully customed kernel module.
Afterwards go to /lib/modules/fglrx and run './make_install.sh'
in order to install the module into your kernel's module repository.
(see readme.txt for more details.)

As of now you can still run your XServer in 2D, but hardware acclerated
OpenGL will not work and 2D graphics will lack performance.

failed.
alvaro@ubuntu:/lib/modules/fglrx$
``` 

```
alvaro@ubuntu:/lib/modules/fglrx/build_mod$ sudo sh make.sh
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
alvaro@ubuntu:/lib/modules/fglrx/build_mod$
``` 


:( :(

What can I do?? :(

---

### Post by lindt on 2005-06-11
[QUOTE=aboe]tried the installer, it says it installs everything ok, I got the control panel but no module...

looked in /lib/modules/fglrx...and it's empty...

tried the build_mod map,....couldn't run sudo sh make.sh....gives an error:
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
Makefile:50: *** gemengde implicite en normale regels.  Stop.
build failed with return value 2

so something is wrong...

running Linux ubuntu 2.6.11-1-k7 #1 Fri Feb 11 14:16:27 UTC 2005 i686 GNU/Linux

the new driver should work with the 2.6.11

so what am I doing wrong??[/QUOTE]


I've the same problem with 2.6.10-5-k7 kernel; headers, source and build-essential are installed.

I can't see any solution  ](*,)

---

### Post by Jesus Franco on 2005-06-11
[QUOTE=Antipop]OK, now I'm starting to get really fed up with ati+linux -combination. I've had this same problem all the way from the beginning and have had no help from any HowTo's whatsoever. Installing and configurating goes always as planned but when it comes to starting X, the same problem always occurs when the driver is determined "fglrx". If I put "ati" or "radeon" instead of "fglrx" I can get the X to start but without any hope of 3D acceleration. Check the log below and my xorg.conf below that and please help if you can, thank you.
[/QUOTE]

Remove the compositing line...
And remove this line       
```
 Option    "omit xfree86-dga"   # don't initialise the DGA extension 
```
These drivers dont require that line to be stated.

**==========================================**

And in this tutorial I stated to use the automatic installation. It seems AlvaroBF that you didnt do this. Why are you trying to build your kernel module?

---

### Post by kleeman on 2005-06-11
Perhaps this has been mentioned above BUT
I had problems with the Howto here because the ati installer did not replace the old kernel driver installed in the restricted modules package.
I had to install the fglrx module manually i.e.

cd /lib/modules/fglrx

sudo cp fglrx.2.6.10-5-686.ko /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko

(Note I am using 2.6.10-5-686 kernel so you need to change this apprpriately above).

Without this fix the old version of the kernel module fglrx.ko was being loaded and the violation with the other stuff that the ati installer had created caused 3d acceleration to fail. Hope this helps someone.......

---

### Post by rugmonster on 2005-06-12
Has anyone figured out how to get the module to load when receiving this error?

FATAL: Error inserting fglrx (/lib/modules/2.6.11-1-amd64-k8/kernel/drivers/char/drm/fglrx.ko): No such device

I tried last night and again this morning. I see that the module is installed there, I have build-essentials and the kernel headers installed. It appears to build fine (with the exception of the following:

Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3

Otherwise, I've tried copying the module file to the alternate locations, run depmod -a and still get the "No such device" error. I've got a Sapphire 9800XT. Here is the output from lspci.

0000:01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary)

---

### Post by mulperi on 2005-06-12
This works, thanks alot for this Howto! I created a profile just to thank you  :smile:

The important part IMHO is that you need to install kernel headers (use Synaptic) and kernel sources:
[http://www.ubuntulinux.org/wiki/KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowto)

Even with the sources I got some warning messages in /usr/share/fglrx/fglrx-install.log

In my /etc/modules I load via82cxxx and in /etc/X11/xorg.conf I do not use the internal AGP, just as Jesus Franco suggests.

Also you really need to copy the .ko files in several "strange" locations, just as Jesus Franco suggests:
[http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87](http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87)

Boot and voila, ATI control panel says RADEON and not MESA!

//Mulperi

---

### Post by skylark on 2005-06-12
I finally managed to get these drivers installed with no major issues. I followed asmodeas's recipe to get everything to work for me.

I wrote a script which I believe automates the process (I've tested it on my box, but not yet from a fresh install). The script automates everything except the editing of xorg.conf.

To run it, copy and paste it into a file called "ati_install.sh" and then run:
sudo sh ati_install.sh

Hope it helps someone.

PS: Hopefully someone will create a 8.14.13 binary driver package for Ubuntu soon so we don't have to go through this sort of hassle?!

```
#!/bin/sh
# Automated install of ATI Linux Drivers (8.14.13) for X.Org 6.8
# script created 13 June 2005
AMD64_FILE='http://www2.ati.com/drivers/linux/64bit/fglrx64_6_8_0-8.14.13-1.x86_64.rpm'
I386_FILE='http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.14.13-1.i386.rpm'

RED_ON='\033[0;31m'
RED_OFF='\033[0m'

# determine kernel version and infer package name of kernel headers
KERN_VER="$(uname -r)"
HEADERS="linux-headers-$KERN_VER"
# determine architecture of system
ARCH=''
WEBLOC=''
FILE=''
AMD64_FLAG="$(echo "$KERN_VER" | grep -i amd64 | wc -l)"
I386_FLAG="$(echo "$KERN_VER" | grep -i i386 | wc -l)"
if [ "$AMD64_FLAG" = "1" ]; then
  ARCH='AMD64'
  WEBLOC="$AMD64_FILE"
elif [ "$I386_FLAG" = "1" ]; then
  ARCH='I386'
  WEBLOC="$I386_FILE"
else
  echo -e "$RED_ON Unable to determine a compatible system architecture"
  echo -e "The ATI Linux drivers only support AMD64 or X86 I386 $RED_OFF"
  exit 0;
fi
FILE="$(echo "$WEBLOC" | sed s/.*fgl\/fgl/)"

echo 
echo
echo -e "$RED_ON ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^"
echo -e 'Attempting to install ATI Linux Drivers 8.14.13 on this system...'
echo -e "Your system is running the $KERN_VER linux kernel"
echo -e "System architecture is $ARCH"
echo -e 'Please abort this install if the above information is incorrect'
echo -e
echo -e 'Note: this install does not support mobile ATI graphics or the FireGL range'
echo -e ' ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^'
echo -e " -----> Do you want to proceed (Y/N)? $RED_OFF"

read answer
if [ "$answer" != "Y" -a "$answer" != "y" ]; then
  exit 0;
fi

# Download the relevant drivers from the ATI web site:
echo
echo -e "$RED_ON Downloading drivers, please wait. $RED_OFF"
mkdir -p /tmp/ati_graphics
cd /tmp/ati_graphics
wget "$WEBLOC"
if [ ! -r "$FILE" ]; then
  echo -e "$RED_ON Error downloading $WEBLOC"
  echo -e "Aborting install! $RED_OFF"
  cd $HOME
  exit 0;
fi

# Ensure required packages are installed
echo -e "$RED_ON Ensuring Ubuntu packages build-essential and $HEADERS are installed... $RED_OFF"
apt-get install build-essential "$HEADERS"

# Convert rpm to deb package
echo
echo -e "$RED_ON Converting $FILE to a deb package. This can take up to a few mintues, please be patient... $RED_OFF"
DEB_PKG="$(alien $FILE | tail -1 | sed s/\ generat.*//)"

# Backup OpenGL shared library
TSTAMP="$(date +%Y%m%d_%T)"
mv -f /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so.1.2.backup_$TSTAMP
echo
echo -e "$RED_ON libGL.so.1.2 has been backed up to /usr/X11R6/lib/libGL.so.1.2.backup_$TSTAMP $RED_OFF"
echo

# Install deb
echo -e "$RED_ON Installing $DEB_PKG ... $RED_OFF"
dpkg -i --force-overwrite $DEB_PKG

# not sure if this is needed...
mv /lib/modules/$KERN_VER/kernel/drivers/video/fglrx.ko $HOME

cd /lib/modules/fglrx/build_mod/
chmod +x make.sh
./make.sh
cd ..
chmod +x make_install.sh
./make_install.sh

#Note sure about the need for a dpkg-divert, commented out for now:
#dpkg-divert --package fglrx --add /usr/X11R6/lib/libGL.so.1.2

# Setup module symlinks to cover all possibilities
cd /lib/modules/$KERN_VER/
rm -f fglrx.$KERN_VER.ko 
rm -f fglrx.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.$KERN_VER.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.ko
mkdir -p /lib/modules/$KERN_VER/kernel/video
cd /lib/modules/$KERN_VER/kernel/video
rm -f fglrx.$KERN_VER.ko 
rm -f fglrx.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.$KERN_VER.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.ko
mkdir -p /lib/modules/$KERN_VER/kernel/drivers/video/fglrx
cd /lib/modules/$KERN_VER/kernel/drivers/video/fglrx
rm -f fglrx.$KERN_VER.ko 
rm -f fglrx.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.$KERN_VER.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.ko
mkdir -p /lib/modules/$KERN_VER/kernel/drivers/misc
cd /lib/modules/$KERN_VER/kernel/drivers/misc
rm -f fglrx.$KERN_VER.ko 
rm -f fglrx.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.$KERN_VER.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.ko
mkdir -p /lib/modules/$KERN_VER/kernel/drivers/misc/video
cd /lib/modules/$KERN_VER/kernel/drivers/misc/video
rm -f fglrx.$KERN_VER.ko 
rm -f fglrx.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.$KERN_VER.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.ko
mkdir -p /lib/modules/$KERN_VER/kernel/drivers/misc/fglrx
cd /lib/modules/$KERN_VER/kernel/drivers/misc/fglrx
rm -f fglrx.$KERN_VER.ko 
rm -f fglrx.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.$KERN_VER.ko
ln -s /lib/modules/fglrx/fglrx.$KERN_VER.ko fglrx.ko

# Ensure libGL library symlinks are correct
cd /usr/X11R6/lib
rm libGL.so.1
rm libGL.so
sudo ln -s libGL.so.1.2 libGL.so.1
sudo ln -s libGL.so.1.2 libGL.so

# cleanup hanging module in $HOME as it is no longer needed
rm -f $HOME/fglrx.ko

# Backup xorg.conf file for convenience of user
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup_$TSTAMP

echo
echo -e "$RED_ON ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^"
echo -e 'Installation of drivers complete.'
echo -e 'You must manually configure /etc/X11/xorg.conf however, and then reboot.'
echo -e 'A backup of xorg.conf has already been created for you in /etc/X11'
echo -e
echo -e 'It is recommended these options are setup in xorg.conf:'
echo -e 'Under Section "Device":'
echo -e '   Driver "fglrx" #and remove any reference to Driver "ati"'
echo -e '   Option "no_accel" "no"'
echo -e '   Option "no_dri" "no"'
echo -e '   Option "mtrr" "off" # disable DRI mtrr mapper, driver has its own code for mtrr'
echo -e '   Option "UseInternalAGPGART" "no"'
echo -e
echo -e 'Under Section "Module"'
echo -e '   Load "dbe"'
echo -e '   Load "glx"'
echo -e '   Load "dri"'
echo -e
echo -e 'Under Section "DRI" #note create this section is it is missing from xorg.conf'
echo -e "   Mode 0666 $RED_OFF"

```

---

### Post by dlpfmVfH on 2005-06-13
> **lindt]I've the same problem with 2.6.10-5-k7 kernel said:**
> (*,)
 you don't need the source for the driver...
and make sure make has no colormake or other enhanced features...
like pbuilder, or pentiumbuilder links...

that worked for me..

---

### Post by meteorain on 2005-06-13
> **lindt]I've the same problem with 2.6.10-5-k7 kernel said:**
> (*,)

Same problem here with 2.6.10-5-k7 kernel

---

### Post by bastya_elvtars on 2005-06-13
I tested Ubunto on a machine with GeForce, and it took 1 minute to make nVidia drivers work fine, so this is awful.

---

### Post by bugsbunny on 2005-06-13
Well i can't even get it to compile. Here goes: I downloaded the graphical installer to /home/myhome/ATi-driver then i followed the howto on the first page. Well this below is my install log:

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-686-smp/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686-smp'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.c:57: error: static declaration of ‘__fgl_agp_try_unsupported’ follows non-static declaration
/lib/modules/fglrx/build_mod/2.6.x/agp_backend.h:92: error: previous declaration of ‘__fgl_agp_try_unsupported’ was here
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686-smp'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.

----------------------------------------------------------------------------------------------------------------

I am running breezy is that a problem?

---

### Post by mulperi on 2005-06-13
I also have the k7 kernel.

I feel that if you get mesa drivers, problem is in AGP. If you get no drivers at all, try to uninstall (with complete remove) old driver before installation. 

-----------------------------------------------------
Here are the important sections of my xorg.conf:

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        SubSection "extmod"
         Option "omit xfree86-dga"
        EndSubSection
        Load    "freetype"
        Load    "GLcore"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9500 Pro (R300 NE)"
        Driver          "fglrx"
        Option          "UseInternalAGPGART"    "no"
        BusID           "PCI:1:0:0"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection

Section "DRI"
        Mode    0666
EndSection

-----------------------------------------------------

Good luck!

---

### Post by Ashtray on 2005-06-13
i noticed Ati finaly got a graphical installer... this is truely a giant leap for the linux desktop (user friendly).

 :) 

this is what i get after installing the driver:

1127 frames in 5.0 seconds = 225.400 FPS
1238 frames in 5.0 seconds = 247.600 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1243 frames in 5.0 seconds = 248.600 FPS

//edit

I needed to** COPY the .ko files**, as Jesus explained us earlier !
Afterwards...

11217 frames in 5.0 seconds = 2243.400 FPS
13256 frames in 5.0 seconds = 2651.200 FPS
13257 frames in 5.0 seconds = 2651.400 FPS
13255 frames in 5.0 seconds = 2651.000 FPS

(Note.. pherhaps you need to change the 686 tot 386 it depends on your processor)

[SIZE=4]Thx jesus [/SIZE]

edit//

---

### Post by Ashtray on 2005-06-13
i'm pretty sure the driver is installed correctly now, but hey the **whole system hangs after just a couple of seconds** when i run tuxracer OR Americas Army..

 ](*,)

---

### Post by tabasko on 2005-06-13
Anyway, thanks to your howto, now i can terminate winblows because unrealtournament runs in my linuxbox too!

---

### Post by bugsbunny on 2005-06-13
Is any ATI user using Breezy?

---

### Post by aleyah on 2005-06-14
[QUOTE=bugsbunny]Is any ATI user using Breezy?[/QUOTE]
this morning it works!!
> 2152 frames in 5.0 seconds = 430.400 FPS
2588 frames in 5.0 seconds = 517.600 FPS
3633 frames in 5.0 seconds = 726.600 FPS
3649 frames in 5.0 seconds = 729.800 FPS
3652 frames in 5.0 seconds = 730.400 FPS
3636 frames in 5.0 seconds = 727.200 FPS 
but i'm not sure how...

more or less here what i did (sorry for my english)

1- when i was in hoary i installed the ati drivers and they where ok
2- dist-upgraded to breezy
3- (now the ati control panel has mesa drivers in it)
4- I copied the files as suggested by Jesus (again)
5- then the kleeman way [here](http://www.ubuntuforums.org/showpost.php?p=208786&postcount=99) 
6- so ./ati-driver-installer-8.14.13.run (again..)
(7 - maybe they are not all necessary)

now it seems to work

---

### Post by ChamPro on 2005-06-14
Is this method better than converting the X.org rpm to a deb using alien and then building your own kernel modules?

It seems to me that not breaking the package database and compiling your own kernel modules would produce better results.

---

### Post by foxy123 on 2005-06-14
Thanks for the howto, especially for the link about copying stuff to make the driver work. Though i have to admit that I did not notice any improvement with a new driver. In case of glxgears, the fps remained the same at 1,800. But it's nice to have it anyway.

---

### Post by Ashtray on 2005-06-16
Anybody got any clue why my system gets stuck after a couple of seconds when trying to run a 3d application like americas army or tuxracer ?

I also had this problem on my previous distro (fecora core 3)  and never really could solve it out..

   ](*,)

---

### Post by kori.mendocino on 2005-06-17
i also had troubles with mesa taking over opengl until i removed my restricted-modules, then rebooted, then everything worked just fine. you might want to try it

---

### Post by andhala on 2005-06-18
Has anyone gotten a X800XL to work with 5.04/5.10 ?
If so, please tell how cause i cant even get x to start..

And i have ofcourse tried the things i see here, but none of 'em seems to work

---

### Post by pistoli on 2005-06-18
Thank you to everyone who had input on this subject.  I switched from FC3 a month ago after trying for 3 months to get the ATI driver to work.  It took less than half an hour of fiddling (and a move of the fglrx file) to get the driver to load.  Everything just works...

---

### Post by snaker on 2005-06-19
TO FIX errors with kernel 2.6.12

something like this errors:
...
 CC [M] /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function ‘agp_find_supported_device’:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7134: error: ‘struct pci_dev’ has no member named ‘slot_name’
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7154: error: ‘struct pci_dev’ has no member named ‘slot_name’
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7159: error: ‘struct pci_dev’ has no member named ‘slot_name’
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7185: error: ‘struct pci_dev’ has no member named ‘slot_name’
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7205: error: ‘struct pci_dev’ has no member named ‘slot_name’
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7225: error: ‘struct pci_dev’ has no member named ‘slot_name’
...


*edit* **/lib/modules/fglrx/build_mod/agpgart_be.c**
and
*change all:*       **dev->slot_name** 
*for this:*             **pci_name(dev)**

---

### Post by snaker on 2005-06-19
apply this patch to fix inserting error:

patch: [http://ati.cchtml.com/attachment.cgi?id=110](http://ati.cchtml.com/attachment.cgi?id=110)

error sample:

fglrx: Unknown symbol inter_module_get

---

### Post by lucascr on 2005-06-21
Ciao,

I have a ATI Radeon Mobility 9700 64Mb on an Asus laptop and I have not been able to let it work. My system is a standard Kubuntu 5.04 with kernel 2.6.10-5-686.
I follow the instructions of Jesus and installed the ATI driver running ati-driver-installer-8.14.13.run
Then I changed the /etc/X11/xorg.conf (after I did a backup of the file) according with the howto, so now the Device section looks like 

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M1
1 (RV350 NP)"
        Driver  "fglrx"
        Option  "UseInternalAGPGART" "no" 
EndSection

Reboot, and 
> fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

glxgears gives approximately the same FPS as before. 
This was not the first try, but no matter what I did I ended up with the same situation. 

I tried copyng the fglrx.ko but
/lib/modules/fglrx/> sudo sudo cp fglrx.ko /lib/modules/2.6.10-5-686/
cp: cannot stat `fglrx.ko': No such file or directory

/lib/modules/fglrx/> ls -lt *
-rwxr-xr-x  1 root root  10K 2005-06-20 19:28 make_install.sh

build_mod:
total 1.1M
drwxr-xr-x  2 root root 4.0K 2005-06-20 19:28 2.6.x
-rw-r--r--  1 root root  21K 2005-06-20 19:28 agp3.c
-rw-r--r--  1 root root  11K 2005-06-20 19:28 agp_backend.h
-rw-r--r--  1 root root 211K 2005-06-20 19:28 agpgart_be.c
-rw-r--r--  1 root root 7.1K 2005-06-20 19:28 agpgart.h
-rw-r--r--  1 root root  39K 2005-06-20 19:28 agp.h
-rw-r--r--  1 root root 4.3K 2005-06-20 19:28 drm_compat.h
-rw-r--r--  1 root root  21K 2005-06-20 19:28 drm.h
-rw-r--r--  1 root root 4.7K 2005-06-20 19:28 drm_os_linux.h
-rw-r--r--  1 root root  32K 2005-06-20 19:28 drmP.h
-rw-r--r--  1 root root  16K 2005-06-20 19:28 drm_proc.h
-rw-r--r--  1 root root  98K 2005-06-20 19:28 firegl_public.c
-rw-r--r--  1 root root  31K 2005-06-20 19:28 firegl_public.h
-rw-r--r--  1 root root 5.2K 2005-06-20 19:28 i7505-agp.c
-rw-r--r--  1 root root 219K 2005-06-20 19:28 libfglrx_ip.a.GCC2
-rw-r--r--  1 root root 228K 2005-06-20 19:28 libfglrx_ip.a.GCC3
-rwxr-xr-x  1 root root  33K 2005-06-20 19:28 make.sh
-rw-r--r--  1 root root  14K 2005-06-20 19:28 nvidia-agp.c

So I don't have fglrx.ko here, but a version is present in 
/lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko

Looking at the install log I read:

> more /usr/share/fglrx/fglrx-install.log
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.

So something was wrong at install time, but what? What should I do? 
Any hint?

Thanks,

Luca

---

### Post by bobgreen5s on 2005-06-21
I did everything correctly described here and installed linux-restricted modules for my kernal version and yet I get this error and cannot get 3D acceleration enabled

```
**cat /var/log/Xorg.0.log**
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
```

Any help would be appreciated.

---

### Post by lucascr on 2005-06-23
I solved the problem  :)  with my ATI Radeon Mobility 9700 64Mb.
I used the deb package xorg-driver-fglrx instead of the ATI official, but I guess it should be the same (at least the errors I had were the same, so no driver dependent). 
Check your kernel version (mine is 2.6.10-5-686) and modify below according to it.
Here are the step:

> sudo /etc/initi.d/kdm stop
> sudo modprobe -r fglrx
> cp /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko ~/fglrx.ko_backup
> sudo apt-get install xorg-driver-fglrx
> sudo nedit /etc/X11/xorg.conf                        # or use any editor you like
# Modify the Device section as follows:
+----------------------------
| Section "Device"
|	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
|	Driver		"fglrx"
|   # === Video Overlay for the Xv extension ===
|   Option      "VideoOverlay"               "on"
|   # === OpenGL Overlay ===
|   # Note: When OpenGL Overlay is enabled, Video Overlay
|   #       will be disabled automatically
|   Option      "OpenGLOverlay"              "off"
|   Option      "UseInternalAGPGART"         "no"
|   BusID		"PCI:1:0:0"
| EndSection
+---------------------------
# Identifier and BusID may of course be different

> sudo cp ~/fglrx.ko_backup/lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko
> sudo shutdown -r now

Some of the above lines are taken from the thread [http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

However I still have "Asus ACPI: Error reading LCD status" showing in /var/log/messages

I hope this can help others having my problem.

Ciao   8-) 

Luca

---

### Post by Segovia on 2005-06-23
Everything worked quite easily for me.  nForce2 mobo, ATI 9600 Pro.  I just:

1. Uninstalled the restricted modules and the ubuntu fglrx xorg drivers - in Synaptic.
2. Ran the ATI driver installer.
3. Ran dpkg-reconfigure xserver-xorg
4. Rebooted

With previous version of ATI drivers on nForce2, I have needed - Option "UseInternalAGPGART" "no".  This version seems to have fixed that.  Everything working perfectly out of the box, and I went from 1850 in glxgears to 3200.  Rather amazing increase.

Easiest ATI driver install I've ever done in Linux.

---

### Post by Segovia on 2005-06-23
[QUOTE=bobgreen5s]I did everything correctly described here and installed linux-restricted modules for my kernal version and yet I get this error and cannot get 3D acceleration enabled

```
**cat /var/log/Xorg.0.log**
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
```

Any help would be appreciated.[/QUOTE]
You need to remove the Restricted modules for the kernel you have installed (that is why you're getting the mismatch error), and also the old fglrx package and reboot.  Reinstall the drivers and continue from there.

edit:  I'm assuming you're trying to install the 8.14.13 drivers?  They will install their own modules.  You can't use the ones in the repos.

---

### Post by heltreko on 2005-06-24
[QUOTE=skylark]I finally managed to get these drivers installed with no major issues. I followed asmodeas's recipe to get everything to work for me.

I wrote a script which I believe automates the process (I've tested it on my box, but not yet from a fresh install). The script automates everything except the editing of xorg.conf.

To run it, copy and paste it into a file called "ati_install.sh" and then run:
sudo sh ati_install.sh

Hope it helps someone.
[/CODE][/QUOTE]

Thanks Skylark and others! I've been struggling to get hardware acceleration on my my ATI 9600 XT and it took some work. I finally found and used Skylarks script and look on the difference on my glxgears...

Before... (on ati drivers no hardware acceleration)
linus@sonata:~$ glxgears
726 frames in 5.0 seconds = 145.200 FPS
840 frames in 5.0 seconds = 168.000 FPS
720 frames in 5.0 seconds = 144.000 FPS
720 frames in 5.0 seconds = 144.000 FPS
840 frames in 5.0 seconds = 168.000 FPS
720 frames in 5.0 seconds = 144.000 FPS
840 frames in 5.0 seconds = 168.000 FPS
720 frames in 5.0 seconds = 144.000 FPS

After... (on fglrx 8.14.13)
linus@sonata:~$ glxgears
11800 frames in 5.0 seconds = 2360.000 FPS
13350 frames in 5.0 seconds = 2670.000 FPS
13347 frames in 5.0 seconds = 2669.400 FPS
13350 frames in 5.0 seconds = 2670.000 FPS
13350 frames in 5.0 seconds = 2670.000 FPS
13349 frames in 5.0 seconds = 2669.800 FPS
13350 frames in 5.0 seconds = 2670.000 FPS

Quite a difference. :-)

Once again THANKS!

---

### Post by Siorfin on 2005-06-29
Installed synaptic fglrx drivers then installed latest ati driver and worked like a charm. My xorg.conf is below. I got about a 10-15% increase in performance with these drivers so well worth it.

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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load    "GLcore"
	Load	"glx"
	Load	"dri"
	
	# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
  	SubSection "extmod"
    	    Option "omit xfree86-dga"
  	EndSubSection
	
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Mobility Radeon 9200"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"

	# If X refuses to use the screen resolution you asked for,
	# uncomment this; see "Bugs and Workarounds" for details.
	#Option "NoDDC"

	# === Video Overlay for the Xv extension ===
	Option "VideoOverlay" "on"

	# === OpenGL Overlay ===
	# Note: When OpenGL Overlay is enabled, Video Overlay
	#       will be disabled automatically
	Option "OpenGLOverlay" "off"

	# === Use internal AGP GART support? ===
	# If OpenGL acceleration doesn't work, try using "yes" here
	# and disable the kernel agpgart driver.
	Option "UseInternalAGPGART" "no"

	# === Tweaks ===
	Option "AGPMode" "4"
	Option "EnablePageFlip" "on"
	Option "AGPFastWrite" "on"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Mobility Radeon 9200"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "960x720" "960x600" "928x696" "896x672" "800x600" "640x480"
 	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Deomanh on 2005-07-01
Greets...

I've been fooling around with the newest fglrx and my newly acquired ASUS A6VA laptpop with its mobility x700 card, but the following problem seems to insist on frying my brain cells:  ](*,) 

I downloaded and installed the new drivers from ATI with no trouble at all, and it runs fine with no errors, dri enabled et al. BUT - and here's the killer - the screen is very very dark. No, not blank as in shut off, just it seems very dim, as if i needed to adjust the brightness levels on the damned thing. This means I can see my Kubuntu 5.04 KDE Desktop with a little effort, noticing that it's 1280x800 resolution is undistorted, and can even manage to get to the configuration windows to adjust gamma settings, both on ATI control panel and KDE control center. However, no matter what i do, the brightness of my 15'4 WXGA screen remains quite constant. Darkening the entire room enables me to browse KDE a little further to access a terminal and run glxgears to around 3500 FPS and fgl_glxgears to circa 650 FPS, indicating that everything else is working properly. I can even hear the card's fan powering up and running as it should, again confirming the GPU is being put to work, as opposed to the disappointing ~600 FPS glxgears without fglrx nor DRI.

Also, the special brightness adjustment keys on my laptop, which work flawlessly under radeon or ati drivers, seem to have no effect whatsoever under fglrx. I've also tried using fglrx_xgamma and it does have some visible effect on the colors, but, like before, the monitor simply refuses to "lighten up".  ](*,) 

Please please please HELP!!!  :? 

Thanx

---

### Post by Deomanh on 2005-07-01
Oops, forget that! I just succeeded... turns out all all i had to do is swap Option "MonitorLayout" "LVDS,NONE" with "NONE,LVDS"..... go figure!

I suppose everyone else who have dark screens might try this out and see if it works for them...

---

### Post by tlaloczint on 2005-07-01
I have a question I insatalled ati drivers with out problems at all the only problem was when I restarted ubuntu  I got in to x screen and well I don`t know what to do to make me log in as normal gnome 
any ideas?

---

### Post by Sky-Net on 2005-07-03
Thanks Jesus and Skylark! 

  Following your instructions and installing your script i have my 3d acceleration working.


  But when i try fireglcontrol panel the following message appears : 

[HTML]fireglcontrolpanel: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory[/HTML]

 I'm running the 64 bit generic version of Ubuntu.  Do you know on wich folder should this library be placed in order to run this control panel?

Thanks again!

---

### Post by duffman25 on 2005-07-06
Hi

I've followed this instructions and my driver installation is halfb broken. I've uninstalled fglrx driver delivered on the repos & installed the ati 8.14.13 drivers. Everything seems to work fine except my 3d acceleration. I have a acer aspire 1691WMLi with ati x600 64MB PCI Express. The installation went fine and now I have support for ati's powerplay & I can change the resolution (before I couldn't do so with repos. drivers). My problem comes when I try to load fgl_gears:

```
j$ fgl_glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30

``` 

and

```

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

``` 

this is my xorg.conf:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X600 (M24)"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"MonitorLayout"	"LVDS, AUTO"
	Option		"VideoOverlay"	"on"
	Option          "EnablePageFlip"	"on"
	Option		"DynamicClocks"	"on"
	#Option		"UseInternalAGPGART" "off"
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	30-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X600 (M24)"
	Monitor		"Monitor genérico"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "ServerFlags"
        Option          "DontZap"               "yes"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I've followed this HOWTO with no success on the fgl_glxgears. The searching the web I found instructions on how to duild ati's fglrx modules:
```

cd /lib/modules/fglrx/build_mod
sudo sh make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686'
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
==============================

```

and then:
```

cd ..
sudo sh make_install.sh
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
done.

```

Any ideas? Thanxs in advanced.

---

### Post by duffman25 on 2005-07-06
And this is my Xorg.0.log

and my Xorg.0.log: (see atachment, too long to post it here)

Maybe it clarifies my problem.

---

### Post by kleeman on 2005-07-06
These lines look relevant from your log:

(WW) RADEON(0): Direct rendering not yet supported on Radeon 9500 and newer cards
(WW) RADEON(0): Option "VideoOverlay" is not used
(II) RADEON(0): Direct rendering disabled

The first one is strange since your card is supposed to be supported Hmmm. 

Wait a minute!!!! I just noticed that in your xorg.conf you are using the radeon video driver (which would explain the stuff above). Read the initial post again carefully  ;-) You need to specify fglrx in the Device section NOT radeon (which is the open driver)

---

### Post by duffman25 on 2005-07-06
[QUOTE=kleeman]These lines look relevant from your log:

(WW) RADEON(0): Direct rendering not yet supported on Radeon 9500 and newer cards
(WW) RADEON(0): Option "VideoOverlay" is not used
(II) RADEON(0): Direct rendering disabled

The first one is strange since your card is supposed to be supported Hmmm. 

Wait a minute!!!! I just noticed that in your xorg.conf you are using the radeon video driver (which would explain the stuff above). Read the initial post again carefully  ;-) You need to specify fglrx in the Device section NOT radeon (which is the open driver)[/QUOTE]

Do'h! I have tryed so many combinations that I missed that... hehe thanxs! But still not working :( I have now this configuration in my xorg.conf:

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X600 (M24)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"MonitorLayout"	"LVDS, AUTO"
	Option		"VideoOverlay"	"on"
	Option          "EnablePageFlip"	"on"
	Option		"DynamicClocks"	"on"
	#Option		"UseInternalAGPGART" "off"
EndSection

```

and now my fglrxinfo is:

```

libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

and fglx_gears:
```

libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  36
  Current serial number in output stream:  36

```

Any ideas?

---

### Post by duffman25 on 2005-07-06
Ok... I'm getting closer ... I've read [this](http://dri.freedesktop.org/wiki/DriTroubleshooting) page and it's says that my error is due to file permissions:

> If you get:

libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering

then you are trying to run as a user that doesn't have permission to use the DRI (root is the default allowed user). To let all users access the DRI, add the following section to your XF86Config:

Section "DRI"
    Mode 0666
EndSection 

But my xorg.conf has that setting, so I don't have a clue. If I "sudo fgl_glxgears" then everything is ok.

---

### Post by kleeman on 2005-07-06
Reboot and show you log file (you can find relevant info in it by searching for WW and EE btw).

---

### Post by duffman25 on 2005-07-06
Hehe. I was about to post this:
"rebooting did the trick!"

Thank you very much. It seems that since I uninstalled the xorg-fglrx driver after I installed ati's 8.14.13 dpkg reconfigured my xorg.conf to the free driver. And I didn't noticed that (shame on me for not being carefull enough).

Thanxs again!

EDIT: Ok, after looking carefully at my /var/log/Xorg.0.log I can see that fglrx driver doesn't support the DynamicClocks options (aka PowerPLay):

```

(WW) fglrx(0): Option "DynamicClocks" is not used

```

Does somebody know why this happens? Can't I have simultaneously 3D & powerplay ?¿

Thanxs

---

### Post by kleeman on 2005-07-06
Cool! Configuring X can be a real PITA......

---

### Post by taddy_porter on 2005-07-09
I've been trying to get 3d acceleration working for weeks with no luck from ati or the stock fglrx. Here's the error I'm getting. I removed the resricted modules and stock fglrx but still get the error:

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
Makefile:50: *** mixed implicit and normal rules.  Stop.
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.

---

### Post by Conan_the_Librarian on 2005-07-11
Hi,

Taddy_porter and others who are having the problem where running /lib/modules/fglrx/build_mod/make.sh results in the following error : -

Makefile:50: *** mixed implicit and normal rules. Stop.
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.

this seems to be caused by an error(?) in the ATI makefile where your verison of GCC is detected or parsed incorrectly. To work around this change the first line of /lib/modules/fglrx/build_mod/2.6.x/Makefile to read : -

GCC_VER_MAJ      = 3

and then re-run **sudo /lib/modules/fglrx/build_mod/make.sh**. This should force the installer to compile against GCC3.

---

### Post by songochain on 2005-07-13
Somebody have a ubuntu amd64 and he can play to doom3?? I get [this](http://songochain.eresmas.com/doom3) error when i try to run doom3
I've installed fglrx correctly and i've 3d acceleration.
Thanks

---

### Post by edgarallan on 2005-07-13
hi i've barton 2500 on nforce2 mobo and radeon 2600 pro (agpgart and nvidia_agp loaded into kernel)

i've done all the possible... followed all the stiky messages. (2 days of frustration maybe i will return winzozz)

fglrxinfo say i'm in MESA
Xorg.0.log say loaded kernel module for "fglrx" driver
Kernel Module version matches driver.
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
DRI initialization successfull!
glrxinfo say direct rendering: No
client glx vendor string: ATI
OpenGL vendor string: Mesa

don't know what i can do
please helpme
tanks and bye,
francesco. this is my xorg.conf:

ection "Files"
FontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
FontPath "/usr/lib/X11/fonts/misc"
FontPath "/usr/lib/X11/fonts/cyrillic"
FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/Type1"
FontPath "/usr/lib/X11/fonts/CID"
FontPath "/usr/lib/X11/fonts/100dpi"
FontPath "/usr/lib/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "dri"
Load "bitmap"
Load "dbe"
Load "ddc"
Load "glx"
# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
SubSection "extmod"
Option "omit xfree86-dga"
EndSubSection
Load "freetype"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
Load "GLcore"
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "it"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
Driver "fglrx"
Option "UseInternalAGPGART" "no"
BusID "PCI:2:0:0"
Option "backingstore" "true"
# === Video Overlay for the Xv extension ===
Option "VideoOverlay" "yes"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
# will be disabled automatically
Option "OpenGLOverlay" "off"
# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.

EndSection

Section "Monitor"
Identifier "CM715"
Option "DPMS"
EndSection



Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
Monitor "CM715"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

---

### Post by nehalem on 2005-07-13
I can never get the ati drivers to install on my laptop (nx7010 w/9200 radeon mobility).  Here is what I get from the log:

> initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
In file included from /lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:125:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:56:48: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:57:6: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:58:41: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:508: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:510: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:530: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:577)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:561: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2647: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_uninit':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3185: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.

I gave up before but would still love to get this to work.

What could be the problem (I have the 686 kernel with headers.

As to this line:
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
I can say that the file libfglrx_ip.a.GCC3 does exist.

---

### Post by Jesus Franco on 2005-07-14
Okay people. Some of you are asking questions that I have already answerd.  :neutral: 
Please either use the forum search or read the whole thread.

If all else fails use the drivers in the repository.  :grin:

---

### Post by nehalem on 2005-07-14
Really? 

I swear I've gone through this thread like ten times in frustration (it's not exactly a small thread).  I'll look again.

I can see that people have had similar problems as me but I haven't seen an answer given for them.  I have tried your method where you copy all the modules and stuff but still don't have success.  I really don't know what to do and the repository version is buggy.

---

### Post by zalves on 2005-07-16
Hi there!

I'm Stuck with 640x480 @ 60hz, when I try to install the drivers everything goes till it says "there were errors during the instalation" bla bla check log. the says this:

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.

I have the kernel-headers installed and my version of ubuntu was the one downloaded in 11-July-05.

If it helps my video card is a 9800XT

Pls help

Thks, Pedro

---

### Post by WetWilly on 2005-07-17
damn ati for releasing such crappy drivers. I installed it, and it fucked up my resolution so hard. The config is stuck at 1024x768 but the monitor only displays 640x480 and I cannot run fgl_glxgears as it prints this nonsense..

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  145 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32


and fglrxinfo prints this

 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


although my xorg;conf is correct...

---

### Post by nubcakes on 2005-07-19
Great tutorial, thanks a lot man.  \\:D/

---

### Post by joe897897 on 2005-07-20
Nice job, i had to do the 686 to k7 copy procedure you mention at the bottom and it's ok !
Huge improve too, 3250 -> 4500 at glxgears with those new drivers !!! 

TKS a lot

---

### Post by Jesus Franco on 2005-07-20
No problem. I *hear* ATI should release their new drivers in september. They would most likely have support for the 2.6.12 kernels and the xorg that will be out by then. Once those come out I will update the tutorial.

---

### Post by nehalem on 2005-07-30
Hehe, finally got these to work and they're awesome.  I am really dumb in that I didn't realize I had to uninstall the restricted modules...

Perhaps in the future of your tutorial you might include how to uninstall the old drivers (drivers and restricted modules) since I bet a lot of people started with the repository drivers first.

Thanks for your tutorial!

---

### Post by Jakenaattori on 2005-08-01
Hi!
When I'm trying to install the drivers it says "There were errors during the installation
Details can be found in...".
Heres the log:
```

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.

```
Please help me! I'm a total Linux n00b and I just want those drivers up and running.

---

### Post by Jon E on 2005-08-07
[QUOTE=Jakenaattori]Hi!
When I'm trying to install the drivers it says "There were errors during the installation
Details can be found in...".
Heres the log:
```

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.

```
Please help me! I'm a total Linux n00b and I just want those drivers up and running.[/QUOTE]

Run this:

sudo apt-get install build-essential

and sudo apt-cache search linux-headers

find whichever one matches your system and install that as well, that should get you through the ati installer.

---

### Post by Kanbeki on 2005-08-08
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
 ](*,) 
I have followed every step, I've moved the old file out of the dir, I've removed the old drivers with synaptic..wtc

---

### Post by johannes on 2005-08-09
Works great on my laptop with Radeon Mobility 9700, 64 mb. I powered up in glxgears from 1400 to 2000.  :)  Thanks!

---

### Post by graigsmith on 2005-08-09
omg sweet, i got it working !  :)  :)  :)  :)  :) 

i was having problems, after i installed it direct rendering (dri) was not working. 

so i uninstalled the restricted modules packages. and then reinstalled the ati drivers and it worked perfectly :)

---

### Post by nehalem on 2005-08-10
Well after going for some time all I can say is these drivers have been incredibly stable.  I'm happy to see what ATI is doing.  Now if they can get the performance (and features) side stuff up a bit then they'll be on their way to matching Nvidia's offerings.

---

### Post by jyank on 2005-08-10
[QUOTE=Kanbeki]fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
 ](*,) 
I have followed every step, I've moved the old file out of the dir, I've removed the old drivers with synaptic..wtc[/QUOTE]
 Not sure if this has been posted earlier in the thread, I didn't read every page sorry ;)

But, the way I got my opengl working properly was doing this:

Go into synaptic and remove xorg-driver-fglrx and xorg-driver-fglrx-dev.  Restart X (control alt backspace) and head into a normal command line, (if restarting X didn't bring you to one, hit control alt F1) 

login as you normally would at the ubuntu splash screen, then reinstall the drivers.

```
 sudo apt-get install xorg-driver-fglrx xorg-driver-fglrx-dev
```

That has succesfully solved my opengl problems multiple times with different PCs all with ATI cards.

---

### Post by HammerDonk on 2005-08-10
[QUOTE=jyank]Not sure if this has been posted earlier in the thread, I didn't read every page sorry ;)

But, the way I got my opengl working properly was doing this:

Go into synaptic and remove xorg-driver-fglrx and xorg-driver-fglrx-dev.  Restart X (control alt backspace) and head into a normal command line, (if restarting X didn't bring you to one, hit control alt F1) 

login as you normally would at the ubuntu splash screen, then reinstall the drivers.

```
 sudo apt-get install xorg-driver-fglrx xorg-driver-fglrx-dev
```

That has succesfully solved my opengl problems multiple times with different PCs all with ATI cards.[/QUOTE]
 after you run the install,
try to type: fglrxconf - it's configure your xorg.conf - i think ..?

---

### Post by jyank on 2005-08-10
[QUOTE=HammerDonk]after you run the install,
try to type: fglrxconf - it's configure your xorg.conf - i think ..?[/QUOTE]
 Yes, but I've found when you let them configure it, it usually only leads to problems.  I'd reccomend doing it manually, it's not that hard

---

### Post by Dolphin on 2005-08-10
[QUOTE=SWAT]Yes.... problem solved. 
I removed the 'old' fglrx, by using Synaptic. Then I used the howto in THIS thread and JUST BEFORE compiling you need to do **sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME**. Then it still compiles with an error, but it works fine  :)[/QUOTE]

I installed using OP's howto and it's not working.  I'm running glxgears at 150fps.  Is this what I need to do to fix it?  And where exactly do I insert this step?  Thank you.

---

### Post by Lux Perpetua on 2005-08-10
Do it right before you install the new driver. The installation will add its own fglrx.ko in that directory, and I guess it doesn't always work if the old file is still there (I think).

---

### Post by Dolphin on 2005-08-11
Okay, I'm going outta my mind trying to get these to work.

There's been so many add-ons and corrections to the tutorial that I don't know what to do anymore and I'm obviously screwing up somewhere.

Could some kind soul tell me step-by-step what I need to do, from a clean ubuntu install, to get these drivers to work?  Assistance would be greatly appreciated.

TIA

---

### Post by Epskampie on 2005-08-11
Hi everybody, I've gotten mine to work too, using this guide. I don't know exactly how I did it, since i didn't start with a clean install, and there was QUITE a bit of messing around involved. :) Anyway, here is a step by step guide which might work, for the people who are getting confused. You might want to run "glxgears" in a terminal now to see what framerate you're getting, and if it has improved after succesfull install.

[list]
[*]First off you will need some packages. Open synaptic package management for this.
Install the **"build-essential"** package.

Furthermore you will need headers for your kernel. This may sound threatening, but it's just another package.  ;-) 
If you have got hoary ubuntu on an x86 pc (most likely), you will need the **"linux-headers-2.6.10-5-386"** package. Install this too. 

*If you're not using an x86 processor you will need an other package, just search for "linux-header" and read the descriptions, they speak for themselves.*


[*]Now, before going on, backup your "xorg.conf" file. It's the file where all the settings concerning your video output are saved, and if you screw up at any point, you are likely to fix it by putting the backup of this file back.
Open up a terminal, and type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```*All this does really is making a backup of you xorg.conf file to a file called xorg.conf-backup, in the /etc/X11/ dir. You might want to back it up to some other place like your homedir too, just to be sure.*


[*]Next were gonna move a file away, which supposedly is in the way during installation of the ati drivers. Some people have reported this step necessary.
To move (mv) the file out of the way (into your homedir), enter the following command in your terminal:
```
sudo mv /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko $HOME
```*Taken that you have the 2.6.10-5-386 kernel ofcourse, otherwise this folder will be named differently*


[*]Next we download the the ati installer and start it. First navigate the terminal to the folder you want to download the file to, then execute the following two commands:
```
wget http://www2.ati.com/drivers/linux/ati-driver-installer-8.14.13.run 
sudo sh ./ati-driver-installer-8.14.13.run
```The ati installer will now start. First choose "Install Driver" (selected by default), then click next. On the next screen you might wanna choose "Automatic Installation", with me it didn't work, it complained about not having write acces to the binary folder.
So I choose "custom installation", which works just fine too, because the right options are already selected on the next screen. (the three options under xorg 6.8.)
The installer will copy and compile some files, then finish.
Now check the log of the install. Its located in **/usr/share/fglrx/fglrx-install.log**
mine looked like this:
```
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
In file included from /lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:125:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:56:48: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:57:6: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:58:41: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:508: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:510: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:530: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:577)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:561: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2647: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_uninit':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3185: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
done.
```
*Notice there still is a warning about libfglrx_ip.a.GCC3.cmd, but since we moved the file out of the way this shouldn't matter.*
If your log is very short and there is something about it missing a "kernel module build environment" you haven't installed the kernel headers right. Go back to step one.


[*]Now you have a choice. You will need to configure your xorg.conf to use the freshly installed ati drivers. There are two ways to do this.

*method A* - You could use the utility provided by by ati, called "fglrxconfig". This is much advised against on this forums, but I did it anyway, and it turned out fine.
*method B* - You could edit the xorg.conf manualy, using some instructions from the original howto. This might be easier, since you don't have to answer a lot of questions about your setup, but you might miss some settings.

*If you don't know which method to choose, just take a pick. Since you made a backup of xorg.conf, you can always revert to the old situation and try again using the other method.*

**Method A**
Manouver to your home directory.
Enter "fglrxconfig" in your terminal to start the ati config utility. In the beginning everything pretty much speaks for itself. 
For the horizontal and vertical refresh rate of your monitor you can look up the specifications of your monitor on the web, or open your backup of xorg.conf, xorg.conf-backup, and read them from there. 
I started getting a bit confused at the "Do you want to initialize xfree86-dga (y/n)? [n]" so from there on i used the settings on this site if i didn't know what to choose: [http://www.alexandern.com/3D_ATI_RADEON_on_Linux.html](http://www.alexandern.com/3D_ATI_RADEON_on_Linux.html)

If your finished there should be a freshly created xorg.conf file in your home dir. Copy it over the original xorg.conf:
```
sudo cp ~/xorg.conf /etc/X11/xorg.conf
```*Please open /etc/X11/xorg.conf to verify that it is the newly created file*

**Method B**
Fill in the new options yourself, I quote:
> Now type ```
# sudo gedit /etc/X11/xorg.conf 
```
In your xorg.conf file make sure that under Section "Module" the following lines are listed
```
 
 Load "dri"
 Load "glx"

```
Now look for Section "Device" And make sure that it looks like the following
```
 
 Identifier  "Radeon"
 Driver  "fglrx"
 Option  "UseInternalAGPGART" "no" 
 BusID  "PCI:3:0:0"

```
Its okay if your Identifier is different and if your BusID is different aswell. But make sure your Driver says "fglrx" and that you have the "Option              "UseInternalAGPGART" "no" " Right below it.

Now look for another section. Most of the time this is the last one listed.
```
 
Section "DRI"
 Mode 0666
EndSection

```If it is not on your config Make Sure You Add It.


[*]reboot


[*]If you get some kind of blue screen telling you something went wrong with the x server the xorg.conf you created is not right. Press ctrl + alt + F1 to go to a command prompt, log in like you normally would, and copy the backup of xorg.conf back. Then restart gdm, and you should have the old login screen back.
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
sudo killall gdm
sudo /etc/init.d/gdm start
```You can now have another try at editing your xorg.conf :)


[*]If you just get you're normal login screen, it MIGHT have just worked. Login, open a terminal, and enter "fglrxinfo" to see the video driver.
It should say something like:
```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro Generic
OpenGL version string: 1.3.5140 (X4.3.0-8.14.13)
```*Notice the 8.14.13, which are the drivers we just installed*
If it says something including MESA it didn't work, the mesa drivers are the default ones.


[*]If everything turned out allright you might wanna run "glxgears", and the real test "fgl_glxgears" to test the opengl drivers.
I'm getting 3300+ fps on glxgears, and 500+ fps on fgl_glxgears with a radeon 9700 and AMD64 3200+ (using ubuntu 32 bit).
[/list]

Im hoping this will help some of you.
[COLOR=Red]
Disclaimer: above worked for me, but it might not for you. Use at your own risk.
[/COLOR]

---

### Post by DGibFen on 2005-08-11
Nice guide Epskampie.  Works flawlessly for me.  Thanks!

---

### Post by Dolphin on 2005-08-11
Epskampie,

This is, without a doubt, the best first post by any user on any forum ever!

That Epskampie is a computer genius man!  Let's do a dance for the computer genius man!

[img]http://brendoman.com/images/strongbad.jpg[/img]

---

### Post by runamonk on 2005-08-12
[QUOTE=NoTiG]I think i have a slight problem. I followed the directions exactly (except replacing the filename with the 64 bit one since im doing the 64 bit driver) ... everything went without error. I restarted and all... BUt when i run glxgears... it lists as 144 FPS . i think that is low right??????? And when I run tuxracer.... the fps is so slow it is unplayable. so i believe something is wrong. I opened up /etc/X11/xorg.config again after to see that i was using the fglrx driver and the changes are still there... so what is wrong??? BTW im using an ATI 9600 Mobility , on a amd64 300 .. with 512mb of ram.[/QUOTE]

I have this exact same issue except I'm using the drivers that were listed. I have a P4 1.6 with 1GIG of ram and a ATI 9600 Mobility chipset.

---

### Post by runamonk on 2005-08-13
[QUOTE=Epskampie]Best How TO yet[/QUOTE]


Awesome work. This made alot of sense, basically I was missing that my kernal needed to be recompiled hehehe. :)

This worked great!

---

### Post by Unam on 2005-08-16
Epskampie,

Thanks, I read through this forum and the "HOW TO: ATI Divers v0.2" from front to back, I was missing one simple step, your guide helped because it puts everything on one page. Once I fixed that one step everything works fine!

Well done!

---

### Post by Unam on 2005-08-18
FYI,

I successfully installed the latest ATi driver (8.16.20) using the same method, worked just fine.

Follow the "How to" but insert these lines at the beginning;

```
# wget http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run
# sudo sh ./ati-driver-installer-8.16.20-i386.run
```

Output of glxgears = 22914 frames in 5.0 seconds = 4582.800 FPS
Output of fgl_glxgears = 4549 frames in 5.0 seconds = 909.800 FPS

Have fun... :wink:

---

### Post by firenurse4 on 2005-08-18
[QUOTE=Unam]Epskampie,

Thanks, I read through this forum and the "HOW TO: ATI Divers v0.2" from front to back, I was missing one simple step, your guide helped because it puts everything on one page. Once I fixed that one step everything works fine!

Well done![/QUOTE]

How about an AMEN chorus for that!   \\:D/  \\:D/ 

Installed the kernel headers and moved the file in question. Re ran the installer and [COLOR=DarkRed]BAM!!![/COLOR] 3d acceleration now works! I was getting ready to scrab my ATI card and switch to nvidia!

Now if we could make Epskampie's post a sticky  ;-) 

Thanks Again

---

### Post by mwave on 2005-08-23
thankyou thankyou thankyou, epskarmpie, very good followed your instructions and now have full 3d graphics, new to linux was getting to the stage of tearing my hair out then you get a little light at the end of the tunnel, very rewarding whe something goes to plan. iam starting to understand why you guys like linux.
thanks again, now onwards to the next challenge  \\:D/

---

### Post by Hamman on 2005-08-23
[QUOTE=mwave]thankyou thankyou thankyou, epskarmpie, very good followed your instructions and now have full 3d graphics, new to linux was getting to the stage of tearing my hair out then you get a little light at the end of the tunnel, very rewarding whe something goes to plan. iam starting to understand why you guys like linux.
thanks again, now onwards to the next challenge  \\:D/[/QUOTE]
 On a side note, for those who had problems installing 8.14, 8.16 worked much better for me. Just a tip.

---

### Post by Belutz on 2005-08-25
I finally installed the 8.16.20 driver :)

```
Enter Command > fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)
``` 

thx for the great HOWTO

---

### Post by blazer78 on 2005-09-05
i followed the instructions to the letter, however i'm still getting this error in my fglrx-install.log (it appears at the very bottom of the log file)

- trying a sample load of the kernel module
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.

what am i doing wrong?

---

### Post by Lux Perpetua on 2005-09-05
Post the rest of the log file, or at the very least, start from where the errors begin.

---

### Post by blazer78 on 2005-09-05
well i went ahead and ignored the error and rebooted, once i log in all of ubuntu locks up. (cannot alt-ctrl-f1)

Now the problem is... when i restore my original xorg.conf file, screen corruption occurs... As soon as i fix this problem, i shall post the log file.

---

### Post by Christoff UK on 2005-09-06
Well the linked guide worked like a dream for me, thanks guys! Finnally that DRI missing message has dissapeared!

---

### Post by BrokenBrick on 2005-09-09
Was going to note that, yes I had the same problem.  However, not sure it is necessary to connect to http/ftp for the files, since the installation saves them to your drive in the step previous to user setup.  Not sure WHERE, but somewhere - Might speed up installation and take some strain off the servers :)

---

### Post by blazer78 on 2005-09-10
```
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-k7/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-k7'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6070: warning: `ati_gart_base' defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:498: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:500: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:520: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:577)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:551: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_uninit':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3428: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
include/linux/module.h: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1921: warning: `deferred_flush' defined but not used
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-k7'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.

```

what am i doing wrong?

---

### Post by blazer78 on 2005-09-13
hmm.. i've tried multiple methods of installing the ati driver.... unfortunately none of them worked properly. either ubuntu locks up or it loads using MESA software opengl. =(

---

### Post by BrokenBrick on 2005-09-15
I would not care about getting drivers to work, since the default one works fine, and I don't really play games.  But I rely heavily on TV out for watching movies so I have been wrestling with this problem all week.  Here is the output from my fglrx-install.log
```
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.12-8-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-8-386'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `agp_find_supported_device':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7136: error: structure has no member named `slot_name'
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7156: error: structure has no member named `slot_name'
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7161: error: structure has no member named `slot_name'
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7187: error: structure has no member named `slot_name'
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7207: error: structure has no member named `slot_name'
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7227: error: structure has no member named `slot_name'
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7232: error: structure has no member named `slot_name'
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_init':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7613: warning: `pm_register' is deprecated (declared at include/linux/pm.h:106)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_cleanup':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:7623: warning: `pm_unregister_all' is deprecated (declared at include/linux/pm.h:116)
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-8-386'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.
```

Not sure if this is important but my fglrx.ko file was in /lib/modules/2.6.12-8-386/volatile/fglrx.ko and not in the video drivers folder.  I am also running breezy, not hoary

---

### Post by ArthurDent on 2005-09-24
```
[Error] Kernel Module : Failed to compile kernel module - please consult readme.
```
I had the same problem - it seems to be caused by having the fglrx packages already installed when the ATI Driver Installer is run.  I fixed it using this process:

1.  Use Synaptic to **remove** every fglrx package (there are 4 that may be installed - remove any that are).

2.  Backup /etc/X11/xorg.conf ([Epskampie shows how](url=http://www.ubuntuforums.org/showthread.php?t=32495&page=17&pp=10)) 

3.  Set your driver to "radeon" (not "fglrx") in xorg.conf.  (I'm assuming that xorg.conf is otherwisely OK)
```
(...)
Section "Device"
	Identifier	"*Your card name should be here*"
	Driver		"radeon"
(...)
```4.  Follow [Epskampie's walkthrough from Page 17 of this thread](http://www.ubuntuforums.org/showthread.php?t=32495&page=17&pp=10), **but**:

4.1  You might as well get the newest ATI Drivers, so use these two lines instead of the similar ones in Epskampie's walkthrough:
```
wget http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run 
sudo sh ./ati-driver-installer-8.16.20-i386.run
```4.2  Before rebooting, edit your /etc/X11/xorg.conf again, setting the driver to "fglrx".
```
(...)
Section "Device"
	Identifier	"*Your card name should be here*"
	Driver		"fglrx"
(...)
```5.  Reboot, and enjoy.

Note: Steps 3 and 4.2 are there to make sure you'll still be able to load X if you happen to reboot your machine before it says to during Epskampie's walkthrough.

With this method, I now get 10240 FPS in glxgears.  :grin:

Thanks Epskampie!

---

### Post by predator on 2005-09-25
[SIZE=4]**don't worry.. my bad.. anybody having same problem may wish to visit [http://ubuntuforums.org/showthread.php?t=66334](http://ubuntuforums.org/showthread.php?t=66334)**[/SIZE]

i have downloaded.. and run ATI drivers.. 

in my /usr/share/fglrx log however I get

> 
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
make -C /lib/modules/2.6.12-8-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
/usr/src/linux-headers-2.6.12-8-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-8-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-8-386'
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/agp3.o] Error 127
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-8-386'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.



I have installed the 'build-essential packages' using synaptic package.. and also the required linux kernal header files as discussed above. .Appears the main problem is that its trying to run gcc-3.4 but its not the right gcc (if i type GCC, its there). 

I am using Badger 5.10 release.

Any pointers. Yes i am a bit of a n00b to this sort of thing.

---

### Post by ale_mza on 2005-10-01
Help? Please? :)  Here's what happened. I'm a newbie. I followed the How to, and everything was fine, except for the detail that what it supposed to say in the xorg.conf, didn't match. I have a MSI Radeon 9800 Pro (with XT chip). My xorg.conf said:

Identifier  "Radeon"
Driver  "Ati"
VideoRam    "131072" 
Option  "xxxxxxxxxx" "true" 

So, as you can see, the part where says [BusID  "PCI:3:0:0"] wasn't there. And I didn't add it neither. I just changed the Driver part and the option. I rebooted the Pc, and everything seems to work right. Except that, the Ati Control, doesn't open. And I can not play videos with totem, because when i'm opening it, it gives me an error saying that the video output is being used by another application, and that I should close the other application or to choose another video output (????). But then, when I open a video with Xine (that works), it doesn't run well. It is like if it has a hard time trying to show it. (sorry about my english). 

Should I change any other value? add anything else?

---

### Post by duffydack on 2005-10-05
Ive dloaded the .run file from ati, ran it, finished it, ran fglrxconfig and went thru it, then made sure fglrx was set as driver in xorg.conf and rebooted, and still get mesa crap
I have had this working before with the older drivers but i cant remember if i did anything different,


# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
 

Update:
after lots of fumbling and searching i had to do this
[http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87](http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87)

dont know why all those files werent there already, but it works now..
6486 frames in 5.0 seconds = 1297.200 FPS (only when the gears are minimised, when showing its half of that)
That seem right for a dell inspiron 9100 (p4 3.2/HT gig o ram and mobility radeon 9800?

Glxgears:
18138 frames in 5.0 seconds = 3627.600 FPS --open
36401 frames in 5.0 seconds = 7280.200 FPS -- minimised
39018 frames in 5.0 seconds = 7803.600 FPS -- minimised

---

### Post by graigsmith on 2007-01-05
have they improved stability any? cause all they do to my system is crash it.

---

### Post by supertux on 2007-01-05
> **graigsmith said:**
> have they improved stability any? cause all they do to my system is crash it.

dude this topic is very old :)

---

