---
title: "sizeof(struct a)"
date: 2011-01-20
forum: Programming Talk
---

### Post by cybo on 2011-01-20
i bumped onto this question on my preparation for a job interview

```
struct a
{
    union b
    {
        char x;
    }B;
    union c
    {
        int y;
    }C;
    struct d
    {
        char z;
    }D;
};

```
What is sizeof(struct a) ?

1.sizeof operator cannot be applied on a user defined data type
2.9
3.12
4.6

i don't think i understand alignment correctly. because in my mind there are two possible answers, 6 and 9, but as it turns out the correct answer is 12. i did lookup alignment online and my answer is still 6 or 9. i did ran the code on my machine and result was 12. i would really appreciate if someone could offer and explanation why the answer is 12.

---

### Post by ibuclaw on 2011-01-20
The 3 bytes padding are added after each char, so what we end up with is this:

```

struct a
{
    // size = 0 bytes
    union b
    {
        char x;
    }B;
    // size = 1 byte
    char[3] _pad1;
    // size = 4 bytes
    union c
    {
        int y;
    }C;
    // size = 8 bytes
    struct d
    {
        char z;
    }D;
    // size = 9 bytes
    char[3] _pad2;
    // size = 12 bytes
};

```

Magic. :)

---

### Post by Simian Man on 2011-01-20
Keep in mind that these answers are totally dependent on your machine and compiler.  You should understand why the compiler does this, but don't rely on this behavior.

---

### Post by worksofcraft on 2011-01-20
> **Simian Man said:**
> Keep in mind that these answers are totally dependent on your machine and compiler.  You should understand why the compiler does this, but don't rely on this behavior.

I completely agree with that :)

For a start some compilers let you pack data structures to have minimum size. I think Microsoft C even has a "pragma" for this so you can turn it on or off selectively for different structures.

Some processors are perfectly happy to fetch data that is not aligned to word or quad word boundaries, for others it will cause significant overhead.

I suspect the language standard even allows the compiler to rearrange the order of fields in a struct, because indexing them by offsets is not a supported feature.

---

### Post by trent.josephsen on 2011-01-20
With -fpack-struct, gcc indeed generates 6.  9 is also acceptable according to the Standard, as is 1, 2, 3, 4, etc.

It's a bad question, but 12 is the "most probable" answer for a system with 8-bit chars and 4-byte words.

IIRC, worksofcraft is right about the compiler being allowed to rearrange the order of fields, with the constraint that two identical struct definitions in two different and independent files must be compatible.  Don't quote me on that.

---

### Post by Stefan J on 2011-01-21
Simian Man is right. The question is simply wrong. The "pragma" keyword is not in the spec. So you can't rely on it. The "implemention" of the structure in the processors memory is done by the compiler. If you working on a System only capable to adress in 4Byte steps (floating point DSPs) the structure is 3x32Bits (sizeof(int) = 1!). If your on a 16Bit Platform with 1Byte and 2Byte Adressmode the structure is 4Byte (2 char @ 1Byte and 2Byte for the int).

---

### Post by Arndt on 2011-01-21
> **trent.josephsen said:**
> With -fpack-struct, gcc indeed generates 6.  9 is also acceptable according to the Standard, as is 1, 2, 3, 4, etc.

It's a bad question, but 12 is the "most probable" answer for a system with 8-bit chars and 4-byte words.

IIRC, worksofcraft is right about the compiler being allowed to rearrange the order of fields, with the constraint that two identical struct definitions in two different and independent files must be compatible.  Don't quote me on that.

Still, using 'offsetof', accessing fields by their offset is a completely reasonable thing to do.

---

### Post by trent.josephsen on 2011-01-21
> **Arndt said:**
> Still, using 'offsetof', accessing fields by their offset is a completely reasonable thing to do.

Quite so; I'd forgotten about offsetof.  Thanks for the half-correction.

---

### Post by worksofcraft on 2011-01-21
> **Arndt said:**
> Still, using 'offsetof', accessing fields by their offset is a completely reasonable thing to do.

While *offsetof* may well be a legitimate macro I do wonder why would anyone want to access a field using numerical byte offsets into the structure that contains it when you can access it by it's proper identifier: "structName.fieldName" :popcorn:

p.s. The new std=c++0x introduces the concept of "tuple" which let's you create a kind of "struct" in which you can address anonymous fields with an ordinal numeric index. TBH I don't really see much point in that either :P

---

### Post by psusi on 2011-01-21
Yes, it depends, so the correct answer to the question is none of the above.  Either the question is flawed, or it is a trick question.

Some compilers will bad the whole structure out to an 8, 16, or 32 byte boundary so it aligns with the cache line size.  Even the size of an int is platform dependent.  I'm working on one now where it is 24 bits.  On amd64, it normally will be 64 bits.

---

### Post by dribeas on 2011-01-21
> **worksofcraft said:**
> I completely agree with that :)
I suspect the language standard even allows the compiler to rearrange the order of fields in a struct, because indexing them by offsets is not a supported feature.

> **trent.josephsen said:**
> 
IIRC, worksofcraft is right about the compiler being allowed to rearrange the order of fields, with the constraint that two identical struct definitions in two different and independent files must be compatible.  Don't quote me on that.

@Josephsen: I am just quoting you on this :) The compiler is not allowed to reorder the fields in the structure in neither C nor C++. In C the storage of the fields in the struct has to be sequenced in the same order of declaration. In C++, the compiler has to keep the order of declaration for the fields within the same *access-specifier* (public, private, protected), but is allowed to reorder the blocks (a compiler may decide that regardless of the order of declaration, public fields are layed out before protected/private members. All current compilers I know of maintain the same order as the declaration, ignoring the access specifiers.

> C++, §9.2/12
Nonstatic data members of a (non-union) class declared without an intervening access-specifier are allocated so that later members have higher addresses within a class object. The order of allocation of nonstatic data members separated by an access-specifier is unspecified (11.1).


> 
C §6.7.2.1/12
Within a structure object, the non-bit-field members and the units in which bit-fields reside have addresses that increase in the order in which they are declared. A pointer to a structure object, suitably converted, points to its initial member (or if that member is a bit-field, then to the unit in which it resides), and vice versa. There may be unnamed padding within a structure object, but not at its beginning.


---

### Post by trent.josephsen on 2011-01-21
Thanks for that catch; I'm glad somebody took the time to look it up in the Standard.

Of course, the point is rather moot, since the only portable way to get the offsets is offsetof... but I suppose you could make a case that for
```
struct st {
    int a;
    int b;
}
```
the C standard requires offsetof(struct st, a) > offsetof(struct st, b).  While obscure, I can imagine that a programmer working on code so deeply involved might like to have such a guarantee.

---

### Post by worksofcraft on 2011-01-21
> **trent.josephsen said:**
> Thanks for that catch; I'm glad somebody took the time to look it up in the Standard.

Of course, the point is rather moot, since the only portable way to get the offsets is offsetof... but I suppose you could make a case that for
```
struct st {
    int a;
    int b;
}
```
the C standard requires offsetof(struct st, a) > offsetof(struct st, b).  While obscure, I can imagine that a programmer working on code so deeply involved might like to have such a guarantee.

Um well I think you can just do as follows:
```

struct st thingy;

void *p = &thingy;
void *pb = &thingy.b;

int offset_b = (char*) pb - (char *)p;

```

... but can you actually think of ANY valid reason why you would need to work with such malarky?
I recommend they simply declare it "undefined" and be done with it.

---

### Post by Npl on 2011-01-22
before C++ it was required to allow structures to be expendable (without the possibility of inheritance). So there is a very good reason the order is fixed.

eg. you can "subclass" struct A by placing it on the top of struct B.
```

struct A {
  .....
};

struct B {
   struct A aVal;
   .....
}

foo(struct A *ptr ) {
}

bar() {
  struct B val;
  
  foo((struct A *)&val); // polymorphism ala C
}

```

(and this is still done similarly within C++ and classes, since it greatly simplifies handling of pointers and references)

---

### Post by worksofcraft on 2011-01-22
> **Npl said:**
> before C++ it was required to allow structures to be expendable (without the possibility of inheritance). So there is a very good reason the order is fixed.

eg. you can "subclass" struct A by placing it on the top of struct B.
```

struct A {
  .....
};

struct B {
   struct A aVal;
   .....
}

foo(struct A *ptr ) {
}

bar() {
  struct B val;
  
  foo((struct A *)&val); // polymorphism ala C
}

```

(and this is still done similarly within C++ and classes, since it greatly simplifies handling of pointers and references)

Lol - that isn't polymorphism ala anything.
Why don't you try:

```

bar() {
  struct B val;
  
  foo(&val.aVal);
}

```

p.s. However I will concede that you do have a good point :)

One might well have need to use offsets of members in C structures when casting a base class into a derived class!

---

### Post by dribeas on 2011-01-22
There are a couple of good reasons to require that ordering. It is obvious that an order is required, else a compiler would be allowed to provide different layouts in different translation units for the same type defined in a common header. The second part is that the order has to be controlled by the programmer, not by the compiler to make sense of some constructs like unions:

```

struct a {
   int a, b;
};
struct b {
   int c, d;
};
union u {
   struct a the_a;
   struct b the_b;
};

```

If there was no exact order controlled by the programmer, there would not be any guarantee that the bit pattern written to 'the_a.a'  would be written in the same position as the 'the_b.c'. In the same way, allocating an object of type 'struct a' and casting the pointer to be of type 'struct b*' could produce different outcomes depending on the phase of the moon or the mood of the compiler.

And of course, the already mentioned case of composition, where the first element in a struct is guaranteed to be aligned with the beginning of the object. Consider the case of parsing a network protocol:

```

struct header { ... }; // header includes a 'type' that identifies the type of message
struct body1 { ... };
struct body2 { ... };
struct message {
    struct header hdr;
    union {
        struct body1 b1;
        struct body2 b2;
        ...
    };
};
...
struct message msg;
int r = read( socket, &msg, sizeof msg.hdr ); // error checking skipped
switch ( msg.hdr.type ) {
case TYPE1: read( socket, &msg.b1, sizeof msg.b1 ); break;
...

```

If the compiler was allowed to reorder the fields, it could happilly change the layout and have the header in a different position, and the above code (which is common) would break. Of course, you can say that reading the message can be fixed by changing the first read to: "read( socket, &msg.hdr, sizeof msg.hdr)", and I would have to agree, but the same type of construct is also used for writing and without the layout guarantee, the programmer would have to perform two writes (first header from its "unknown" position, then body) which could be fine for a stream oriented protocol, but would not work for datagram oriented protocols.

---

### Post by Arndt on 2011-01-22
> **trent.josephsen said:**
> Thanks for that catch; I'm glad somebody took the time to look it up in the Standard.

Of course, the point is rather moot, since the only portable way to get the offsets is offsetof... but I suppose you could make a case that for
```
struct st {
    int a;
    int b;
}
```
the C standard requires offsetof(struct st, a) > offsetof(struct st, b).  While obscure, I can imagine that a programmer working on code so deeply involved might like to have such a guarantee.

This construct used to be common:

struct s {
  int a;
  float b;
  int x[1];
}

The types don't matter for the example, but the point is that one would then do malloc(sizeof(struct s) + (N-1)*sizeof(s.x[0])) and in practice have a pointer to

struct s {
  int a;
  float b;
  int x[N];
}

where N is available only at runtime. For this to work, x obviously has to be guaranteed to be last.

---

### Post by Arndt on 2011-01-22
> **worksofcraft said:**
> Um well I think you can just do as follows:
```

struct st thingy;

void *p = &thingy;
void *pb = &thingy.b;

int offset_b = (char*) pb - (char *)p;

```

... but can you actually think of ANY valid reason why you would need to work with such malarky?
I recommend they simply declare it "undefined" and be done with it.

In reality, history developed the other way around. There didn't use to be a macro 'offsetof' in the language, but people did find a need to define it themselves, in different ways for different compilers. Since there was a need and lots of existing code, the standard added a way to do it portably. C89, I think.

---

### Post by worksofcraft on 2011-01-22
> **dribeas said:**
> There are a couple of good reasons to require that ordering. It is obvious that an order is required, else a compiler would be allowed to provide different layouts in different translation units for the same type defined in a common header...

IMO that is a very feeble reason: The compiler is only required to be consistent with itself.


AFIK there is **no** guarantee about bit pattern equivalences in unions. Similarly also it is non valid to assume any bit pattern equivalence between your protocol headers and binary data blocks that are transferred.

Even simple things like the size, alignment and the byte order of a single integer are not defined. Relying on it is completely non portable.

IMO if you are programming that way then chances are you are producing code that will be highly platform and compiler implementation dependent. :shock:

---

### Post by wmcbrine on 2011-01-22
Aside from the obvious objection that it's implementation-dependent, the question seems intentionally misleading in the way that it uses "union" twice with a single member in each union. (And "union" is rare enough in real use that I had to double-check my understanding of this just now.) It wants to trip you up by making you think that B and C use the same storage, but, they don't.

This doesn't render the question invalid, the way the issue of implementation-dependency does, but it does make it a bit malicious IMHO.

---

