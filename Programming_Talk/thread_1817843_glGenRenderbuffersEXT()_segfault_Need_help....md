---
title: "glGenRenderbuffersEXT() segfault? Need help..."
date: 2011-08-03
forum: Programming Talk
---

### Post by MR.UNOWEN on 2011-08-03
Anyone have a clue why glGenRenderbuffersEXT() would segfault? I'm using Qt QGLWidget.

```
ScreenItem::ScreenItem(int img) : Manager()
{
   mTexImg = img;

   glEnable(GL_TEXTURE_2D);


   // create a texture object
   glGenTextures(1, &mTexBack);
   glBindTexture(GL_TEXTURE_2D, mTexBack);
   glTexParameterf(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
   glTexParameterf(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR_MIPMAP_LINEAR);
   glTexParameterf(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_CLAMP_TO_EDGE);
   glTexParameterf(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_CLAMP_TO_EDGE);
   glTexParameteri(GL_TEXTURE_2D, GL_GENERATE_MIPMAP, GL_TRUE); // automatic mipmap
   glTexImage2D(GL_TEXTURE_2D, 0, GL_RGBA8, SysInfo::width(), SysInfo::height(), 0,
                GL_RGBA, GL_UNSIGNED_BYTE, 0);
   glBindTexture(GL_TEXTURE_2D, 0);
printf("P %d\n", &mDepth);
   // create a renderbuffer object to store depth info
   glGenRenderbuffersEXT(1, &mDepth);
printf("dP\n");
   glBindRenderbufferEXT(GL_RENDERBUFFER_EXT, mDepth);
printf("ddP\n");
   glRenderbufferStorageEXT(GL_RENDERBUFFER_EXT, GL_DEPTH_COMPONENT,
                                SysInfo::width(), SysInfo::height());
printf("dP\n");
   glBindRenderbufferEXT(GL_RENDERBUFFER_EXT, 0);
printf("P\n");
   // create a framebuffer object
   glGenFramebuffersEXT(1, &mFBO);
   glBindFramebufferEXT(GL_FRAMEBUFFER_EXT, mFBO);
printf("P\n");
   // attach the texture to FBO color attachment point
   glFramebufferTexture2DEXT(GL_FRAMEBUFFER_EXT, GL_COLOR_ATTACHMENT0_EXT,
                                GL_TEXTURE_2D, mTexBack, 0);
printf("P\n");
   // attach the renderbuffer to depth attachment point
   glFramebufferRenderbufferEXT(GL_FRAMEBUFFER_EXT, GL_DEPTH_ATTACHMENT_EXT,
                                GL_RENDERBUFFER_EXT, mDepth);
printf("P\n");
}
```

```
f
gggggga
adddddd
P 144564912
Segmentation fault
```

---

### Post by Bachstelze on 2011-08-03
```
   glGenRenderbuffersEXT(1, &mDepth);
printf("dP\n");
   glBindRenderbufferEXT(GL_RENDERBUFFER_EXT, mDepth);
```

Is the second argument mDepth or &mDepth. ;) Also, never use %d to printf a pointer, use %p.

---

### Post by MR.UNOWEN on 2011-08-03
its segfaulting on    glGenRenderbuffersEXT(1, &mDepth); and the arguments are correct. mDepth is just an int.

---

### Post by Bachstelze on 2011-08-03
Oh, never mind, I misread. Then I have no idea, sorry. Wait for someone proficient on OpenGL, or try asking on their mailing lists.

---

