---
title: "Compile a so module from a patch"
date: 2008-12-01
forum: Packaging and Compiling Programs
---

### Post by nolanpro on 2008-12-01
Hi gurus! As far as compiling c code, my knowledge is limited to configure,make,make install..... but I'm trying....

So when I came across a patch (pip vhook for ffmpeg) that I would really like to compile into a so module, I was stumped.

The strange thing is that the author calls it a patch, but he also calls it a self contained plugin. It also has a make file patch, whats that?

I'm hoping anyone has any advice for how to get started with applying patches. Would it involve recompiling ffmpeg even though vhooks are separate (/usr/bin/vhook)? If it's a patch, what would I apply it to?

I've included the 2 files. One is abridged to fit the forum size requirements.

The page on this is here: [http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2006-October/017666.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2006-October/017666.html)

(I know vhooks is depreciated for ffmpeg but I just cant figure out how to do it any other way)

Thanks!

---

### Post by PmDematagoda on 2008-12-01
If there is a patch for the makefile included, then you can compile that plugin by passing the required arguments to configure(or it maybe there by default).

Just patch the source with:-
```
patch -p1 < name-of-patch
```
for both files and then compile the source in the normal way.

---

