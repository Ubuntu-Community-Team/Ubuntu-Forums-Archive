---
title: "sizeof(pointer) in C?"
date: 2008-11-21
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-21
Why does sizeof(pointer) give me always 4, no matter what is the pointer argument?

Does it give the size of the address itself? How to get the size of the pointer's content then?

I don't understand pointers too well. I have a good book, a lot e-tutorials, but I just don't get them.

---

### Post by psusi on 2008-11-21
> **crazyfuturamanoob said:**
> Why does sizeof(pointer) give me always 4, no matter what is the pointer argument?

Does it give the size of the address itself? How to get the size of the pointer's content then?


Yes, it gives you the size of the pointer, not what it points to.  Dereference the pointer ( *foo ) and take the sizeof that if that is what you want.

---

### Post by bukwirm on 2008-11-21
```
#include <stdio.h>

int main()
{
	char c;
	char* cp = &c;

	printf("sizeof(char*): %d\nsizeof(char): %d\nsizeof(&char*): %d\n", sizeof(cp), sizeof(c), sizeof(*cp));
}
```

Does that answer your question?

(Except psusi beat me to it)

---

### Post by gpsmikey on 2008-11-21
That is the number of bytes used to hold the pointer value.  The only time that will typically change is on a different architecture - for example, the pointer size on an 8 bit machine will probably be 2 bytes (although not always).

mikey

---

### Post by CptPicard on 2008-11-21
Then there is the added complication of arrays... I have even seen questions here where people assume that sizeof returns the length of the array that the dereferenced pointer is the first item of...

---

### Post by mike_g on 2008-11-21
> Then there is the added complication of arrays... I have even seen questions here where people assume that sizeof returns the length of the array that the dereferenced pointer is the first item of...
Thats understandable tho, especially if they are coming from a php background.

---

