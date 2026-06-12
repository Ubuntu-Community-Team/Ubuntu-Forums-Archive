---
title: "OpenGL 2.0 support missing"
date: 2007-04-10
forum: Programming Talk
---

### Post by payton on 2007-04-10
I have recently moved to the Ubuntu edgy 6.1 platform from Windows and I am going to do quite a lot of 3D programming. 

I have decided on using Code::Blocks as the IDE, but have problems compiling my program. It gets problems with functions etc. that belongs to Open GL 2.0, i.e.

```

glglobals.h:61: error: &#8216;glGetShaderiv&#8217; was not declared in this scope
glglobals.h:65: error: &#8216;glGetShaderInfoLog&#8217; was not declared in this scope.

```

I have installed mesa-common-dev package but for some reason it seems to be an old version of this. I have been able to compile this program earlier using other IDE's, but not in Code::Blocks. I just wonder if it looks in the wrong place for the open gl definitions.

My driver seems to be working alright, output from 
```
glxinfo | grep OpenGL && glxinfo | grep direct 

```
is
```

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.6011 (8.28.8)
OpenGL extensions:
direct rendering: Yes

```

Does anyone have a clue what I am doing wrong, I suppose there must be something since I was able to compile this before !?!

All help would be much appreciated.

---

### Post by slavik on 2007-04-10
maybe code blocks uses some other include directories instead of system-wide stuff. also, did you make sure to link to proper libraries? (-llibMesa I think it is).

---

### Post by payton on 2007-04-11
Thanks for your reply!

I do think Code Blocks is looking in the right location. the problems occur during compilation, I haven't got to linking yet. I do run other Open GL programs from Code Blocks, just not with shader functionality.

I have a sneaking suspicion after checking out Mesa's web site that they do not yet support Open GL 2.0, but I am not sure of this. Any ideas?

---

