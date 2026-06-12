---
title: "OpenGL DDS compressed texture problem"
date: 2008-10-22
forum: Programming Talk
---

### Post by jefftimesten on 2008-10-22
I am having trouble getting any DDS textures to show up in my c++ application. They just show up as white. I am getting an "invalid enum" error from my glCompressedTex2d, which is supposed to mean that 1) internalformat is one of the generic compressed internal formats, or 2) target is not set to GL_TEXTURE_2D. Neither of these are true. I am using GL_TEXTURE_2D as the target, and I am definitely using GL_COMPRESSED_RGBA_S3TC_EXT5_EXT. A call to glGetString( GL_COMPRESSED_TEXTURE_FORMATS ) returns: GL_EXT_texture_compression_dxt1
GL_EXT_texture_compression_s3tc

This same code and texture works fine on my mac, but when I bring it to Ubuntu, it spits errors at me. I am using Andreas Jonsson's DDS texture loader that I found at the bottom of this page: [http://www.codesampler.com/usersrc/usersrc_7.htm](http://www.codesampler.com/usersrc/usersrc_7.htm)

I am running this app in Parallels on my MacBook Pro, so the setup is kind of crazy. But I think it should be able to run fine on both platforms.  According to the tests that I do in the app, it should support compressed textures.  However, in my [glxinfo]("http://stuff.jeffcrouse.info/glxinfo.txt"), it says nothing about compressed textures.  

If anyone has any ideas what might be going on here, I would very much appreciate some help.

Thanks!

[edit]
PS:  I explained my situation a little better here: [http://www.openframeworks.cc/forum/viewtopic.php?p=6489]("http://www.openframeworks.cc/forum/viewtopic.php?p=6489")

---

