---
title: "Graphics card/driver problem"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by XDPirate on 2008-05-04
Hai guize.

I'm a devout Ubuntu fan, but since my old, deprecated computer without an internal cdrom drive refuses to install it, I installed openSuSE 10.3 (don't kill me). Here's my problem, I think you should be able to help even though this doesn't directly relate to ubuntu, but i've tried numerous other forums, and didnt get any responses:

I have an Acer Aspire 1350 laptop with an integrated graphics card (VIA KM400). I know it supports 3D and OpenGL etc, because back in the days I ran windows, i had no problems with 3d. Problem is, I can't get it to work. I've tried manually editing the xorg.conf file, i've tried installing openchrome (opensource driver for the card), i've tried lots of stuff, but it just won't work.

Graphic proof:
[img]http://djlarz.bzfiles.net/screenshot1.png[/img]

Indeed, my graphics card DOES support 3d, and i CAN'T configure it, because SaX2 and xorgconf wont let me. Anyone, help please?

Thanks in advance, I miss 3D. :(

---

### Post by Glaxed on 2008-05-04
Can you post your device section of the xorg.conf (kate /etc/X11/xorg.conf)?
And what does glxinfo | grep direct output?

(PS- Suse. Really? :lolflag:)

---

### Post by XDPirate on 2008-05-04
xorg.conf:

```
Section "Device"
  BoardName    "Aspire 1353LC KM400"
  BusID        "1:0:0"
  Driver       "via"
  Identifier   "Device[0]"
  Option       "VBEModes" "true"
  Screen       0
  VendorName   "Acer"
EndSection
```

glxinfo:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_SGIX_fbconfig GLX_SGIX_pbuffer
server glx version string: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_SGIX_fbconfig GLX_SGIX_pbuffer
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
client glx vendor string: SGI
client glx version string: 1.2
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_shadow, GL_ARB_shadow_ambient,
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_blend_color, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 16 tc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2b 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2c 16 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x2d 16 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow

```

glxinfo | grep direct:
```
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

(PS.: Ya rly :) )

---

### Post by overdrank on 2008-05-04
> **XDPirate said:**
> Hai guize.

I'm a devout Ubuntu fan, but since my old, deprecated computer without an internal cdrom drive refuses to install it, I installed openSuSE 10.3 (don't kill me). Here's my problem, I think you should be able to help even though this doesn't directly relate to ubuntu, but i've tried numerous other forums, and didnt get any responses:

I have an Acer Aspire 1350 laptop with an integrated graphics card (VIA KM400). I know it supports 3D and OpenGL etc, because back in the days I ran windows, i had no problems with 3d. Problem is, I can't get it to work. I've tried manually editing the xorg.conf file, i've tried installing openchrome (opensource driver for the card), i've tried lots of stuff, but it just won't work.

Graphic proof:
[img]http://djlarz.bzfiles.net/screenshot1.png[/img]

Indeed, my graphics card DOES support 3d, and i CAN'T configure it, because SaX2 and xorgconf wont let me. Anyone, help please?

Thanks in advance, I miss 3D. :(

HI and yes in windows you probably did have 3d. But VIA is not supporting linux very well. But you may find some help here
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

### Post by starcannon on 2008-05-04
Change this:
> 
Section "Device"
  BoardName    "Aspire 1353LC KM400"
  BusID        "1:0:0"
  Driver       "via"
  Identifier   "Device[0]"
  Option       "VBEModes" "true"
  Screen       0
  VendorName   "Acer"
EndSection

to look like this:
```

Section "Device"
  BoardName    "Aspire 1353LC KM400"
  BusID        "1:0:0"
  Driver       "openchrome"
  Identifier   "Device[0]"
  Option       "VBEModes" "true"
  Screen       0
  VendorName   "Acer"
EndSection
```

That will get you a little ways.
VIA has also put out an official 3d accelerated driver, not sure if it will work for your chipset or not, but they can be found at [http://www.linux.via.tw.com](http://www.linux.via.tw.com) GL

---

### Post by XDPirate on 2008-05-04
> **starcannon said:**
> Change this:


to look like this:
```

Section "Device"
  BoardName    "Aspire 1353LC KM400"
  BusID        "1:0:0"
  Driver       "openchrome"
  Identifier   "Device[0]"
  Option       "VBEModes" "true"
  Screen       0
  VendorName   "Acer"
EndSection
```

That will get you a little ways.
VIA has also put out an official 3d accelerated driver, not sure if it will work for your chipset or not, but they can be found at [http://www.linux.via.tw.com](http://www.linux.via.tw.com) GL

Editing the xorg.conf file ****** up everything. When I rebooted, no x server was started, and i tried starting one manually but it refused, so I had to have sax2 make one and reset my configuration to what it previously was.

Trying overdrank's suggestion now, will post in a few mins when I've tested it.

Thanks.

---

### Post by XDPirate on 2008-05-04
That didn't work either, because it didn't support my chipset..

I've read somewhere that the current version of the via driver doesnt support 3d, but has previously. Is it possible to use a previous version of the driver?

Any other suggestions of how I would go about making this work? all help appreciated.

---

### Post by starcannon on 2008-05-04
If you are stuck at a command line you'll need to use nano or vi to set it back to via.
```

sudo nano /etc/X11/xorg.conf

```

---

### Post by XDPirate on 2008-05-04
> **starcannon said:**
> If you are stuck at a command line you'll need to use nano or vi to set it back to via.
```

sudo nano /etc/X11/xorg.conf

```

Yeah, I've sat it back to via now, but what should I do next?

---

### Post by starcannon on 2008-05-04
I'd probably try installing the openchrome drivers, though I'm unsure how to do it using suse was it? then setting it back to openchrome again.

---

### Post by XDPirate on 2008-05-05
> **starcannon said:**
> I'd probably try installing the openchrome drivers, though I'm unsure how to do it using suse was it? then setting it back to openchrome again.

I've already done that, and as I said earlier, it crashed and wouldnt make an x server at startup..

---

