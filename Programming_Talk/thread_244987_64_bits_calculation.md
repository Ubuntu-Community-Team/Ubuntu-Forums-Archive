---
title: "64 bits calculation"
date: 2006-08-27
forum: Programming Talk
---

### Post by Thiago Tomei on 2006-08-27
Hi, I'm an amateur programmer, and I'm trying to perform 64 bits calculation in my Ubuntu Box. I think I have the necessary stuff (64 bits processor and 64 bis Dapper). So how do I make something like

```

int a;
a = 100000000*100000000;

```

work? BTW, I'm using old plain C. So the whole program would be something like:

```

include <stdio.h>

int main(void)
{
   int a;
   a = 100000000*100000000;
   printf("%d\n");
   return 0;
}

```

When I compile and run:
$ gcc 64bits.c -o 64bits.out
64bits.c: In function ‘main’:
64bits.c:6: warning: integer overflow in expression
$ ./64bits.out
-2732584

So, what exactly must I do?

Thanks in advance

---

### Post by tkjacobsen on 2006-08-27
Try to make a floating point calculation instead of an integer one:
100000000.*100000000.

Else you could try fortran... It's good for calculation

---

### Post by tkjacobsen on 2006-08-27
it should look like this:

```

PROGRAM calc
IMPLICIT NONE
INTEGER, PARAMETER :: kind = SELECTED_INT_KIND(15)
INTEGER (kind) :: a,b,c
  a = 100000000
  b = 100000000
  c = a * b
  print *,c
END PROGRAM calc

```

you need the gfortran compiler, then just:
gfortran filename.f95 -o filename.out

---

### Post by toojays on 2006-08-27
IIRC, amd64 C ABI uses 32-bit ints. If you want 64-bit ints, try to #include <stdint.h> and declare "a" with type int64_t. You will no doubt also need to use a different format string with printf; I've seen "%lld" mentioned somewhere.

I don't have a 64-bit CPU so this is all untested advice, but hopefully it puts you in the right direction.

Edit: I think the Scheme version looks nicer than the fortran version, but in this case we don't know whether or not the CPU is actually doing a single 64-bit multiplication.```

#!/usr/bin/guile -s
# -*-Scheme-*-
!#

(use-modules (ice-9 format))

(let ((a 100000000))
  (format #t "~a\n" (* a a)))

```

---

### Post by JonahRowley on 2006-08-27
If you need large, accurate calculations, perhaps a bignum library is what you're looking for.  It's slower, but there is no limit to the numbers it can handle (within reason).  Also, if speed is not a large issue, check out Ruby.  It's a lot easier to work with than C and has bignum support built in and transparent (variables switch from native to bignum automatically).

---

### Post by Thiago Tomei on 2006-08-27
Ok, thanks for all the answers.

First point: as I said, this isn't a real project at all. I'm just playing with my box, trying to see what I can do with it. I know I could use floating number, a bignum library, or the like. It's just a matter of curiosity to see what difference those 64 bits do in the end.

I tried the type int64_t approach to no avail. Next, I'll try doing it in Fortran. I'll update the thread with my results. ^^

---

### Post by rplantz on 2006-08-27
1. Regardless of how you end up implementing this, test your program very thoroughly.

2. Be very careful when using floats. In C/C++, they are 32-bit variables, and the significand has only 24 bits of significance. Furthermore, if you have any fractional values, even in intermediate computations, be aware that only powers of 1/2 can be stored exactly. Round off errors can produce incorrect answers. For example,
```

#include <stdio.h>

int main(void) {
   int anInt = 19088743;
   float aFloat = 19088.743;
   
   printf("The integer is %d and the float is %f\n", anInt, aFloat);
   
   return 0;
}

```
produces
```

The integer is 19088743 and the float is 19088.742188

```
You should at least use doubles, which are 64-bit variables with 53 bits for the significand.

3. Try using long ints. To see how many bytes are allocated for your variables use the sizeof operator. For example,
```

#include <stdio.h>
int main() {
   long int x, y, z;
   
   printf("An int has %i bytes.\n", sizeof(x));
   x = 100000000;
   y = 100000000;
   z = x * y;
   printf("%li * %li = %li\n", x, y, z);
   
   return 0;
}

```

Notice the use of "l" (ell, not one) in the printf type specifications -- "%li". If you use long ints and leave out the l and test with small numbers, everything will look okay because the x86 architecture uses little endian storage.

Also note that long ints are 32-bit values if compiled in a 32-bit environment. To see this, use
```

gcc -m32 filename.c

```
in your 64-bit Ubuntu installation.

I assume that
```

gcc -m64 filename.c

```
in a 32-bit Ubuntu installation will produce 8-byte long ints, but I'm not sure.

---

### Post by rplantz on 2006-08-27
> **Thiago Tomei said:**
> Ok, thanks for all the answers.

First point: as I said, this isn't a real project at all. I'm just playing with my box, trying to see what I can do with it. I know I could use floating number, a bignum library, or the like. It's just a matter of curiosity to see what difference those 64 bits do in the end.

I tried the type int64_t approach to no avail. Next, I'll try doing it in Fortran. I'll update the thread with my results. ^^

If you're really curious about the box, I don't think that FORTRAN will answer your curiosity. I haven't used FORTRAN in a long time, but ultimately all languages get reduced to the instruction set architecture. One of the main reasons that so many number crunching programs use FORTRAN is that it is an old language that has been used for this purpose for a long time. Thus, there are lots of excellent FORTRAN number crunching libraries out there.

Anyway, have fun playing with your box. I'm retired, and that's the main reason I installed the 64-bit Ubuntu. I wanted to play with 64-bit things. Great fun! :)

---

### Post by Thiago Tomei on 2006-08-28
Ok, people. Declaring it as long int and using %li in the printf did the trick. ^^ Thank you all!

---

### Post by LordHunter317 on 2006-08-28
FWIW, you don't need a 64-bit processor to do 64-bit integer or FP math.  

You can do it in C on just about any 32-bit platform.  The compiler emits code to do the math in two parts.

---

### Post by rplantz on 2006-08-28
I've played with this and have learned some things.

If you read the info manual for gcc, under "C Extensions" you will find "Long long." From my playing around and what I recall from the C standards, I believe the following is how it works:

1. An int is 32 bits in both 32-bit and 64-bit systems.

2. A long long int is 64 bits in both 32-bit and 64-bit systems.

3. A long int is 32 bits in a 32-bit system and 64 bits in a 64-bit system.


printf does roughly the same thing. That is

1. "%i" (or "%d") prints a 32-bit decimal.

2. "%lli" prints a 64-bit decimal.

3. "%li" prints a 32-bit decimal in a 32-bit system and a 64-bit decimal in a 64-bit system.

Bottom line:

1. If you want 32-bit ints, use int variable types and "%i" for printf.

2. If you want 64-bit ints, use long long int variable types and "%lli" for printf.

3. Avoid using long int variable types and "%li" for printf.

---

### Post by LordHunter317 on 2006-08-29
> **rplantz said:**
> II believe the following is how it works:

1. An int is 32 bits in both 32-bit and 64-bit systems.

2. A long long int is 64 bits in both 32-bit and 64-bit systems.

3. A long int is 32 bits in a 32-bit system and 64 bits in a 64-bit system.Nope, wrong.  This is tough to understand however, because the rules are intentionally vague.

Here's what the standard promises you[1]:[list=1][*]char can hold integer values up to 127.[*]sizeof(char) == 1, so char is always one byte[2][*]short can hold values of at least 2^15-1[*]long can hold values of at least 2^31-1[*]In C99, long long can hold at least 2^63-1[*]Signed and unsigned versions of a type have the same width (i.e., sizeof(unsigned T) == (signed T) for all T).[*]sizeof(char) <= sizeof(short) <= sizeof(int) <= sizeof(long) <= sizeof(long long)[/list]

The only type who doesn't have a minimum or maximum defined as an absolute is int.  It can be as small as a short or as big as a long.  It's also not correct to assume that sizeof(int) == sizeof(void *) or even sizeof(T*) for all T.  

Normally, we talk about 3 64-bit programming data models[3]:[list][*]LP64: int is 32-bits.  long and pointers are 64-bits.  This is used on 64-bit Linux and most UNIX.[*]ILP64: int, long, and pointers are 64-bits.[*]LLP64: int and long are 32-bits.  Pointers are 64-bits.  This is used on Windows NT.[/list]

The short story is if you want an assured minimum 64-bit type, use 'long long'.

[1]See [http://c-faq.com/decl/inttypes.html](http://c-faq.com/decl/inttypes.html) and [http://c-faq.com/decl/octabyte.html](http://c-faq.com/decl/octabyte.html)

[2]The assumption a byte == 8 bits is incorrect, however.  

[3] Assuming you're programming a 64-bit machine, of course.

---

### Post by rplantz on 2006-08-29
Thanks for correcting my misconceptions and the links. My remarks were based on looking at the assembly language and some brief experiments.

> **LordHunter317 said:**
> Nope, wrong.  This is tough to understand however, because the rules are intentionally vague.


Probably "...intentionally flexible" is a little more tactful. :)

> 
[2]The assumption a byte == 8 bits is incorrect, however.  

I knew this. I used to work on a CYBER. It used a 60-bit word and 6-bit byte. So you could store 10 chars in a word. A little thought will show that the character set was all upper case. It was intended for scientific computing, but my university used it for administrative chores. As of a couple of years ago (when I retired) some documents on campus were still kept in all upper case.

Actually, one could use the CYBER in ASCII mode, but then it used an entire 60-bit word for each character. And memory cost a LOT more in those days.

---

### Post by LordHunter317 on 2006-08-29
Looking at the assembly language doesn't tell you the full details in this case.  

In the most practical terms, the 3 models I noted are what people need be aware of.  Variation from them is AFAIK, non-existent on non-estoeric hardware.

---

### Post by rplantz on 2006-08-29
> **LordHunter317 said:**
> Looking at the assembly language doesn't tell you the full details in this case.

I looked at the assembly language because compiling with the -m32 option on my 64-bit system gave different results. In my example above I changed the variables to long long ints, but (due to my ignorance) used "%li" for printf. y printed as 0 and z printed as 100000000. I suspected that things were off by 4 bytes. From the assembly language I could tell that the program was doing 64-bit arithmetic. So this caused me to look at printf, which caused me to learn more. In particular, "%lli".

Your "short story ... use 'long long'" is the important message here.

I would reiterate my point above that testing is very important. From 20+ years of teaching programming, I know that new programmers do not know how to test and how important it is. Especially when using large numbers.

Another thing I learned very early in my teaching career is that I don't know everything. It was often the more naive questions that caused me to do some investigation and learn more. Naive students tend to ask questions that I never thought about.

Even though I'm now retired, I still enjoy learning things. Thank you to all who have contributed to this thread and helped me learn more.

---

