---
title: "Repository protection"
date: 2009-03-14
forum: Packaging and Compiling Programs
---

### Post by Robbyx on 2009-03-14
I suggested to a repository holder that he add an authentication key to his repository. He has said that it is difficult to do because to quote him:

> As I have ALSA 1.0.19 installed ; each time I compile the package it automatically adds a dependency to 1.0.19 forcing everyone to upgrade alsa.

So right now, after I compile I run a script that directly edit the package and replace the dependency of alsa from 1.0.19 back to 1.0.17 .. doing so change the signature of the package and if signature was enforced it wouldn't install anymore.



He seems to be talking about package signature but I am just suggesting he add a key to his repository.  Does anyone know how that is done?

Robin

---

