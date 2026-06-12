---
title: "Man pages for OpenGL"
date: 2010-09-21
forum: Programming Talk
---

### Post by Renée Jade on 2010-09-21
Hey guys,

So it's project month for Australian Computer Science students. Pretty exciting! What I need to know is whether there are man pages for OpenGL and GLUT  available, like the man pages for standard C libraries, and where I can find them for Karmic. There was a thread about this many years ago. I would love some more up-to-date info.

Thanks.


Renée.

[COLOR=Blue]EDIT:[/COLOR] Just to clarify that, I am doing a simple project in OpenGL with C language. We're implementing some pretty basic interactive 3D stuff. I'm not 100% sure where that fits in the big scheme of things.

---

### Post by kahumba on 2010-09-21
Afaik you can only get them online (and download if needed), google for "OpenGL 2.1 Reference Pages".

---

### Post by Renée Jade on 2010-09-21
Thanks

---

### Post by cprevoe on 2010-09-26
Hello,

I've successfully installed the OpenGL man pages. 

To do this, first I downloaded the "man" directory from svn as instructed on [http://www.opengl.org/wiki/Getting_started/XML_Toolchain_and_Man_Pages](http://www.opengl.org/wiki/Getting_started/XML_Toolchain_and_Man_Pages) (one link away from the OpenGL Reference). 

Once downloaded, I did the following:
```
sudo apt-get install docbook2x docbook-mathml
cd man
for x in *.xml; do echo Converting $x; docbook2x-man $x; done
for x in *.3G; do Compressing $x; gzip $x; done
mv *.gz /usr/share/man/man3
```

Is this the correct way to install these pages? I am not actually familiar with docbook (or man) and while this method works for me, I'd still like to know what the 'correct' way is.

---

