---
title: "OpenGL programming?"
date: 2006-03-06
forum: Programming Talk
---

### Post by Zdravko on 2006-03-06
What do I need, when I have to do a simple OpenGL application under Ubuntu? g++ is already installed. I guess I need 2 things:
1. Headers
2. Runtime libraries to link the executable against

---

### Post by hod139 on 2006-03-06
```
sudo apt-get install build-essential libgl1-mesa-dev
```

and optionally if you want glut

```
sudo apt-get install libglut3-dev
```

---

### Post by Zdravko on 2006-03-06
hod139, why installing mesa? Isn't this a software emulation for OpenGL directives? I would really like to use a simple (yet fast) 2d visualization. MESA does this? 
And why this "build-essential", as I already installed it (g++ is working, as with STL).
What is GLUT good for?

---

### Post by hod139 on 2006-03-06
[quote=Zdravko]hod139, why installing mesa? Isn't this a software emulation for OpenGL directives? [/quote] "Mesa is a 3-D graphics library with an API which is very similar to that of OpenGL. On Linux, this library is also known as libGL or libGL.so.1."

> 
I would really like to use a simple (yet fast) 2d visualization. MESA does this? 
 For 2D, I would suggest SDL. MESA does this, if by MESA you mean "A free implementation of the OpenGL API" and you write an OpenGL 2D application.

> 
And why this "build-essential", as I already installed it (g++ is working, as with STL).  build-essential installs everything needed to build and link programs.  

> 
What is GLUT good for? GLUT is a basic windowing API for OpenGL. I should add to the previous post, that another optional package to install is libglu1-mesa-dev, which includes headers and static libraries for compiling programs with GLU. GLU is a set of extensions to OpenGL.

---

### Post by richardhp on 2006-03-06
I don't know much, but I do know what worked for me.

I downloaded the Mesa Tars from the Mesa site after trying to get the packages to work and failing. I then used "make" etc. to build the libraries, then "make install" to get it all installed onto the system. I then copied the header files (included in the tar) using "sudo cp /home/desktop/mesa/headers/* /usr/include/GL/" after creating the folder in include using "sudo mkdir /usr/include/GL" or where ever the include files are for C. You then either need gcc or g++ to compile the files.

OpenGL is good for 2D as well as 3D and I have no idea what the GLUT does but I installed it anyway in case I needed it.

If you really want to know then I suggest going to the OpenGL site at [www.opengl.org](www.opengl.org)

Good Luck

NB, good idea to have either SDL or GTK installed. makes building the windows much easier

---

### Post by hod139 on 2006-03-06
There is no reason to download the Mesa tars and install manually.  Everything you need is in the repositories.

---

### Post by Zdravko on 2006-03-07
Without installing anything I just type glxgear and a window with some machinery appeared. The weels were rotating too slowly - perhaps I need some driver for my videocard?
When I run glxinfo I got:
> 

name of display: :0.0
display: :0 screen: 0
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
GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
GLX_SGIX_visual_select_group
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

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
0x23 24 tc 0 24 0 r y . 8 8 8 0 0 16 0 0 0 0 0 0 0 None
0x24 24 tc 0 24 0 r y . 8 8 8 0 0 16 8 16 16 16 0 0 0 None
0x25 24 tc 0 32 0 r y . 8 8 8 8 0 16 8 16 16 16 16 0 0 None
0x26 24 tc 0 32 0 r . . 8 8 8 8 0 16 8 16 16 16 16 0 0 None
0x27 24 dc 0 24 0 r y . 8 8 8 0 0 16 0 0 0 0 0 0 0 None
0x28 24 dc 0 24 0 r y . 8 8 8 0 0 16 8 16 16 16 0 0 0 None
0x29 24 dc 0 32 0 r y . 8 8 8 8 0 16 8 16 16 16 16 0 0 None
0x2a 24 dc 0 32 0 r . . 8 8 8 8 0 16 8 16 16 16 16 0 0 None


I am thinking of using MESA. Is it easy to program with it?

---

### Post by hod139 on 2006-03-07
Your video card drivers are not set up correctly.

Line 3: [B]direct rendering: No
[/B]basically says that you do not have hardware 3D support. If you have an Nvidia or ATI card, the forums have howtos for setting both up.

> 
 I am thinking of using MESA. Is it easy to program with it?

For all intents and purposes:  MESA == OpenGL

Mesa is technically a "free implementation of the OpenGL API". If you have programmed using SGI's OpenGL, then you will find Mesa's implementatin easy to program with (seeing how it is a clone). If you have never programmed in OpenGL before, it can be tricky setting up 2D projections like you said you wanted before. For a reference, I suggest the "[Red Book]("http://www.opengl.org/documentation/red_book_1.0/")".  The publishers of the book have kindly put up version 1.0 online for free as well.

---

### Post by Zdravko on 2006-03-07
I set my videocard correctly. Now I have some questions... It appears that the OpenGL API has a main loop function, which once entered never leaves until the end of application. Very cool - now my I/O and flowing logic is blocked. Do you know some easy (best C++) way to separate the (re)drawing from the main program? Maybe I should use some kind of threads? Or MessageDispatcher system?

---

### Post by hod139 on 2006-03-07
OpenGL does not have a main loop function.  I'm assuming you must be using GLUT?  If you use GLUT, you must transfer control to the GLUT event loop.  There is no return from glutMainLoop().  What do you mean "now my I/O and flowing logic is blocked."  GLUT is designed using callback functions, so you can register a callback to perform what you need, and tell GLUT when and how to use it.   A small GLUT example can be found here: [http://graphics.stanford.edu/courses/cs248-00/helpsession/opengl/code_example.html](http://graphics.stanford.edu/courses/cs248-00/helpsession/opengl/code_example.html)
If you want, you can even set up a model-view-controller framework: [http://www.designlab.ku.edu/~miller/Courses/672/BoilerplatePrograms/](http://www.designlab.ku.edu/~miller/Courses/672/BoilerplatePrograms/) (see Part2)

---

### Post by Zdravko on 2006-03-08
hod139, the problem is that there is no way to separate the drawing from the main application. I tried GLUT and noticed it - once entered this loop, the rest of the program isn't available. The callbacks are connected with the visualization, which doesn't work for me. In C++ everything is a separate object - the main logic (including I/O) and the graphical visualization are two different things. I want to have a large object that controlls the graphics but also provides I/O etc simultanously. It seems that GLUT doesn't allow this...

---

### Post by hod139 on 2006-03-08
Check out the Model-View-Controller GLUT example [http://www.designlab.ku.edu/~miller/...platePrograms/]("http://www.designlab.ku.edu/%7Emiller/Courses/672/BoilerplatePrograms/") (Part 2) I posted in my earlier link.  The idea is to break apart the underlying model from the the GUI view/representation and allow controllers to change the model.

You're right in that the OpenGL API is non-OO, but there are ways to do it.  Hope that helps.

---

### Post by Zdravko on 2006-03-08
hod139, I checked that site. The 2nd parts really sounds interesting. But I expected something a little bit more general. As far as I can see in the source, the main program logic is still very strong binded to the OpenGL. Further more the example doesn't compile :(

---

