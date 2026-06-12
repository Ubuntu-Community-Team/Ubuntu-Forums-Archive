---
title: "java web start deployement"
date: 2008-07-12
forum: Programming Talk
---

### Post by dexter.deepak on 2008-07-12
i am fairly new to this so i need some basics.i am trying to make a jnlp file for my java app.
i came through this method for making a jnlp file,but this is for windows;a part of it is:

```
<jnlp spec="1.0+"
  codebase="file:///c:/jdc/jnlp/"
>
```

i cant understand the equivalent for ubuntu.

---

### Post by CptPicard on 2008-07-12
Never done any Java Web Start stuff, but I would suspect it's just your usual URL which can maybe even be http:// or ftp:// or whatever. Just replace the file URL with anything that is appropriate to your project... if it's a local file, with the unix filesystem path.

---

### Post by txcrackers on 2008-07-12
The JNLP docs are pretty clear on this: 

[http://java.sun.com/products/javawebstart/developers.html](http://java.sun.com/products/javawebstart/developers.html)

---

