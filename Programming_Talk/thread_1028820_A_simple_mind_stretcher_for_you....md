---
title: "A simple mind stretcher for you..."
date: 2009-01-02
forum: Programming Talk
---

### Post by CLomax on 2009-01-02
Here's a slight challenge if you're interested, I just quickly wrote a program and thought it would make for an easy exercise...

**Write a program in any language you please which determines and prints every square number between 0 and 10000.**

Try not to copy any one else's code no matter how tempting it may be.

Hopefully I'll see some replies when I wake up... today.

---

### Post by CptPicard on 2009-01-02
I don't want to spoil this, but let's just say that in Python it's a one-liner... list comprehensions rule :)

---

### Post by monkeyking on 2009-01-02
It might be more interesting to see who can find the fastest program that finds all squarenumbers from 0 to max_int.

---

### Post by Cracauer on 2009-01-02
> **monkeyking said:**
> It might be more interesting to see who can find the fastest program that finds all squarenumbers from 0 to max_int.

That'll really screw the 64 bit SPARC people :)

---

### Post by ghostdog74 on 2009-01-02
> **CptPicard said:**
> I don't want to spoil this, but let's just say that in Python it's a one-liner... list comprehensions rule :)
No big deal. So can Perl/Awk (and others) :)

---

### Post by slavik on 2009-01-02
square number == perfect square?

---

### Post by CLomax on 2009-01-02
> **CptPicard said:**
> I don't want to spoil this, but let's just say that in Python it's a one-liner... list comprehensions rule :)

Haha, well that's a kick in the teeth. :D

Since the "challenge" is dead I might as well post what I came up with...

[PHP]#include <stdio.h>
#include <math.h>

/*=======================================*\ 
*  Program Name: square.c                 *
*  Author: C Lomax                        *
*  Date: Sat 3 Jan 2009 00:35             *
*  Description: This program calculates   *
*  and displays all square numbers where  *
*  the root is between 1 and 100          *
\*=======================================*/

int main()
{
   int a;
   double sqr;

	putchar('\n');
	printf("All square numbers where the root is 1 -> 100:\n");

	for(a=1;a<=100;a++)  //While a is between 1 and 100, +1
	{
		sqr = pow(a,2);        // a^2
		printf("%0.f\t ",sqr);  //print result in columns
	}
   return(0);
}[/PHP]

> square number == perfect square?

Not necessarily, you can do it that way if you want though. I might give it a go.

---

### Post by .Maleficus. on 2009-01-02
> **CptPicard said:**
> I don't want to spoil this, but let's just say that in Python it's a one-liner... list comprehensions rule :)
Hehe... that got me working on list comprehensions again :D.  Are we supposed to post the answer?  I'd like to see what people come up with.  Anyways, as far as time goes, my Python list comprehension was:
```
real	0m0.012s
user	0m0.008s
sys	0m0.004s
```
Probably not the best way to do it either.


Edit:  Looks like we do.  Here's my list comprehension:
[php]print [x**2 for x in xrange(100)][/php]
I'm still new to list comprehensions, so is there a better way to write it?

---

### Post by ghostdog74 on 2009-01-02
> **.Maleficus. said:**
> 
I'm still new to list comprehensions, so is there a better way to write it?

here's some experiment using range of 1000000 for 2 tries
```

# time python -c "for i in xrange(1000000): print i**2" > /dev/null

real    0m8.895s
user    0m8.877s
sys     0m0.008s

# time python -c "print [x**2 for x in xrange(1000000)]" > /dev/null

real    0m8.180s
user    0m8.125s
sys     0m0.044s

# time python -c "for i in xrange(1000000): print i**2" > /dev/null

real    0m8.892s
user    0m8.865s
sys     0m0.012s

# time python -c "print [x**2 for x in xrange(1000000)]" > /dev/null

real    0m8.423s
user    0m8.333s
sys     0m0.060s


```

list comprehension is slightly faster, however the above does not take into account the same output format.

Python aside, awk takes roughly half the time to complete.
```

# time awk 'BEGIN{ for(i=1;i<1000000;i++) print i**2}' > /dev/null

real    0m4.576s
user    0m4.516s
sys     0m0.020s

# time awk 'BEGIN{ for(i=1;i<1000000;i++) print i**2}' > /dev/null

real    0m4.079s
user    0m4.076s
sys     0m0.004s


```


you judge for yourself.

---

### Post by Cracauer on 2009-01-02
All you see there is interpreter startup time and print statement speed.

---

### Post by slavik on 2009-01-02
> **ghostdog74 said:**
> here's some experiment using range of 1000000 for 2 tries
```

# time python -c "for i in xrange(1000000): print i**2" > /dev/null

real    0m8.895s
user    0m8.877s
sys     0m0.008s

# time python -c "print [x**2 for x in xrange(1000000)]" > /dev/null

real    0m8.180s
user    0m8.125s
sys     0m0.044s

# time python -c "for i in xrange(1000000): print i**2" > /dev/null

real    0m8.892s
user    0m8.865s
sys     0m0.012s

# time python -c "print [x**2 for x in xrange(1000000)]" > /dev/null

real    0m8.423s
user    0m8.333s
sys     0m0.060s


```

list comprehension is slightly faster, however the above does not take into account the same output format.

Python aside, awk takes roughly half the time to complete.
```

# time awk 'BEGIN{ for(i=1;i<1000000;i++) print i**2}' > /dev/null

real    0m4.576s
user    0m4.516s
sys     0m0.020s

# time awk 'BEGIN{ for(i=1;i<1000000;i++) print i**2}' > /dev/null

real    0m4.079s
user    0m4.076s
sys     0m0.004s


```


you judge for yourself.
Perl

```

slavik@slavik-desktop:~$ perl -v

This is perl, v5.10.0 built for x86_64-linux-gnu-thread-multi

slavik@slavik-desktop:~$ time perl -e 'use bignum; for (1..1000000) { print $_*$_; }' > /dev/null

real	0m1.047s
user	0m0.924s
sys	0m0.016s
slavik@slavik-desktop:~$ time perl -e 'use bignum; for (1..1000000) { print $_*$_; }' > /dev/null

real	0m0.882s
user	0m0.868s
sys	0m0.008s
slavik@slavik-desktop:~$ time perl -e 'use bignum; for (1..1000000) { print $_*$_; }' > /dev/null

real	0m0.914s
user	0m0.900s
sys	0m0.012s

```

```

slavik@slavik-desktop:~$ time python -c 'print "Hello World"' > /dev/null

real	0m0.018s
user	0m0.008s
sys	0m0.008s
slavik@slavik-desktop:~$ time perl -e 'use bignum; print "Hello World";' > /dev/null

real	0m0.090s
user	0m0.084s
sys	0m0.008s

```

---

### Post by ghostdog74 on 2009-01-02
> **Cracauer said:**
> All you see there is interpreter startup time.
feel free to make the Python interpreter startup faster.

---

### Post by CptPicard on 2009-01-02
The Python vs. awk comparison is not a fair one though, as the awk one does not build the list structure... a while loop in Python would be much faster (don't use range or xrange either)...

(and yes I do feel like a lack of non-list-iteration or non-generator for loop is a wart in Python)...

---

### Post by ghostdog74 on 2009-01-02
> **slavik said:**
> Perl

```

slavik@slavik-desktop:~$ perl -v

This is perl, v5.10.0 built for x86_64-linux-gnu-thread-multi

slavik@slavik-desktop:~$ time perl -e 'use bignum; for (1..1000000) { print $_*$_; }' > /dev/null

real	0m1.047s
user	0m0.924s
sys	0m0.016s
slavik@slavik-desktop:~$ time perl -e 'use bignum; for (1..1000000) { print $_*$_; }' > /dev/null

real	0m0.882s
user	0m0.868s
sys	0m0.008s
slavik@slavik-desktop:~$ time perl -e 'use bignum; for (1..1000000) { print $_*$_; }' > /dev/null

real	0m0.914s
user	0m0.900s
sys	0m0.012s

```

```

slavik@slavik-desktop:~$ time python -c 'print "Hello World"' > /dev/null

real	0m0.018s
user	0m0.008s
sys	0m0.008s
slavik@slavik-desktop:~$ time perl -e 'use bignum; print "Hello World";' > /dev/null

real	0m0.090s
user	0m0.084s
sys	0m0.008s

```

i have a different setup as yours
```

# perl -v

This is perl, v5.8.8 built for i586-linux-thread-multi

# time perl -e 'use bignum; for (1..1000000) { print $_*$_; }' >/dev/null

real    0m5.242s
user    0m3.880s
sys     0m0.052s

# time perl -e 'use bignum; for (1..1000000) { print $_*$_; }' >/dev/null

real    0m4.813s
user    0m3.868s
sys     0m0.140s

# time python -c 'print "Hello World"' > /dev/null

real    0m0.047s
user    0m0.028s
sys     0m0.012s

# time perl -e 'use bignum; print "Hello World";' > /dev/null

real    0m0.251s
user    0m0.100s
sys     0m0.012s

# time python -c 'print "Hello World"' > /dev/null

real    0m0.044s
user    0m0.020s
sys     0m0.016s

# time perl -e 'use bignum; print "Hello World";' > /dev/null

real    0m0.115s
user    0m0.096s
sys     0m0.016s


```

---

### Post by jimi_hendrix on 2009-01-02
> **CptPicard said:**
> I don't want to spoil this, but let's just say that in Python it's a one-liner... list comprehensions rule :)

C one-liner too...

---

### Post by ghostdog74 on 2009-01-02
> **CptPicard said:**
> The Python vs. awk comparison is not a fair one though, as the awk one does not build the list structure... 

The awk snippet is used to compare to that of Python's for xrange loop, not the list comprehension.

> 
a while loop in Python would be much faster (don't use range or xrange either)...

It would be nice if someone can verify that.

---

### Post by .Maleficus. on 2009-01-02
> **ghostdog74 said:**
> The awk snippet is used to compare to that of Python's for xrange loop, not the list comprehension.


It would be nice if someone can verify that.
The setup:
[php]x = 1
while x**2 < 1000000:
    print x**2
    x += 1

real	0m0.013s
user	0m0.008s
sys	0m0.004s[/php]
[php]print [x**2 for x in xrange(1000)]

real	0m0.012s
user	0m0.012s
sys	0m0.000s[/php]
Meh.

I'll try it in C later.  As for my system specs - 64-bit Ubuntu and hardware in sig.

---

### Post by eightmillion on 2009-01-02
Another python version:

> time python -c " print map(lambda n: n**2, xrange(1,1000000))" > /dev/null

real    0m4.304s
user    0m3.592s
sys     0m0.108s

time python -c "print map(lambda n: n**2, xrange(1,1000000))" > /dev/null

real    0m4.212s
user    0m3.672s
sys     0m0.120s

time python -c "print map(lambda n: n**2, xrange(1,1000000))" > /dev/null

real    0m4.216s
user    0m3.724s
sys     0m0.116s



I'm not getting much of a speed difference with awk:

> time awk 'BEGIN{ for(i=1;i<1000000;i++) print i**2}' > /dev/null

real    0m3.878s
user    0m3.472s
sys     0m0.096s

time awk 'BEGIN{ for(i=1;i<1000000;i++) print i**2}' > /dev/null

real    0m4.008s
user    0m3.496s
sys     0m0.084s

time awk 'BEGIN{ for(i=1;i<1000000;i++) print i**2}' > /dev/null

real    0m4.008s
user    0m3.496s
sys     0m0.084s


Perl is a bit quicker.

> time perl -e 'use bignum; for (1..1000000) { print $_*$_; }' > /dev/null

real    0m2.801s
user    0m2.564s
sys     0m0.060s


---

### Post by bruce89 on 2009-01-02
Guess what?
```

#include <stdio.h>

int
main (void)
{
	int i;

	for (i = 1; (i * i) <= 10000; i++)
	{
		printf ("%d\n", (i * i));
	}
}

bruce@Scooby-Dum:~/Desktop$ time ./moo > /dev/null

real	0m0.003s
user	0m0.000s
sys	0m0.000s

```

Not the most exciting thing in the world, but it's the best I can (be bothered) to do.

---

### Post by Cracauer on 2009-01-02
```

time sbcl --noinform --no-userinit --eval '(progn
(declaim (optimize (speed 3) (safety 0) (debug 0)))
(defun abuse (max)
  (declare (fixnum max))
  (loop for i fixnum from 0
        for prod fixnum = (expt i 2)
     when (>= prod max)
     return i
     do
       (print prod)))
(compile '"'"'abuse)
(abuse 10000)
(sb-ext::quit))' > /dev/null


```

real    0m0.031s
user    0m0.008s
sys     0m0.023s

If we want to get rid of some startup overhead, let's use this:
```

[...]
(abuse 100000000000)                                                            

```

real    0m0.700s
user    0m0.614s
sys     0m0.076s

This is dominated by the printer, and memory breathing in the printer in particular.

---

### Post by Delever on 2009-01-02
I usually find that CPU is too good at caching operations to make serious comparisons at this level...

---

### Post by ghostdog74 on 2009-01-02
> **bruce89 said:**
> Guess what?
```

#include <stdio.h>

int
main (void)
{
	int i;

	for (i = 1; (i * i) <= 10000; i++)
	{
		printf ("%d\n", (i * i));
	}
}

bruce@Scooby-Dum:~/Desktop$ time ./moo > /dev/null

real	0m0.003s
user	0m0.000s
sys	0m0.000s

```

Not the most exciting thing in the world, but it's the best I can (be bothered) to do.

IMO, C will definitely have a speed advantage mostly because of the fact that the loop construct is compiled. (Btw, its 1000000 and not 10000)

---

### Post by bruce89 on 2009-01-02
> **ghostdog74 said:**
> IMO, C will definitely have a speed advantage mostly because of the fact that the loop construct is compiled. (Btw, its 1000000 and not 10000)

> **CLomax said:**
> [...]**between 0 and 10000.**

If anyone's interested, here's the correspoding assembly:

```

	.file	"moo.c"
	.section	.rodata
.LC0:
	.string	"%d\n"
	.text
.globl main
	.type	main, @function
main:
	leal	4(%esp), %ecx
	andl	$-16, %esp
	pushl	-4(%ecx)
	pushl	%ebp
	movl	%esp, %ebp
	pushl	%ecx
	subl	$36, %esp
	movl	$1, -8(%ebp)
	jmp	.L2
.L3:
	movl	-8(%ebp), %eax
	imull	-8(%ebp), %eax
	movl	%eax, 4(%esp)
	movl	$.LC0, (%esp)
	call	printf
	addl	$1, -8(%ebp)
.L2:
	movl	-8(%ebp), %eax
	imull	-8(%ebp), %eax
	cmpl	$10000, %eax
	jle	.L3
	addl	$36, %esp
	popl	%ecx
	popl	%ebp
	leal	-4(%ecx), %esp
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu 4.3.2-1ubuntu11) 4.3.2"
	.section	.note.GNU-stack,"",@progbits

```

---

### Post by ghostdog74 on 2009-01-02
> **.Maleficus. said:**
> The setup:

x = 1
while x**2 < 1000000:
    print x**2
    x += 1

please check whether you have the correct output. They are not the same.
```

# more test.py
x = 1
while x**2 < 10:
    print x**2
    x += 1

# awk 'BEGIN{ for(i=1;i<10;i++) print i**2}'
1
4
9
16
25
36
49
64
81

# python test.py
1
4
9


```

---

### Post by ghostdog74 on 2009-01-02
> **eightmillion said:**
> Another python version:



I'm not getting much of a speed difference with awk:



Perl is a bit quicker.

```

# time python -c "print map(lambda n: n**2, xrange(1,1000000))" > /dev/null

real    0m8.460s
user    0m8.257s
sys     0m0.128s

# time python -c "print map(lambda n: n**2, xrange(1,1000000))" > /dev/null

real    0m10.151s
user    0m8.485s
sys     0m0.112s

 # time awk 'BEGIN{ for(i=1;i<1000000;i++) print i**2}' > /dev/null

real    0m4.283s
user    0m4.236s
sys     0m0.012s

# time awk 'BEGIN{ for(i=1;i<1000000;i++) print i**2}' > /dev/null

real    0m4.230s
user    0m4.200s
sys     0m0.024s


```

I think differences of interpreters/programs and hardware plays a part in discrepancies.

---

### Post by Cracauer on 2009-01-02
> **ghostdog74 said:**
> IMO, C will definitely have a speed advantage mostly because of the fact that the loop construct is compiled. (Btw, its 1000000 and not 10000)

No, the advantage is that printf is very quick and doesn't breathe.

---

### Post by Cracauer on 2009-01-02
> **bruce89 said:**
> If anyone's interested, here's the correspoding assembly:
[...]



Function is posted above:

```

:CL-USER Yes, Master? (disassemble 'abuse)
; disassembly for ABUSE
; 0343B643:       31DB             XOR EBX, EBX               ; no-arg-parsing entry point
;       45:       31C9             XOR ECX, ECX
;       47:       EB37             JMP L1
;       49:       90               NOP
;       4A:       90               NOP
;       4B:       90               NOP
;       4C:       90               NOP
;       4D:       90               NOP
;       4E:       90               NOP
;       4F:       90               NOP
;       50: L0:   48895DE0         MOV [RBP-32], RBX
;       54:       488BD1           MOV RDX, RCX
;       57:       488BF4           MOV RSI, RSP
;       5A:       4883EC18         SUB RSP, 24
;       5E:       488B058BFFFFFF   MOV RAX, [RIP-117]         ; #<FDEFINITION object for PRINT>
;       65:       B908000000       MOV ECX, 8
;       6A:       48896EF8         MOV [RSI-8], RBP
;       6E:       488BEE           MOV RBP, RSI
;       71:       FF5009           CALL QWORD PTR [RAX+9]
;       74:       480F42E3         CMOVB RSP, RBX
;       78:       488B5DE0         MOV RBX, [RBP-32]
;       7C:       4883C308         ADD RBX, 8
;       80: L1:   488BCB           MOV RCX, RBX
;       83:       48C1F903         SAR RCX, 3
;       87:       480FAFCB         IMUL RCX, RBX
;       8B:       483B4DE8         CMP RCX, [RBP-24]
;       8F:       7CBF             JL L0
;       91:       488BD3           MOV RDX, RBX
;       94:       488D65F0         LEA RSP, [RBP-16]
;       98:       F8               CLC
;       99:       488B6DF8         MOV RBP, [RBP-8]
;       9D:       C20800           RET 8
NIL
:CL-USER Yes, Master?

```

---

### Post by ghostdog74 on 2009-01-02
> **Cracauer said:**
> No, the advantage is that printf is very quick and doesn't breathe.

Look at it this way
```

int
main (void)
{
	int i;

	for (i = 1; (i * i) <= 10000; i++)
	{
		printf ("%d\n", (i * i));
	}
}

```

and then i compile it and name it awk.

the corresponding differences will be
```

# ./awk

```

versus

```

# awk 'BEGIN{ for(i=1;i<1000000;i++) print i**2}' > /dev/null

```

In the latter, you have to specifically create a loop and pass it as parameter to the program. The former is already compiled. That's where the difference lie.

---

### Post by Cracauer on 2009-01-02
In the C example the runtime for the compiler should be included to make it more comparable. This whole "test" is more a comparison of how practical languages are, not raw speed.

It's not too unfair, C still gets a kick out of the faster print/stream subsystem.

In my Lisp example I included it, the compiler is called within the timed commandline.

---

### Post by bruce89 on 2009-01-02
Thought I'd do a threaded one (using GThread)

```

#include <stdio.h>

#include <glib.h>

static void
thread_func (gint *thread_no)
{
	gint i;
	gdouble time;
	GTimer *timer;

	timer = g_timer_new ();

	for (i = 1; (i * i) <= 10000; i++)
	{
		printf ("%d\n", (i * i));
	}

	time = g_timer_elapsed (timer, NULL);
	fprintf (stderr, "Thread #%d took %lf seconds\n", GPOINTER_TO_INT (thread_no), time);

	return;
}

int
main (void)
{
	gint i;
	GThread *thread;

	g_thread_init (NULL);

	for (i = 0; i < 10; i++)
	{
		thread = g_thread_create ((GThreadFunc) thread_func, GINT_TO_POINTER (i), TRUE, NULL);
		g_thread_join (thread);
	}

	return 0;
}

bruce@Scooby-Dum:~/Desktop$ ./moo > /dev/null
Thread #0 took 0.000141 seconds
Thread #1 took 0.000069 seconds
Thread #2 took 0.000070 seconds
Thread #3 took 0.000070 seconds
Thread #4 took 0.000067 seconds
Thread #5 took 0.000067 seconds
Thread #6 took 0.000070 seconds
Thread #7 took 0.000071 seconds
Thread #8 took 0.000078 seconds
Thread #9 took 0.000068 seconds

```

---

### Post by ghostdog74 on 2009-01-03
> **Cracauer said:**
> This whole "test" is more a comparison of how practical languages are, not raw speed.

Define practical and elaborate more on that area. I am curious

---

### Post by Cracauer on 2009-01-03
> **ghostdog74 said:**
> Define practical and elaborate more on that area. I am curious

Not a chance :)

But I still think compilation time should be included. Many of the scripting languages do a byte-compile when loading. SBCL by default doesn't have an interpreter and compiles stuff coming in with --eval. Languages that choose not to compile should have a chance to show it can pay off.

---

### Post by ghostdog74 on 2009-01-03
> **Cracauer said:**
> Not a chance :)
why not? if you don't, then there's no justification that what you said earlier
> 
This whole "test" is more a comparison of how practical languages are, not raw speed

is true, you know ? :)

---

### Post by eightmillion on 2009-01-03
> **ghostdog74 said:**
> why not? if you don't, then there's no justification that what you said earlier

is true, you know ? :)

I really don't see the point of including compile time. Presumably a program is something that you compile once and run many times. Even if you included compile time, I suspect that the compiled languages would still win out for many of the examples in this thread.

Anyway, here's something that's kind of cool. It's one line of python that I just wrote that calculates the factorials of the numbers 1 through 1000.

```
python -c "print map(lambda f: [0,1][f<=1] or reduce(lambda x,y:x*y,xrange(1,f+1)),xrange(1,1001))"
```

---

### Post by Reiger on 2009-01-03
Haskell:

List *comprehension* is terribly overcomplicated (for simply squaring the numbers 1 through 1000):
```

main = putStrLn $ show $ map (\x -> x*x) [1..1000]

```
EDIT: Naturally, in Haskell one can rewrite (\x -> x*x) as simply (^2).

For the other one (all factorials of the numbers 1 through 1000):
```

main = putStrLn $ show $ map (\x-> product [1..x]) [1..1000]

```

---

### Post by .Maleficus. on 2009-01-03
> **ghostdog74 said:**
> please check whether you have the correct output. They are not the same.
It's the correct output...  The last number printed for either one is 998001, which is 999 squared.

---

### Post by pp. on 2009-01-03
If you wanted to compare the run times of the different solutions, you ought to:

- reach a consensus on the number of results the program is to produce. OP said 'square numbers between 0 and 10,000', that's 0² up to 100², inclusive.

- eliminate obvious overhead such as raising x to the second power both in the termination test and the print statement of the same loop.

Otherwise, this thread is very entertaining. Keep it up, please.

---

### Post by ghostdog74 on 2009-01-03
> **.Maleficus. said:**
> It's the correct output...  The last number printed for either one is 998001, which is 999 squared.

in order to illustrate, i had already posted the differences in [post #24](http://ubuntuforums.org/showpost.php?p=6483687&postcount=24). If you haven't noticed yet, the while loop should be like this
```

x = 1
while x < 10:
    print x**2
    x += 1 

```

---

### Post by .Maleficus. on 2009-01-04
> **ghostdog74 said:**
> in order to illustrate, i had already posted the differences in [post #24](http://ubuntuforums.org/showpost.php?p=6483687&postcount=24). If you haven't noticed yet, the while loop should be like this
```

x = 1
while x < 10:
    print x**2
    x += 1 

```
Ah, I see what you mean.  Instead of the condition being x^2, you mean have it be x and then the square root of the larger number? (in this case it would be 1000).  I haven't tried it yet, but would that give me a speed increase, because it isn't squaring x twice per iteration?

---

### Post by Darwinfish on 2009-01-04
Revise this to just the sum of the first n squares so the maths people can have fun :)

---

### Post by Reiger on 2009-01-04
There's a well known formula for this and I would not be surprised if it's used to teach Mathematical Induction or Sigma manipulation with.

---

### Post by cellerit on 2009-01-04
haskell:
main = print [x*x | x <- [1..100] ]

time:
real	0m0.004s
user	0m0.004s
sys	0m0.000s

Fast and easy who wouldve guessed :)!

as for factorials:

main = print [foldl (*) 1 [1..x] | x <- [1..1000]]
(for each list of numbers from 1 to x for x going from 1 to 1000 multiply all the numbers together)

---

