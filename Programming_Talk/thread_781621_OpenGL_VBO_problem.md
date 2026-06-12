---
title: "OpenGL VBO problem"
date: 2008-05-04
forum: Programming Talk
---

### Post by davek20 on 2008-05-04
Hey guys. I'm having some troubles setting up a vertex buffer objects (VBO) in OpenGL. At first I thought it had to something with how I was creating them, but now I'm starting to lean towards a driver issue (possibly). I'm using Ubuntu 8.04, my video card is a nVidia 7600GT and I am using the proprietary drivers.

At first the problem was with glDrawElements() since that was crashing my program. After a little investigation, that wasn't the overall problem. So basically what is happening is that my calls to glGenBuffers(1,&varName) are ALWAYS setting varName to 0, no matter how many times I call it (I even did an array assignment with glGenBuffers(10, varName) and all 10 elements were still 0). So in the code below, BOTH vertex_buf and index_buf are 0. Here is my create VBO code:

```

void CreateVBO(){

	//create the vertices
	vertices = new GLfloat[3 * 3];
	vertices[0] = -5.0f;	vertices[1] = -5.0f;	vertices[2] = 40.0f;	//vertex 1
	vertices[3] = -5.0f;	vertices[4] = 5.0f;	vertices[5] = 40.0f;	//vertex 2
	vertices[6] = 5.0f;	vertices[7] = -5.0f;	vertices[8] = 40.0f;	//vertex 3
	
	// generate a new VBO and get the associated ID
	glGenBuffers(1, &vertex_buf);
        //HERE VERTEX_BUF IS 0!!!!


	// bind VBO in order to use
	glBindBuffer(GL_ARRAY_BUFFER, vertex_buf);

	// upload data to VBO
	glBufferData(GL_ARRAY_BUFFER, 3 * 3 * sizeof(GLfloat), vertices, GL_STATIC_DRAW);	

	
	//create the indices
	indices = new GLushort[3];
	indices[0] = 0;		indices[1] = 1;		indices[2] = 2;		
	
        // generate a new VBO for the indices
	glGenBuffers(1, &index_buf);	
        //HERE INDEX_BUF IS 0!!!!

	// bind VBO in order to use
	glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, index_buf);

	// upload index data to VBO
	glBufferData(GL_ELEMENT_ARRAY_BUFFER, 3 * sizeof(GLushort), indices, GL_STATIC_DRAW);
}

```

Also, here is some output from glxinfo:
direct rendering: Yes
OpenGL renderer string: GeForce 7600 GT/PCI/SSE2
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 2.1.2 NVIDIA 169.12

Does anyone have an idea on what is wrong and how to fix it?

---

### Post by stroyan on 2008-05-04
The simplest explanation is that you are getting OpenGL errors and the
glGenBuffers calls are just returning without modifying the vertex_buf
parameter.

You should add some calls to glGetError to test for errors from your
OpenGL calls.

---

### Post by davek20 on 2008-05-04
I found out my problem. I was trying to create my VBOs BEFORE I had an active context (ie all the glutInit()'s and glutCreate() calls). Once I move my creation stuff after those, it works fine.

Funny thing was that I put all the glGetErrors() after EVERY gl call, and nothing returned any errors at all, dispite things being out of order. I thought at least the GL_INVALID_OPERATION would be set when trying to call glGenBuffers() before the window was created.

Thanks for the help.

---

### Post by VuDu on 2008-05-14
Hello, I'm also trying to use VBO's but I get many errors like these while compiling:

XXXX.cpp:XX: error: ‘glGenBuffers’ was not declared in this scope
XXXX.cpp:XX: error: ‘glBindBuffer’ was not declared in this scope
XXXX.cpp:XX: error: ‘glBufferData’ was not declared in this scope

Do you have any idea what is missing?
I have other glGenLists and other Lists methods in the same file and it's working, the problem is only with the VBO functions.

some glxinfo dump:
```

OpenGL renderer string: GeForce Go 6200/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

```

---

### Post by rnodal on 2008-06-11
Those are compile errors so the probable cause of the problem is OpenGL headers out of date or that simply don't define those functions. Also make sure that you are calling the functions correctly. Most OpenGL functions have the type and number of parameters as part of the name of the function. For example glColor4f for 4 floats. I hope that helps.

-r

---

