---
title: "Shader program fails to compile on Linux with nvidia drivers 195.36.24"
date: 2010-10-20
forum: Programming Talk
---

### Post by pootle42 on 2010-10-20
I'm starting to write an opengl program on Linux (Ubuntu 10.06).

I've used lots of the OpenGL 2.x calls without problems, but I've just bought edition 5 of the superbible to learn about OpenGL 3 capabilities, and when I try and run the Cubemap program from chapter 7, it fails with
```

The shader at Reflection.vp failed to compile with the following error:
0(5) : error C0201: unsupported version 330
0(8) : warning C7532: global type vec4 requires "#version 100" or later
0(9) : warning C7532: global type vec3 requires "#version 100" or later
0(11) : warning C7532: global type mat4 requires "#version 100" or later
0(13) : warning C7532: global type mat3 requires "#version 100" or later
0(17) : warning C7022: unrecognized profile specifier "smooth"
0(17) : error C0502: syntax error at token "smooth"
0(17) : error C5060: out can't be used with non-varying vVaryingTexCoord
0(26) : warning C7532: global function normalize requires "#version 100" or later
0(30) : warning C7532: global function reflect requires "#version 100" or later
0(35) : warning C7532: global variable gl_Position requires "#version 100" or later

```
Anyone know how to fix this?

(the earlier demos (that don't use shaders) work fine.

The software comes from the zip archive at [http://www.starstonesoftware.com/OpenGL/](http://www.starstonesoftware.com/OpenGL/)

---

### Post by pootle42 on 2010-10-21
I updated the drivers to 260.19. and it now runs OK, although some bits don't work right, I suspect that is the program.

Looks like although that driver supports the relevant features, something wasn't knitting together right

---

### Post by xander98989 on 2010-12-06
Same issue, same solution. Funny they don't mention that as a release highlight. Definitely a highlight for me.

---

