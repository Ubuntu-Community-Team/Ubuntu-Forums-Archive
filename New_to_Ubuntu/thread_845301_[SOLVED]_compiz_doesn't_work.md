---
title: "[SOLVED] compiz doesn't work"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by novatotal on 2008-06-30
don't know why I can't get compiz to work, tried everything but no luck,
even ended having to do a reinstall because I broke xorg.conf trying to get it to work; mine is a desktop, and the specs are in my sig.
everywhere I read of people with similar machines and compiz running smothly, so I don't get it, any help is welcome.
I am starting to think it, has something to do, with mine being a desktop and not a laptop.

emachines intel pentiumd 925 3.0Ghz/2x2MBL2 cache/800 Mhz FSB, SATA 320GB/7200 RPM/8 MB cache, 1GB DDR2, intel GMA 950PCI slot free, LCD 17"

---

### Post by Canis familiaris on 2008-06-30
Is Direct Rendering Enabled?
Check it by the output of:

```
glxinfo | grep direct
```

---

### Post by novatotal on 2008-06-30
yes it is enabled, followed several how tos to no avail, other than breaking my xorg.conf and doing a complete reinstall(formated everything)

---

### Post by anewguy on 2008-06-30
Okay - a few dumb questions:

(1) Can you post the entire output of glxinfo back here?

(2) Does "Advanced Desktop Settings" show under System/Preferences?

(3) When in a terminal window, if you type "compiz" what is the output?

---

### Post by novatotal on 2008-06-30
1) here it is
eduardo@eduardo-desktop:~$ glxinfo | grep direct
direct rendering: Yes
eduardo@eduardo-desktop:~$

2) no

2) this
eduardo@eduardo-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x720) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
any  idea? and thanks in advance even if it doesn't work

I'm running on hardy

---

### Post by blazercist on 2008-06-30
looks like a problem with the settings in the scale plugin, don't know why that would be there, but i would suggest reinstalling compiz and compiz-plugins packages. see if that helps.

---

### Post by anewguy on 2008-06-30
Could you post back the entire output of just glxinfo, without the grep - want to see if it says anything about certain things not being supported.

Also - what type of video adapter do you have?  Is it using the built-in from the chipset?  Do you have the drivers installed for it?

All dumb question, I know, and I don't claim to be an expert.  I just remember some of the things I had to check before I could use compiz.

---

### Post by novatotal on 2008-06-30
thank you ; you mean uninstall and then reinstall?

---

### Post by blazercist on 2008-06-30
```

sudo apt-get install --reinstall compiz compiz-plugins

```

should work.

---

### Post by novatotal on 2008-06-30
heres the out put

eduardo@eduardo-desktop:~$ glxinfo
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

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
0x5f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
eduardo@eduardo-desktop:~$ 

 as for the drivers dont know didn't install anything, and what is a video adapter?

---

### Post by anewguy on 2008-06-30
I think you also need to install something - check in synaptic package manager and see if you have the following installed:

compiz_settings_manager

I don't remember for sure, but I think it is what puts the entry for Advanced Desktop Effects on the System/Prefences menu.  Once you have that entry, you can config compiz for those things you want - the cube, floppy windows, etc..


EDIT:  Also be sure you've installed the compiz plugins via synaptic

---

### Post by anewguy on 2008-06-30
Well, if you didn't install a video driver, that may or may not have something to do with it.  In your xorg.conf file, what does it say for adapter?  I'm going to assume from the description of your PC it might be using the internal Intel 945 graphics, but try this in a terminal and post back:

lspci

---

### Post by blazercist on 2008-06-30
its called compizconfig-settings-manager

its also quite useless unless compiz is actually running.  Yea he may need the drivers for that onboard card.

---

### Post by novatotal on 2008-06-30
here's what is installed as far as compiz 
compiz 1:0.7.4-0ubuntu7
compizconfig-backend-gconf 0.7.4 Oubuntu1
compiz core 1:0.7.4-0ubuntu7 
compiz-fusion-plugins-extra 0.7.4-0ubuntu1
compiz-fusion-plugins-main 0.7.4-Oubuntu5
compiz-gnome 1:0.7.4 Oubuntu7
compiz-plugins 1:0.7.4 Oubuntu7 
libcompizconfig0 0.7.4 Oubuntu1
libdecoration0 1:0.7.4 Oubuntu7

and thats all

---

### Post by anewguy on 2008-06-30
So maybe a better question would be - what makes you think compiz isn't running?  If you do ps -e in a terminal, do you see entries for things like compiz, compiz-decorations, etc.?  If you don't think it's running because you can't see the cube, etc., you could be in error.  You'll need multiple work spaces, and in this case you DO need the configuration utility in order to be sure the cube is checked, etc..

---

### Post by philinux on 2008-06-30
Have a look in system>admin>hardware drivers.

What you got in there.

---

### Post by anewguy on 2008-06-30
Go ahead and install the configuration utility.

---

### Post by novatotal on 2008-06-30
sorry for the long paste but didn't find any "adapter"

eduardo@eduardo-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:05.0 Communication controller: Conexant Unknown device 2f40
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
eduardo@eduardo-desktop:~$

---

### Post by novatotal on 2008-06-30
> **philinux said:**
> Have a look in system>admin>hardware drivers.

What you got in there.

nothing, it is empty

anewguy: ok compizconfig-settings-manager installed via synaptic

---

### Post by anewguy on 2008-06-30
The only video adapter it shows is:

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)


I'm not familiar with the on board graphics, so perhaps someone else watching/commenting here can help you be sure the driver is installed.

---

### Post by novatotal on 2008-06-30
last time I did install some driver, but it caused my hardy to beheave strange; slow response time

---

### Post by anewguy on 2008-06-30
> **novatotal said:**
> nothing, it is empty

anewguy: ok compizconfig-settings-manager installed via synaptic

(1) the 945G may be recognized by Ubuntu in which case a special driver would not show in the drivers page

(2) what did the ps -e show for compiz?

---

### Post by novatotal on 2008-06-30
> **anewguy said:**
> (1) the 945G may be recognized by Ubuntu in which case a special driver would not show in the drivers page

(2) what did the ps -e show for compiz?

ps -? what is that?

activated cube and other stuf on compiz manager, firefox froze, forced to exit did a reboot, still nothing, activated extras on system/apearance, firefox froze forced to exit and another reboot, still nothing

---

### Post by anewguy on 2008-06-30
The ps -e in a terminal window will show all the processes running on your system.  Check the output and look to be sure compiz, compiz decorations, etc., are showing in that list.

Also, if you forget about Firefox for now, does the flame, wobbly windows, or any of those other effects do anything on your desktop?

Be sure you have at least 4 desktop workspaces defined, then place your mouse in a blank space on the desktop, hold down the ctrl and alt keys and while holding them down hold down the left mouse button and move your mouse - what happens?

---

### Post by novatotal on 2008-06-30
out put of ps -e

eduardo@eduardo-desktop:~$ ps-e
bash: ps-e: orden no encontrada
eduardo@eduardo-desktop:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   46 ?        00:00:00 kblockd/0
   47 ?        00:00:00 kblockd/1
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  130 ?        00:00:00 kseriod
  170 ?        00:00:00 pdflush
  171 ?        00:00:00 pdflush
  172 ?        00:00:00 kswapd0
  213 ?        00:00:00 aio/0
  214 ?        00:00:00 aio/1
 1424 ?        00:00:00 ksuspend_usbd
 1425 ?        00:00:00 khubd
 1546 ?        00:00:00 ata/0
 1549 ?        00:00:00 ata/1
 1550 ?        00:00:00 ata_aux
 2046 ?        00:00:00 scsi_eh_0
 2050 ?        00:00:00 scsi_eh_1
 2286 ?        00:00:00 scsi_eh_2
 2287 ?        00:00:00 usb-storage
 2295 ?        00:00:00 scsi_eh_3
 2296 ?        00:00:00 scsi_eh_4
 2487 ?        00:00:00 kjournald
 2690 ?        00:00:00 udevd
 3104 ?        00:00:00 kpsmoused
 4181 ?        00:00:00 kjournald
 4452 tty4     00:00:00 getty
 4453 tty5     00:00:00 getty
 4455 tty2     00:00:00 getty
 4458 tty3     00:00:00 getty
 4459 tty6     00:00:00 getty
 4639 ?        00:00:00 acpid
 4668 ?        00:00:00 kondemand/0
 4669 ?        00:00:00 kondemand/1
 4760 ?        00:00:00 syslogd
 4816 ?        00:00:00 dd
 4818 ?        00:00:00 klogd
 4840 ?        00:00:00 dbus-daemon
 4856 ?        00:00:00 NetworkManager
 4870 ?        00:00:00 NetworkManagerD
 4883 ?        00:00:00 system-tools-ba
 4903 ?        00:00:00 avahi-daemon
 4904 ?        00:00:00 avahi-daemon
 4945 ?        00:00:00 cupsd
 5011 ?        00:00:00 dhcdbd
 5030 ?        00:00:00 hald
 5033 ?        00:00:00 console-kit-dae
 5095 ?        00:00:00 hald-runner
 5115 ?        00:00:00 hald-addon-cpuf
 5116 ?        00:00:00 hald-addon-acpi
 5120 ?        00:00:00 hald-addon-inpu
 5136 ?        00:00:00 hald-addon-stor
 5138 ?        00:00:00 hald-addon-stor
 5140 ?        00:00:00 hald-addon-stor
 5142 ?        00:00:00 hald-addon-stor
 5145 ?        00:00:00 hald-addon-stor
 5172 ?        00:00:00 hcid
 5190 ?        00:00:00 btaddconn
 5191 ?        00:00:00 btdelconn
 5202 ?        00:00:00 bluetoothd-serv
 5203 ?        00:00:00 bluetoothd-serv
 5209 ?        00:00:00 krfcommd
 5247 ?        00:00:00 gdm
 5250 ?        00:00:00 gdm
 5254 tty7     00:00:35 Xorg
 5315 ?        00:00:00 atd
 5334 ?        00:00:00 cron
 5418 tty1     00:00:00 getty
 5421 ?        00:00:00 dhclient
 5513 ?        00:00:00 gconfd-2
 5515 ?        00:00:00 gnome-keyring-d
 5516 ?        00:00:00 x-session-manag
 5619 ?        00:00:00 seahorse-agent
 5623 ?        00:00:00 dbus-daemon
 5624 ?        00:00:00 gnome-settings-
 5632 ?        00:00:02 pulseaudio
 5635 ?        00:00:00 gconf-helper
 5649 ?        00:00:00 gnome-screensav
 5654 ?        00:00:00 compiz
 5656 ?        00:00:02 gnome-panel
 5657 ?        00:00:01 nautilus
 5659 ?        00:00:00 bonobo-activati
 5669 ?        00:00:00 gvfsd
 5695 ?        00:00:00 gvfs-fuse-daemo
 5728 ?        00:00:05 compiz.real
 5729 ?        00:00:00 bluetooth-apple
 5732 ?        00:00:00 update-notifier
 5737 ?        00:00:00 tracker-applet
 5739 ?        00:00:00 evolution-alarm
 5742 ?        00:00:00 trackerd
 5745 ?        00:00:00 nm-applet
 5746 ?        00:00:00 python
 5749 ?        00:00:00 gnome-power-man
 5752 ?        00:00:00 gnome-volume-ma
 5754 ?        00:00:00 gvfsd-burn
 5759 ?        00:00:00 trashapplet
 5764 ?        00:00:00 gvfsd-trash
 5789 ?        00:00:00 mixer_applet2
 5792 ?        00:00:00 fast-user-switc
 5798 ?        00:00:00 sh
 5799 ?        00:00:00 compiz-decorato
 5801 ?        00:00:00 gtk-window-deco
 5940 ?        00:00:24 firefox
 6159 ?        00:00:00 gnome-terminal
 6162 ?        00:00:00 gnome-pty-helpe
 6163 pts/0    00:00:00 bash
 6185 pts/0    00:00:00 ps
eduardo@eduardo-desktop:~$ 

how do I define desktops?

---

### Post by anewguy on 2008-06-30
Also - be sure any previous attempted video drivers are removed - use synaptic and look to be sure such things as xorg-driver-fglrx, etc., are not installed.  You may also need to reinstall the libgl1-mesa-glx package.

Further searching on the web makes me think you will need to install the driver for your 945 graphics.  Try doing a search in this forum with intel 945 and see if it returns some things for you to look at.

---

### Post by anewguy on 2008-06-30
The line:

5654 ? 00:00:00 compiz


indicates that compiz itself is running.  We just need to find out if any of the effects work or if we need to have you install the video driver first (I'm leaning towards the driver).

If you look under System/Preferences/Hardware Information, what do you see listed for the 945 graphics?

---

### Post by novatotal on 2008-06-30
> **anewguy said:**
> Also - be sure any previous attempted video drivers are removed - use synaptic and look to be sure such things as xorg-driver-fglrx, etc., are not installed.  You may also need to reinstall the libgl1-mesa-glx package.

Further searching on the web makes me think you will need to install the driver for your 945 graphics.  Try doing a search in this forum with intel 945 and see if it returns some things for you to look at.

no other driver, this is a fresh install, formated everything
to reinstall it do I use apt-get or aptitude?

---

### Post by novatotal on 2008-06-30
> **anewguy said:**
> The ps -e in a terminal window will show all the processes running on your system.  Check the output and look to be sure compiz, compiz decorations, etc., are showing in that list.

Also, if you forget about Firefox for now, does the flame, wobbly windows, or any of those other effects do anything on your desktop?

Be sure you have at least 4 desktop workspaces defined, then place your mouse in a blank space on the desktop, hold down the ctrl and alt keys and while holding them down hold down the left mouse button and move your mouse - what happens?

the desktop image moves(rotates)
still don't know how to define the 4 desktops you mentioned

---

### Post by anewguy on 2008-06-30
> **novatotal said:**
> the desktop image moves(rotates)
still don't know how to define the 4 desktops you mentioned

In the lower right side of your screen should be a little box.  Right click on it and select preferences.  A Window will pop up saying how many desktops you have defined - make sure it is at least 4.  Then try the ctl/alt/left mouse thing again and see if you have a cube that moves around as you move your mouse.

---

### Post by novatotal on 2008-06-30
hey figured out the defining issue by my self!!!! now I do have the cube and everithing else!!! thank you all!!! consider this thread solved!!!!! it was just a configurying issue, nothing wrong with the driver or the gma950!!!!! thank you all!!!!

---

### Post by beanhead on 2008-06-30
Ok lets try this the easy way, have you tried compiz check ?

just copy and paste in your terminal

You can use this command to download it to your home directory:

wget [http://blogage.de/files/4359/download](http://blogage.de/files/4359/download) -O compiz-check


Afterwards, you have to make it executable:

chmod +x compiz-check


And finally run it like this:

./compiz-check

thats from the compiz website here is the link for the check

[http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)

there are also walkthroughs in the compiz website
and they clarify what will work and what wont when it comes to drivers.

Compiz.org link    

[http://compiz.org/Documentation/Documentation](http://compiz.org/Documentation/Documentation)

Hope it helps, made it simple for me :)

---

### Post by anewguy on 2008-06-30
Glad to have been of help.

---

