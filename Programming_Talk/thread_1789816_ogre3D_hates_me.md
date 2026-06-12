---
title: "ogre3D hates me"
date: 2011-06-24
forum: Programming Talk
---

### Post by vivichrist on 2011-06-24
I thought I'd look at Ogre3D and I installed the default packages in ubuntu natty and couldn't compile the tutorial examples because SDK*.h etc were missing. so I found this repository [http://ppa.launchpad.net/ogre-team/ogre/ubuntu](http://ppa.launchpad.net/ogre-team/ogre/ubuntu) and still can't compile any code, I fixed several inconsistencies like OgreMain instead of OgreMain_h (windows crap) in code::blocks. I'm at my wits end. ogre-teams version is 1.7.3. I have blocked (commented out) certain plug-ins through plugins.cfg but left the default resources.cfg (copyed) from /usr/share/OGRE. also tryed changing FBO to PBuffer to Copy etc. haven't modified the code just added "TutorialApplication.h/cpp" and "BaseApplication.h/cpp" to the project. but even the original sampleApp class give me the exact same segfault... :(

```
21:58:03: Creating resource group General
21:58:03: Creating resource group Internal
21:58:03: Creating resource group Autodetect
21:58:03: SceneManagerFactory for type 'DefaultSceneManager' registered.
21:58:03: Registering ResourceManager for type Material
21:58:03: Registering ResourceManager for type Mesh
21:58:03: Registering ResourceManager for type Skeleton
21:58:03: MovableObjectFactory for type 'ParticleSystem' registered.
21:58:03: OverlayElementFactory for type Panel registered.
21:58:03: OverlayElementFactory for type BorderPanel registered.
21:58:03: OverlayElementFactory for type TextArea registered.
21:58:03: Registering ResourceManager for type Font
21:58:03: ArchiveFactory for archive type FileSystem registered.
21:58:03: ArchiveFactory for archive type Zip registered.
21:58:03: DDS codec registering
21:58:03: FreeImage version: 3.15.0
21:58:03: This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
21:58:03: Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2,pfm,pct,pict,pic,3fr,arw,bay,bmq,cap,cine,cr2,crw,cs1,dc2,dcr,drf,dsc,dng,erf,fff,ia,iiq,k25,kc2,kdc,mdc,mef,mos,mrw,nef,nrw,orf,pef,ptx,pxn,qtk,raf,raw,rdc,rw2,rwl,rwz,sr2,srf,sti
21:58:03: Registering ResourceManager for type HighLevelGpuProgram
21:58:03: Registering ResourceManager for type Compositor
21:58:03: MovableObjectFactory for type 'Entity' registered.
21:58:03: MovableObjectFactory for type 'Light' registered.
21:58:03: MovableObjectFactory for type 'BillboardSet' registered.
21:58:03: MovableObjectFactory for type 'ManualObject' registered.
21:58:03: MovableObjectFactory for type 'BillboardChain' registered.
21:58:03: MovableObjectFactory for type 'RibbonTrail' registered.
21:58:03: Loading library /usr/lib/OGRE/RenderSystem_GL
21:58:03: Installing plugin: GL RenderSystem
21:58:03: OpenGL Rendering Subsystem created.
21:58:03: Plugin successfully installed
21:58:03: Loading library /usr/lib/OGRE/Plugin_ParticleFX
21:58:03: Installing plugin: ParticleFX
21:58:03: Particle Emitter Type 'Point' registered
21:58:03: Particle Emitter Type 'Box' registered
21:58:03: Particle Emitter Type 'Ellipsoid' registered
21:58:03: Particle Emitter Type 'Cylinder' registered
21:58:03: Particle Emitter Type 'Ring' registered
21:58:03: Particle Emitter Type 'HollowEllipsoid' registered
21:58:03: Particle Affector Type 'LinearForce' registered
21:58:03: Particle Affector Type 'ColourFader' registered
21:58:03: Particle Affector Type 'ColourFader2' registered
21:58:03: Particle Affector Type 'ColourImage' registered
21:58:03: Particle Affector Type 'ColourInterpolator' registered
21:58:03: Particle Affector Type 'Scaler' registered
21:58:03: Particle Affector Type 'Rotator' registered
21:58:03: Particle Affector Type 'DirectionRandomiser' registered
21:58:03: Particle Affector Type 'DeflectorPlane' registered
21:58:03: Plugin successfully installed
21:58:03: Loading library /usr/lib/OGRE/Plugin_BSPSceneManager
21:58:03: Installing plugin: BSP Scene Manager
21:58:03: Plugin successfully installed
21:58:03: Loading library /usr/lib/OGRE/Plugin_CgProgramManager
21:58:03: Installing plugin: Cg Program Manager
21:58:03: Plugin successfully installed
21:58:03: Loading library /usr/lib/OGRE/Plugin_PCZSceneManager
21:58:03: Installing plugin: Portal Connected Zone Scene Manager
21:58:03: PCZone Factory Type 'ZoneType_Default' registered
21:58:03: Plugin successfully installed
21:58:03: Loading library /usr/lib/OGRE/Plugin_OctreeZone
21:58:03: Installing plugin: Octree Zone Factory
21:58:03: Plugin successfully installed
21:58:03: Loading library /usr/lib/OGRE/Plugin_OctreeSceneManager
21:58:03: Installing plugin: Octree & Terrain Scene Manager
21:58:03: Plugin successfully installed
21:58:03: *-*-* OGRE Initialising
21:58:03: *-*-* Version 1.7.3 (Cthugha)
21:58:03: Creating resource group Essential
21:58:03: Added resource location '/usr/share/OGRE/media/thumbnails' of type 'FileSystem' to resource group 'Essential'
21:58:03: Added resource location '/usr/share/OGRE/media/packs/SdkTrays.zip' of type 'Zip' to resource group 'Essential'
21:58:03: Added resource location '/usr/share/OGRE/media' of type 'FileSystem' to resource group 'General'
21:58:03: Creating resource group Popular
21:58:03: Added resource location '/usr/share/OGRE/media/fonts' of type 'FileSystem' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/materials/programs' of type 'FileSystem' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/materials/scripts' of type 'FileSystem' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/materials/textures' of type 'FileSystem' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/materials/textures/nvidia' of type 'FileSystem' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/models' of type 'FileSystem' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/particle' of type 'FileSystem' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/DeferredShadingMedia' of type 'FileSystem' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/PCZAppMedia' of type 'FileSystem' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/RTShaderLib' of type 'FileSystem' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/RTShaderLib/materials' of type 'FileSystem' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/packs/cubemap.zip' of type 'Zip' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/packs/cubemapsJS.zip' of type 'Zip' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/packs/dragon.zip' of type 'Zip' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/packs/fresneldemo.zip' of type 'Zip' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/packs/ogretestmap.zip' of type 'Zip' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/packs/ogredance.zip' of type 'Zip' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/packs/Sinbad.zip' of type 'Zip' to resource group 'Popular'
21:58:03: Added resource location '/usr/share/OGRE/media/packs/skybox.zip' of type 'Zip' to resource group 'Popular'
21:58:10: CPU Identifier & Features
21:58:10: -------------------------
21:58:10:  *   CPU ID: GenuineIntel: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz
21:58:10:  *      SSE: yes
21:58:10:  *     SSE2: yes
21:58:10:  *     SSE3: yes
21:58:10:  *      MMX: yes
21:58:10:  *   MMXEXT: yes
21:58:10:  *    3DNOW: no
21:58:10:  * 3DNOWEXT: no
21:58:10:  *     CMOV: yes
21:58:10:  *      TSC: yes
21:58:10:  *      FPU: yes
21:58:10:  *      PRO: yes
21:58:10:  *       HT: no
21:58:10: -------------------------
21:58:10: ******************************
*** Starting GLX Subsystem ***
******************************
21:58:10: GLRenderSystem::_createRenderWindow "TutorialApplication Render Window", 640x480 windowed  miscParams: FSAA=0 displayFrequency=60 MHz gamma= vsync=No 
21:58:10: GLXWindow::create used FBConfigID = 104
21:58:10: GL_VERSION = 1.4 Mesa 7.10.2
21:58:10: GL_VENDOR = Tungsten Graphics, Inc
21:58:10: GL_RENDERER = Mesa DRI Intel(R) 945GM GEM 20100330 DEVELOPMENT 
21:58:10: GL_EXTENSIONS = GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture3D GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture GL_EXT_texture_rectangle GL_EXT_vertex_array GL_OES_EGL_image GL_OES_read_format GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_object_purgeable GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_window_pos GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_program1_1 GL_NV_vertex_program GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays 
21:58:10: Supported GLX extensions: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_MESA_swap_control GLX_OML_swap_method GLX_OML_sync_control GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGI_video_sync GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGIX_visual_select_group GLX_EXT_texture_from_pixmap GLX_INTEL_swap_event 
21:58:10: ***************************
21:58:10: *** GL Renderer Started ***
21:58:10: ***************************
21:58:10: Registering ResourceManager for type GpuProgram
21:58:10: GLSL support detected
21:58:10: GL: Using GL_EXT_framebuffer_object for rendering to textures (best)
21:58:10: FBO PF_UNKNOWN depth/stencil support: D0S1 D0S4 D0S8 D0S16 D16S0 D24S0 D32S0 Packed-D24S8 
```

and then segmentation fault...

---

### Post by scu-ba-de-buntu on 2011-06-24
hmmm. not really sure what to make of your post. This may or may not be helpful, but if I was in your situation, I think I would start over on my Orge3D setup since something isn't right - be it the configuration, linked libs, graphics configuration, or IDE/compiler. 

Can you compile say an OpenGL demo and run it successfully on this box? Are you sure you have the Stable version of Orge3D for linux? When you installed it did you do the ./configure make stuff or copy the directory, or use a package manager?

---

### Post by vivichrist on 2011-06-25
I have previously compiled opengl demo's and these were opengl accelerated but I wonder if ogre has a problem with dri or something since I couldn't use openGL-ES plugin. so far I have not compiled my own, have tried 1.7.3, 1.7.2 and 1.6.4 (default ubuntu package). what version should I go for?

---

### Post by vivichrist on 2011-06-27
to be clear I didn't compile my own ogre binaries. I used the packages available from the repositories. recently I tried compiling my own ogre binaries and got the same problem... no sdk for the tutorial code (1.6.3-5) on one hand and segfault on the other (1.7.2-3). as you can see from the log I am using laptop onboard graphics chipset.

---

### Post by Simian Man on 2011-06-27
You should just download the SDK from the main website, don't use any Ubuntu packages.  Then if you still have problems, just ask on the Ogre forums.

---

### Post by scu-ba-de-buntu on 2011-06-28
> **Simian Man said:**
> You should just download the SDK from the main website, don't use any Ubuntu packages.  Then if you still have problems, just ask on the Ogre forums.

Good point.

[http://www.ogre3d.org/download/sdk](http://www.ogre3d.org/download/sdk)

If you solve it on the ogre forums please post a link to that thread here so that people with a similar problem can follow what you did to fix it.

---

