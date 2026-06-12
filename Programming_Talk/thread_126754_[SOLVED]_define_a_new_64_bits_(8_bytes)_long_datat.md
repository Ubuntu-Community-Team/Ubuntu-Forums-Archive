---
title: "[SOLVED] define a new 64 bits (8 bytes) long datatype"
date: 2006-02-07
forum: Programming Talk
---

### Post by nuttycat on 2006-02-07
Could someone help me out here? 
For a C program , I need to define a new datatype using typedef (or similar), that can hold the value of 2 unsigned long variables.

I have two unsigned long variables x and y.
I need to create a single variable z that is the combination of both x and y - (something like the strcat( ) for strings.)

the best case scenario would be for me to have a single 64 bit data type.

Can I use unsigned long double?

would this supported by gcc 3.x and/or gcc 4 ?

Thanks,
Nuttycat

---

### Post by skirkpatrick on 2006-02-07
I thought **unsigned long** was 64-bit and **unsigned int** was 32-bit.  I do think I've seen **unsigned long long** used before.

---

### Post by nuttycat on 2006-02-07
unsigned long long sounds promising.
I'll check this out and get back to you.

Thanks,
Nuttycat

---

### Post by hod139 on 2006-02-07
[quote=skirkpatrick]I thought **unsigned long** was 64-bit and **unsigned int** was 32-bit.  I do think I've seen **unsigned long long** used before.[/quote] 
Long (unsigned doesn't change the number of bits) is usually 4 bytes (32 bits), but this is not guarenteed, it may vary depending on the underlying hardware. Int is almost always 32 bits, but again this is not guarenteed. For example, a 64 bit arch may define int to be 64 bits.

nuttycat, it sounds like you want to write a stuct that can hold two unsigned long variables, and define this as a new type. This way you will be guarenteed that you have enough storage for the data. Here is some example C code to get you started, it also prints out the size of int, long, and the new type in bytes:
```

#include <stdio.h>

int main(void){
  printf("The size of unsigned long %d\n", sizeof(unsigned long));
  printf("The size of unsigned int %d\n", sizeof(unsigned int));

  typedef struct 
  {
    unsigned long x;
    unsigned long y;
  } TwoUnsignedLongs;  

  printf("The size of TwoUnsignedLongs %d\n", sizeof(TwoUnsignedLongs));
  
  TwoUnsignedLongs z;
  z.x = 9l;
  z.y = 2l;

return 0;
}

``` 
The output of the code is:
```

The size of unsigned long 4
The size of unsigned int 4
The size of TwoUnsignedLongs 8

``` 
Hope this helps

---

### Post by toojays on 2006-02-08
The C99 standard header stdint.h defines the 64-bit types uint64_t and int64_t.

---

### Post by nuttycat on 2006-02-08
hod139,
Thanks, I think this will do the trick. I will try to implement your "struct" and see how it works.

skirkpatrick, that "unsigned long long" unfortunately did not work. may have something to do with the architecture.

I'll post the results of all this shortly,
Thanks,
Nuttycat

---

### Post by skirkpatrick on 2006-02-08
I had forgotten about stdint.h.  As was stated by others, it's very dependent upon the processor used.  I do most of my programming on embedded systems and on the current DSP I'm using, a long is 64-bits and an int is 32-bits.

---

### Post by nuttycat on 2006-02-12
hod139,
Thanks, your struct with two long's inside was the way that finally worked.
Thanks to all those who posted here.

-Nuttycat
(ps: anyone know if I can close this thread or something to mark it as complete?)

---

