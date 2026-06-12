---
title: "How to programing in 64bit."
date: 2008-12-05
forum: Programming Talk
---

### Post by Arukas on 2008-12-05
I've been getting back into programming.  When I started, there weren't any 64bit processors.  

From what I read, if you have source code for 32bit, and compile it into a 64bit application.  It makes some use of the 64bit benefits, but is still essentially a 32bit program running in an 64bit environment.

Now all the books I have on programing basically say, here's how the language works, and then let the compile do the magic. From what I understand, there's more to 64bit than compiler magic.


So Does anyone know any books, links or tutorials?  Everything, I read is just generalizations that don't help.  

-Thanks

---

### Post by snova on 2008-12-05
Assuming a high level language, there should be no trouble. One of the differences, however, I think will be in the sizes of some of the integer types.

---

### Post by psusi on 2008-12-06
Unless you are planning on writing hand optimized assembly, just let the compiler worry about it and write code like you always have.

---

### Post by mmix on 2008-12-06
same, except that pointer size isn't 4bytes.

---

### Post by bostonaholic on 2008-12-06
Like stated above, it's mainly for lower level languages like ASM and SPARC.  It will be language dependent though, what language are ou programming in?

---

### Post by jespdj on 2008-12-06
> **Arukas said:**
> From what I read, if you have source code for 32bit, and compile it into a 64bit application.  It makes some use of the 64bit benefits, but is still essentially a 32bit program running in an 64bit environment.
If you compile it with a 64-bit compiler, then the result will be a 64-bit native program. The compiler will optimize it for 64-bit automatically to a great extent (for example, it will automatically use the more and larger processor registers, and use the x86_64 calling convention, which is to pass parameters in registers instead of on the stack).

There's really not that much that you have to do yourself if you're programming in a higher level programming language. There are some things that you have to take into account, for example that pointers are not 32-bit anymore (as already said above).

---

### Post by Arukas on 2008-12-06
I figured writing in ASM would be different. I've also read that pointers will not be the same size.  However, I have read nothing that suggest that the data types will be different.  

Pointers being a difference size makes since.  But the other variable data types being different sizes sounds like something you should know if you playing in 64bit land.

---

### Post by wmcbrine on 2008-12-06
In gcc, pointers and longs become 64 bits. ints remain 32 bits. This is a problem mainly for programs that erroneously expect ints and longs to be interchangeable.

---

### Post by scourge on 2008-12-06
> **wmcbrine said:**
> In gcc, pointers and longs become 64 bits. ints remain 32 bits. This is a problem mainly for programs that erroneously expect ints and longs to be interchangeable.

Yup. One should never assume any exact size for short int, int, or long int. stdint.h has exact-width integers for that.

---

