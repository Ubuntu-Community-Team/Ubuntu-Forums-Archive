---
title: "Why is GMP not working on this code?"
date: 2011-06-05
forum: Programming Talk
---

### Post by strategically dumb on 2011-06-05
I am starting with Ubuntu, and I got Code::Blocks (never used it before) to program in C.
Of course I ran into troubles, and found ways to get things done eventually.

But then I had to use the GMP to handle very large numbers, and there things got so frustrating that I can't even find the words to describe it.

My problem is that when I use this code:
```

#include <gmp.h>
#include <stdio.h>

int main() {

mpz_t nm,rez ;
mpz_init (nm);
mpz_init(rez);
unsigned long i = 0;

mpz_ui_pow_ui(nm , 2 , 1000);

while (mpz_sgn(nm)) {
i += mpz_mod_ui(rez, nm , 10);
mpz_fdiv_q_ui(nm , nm , 10);
}

return printf("%lu\n" , i);

}
```the builder says:
> 
8: undefined reference to '__gmpz_init'
9: undefined reference to '__gmpz_init'
12: undefined reference to '__gmpz_ui_pow_ui'
15: undefined reference to '__gmpz_fdiv_r_ui'
16: undefined reference to '__gmpz_fdiv_q_ui'What do I have to copy where to make things work?
Thanks

And yes, I have tried my best, but it's been more than 15 hours and I am stuck here....

---

### Post by wmcbrine on 2011-06-05
No copying needed. You just have to tell the compiler to link against the GMP library at build time. I'm not familiar with Code::Blocks, so I can't advise you there, but if you were building it from the command line, you'd just add "-lgmp" to the gcc options.

---

### Post by strategically dumb on 2011-06-06
Thaks for the answer.
However, I am not using gcc from the command line, but Code::Blocks, and that's why i was asking what to put where...

In Code::Blocks, settings -> Compiler and debugger settings -> Linker settings
Linker libraries: What libraries do i have to put there? Where are they? In the gmp package there are no .lib

Very very very frustrating.

---

### Post by r-senior on 2011-06-06
I don't use it but "linker flags" is the thing to search for:

[http://www.mr337.com/blog/?p=77](http://www.mr337.com/blog/?p=77)

If you can find that screen and put -lgmp in the "Other linker options" box, that should work. It's the same deal as linking to the maths libraries with -lm.

---

### Post by strategically dumb on 2011-06-06
It worked!! (tears of joy...)
I love you guys, you two go get a coffee on me (too soon to get a beer).

:grin:

---

### Post by ziekfiguur on 2011-06-06
> **strategically dumb said:**
> Thaks for the answer.
However, I am not using gcc from the command line, but Code::Blocks, and that's why i was asking what to put where...

In Code::Blocks, settings -> Compiler and debugger settings -> Linker settings
Linker libraries: What libraries do i have to put there? Where are they? In the gmp package there are no .lib

Very very very frustrating.

On linux libraries have either a .a extension for static libraries or .so (often .so.versionnumber) for shared libraries. for instance, on my system i have /usr/lib/libgmp.a /usr/lib/libgmp.so.3.5.2 /usr/lib/libgmp.so.3 and /usr/lib/libgmp.so where the last two are symbolic links to the second one.
I'm not very familiar with codeblocks, but i think you could just put gmp with the linker libraries, the linker will pick the right one depending on wether you use the -static flag

---

