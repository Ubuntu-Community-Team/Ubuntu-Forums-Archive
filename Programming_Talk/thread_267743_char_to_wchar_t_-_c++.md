---
title: "char to wchar_t - c++"
date: 2006-09-29
forum: Programming Talk
---

### Post by Dutchie90 on 2006-09-29
how can i convert a char to wchar_t?
i also like a little sample code, and not just:
thisfunction();


thanks...

---

### Post by po0f on 2006-09-29
Dutchie90,

This won't work?  (Sorry if I show my ignorance of wide characters):
```
char c;
wchar_t w;
w = (wchar_t)c;
```

[EDIT]

Yes, I am stupid.

After a quick look through my handy reference book, I believe this is the function you want:
```
#include <cstdlib>

int mbstowcs(wchar_t *out, const char *in, size_t size);
```

Sorry I can't give you an example.  Like I said, I probably don't know what I'm talking about when it comes to wide characters.

---

### Post by Dutchie90 on 2006-09-29
i get this error i use the last one:
Segmentation fault


and the first one doesn't work either... any other solution?

---

### Post by thumper on 2006-09-29
As long as you are only converting a single char then
```
char c = 42;
wchar_t w = c;
```should work.

The complexity comes when you are using encoded characters such as UTF-8.

---

### Post by Dutchie90 on 2006-09-29
i have to do it for a simple chat thing. im using irrlicht(a game engine) for it, because i want to use irrlicht later for making games(wich is still far away i guess :P)... and i also want to use zoidcom(a networking api) for it, and that's why im making a simple chat program.
but the problem is dat irrlicht needs to use wchar_t and that i have used chars to copy username + : + his text to be put on the client.
so i need a way to convert char to wchar_t

---

