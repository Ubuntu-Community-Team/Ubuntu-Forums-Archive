---
title: "Flash is not working in Firefox"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by srobles97 on 2012-07-07
I am running Ubuntu 10.04.4 (Lucid Linux) and web browsers are driving me insane. My installed version of Google Chrome won't open and my installed version of Firefox won't play any flash. I've tried re-installing flash and nothing seems to be working.

---

### Post by robtygart on 2012-07-07
Are you running any add-ons? Popup blockers, Noscript, Flashbock.....?

---

### Post by madjr on 2012-07-07
sometimes it could be a hard drive space issue, do you have enough space available ?

---

### Post by daniell59 on 2012-07-07
> **robtygart said:**
> Are you running any add-ons? Popup blockers, Noscript, Flashbock.....?

Let me be more precise. In Chrome I can watch such videos as are on Hulu, but not Youtube. There is no such problem on Firefox.

Thanks for your input.

I just realized that I wrote the wrong title. It works in Firefox but not in Chrome.

---

### Post by dcsoldschool53 on 2012-07-07
Have you tried in chrome```
about:plugins
```and deleting one or both flash in chrome or updating flash in chrome.

---

### Post by daniell59 on 2012-07-07
> **dcsoldschool53 said:**
> Have you tried in chrome```
about:plugins
```and deleting one or both flash in chrome or updating flash in chrome.

Please forgive my ignorance. How do I use that code?

I updated the flash in Firefox using Flashaid. I do not know how to update it in Chrome.

Thanks for your assistance.

---

### Post by dcsoldschool53 on 2012-07-07
Quick questions? Do you use the stable or the beta version of flash-aid in Firefox? What versions of chrome are you using the one in repositories or did you download it from online?  

In chrome address bar type in ```
about:plugins
``` also in another tab, type in```
chrome://flash
```What we are looking for is the version of flash being used.

in about plugins click on details to open to see more info.See attachment.

---

### Post by daniell59 on 2012-07-07
> **dcsoldschool53 said:**
> Quick questions? Do you use the stable or the beta version of flash-aid in Firefox? What versions of chrome are you using the one in repositories or did you download it from online?  

In chrome address bar type in ```
about:plugins
``` also in another tab, type in```
chrome://flash
```What we are looking for is the version of flash being used.

in about plugins click on details to open to see more info.See attachment.

Flash (3 files) - Version: 11.2 r202
Shockwave Flash 11.2 r202
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/chromium-browser/plugins/libflashplayer.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/flashplugin-installer/libflashplayer.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Name:	Shockwave Flash
Version:	10.3 d162
Location:	/usr/lib/mozilla/plugins/libflashplayer.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Disable   Allow
iTunes Application Detector
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
Name:	iTunes Application Detector
Description:	This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
Version:	
Location:	/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/itunes-plugin		
.
Disable   Allow
VLC Multimedia Plugin (compatible Totem 2.30.2)
The Totem 2.30.2 plugin handles video and audio streams.
Name:	VLC Multimedia Plugin (compatible Totem 2.30.2)
Description:	The Totem 2.30.2 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-cone-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-vlc-plugin	VLC Multimedia Plugin	
.
application/vlc	VLC Multimedia Plugin	
.
video/x-google-vlc-plugin	VLC Multimedia Plugin	
.
application/x-ogg	Ogg multimedia file	
.ogg
application/ogg	Ogg multimedia file	
.ogg
audio/ogg	Ogg Audio	
.oga
audio/x-ogg	Ogg Audio	
.ogg
video/ogg	Ogg Video	
.ogv
video/x-ogg	Ogg Video	
.ogg
application/annodex	Annodex exchange format	
.anx
audio/annodex	Annodex Audio	
.axa
video/annodex	Annodex Video	
.axv
video/mpeg	MPEG video	
.mpg	.mpeg	.mpe
audio/wav	WAV audio	
.wav
audio/x-wav	WAV audio	
.wav
audio/mpeg	MP3 audio	
.mp3
application/x-nsv-vp3-mp3	NullSoft video	
.nsv
video/flv	Flash video	
.flv
application/x-totem-plugin	Totem Multimedia plugin	
.
Disable   Allow
Windows Media Player Plug-in 10 (compatible; Totem)
The Totem 2.30.2 plugin handles video and audio streams.
Name:	Windows Media Player Plug-in 10 (compatible; Totem)
Description:	The Totem 2.30.2 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-mplayer2	AVI video	
.avi	.wma	.wmv
video/x-ms-asf-plugin	ASF video	
.asf	.wmv
video/x-msvideo	AVI video	
.asf	.wmv
video/x-ms-asf	ASF video	
.asf
video/x-ms-wmv	Windows Media video	
.wmv
video/x-wmv	Windows Media video	
.wmv
video/x-ms-wvx	Windows Media video	
.wmv
video/x-ms-wm	Windows Media video	
.wmv
video/x-ms-wmp	Windows Media video	
.wmv
application/x-ms-wms	Windows Media video	
.wms
application/x-ms-wmp	Windows Media video	
.wmp
application/asx	Microsoft ASX playlist	
.asx
audio/x-ms-wma	Windows Media audio	
.wma
Disable   Allow
DivX® Web Player
DivX Web Player version 1.4.0.233
Name:	DivX® Web Player
Description:	DivX Web Player version 1.4.0.233
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-mully-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
video/divx	AVI video	
.divx
Disable   Allow
QuickTime Plug-in 7.6.6
The Totem 2.30.2 plugin handles video and audio streams.
Name:	QuickTime Plug-in 7.6.6
Description:	The Totem 2.30.2 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
video/quicktime	QuickTime video	
.mov
video/mp4	MPEG-4 video	
.mp4
image/x-macpaint	MacPaint Bitmap image	
.pntg
image/x-quicktime	Macintosh Quickdraw/PICT drawing	
.pict	.pict1	.pict2
video/x-m4v	MPEG-4 video	
.m4v
Disable   Allow

---

### Post by daniell59 on 2012-07-07
About Flash

Chromium	18.0.1025.151 (Ubuntu 10.04)
OS	Linux
Flash plugin	11.2 r202 /usr/lib/chromium-browser/plugins/libflashplayer.so
Flash plugin	11.2 r202 /usr/lib/flashplugin-installer/libflashplayer.so (not used)
Flash plugin	10.3 d162 /usr/lib/mozilla/plugins/libflashplayer.so (not used)
--- Crash data ---
Crash Reporting	Enable crash reporting to see crash IDs
For more details	[https://support.google.com/chrome/?p=ui_usagestat](https://support.google.com/chrome/?p=ui_usagestat)
--- GPU information ---
--- GPU driver, more information ---
Vendor Id	0x1002
Device Id	0x95c5
Driver vendor	ATI / AMD
Driver version	8.723.1
Driver date	
Pixel shader version	1.50
Vertex shader version	1.50
GL version	3.2
GL_VENDOR	ATI Technologies Inc.
GL_RENDERER	ATI Radeon HD 3400 Series
GL_VERSION	3.2.9756 Compatibility Profile Context
GL_EXTENSIONS	GL_AMDX_name_gen_delete GL_AMD_conservative_depth GL_AMD_draw_buffers_blend GL_AMD_performance_monitor GL_AMD_shader_stencil_export GL_ARB_color_buffer_float GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_seamless_cube_map GL_ARB_shader_objects GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_snorm GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_buffer GL_EXT_copy_texture GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_buffer_object_rgb32 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_explicit_multisample GL_NV_primitive_restart GL_NV_texgen_reflection GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays GL_WIN_swap_hint WGL_EXT_swap_control

---

### Post by Autodave on 2012-07-07
> **srobles97 said:**
> I am running Ubuntu 10.04.4 (Lucid Linux) and web browsers are driving me insane. My installed version of Google Chrome won't open and my installed version of Firefox won't play any flash. I've tried re-installing flash and nothing seems to be working.


I don't use Chrome, but I have had a good bit of success using GNASH instead of flash.  I have better luck removing Flash and then installing Gnash.

---

### Post by robtygart on 2012-07-07
> **srobles97 said:**
> I am running Ubuntu 10.04.4 (Lucid Linux) and web browsers are driving me insane. My installed version of Google Chrome won't open and my installed version of Firefox won't play any flash. I've tried re-installing flash and nothing seems to be working.

:idea: :idea: Do you have the the current up to date Firefox??

Open firefox click Help> About Firefox?

---

### Post by kedarlasane on 2012-07-07
Try to update Flash Player from get.adobe.com
----------------------------------------------------------------------------------------------------------

---

### Post by rokytnji on 2012-07-07
```
Flash (3 files) - Version: 11.2 r202
Shockwave Flash 11.2 r202
Name: Shockwave Flash
Version: 11.2 r202
Location: /usr/lib/chromium-browser/plugins/libflashplayer.so
Type: NPAPI
Disable
MIME types:
MIME type Description File extensions
application/x-shockwave-flash Shockwave Flash
.swf
application/futuresplash FutureSplash Player
.spl
Name: Shockwave Flash
Version: 11.2 r202
Location: /usr/lib/flashplugin-installer/libflashplayer.so
Type: NPAPI
Disable
MIME types:
MIME type Description File extensions
application/x-shockwave-flash Shockwave Flash
.swf
application/futuresplash FutureSplash Player
.spl
Name: Shockwave Flash
Version: 10.3 d162
Location: /usr/lib/mozilla/plugins/libflashplayer.so
Type: NPAPI
Disable
MIME types:
MIME type Description File extensions
application/x-shockwave-flash Shockwave Flash
.swf
application/futuresplash FutureSplash Player
.spl
```

Disable all 3 flash plugins in Chrome. Then enable one at a time and go to youtube. See if it works. If not. Disable the one you enabled and move on to the next one. Enable it. Refresh youtube page. See whether it works or not. You have 3 flash plugins trying to work in Chrome. You only need one.

---

### Post by daniell59 on 2012-07-07
> **rokytnji said:**
> ```
Flash (3 files) - Version: 11.2 r202
Shockwave Flash 11.2 r202
Name: Shockwave Flash
Version: 11.2 r202
Location: /usr/lib/chromium-browser/plugins/libflashplayer.so
Type: NPAPI
Disable
MIME types:
MIME type Description File extensions
application/x-shockwave-flash Shockwave Flash
.swf
application/futuresplash FutureSplash Player
.spl
Name: Shockwave Flash
Version: 11.2 r202
Location: /usr/lib/flashplugin-installer/libflashplayer.so
Type: NPAPI
Disable
MIME types:
MIME type Description File extensions
application/x-shockwave-flash Shockwave Flash
.swf
application/futuresplash FutureSplash Player
.spl
Name: Shockwave Flash
Version: 10.3 d162
Location: /usr/lib/mozilla/plugins/libflashplayer.so
Type: NPAPI
Disable
MIME types:
MIME type Description File extensions
application/x-shockwave-flash Shockwave Flash
.swf
application/futuresplash FutureSplash Player
.spl
```

Disable all 3 flash plugins in Chrome. Then enable one at a time and go to youtube. See if it works. If not. Disable the one you enabled and move on to the next one. Enable it. Refresh youtube page. See whether it works or not. You have 3 flash plugins trying to work in Chrome. You only need one.
Please explain how to disable Chrome plugins.

Thanks

---

### Post by daniell59 on 2012-07-07
Never Mind!

I see that it is easy to do.

Thanks for your input.

---

### Post by dcsoldschool53 on 2012-07-07
What I was able to tell from your output was, that you have a later version of flash. The newer version is 11.3. It needs to be updated.

---

### Post by dcsoldschool53 on 2012-07-07
> Disable all 3 flash plugins in Chrome. Then enable one at a time and go  to youtube. See if it works. If not. Disable the one you enabled and  move on to the next one. Enable it. Refresh youtube page. See whether it  works or not. You have 3 flash plugins trying to work in Chrome. You  only need one.If you do this make sure that you close chrome, then, reopen it, after you enable each flash setting in chrome that you chose. The only reason I am saying this is to make sure that chrome refreshes itself, and take that setting.

---

### Post by daniell59 on 2012-07-07
I tried disabling then enabling one at a time. It did not help. How can I delete then all, then re-install them?

---

### Post by dcsoldschool53 on 2012-07-07
Theoretically speaking, from my understanding only, if you update one browser, it will update the other one too. This may or may not be true. So my question is again[quote=dcsoldschool53]Quick questions? Do you use the stable or the beta version of flash-aid  in Firefox? What versions of chrome are you using the one in  repositories or did you download it from online?[/quote]

---

### Post by srobles97 on 2012-07-08
I don't think hard drive space is an issue

---

### Post by srobles97 on 2012-07-08
I may have confused some people in this thread. Google Chrome will not open at all. I cannot open a window to check plug-ins. I have un-installed and re-installed Google Chrome already and it still won't work.

---

### Post by srobles97 on 2012-07-08
> **robtygart said:**
> Are you running any add-ons? Popup blockers, Noscript, Flashbock.....?

In Firefox I am running Shockwave Flash 11.2 r202, DivX Web Player, iTunes Application Detector, Quicktime Plug-in 7.6.6, VLC Multimedia Plug-in, and Windows Media Player Plug-in 10.

I cannot check the add-ons in Google Chrome because a window won't open.

---

### Post by Mopar1973Man on 2012-07-08
What little information I can provide.  I found that the 64 Bit Ubuntu works flawless with Adobe flash 64-bit. But now the 2 machines I've play with 32 bit Ubuntu flash don't work at all. Something to do with Adobe's 32 bit files are not right.  

On the 64 bit side I've got flash-aid installed and it updates the browser without a problem. On the 32 bit machines it doesn't work no matter what setting I use.

---

