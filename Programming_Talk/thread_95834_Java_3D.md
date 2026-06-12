---
title: "Java 3D"
date: 2005-11-27
forum: Programming Talk
---

### Post by mindead on 2005-11-27
Can someone tell me if we can do Java 3D programming on linux?
I am new to Java 3D (but not to Java programming).

Browsing the sun's website for a java 3D api gave me only two OS: of course solaris & winquelquechose...
I didn't find anything in Ubuntu repositories too.
I guess there could be useful libraries instead?

Thank you very much for any help.

---

### Post by Leif on 2005-11-27
maybe we're talking about different things, but there are plenty of linux builds here :

[https://java3d.dev.java.net/binary-builds.html](https://java3d.dev.java.net/binary-builds.html)

---

### Post by mindead on 2005-11-27
No, that seems to be what I was looking for! I was in the developer section.
Thank you
Someone have tried that on breezy?

---

### Post by blastus on 2005-11-27
It's been quite a while since I've done any Java 3D and I've only worked with it on Windows, but I just tried installing
[Java 3D 1.3.2](http://download.java.net/media/java3d/builds/release/1.3.2/java3d-1_3_2-linux-i586.zip). To install it I extracted the contents of j3d-132-linux-x86.zip as follows:

/usr/lib/j2sdk1.5-sun/jre/lib/ext/j3dcore.jar
/usr/lib/j2sdk1.5-sun/jre/lib/ext/j3dutils.jar
/usr/lib/j2sdk1.5-sun/jre/lib/ext/vecmath.jar
/usr/lib/j2sdk1.5-sun/jre/lib/i386/libj3dcore-ogl.so
/usr/lib/j2sdk1.5-sun/jre/lib/i386/libj3dutils.so

Works beautifully on Breezy! :) I must say that it seems to work a LOT faster on Linux than on Windows XP. It takes forever to create a scene graph on Windows XP but on Linux it is almost instantaneous.

```
/*
 * Copyright (c) 1996-1998 Sun Microsystems, Inc. All Rights Reserved.
 *
 * Sun grants you ("Licensee") a non-exclusive, royalty free, license to use,
 * modify and redistribute this software in source and binary code form,
 * provided that i) this copyright notice and license appear on all copies of
 * the software; and ii) Licensee does not utilize the software in a manner
 * which is disparaging to Sun.
 *
 * This software is provided "AS IS," without a warranty of any kind. ALL
 * EXPRESS OR IMPLIED CONDITIONS, REPRESENTATIONS AND WARRANTIES, INCLUDING ANY
 * IMPLIED WARRANTY OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE OR
 * NON-INFRINGEMENT, ARE HEREBY EXCLUDED. SUN AND ITS LICENSORS SHALL NOT BE
 * LIABLE FOR ANY DAMAGES SUFFERED BY LICENSEE AS A RESULT OF USING, MODIFYING
 * OR DISTRIBUTING THE SOFTWARE OR ITS DERIVATIVES. IN NO EVENT WILL SUN OR ITS
 * LICENSORS BE LIABLE FOR ANY LOST REVENUE, PROFIT OR DATA, OR FOR DIRECT,
 * INDIRECT, SPECIAL, CONSEQUENTIAL, INCIDENTAL OR PUNITIVE DAMAGES, HOWEVER
 * CAUSED AND REGARDLESS OF THE THEORY OF LIABILITY, ARISING OUT OF THE USE OF
 * OR INABILITY TO USE SOFTWARE, EVEN IF SUN HAS BEEN ADVISED OF THE
 * POSSIBILITY OF SUCH DAMAGES.
 *
 * This software is not designed or intended for use in on-line control of
 * aircraft, air traffic, aircraft navigation or aircraft communications; or in
 * the design, construction, operation or maintenance of any nuclear
 * facility. Licensee represents and warrants that it will not use or
 * redistribute the Software for such purposes.
 */

import java.applet.Applet;
import java.awt.BorderLayout;
import java.awt.Frame;
import java.awt.event.*;
import com.sun.j3d.utils.applet.MainFrame; 
import com.sun.j3d.utils.geometry.ColorCube;
import com.sun.j3d.utils.universe.*;
import javax.media.j3d.*;
import javax.vecmath.*;

//   HelloJava3Dc renders a single, rotating cube.  

public class HelloJava3Dd extends Applet {

     public BranchGroup createSceneGraph() {
	// Create the root of the branch graph
	BranchGroup objRoot = new BranchGroup();

	// rotate object has composited transformation matrix
	Transform3D rotate = new Transform3D();
	Transform3D tempRotate = new Transform3D();

        rotate.rotX(Math.PI/4.0d);
	tempRotate.rotY(Math.PI/5.0d);
        rotate.mul(tempRotate);

	TransformGroup objRotate = new TransformGroup(rotate);

	// Create the transform group node and initialize it to the
	// identity.  Enable the TRANSFORM_WRITE capability so that
	// our behavior code can modify it at runtime.  Add it to the
	// root of the subgraph.
	TransformGroup objSpin = new TransformGroup();
	objSpin.setCapability(TransformGroup.ALLOW_TRANSFORM_WRITE);

	objRoot.addChild(objRotate);
	objRotate.addChild(objSpin);
 
	// Create a simple shape leaf node, add it to the scene graph.
	// ColorCube is a Convenience Utility class
	objSpin.addChild(new ColorCube(0.4));

	// Create a new Behavior object that will perform the desired
	// operation on the specified transform object and add it into
	// the scene graph.
	Transform3D yAxis = new Transform3D();
	Alpha rotationAlpha = new Alpha(-1, 4000);

	RotationInterpolator rotator =
	    new RotationInterpolator(rotationAlpha, objSpin, yAxis,
				     0.0f, (float) Math.PI*2.0f);

	// a bounding sphere specifies a region a behavior is active
	// create a sphere centered at the origin with radius of 1
	BoundingSphere bounds = new BoundingSphere();
	rotator.setSchedulingBounds(bounds);
	objSpin.addChild(rotator);

	return objRoot;
    } // end of CreateSceneGraph method of HelloJava3Dd

    public HelloJava3Dd() {
        setLayout(new BorderLayout());
        Canvas3D canvas3D = new Canvas3D(null);
        add("Center", canvas3D);

        BranchGroup scene = createSceneGraph();
	scene.compile();

        // SimpleUniverse is a Convenience Utility class
        SimpleUniverse simpleU = new SimpleUniverse(canvas3D);

	// This will move the ViewPlatform back a bit so the
	// objects in the scene can be viewed.
        simpleU.getViewingPlatform().setNominalViewingTransform();

        simpleU.addBranchGraph(scene);
   } // end of HelloJava3Dd (constructor)

    //  The following allows this to be run as an application
    //  as well as an applet

    public static void main(String[] args) {
        Frame frame = new MainFrame(new HelloJava3Dd(), 256, 256);
    } // end of main (method of HelloJava3D)

} // end of class HelloJava3Dd
```

---

### Post by mindead on 2005-11-28
Nice.

I tried your code, it compiled with the following exception:

```

************************************************************************
*** ERROR: Canvas3D constructed with a null GraphicsConfiguration
*** This will cause a NullPointerException in a subsequent release
************************************************************************

```

The applet viewer is showing up, but nothing happens, black screen.
What could this mean?

I have a intel 915GM graphics card. 
I can run OpenGL screensavers.
I'm working with Eclipse 3.1.

---

### Post by blastus on 2005-11-28
That error is just a warning and doesn't affect anything. To get rid of it, change
```
Canvas3D canvas3D = new Canvas3D(null);
```
to```
Canvas3D canvas3D = new Canvas3D(
	SimpleUniverse.getPreferredConfiguration());
```
You should see a rotating 3D cube--each side being a different color. For Java 3D 1.3.2 you need a graphics card with a driver that supports the GLX extension: GLX 1.3 or later and OpenGL 1.2 or later. I have an NVIDIA graphics card with the NVIDIA driver installed. Do you have Linux drivers for your graphics card installed? It may be that your card and/or the drivers you are using don't support the GLX extension. I'm not sure what that means or how one could find out if GLX is supported. Does the Java 3D OpenGL implementation work on Windows on your machine? It may be that ATI and NVIDIA are better supported I'm not sure.

---

### Post by cmmorri on 2005-11-29
I too am having difficulty getting Java3D to work in Breezy. I was previously using Fedora Core 3 and didn't have a problem. In Breezy, I get the black window, no rendering. My setup is a little different. I'm using a tablet PC which uses the siliconmotion driver. Except for not being able to get Java3D to run, I love ubuntu. But due to my thesis project, I have to get it working so I may end up switching back to Fedora.

---

### Post by mindead on 2005-11-29
Passing the glxinfo command gives me the following result:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.3.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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
mindead@cordelia:~$ sudo glxinfo | more
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.3.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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

```
DRI and glx modules are set up to be loaded in the xorg.conf file as well.

I really don't know what to do here! Is it a bug?

---

### Post by blastus on 2005-11-29
[quote=mindead]GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group[/quote]

I think that may be your problem. According to the [Java 3D 1.3.2 Release Notes](https://j3d-core.dev.java.net/j3d1_3_2/RELEASE-NOTES.html), you need GLX version 1.3 or later. It sounds like your video card is integrated on the motherboard. Here's what glxinfo shows on my machine--notice mine says GLX version: 1.3...```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5600/AGP/SSE2
OpenGL version string: 2.0.0 NVIDIA 76.67
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shadow, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_HP_occlusion_test, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_half_float, GL_NV_light_max_exponent, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x22 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x2a 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x2b 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x2c 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x2d 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x2e 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x2f 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x30 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x31 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x32 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x33 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon
0x34 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x35 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon
0x36 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x37 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x38 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x39 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x3a 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x3b 16 dc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x3c 16 dc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x3d 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x3e 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x3f 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x40 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x41 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x42 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x43 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x44 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x45 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x46 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon
0x47 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x48 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon
```

What's strange about yours is that the "glx server" is 1.4 but the "glx client" is 1.2 whereas mine they are both 1.3. Maybe you need an updated Linux driver for your video card--one that supports GLX 1.3? Or maybe there is an earlier release of Java 3D on Linux that can use GLX 1.2?

---

### Post by blastus on 2005-11-29
[QUOTE=cmmorri]I too am having difficulty getting Java3D to work in Breezy. I was previously using Fedora Core 3 and didn't have a problem. In Breezy, I get the black window, no rendering. My setup is a little different. I'm using a tablet PC which uses the siliconmotion driver. Except for not being able to get Java3D to run, I love ubuntu. But due to my thesis project, I have to get it working so I may end up switching back to Fedora.[/QUOTE]

What I would do is run the glxinfo command like mindead did. Run it on Fedora Core 3 then run it on Ubuntu Breezy. Then compare the results. According to the Java 3D 1.3.2 release notes, you need GLX 1.3 or later and OpenGL 1.2 or later. If Java 3D runs on Fedora Core for you then that tells me that your graphics adaptor supports Java 3D on Linux. The issue may be you need a driver for your graphics card for Ubuntu Breezy--one that supports OpenGL 1.2 (or later) and GLX 1.3 (or later.)

---

### Post by mindead on 2005-11-29
Thank you for your feedback.
My card wasn't supported at all in Hoary. For now I'm lucky to see something :) without the old vesa drivers!
I guess it would now be a though time uninstalling files of J3D, and installing a older version, but I'll give it a try.

---

### Post by Blunderbuss on 2006-12-02
Did you have any luck figuring this out? I'm having the same problem. I've got the most recent Nvidia drivers off their website and glxinfo shows my server version as 1.2 and my client version as 1.4. It seems like some more recent version of libglx must be needed but I'm having trouble figuring out where to get it. Any ideas? Thanks.

---

