---
title: "Graphics card"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-05-18
Someone told me my graphics card is not supported... could i get some assistance ???

---

### Post by Joeb454 on 2008-05-18
Could you tell us what Graphics Card you have?

It'd help if we knew ;)

---

### Post by pikabuntu on 2008-05-18
> **Joeb454 said:**
> Could you tell us what Graphics Card you have?

It'd help if we knew ;)

how could i find out :)

---

### Post by shifty_powers on 2008-05-18
heh, is it a laptop or desktop for a start?

---

### Post by pikabuntu on 2008-05-18
laptop

---

### Post by shifty_powers on 2008-05-18
```
sudo dmidecode | more
```

post the out put of that ;)

---

### Post by Joeb454 on 2008-05-18
True the above would narrow it down a lot, also can you please open a terminal (Applications > Accessories) and post the output of the command ```
lspci
```

---

### Post by shifty_powers on 2008-05-18
or that would make more sense i suppose ;)

---

### Post by pikabuntu on 2008-05-18
> **shifty_powers said:**
> ```
sudo dmidecode | more
```

post the out put of that ;)

# dmidecode 2.9
SMBIOS 2.3 present.
44 structures occupying 1332 bytes.
Table at 0x000DF010.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Phoenix Technologies Ltd.
	Version: KA.M1.34 
	Release Date: 12/17/2002
	Address: 0xE5380
	Runtime Size: 109696 bytes
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
--More--

---

### Post by pikabuntu on 2008-05-18
> **Joeb454 said:**
> True the above would narrow it down a lot, also can you please open a terminal (Applications > Accessories) and post the output of the command ```
lspci
```

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by shifty_powers on 2008-05-18
heh sorry dude. my bad.

two things, that command gives you a LOT of information, and you need to scroll down to acess it all.

right now, joeb's suggestion of lspci in a terminal and posting that would probably be better ;)

---

### Post by shifty_powers on 2008-05-18
heh well, looked up that chip, otherwise knwon as igp 320m.

heh, thats quite old, and may struggle with compiz.

try using envy to get the right driver for it.

```
sudo apt-get install envyng-gtk
```

then go applications>system tools>envy

---

### Post by pikabuntu on 2008-05-18
lpci:

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by shifty_powers on 2008-05-18
heh, think we get the idea for lspci ;)

---

### Post by pikabuntu on 2008-05-18
> **shifty_powers said:**
> heh, think we get the idea for lspci ;)

sorry accident :)

someone had me try envy before and it messed my computer up

---

### Post by Joeb454 on 2008-05-18
> **pikabuntu said:**
> 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

That is the line you are looking for - You have an ATI Radeon card :) Most ATI cards are compatible, though they can be a little more problematic than Nvidia (this may well change in future).

---

### Post by shifty_powers on 2008-05-18
> **Joeb454 said:**
> That is the line you are looking for - You have an ATI Radeon card :) Most ATI cards are compatible, though they can be a little more problematic than Nvidia (this may well change in future).

looked that one up like i said, also called igp 320m, and maybe the situation has changed, but it seemed to give people a lot of problems in linux and ubuntu. still think it is worth him trying envy, get the right drivers and then seeing how it goes ;)

---

### Post by pikabuntu on 2008-05-18
ok, im going to try envy then...

---

### Post by Joeb454 on 2008-05-18
Let us know how it goes :)

---

### Post by pikabuntu on 2008-05-18
I got an error:

Envy does not recognise your card as compatible with any version of the driver.

---

### Post by shifty_powers on 2008-05-18
heh, thats not a good sign.

```
glxinfo
```

can you post the output of the that and run

```
glxgears
```

and tell us what kind of socre you get?

---

### Post by shifty_powers on 2008-05-18
btw, the threads i saw indicated that your grpahics chipset does not work very well, if at all, in ubuntu...

---

### Post by pikabuntu on 2008-05-18
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x55 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by pikabuntu on 2008-05-18
1042 frames in 5.0 seconds = 208.179 FPS
2744 frames in 5.0 seconds = 548.214 FPS
7934 frames in 5.0 seconds = 1582.166 FPS
11504 frames in 5.0 seconds = 2297.824 FPS
12051 frames in 5.0 seconds = 2410.162 FPS
10662 frames in 5.0 seconds = 2128.688 FPS
7635 frames in 5.0 seconds = 1523.497 FPS
6062 frames in 5.0 seconds = 1211.656 FPS
14596 frames in 5.0 seconds = 2919.094 FPS
11685 frames in 5.0 seconds = 2335.932 FPS
9643 frames in 5.0 seconds = 1928.553 FPS
15327 frames in 5.1 seconds = 3018.184 FPS
16262 frames in 5.0 seconds = 3252.332 FPS
16528 frames in 5.0 seconds = 3305.495 FPS

---

### Post by shifty_powers on 2008-05-18
what about th score in glxgears?

i get 4000-500 fps...

---

### Post by pikabuntu on 2008-05-18
what do you mean?

---

### Post by shifty_powers on 2008-05-18
> **pikabuntu said:**
> 1042 frames in 5.0 seconds = 208.179 FPS
2744 frames in 5.0 seconds = 548.214 FPS
7934 frames in 5.0 seconds = 1582.166 FPS
11504 frames in 5.0 seconds = 2297.824 FPS
12051 frames in 5.0 seconds = 2410.162 FPS
10662 frames in 5.0 seconds = 2128.688 FPS
7635 frames in 5.0 seconds = 1523.497 FPS
6062 frames in 5.0 seconds = 1211.656 FPS
14596 frames in 5.0 seconds = 2919.094 FPS
11685 frames in 5.0 seconds = 2335.932 FPS
9643 frames in 5.0 seconds = 1928.553 FPS
15327 frames in 5.1 seconds = 3018.184 FPS
16262 frames in 5.0 seconds = 3252.332 FPS
16528 frames in 5.0 seconds = 3305.495 FPS

well those scores are fluctuating quite a bit, but seem fine.

it is a test of your drivers and graphics card, albeit a crude one.

do you have any issues if you have compiz running?

---

### Post by pikabuntu on 2008-05-18
ummm..... how do i get compiz running?

---

### Post by shifty_powers on 2008-05-18
heh, well thats a whole nother ball game...

what version of ubuntu you using btw?

(ubunutu, kubuntu, xubunut etc.. and what eiditon, 7.10 8.04 etc...)

---

### Post by pikabuntu on 2008-05-18
> **shifty_powers said:**
> heh, well thats a whole nother ball game...

what version of ubuntu you using btw?

(ubunutu, kubuntu, xubunut etc.. and what eiditon, 7.10 8.04 etc...)

ubuntu 8.04

---

### Post by pikabuntu on 2008-05-18
uh, i don't know if this will help any, but desktop effects worked when i had 7.10 running, but not with 8.04

(this whole thing started because im trying to get avant window navigator to work..)

---

### Post by pikabuntu on 2008-05-18
sorry for putting u guys thru all of the trouble but someone told me to use metacity + it worked...

---

### Post by shifty_powers on 2008-05-18
heh yeah io saw the thread.

and i'm glad you got it all sorted.

anyways, this is how you learn ;)

---

### Post by nowin4me on 2008-05-18
> **shifty_powers said:**
> 
and i'm glad you got it all sorted.
anyways, this is how you learn ;)

Darn right:lolflag::-({|=

---

### Post by Eric Qel-Droma on 2008-06-26
I also have the impossibly powerful IGP 320M, but I have no idea what I need metacity for.  It is a "window manager".  What is that?  The stuff I saw when I Googled it looked like... windows and stuff.

I mainly want to make sure I'm getting the most out of the pathetic hardware I have, and I feel like I'm scraping the bottom of the barrel with what I'm seeing right now in Ubuntu.  However, my Ubuntu is running 100x faster than XP ever did on this pathetic laptop.  Would this metacity thing slow down my system?

Thanks!

---

