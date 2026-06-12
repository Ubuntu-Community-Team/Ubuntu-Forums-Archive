---
title: "[C] How do you read this? What does it mean?"
date: 2011-03-06
forum: Programming Talk
---

### Post by cguy on 2011-03-06
this:
[php]   extern int *_ _errno_location(void);
   #define errno  (*_ _errno_location())
[/php]

(Edit) and this:
[php] #define SIG_ERR (void (*)())-1
[/php]

Thanks!

---

### Post by Aikar on 2011-03-06
It's basically aliases.

say 


return SIG_ERR;


is same as

return ((void (*)())-1;

But I think they are getting carried away with it.

---

### Post by cguy on 2011-03-06
Aliases, yes.
But the syntax eludes me.


It's part of POSIX.

---

### Post by cguy on 2011-03-06
I also have some questions from an online test I took:


Which of the following statements accurately describes the intended effect of the declaration: int (* a)[10]; ?
Choose only one of the following
An array of ten integers
A pointer to an array of ten integers
An array of ten pointers to integers
An array of ten pointers to functions
No answer


Which of the following is a correct way to write the value 0xAA55 to physical memory address 0x67A9?
Choose only one of the following
uint16_t * p = (uint16_t *) 0x67A9; p = 0xAA55;
uint16_t * p = (uint16_t *) 0xAA55; p = 0x67A9;
* (uint16_t * const) (0x67A9) = 0xAA55;
* (uint16_t * const) (0xAA55) = 0x67A9;
No answer

Thanks!

---

### Post by trent.josephsen on 2011-03-06
What is this, free homework help?

[http://cdecl.org/](http://cdecl.org/)

---

### Post by cguy on 2011-03-06
No. It's free ''I had an online job interview and will have another one tomorrow, this time face to face, so I'm trying to clarify some things''-help.

Thanks for the link, but I dislike the attitude. When you don't like a thread don't contribute.

---

### Post by Arndt on 2011-03-06
> **cguy said:**
> No. It's free ''I had an online job interview and will have another one tomorrow, this time face to face, so I'm trying to clarify some things''-help.

Thanks for the link, but I dislike the attitude. When you don't like a thread don't contribute.

Maybe, but you could clarify things yourself, too, for example say what it is with these questions that you have problems with, not just ask what the answer is.

---

### Post by gmargo on 2011-03-06
You can also install the **cdecl** package and get the same (or similar?) functionality as [http://cdecl.org/](http://cdecl.org/) in a command line tool.

[http://packages.ubuntu.com/maverick/cdecl](http://packages.ubuntu.com/maverick/cdecl)

```

$ cdecl explain "int (* a)[10];"
declare a as pointer to array 10 of int

```

---

### Post by Milliways on 2011-03-07
> **cguy said:**
> No. It's free ''I had an online job interview and will have another one tomorrow, this time face to face, so I'm trying to clarify some things''-help.

Thanks for the link, but I dislike the attitude. When you don't like a thread don't contribute.

cdecl.org will explain c constructs.
It is also available as an executable cdecl

extern int *_ _errno_location(void); is meaningless, but

int * _errno_location(void); means
declare _errno_location as function (void) returning pointer to int

---

