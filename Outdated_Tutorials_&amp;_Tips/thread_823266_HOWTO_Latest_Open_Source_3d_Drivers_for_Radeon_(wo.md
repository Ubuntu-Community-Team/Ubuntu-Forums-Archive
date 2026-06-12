---
title: "HOWTO: Latest Open Source 3d Drivers for Radeon (works on r5xx)"
date: 2008-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by dmb on 2008-06-09
Hello, I decided to make a guide on how to get the latest open source 3d drivers for the radeon card. I made this tutorial based on my ATI Mobility Radeon x1400 on a Dell E1705, but this should get any card below and including the R5xx chipset working with 3D. Please note that this does not work with compiz yet, not quite sure why, it could have to do with the fact that maybe the mesa from git is too new for the xserver hardy has, but everything else works. 

First, you need to install some development libraries:
```

sudo apt-get build-dep libdrm mesa
sudo apt-get install linux-headers-`uname -r` libxi-dev libxmu-dev x11proto-xf86vidmode-dev libxkbfile-dev libxfont-dev libfontenc-dev libssl-dev git-core autoconf automake libtool xserver-xorg-dev
sudo apt-get install x11proto*

```
Now, lets create and enter a source directory to place the sources into:
```

mkdir src
cd src

```

We need to install the dri2 prototypes:
```

wget [ftp://ftp.freedesktop.org/pub/individual/proto/dri2proto-1.1.tar.bz2](ftp://ftp.freedesktop.org/pub/individual/proto/dri2proto-1.1.tar.bz2) 
tar xjf dri2proto-1.1.tar.bz2
cd dri2proto-1.1/ 
./autogen.sh --prefix=/usr
sudo make install
cd ..

```

Now we need to grab both mesa and drm from git:
```

git clone git://anongit.freedesktop.org/git/mesa/drm
git clone git://anongit.freedesktop.org/git/mesa/mesa

```
Lets build and install drm, which is the kernel part:
```

cd drm
./autogen.sh --prefix=/usr
make 
sudo make install
cd linux-core
make DRM_MODULES="radeon"
make 
sudo make install
sudo depmod -a
cd ../../

```
Now lets build mesa, with the radeon and r300 drivers (r3xx is required for r5xx cards):
```

cd mesa
./autogen.sh --prefix=/usr --with-dri-drivers=radeon,r300
make
sudo make install
cd ..

```
Now, we need to build and install the latest open sourcec ati/radeon driver:
```

git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-ati 
cd xf86-video-ati
./autogen.sh --prefix=/usr
make
sudo make install

```
After that is done, reboot, make sure your /etc/X11/xorg.conf has radeon as its driver, and 3d should be working.  Run glxinfo and make sure 
>  direct rendering: Yes 
If not, you have done something wrong (or I did something wrong in the tutorial)

This guide was based off of the original dri building guide, as well as [http://www.x.org/wiki/radeonhd%3ADRI](http://www.x.org/wiki/radeonhd%3ADRI) and some other sources. Any problems, corrections or criticisms can go on this thread.

---

### Post by alof8k on 2008-07-05
where is the xf86-video-ati directory? it's not in the src directory....

EDIT: I got the issue fixed. You forgot to add the command 
> git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-ati

But after all of that, when running glxinfo, I get:

> name of display: :0.0
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
0x6a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


---

### Post by nikhilgupta on 2008-07-05
> **alof8k said:**
> where is the xf86-video-ati directory? it's not in the src directory....

Before, ```
cd xf86-video-ati
```
Do ```
git clone ssh://git.freedesktop.org/git/xorg/driver/xf86-video-ati
``` to get the xf86-video-ati sources.

---

### Post by nikhilgupta on 2008-07-05
Thanks dmb for the guide. It helped me get 3d and 2d working on my x1300 mobility radeon card. Even I cannot run compiz. Gives me a blank white screen. Did you get it to work?

---

### Post by timewave on 2008-07-05
> **alof8k said:**
> where is the xf86-video-ati directory? it's not in the src directory....

EDIT: I got the issue fixed. You forgot to add the command 


But after all of that, when running glxinfo, I get:
Try compiling mesa with the software rasterizer driver:

./autogen.sh --prefix=/usr --with-dri-drivers=radeon,r300,**swrast**
make
sudo make install

Then build/install the driver as usual.

---

### Post by dmb on 2008-07-05
> **nikhilgupta said:**
> Thanks dmb for the guide. It helped me get 3d and 2d working on my x1300 mobility radeon card. Even I cannot run compiz. Gives me a blank white screen. Did you get it to work?

Yes, compiz will not work because it requires a newer version of xserver.  Also, I updated the guide to include cloning the ati driver (my bad).

---

### Post by dmb on 2008-07-06
> **alof8k said:**
> where is the xf86-video-ati directory? it's not in the src directory....

EDIT: I got the issue fixed. You forgot to add the command 


But after all of that, when running glxinfo, I get:

Can you post your /var/log/Xorg.0.log please? Also if possible, post 
the output of 'LIBGL_DEBUG=verbose glxinfo'

---

### Post by zgornel on 2008-07-06
Thanks, it worked. Still no compiz, heavy tearing and unreliable 3D support for some games like Open Arena but 2D performance under KDE with transparencies enabled is much better. I estimate that by the time 8.10 comes out R500 will be fully supported :D .
PS. I tried the latest xorg packages (created from latest git) from Xorg-edgers but they break X and have no support for some input devices. Is there a somewhat stable release (packages) that supports compiz with the latest ATI driver ?

---

### Post by timewave on 2008-07-06
To get compiz working put in your /etc/X11/xorg.conf in section Device:

```
"Option" "AccelMethod" "exa"
```

Also don't forget that your driver, in that same section, has to be "radeon", if it isn't already. 

Note that this driver is only designed for Radeon X1000 series and older, support for RadeonHD cards is not official yet.

---

### Post by zgornel on 2008-07-06
> **timewave said:**
> To get compiz working put in your /etc/X11/xorg.conf in section Device:

```
"Option" "AccelMethod" "exa"
```

Also don't forget that your driver, in that same section, has to be "radeon", if it isn't already. 

Note that this driver is only designed for Radeon X1000 series and older, support for RadeonHD cards is not official yet.

Nope, that does not work, tried all possible combinations. Compiz will work only with an updated git Xserver. The problem resides in AIGLX and it is known:
```

(EE) AIGLX error: dlopen of /usr/lib/dri/r300_dri.so failed (/usr/lib/dri/r300_dri.so: undefined symbol: _glapi_tls_Context)
(EE) AIGLX: reverting to software rendering

```

---

### Post by alof8k on 2008-07-06
I've done everything from the first post again, but this time with swrast as suggested by timewave.  the entire system seems to be crawling i don't know why. 

here's the LIBGL_DEBUG=verbose glxinfo:

> $ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x27 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x28 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x29 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2a 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x6a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


and here is the Xorg.0.log :

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux mohammed-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul  6 17:29:02 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3205 card 1043,8118 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 109e,036e card 1822,0001 rev 11 class 04,00,00 hdr 80
(II) PCI: 00:09:1: chip 109e,0878 card 1822,0001 rev 11 class 04,80,00 hdr 80
(II) PCI: 00:0a:0: chip 11c1,048c card 11c1,044c rev 03 class 07,80,00 hdr 00
(II) PCI: 00:0b:0: chip 1106,3044 card 1043,808a rev 80 class 0c,00,10 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,810a rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80ff rev 78 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,71c7 card 1787,2227 rev 9e class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71e7 card 1787,2226 rev 9e class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:9:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xe6000000/12
(--) PCI:*(1:0:0) ATI Technologies Inc RV535 [Radeon X1650 Series] rev 158, Mem @ 0xd0000000/28, 0xe5000000/16, I/O @ 0x9000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV535 [Radeon X1650 Series] rev 158, Mem @ 0xe5010000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe6005000 - 0xe60050ff (0x100) MX[B]
	[1] -1	0	0xe6004000 - 0xe60040ff (0x100) MX[B]
	[2] -1	0	0xe6003000 - 0xe60037ff (0x800) MX[B]
	[3] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[4] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B](B)
	[9] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[10] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[26] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe6005000 - 0xe60050ff (0x100) MX[B]
	[1] -1	0	0xe6004000 - 0xe60040ff (0x100) MX[B]
	[2] -1	0	0xe6003000 - 0xe60037ff (0x800) MX[B]
	[3] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[4] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B](B)
	[9] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[10] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[26] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6005000 - 0xe60050ff (0x100) MX[B]
	[5] -1	0	0xe6004000 - 0xe60040ff (0x100) MX[B]
	[6] -1	0	0xe6003000 - 0xe60037ff (0x800) MX[B]
	[7] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[8] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B](B)
	[13] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[25] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[27] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[29] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[30] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[31] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[32] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[33] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,

	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610, ATI RV670,
	ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE, ATI Radeon HD 3470,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI FireMV 2450, ATI FireMV 2260,
	ATI FireMV 2260, ATI ATI Radeon HD 3600 Series,
	ATI ATI Radeon HD 3650 AGP, ATI ATI Radeon HD 3600 PRO,
	ATI ATI Radeon HD 3600 XT, ATI ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics
(II) Primary Device is: PCI 01:00:0
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon X1650 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6005000 - 0xe60050ff (0x100) MX[B]
	[5] -1	0	0xe6004000 - 0xe60040ff (0x100) MX[B]
	[6] -1	0	0xe6003000 - 0xe60037ff (0x800) MX[B]
	[7] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[8] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B](B)
	[13] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[25] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[27] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[29] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[30] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[31] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[32] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[33] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6005000 - 0xe60050ff (0x100) MX[B]
	[5] -1	0	0xe6004000 - 0xe60040ff (0x100) MX[B]
	[6] -1	0	0xe6003000 - 0xe60037ff (0x800) MX[B]
	[7] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[8] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B](B)
	[13] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[24] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[30] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[32] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[33] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[34] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[35] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[36] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000e5000000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "AGPMode" "8"
(**) RADEON(0): Option "GARTSize" "64"
(**) RADEON(0): Option "EnablePageFlip" "true"
(**) RADEON(0): Option "DMAForXv" "true"
(**) RADEON(0): Option "ColorTiling" "on"
(**) RADEON(0): Option "DynamicClocks" "on"
(**) RADEON(0): Option "AccelMethod" "exa"
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon X1650" (ChipID = 0x71c7)
(WW) RADEON(0): R500 support is under development. Please report any issues to [email]xorg-driver-ati@lists.x.org[/email]
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): AGP card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1787 SubsystemID: 0x2227
	IOBaseAddress: 0x9000
	Filename: 67402CAC.HFA
	BIOS Bootup Message: 

RV535PRO DDR2 512M 1787-67417CAA.HFA                                        


(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x1fffb000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 600000
(II) RADEON(0): Default Memory Clock: 400000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1100000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1600
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 110000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 600.000000, mclk: 400.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=13 min=64800 max=110000; xclk=40000
(II) RADEON(0): Skipping TV-Out
(II) RADEON(0): Skipping Component Video
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x7e40, DACType-1, TMDSType-0, ConnectorType-1, hpd_mask-0x0
(II) RADEON(0): Port3: DDCType-0x7e50, DACType-2, TMDSType-1, ConnectorType-2, hpd_mask-0x1
(II) RADEON(0): Output VGA-0 using monitor section aticonfig-Monitor[0]-0
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): TMDS PLL from BIOS: 16500 e0153
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x7e40
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x7e50
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "720x350"x0.0   28.32  720 738 846 900  350 388 390 449 +hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 71a5  Serial#: 1481395266
(II) RADEON(0): Year: 1999  Week: 49
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.85
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 28.3 MHz   Image Size:  250 x 184 mm
(II) RADEON(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) RADEON(0): Serial No: 1780RDXLLBC9
(II) RADEON(0): Monitor name: DELL M770
(II) RADEON(0): Ranges: V min: 48  V max: 160 Hz, H min: 30  H max: 69 kHz,
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010aca571424c4c58
(II) RADEON(0): 	31090101081e17b9e80eb2a057479926
(II) RADEON(0): 	10484fa44a0061594559818031590101
(II) RADEON(0): 	010101010101100bd0b4205e6310126c
(II) RADEON(0): 	6208fab80000001a000000ff00313738
(II) RADEON(0): 	305244584c4c4243390a000000fc0044
(II) RADEON(0): 	454c4c204d3737300a202020000000fd
(II) RADEON(0): 	0030a01e45ff000a20202020202000bf
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
finished output detect: 1
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "720x350"x0.0   28.32  720 738 846 900  350 388 390 449 +hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 71a5  Serial#: 1481395266
(II) RADEON(0): Year: 1999  Week: 49
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.85
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 28.3 MHz   Image Size:  250 x 184 mm
(II) RADEON(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) RADEON(0): Serial No: 1780RDXLLBC9
(II) RADEON(0): Monitor name: DELL M770
(II) RADEON(0): Ranges: V min: 48  V max: 160 Hz, H min: 30  H max: 69 kHz,
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010aca571424c4c58
(II) RADEON(0): 	31090101081e17b9e80eb2a057479926
(II) RADEON(0): 	10484fa44a0061594559818031590101
(II) RADEON(0): 	010101010101100bd0b4205e6310126c
(II) RADEON(0): 	6208fab80000001a000000ff00313738
(II) RADEON(0): 	305244584c4c4243390a000000fc0044
(II) RADEON(0): 	454c4c204d3737300a202020000000fd
(II) RADEON(0): 	0030a01e45ff000a20202020202000bf
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1280x768
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (300, 230) mm
(**) RADEON(0): DPI set to (142, 176)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(**) RADEON(0): Using EXA acceleration architecture
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe5000000 - 0xe500ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe6005000 - 0xe60050ff (0x100) MX[B]
	[7] -1	0	0xe6004000 - 0xe60040ff (0x100) MX[B]
	[8] -1	0	0xe6003000 - 0xe60037ff (0x800) MX[B]
	[9] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[10] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B](B)
	[15] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[27] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[28] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[29] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[31] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[32] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[33] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[35] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[36] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[37] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[38] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[39] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit d0000000 0 0
(==) RADEON(0): Write-combining range (0xd0000000,0x10000000)
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Static power management enable success
Dynamic clock gating enable success
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x20000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(==) RADEON(0): Not using accelerated EXA DownloadFromScreen hook
(II) RADEON(0): Allocating from a screen of 262144 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00a8c000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00a90000
(II) RADEON(0): Will use 10800 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 251312 kb for X Server offscreen at offset 0x00a94000
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1280x768 - 1680 795 0
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffd000 0xffffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 80140000
best_freq: 80140909
best_feedback_div: 653
best_ref_div: 22
best_post_div: 10
(II) RADEON(0): crtc(0) Clock: mode 80140, PLL 80140
(II) RADEON(0): crtc(0) PLL  : refdiv 22, fbdiv 0x28D(653), pdiv 10
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DAC1 setup success
Output 68 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): EXA Composite requires CP on R5xx/IGP
(II) RADEON(0): num pipes is 1
(II) EXA(0): Offscreen pixmap area of 257343488 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         UploadToScreen
(II)         DownloadFromScreen
(II) RADEON(0): Acceleration enabled
(**) Option "dpms" "true"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Textured video requires CP on R5xx/IGP
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "TripleBuffer" is not used
(WW) RADEON(0): Option "VendorName" is not used
(WW) RADEON(0): Option "ModelName" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 250 x 184
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "720x350"x0.0   28.32  720 738 846 900  350 388 390 449 +hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 71a5  Serial#: 1481395266
(II) RADEON(0): Year: 1999  Week: 49
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.85
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 28.3 MHz   Image Size:  250 x 184 mm
(II) RADEON(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) RADEON(0): Serial No: 1780RDXLLBC9
(II) RADEON(0): Monitor name: DELL M770
(II) RADEON(0): Ranges: V min: 48  V max: 160 Hz, H min: 30  H max: 69 kHz,
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010aca571424c4c58
(II) RADEON(0): 	31090101081e17b9e80eb2a057479926
(II) RADEON(0): 	10484fa44a0061594559818031590101
(II) RADEON(0): 	010101010101100bd0b4205e6310126c
(II) RADEON(0): 	6208fab80000001a000000ff00313738
(II) RADEON(0): 	305244584c4c4243390a000000fc0044
(II) RADEON(0): 	454c4c204d3737300a202020000000fd
(II) RADEON(0): 	0030a01e45ff000a20202020202000bf
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "720x350"x0.0   28.32  720 738 846 900  350 388 390 449 +hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 71a5  Serial#: 1481395266
(II) RADEON(0): Year: 1999  Week: 49
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.85
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 28.3 MHz   Image Size:  250 x 184 mm
(II) RADEON(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) RADEON(0): Serial No: 1780RDXLLBC9
(II) RADEON(0): Monitor name: DELL M770
(II) RADEON(0): Ranges: V min: 48  V max: 160 Hz, H min: 30  H max: 69 kHz,
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010aca571424c4c58
(II) RADEON(0): 	31090101081e17b9e80eb2a057479926
(II) RADEON(0): 	10484fa44a0061594559818031590101
(II) RADEON(0): 	010101010101100bd0b4205e6310126c
(II) RADEON(0): 	6208fab80000001a000000ff00313738
(II) RADEON(0): 	305244584c4c4243390a000000fc0044
(II) RADEON(0): 	454c4c204d3737300a202020000000fd
(II) RADEON(0): 	0030a01e45ff000a20202020202000bf
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "720x350"x0.0   28.32  720 738 846 900  350 388 390 449 +hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 71a5  Serial#: 1481395266
(II) RADEON(0): Year: 1999  Week: 49
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.85
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 28.3 MHz   Image Size:  250 x 184 mm
(II) RADEON(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) RADEON(0): Serial No: 1780RDXLLBC9
(II) RADEON(0): Monitor name: DELL M770
(II) RADEON(0): Ranges: V min: 48  V max: 160 Hz, H min: 30  H max: 69 kHz,
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010aca571424c4c58
(II) RADEON(0): 	31090101081e17b9e80eb2a057479926
(II) RADEON(0): 	10484fa44a0061594559818031590101
(II) RADEON(0): 	010101010101100bd0b4205e6310126c
(II) RADEON(0): 	6208fab80000001a000000ff00313738
(II) RADEON(0): 	305244584c4c4243390a000000fc0044
(II) RADEON(0): 	454c4c204d3737300a202020000000fd
(II) RADEON(0): 	0030a01e45ff000a20202020202000bf
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "720x350"x0.0   28.32  720 738 846 900  350 388 390 449 +hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 71a5  Serial#: 1481395266
(II) RADEON(0): Year: 1999  Week: 49
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.85
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 28.3 MHz   Image Size:  250 x 184 mm
(II) RADEON(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) RADEON(0): Serial No: 1780RDXLLBC9
(II) RADEON(0): Monitor name: DELL M770
(II) RADEON(0): Ranges: V min: 48  V max: 160 Hz, H min: 30  H max: 69 kHz,
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010aca571424c4c58
(II) RADEON(0): 	31090101081e17b9e80eb2a057479926
(II) RADEON(0): 	10484fa44a0061594559818031590101
(II) RADEON(0): 	010101010101100bd0b4205e6310126c
(II) RADEON(0): 	6208fab80000001a000000ff00313738
(II) RADEON(0): 	305244584c4c4243390a000000fc0044
(II) RADEON(0): 	454c4c204d3737300a202020000000fd
(II) RADEON(0): 	0030a01e45ff000a20202020202000bf
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "720x350"x0.0   28.32  720 738 846 900  350 388 390 449 +hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 71a5  Serial#: 1481395266
(II) RADEON(0): Year: 1999  Week: 49
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.85
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 28.3 MHz   Image Size:  250 x 184 mm
(II) RADEON(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) RADEON(0): Serial No: 1780RDXLLBC9
(II) RADEON(0): Monitor name: DELL M770
(II) RADEON(0): Ranges: V min: 48  V max: 160 Hz, H min: 30  H max: 69 kHz,
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010aca571424c4c58
(II) RADEON(0): 	31090101081e17b9e80eb2a057479926
(II) RADEON(0): 	10484fa44a0061594559818031590101
(II) RADEON(0): 	010101010101100bd0b4205e6310126c
(II) RADEON(0): 	6208fab80000001a000000ff00313738
(II) RADEON(0): 	305244584c4c4243390a000000fc0044
(II) RADEON(0): 	454c4c204d3737300a202020000000fd
(II) RADEON(0): 	0030a01e45ff000a20202020202000bf
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1280x1024 - 1712 1063 6
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffd000 0xefffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 109000000
best_freq: 109000000
best_feedback_div: 109
best_ref_div: 3
best_post_div: 9
(II) RADEON(0): crtc(0) Clock: mode 109000, PLL 109000
(II) RADEON(0): crtc(0) PLL  : refdiv 3, fbdiv 0x6D(109), pdiv 9
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DAC1 setup success
Output 68 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "720x350"x0.0   28.32  720 738 846 900  350 388 390 449 +hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 71a5  Serial#: 1481395266
(II) RADEON(0): Year: 1999  Week: 49
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.85
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 28.3 MHz   Image Size:  250 x 184 mm
(II) RADEON(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) RADEON(0): Serial No: 1780RDXLLBC9
(II) RADEON(0): Monitor name: DELL M770
(II) RADEON(0): Ranges: V min: 48  V max: 160 Hz, H min: 30  H max: 69 kHz,
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010aca571424c4c58
(II) RADEON(0): 	31090101081e17b9e80eb2a057479926
(II) RADEON(0): 	10484fa44a0061594559818031590101
(II) RADEON(0): 	010101010101100bd0b4205e6310126c
(II) RADEON(0): 	6208fab80000001a000000ff00313738
(II) RADEON(0): 	305244584c4c4243390a000000fc0044
(II) RADEON(0): 	454c4c204d3737300a202020000000fd
(II) RADEON(0): 	0030a01e45ff000a20202020202000bf
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "720x350"x0.0   28.32  720 738 846 900  350 388 390 449 +hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 71a5  Serial#: 1481395266
(II) RADEON(0): Year: 1999  Week: 49
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.85
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 28.3 MHz   Image Size:  250 x 184 mm
(II) RADEON(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) RADEON(0): Serial No: 1780RDXLLBC9
(II) RADEON(0): Monitor name: DELL M770
(II) RADEON(0): Ranges: V min: 48  V max: 160 Hz, H min: 30  H max: 69 kHz,
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010aca571424c4c58
(II) RADEON(0): 	31090101081e17b9e80eb2a057479926
(II) RADEON(0): 	10484fa44a0061594559818031590101
(II) RADEON(0): 	010101010101100bd0b4205e6310126c
(II) RADEON(0): 	6208fab80000001a000000ff00313738
(II) RADEON(0): 	305244584c4c4243390a000000fc0044
(II) RADEON(0): 	454c4c204d3737300a202020000000fd
(II) RADEON(0): 	0030a01e45ff000a20202020202000bf
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 29093
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
SetClientVersion: 0 9
```


by the way, my system specs are:

amd athlon xp 2800+, radeon x1650 PRO (512MB agp version, saphire card), asus mobo (forgot which one, but its a compaq presario from about 4 years ago), 1GB RAM.

---

### Post by zgornel on 2008-07-07
The problem is DRI cannot be initialized because of the kernel (DRM) module: 
[I]drmOpenDevice: Open failed
[COLOR="Red"](EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM[/COLOR]
[dri] Disabling DRI.
[/I]
Are you sure you got it installed? Do a ```
sudo modprobe radeon
``` followed by ```
sudo depmod -a
``` after being sure you compiled and installed it. Then, restart X server and check if Direct Rendering is enabled. If not, post the result of [CODE]cat /var/log/Xorg.0.log |grep EE[CODE]

---

### Post by Green_Star on 2008-07-08
This is great guide. So far I was using proprietary drivers for my ati x1300. My monitor supports upto 1920*1080 but i am using my default resolution as 1080*1050. I successfully installed this open source drivers but I have a problem when i am using these open source drivers, my ubuntu 7.10 is going to screen resolution 1280*800 and funny thing is my background image is spread to whole screen but my ubuntu using only a portion (3/4) of the screen that means i have some empty space at left side and bottom. when i run movies in full screen then also same thing it is not using whole screen. it is little annoying. How can i change the screen resolution? I tried going to Preferences -> Screen resolution but the max resolution i can select is 1280*800. If i switch back to fglrx then everything is good. here below my xorg.conf

> 
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#Section "Extensions"
#	Option	    "Composite" "0"
#EndSection
#Section "Extensions"
#	Option		"Composite"	"0"
#	Option		"Composite"	"0"
#EndSection

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option 	    "XkbOptions" "altwin:super_win"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
#	Driver      "fglrx"
	Driver      "radeon"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
	SubSection "Display"
	Depth 1
	Modes "1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 4
	Modes "1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 8
	Modes "1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 15
	Modes "1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 16
	Modes "1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 24
	Modes "1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection


---

### Post by zgornel on 2008-07-08
A quick fix, try ```
xrandr --fb <width>x<height>
```

---

### Post by Green_Star on 2008-07-09
> **zgornel said:**
> A quick fix, try ```
xrandr --fb <width>x<height>
```

Thanks man, but it didnt help me, i am getting following message and I attached the screen shot, my monitor saying it is running at 1680*1050@60Hz. But my ubuntu shows in menu that it is running at 1280*800. As i said before screen background is using whole my screen but not the windows.

> ~$ xrandr --fb 1080x1050
xrandr: specified screen 1080x1050 not large enough for output VGA-0 (1280x800+0+0)


---

### Post by zgornel on 2008-07-09
Hmmm, well, you don't seem to have 1080x1050 in the list of resolution for any of the color depths. Add "1080x1050" for all the depths out there : 1,4,8,15,16 and 24. I don't think the proprietary driver looks inside Xorg for them but the open source one does. This is because I can change resolutions on my laptop without having them listed in my xorg.conf.

---

### Post by rtom on 2008-10-07
I tried to follow the guide but at the autogen.sh command for mesa I got the following error:
" Requested 'dri2proto >= 1.99.1' but version of DRI2Proto is 1.1".

Where to get a higher version of dri2proto?

---

### Post by rtom on 2008-10-14
OK, I continued serching for a solution, and found that I need to patch the dri2proto package to 1.99, based on [this]("http://cgit.freedesktop.org/xorg/proto/dri2proto/diff/").

Never done such a patching, could someone advice me?

---

### Post by rtom on 2008-10-24
I found the version 1.99 of dri2proto in git: git://anongit.freedesktop.org/git/xorg/proto/dri2proto

Now I have another problem making mesa:

```
dri2.c: In function ‘DRI2Connect’:
dri2.c:117: error: ‘xDRI2ConnectReq’ has no member named ‘screen’
dri2.c:124: error: ‘xDRI2ConnectReply’ has no member named ‘busIdLength’
dri2.c:134: error: ‘xDRI2ConnectReply’ has no member named ‘busIdLength’
dri2.c:142: error: ‘xDRI2ConnectReply’ has no member named ‘busIdLength’
dri2.c:145: error: ‘xDRI2ConnectReply’ has no member named ‘busIdLength’
dri2.c:150: error: ‘xDRI2ConnectReply’ has no member named ‘busIdLength’
dri2.c:151: error: ‘xDRI2ConnectReply’ has no member named ‘busIdLength’
dri2.c: In function ‘DRI2AuthConnection’:
dri2.c:162: error: ‘xDRI2AuthConnectionReq’ undeclared (first use in this function)
dri2.c:162: error: (Each undeclared identifier is reported only once
dri2.c:162: error: for each function it appears in.)
dri2.c:162: error: ‘req’ undeclared (first use in this function)
dri2.c:163: error: ‘xDRI2AuthConnectionReply’ undeclared (first use in this function)
dri2.c:163: error: expected ‘;’ before ‘rep’
dri2.c:168: error: ‘sz_xDRI2AuthConnectionReq’ undeclared (first use in this function)
dri2.c:168: error: expected expression before ‘)’ token
dri2.c:168: error: ‘X_DRI2AuthConnection’ undeclared (first use in this function)
dri2.c:173: error: ‘rep’ undeclared (first use in this function)
dri2.c: In function ‘DRI2SwapBuffers’:
dri2.c:263: error: ‘xDRI2SwapBuffersReq’ undeclared (first use in this function)
dri2.c:263: error: ‘req’ undeclared (first use in this function)
dri2.c:264: error: ‘xDRI2SwapBuffersReply’ undeclared (first use in this function)
dri2.c:264: error: expected ‘;’ before ‘rep’
dri2.c:269: error: ‘sz_xDRI2SwapBuffersReq’ undeclared (first use in this function)
dri2.c:269: error: expected expression before ‘)’ token
dri2.c:269: error: ‘X_DRI2SwapBuffers’ undeclared (first use in this function)
dri2.c:278: error: ‘rep’ undeclared (first use in this function)
make[2]: *** [dri2.o] Error 1
```

Any ideas to solve this?

---

### Post by Rob2687 on 2008-12-25
I had to add the following to Xorg.conf otherwise it would revert to the software raster thing.

> Section "DRI"
    Mode 0666
EndSection

This was based on the following page.
[http://dri.freedesktop.org/wiki/DriTroubleshooting#head-e217f9d56159347d24d9b33b0aaf2e631482482d](http://dri.freedesktop.org/wiki/DriTroubleshooting#head-e217f9d56159347d24d9b33b0aaf2e631482482d)

---

### Post by sam1948 on 2009-01-26
on ubuntu 8.10 it has a simpler way look at this thread
[http://ubuntuforums.org/showthread.php?p=6623552#post6623552](http://ubuntuforums.org/showthread.php?p=6623552#post6623552)

---

