---
title: "libEGL warning: DRI2: failed to authenticate"
date: 2013-01-22
forum: Programming Talk
---

### Post by erreina on 2013-01-22
I start working with OpenGLES using mesa on ubuntu 12.04 and when I run any program this message appears:

<message>
libEGL warning: DRI2: failed to authenticate
libEGL warning: DRI2: failed to open swrast (search paths /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri)
</message>

If the program is runned as root onle the first warning is displayed. I run eglinfo (download from [http://pastebin.com/Vnje5sEe]("http://pastebin.com/Vnje5sEe") and then gcc -o eglinfo eglinfo.c -lEGL -lGLESv2) and this is the output:

<output>
libEGL warning: DRI2: failed to authenticate
libEGL warning: DRI2: failed to open swrast (search paths /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri)
EGL
  Vendor: Mesa Project
  Version: 1.4 (Gallium)
  Client APIs: OpenGL OpenGL_ES OpenGL_ES2 OpenVG 
  Extensions: EGL_KHR_image_base EGL_KHR_reusable_sync EGL_KHR_fence_sync EGL_KHR_surfaceless_gles1 EGL_KHR_surfaceless_gles2 EGL_KHR_surfaceless_opengl 
OpenGL ES
  Vendor: VMware, Inc.
  Renderer: Gallium 0.4 on llvmpipe (LLVM 0x300)
  Version: OpenGL ES 2.0 Mesa 8.0.4
  GLSL version: OpenGL ES GLSL ES 1.0.16
  Extensions: GL_EXT_blend_minmax GL_EXT_multi_draw_arrays GL_OES_draw_texture GL_EXT_texture_format_BGRA8888 GL_OES_compressed_ETC1_RGB8_texture GL_OES_depth24 GL_OES_element_index_uint GL_OES_fbo_render_mipmap GL_OES_mapbuffer GL_OES_rgb8_rgba8 GL_OES_standard_derivatives GL_OES_stencil8 GL_OES_texture_3D GL_OES_texture_npot GL_OES_EGL_image GL_OES_depth_texture GL_OES_packed_depth_stencil GL_EXT_texture_type_2_10_10_10_REV GL_NV_fbo_color_attachments GL_OES_EGL_image_external GL_NV_draw_buffers 
  Implementation limits:
    GL_MAX_COMBINED_TEXTURE_IMAGE_UNITS = 32
    GL_MAX_CUBE_MAP_TEXTURE_SIZE = 4096
    GL_MAX_FRAGMENT_UNIFORM_VECTORS = 4096
    GL_MAX_RENDERBUFFER_SIZE = 16384
    GL_MAX_TEXTURE_IMAGE_UNITS = 16
    GL_MAX_TEXTURE_SIZE = 4096
    GL_MAX_VARYING_VECTORS = 16
    GL_MAX_VERTEX_ATTRIBS = 16
    GL_MAX_VERTEX_TEXTURE_IMAGE_UNITS = 16
    GL_MAX_VERTEX_UNIFORM_VECTORS = 4096
    GL_MAX_VIEWPORT_DIMS = 16384, 16384
</output>

What am I missing?

Please your comments will be more than welcome.

Best regards,
Ernesto

---

