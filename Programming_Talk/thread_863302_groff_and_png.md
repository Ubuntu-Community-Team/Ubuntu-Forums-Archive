---
title: "groff and png"
date: 2008-07-18
forum: Programming Talk
---

### Post by thirddeep on 2008-07-18
Not sure if this is the right place, but hey, some might argue that groff is a language of it's own :-)

I am trying to insert a png into a document with groff (and output as ps), but not having much luck.

Any pointers would be appreciated.

Thd.

---

### Post by thirddeep on 2008-07-18
For anyone that is interested, I found how to do this.

First, you need to convert the PNG (or any other image I suppose) to eps - encapsulated postscript.

Use this little bit of python I found :

```
import image

if im.mode not in ("L", "RGB", "CMYK"):
	im = im.convert("RGB")

im.save("test.eps")
```

Then, in your file put :

```
.PSPIC <filename.eps>
```

Thd.

---

