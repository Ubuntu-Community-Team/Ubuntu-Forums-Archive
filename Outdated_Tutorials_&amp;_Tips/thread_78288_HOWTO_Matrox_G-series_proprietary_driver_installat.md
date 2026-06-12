---
title: "HOWTO: Matrox G-series proprietary driver installation"
date: 2005-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by pinf on 2005-10-18
DRI support dropped since it didn't work after all :-(
Maybe someone can explain howto install from source?

I hope this helps someone. Sorry for my bad English.

MATROX PROPRIETARY GRAPHICS DRIVER (BINARY) INSTALLATION - UBUNTU BREEZY

OS: Ubuntu Breezy 5.10 i386
HW: Matrox G550 32Mt (DualHead) and 2 x Viewsonic VX900 LCD

This document will help you to install Matrox proprietary driver to Ubuntu.
Matrox driver is needed for DVI support (also 3D and TV-out with limitations...no luck with 3D (DRI) so far with binary driver).
See Matrox document for more info on features.

1. Download the latest driver package at [www.matrox.com](www.matrox.com). Grab the binary version tar.gz which was v. 4.2.0 at the time of writing.

2. Unpack and install the driver (as root).

$ sudo -i
$ tar zxvf mgadriver-4.2.0.tar.gz
$ cd mgadriver-4.2.0
$ ./install

This will copy binary drivers to /usr/X11/lib/modules/drivers
I got some errors here, but copy was successfull.

You can verify copy with (check file time stamps) ls command:

$ ls -l /usr/X11R6/lib/modules/drivers/mga*
-rw-r--r--  1 root root 211291 Oct 17 08:52 /usr/X11R6/lib/modules/drivers/mga_drv.o
-rw-r--r--  1 root root 328354 Oct 17 08:52 /usr/X11R6/lib/modules/drivers/mga_hal_drv.o

3. Backup xorg.org file and copy Matrox version in place.

$ cp /etc/X11/xorg.conf /etc/X11/xorg.conf.org
$ cd mgadriver-4.2.0/samples/
$ cp XF86Config.dual /etc/X11/xorg.conf 
(Matrox provides several examples, see which one suits you best)

4. Working xorg.conf example

Below is my xorg.conf (see comments).

Section "ServerLayout"
        Identifier     "Simple Layout"

        Screen         "Screen 1" RightOf "Screen 2"
        Screen         "Screen 2"

        InputDevice    "Mouse1" "CorePointer"
        InputDevice    "Keyboard1" "CoreKeyboard"
EndSection

Section "ServerFlags"
	# disabled xinerama, because I want two separate screens
    Option "Xinerama"   "no"
EndSection

Section "Files"
        RgbPath      "/usr/X11R6/lib/X11/rgb"
        FontPath     "/usr/X11R6/lib/X11/fonts/local/"
        FontPath     "/usr/X11R6/lib/X11/fonts/misc/"
        FontPath     "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/X11R6/lib/X11/fonts/Type1/"
        FontPath     "/usr/X11R6/lib/X11/fonts/Speedo/"
        FontPath     "/usr/X11R6/lib/X11/fonts/75dpi/"
EndSection

Section "Module"
        Load  "dbe"
        Load  "extmod"
        Load  "type1"
        Load  "freetype"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Keyboard1"
        Driver      "kbd"
        Option      "AutoRepeat" "500 30"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "fi"
        Option      "XkbCompat" ""
EndSection

Section "InputDevice"
        Identifier  "Mouse1"
        Driver      "mouse"
	# good for MS IntelliMouse 1.1 (wheel and sidebuttons)
        Option      "Protocol" "ExplorerPS/2"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5"
        Option      "Buttons" "7"
EndSection

Section "Monitor"
        Identifier   "My Monitor 1"
        HorizSync    30.0 - 82.0
        VertRefresh  50.0 - 75.0
EndSection

Section "Monitor"
        Identifier   "My Monitor 2"
        HorizSync    30.0 - 82.0
        VertRefresh  50.0 - 75.0
EndSection

Section "Device"
        Identifier  "MGA CARD 1"
        Driver      "mga"
        BusID       "PCI:1:0:0"
	# first LCD is connected with DVI)
        Option      "DigitalScreen1" "on"
        Screen      0
        Option  "DPMS"
EndSection

Section "Device"
        Identifier  "MGA CARD 2"
        Driver      "mga"
        BusID       "PCI:1:0:0"
#   Option      "DigitalScreen2" "on"
        Screen      1
        Option  "DPMS"
EndSection

Section "Screen"
        Identifier "Screen 1"
        Device     "MGA CARD 1"
        Monitor    "My Monitor 1"
        DefaultDepth   24

        SubSection "Display"
                Depth     16
        Modes   "1024x768" "800x600" "640x480"
        EndSubSection

        SubSection "Display"
                Depth     24
#        Modes   "1024x768" "800x600" "640x480"
        Modes   "1280x1024" "1024x768" "800x600" "640x480"

        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen 2"
        Device     "MGA CARD 2"
        Monitor    "My Monitor 2"
        DefaultDepth    24

        SubSection "Display"
                Depth     16
        Modes   "1024x768" "800x600" "640x480"
        EndSubSection

        SubSection "Display"
                Depth     24
#        Modes   "1024x768" "800x600" "640x480"
        Modes   "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by chrisle on 2005-10-18
And does this work for you?

In my case dri does not work because of some version mismatch.

So please edit this howto, and tell people howto compile the driver from source or howto install only the hallib if they need a dual monitor setup.

Thanks.

Bye chris.

---

### Post by drucer on 2005-10-18
Is dual monitor (DVI) supported with Matrix G550 and Ubuntu? Anyone got it working?

---

### Post by pinf on 2005-10-19
[QUOTE=chrisle]And does this work for you?

In my case dri does not work because of some version mismatch.

So please edit this howto, and tell people howto compile the driver from source or howto install only the hallib if they need a dual monitor setup.
[/QUOTE]

DRI works me out of the box with this. What errors do you get in /var/log/Xorg.0.log

Sorry I can't help with source compile since I haven't done it.
As far as I know, source compile shouldn't be needed if xorg version is supported (like 6.8.2 in Breezy).

And for dual DVI, I haven't been able to test it out because my Matrox has VGA+DVI. It should work with DigitalScreen option.

Matrox also has a great web forum for Linux support, check it out for more info.

---

### Post by chrisle on 2005-10-19
Did how you wrote, but

export LIBGL_DEBUG=verbose

glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 1.1.1 mga (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/mga_dri.so
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
libGL error:
MGA DRI driver expected DDX version 1-1.2.x but got version 1.1.1
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
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
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None

 ls -l /usr/X11R6/lib/modules/drivers/mga*
-rw-r--r--  1 root root 211291 2005-10-19 15:11 /usr/X11R6/lib/modules/drivers/mga_drv.o
-rw-r--r--  1 root root 328354 2005-10-19 15:11 /usr/X11R6/lib/modules/drivers/mga_hal_drv.o

can you post your glxinfo ouput?

Thanks

---

### Post by _cato on 2005-10-30
When I tried to install the xorg-drivers from matrox, I ran into the same problems like chrisle, with exactly the same version-missmatched-error.

I solved the problem with using xorg's mga_drv.o and matrox' mga_hal_drv.o. This way I got direct rendering working (This is tested). With this solution it _should_ also be possible to use the tv-out (I'm going to test this next week - some cabels and adapters are still missing) and dvi (Which I couldn't test because neither my matrox nor my monitor have dvi).

I hope this helps a bit

_cato

---

### Post by argux on 2005-10-30
I tried this, restarted the X server and checked /var/log/Xorg.0.log. It says the modules are loaded and that Direct Rendering is working.

Then, when I run glxinfo, it says

glxinfo
name of display: :0.0
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
display: :0  screen: 0
direct rendering: No

I am in the video group, and the permissions are set right. What am I missing?

I'd like to try using the old xorg module, but I don't know where it was copied (assuming it was copied and not simply deleted by the *script of hell*)

---

### Post by _cato on 2005-10-31
You missed to read the thread. It said that the matrox-binaries currently doesn't work completely with ubuntu breezy. In my previous post I provided a kind of a workaround.

How to get the original xorg-driver back:

1) ./install.sh restore (the matrox way)
2) a) get xserver-xorg-driver-mga_6.8.2-77_i386.deb (either from your /var/cache/apt/archives dir or from a mirror)
    b) unpack the .deb: ar xf xserver-xorg-driver-mga_6.8.2-77_i386.deb
    c) untar the data.tar.gz: tar xzf data.tar.gz
    d) copy ./usr/X11R6/lib/modules/drivers/mga_drv.o to /usr/X11R6/lib/modules/drivers
    e) restart X ;)

---

### Post by pinf on 2005-11-07
xorg driver does not provide DVI support (as far as I know). And I haven't been able to enable DRI with prop driver. I also get "direct rendering enabled" in Xorg log, but glxinfo does not work still. I don't need DRI but DVI is essential so maybe I wait for Matrox fixes...

---

