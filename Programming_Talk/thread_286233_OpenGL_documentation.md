---
title: "OpenGL documentation"
date: 2006-10-27
forum: Programming Talk
---

### Post by tpg on 2006-10-27
Does anyone know how can you get man pages (or info pages) for the opengl, glu and glx functions, as they are not included after installing the manpages-dev package. Thanks in advance.

---

### Post by hod139 on 2006-11-21
```

apt-cache search opengl | grep doc

```
one hit returned was: 
mesa-common-dev - Developer documentation for Mesa

---

### Post by slavik on 2006-11-22
look around for a version of the 'red book' online.

---

### Post by amo-ej1 on 2006-11-22
throwing "opengl red book" in google gives you online versions of the opengl tutorial, not that these versions are rather outdated and cover older versions over opengl (typically 1.2, or 1.4) while current releases are 2.1 and higher.

The 'blue book' is a printed version of the opengl manpages, these are simalar to the ones found in the mesa package.

My personal favorite is the green book ;-) which handles opengl programming under (old school) linux. It's rather dated and handles X11 programming and doesn't mention qt/sdl/and other recent version.

---

### Post by tpg on 2006-11-22
Thanks for the feedback. I'm pretty sure the mesa-common-dev package doesn't have the man pages. What I was really looking for, rather than a tutorial, was reference material (when all I need is function arguments etc.), and something that is easily and quickly searched (like man pages, or info pages).

The blue book is useful, although it is rather outdated (I can only find it for OpenGL 1.0 online), and I'd rather not have to buy a book!

---

### Post by slavik on 2006-11-23
> **amo-ej1 said:**
> throwing "opengl red book" in google gives you online versions of the opengl tutorial, not that these versions are rather outdated and cover older versions over opengl (typically 1.2, or 1.4) while current releases are 2.1 and higher.

The 'blue book' is a printed version of the opengl manpages, these are simalar to the ones found in the mesa package.

My personal favorite is the green book ;-) which handles opengl programming under (old school) linux. It's rather dated and handles X11 programming and doesn't mention qt/sdl/and other recent version.
Where did you find 2.1? I thought OpenGL 2.0 was the latest revision ...

---

### Post by tpg on 2006-11-23
You can see the specification for OpenGL 2.1 here:

[http://www.opengl.org/documentation/specs/version2.1/glspec21.pdf](http://www.opengl.org/documentation/specs/version2.1/glspec21.pdf)

---

### Post by amo-ej1 on 2006-11-24
opengl.org mentions 2.1 release ... i knew they were in the 2.x series alreayd and peeking at opengl.org dropped my eye on 2.1 ...

---

