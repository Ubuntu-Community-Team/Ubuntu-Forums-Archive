---
title: "[C++] Simple question about size of class"
date: 2010-03-08
forum: Programming Talk
---

### Post by BramWillemsen on 2010-03-08
Hi, i was experimenting a bit with C++ and i encountered something i don't really understand about the size of objects.

on my compiler (GCC 4.4 i think, Karmic). 

[b]sizeof(short) = 2
sizeof(int) = 4[/b]

but if i make an object:

[b]class G{
	short i;
	int j;
};

sizeof(G) = 8, and not 2 + 4 = 6 !. [/b]

How come that when a short and an int are combined the size of 2 ints is made free for the object? I would expect sizeof(G) to return 6, the size of the short (2) plus the size of the int (4). I'm interested in finding out why the compiler frees extra space. Could anyone give me a hint?:)

i included some test code below.
```

#include <stdio.h>
using namespace std;

class G{
	short i;
	int j;
};

int main(int argc, char *argv[])
{
printf("class G contains a short and an int. so sizeof(G) is expected to return 2 + 4 = 6. result is %li \n", sizeof(G));
}

```

---

### Post by SledgeHammer_999 on 2010-03-08
It's called "padding" or "alignment" if I remember correctly. Surely, someone in here will provide a link that documents this.

---

### Post by LKjell on 2010-03-08
Remember that struct and class is the same with some access modification difference in C++.

[http://ubuntuforums.org/showthread.php?t=1423904](http://ubuntuforums.org/showthread.php?t=1423904)

---

### Post by BramWillemsen on 2010-03-08
Thanks guys! I thought i was missing something obvious, but this seems to go a bit deeper. I just read something about padding, but the article you linked seems to be a bit more thorough. 

The thing that surprises me though is that changing the order of variables in your struct/class can actually change the size of it. Why doesn't the compiler put the variables in the order that requires the least padding bytes?

---

### Post by LKjell on 2010-03-08
Because you can write a struct to file and load from file.

---

### Post by BramWillemsen on 2010-03-08
> **LKjell said:**
> Because you can write a struct to file and load from file.

sorry im just a beginning programmer, i don't really see the implications of your statement yet. Could you elaborate a bit more it please?

---

### Post by LKjell on 2010-03-08
How can you load something if the order is totally random to you?

---

### Post by johnl on 2010-03-08
> **BramWillemsen said:**
> Thanks guys! I thought i was missing something obvious, but this seems to go a bit deeper. I just read something about padding, but the article you linked seems to be a bit more thorough. 

The thing that surprises me though is that changing the order of variables in your struct/class can actually change the size of it. Why doesn't the compiler put the variables in the order that requires the least padding bytes?

The following is from the C99 standard.  A similar excerpt (re: classes) is probably somewhere in the C++ standard.

> 
6.7.2.1 Structure and Union Specifiers
13. Within a structure object, the non-bit-field members and the units in which bit-fields reside **have addresses that increase in the order in which they are declared.** A pointer to a structure object, suitably converted, points to its initial member (or if that member is a bit-field, then to the unit in which it resides), and vice versa. There may be unnamed padding within a structure object, but not at its beginning.


The standard guarantees that the members of a struct will be laid out in memory in the order that that you declare them.  Optimizing for size is not always (or even 50% of the time) the desired behavior.  But if you want to optimize for size, you are free to order your structure however you like :)

---

### Post by srs5694 on 2010-03-08
It's possible to load data directly from the hard disk into a class or structure, or write a class or structure straight from memory to the hard disk, in binary form. If the compiler were free to rearrange the order of variables in structures and classes, this wouldn't work reliably, especially should the compiler change its padding rules with a version change or should you recompile with another compiler. Of course, the very padding you've discovered can cause problems with this, too. If you're trying to read a data structure from disk and the compiler pads the items in your class/structure, it might not work, depending on how the on-disk data is arranged. The solution is to use the "pack" pragma:

```

#pragma pack(1)
struct foo {
   uint8_t bar1;
   uint16_t bar2;
   uint32_t bar3;
};

```

This will force the compiler to pack the variables in as tightly as it can. The drawback will be reduced performance, but that may be an acceptable tradeoff in your application; or you can pack just the structures you use for disk I/O and copy the data into another data structure that the compiler can optimize as it sees fit. Note that my example also used unambiguous data type sizes (uint8_t, etc.); the size of the basic types, such as int, can change from one platform to another or from one compiler to another. Something like uint8_t, OTOH, should be the same on any platform or compiler. (IIRC, uint8_t is defined in the stdint.h header file.)

---

### Post by lisati on 2010-03-08
> **BramWillemsen said:**
> sorry im just a beginning programmer, i don't really see the implications of your statement yet. Could you elaborate a bit more it please?

It matters when you're using a struct to describe records in a file. It wouldn't be any good if I wrote a program for my old desktop, and the compiler decided, based on the kind of CPU and other hardware, to put the data in one sequence, and then I wrote a program for my laptop to read the file, using the exact same definition of the data and the compiler, seeing that my laptop has different "innards", decided that a different arrangement of the data would be better. The programs would assign different meanings to the same piece of data. Hope that makes some kind of sense!

---

### Post by dwhitney67 on 2010-03-08
EDIT:  I love it!

---

