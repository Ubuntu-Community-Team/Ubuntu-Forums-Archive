---
title: "Composite numbers in C"
date: 2007-11-13
forum: Programming Talk
---

### Post by Ferrari69 on 2007-11-13
Hello,

I'm trying to solve out a problem in C. The problem is to implement a program that take a positive ODD number and prints out the first serie, near to the initial odd, of composite number.

eg: First 1 consecutive composites from 4 to 4.
First 3 consecutive composites from 8 to 10.
First 5 consecutive composites from 24 to 28.
First 7 consecutive composites from 90 to 96.
First .. consecutive composites from .. to ...
..............................................
First 45 consecutive composites from 81464 to 81508.
...............................................

Notice that I have to define the N at the beginning of the program, and depending on N, any positive odd and integer number equilevant to K, and the K must be less or equal to N, it must be print out the first near serie of composite numbers.

Any help would be appriciated.

Thanks

---

### Post by LaRoza on 2007-11-13
This is the first of your posts, and you are asking a question that sounds like an acedemic assignment. We do not do homework for others, which is what it sounds like to me.

---

### Post by Ferrari69 on 2007-11-14
yes its an acedemic assignment but i didnt expect someone to make for me the program i want, i just put the whole program to let u know what its all about. besides how am i going to learn if i find the program ready for me. Anyways, 

i tried something but im confused

```
/* File: exe1.c */
#include <stdio.h> 	/* Header file for standard I/O library */
#include <math.h>	/* Header file for math library */
#define N 101


main()
{ int k,i,root,;
		for ( k=3 ; k<=N ; i++ ) do { 
			root=sqrt(k) }; if (k = k / root) && (k != INTEGER?NOT SURE);  
                        then (k=0); else (k=k+i++); 
```

the idea is that a number to be composite,the program must check only until the number of the root. 

eg:

to check the number 4
i have to calculate sqrt(4), which is 2.. then do these steps:
4 : 1 = 1 (until here its a prime numb)
4 : 2 = 2 (so its a composite numb)

but the program is more complicated as it wants to calculate some series of numbers.

---

### Post by smartbei on 2007-11-14
Ok, I am having trouble making sense of your code. Are you new to c/c++? That will definitely not compile. Just for reference, here is that same code formatted normally and changed so it will compile, except of course the NOT SURE part. That said, I am not really sure what this snippet is supposed to accomplish.

```

/* File: exe1.c */
#include <stdio.h> 	/* Header file for standard I/O library */
#include <math.h>	/* Header file for math library */
#define N 101

int main(void)
{
	int k, i, root;
	for ( k=3; k<=N; i++ )
	{
		root=sqrt(k);
		if (k = k / root) && (k != INTEGER?NOT SURE);
		{
			k=0;
		}else
		{
			k=k+i++;
		}
	}
	return 0;
}

```
You may want to look at various algorithms (the simplest ones will do - even those are easily quick enough up to a million or 10 million) for finding prime numbers. Once you find those, it shouldn't be difficult to find composite numbers.

---

### Post by Rumo on 2007-11-15
Yeah, you're code really doesn't make sense. But here are some things you probably got wrong:
```

if (k = k / root)

```
you probably meant (k == k/root) - but this doesn't make much sense either as this will only be true for k == 1 (which will never happen in your code).
```

(k != INTEGER?NOT SURE);

```
You want to check if k is an integer? k is an integer by definition ( int k - remember). If you want to check if k is dividable by root you can do this with modulo:
```

if (k%root == 0) {
...
}

```

```

k=k+i++;

```
Although this is correct C-code I'm not sure if you know what you're doing here.

---

### Post by Ferrari69 on 2007-11-20
hello and sorry for my delay response. with some advise of a friend i have managed to make this code which checks if the number is composite

```
for (num=3 ; num<=N ; num=num+2)
{
        if flag==0
         {
                if (num%2=0 && num!=2)
                        flag==1
                else (num%3=0 && num!=3)
                        flag==1
         }
         else flag==1
         { for (k=5 ; k<=sqrt(num) ; k=k+6)
                { if (num%k=0)
                        flag==1
                 else (num%(k+2)
                        flag==1
                }
         }

}

```

wat do u think?

---

### Post by smartbei on 2007-11-20
Have you tested it? That code won't compile. And it has tons of logic errors:
[list]
[*]flag==1 does not set flag to anything - just compares flag to 1.
[*]The whole if/else checking the flag is useless - the flag is undefined for a certain number at the beginning of the loop. 
[*]There are more...
[/list]

There are also simpler ways to accomplish what you are trying to di with the inner loop (+6 ???).

I don't mean to sound harsh, but take a piece of paper, think through what you are trying to do, and write it in code as simply as possible, without any optimizations. Only when it works should you go back and add optimizations such as checking if the number is even, etc.

Good Luck!

---

### Post by jfinkels on 2007-11-20
You need an introduction to C. Start with this [http://aelinik.free.fr/c/](http://aelinik.free.fr/c/)

If you want a language that's easier to understand, try Python.

---

### Post by Ferrari69 on 2007-11-20
thx both of u..i'll see wat im going to do..

---

### Post by Ferrari69 on 2007-11-21
hello, im trying to declare **c** as **double** and in the program i want to do this:
```
if ((c<b) && ((c%2==0) || (c%2==1)))
```

but i get the error

```
invalid operands to binary % 
```

what can i do?

---

### Post by jfinkels on 2007-11-21
> **Ferrari69 said:**
> hello, im trying to declare **c** as **double** and in the program i want to do this:
```
if ((c<b) && ((c%2==0) || (c%2==1)))
```

but i get the error

```
invalid operands to binary % 
```

what can i do?

The mod operator (%) is probably an operator on integers only (because   it wouldn't make sense to use this operator on a double, for example). You need to either declare 'c' as an integer like this:```
int c;
``` or cast it as an integer in the 'if' statement:```
if ((c < b) && (( (int) c % 2 == 0) || ( (int) c % 2 == 1)))
```

It makes more sense to declare 'c' the first way for this program, because a composite number must be an integer.

---

### Post by Ferrari69 on 2007-11-21
thx a lot **jfinkels**, it was very useful, but im not sure if **c** will still have its decimal points.

---

### Post by jfinkels on 2007-11-21
> **Ferrari69 said:**
> thx a lot **jfinkels**, it was very useful, but im not sure if **c** will still have its decimal points.

That's correct, casting the number "9.12" as an integer will return the integer "9".

A program to test the prime-ness of a number must inherently test only integers, as only integers can be prime (or composite). In other words, you won't be testing non-integral numbers anyway, so you don't need to bother with numbers with decimal points!

---

### Post by Ferrari69 on 2007-11-21
i have to have decimal points in my program so i can make that trick in the program..

here is the new idea for the program:

```
/* File: askisi1.5.c */
#include <stdio.h> /* Header file for standard I/O library */
#include <math.h> /* Header file for math library */
#define N 70

main()
{
      int ready, ready2, count, k, a, b, riza, num; /* Dilosi akereon, riza = root */
      double c;
            
      ready = 1;    /* Ka8orismos timis ka8e akereou */
      ready2 = 1;
      count = 1;
      k = 3;
      a = 0;
      b = 0;
      num = 3;
      riza = 0;
      c = 0;

for (k=3; k<=N; k=k+2)
{
	ready = 1;
	ready2 = 1;
  
	while (ready2 == 1)
	{
		riza = sqrt(b);
		for (count = 1 ; count<=riza ; count = count + 1)
		{
  		c = b/count;
  		if ((c<b) && (((int)c%2==0) || ((int)c%2==1)))
  		{
  			ready2 = 0;
  			count = riza + 1;
  			b = b;
  		}
  	    }
		b = b + 1; 
     }
  
	
	while (ready == 1)
	{
		for (count = 1; count<=k-1; count=count + 1)
		{
			b=b+count;
			/* here the composite code must enter again to:
            check if the b == composite. If yes continue. an oi, set ready = 1, then break; */
			if (count == k-1)
			{
			  /* alert("I have to store: " + b); that was some test in javascript,ignore it,as its not ready yet */
			  a = b - (k-1);
			  ready = 0;
			} else
			{
				/* alert("Not store: " +b);  that was some test in javascript,ignore it,as its not ready yet */
			}
		}
	}
}



printf("show %ld je %ld alla jeto %ld \n", k, a, b); /* NOT READY YET*/
getchar();
}

```

---

### Post by jfinkels on 2007-11-21
A couple of tips:

It's very hard to understand what's going on in your code. Too many loops, variables, etc. The key to programming is simplicity. Name your variables appropriately and clearly. Have only a few loops, avoid deeply nested loops. The most important: plan out how you're going to solve the problem before starting programming.

If I understand your problem correctly, you need to calculate whether a given number (or several numbers) is a prime number. Here's an idea: write a function that calculates whether a given number is a prime, like this:```
#include <stdio.h>
#define LOW 10
#define HIGH 20

int isPrime(int x) {
  int i, numberIsPrime;
  numberIsPrime = 1;

  for (i=2; i < x; ++i)
    if (x % i == 0)
      numberIsPrime = 0;

  return numberIsPrime;
}

void findPrimesBetween(int lower, int higher, int* result) {
  int i;

  i = 0;

  for (i = lower; i <= higher; i++)
    if (isPrime(i))
      result[i - lower] = i;
    else
      result[i - lower] = 0;

}

int main() {
  int i;
  int listOfPrimes[HIGH - LOW];

  findPrimesBetween(LOW, HIGH, &listOfPrimes);

  for (i = HIGH - LOW - 1; i >= 0; --i)
    if (listOfPrimes[i] != 0)
      printf("%d\n", listOfPrimes[i]);


  return 0;
}

```
Understand what's going on here?

Keep in mind, this is a very simple way of solving this problem, but it is also very inefficient.

---

### Post by Ferrari69 on 2007-11-21
thx for all your time and your help **jfinkels**, but i want to find the composite numbers and not primes, and i have to do this program without functions, thats why im lost in loops. anw thx again for all ur time u spent

---

### Post by jfinkels on 2007-11-21
> **Ferrari69 said:**
> thx for all your time and your help **jfinkels**, but i want to find the composite numbers and not primes,Then just return the inverse in the isPrime function:```
return !numberIsPrime;
```> and i have to do this program without functions, thats why im lost in loops.
Well you get the idea, then. It's easier to think in terms of functions anyway, in this case. Let me know if you have any more questions.

---

### Post by bongobonga on 2007-11-22
The '&' operator only works with integers, using it with anything else will result in a compile error. Use the fmod function for floating point numbers.

---

### Post by Ferrari69 on 2007-11-25
hello, ive managed to make the program at last..
here it is:

```
/* File: composites07133.c */
#include <stdio.h>            /* Header file for standard I/O library */
#include <math.h>             /* Header file for math library */
#define N 101
main()
{  
  int ready, protos, sira, num, num2, ats, min, max;   /* protos means prime, sira means serie, ats means Already Taken Serie */
    for (sira=1 ; sira<=N ; sira=sira+2) 
    {
      num = 2;           /* declearing values */
      protos = 1;        /* if its 1, then the number is prime || if its 0, then the number is composite */
      ready = 0;         /* if its 0, end of repeat if the composites numbers appeared before */
      while (ready == 0)
      {
            ats = 0; /* ats means already taken serie which checksi if it has show the team of composite numbers */
            
            if ((num%2 == 0) && (num != 2)) /* check if the num is composite */
               protos = 0; 
            for (num2=3 ; num2<=sqrt(num) ; num2=num2+2) /* check if the num is composite */
            { 
                if (num%num2 == 0)
                   protos = 0;
                   break;
            }
            while (protos == 0) 
            {
               ats = ats + 1;
               num = num + 1;
               protos = 1;
               
               if ((num%2 == 0) && (num != 2)) /* check if the num is composite */
               {
                  protos = 0;
                  continue;
               }
               for (num2=3 ; num2<=sqrt(num) ; num2=num2+2) /* check if the num is composite */
               { 
                  if (num%num2 == 0)
                  {
                     protos = 0;
                     break;
                  }
                             
               }
            }                 
          if (ats == sira) /* check if the consequtive composite numbers have been shown before */
          {  
                ready = 1;
                break;
          }
          else             /* if not, then keep checking */
          {
             num = num + 1;
             continue;
          }
       }
       min = num - sira; /* in that way will appear the 1st number of the serie */
       max = num - 1;    /* in that way will appear the last number of the serie */
       printf("First %d consecutive composites from %d to %d\n", sira, min, max);
    }

}


```

---

