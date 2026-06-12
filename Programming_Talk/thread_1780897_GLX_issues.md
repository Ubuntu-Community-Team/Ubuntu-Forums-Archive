---
title: "GLX issues"
date: 2011-06-12
forum: Programming Talk
---

### Post by lordio on 2011-06-12
I wrote a program to try to familiarize myself with GLX, and while it works mostly fine on my netbook, it sends out warnings before segfaulting on my VirtualBox. Since the error appears to be with Ubuntu (more specifically, the GLX implementation) and not VB, I've come here.

A minimal program that displays the error:
```
//GLXTest.cpp

#include <X11/Xlib.h>
#include <GL/gl.h>
#include <GL/glx.h>
#include <GL/glxext.h>
#include <cstdio>

int main()
{
    printf("Opening X Display.");
    Display* dpy = XOpenDisplay(NULL);

    int attribs[] = {None};
    int fbConfigRet = 0;
    printf("Getting list of usable GLX FB Configs.");
    GLXFBConfig* fbc = glXChooseFBConfig(dpy,DefaultScreen(dpy),attribs,&fbConfigRet);
    XVisualInfo* xvi = NULL;
    printf("Finding appropriate X Visual Info.");
    for(int iter = 0; (iter < fbConfigRet) && !xvi; iter++) xvi = glxGetVisualFromFBConfig(dpy,fbc[iter]);

    printf("Creating X Colormap.");
    Colormap cmap = XCreateColormap(dpy,DefaultRootWindow(dpy),xvi->visual,AllocNone);
    XSetWindowAttributes xswa;
    xswa.colormap = cmap;
    xswa.event_mask = ExposureMask | KeyPressMask;

    printf("Creating X Window.");
    Window win = XCreateWindow(dpy,DefaultRootWindow(dpy),0,0,640,480,1,xvi->depth,InputOutput,xvi->visual, CWColormap | CWEventMask,&xswa);

    sleep(10);
    XDestroyWindow(dpy,win);
    XCloseDisplay(dpy);
    return 0;
}
```This program prints the following warning each time it runs glXGetVisualFromFBConfig(), with different pointers each time:
```
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0xfe43e0
OpenGL Warning: Retry with 0x8003 returned 0 visuals

```It then segfaults when it tries to create the colormap.

glxinfo prints the following:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: Chromium
server glx version string: 1.3 Chromium
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
client glx vendor string: Chromium
client glx version string: 1.3 Chromium
client glx extensions:
    GLX_ARB_multisample, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
GLX version: 1.3
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: Humper
OpenGL renderer string: Chromium
OpenGL version string: 2.1 Chromium 1.9
OpenGL shading language version string: 4.10 NVIDIA via Cg compiler
OpenGL extensions:
    GL_EXT_texture_compression_s3tc, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_compiled_vertex_array, 
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shadow, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_EXT_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_EXT_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_pixel_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_func_separate, 
    GL_EXT_blend_subtract, GL_EXT_texture_env_add, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_secondary_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture3D, GL_IBM_rasterpos_clip, 
    GL_NV_fog_distance, GL_NV_fragment_program, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_ARB_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, GL_SGIS_generate_mipmap, 
    GL_ARB_shading_language_100, GL_ARB_shader_objects, GL_ARB_vertex_shader, 
    GL_ARB_fragment_shader, GL_EXT_texture_sRGB, GL_EXT_framebuffer_blit, 
    GL_EXT_blend_equation_separate, GL_EXT_stencil_two_side, 
    GL_CR_state_parameter, GL_CR_cursor_position, GL_CR_bounding_box, 
    GL_CR_print_string, GL_CR_tilesort_info, GL_CR_synchronization, 
    GL_CR_head_spu_name, GL_CR_performance_info, GL_CR_window_size, 
    GL_CR_tile_info, GL_CR_saveframe, GL_CR_readback_barrier_size, 
    GL_CR_server_id_sharing, GL_CR_server_matrix,  GL_EXT_stencil_two_side

64 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0c8 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0c9 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ca 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0cb 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0cc 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0cd 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ce 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0cf 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d0 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d1 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d2 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d3 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d4 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d5 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d6 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d7 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d8 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d9 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0da 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0db 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0dc 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0dd 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0de 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0df 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e0 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e1 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e2 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e3 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e4 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e5 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e6 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e7 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e8 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e9 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ea 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0eb 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ec 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ed 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ee 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ef 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f0 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f1 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f2 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f3 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f4 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f5 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f6 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f7 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f8 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f9 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0fa 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0fb 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0fc 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0fd 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0fe 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ff 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x100 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x101 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x102 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x103 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x104 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x105 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x047 32 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None

64 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0c8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0c9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ca 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0cb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0cc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0cd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ce 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0cf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0da 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0db 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0dc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0dd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0de 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0df 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ea 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0eb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ec 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ed 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ee 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ef 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0fa 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0fb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0fc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0fd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0fe 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ff 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x100 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x101 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x102 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x103 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x104 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x105 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x047 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  8  0  0  0  0  1 1 None

```When I try the same program on my netbook, it runs just fine, creates the window (albeit, the window doesn't draw correctly since the GLXContext isn't set up, but that's not the issue), then closes the window after 10 seconds.

My netbook reports that it's using GLX 1.4 with Mesa.

Checking Synaptic on my VBox shows that I have a number of Mesa libraries, but for some reason, the Chromium implementation is the one in use.

For present and future reference, what's the simplest way to remedy this situation? Whether updating the Chromium implementation, switching to the Mesa one, or some other solution. I want to use GLX for the Linux build of a game I'm working on, so if there are different but compatible solutions for the development side and client side, then that would be good to know, as well.

Sorry for the huge post, figured I'd say everything I've figured out on my own.

---

