---
title: "[SOLVED] New graphics card not working"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by one_ako on 2008-08-25
wondering if i can get some help with this same type of situation. i also have pro savage on my system so i was able to find an old nvidia 5200. i put it in the vga slot and connected the monitor to it but i get nothing. conecting it back to the onboard gets me the log in screen and im able to use ubuntu fine.
im pretty new to this so im not sure if im missing a step. shouldnt it automatically detect the new card?

thanks for your help!

---

### Post by overdrank on 2008-08-25
> **one_ako said:**
> wondering if i can get some help with this same type of situation. i also have pro savage on my system so i was able to find an old nvidia 5200. i put it in the vga slot and connected the monitor to it but i get nothing. conecting it back to the onboard gets me the log in screen and im able to use ubuntu fine.
im pretty new to this so im not sure if im missing a step. shouldnt it automatically detect the new card?

thanks for your help!

Hi and I have moved your post to its own thread.
Are you sure the graphics card is good? Can you disable the onboard graphics in bios on the system?

---

### Post by one_ako on 2008-08-25
thanks for the fast reply and getting me a new thread. im not completly sure if the card works but the last time it was tried it did work fine. on a windows machine. is there a way to check it? or by it not doing anything automatically means that it doesnt work? i dont have another computer with windows other than my laptop to test it out.

i also read that disabling the onboard graphics might help. but dont really know how to go about doing that.

BTW:im running ubuntu 8.04

thank you!!

---

### Post by overdrank on 2008-08-25
> **one_ako said:**
> thanks for the fast reply and getting me a new thread. im not completly sure if the card works but the last time it was tried it did work fine. on a windows machine. is there a way to check it? or by it not doing anything automatically means that it doesnt work? i dont have another computer with windows other than my laptop to test it out.

i also read that disabling the onboard graphics might help. but dont really know how to go about doing that.

BTW:im running ubuntu 8.04

thank you!!

Hi and if you can get into bios by using the delete key or on some system it is the F1 or so on. You may see the directions on the Post screen as to which keys to use. Then you can search the bios and determine if you can disable the integrated graphics or select which to use primary.

---

### Post by one_ako on 2008-08-25
im at work so i cant try this untill i get home. but....

after i disable the integrated graphics will the new one be automatically detected? and if it doesnt get detected then it means the card does not work?

---

### Post by coolbrook on 2008-08-25
Is it AGP or PCI?  You need to configure X to look at the address of your AGP/PCI slot instead of the address of the onboard video.  Run these commands in terminal:

[http://ubuntuforums.org/showpost.php?p=3944138&postcount=2](http://ubuntuforums.org/showpost.php?p=3944138&postcount=2)

The driver I selected is **"nv"**

---

### Post by one_ako on 2008-08-25
it is an AGP card....does it matter when i run the commands you suggest?

i will run those commands as soon as i get home. 

thanks to both of you!

---

### Post by one_ako on 2008-08-25
so i did what you suggested (coolbrook) but it didnt work. i went into bios like (overdrank) suggested and i was able to tell it to use the AGP slot.

that worked and was able to get into ubuntu fine. i went to appearance to see if i can get the visual effects from none to normal or extra. ubuntu automatically started requesting and downloading the proper drivers for the 5200.

it then told me a re-start was required for the changes to take effect.

after the re-start i went to change appearance again and it said that it "desktop effects could not be enabled"

any reason for that?

---

### Post by one_ako on 2008-08-25
so i found the compiz check. it gave me this info. 

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Composite manually disabled 

Would you like to know more? (Y/n) y

 It has been detected that the "Composite" option of your /etc/X11/xorg.conf
 has been set to "Disable" 

 Open the file being root and change "Disable" to "Enable"
 Then restart X and try again. 

ortez@ortez-desktop:~$ 

how do i do this part? ===It has been detected that the "Composite" option of your /etc/X11/xorg.conf
 has been set to "Disable" 

 Open the file being root and change "Disable" to "Enable"
 Then restart X and try again. ====

---

### Post by overdrank on 2008-08-25
Hi and can you post the output of the command ```
cat /etc/X11/xorg.conf
``` you can just copy and paste.

---

### Post by one_ako on 2008-08-25
here is the info you requested.

```
ortez@ortez-desktop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
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

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option		"UseEdidFreqs"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
ortez@ortez-desktop:~$ 
```

also i figured out that the nvidia card was not enabled. after i enable i did the compiz-check and got this

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...
ERROR: NV-CONTROL extension version 1.6 is too old; the minimimum required
       version is 1.11.

./compiz-check: line 715: [: : integer expression expected
           [ OK ]
```

thank you!

---

### Post by one_ako on 2008-08-26
bump.

---

### Post by one_ako on 2008-08-26
so i got the card working after going into bios and directed it to use the AGP slot.

after trying to get the extra effects.... it installed the "restricted drivers" and asked for a re-start. after the re-start i tried to enable the extra graphics but it kept telling me that extra settings could not be enabled

i read that envyng might help. ran it and it seemed to be installing my proper drivers. it went through everything ok and said my drivers were installed and requested a re-start. 

after the re-start and trying to get extra settings again it said the composite derectory was not activated.

looked in the hardware drivers and saw that the nvidia card was disabled.

should it be disabled? i enabled it and went to try to get the extra settings again and it says that extra settings could not be enabled.

is this just a crappy card? because of this
```
ERROR: NV-CONTROL extension version 1.6 is too old; the minimimum required
       version is 1.11.
```

---

### Post by one_ako on 2008-08-26
anyone? overdrank where are you?

checking the nvidia x server settings i get this.

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

how do i do that?

---

### Post by Crafty Kisses on 2008-08-26
Post the results of > glxinfo

---

### Post by one_ako on 2008-08-26
here is the info but FYI i am currently re-running envyNG

```
ortez@ortez-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
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
GLX version: 1.3
GLX extensions:
    GLX_ARB_get_proc_address, GLX_EXT_import_context, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: RIVA TNT2/AGP/SSE2
OpenGL version string: 1.4 (1.5.3 NVIDIA 71.86.04)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_texture_env_add, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square, GL_NV_fog_distance, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_SGIS_texture_edge_clamp, 
    GL_SUN_multi_draw_arrays, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
ortez@ortez-desktop:~$ 


```

---

### Post by starcannon on 2008-08-26
Heres a guide I wrote on how I install all of my NVidia Cards. I believe that if you follow it and don't skip steps you'll have compiz goodness shortly, caveat is not all hardware is the same, but from the sounds of it, I think this link should fix you up.

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

GL

---

### Post by one_ako on 2008-08-26
im willing to try those steps but one little question before i do.

i dont know what nvidia driver to download

thanks

---

### Post by one_ako on 2008-08-26
also after trying envy again it messed me up by only giving me 640x800 resolution.

i went to hardware drivers and enabled the card and it started downloading drivers again. it seemed like legacy drivers...

so now im back to normal resolution but when i try to select extra graphics it says composite extension is not available.

runing compiz checks tells me this

```
Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Composite manually disabled 

Would you like to know more? (Y/n) y

 It has been detected that the "Composite" option of your /etc/X11/xorg.conf
 has been set to "Disable" 

 Open the file being root and change "Disable" to "Enable"
 Then restart X and try again. 

ortez@ortez-desktop:~$ 
```

how do i change that "disable" to "enable"?

---

### Post by starcannon on 2008-08-26
> **one_ako said:**
> im willing to try those steps but one little question before i do.

i dont know what nvidia driver to download

thanks

This one should do the trick:
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run)

GL pm me if you get into trouble with the guide, I have time tonight, I could even be convinced to remote in and help you if needed.

---

### Post by one_ako on 2008-08-26
thank you my good man.

ill go do this right now.

---

### Post by one_ako on 2008-08-26
so im on my laptop now...hehe..

i followed all the steps. downloaded the driver to home folder and went through all the steps. 

i did the part in the end again so it can re do it but it tells me "command not found"

what do i do?

---

### Post by starcannon on 2008-08-27
remoted in, he's all fixed now.

---

### Post by one_ako on 2008-08-27
yup star cannon went in...original problem is done but we are working on another one..

---

