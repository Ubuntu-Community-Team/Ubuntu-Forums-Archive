---
title: "How to upgrade OpenGL?"
date: 2016-05-30
forum: New to Ubuntu
---

### Post by EssexEagle on 2016-05-30
When I launch SuperTuxKart I get the following warning:
> Your OpenGL version appears to be too old.  Please verify if an update for your video driver is available.  SuperTuxKart requires OpenGL 3.1 or better.

How do I update this?  I've tried Googling but have got a bit lost...  (Please bear in mind I know NOTHING about video drivers.)

Hopefully useful information:
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
$ glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 
OpenGL version string: 2.1 Mesa 11.2.0
OpenGL shading language version string: 1.20
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 11.2.0
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:
```

---

### Post by mastablasta on 2016-05-30
> Intel® 4 Series Express Chipsets support OpenGL version 2.0 and some extensions from OpenGL 2.1 (Pixel Buffer Objects) and OpenGL 3.0 (Frame Buffer Objects, floating point textures and half float pixels).
[SIZE=2]source: [https://software.intel.com/en-us/articles/opengl-extensions-supported-in-intel-4-series-express-chipsets-and-beyond](https://software.intel.com/en-us/articles/opengl-extensions-supported-in-intel-4-series-express-chipsets-and-beyond). 
OpenGL 4 should be supported. but it could be that it is not enabled.

[SIZE=2]

[http://www.intel.com/content/www/us/en/support/graphics-drivers/000005575.html](http://www.intel.com/content/www/us/en/support/graphics-drivers/000005575.html)

you can try with "Intel Graphics installer for Linux" 
[SIZE=2]

[https://01.org/linuxgraphics](https://01.org/linuxgraphics)


[/SIZE]
- see bottom of this link for more info:

[SIZE=2]

[http://stackoverflow.com/questions/14123895/opengl-glsl-3-3-on-an-hd-graphics-4000-under-ubuntu-12-04](http://stackoverflow.com/questions/14123895/opengl-glsl-3-3-on-an-hd-graphics-4000-under-ubuntu-12-04)


[/SIZE]or oibaf repository (PPA)

edit: i would just like to add that if this is on 16.04 you should already have the latest intel stack. my guess is something is not getting recognies well here. unfortunaltely i do not know about the inte'sl switches and how to enable things if it doesnt' have any GUI available,



[/SIZE]

[/SIZE]

---

### Post by $yl9pAR%t on 2016-05-30
In opposition to mastablasta I will give you bad news in the link below. This is not my experience, just common knowledge.

[https://en.wikipedia.org/wiki/Comparison_of_Intel_graphics_processing_units#Fourth_generation](https://en.wikipedia.org/wiki/Comparison_of_Intel_graphics_processing_units#Fourth_generation)

---

### Post by mastablasta on 2016-05-31
well official sources say otherwise:

> **4th Generation Intel® Core&#8482; Processors**With Iris&#8482; Graphics [5200]("http://www.intel.com/support/graphics/intelirisprographics5200/"), [5100]("http://www.intel.com/support/graphics/intelirisgraphics5100/")
 With Intel® HD Graphics [5000]("http://www.intel.com/support/graphics/intelhdgraphics5000/"), [4600]("http://www.intel.com/support/graphics/intelhdgraphics4600/"), [4400]("http://www.intel.com/support/graphics/intelhdgraphics4400/"), [4200]("http://www.intel.com/support/graphics/intelhdgraphics4200/")
[TABLE]
[TR]
[TD="class: bodycopy, bgcolor: #efefef"]**DirectX***[/TD]
[TD="class: bodycopy, bgcolor: #efefef"]**OpenGL***[/TD]
[TD="class: bodycopy, bgcolor: #efefef"]**OpenCL***[/TD]
[TD="class: bodycopy, bgcolor: #efefef"]**Shader Model Support**[/TD]
[TD="class: bodycopy, bgcolor: #efefef"]**Intel® Quick Sync Video**[/TD]
[TD="class: bodycopy, bgcolor: #efefef"]**Intel® Wireless Display**[/TD]
[TD="class: bodycopy, bgcolor: #efefef"]**Intel® Insider&#8482; technology**[/TD]
[TD="class: bodycopy, bgcolor: #efefef"]**Intel® InTru&#8482; 3D Technology**[/TD]
[TD="class: bodycopy, bgcolor: #efefef"]**Intel® Clear Video HD Technology**[/TD]
[/TR]
[TR]
[TD="class: bodycopy, bgcolor: #ffffff"]11.1[/TD]
[TD="class: bodycopy, bgcolor: #ffffff"]4[/TD]
[TD="class: bodycopy, bgcolor: #ffffff"]1.2[/TD]
[TD="class: bodycopy, bgcolor: #ffffff"]5[/TD]
[TD="class: bodycopy, bgcolor: #ffffff"]Yes[/TD]
[TD="class: bodycopy, bgcolor: #ffffff"]Yes[/TD]
[TD="class: bodycopy, bgcolor: #ffffff"]Yes[/TD]
[TD="class: bodycopy, bgcolor: #ffffff"]Yes[/TD]
[TD="class: bodycopy, bgcolor: #ffffff"]Yes[/TD]
[/TR]
[/TABLE]

source: [SIZE=2]http://www.intel.com/content/www/us/en/support/graphics-drivers/000005524.html


[SIZE=2]to the OP - you can use an older version of supertuxkart if you do not need the latest one.

from the Supertuxkart blog about new engine: 

> [FONT=Arial]Based on our somewhat limited testing the following graphics adapters should be fast enough at low graphics settings (go into settings, video to increase or decrease the graphical details):[/FONT]
[LIST]
[*][FONT="Helvetica Neue"][COLOR=#333333]ATI/AMD Radeon HD 3650[/COLOR] [/FONT][FONT="Helvetica Neue"][/FONT] 
[*][FONT="Helvetica Neue"]Intel HD 3000[/FONT][FONT="Helvetica Neue"][/FONT] 
[*][FONT="Helvetica Neue"][COLOR=#333333]NVIDIA GeForce 8600[/COLOR][/FONT]
[/LIST]

[FONT="Helvetica Neue"]We also recommend your graphics adapter to have at least 1 GB VRAM available when playing. Note that these are estimates and weaker hardware may be able to run the game, but perhaps not at playable framerates. You should also have at least 600MB free hard drive space, 1GB free memory, and a 1.2 GHz processor.[/FONT]

[SIZE=2]http://supertuxkart.blogspot.si/
[/SIZE][B][I][U][SUB][SUP]
[/SUP][/SUB][/U][/I][/B][/SIZE]
[/SIZE]

---

### Post by mc4man on 2016-05-31
> **EssexEagle said:**
> 


How do I update this?  I've tried Googling but have got a bit lost..
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
$ glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 
OpenGL version string: 2.1 Mesa 11.2.0
OpenGL shading language version string: 1.20
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 11.2.0
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:
```

As far as OpenGL  you'd need to get newer hardware, that chipset will not be getting any higher OpenGL support than it already has. (2.1

---

