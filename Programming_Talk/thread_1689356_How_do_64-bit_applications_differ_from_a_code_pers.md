---
title: "How do 64-bit applications differ from a code perspective?"
date: 2011-02-16
forum: Programming Talk
---

### Post by kittkatt on 2011-02-16
I've never made a 64-bit program before and I don't know the answer and I thought someone here would know.

I understand the concepts of addressing space + ram etc. , but I don't understand why it would make any difference from the perspective of the source code.  If you are calling in your program for more memory to do something, unless you're doing assembly, doesn't the compiler deal with making sure that there is enough memory left to do the stuff that you want?

Is it just a matter of compiling using a compiler that knows that you have 2^64 addresses to use vs 2^32, a 64-bit compiler in other words?

Please enlighten me.

Thanks,

Kitt

---

### Post by Reiger on 2011-02-16
Well for starters bad code might hardcode the size of memory that is allocated with 32bit in mind. For instance allocating an array of pointers as an array of 4byte values would not work on 64bit since the pointers are double that size.

For main there is of course the fact that the instruction set and calling conventions tend to differ. This matters because code compiled for one set will not interoperate with a different set since expectations and conventions are not being met.

---

### Post by worksofcraft on 2011-02-16
> **kittkatt said:**
> I've never made a 64-bit program before and I don't know the answer and I thought someone here would know.

I understand the concepts of addressing space + ram etc. , but I don't understand why it would make any difference from the perspective of the source code.  If you are calling in your program for more memory to do something, unless you're doing assembly, doesn't the compiler deal with making sure that there is enough memory left to do the stuff that you want?

Is it just a matter of compiling using a compiler that knows that you have 2^64 addresses to use vs 2^32, a 64-bit compiler in other words?

Please enlighten me.

Thanks,

Kitt

It depends what programming language you are using. e.g. if you use C then your pointer types become 64 bit and can't be stored in an integer anymore. The "size_t" also becomes a long integer which returns different type from traditional functions like strlen(). It affects things like printf() that have formats specifying integer where long integer is needed...

A lot of that can be avoided by good programming practices but sadly huge amounts of legacy C code were written with all sorts of assumptions :shock:

---

### Post by NovaAesa on 2011-02-16
With (very) high level languages such as Python, Java, LISP etc there is no difference and you have to go to great length to write code that will only work on a 32 bit platform. The only thing you really have to worry about in that case is 32 bit libraries vs 64 bit libraries (this isn't always an issue though).

Reiger is correct, when allocating a block of memory to store pointers in you should do something like alloc(sizeof(void*) * arrLen), rather than alloc(4 * arrLen). Not only it it more readable, it will always work. You should do this even if you are only planning on releasing on a 32 bit platform.

@worksofcraft, why on earth would you store a pointer in an integer anyway? I assume by integer you mean the "int" datatype?

---

### Post by worksofcraft on 2011-02-16
> **NovaAesa said:**
> With (very) high level languages such as Python, Java, LISP etc there is no difference and you have to go to great length to write code that will only work on a 32 bit platform. The only thing you really have to worry about in that case is 32 bit libraries vs 64 bit libraries (this isn't always an issue though).

Reiger is correct, when allocating a block of memory to store pointers in you should do something like alloc(sizeof(void*) * arrLen), rather than alloc(4 * arrLen). Not only it it more readable, it will always work. You should do this even if you are only planning on releasing on a 32 bit platform.

@worksofcraft, why on earth would you store a pointer in an integer anyway? I assume by integer you mean the "int" datatype?

Some people write code that assumes pointers are 4 bytes and some people think they are two bytes and some think that if you subtract one pointer from another you get an "int" result... which... yes the "int" type in C is indeed intended to represent an integer number. I thought that was self evident :confused:

Anyway I vaguely remember original K&R C language specification stating one can convert freely between a pointer and an int without loss of information. So I was trying to explain to the OP that it is because of poor programming practices in legacy code...

As to your question, one might want to cast numbers into pointers when you need to access specific hardware that resides at a specific address like setting the dma controller to blit an image to your video card. Of course you are more likely to only find that in system software but then C was designed specifically for writing the UNIX operating system... something that Python and Java would be less suitable for IMHO.
 
Incidentally Java ONLY runs on the Java virtual machine and I heard a rumor that said Java virtual machine is defined as a 32 bit machine, so it shouldn't really run on 64 bit machines at all and probably will never be using half the bits that the hardware actually has :shock:

---

### Post by nvteighen on 2011-02-17
> **worksofcraft said:**
> It depends what programming language you are using. e.g. if you use C then your pointer types become 64 bit and can't be stored in an integer anymore.

The 'int' data type is defined as the computer word. If your platform is truly 64-bits, it means that 'int' will be 64-bit. Unless you're on a platform with different word sizes for different purposes (e.g. Wikipedia states that the 32-bit Pentium processor always had a 64-bit data bus).

---

### Post by Some Penguin on 2011-02-17
Interoperability.  Things get more interesting when you're sharing data across heterogeneous systems, if you're going for binary formats rather than e.g. JSON.

---

### Post by Npl on 2011-02-17
> **nvteighen said:**
> The 'int' data type is defined as the computer word. If your platform is truly 64-bits, it means that 'int' will be 64-bit. Unless you're on a platform with different word sizes for different purposes (e.g. Wikipedia states that the 32-bit Pentium processor always had a 64-bit data bus).an int is only required to be >= 16bit, and it might even be different on the same architecture with different compilers.
Anecdotal:
[LIST]
[*]a 'word' on the x86 architecture is still 16bit in every piece of documentation
[*]all compilers for x64 (that I know of) define int as 32bit (yet of course pointers are 64bit)
[*]there is no clearcut definition on "bitness" of a plattform. eg. PS2`CPU can do 64 bit operation natively, has 32bit addresspace and a 128bit datapath
[/LIST]

But to the OP: Unless you make assumptions on the exact size of pointers or ints you dont see a difference in higher level languages.

---

### Post by nvteighen on 2011-02-17
> **Npl said:**
> an int is only required to be >= 16bit, and it might even be different on the same architecture with different compilers.
Anecdotal:
[LIST]
[*]a 'word' on the x86 architecture is still 16bit in every piece of documentation
[*]all compilers for x64 (that I know of) define int as 32bit (yet of course pointers are 64bit)
[*]there is no clearcut definition on "bitness" of a plattform. eg. PS2`CPU can do 64 bit operation natively, has 32bit addresspace and a 128bit datapath
[/LIST]


Oh, thanks. I was wrong, then.

---

### Post by johnl on 2011-02-17
The C99 standard introduces a set of typedefs:
[LIST]
[*]**intptr_t** is a signed integer type which can hold a pointer value
[*]**uintptr_t** is an unsigned integer type which can hold a pointer value
[*]**ptrdiff_t** is an integer type that can hold the result of subtracting two pointers.
[/LIST]

In the case that you do need to convert from pointer to integer or vice versa, usage of these types will prevent you from running into any 32-bit vs 64-bit compatibility issues.  

Also, use the correct format-specifier in printf functions:

```

size_t size = 4;
size_t* foo = &size;

printf("%u %x\n", size, foo);  /* bad */
printf("%zu %p\n", size, foo); /* good */

```

---

### Post by NovaAesa on 2011-02-17
> **worksofcraft said:**
> some think that if you subtract one pointer from another you get an "int" result...Fair enough, I've never seen that sort of thing before.
 
> Incidentally Java ONLY runs on the Java virtual machine and I heard a rumor that said Java virtual machine is defined as a 32 bit machine, so it shouldn't really run on 64 bit machines at all and probably will never be using half the bits that the hardware actually has :shock:Java has some 64 bit datatypes such as double and long, which are implemented as 64 bit native types on a 64 bit computers. On 32 bit computers, 64 bit datatypes are stored in two adjacent (?) locations, and extra processing has to be used to manipulate them.

---

### Post by worksofcraft on 2011-02-17
> **johnl said:**
> The C99 standard introduces a set of typedefs:
[LIST]
[*]**intptr_t** is a signed integer type which can hold a pointer value
[*]**uintptr_t** is an unsigned integer type which can hold a pointer value
[*]**ptrdiff_t** is an integer type that can hold the result of subtracting two pointers.
[/LIST]

In the case that you do need to convert from pointer to integer or vice versa, usage of these types will prevent you from running into any 32-bit vs 64-bit compatibility issues.  

Also, use the correct format-specifier in printf functions:

```

size_t size = 4;
size_t* foo = &size;

printf("%u %x\n", size, foo);  /* bad */
printf("%zu %p\n", size, foo); /* good */

```

That's useful to know :)

Personally I don't think the standards commitee people understood what Kernighan and Ritchie intended.

The way I read their book was that it was all designed to maximize performance. Thus the int data type was intended to represent whatever (minimum) size was needed to manipulate memory addresses.

The short data type was meant to be what ever size was most efficiently handled as single cycle ALU instruction (typically the width of a processor register).

A char was meant to be the smallest addressable single unit, so for instance on some DSP processor that could be 48 bits and identical to the short data type...

Long was meant to be the longest kind of integer that there were instructions for e.g. when you multiply two 32 bit registers you would get a 64 bit result, but it doesn't mean the processor can natively do 64 bit arithmetic.

Anyway the standards people have blundered off proliferating endless different integral types like long longs and wchar_16's and strict enums and size_t and evidently intptr_t and uintptr_t so you can choose to have negative memory addresses now too :shock:

---

