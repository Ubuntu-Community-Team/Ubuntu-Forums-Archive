---
title: "OpenGL and Mesh Imports"
date: 2011-01-29
forum: Programming Talk
---

### Post by roadkillguy on 2011-01-29
Are there any classes freely available that import 3d models into OpenGL?  What filetype do they import from?

If there isn't, what 3d mesh files store little data(texture coords, vertices, and faces) in a easily parsed file?

What other options do I have?

Thanks in advance.

---

### Post by roadkillguy on 2011-01-30
Nobody?

---

### Post by talonmies on 2011-01-30
I am wondering what you actually mean when you say "import 3d models into OpenGL". OpenGL is an API. Do you want a library that can generate pre-canned OpenGL code for rendering something that you could compile into another application? Or something else?

---

### Post by roadkillguy on 2011-01-30
I suppose it should read "for USE in openGL"

Maybe just a parser that stores things in arrays, sorry.

---

### Post by talonmies on 2011-01-30
[Assimp]("http://assimp.sourceforge.net/") might do what you want.

---

