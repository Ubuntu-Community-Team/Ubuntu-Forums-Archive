---
title: "Fun with Fortran: Functions"
date: 2008-04-05
forum: Programming Talk
---

### Post by Shining Arcanine on 2008-04-05
I am currently trying to learn Fortran 90. I borrowed a book called Fortran 90 for Engineers and Scientists from my university's library and I have been reading it intermittently over the past two weeks. I have also been figuring out what compilers are available to me on what computers and running Hello World programs to make sure that they are working properly.

Today, I tried writing my first real program in Fortran by porting a chinese remainder problem solver I wrote in C last semester to Fortran. Looking at code examples in the book and online, my port should have worked, but it did not. I spent a few hours debugging and I finally discovered the cause of the problem. Apparently, my functions are not returning their variables. I wrote a second program that is much less sophisticated than my first to verify that was the case and it apparently is.

```
PROGRAM Factorial

	INTEGER :: n

	PRINT *, "Enter n to compute n!"
	READ *, n

	PRINT *, "The factorial is ", FACT(n)

END PROGRAM



FUNCTION FACT (n)

	INTEGER :: FACT, n

	FACT = 1;

	DO

		IF (n <= 0) EXIT

		FACT = FACT * n

		n = n - 1

	END DO

	PRINT *, "The factorial is ", FACT

END FUNCTION FACT
```

My next move would be to type up and compile some of the code examples in the book to see if they actually work, but I will have to go somewhere soon, so I am wondering if anyone here knows what the problem is. I have tried several variations of this, but none of them have worked.

Also, if anyone is familiar with IMPLICIT NONE, would you please tell me how to avoid a compiler error when I place that in the main program? I assume that it is caused by the lack of a function prototype, but so far, I am not sure how to do that in Fortran.

If it helps, I am using the GNU Fortran compiler (gfortran).

---

### Post by squaregoldfish on 2008-04-05
I'm learning FORTRAN too.

I think the problem with the function not returning is that you've declared FACT as a variable inside the FACT function. I suspect that all you'll do from that point is set the variable, and not the return value.

What compiler error are you getting for the IMPLICIT NONE?

---

### Post by smartbei on 2008-04-05
Ok, had a bit of fun with this myself - there are several problems:
[LIST=1]
[*]FACT is declared inside the FACT function.
[*]The FACT function is not declared INTEGER.
[*]The FACT function is not declared in the main program.
[*]At the end of the FACT function the RETURN statement was missing.
[/LIST]

Here is code that works:
```

PROGRAM Factorial

	INTEGER :: n
	INTEGER FACT
	PRINT *, "Enter n to compute n!"
	READ *, n
	PRINT *, "The factorial is ", FACT(n)

END PROGRAM


INTEGER FUNCTION FACT(n)

	INTEGER :: n

	FACT = 1

	DO

		IF (n <= 0) EXIT

		FACT = FACT * n

		n = n - 1

	END DO

	RETURN
END FUNCTION FACT

```

---

### Post by Shining Arcanine on 2008-04-05
Thank you so much. The list of corrections you made not only makes the factorial program work, but it makes my chinese remainder problem solver made it work as well. :)

---

### Post by GeoffreyBernardo on 2008-09-28
How do you run the files created by gfortran in the terminal.

I can compile, but when I try to run the *.o file, it says "command not found".

---

### Post by LaRoza on 2008-09-28
> **GeoffreyBernardo said:**
> How do you run the files created by gfortran in the terminal.

I can compile, but when I try to run the *.o file, it says "command not found".

```

gfortran program.f
./a.out

```

(You have to specify the path, ./ means "this directory")

---

