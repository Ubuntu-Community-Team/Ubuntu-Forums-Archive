---
title: "tail recursion not optimized?!"
date: 2010-10-02
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-02
I had kind of expected that with -O3 optimization, g++ would eliminate the redundant stack frame from tail recursion.
[php]
#include <stdio.h>

int tail(int C) {
	printf("&C = %p\n", &C);
	if (!C) return 0;
	return tail(C - 1);
}

int main() {
	return tail(10);
}
[/php]

...but it doesn't look like it:
```

$> g++ -Wall -O3 tail.cpp
$> ./a.out
&C = 0x7fffe52dfdbc
&C = 0x7fffe52dfd7c
&C = 0x7fffe52dfd9c
&C = 0x7fffe52dfd98
&C = 0x7fffe52dfd94
&C = 0x7fffe52dfd90
&C = 0x7fffe52dfd8c
&C = 0x7fffe52dfd88
&C = 0x7fffe52dfd84
&C = 0x7fffe52dfd80
&C = 0x7fffe52dfd3c

```

I wonder why not :shock:

---

### Post by Npl on 2010-10-02
You are taking the address of C and then pass it to a function, most likely being in an external library. At which point anything could happen, and the compiler must atleast retain the behavior of passing different stack-variables there (Just think if the address got saved in printf for later use, the compiler doesnt knows implementation details)
Theoretically g++ could still be eliminating the recursion BTW. You wont know until you look at the assembly.

Edit: no it doesnt eliminate recursion, however it does if you replace &C with C.
```
int foo( const char *, ... );

int tail(int C) { 
    foo("&C = %p\n", C); 
    if (!C) return 0; 
    return tail(C - 1); 
}
```
compile with "g++ -O3 -S test.cpp" to get a test.s assembly-file. You will see theres no call to tail, only a loop calling function foo.

---

### Post by worksofcraft on 2010-10-02
> **Npl said:**
> ... You wont know until you look at the assembly...


Nice one :) I had hoped to use the address of the parameter to see if the stack frame was being recycled and it was my test that messed it up :shock:

Now that you explained it I found that if I make clear to the compiler that the variable will go out of scope before the next level of recursion it also works and now I can try what I was really after: Tail optimization when a **different** function is being called:

[php]
#include <stdio.h>
int tail2(int);

int tail1(int C) {
	{
		int V;
		printf("tail1 &V = %p\n", &V);
	}
	if (!C) return 0;
	return tail2(C - 1);
}

int tail2(int C) {
	{
		int V;
		printf("tail2 &V = %p\n", &V);
	}
	if (!C) return 0;
	return tail1(C - 1);
}

int main() {
	return tail1(10);
}
[/php]

```

$> g++ -O3 tail.cpp
$> ./a.out
tail1 &V = 0x7fffc1eaeeec
tail2 &V = 0x7fffc1eaeeec
tail1 &V = 0x7fffc1eaeeec
tail2 &V = 0x7fffc1eaeeec
[B]tail1 &V = 0x7fffc1eaeebc
tail2 &V = 0x7fffc1eaeebc
tail1 &V = 0x7fffc1eaeebc
tail2 &V = 0x7fffc1eaeebc
tail1 &V = 0x7fffc1eaeebc
tail2 &V = 0x7fffc1eaeebc
tail1 &V = 0x7fffc1eaeebc[/B]

```


Now isn't that strange :shock: I wonder why it got optimized a few times then suddenly changed and then optimized again some more!

---

### Post by worksofcraft on 2010-10-02
OK I looked at the assembler again and I conclude this is **not** actually **real** tail recursion optimization like would be essential for a Prolog compiler: The new stack frame is not being constructed to *overlay the one that it supersedes*.

What is happening is best described as *inline expansion* of the functions for a number of iterations, thus deferring but not totally eliminating eventual stack depletion.

Alas no use for my state machine that I wanted to make run by getting its operator() to call itself :( Oh well it was just an experiment anyway :)

---

### Post by Npl on 2010-10-02
> **worksofcraft said:**
> Now isn't that strange :shock: I wonder why it got optimized a few times then suddenly changed and then optimized again some more!Thats because the compiler unrolls the loop quite a few times with O3.
I think you missed the important point: if you use referenced to stack variables then the compiler is very crippled in what it can do, if you take addresses and pass it to functions then the compiler has to assume the variable will be alive forever. You did the very same thing again.
In terms of optimizations, well compilers have to make sure that there are **no observable differences** so trying to print out addresses (or anything else really) is futile. Look at the assembly generated, thats your only valid option.
And on a similar note, if you want to see how functions are optimised, dont do so by calling them with a constant number. compile **just the function** and dont call it from main, do so by using the -S switch.

---

### Post by worksofcraft on 2010-10-02
> **Npl said:**
> Thats because the compiler unrolls the loop quite a few times with O3.
I think you missed the important point: if you use referenced to stack variables then the compiler is very crippled in what it can do, if you take addresses and pass it to functions then the compiler has to assume the variable will be alive forever. You did the very same thing again.

Hum... well, to my understanding in C and C++ the variable V goes out of scope at the closing } here.
If it were an instance of a class it's destructor would be called there and it ceases to exist. It was your explanation that made me realize why I could not do it with the parameter.
[php]
{ 
    int V; 
    printf("tail1 &V = %p\n", &V); 
}
[/php]
> **Npl said:**
> 
And on a similar note, if you want to see how functions are optimised, dont do so by calling them with a constant number. compile **just the function** and dont call it from main, do so by using the -S switch.

That is also a very valid point :)
Indeed the compiler could simply expand it ten times, decide the result was zero and optimize **all** the code away... Thus I used a variable from the command line to check, but didn't update the code because it made no difference in this case.

---

### Post by nvteighen on 2010-10-03
Hey, this is an interesting experiment. But, worksofcraft, I'll have to tell you very bad news: not even the Scheme interpreters do tail recursion optimization right... and the Scheme standard states they should. But despite the supposed behaivor, I've been able to crash MIT/GNU Scheme and PLT Scheme... :cry: So, don't expect too much from g++, a compiler for a language where tail-recursion optimization isn't part of the standard...

---

### Post by saulgoode on 2010-10-03
> **nvteighen said:**
> Hey, this is an interesting experiment. But, worksofcraft, I'll have to tell you very bad news: not even the Scheme interpreters do tail recursion optimization right...
How so?

---

### Post by nvteighen on 2010-10-03
> **saulgoode said:**
> How so?

```

MIT/GNU Scheme running under GNU/Linux
Type `^C' (control-C) followed by `H' to obtain information about interrupts.

Copyright (C) 2010 Massachusetts Institute of Technology
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Image saved on Wednesday March 10, 2010 at 2:10:10 AM
  Release 9.0.1 || Microcode 15.1 || Runtime 15.7 || SF 4.41 || LIAR/i386 4.118
  Edwin 3.116

1 ]=> (define (fact n)
  (if (<= n 0)
      1
      (* n
         (fact (- n 1)))))

;Value: fact

1 ]=> (fact 10000000)

;Aborting!: maximum recursion depth exceeded

1 ]=> 

```

EDIT: No, I'm an idiot. That's not tail-recursion... :P

---

### Post by worksofcraft on 2010-10-03
> **nvteighen said:**
> ```

MIT/GNU Scheme running under GNU/Linux
Type `^C' (control-C) followed by `H' to obtain information about interrupts.

Copyright (C) 2010 Massachusetts Institute of Technology
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Image saved on Wednesday March 10, 2010 at 2:10:10 AM
  Release 9.0.1 || Microcode 15.1 || Runtime 15.7 || SF 4.41 || LIAR/i386 4.118
  Edwin 3.116

1 ]=> (define (fact n)
  (if (<= n 0)
      1
      (* n
         (fact (- n 1)))))

;Value: fact

1 ]=> (fact 10000000)

;Aborting!: maximum recursion depth exceeded

1 ]=> 

```

EDIT: No, I'm an idiot. That's not tail-recursion... :P

lol - yes it still has to come back and do the final multiplication by "n" before it can return it's result. It is quite hard to specify problems in a way that is amenable to tail elimination, and it would be nice if the compiler could tell us sometimes.

What I wanted it for is a state machine that parses text of indeterminate length:

On discovering a state change, instead of trying to push-back the token, change state and fetch it again, I wanted to set and call the new state directly with the current token...

Evidently without redundant tail elimination there could be a danger of stack overflow depending on the input text :shock: so if said optimization is not dependable/verifiable then it's not an acceptable implementation :(

---

### Post by NovaAesa on 2010-10-03
This is more of what you want:
```

(define (fact n acc)
  (if (<= n 0)
      acc
      (fact (- n 1) (* acc n))))

```

---

### Post by nvteighen on 2010-10-04
> **NovaAesa said:**
> This is more of what you want:
```

(define (fact n acc)
  (if (<= n 0)
      acc
      (fact (- n 1) (* acc n))))

```

Yeah, I know... If you remember my (now late) FreeTruco project written in Scheme, it was tail-recursion-obsessive... Maybe Common Lisp-style is damaging my brain... uh... :P

---

### Post by worksofcraft on 2010-10-04
Well just checking your example with g++ compiler:
[php]
#include <stdio.h>

long fac(unsigned long N, unsigned long Acc) {
	{
		char C;
		printf("&C=%p\n", &C);
	}
	if (!N) return Acc;
	return fac(N-1, Acc*N);
}

int main(int Ac, char *Av[]) {
	if (Ac <= 1) return printf("give number on command line\n");
	unsigned long N;
	sscanf(*++Av, "%lu", &N);
	return printf("fac(%lu)=%lu\n", N, fac(N, 1));
}
[/php]
shows as follows:
```


$> g++ -O3 fac.cpp
$> ./a.out 20
**&C=0x7fff9e7a5e9f**
**&C=0x7fff9e7a5e5f**
&C=0x7fff9e7a5e5f
&C=0x7fff9e7a5e5f
&C=0x7fff9e7a5e5f
&C=0x7fff9e7a5e5f
&C=0x7fff9e7a5e5f
&C=0x7fff9e7a5e5f
&C=0x7fff9e7a5e5f
&C=0x7fff9e7a5e5f
**&C=0x7fff9e7a5e1f**
&C=0x7fff9e7a5e1f
&C=0x7fff9e7a5e1f
&C=0x7fff9e7a5e1f
&C=0x7fff9e7a5e1f
&C=0x7fff9e7a5e1f
&C=0x7fff9e7a5e1f
&C=0x7fff9e7a5e1f
&C=0x7fff9e7a5e1f
**&C=0x7fff9e7a5ddf**
&C=0x7fff9e7a5ddf
fac(20)=2432902008176640000

```

so I conclude it doesn't do tail recursion elimination but just some inline expanding of functions called :(

However on the bright side I realized I don't need this optimization for my state machine because it will only call next state directly when it wants to use the same input token. That probably will never mean more than one level of recursion :)

---

### Post by spjackson on 2010-10-05
> **worksofcraft said:**
> so I conclude it doesn't do tail recursion elimination but just some inline expanding of functions called :(

Surely, that *is *tail recursion elimination. What are you expecting instead? What does the assembler show?

---

### Post by worksofcraft on 2010-10-05
> **spjackson said:**
> Surely, that *is *tail recursion elimination. What are you expecting instead? What does the assembler show?

I explained that post #4: "**The new stack frame is not being constructed to overlay the one that it supersedes**."

Certainly expanding a number of iterations inline does eliminate **some** tail recursion but it's not the same thing. This one does real tail call elimination:

[php]
#include <stdio.h>
#define getchar() 'z'

void (* volatile F)(char); // can't expand this at compile time!

void copy_in_to_out(char C) {
	putchar(C);
	C = getchar();
	if (C != EOF) (*F)(C);
}

int main() {
	F = copy_in_to_out;
	copy_in_to_out(getchar());
	return 0;
}
[/php]

A function pointer is not known at compile time so it can't be expanded. Yet in this case it can still run indefinitely without crashing.

Does the above explain the difference for you?

---

### Post by slavik on 2010-10-05
you are using -O3 which optimizes for code speed, try -O2 which optimizes for code size.

Also, compile with -S to get the assembly code without printing the address.

---

### Post by spjackson on 2010-10-05
> **worksofcraft said:**
> Does the above explain the difference for you?
Yes, I now follow what you were saying.

An important difference between your example in post #13 that doesn't result in full tail recursion optimisation and post #15 where it does is your use of the address of operator - but you are aware of this because it was raised earlier in this thread.

The reason why using the address of operator prevents tail recursion optimisation is covered on pages 36-38 of this document [http://www.complang.tuwien.ac.at/schani/diplarb.ps](http://www.complang.tuwien.ac.at/schani/diplarb.ps)

---

### Post by worksofcraft on 2010-10-05
> **spjackson said:**
> 
The reason why using the address of operator prevents tail recursion optimisation is covered on pages 36-38 of this document [http://www.complang.tuwien.ac.at/schani/diplarb.ps](http://www.complang.tuwien.ac.at/schani/diplarb.ps)
That is a very interesting and comprehensive article on the subject :) It took me quite a while to digest and eventually my understanding of the issue was 6.5: "An address of a non-static local variable of the function may only be stored in another non-static local variable of that function."

It is interesting because by preventing the compiler from following the logic to where I print the address on the stack* would* allow the compiler to do full tail elimination :shock:

```

#include <stdio.h>
#define getchar() 'z'

typedef void (* volatile fptr)(char);

fptr E, F;

[B]void stack_track(char C) {
	printf(" stack at %p\n", &C);
}[/B]

void copy_in_to_out(char C) {
	putchar(C);
	int U = getchar();
	**(*E)(U);**
	if (U != EOF) (*F)(U);
}

int main() {
	**E = stack_track;**
	F = copy_in_to_out;
	copy_in_to_out(getchar());
	return 0;
}

```

I suppose part of the problem is that tail elimination is neither a speed nor a size optimization, but one that reduces run time memory requirements... another might be as someone else mentioned,  that it is perhaps not seen as an important optimization for the kind of programs one writes in C or C++.

---

