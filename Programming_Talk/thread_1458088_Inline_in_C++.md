---
title: "Inline in C++"
date: 2010-04-19
forum: Programming Talk
---

### Post by BramWillemsen on 2010-04-19
Hi,

I've been reading about 'inline functions' on several websites. I decided to test some things myself, but during this procedure i encountered some unexpected things.

During all my tests i compiled with g++ using the -O3 flag for optimal performance. 

I encountered my first problem during this piece of code i wrote. I made a function called 'ret' that did some arbitrary things and then returned an integer. This inline function is called 4 times. The thing i expected is that the code for 'ret' gets inserted at each of the 4 function calls. This would logically result in a larger binary size. The opposite is actually true. If i remove the 'inline' in the function declaration the executable size is larger! More strangely, adding an extra function call in the form of 'int e = ret(5)' does not influence the executable size at all! The program is now printing 5 variables (more work), but the executable size remains the same?
```

#include <iostream>
inline
int ret(int k){
	int a = 9;
	int b = 10;
	int c = k + a + b;
	return c;
}

int main(int argc, char *argv[])
{
	int a = ret(1);
	int b = ret(2);
	int c = ret(3);
	int d = ret(4);
	std::cout << a << b << c << d;
}

```

The second problem is probably related to the last problem. I wrote a piece of code to find out if using inline made the execution speed of a test program any faster. There seems to be **no** noticeable difference between using and not using inline. I expected that there would be a big difference since the function does relatively little work. So the overhead of the function call (stack operations) should be relatively high compared to this if no inline is used. After using the 'time' function in the terminal many times there seems to be no indication of any noticeable speed difference. There is a difference in executable size though (so i assume adding/removing inline does affect the way to compiler treats the code).
```

#include <stdio.h>

inline
unsigned long int add(unsigned long int a, unsigned long int b, unsigned long int c, unsigned long int d, unsigned long int e, unsigned long int f){
	return a + b + c + d + e + f;
}

int main(int argc, char *argv[])
{
	unsigned long int amount = 12000000;
	unsigned long int* testarray = new unsigned long int[amount];
	for (unsigned long int i = 0; i < amount; i++){
		testarray[i]=add(i,i,i,i,i,i);
	}
	printf("final value testarray = %li \n", testarray[amount-1]);
}

```

I'd be very grateful if someone with more experience than me could point me in the right direction. I would like to know more about these (potentially) speed improving features since I'm interested in scientific programming.

---

### Post by MadCow108 on 2010-04-19
in the first case after inlining you only have constants left
so the compiler will eliminate all calculations and insert the result directly
this is not possible without inlining (at least without further hints for the compiler)
so the no-inlining version is larger because it includes the calculation code

this is what remains after inlining (replacing cout with return a+b+c+d for simplicity):
 pushl	%ebp
	movl	$86, %eax
	movl	%esp, %ebp
	popl	%ebp
	ret

no function calls or calculations left, only the result 86

---

### Post by BramWillemsen on 2010-04-19
So instead of inserting the code 4 times (a,b,c,d) the compiler calculates the results for each of the 4 cases since it is based on constants? This way the function body does not have to be compiled?

Then i still don't understand why adding a 5th variable like 'int e = ret(5)' has no effect on the executable size at all. It still has the same amount of bytes.

---

### Post by MadCow108 on 2010-04-19
that must be related to some linker optimizations which maybe merge the calls
in machine code the 5.th and additional cout call variable appears
	movl	$24, 4(%esp) <-- ret(5)
	movl	%eax, (%esp)
	call	_ZNSolsEi <-- cout ret(5)

---

### Post by BramWillemsen on 2010-04-19
Thanks MadCow!

I haven't studied assembly yet so i'll bookmark this page for future reference when i understand that. I kind of got the idea of what you are saying though. 

Finally, does anyone have an idea about the second problem ?

---

### Post by MadCow108 on 2010-04-19
I looked at the assembly and it does not even call the add function in either case but it does not eliminate the loop
so no surprise that it runs equally fast

I'm not sure what exactly it does but it seems to employ some loop optimizations and somehow removes the call

also note that O3 flag may inline functions even when not asked to do so

if you want to test inlining you should use functions dealing with pointers
compilers have a very hard time optimizing pointers (which is one of the reasons unoptimized fortran is often faster than unoptimzed C)

---

### Post by BramWillemsen on 2010-04-19
Thanks! i'll look into this further

---

### Post by phrostbyte on 2010-04-19
> **MadCow108 said:**
> 
compilers have a very hard time optimizing pointers (which is one of the reasons unoptimized fortran is often faster than unoptimzed C)

This was fixed in C99 with the "restrict" keyword. :)

---

### Post by phrostbyte on 2010-04-19
Yeah and as MadCow said with GCC, function inline is an automatic optimization. You might have functions inlined that you didn't ask to be inlined, just because the compiler has a reasonable belief that it will result in faster code. I know some projects (Linux kernel) recommend against using inline because it's rare you can do a better job then the compiler (with this specific optimization at least).

---

### Post by MadCow108 on 2010-04-19
> **phrostbyte said:**
> This was fixed in C99 with the "restrict" keyword. :)

fixed is an optimistic wording :)
it can induce nasty bugs if used wrong and it is not part of the c++ standard (although I think gcc adds it as an extension)
also note I said unoptimized C code. inserting restrict (as any optimization including inline) should be done with care and only if it is necessary for performance

---

### Post by phrostbyte on 2010-04-19
> **MadCow108 said:**
> fixed is an optimistic wording :)
it can induce nasty bugs if used wrong and it is not part of the c++ standard (although I think gcc adds it as an extension)
I rarely see it actually being used

Yes well if you pointers which overlap memory areas and use the "restrict" keyword that is undefined behavior. If you don't use the keyword it is okay. You have to be smart about it, but hey if you using C that is a prerequisite already (IMO). 

The C99 standard isn't widely implemented for some reason. I don't think MSVC implements any of it for instance. GCC supports most of it, but disables C99 by default. So for portable code you must use C89, unfortunately. I don't think there is much C99 code out there at all.

---

### Post by BramWillemsen on 2010-04-19
> **phrostbyte said:**
> Yeah and as MadCow said with GCC, function inline is an automatic optimization. You might have functions inlined that you didn't ask to be inlined, just because the compiler has a reasonable belief that it will result in faster code. I know some projects (Linux kernel) recommend against using inline because it's rare you can do a better job then the compiler (with this specific optimization at least).

Hey,

I guess you need to set certain compiler flags for gcc to automatically inline functions it seems fit ? like -01, -02, or 03 ? So with the right compiler flag enabled i should not really bother with inline-ing at all since the compiler probably knows best? It feels better to use inline to at least mark functions that seem like good candidates. compiler trust issues i guess;)

edit: would a reason for using the inline keyword be that not every compiler does a good job finding the suitable functions? By inline-marking functions you seem fit, does the code becomes more portable maybe?

---

### Post by MadCow108 on 2010-04-19
you can also reverse the argument against inlining

inline is just asks the compiler: please inline if you think its appropriate.
The compiler will apply some heuristics to decide if its worth it.

So you can clutter your code with inlines everywhere and the compiler will choose the best functions to inline and skip the bad ones (in the ideal case).

I personally often put inlines on small functions because I mostly compile with O2 where the compiler does not inline by itself.
But it really is not that important.
I only really bother about it when I need the performance or the executable size **after I have profiled**.

note that functions declared in a class body in C++ are implicitly marked with inline (which again does not mean they will be inlined).

---

### Post by Cracauer on 2010-04-19
As people said, you face constant folding here.

You need to feed in the work to do with parameters that are not known at compiler time. From argv[] would be a good candidate for this small test program.

The compiler is free to ignore inline if it thinks the code with bloat so much that it won't be an advantage anymore.

---

### Post by dribeas on 2010-04-20
In C++, the inline keyword has nothing to do with actually inlining the function, but rather that the function definition can be compiled in more than one translation unit without breaking the One Definition Rule. That is, the function can be in the header, and will not trigger a symbol redefined link error.

The compiler can inline or not the function at will (just as it can with non-inlined functions for which the definition is visible by the compiler, or even not visible and optimized at link time)

---

### Post by MadCow108 on 2010-04-20
standard C++ does have C99 like inline:

> "A function declaration [ . . . ] with an inline specifier declares an inline function. **The inline specifier _indicates_ to the implementation that inline substitution of the function body at the point of call is to be preferred to the usual function call mechanism**. An implementation is not required to perform this inline substitution at the point of call; however, even if this inline substitution is omitted, the other rules for inline functions defined by 7.1.2 shall still be respected."
&#8212; ISO 14882:1998(E), the current C++ standard, section 7.1.2

I think for the single definition thing you have to use static inline not only inline

---

### Post by dribeas on 2010-04-20
> **MadCow108 said:**
> I think for the single definition thing you have to use static inline not only inline

For the single definition rule, plain inline suffices. static has a complete different meaning: internal linkage. The difference is that an inline function (whether inlined or not) is shared by the whole program (all translation units) while static functions are compiled in all translation units (there will be one for each translation unit that includes it). 

From the quote of the standard, the sentence that you did not make bold is the key: actual inlining is optional on the compiler side, so it may inline or not.

Don't take my word for it, just google for it.

---

