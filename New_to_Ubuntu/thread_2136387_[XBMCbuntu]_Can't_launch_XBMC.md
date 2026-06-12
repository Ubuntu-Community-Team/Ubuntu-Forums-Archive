---
title: "[XBMCbuntu] Can't launch XBMC"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by r3bol on 2013-04-17
Hi I've just installed the latest xbmcbuntu-12.00.Intel-AMD.iso but after the install, I can only get to the desktop. All attempts to launch xbmc results in ...> :~$ xbmc
WARNING: gnome-keyring:: couldn't connect to: /home/metost/.cache/keyring-Ptq8R0/pkcs11: No such file or directory
/usr/lib/xbmc/xbmc-xrandr: Failed to get size of gamma for output default
/usr/lib/xbmc/xbmc-xrandr: Failed to get size of gamma for output default
LLVM ERROR: Program used external function '' which could not be resolved!
pure virtual method called
terminate called without an active exception
Aborted
Crash report available at /home/metost/xbmc_crashlog-20130417_193444.log
Here is the crash log...
> ############## XBMC CRASH LOG ###############

################ SYSTEM INFO ################
 Date: Wed Apr 17 18:59:48 EEST 2013
 XBMC Options: 
 Arch: i686
 Kernel: Linux 3.5.0-27-generic #46-Ubuntu SMP Mon Mar 25 20:00:05 UTC 2013
 Release: 
    Distributor ID:	Ubuntu
    Description:	Ubuntu 12.10 - XBMCbuntu
    Release:	12.10
    Codename:	quantal
############## END SYSTEM INFO ##############

############### STACK TRACE #################
gdb not installed, can't get stack trace.
############# END STACK TRACE ###############

################# LOG FILE ##################

ï»¿18:59:47 T:3038459648  NOTICE: -----------------------------------------------------------------------
18:59:47 T:3038459648  NOTICE: Starting XBMC (12.0 Git:fb595f2), Platform: Linux (Ubuntu 12.10 - XBMCbuntu, 3.5.0-27-generic i686). Built on Jan 28 2013
18:59:47 T:3038459648  NOTICE: special://xbmc/ is mapped to: /usr/share/xbmc
18:59:47 T:3038459648  NOTICE: special://xbmcbin/ is mapped to: /usr/lib/xbmc
18:59:47 T:3038459648  NOTICE: special://masterprofile/ is mapped to: /home/leke/.xbmc/userdata
18:59:47 T:3038459648  NOTICE: special://home/ is mapped to: /home/leke/.xbmc
18:59:47 T:3038459648  NOTICE: special://temp/ is mapped to: /home/leke/.xbmc/temp
18:59:47 T:3038459648  NOTICE: The executable running is: /usr/lib/xbmc/xbmc.bin
18:59:47 T:3038459648  NOTICE: Local hostname: xbmc-tv
18:59:47 T:3038459648  NOTICE: Log File is located: /home/leke/.xbmc/temp/xbmc.log
18:59:47 T:3038459648  NOTICE: -----------------------------------------------------------------------
18:59:47 T:3038459648   ERROR: CAESinkOSS::EnumerateDevicesEx - Failed to open mixer: /dev/mixer
18:59:47 T:3038459648  NOTICE: Enumerated ALSA devices:
18:59:47 T:3038459648  NOTICE:     Device 1
18:59:47 T:3038459648  NOTICE:         m_deviceName      : @
18:59:47 T:3038459648  NOTICE:         m_displayName     : Default (HDA NVidia STAC92xx Analog)
18:59:47 T:3038459648  NOTICE:         m_displayNameExtra:
18:59:47 T:3038459648  NOTICE:         m_deviceType      : AE_DEVTYPE_PCM
18:59:47 T:3038459648  NOTICE:         m_channels        : FL,FR
18:59:47 T:3038459648  NOTICE:         m_sampleRates     : 44100,48000,88200,96000,176400,192000
18:59:47 T:3038459648  NOTICE:         m_dataFormats     : AE_FMT_S32NE,AE_FMT_S16NE,AE_FMT_S16LE
18:59:47 T:3038459648  NOTICE:     Device 2
18:59:47 T:3038459648  NOTICE:         m_deviceName      : @:CARD=NVidia,DEV=0
18:59:47 T:3038459648  NOTICE:         m_displayName     : HDA NVidia
18:59:47 T:3038459648  NOTICE:         m_displayNameExtra: STAC92xx Analog
18:59:47 T:3038459648  NOTICE:         m_deviceType      : AE_DEVTYPE_PCM
18:59:47 T:3038459648  NOTICE:         m_channels        : FL,FR
18:59:47 T:3038459648  NOTICE:         m_sampleRates     : 44100,48000,88200,96000,176400,192000
18:59:47 T:3038459648  NOTICE:         m_dataFormats     : AE_FMT_S32NE,AE_FMT_S16NE,AE_FMT_S16LE
18:59:47 T:3038459648  NOTICE: load settings...
18:59:47 T:3038459648   ERROR: Unable to load libcrystalhd.so.3, reason: libcrystalhd.so.3: cannot open shared object file: No such file or directory
18:59:47 T:3038459648  NOTICE: special://profile/ is mapped to: special://masterprofile/
18:59:47 T:3038459648  NOTICE: loading special://masterprofile/guisettings.xml
18:59:47 T:3038459648  NOTICE: Getting hardware information now...
18:59:47 T:3038459648  NOTICE: Loading player core factory settings from special://xbmc/system/playercorefactory.xml.
18:59:47 T:3038459648  NOTICE: Loaded playercorefactory configuration
18:59:47 T:3038459648  NOTICE: Loading player core factory settings from special://masterprofile/playercorefactory.xml.
18:59:47 T:3038459648  NOTICE: special://masterprofile/playercorefactory.xml does not exist. Skipping.
18:59:47 T:3038459648  NOTICE: No settings file to load (special://xbmc/system/advancedsettings.xml)
18:59:47 T:3038459648  NOTICE: Loaded settings file from special://profile/advancedsettings.xml
18:59:47 T:3038459648  NOTICE: Contents of special://profile/advancedsettings.xml are...
                                            <advancedsettings>
                                              <useddsfanart>true</useddsfanart>
                                              <cputempcommand>cputemp</cputempcommand>
                                              <gputempcommand>gputemp</gputempcommand>
                                              <samba>
                                                <clienttimeout>30</clienttimeout>
                                              </samba>
                                              <network>
                                                <disableipv6>true</disableipv6>
                                              </network>
                                            </advancedsettings>
18:59:47 T:3038459648  NOTICE: Getting hardware information now...
18:59:47 T:3038459648  NOTICE: Default DVD Player: dvdplayer
18:59:47 T:3038459648  NOTICE: Default Video Player: dvdplayer
18:59:47 T:3038459648  NOTICE: Default Audio Player: paplayer
18:59:47 T:3038459648  NOTICE: Disabled debug logging due to GUI setting. Level 0.
18:59:47 T:3038459648  NOTICE: Log level changed to 0
18:59:47 T:3038459648  NOTICE: Loading media sources from special://masterprofile/sources.xml
18:59:47 T:2971065152  NOTICE: Thread CSoftAE start, auto delete: false
18:59:47 T:3038459648  NOTICE: Running database version Addons15
18:59:47 T:3035769664  NOTICE: Thread XBMC Peripherals start, auto delete: false
18:59:47 T:3038459648  NOTICE: Setup SDL
18:59:47 T:3038459648  NOTICE: Checking resolution 16
18:59:47 T:3038459648  NOTICE: Using visual 0x114
18:59:47 T:3038459648  NOTICE: GL_VENDOR = VMware, Inc.
18:59:47 T:3038459648  NOTICE: GL_RENDERER = Gallium 0.4 on llvmpipe (LLVM 0x301)
18:59:47 T:3038459648  NOTICE: GL_VERSION = 2.1 Mesa 9.0
18:59:47 T:3038459648  NOTICE: GL_SHADING_LANGUAGE_VERSION = 1.20
18:59:47 T:3038459648  NOTICE: GL_EXTENSIONS = GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_compression_s3tc GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_fog_distance GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_primitive_restart GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_ATI_texture_compression_3dc GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_ATI_texture_mirror_once GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_compression_latc GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_AMD_draw_buffers_blend GL_ARB_ES2_compatibility GL_ARB_debug_output GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_shader_texture_lod GL_ARB_vertex_type_2_10_10_10_rev GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_robustness GL_ARB_texture_storage GL_ARB_invalidate_subdata
18:59:47 T:3038459648   ERROR: GLX: Same window as before, refreshing context
18:59:48 T:3038459648  NOTICE: Running database version Addons15
18:59:48 T:3038459648  NOTICE: Running database version ViewModes4
18:59:48 T:3038459648  NOTICE: Running database version Textures13
18:59:48 T:3038459648  NOTICE: Running database version MyMusic32
18:59:48 T:3038459648  NOTICE: Running database version MyVideos75
18:59:48 T:3038459648  NOTICE: Running database version TV22
18:59:48 T:3038459648  NOTICE: Running database version Epg7
18:59:48 T:3038459648  NOTICE: start dvd mediatype detection
18:59:48 T:3038459648  NOTICE: initializing playlistplayer
18:59:48 T:3038459648  NOTICE: DONE initializing playlistplayer
18:59:48 T:3025525568  NOTICE: Thread CDetectDVDMedia start, auto delete: false
18:59:48 T:3038459648  NOTICE: initialize done
18:59:48 T:3038459648  NOTICE: Running the application...
18:59:48 T:2916186944  NOTICE: Thread Jobworker start, auto delete: true
18:59:48 T:3038459648  NOTICE: ES: Starting event server
18:59:48 T:3038459648  NOTICE: starting zeroconf publishing
18:59:48 T:2899401536  NOTICE: Thread CTCPServer start, auto delete: false
18:59:48 T:2907794240  NOTICE: Thread CEventServer start, auto delete: false
18:59:48 T:2907794240  NOTICE: ES: Starting UDP Event server on 0.0.0.0:9777
18:59:48 T:2907794240  NOTICE: UDP: Listening on port 9777
18:59:48 T:2882616128  NOTICE: Thread Jobworker start, auto delete: true


############### END LOG FILE ################

############ END XBMC CRASH LOG #############

Any idea what to do?

Thanks.

---

### Post by Paqman on 2013-04-17
What hardware have you go this installed on, it's thrown a graphics error. This: "GL_VENDOR = VMware, Inc." is a bit odd, have you installed this on a virtual machine?

---

### Post by r3bol on 2013-04-18
> **Paqman said:**
> What hardware have you go this installed on, it's thrown a graphics error. This: "GL_VENDOR = VMware, Inc." is a bit odd, have you installed this on a virtual machine?

Thanks for the reply. It's a Dell Optiplex 740 [https://www.dell.com/downloads/global/products/optix/en/740_customer_brochure.pdf](https://www.dell.com/downloads/global/products/optix/en/740_customer_brochure.pdf) 
I'm using the on-board video.

---

### Post by Paqman on 2013-04-18
Right it looks like your integrated video is Nvidia, have you tried installing the drivers? It's possible the open source nouveau driver isn't up to running XBMC.

---

