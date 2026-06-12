---
title: "The Size of Executables Compiled with Free Pascal"
date: 2006-10-29
forum: Programming Talk
---

### Post by Fingolfin on 2006-10-29
When compiled with Free Pascal 2.0x on Linux, the "Hello world!" program consisting of 4-5 lines of Pascal code is about 150 kbytes in size.

The same code compiled with Free Pascal on MS Windows is only 5-6 kbytes in size as is the equivalent executable produced by GCC for example.

Why does FPC produce enormously big executables in Linux and is Gnu Pascal compiler perhaps better in terms of making more compact exacutable files?

---

### Post by angustia on 2006-10-30
did you use -XX (smart linking)?

fpc uses attaches a big part of code to the executables (RTL), but with smart linking you can attach only really used functions.

---

### Post by Fingolfin on 2006-10-30
> **angustia said:**
> did you use -XX (smart linking)? 

Yes, you are right. With -XX, the compiled "Hello world!" is down to 21 kbytes which is still considerably more than 6 kbytes from GCC but I guess that's the best one can have with FPC.
I haven't used  -XX  option before and was unsuccessfully trying to make executable smaller with -0g.
Thanks for pointing this out to me.

(p.s. have just installed and tried GNU Pascal Compiler, it compiled "Hello world!" to 210 kbytes in size without any optimizing switches.)

---

### Post by toojays on 2006-10-31
Have you stripped your executable as well?

---

### Post by Fingolfin on 2006-10-31
> **toojays said:**
> Have you stripped your executable as well?
Stripped with  -Xs.  It gives the executable of the same size as the  -XX switch does (which is good enough).

---

### Post by angustia on 2006-10-31
well, i supose that it's that way because fpc is designed to make stand-alone executables, and because it doesn't make use of the libc functions in its native form (you use writeln, not printf, so the writeln function has to convert the received string into a C string and then call write()); so this is the extra code that has to be included in the binary.

---

### Post by Fingolfin on 2006-11-03
> **angustia said:**
> well, i supose that it's that way because fpc is designed to make stand-alone executables, and because it doesn't make use of the libc functions in its native form (you use writeln, not printf, so the writeln function has to convert the received string into a C string and then call write()); so this is the extra code that has to be included in the binary.

Apart from the size of executables, does this extra conversion step mean that any FPC'compiled program will always be slower than the exact equivalent compiled with GCC?

---

### Post by Ragazzo on 2006-11-03
> **angustia said:**
> well, i supose that it's that way because fpc is designed to make stand-alone executables, and because it doesn't make use of the libc functions in its native form (you use writeln, not printf, so the writeln function has to convert the received string into a C string and then call write()); so this is the extra code that has to be included in the binary.

write-system call doesn't use C strings (null-terminated character arrays) as you can see in "man 2 write" (if you have installed manpages-dev):

ssize_t write(int fd, const void *buf, size_t count);

---

### Post by emarti on 2006-11-05
thnks

---

### Post by angustia on 2006-11-06
> **Fingolfin said:**
> Apart from the size of executables, does this extra conversion step mean that any FPC'compiled program will always be slower than the exact equivalent compiled with GCC?

it depends...

when you put something like writeln('a string ', aIntegerVar, aRealVar); the compiler transforms this in 4 calls (at compile time):

write_str('a string ');
write_integer(aIntegerVar);
write_real(aRealVar);
writeln;

and every functions has to do only its specific function.

in C, you may use something like this:

printf("a string %d%f\n", aIntVar, aFloatVar);

and the function has to start scanning the format string (at runtime) while writting on the screen, even if there are no variables to write. So fpc in this case can be faster.

As Ragazzo said, write() system call spects a pointer to a stream of bytes and the numbers of bytes to write, and with C strings, the number of characters has to be recalculated scanning the whole string, while with pascal strings, this numbers is at the beginning of the data (four bytes before the characters i think).

but this is only one case, there can be another ones where fpc had to C-ify its data structures before pass them to C functions, and that can cost extra processing or memory (just think about wrapping C++ objects in FPC objects...).

---

### Post by Fingolfin on 2006-11-10
> **angustia said:**
> it depends...

when you put something like writeln('a string ', aIntegerVar, aRealVar); the compiler transforms this in 4 calls (at compile time):

write_str('a string ');
write_integer(aIntegerVar);
write_real(aRealVar);
writeln;

and every functions has to do only its specific function.



Well, thank you for such thorough explanation.
To move away from strings, is it then correct to assume that any mathematical subroutine performing basic operations addition/divisions etc (on floats and integers alike) should execute with about the same speed regardless of the compiler (fpc or gcc)? (meaning that both compilers would transform the routine into identical sequence of calls?)

---

### Post by angustia on 2006-11-11
write a c and a pascal version of a program, compile them to asm source, and see the result by yourself.

---

### Post by Fingolfin on 2006-11-12
I came up with something like this, obviously the contents of the for loop can be changed into anything that needs performance assessing.
However, I do not know why at the end of the program both timestring variables are displaying exactly the same time (regardless of the number of iterations). 

[FONT="Lucida Console"]#include <stdio.h>
#include <sys/types.h>
#include <time.h>

main ()
{	long      N, i,  j;
	long        i2, i3;
	double          r;

        time_t      time1, time2;

        struct 	    tm * timeinfo1, * timeinfo2;
	char     * timestring1, * timestring2;

	time ( &time1 );
	timeinfo = localtime ( &time1 );
	timestring1 = asctime (timeinfo);

	N = 300000;             /* Number of repetitions */
	for (i = 1; i <= N; i++) { 
	/* arbitrary math and printf-writeln operations */
		i2 = i * i;
		i3 = i2 * i;
		printf ("  i  = %d \n  i2 = %d \n  i3 = %d\n",i, i2, i3);
                j = 2 * i;
		r = j / 2.21748236446792;
		printf (" r[%6d] = %e \n",r);
	}

	time ( &time2 );
	timeinfo2 = localtime ( &time2 );
	timestring2 = asctime (timeinfo2);
	
	printf ("Date and time before the for-loop:    %s.\n", timestring1 );
	printf ("Date and time after the for-loop:     %s.\n", timestring2 );
}[/FONT]

---

### Post by Fingolfin on 2006-11-12
This C program with N = 300000 takes, when compiled with GCC on average 1 min: 28 sec to execute on 2GHz Athlon64.
The equivalent Pascal code compiled with FPC takes about 1 min : 23 sec on the same machine.

Once the printf and writeln functions are removed, and when the inner for loop is repeated with additional outer for-loop (k = 1 to 1000), the advantage clearly goes to GCC as it executes in 42 seconds versus 51 sec for FPC code.

---

