---
title: "noob C question"
date: 2009-04-25
forum: Programming Talk
---

### Post by badperson on 2009-04-25
Okay, dabbling a little in C for the first time, thought I'd use it to help get my math chops going, maybe do some of those EulerProject problems, and get some experience with pointers and recursion(although, you'll soon see, that last bit is a ways off...)

```
#include <stdio.h>
#include <math.h>

/* function practice 

to compile: gcc function.c -o funcTest
to run: ./funcTest
*/

int main(){
	printf("beginning program... \n");

	int num;
	printf("try some standard math functions \nPlease enter a number: ");
	scanf("%d", &num);

	printf("square root: %.2f\n", sqrt(num));


	

return(0);
}
```

that gives me this:

```
$ gcc function.c -o funcTest
/tmp/ccce5fpn.o: In function `main':
function.c:(.text+0x5e): undefined reference to `sqrt'
collect2: ld returned 1 exit status

```

but if I just put a plain number, 
```
	printf("square root: %.2f\n", sqrt(9));
```
then it runs fine. 

I've tried casting, but for some reason, it doesn't like a variable being called instead of an actual number. 
thanks, 
bp

---

### Post by Namtabmai on 2009-04-25
I believe that sqrt expects the number to be a float or a double, what did you try casting it to?

---

### Post by badperson on 2009-04-25
I'm thinking I don't have someting installed properly...I tried copying an example out of a book verbatim, and I"m still having the same problem. Here's the updated code...

```
#include <stdio.h>
#include <math.h>

/* function practice 

to compile: gcc function.c -o funcTest
to run: ./funcTest
*/

int main(){
	printf("beginning program... \n");

	int num;
	printf("try some standard math functions \nPlease enter a number: ");
	scanf("%d", &num);

	double c1=13.0;
	double d=3.0;
	double f=4.0;

	printf("%.2f", sqrt( c1 + d * f) );



	

return(0);
}

```
prints out:

> $ gcc function.c -o funcTest
/tmp/cckunYXC.o: In function `main':
function.c:(.text+0x94): undefined reference to `sqrt'
collect2: ld returned 1 exit status
jason@jason-desktop:/media/files/code/CFiles/intro$ 


---

### Post by Namtabmai on 2009-04-25
Ah you need to link the the maths library using gcc.

```

gcc function.c -o funcTest -lm

```

---

### Post by sujoy on 2009-04-25
```
to compile: gcc function.c -o funcTest
```

change that to

```
gcc function.c -o funcTest -lm
```

that lm switch is needed to actually link with the math library

---

### Post by Bölvaður on 2009-04-25
> **Namtabmai said:**
> I believe that sqrt expects the number to be a float or a double, what did you try casting it to?

so that means change

int num;
into
float num = 2;

and comment out scanf

or just have it

float num;
scanf("%e",&num);

unless if Im looking at it with the "glasses of confusion"

---

### Post by sujoy on 2009-04-25
and the int to float conversion will be automatic, being a conversion to high precision it wont cause data loss. the problem here is precisely the "-lm" switch

---

### Post by badperson on 2009-04-25
> **Namtabmai said:**
> Ah you need to link the the maths library using gcc.

```

gcc function.c -o funcTest -lm

```

this did the trick, thanks. Do you need to do this for every library you use? 
bp

---

### Post by _Purple_ on 2009-04-25
To compile:
```
 gcc -Wall function.c -lm -o funcTest


```

You can find details about linking here:
[http://www.network-theory.co.uk/docs/gccintro/gccintro_17.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_17.html)



Edit: the solution is already posted :)

---

### Post by Arndt on 2009-04-25
> **badperson said:**
> this did the trick, thanks. Do you need to do this for every library you use? 
bp

The 'm' in -lm stands for 'math'. What libraries need to be linked explicitly depends on the function, and the man page for them usually say so. So, when linking gives you a "undefined reference to sqrt", you do the command "man sqrt", and it says (among other things) "Link with -lm".

If that was your question; I'm not sure. Ask again if something is unclear.

---

### Post by mali2297 on 2009-04-26
> **badperson said:**
> this did the trick, thanks. Do you need to do this for every library you use? 
bp

Most libraries, but not every. For example, you don't have to link to stdio.

---

### Post by monkeyking on 2009-04-26
I think there are 2 ways of doing this.

either include it like #include <cmath>
or link manually at compile time with -lm.


I normally opts for the first way.

---

### Post by Namtabmai on 2009-04-26
> **monkeyking said:**
> I think there are 2 ways of doing this.

either include it like #include <cmath>
or link manually at compile time with -lm.


I normally opts for the first way.

cmath would be the C++ version.

---

