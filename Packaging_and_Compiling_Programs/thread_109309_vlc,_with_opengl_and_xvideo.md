---
title: "vlc, with opengl and xvideo?"
date: 2005-12-28
forum: Packaging and Compiling Programs
---

### Post by pelle.k on 2005-12-28
I've managed to compile vlc-trunk from svn with vc1 and some other stuff, but i cant get OpenGL, an xvideo output whatever i do. I thought i would be enough to --enable-opengl --enable-glx --enable-xvideo ...?
Suggestions anyone?

---

### Post by jorgis on 2006-01-07
I have the same problem with the 0.8.4 version. It's really annoying not to have the opengl output, since the fullscreen display gets really pixelated with any other output module.

--enable-opengl and --enable-glx are enabled at default, so that is not what causes this problem (I tried both). 

Perhaps some lib we're missing?

EDIT: could this (from ./configure output) has anything to with this?
> 
[b]checking GL/glx.h usability... no
checking GL/glx.h presence... no
checking for GL/glx.h... no[/b]
checking X11/extensions/Xinerama.h usability... yes
checking X11/extensions/Xinerama.h presence... yes
checking for X11/extensions/Xinerama.h... yes
checking for XineramaQueryExtension in -lXinerama_pic... no
checking for XineramaQueryExtension in -lXinerama... yes
[b]checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no[/b]


---

### Post by Simon80 on 2006-03-15
I was also having compilation problems (with stepmania) because /usr/include/GL/gl.h and GL/glext.h are missing.  I'm guessing that they should be part of libgl1-mesa-dev.  I stole the two headers from my Gentoo installation (from /usr/lib/opengl/ati/include in that install), and my compilation worked.  If you guys would like, I can post them, but eventually this will get fixed, I think, cause it's a pretty serious issue with that package.

---

### Post by lameaim on 2006-04-28
The headers are in mesa-common-dev.

---

