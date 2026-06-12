---
title: "Weird OpenGL error"
date: 2009-05-15
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-05-15
hi, i am learning OpenGl using NeHe's tutorials

i compiled the Linux tutorial with glut and it ran fine

but when i tried to compile my own i get:

```
unknown chip id 0x95c4, can't guess.
```

and it doesnt run

any clue?

---

### Post by jespdj on 2009-05-16
It would maybe help if you posted some more information, for example the source code of the program that produces this error, and where and when exactly you get this error.

What graphics card do you have, what driver are you using, do desktop effects and other OpenGL programs work properly?

---

### Post by Gordon Bennett on 2009-05-16
> **jimi_hendrix said:**
> hi, i am learning OpenGl using NeHe's tutorials

i compiled the Linux tutorial with glut and it ran fine

but when i tried to compile my own i get:

```
unknown chip id 0x95c4, can't guess.
```

and it doesnt run

any clue?

Make sure you link/include the correct OpenGL library paths!

---

