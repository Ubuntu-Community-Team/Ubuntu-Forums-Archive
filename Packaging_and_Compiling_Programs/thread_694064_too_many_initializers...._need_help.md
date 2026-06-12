---
title: "too many initializers.... need help"
date: 2008-02-11
forum: Packaging and Compiling Programs
---

### Post by Takuhari on 2008-02-11
hello, Im not too good at programming yet... but i know some of the basics^^*

When i compile my program, i get this error...


aaa.cpp:96: error: too many initializers for ‘const<anonymous struct> [30]’
aaa.cpp:1423: error: too many initializers for ‘char [20][60]’


I was just wondering what can make this error happen?..

---

### Post by stroyan on 2008-02-12
You can get that error if you have more initializing values than an array is declared to hold.
In this example the character 's' is one too many.
```
$ cat too_many.cpp
void f()
{
    char A[20][60] = {
#define ten_chars    'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j',
#define sixty_chars  ten_chars ten_chars ten_chars ten_chars ten_chars ten_chars 
        sixty_chars sixty_chars sixty_chars sixty_chars sixty_chars 
        sixty_chars sixty_chars sixty_chars sixty_chars sixty_chars 
        sixty_chars sixty_chars sixty_chars sixty_chars sixty_chars 
        sixty_chars sixty_chars sixty_chars sixty_chars sixty_chars 
        's'
    };
}
$ g++ -c too_many.cpp
too_many.cpp: In function ‘void f()’:
too_many.cpp:11: error: too many initializers for ‘char [20][60]’
```

---

