---
title: "understanding typeof declarations"
date: 2010-09-09
forum: Programming Talk
---

### Post by jamesbon on 2010-09-09
I read
[http://gcc.gnu.org/onlinedocs/gcc/Typeof.html](http://gcc.gnu.org/onlinedocs/gcc/Typeof.html)
but I was not able to understand what is the meaning of typeof.
Any help would be appreciated.
Specially if you can give some example.
I was going through include/linux/kernel.h
encountered typeof here
```

/**
 * container_of - cast a member of a structure out to the containing structure
 * @ptr:        the pointer to the member.
 * @type:       the type of the container struct this is embedded in.
 * @member:     the name of the member within the struct.
 *
 */
#define container_of(ptr, type, member) ({                      \
        const typeof( ((type *)0)->member ) *__mptr = (ptr);    \ 
```

So I specially want to understand use of typeof with respect to this.
        (type *)( (char *)__mptr - offsetof(type,member) );})

---

### Post by mateom on 2010-09-09
What typeof does is "return" the type of the expression passed as an argument. For example, the following code

```

int x;
typeof (x) b;

```
declares a int variable called b.

Let's analize step by step the code you show:

```

const typeof( ((type *)0)->member ) *__mptr = (ptr);

```

First, whats inside typeof: *((type *)0)->member.* This casts a NULL pointer to the type specified as the second argument in the macro. The typeof of the expression returns the specific type of the member specified as the third parameter in the macro.

Then it declares a const THE_RETURNED_TYPE* variable called __mptr and assigns the value specified as the first argument of the macro.

For example, the code

```

typedef struct {
   int int_member;
} AStruct;

container_of (value, AStruct, int_member);

```is equivalent to

```

typedef struct {
   int int_member;
} AStruct;

const int *__mptr = value;

```

---

### Post by jamesbon on 2010-09-10
Hi, **mateom** thanks with your wonderful explanation I understood the concept.

---

