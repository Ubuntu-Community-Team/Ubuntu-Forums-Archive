---
title: "Help me in a simple Program."
date: 2010-10-24
forum: Programming Talk
---

### Post by rshinde70 on 2010-10-24
please check out the attachment,
I've written an program for finding two variables but it doesn't works :(

Also I've inserted an picture of the terminal showing the output for this program.

Friends.. I'm waiting for your replies ....

---

### Post by krishnandu.sarkar on 2010-10-24
I think you should start a and b with 1, because anything multiplying with 0 returns 0. So the condition is getting true each time.

BTW remember initializing those variables with 1 will never make your condition true, so you won't get any output.

---

### Post by shankhs on 2010-10-24
As I understand you want to find a,b for:

(a+b)^2 = a^2 + b^2

This is only possible if a=0 ( any value of b) or b=0 ( any value of a )

Am I missing anything?

---

### Post by darshan123 on 2010-10-24
Actually, a*a  +  2*a*b  + b*b  =  (a+b) * (a+b)

in ur case, the condition is satified only when b == 0 . hence the output.

change the formula and things will be fine.

Darshan

---

### Post by arubislander on 2010-10-24
> **shankhs said:**
> As I understand you want to find a,b for:

(a+b)^2 = a^2 + b^2

This is only possible if a=0 ( any value of b) or b=0 ( any value of a )

Am I missing anything?

Yep you are: 2*a*b

---

### Post by rshinde70 on 2010-10-24
@[krishnandu.sarkar]("http://ubuntuforums.org/member.php?u=1063048") you are true,
 but Friends, somebody told me that, there are really two numbers, and those are non-zero.
so i thought, to make a program to search it.

look at the output carefully, you will get noticed that, only one variable is getting incremented while both should get incremented..
like..

for a=0, b should increment from 0 to 999,
again, for a=1, b from 0-999, and so on upto a becomes 999.

please help.

](*,) :confused:  ](*,)

---

### Post by shankhs on 2010-10-24
(a+b)^2 = a^2+b^2
=>a^2+b^2+2ab=a^2+b^2
=>2ab=0

So either a=0 or b=0
:)

---

### Post by rshinde70 on 2010-10-24
@ shankhs,

(a+b)^2 = a^2+b^2

is not possible,
actually, the correct formula is :



(a+b)^2 = a^2+b^2 + 2*a*b

---

### Post by krishnandu.sarkar on 2010-10-24
> **rshinde70 said:**
> @[krishnandu.sarkar]("http://ubuntuforums.org/member.php?u=1063048") you are true,
 but Friends, somebody told me that, there are really two numbers, and those are non-zero.
so i thought, to make a program to search it.

look at the output carefully, you will get noticed that, only one variable is getting incremented while both should get incremented..
like..

for a=0, b should increment from 0 to 999,
again, for a=1, b from 0-999, and so on upto a becomes 999.

please help.

](*,) :confused:  ](*,)


Well...how would we know what formula or what do you want to implement. I just corrected the logic.

---

### Post by krishnandu.sarkar on 2010-10-24
Do you want this thing??

> #include<stdio.h>
main()
{
    
    
    //  A PROGRAM TO FIND a AND b IF (a*a)+(2*a*b)+(b*b) = (a*a)+(b*b) 
    
    int i;
    int a=0, b=0;
    int x, y;
    
    for(i=0;i<1000;i++)
    {    
        
        x=(a*a)+(2*a*b)+(b*b);
        
        y=(a*a)+(b*b);
        
        if(x==y)
        {
            printf("\na=%d\tb=%d",a,b);
            a++;
            b++;
        }        
        
    }
    
    if(a==999 && b==999)
    printf("\nElements not found!");
    

}    

---

### Post by arubislander on 2010-10-24
Pencil, paper and highschool math reveal:

(a+b)*(a+b)=a*a + b*b
<=> a*a + 2*a*b + b*b = a*a + b*b
<=> 2*a*b = 0
so: a=0 or b=0!

---

### Post by rshinde70 on 2010-10-25
](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)


It doesn't works !

I want this to be work as like password breaker software.
Its loops should work like that.

for example :

If i want to look for a and b then =====>

it should work like :

a=0, b=0
a=0, b=1
a=0, b=2
.
.
.
.
a=0, b=999;

and then,

a=1, b=0
a=1, b=1
a=1, b=2
.
.
.
a=1, b=999
.
.
.
.
.
a=999, b=999


please help somebody..

look carefully in " for "

---

### Post by Vaphell on 2010-10-25
but it does that, x==y comparison is done exactly 1000000 times
you don't see it because you printf(a, b) only when x==y and that happens exactly 1999 times: (0,0-999) and (0-999,0) minus 1 ((0,0) is in both sets)

besides no program in the world will help you when you can't see the obviousness of your problem. It's a basic math.

run this
[php]#include<stdio.h>
main()
{
  //  A PROGRAM TO FIND a AND b IF (a*a)+(2*a*b)+(b*b) = (a*a)+(b*b) 
	
  int a, b;
  int x, y;
  int counter = 0;
  int counter_if_any_zero = 0;
  int total_tests = 0;
	
  for(a=0;a<1000;a++)
  {			
    for(b=0;b<1000;b++)
    {
      total_tests++;
      x=((a*a)+(2*a*b)+(b*b));
      y=(a*a)+(b*b);
		
      if(x==y)
      {
        printf("a=%d\tb=%d\n",a,b);
        counter++;
        if(!(a && b))
          counter_if_any_zero++;
      }
    }			
  }
  printf( "number of tests: %d\n", total_tests );
  printf( "found: %d\n", counter );
  printf( "found with a=0 or b=0: %d\n", counter_if_any_zero );
  if(!counter)
    printf("Elements not found!");
}
[/php]

---

### Post by VernonA on 2010-10-26
@OP. Your program is working fine, and is printing out all the correct solutions. It is checking a million combinations of a and b, and is correct when it says that the only ones which are valid are those in which a is zero or b is zero. Your screen capture indeed shows the end of the list, where a is non-zero and b is 0.

Multiple posters have noted that the formula for your x variable is just (a+b)^2 but since C doesn't provide an exponentiation operator you have to expand it using schoolbook algebra to the formula you are actually using. By adding some whitespace to your formulae, you will see you are computing:
```
    x=((a*a)+(2*a*b)+(b*b));
    y= (a*a)+        (b*b) ;

```and it should be clear that the only way these two will be equal is if the 2*a*b term is zero.

Finally, if you still doubt your own code, add an else clause to the 'if', eg:
```
    if (x==y)
        printf("\na=%d\tb=%d",a,b);
    else
        printf("\na=%d\tb=%d is NOT a solution",a,b);
```
This will at least show the loops are working as you intended, although the output is going to be pretty long-winded!

---

### Post by rshinde70 on 2010-10-27
@[Vaphell]("http://ubuntuforums.org/member.php?u=347382")
you are right.
I just wanted to confirm that, those for loops are working correctly or not.
But yeah, that structure is correct. Thank you Very Very Much Vaphell.

=;=;=;=;=;=;=;

---

