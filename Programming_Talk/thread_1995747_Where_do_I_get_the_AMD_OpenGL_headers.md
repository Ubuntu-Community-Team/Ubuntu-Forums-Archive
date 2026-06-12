---
title: "Where do I get the AMD OpenGL headers?"
date: 2012-06-03
forum: Programming Talk
---

### Post by GlasGhost on 2012-06-03
I installed the AMD with the unofficial AMD instructions from the [[COLOR="Blue"]wiki link on the AMD website[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide"). Then, I installed the [[COLOR="Blue"]AMD APP SDK[/COLOR]]("http://developer.amd.com/sdks/AMDAPPSDK/downloads/Pages/default.aspx").

When trying to compile [[COLOR="Blue"]AMD OpenGL Parallax Mapping Sample[/COLOR]]("http://developer.amd.com/sdks/radeon/pages/RadeonSDKSamplesDocuments.aspx#opengl"). I'm getting 

```
fatal error: GL/glx.h: No such file or directory
```

Where do I get the AMD hardware accelerated OpenGL headers?

---

### Post by roelforg on 2012-06-04
[http://stackoverflow.com/questions/859501/learning-opengl-in-ubuntu](http://stackoverflow.com/questions/859501/learning-opengl-in-ubuntu)
Look at the answer.
 
Note that the whole point of opengl is to be crossplatform, so the "AMD headers" are the same as any others.

---

