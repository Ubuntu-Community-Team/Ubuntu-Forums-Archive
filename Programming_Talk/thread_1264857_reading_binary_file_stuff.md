---
title: "reading binary file stuff"
date: 2009-09-12
forum: Programming Talk
---

### Post by nbo10 on 2009-09-12
Hi all,
I'm reading a binary file. I come to a point where 64 bits is a pointer to a position in the file, say 9C 18 00 00. and the doc says that the order fo the bytes is little endian. How do I go to that position in the file? Thanks

---

### Post by dwhitney67 on 2009-09-12
Specify your programming language; also, provide your apps requirements.  Your OP was a little difficult to digest.

P.S.  9C 18 00 00 is represented using 4 bytes (32 bits).

---

### Post by jpkotta on 2009-09-13
> **nbo10 said:**
> Hi all,
I'm reading a binary file. I come to a point where 64 bits is a pointer to a position in the file, say 9C 18 00 00. and the doc says that the order fo the bytes is little endian. How do I go to that position in the file? Thanks

Little endian means it's written backwards, but (IMHO) is actually in the correct order*.  You can think of it as being stored in an array: [0x9C, 0x18, 0x00, 0x00] where the least significant byte (LSB, the "little end") comes first.  Written as a 32-bit hex number, it would be 0x0000189C.  

Many languages use the fseek() and related functions to set the position in a file handle.  E.g. in python:
```

import os
fd = open(filename_str, "a+b")
fd.seek(0x189C, os.SEEK_SET) # SEEK_SET means offset from beginning of file

```

* I say correct because it's always the same pattern.  If you have a 16-bit value and want to convert it to 32-bit, you can just append 0s (or 1s). With big endian, you have to move bytes around.  Neither big nor little endian is really *correct * in any absolute sense, though.

---

### Post by nbo10 on 2009-09-13
ahh... I forgot to say I'm using c++, or I could use python. I don't know why I can't write code to read binary files. This is the second project that I've had to read some binary data files. The last project I crashed and burned.

---

### Post by Can+~ on 2009-09-13
Binary files are nothing special. If you need to visualize the content of the file, download ghex.

```
sudo apt-get install ghex
```

A little something on binary files:

In C, using the fread(...) function, you can load directly the content of the binary file into a struct or data type, like:

```
struct mystruct
{
    int number;
    char str[20];
}
```

Then, if the file looks like:

```
0f 00 00 00 48 65 6c 6c 6f 20 57 6f 72 6c 64 0a 00 25 c7 bf a9 85 04 08
```

It will load the data trying to fit it directly on the struct, just like a memcpy.

```

|--number--||------------------------char[20]--------------------------|
0f 00 00 00 48 65 6c 6c 6f 20 57 6f 72 6c 64 0a 00 25 c7 bf a9 85 04 08
```

(In this case, this is 15 and Hello World\n\0).

In python, you do a similar thing, although it uses a perl-like (and php-like) [struct format string]("http://docs.python.org/library/struct.html"):

```
"i20s"
```

(integer and 20-byte string)

And for the original question, you just read the number into an int, and use fseek() to that position (SEEK_SET or SEEK_CUR, depending on the specification).

---

### Post by jpkotta on 2009-09-13
> **nbo10 said:**
> ahh... I forgot to say I'm using c++, or I could use python. I don't know why I can't write code to read binary files. This is the second project that I've had to read some binary data files. The last project I crashed and burned.

Yes, but that Python code is not much more than a wrapper around the C library.  In C, it would be more like
```

#include <stdio.h>

...

FILE fh = fopen(filename_str, "a+b");
fseek(fh, 0x0000189C, SEEK_SET);

```

There is probably a more C++-y way of doing it, but I don't really work with C++.  

If this is a popular binary format, there is probably a library you can use to access the file.

---

### Post by dwhitney67 on 2009-09-13
> **jpkotta said:**
> Yes, but that Python code is not much more than a wrapper around the C library.  In C, it would be more like
```

#include <stdio.h>

...

FILE fh = open(filename_str, "a+b");
fseek(fh, 0x0000189C, SEEK_SET);

```

There is probably a more C++-y way of doing it, but I don't really work with C++.  

If this is a popular binary format, there is probably a library you can use to access the file.

Yes, that is right... you need to include a header file, introduce a typo in the C syntax, and basically accomplish the same thing as posted in the Python example.

Jeez...

---

### Post by nbo10 on 2009-09-14
Thanks. The code is coming along now. reading binary stuff is pretty easy in python.

---

