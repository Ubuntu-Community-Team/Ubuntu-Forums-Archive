---
title: "can not compile!"
date: 2005-11-07
forum: Programming Talk
---

### Post by serlex on 2005-11-07
ok got a program from university, which works fine at university computers, it compile's fine using "make filename" command

when i try to compile on my ubuntu i get alot of syntax errors, im sure the problem is not the program, its the compilers i got in my ubuntu.

can someone give some compiler information, what i should have?

thanks

---

### Post by mustang on 2005-11-07
It might be helpful to post the actual errors the compiler is giving you.

---

### Post by serlex on 2005-11-09
> sercan@sercan:~/Desktop$ gcc distance.c
distance.c:14:19: error: stdio.h: No such file or directory
distance.c: In function &#8216;main&#8217;:
distance.c:25: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
distance.c:26: warning: incompatible implicit declaration of built-in function &#8216;scanf&#8217;
distance.c:35: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
distance.c:36: warning: incompatible implicit declaration of built-in function &#8216;scanf&#8217;
distance.c:45: error: syntax error before &#8216;}&#8217; token
distance.c: At top level:
distance.c:46: error: syntax error before string constant
distance.c:46: warning: conflicting types for built-in function &#8216;printf&#8217;
distance.c:46: warning: data definition has no type or storage class
distance.c:47: error: syntax error before string constant
distance.c:47: warning: conflicting types for built-in function &#8216;scanf&#8217;
distance.c:47: warning: data definition has no type or storage class
distance.c:60: error: &#8216;velocity&#8217; undeclared here (not in a function)
distance.c:60: error: &#8216;time&#8217; undeclared here (not in a function)
distance.c:60: error: &#8216;acceleration&#8217; undeclared here (not in a function)
distance.c:60: warning: data definition has no type or storage class
distance.c:62: error: syntax error before string constant
distance.c:62: warning: data definition has no type or storage class

not that i know much about programming, at uni we use make distance.c then ./distance and it works

---

### Post by darth_vector on 2005-11-09
have you done a

sudo apt-get install build-essential

---

### Post by serlex on 2005-11-09
ok done that. still getting lots of errors! what is the command to run a .c program?

---

### Post by darth_vector on 2005-11-09
how are you compiling it? is it just

gcc -o distance distance.c

?? if so, you can run the executable (not the .c file) by typing

./distance

if your compile command is

gcc distance.c

you will get an executable called a.out which can be run by typing

./a.out

---

### Post by serlex on 2005-11-09
yeah it works now, use ./distance.
C language question!
doing a formula, wanna put a limit on the value user can put in!
example: user can  not put in numbers above 10 and below 0! how do i do that?

velocity>=10 && velocity?????????

---

### Post by xaque on 2005-11-09
you'd have to do error checking. like:

velocity = 50
while (velocity < 0 || velocity > 10)
{
        // have the user input velocity
        // if velocity isn't in the desired range, print an error message
        // then the loop will repeat until velocity is in the desired range
}

messy way of doing it, but it works.

---

### Post by serlex on 2005-11-10
i did
> 
do
	{
	printf("Input Velocity :");
	scanf("%f", &velocity);
	}
	while (velocity>=10 && velocity <=0);


but did not work, i was able to input -2... numbers. the first bit works (>=10)
any ideas why second doesnt?

thanks

---

### Post by raublekick on 2005-11-10
you need to use or ( || ) not and ( && ). 

right now you're checking if the number is greater than 10 AND is below 0, which is impossible.

```
 do
{
printf("Input Velocity :");
scanf("%f", &velocity);
}
while (velocity>=10 || velocity <=0);
```

---

### Post by serlex on 2005-11-10
lol, just got that :) thanks, do i use '}else{' for a error message, if the user inputs data above 10

---

### Post by raublekick on 2005-11-10
currently your code will just loop until the user enters a valid number. if you want a message then you can do this:

```
 do
{
printf("Input Velocity :");
scanf("%f", &velocity);
if(velocity>=10 || velocity<=0)
{
     printf("ERROR: Please enter a number between 1 and 9");
}
}
while (velocity>=10 || velocity <=0);
```

it's not exactly the best way to do it but it should work

---

### Post by serlex on 2005-11-11
thanks for that, it works, but when it prints the "ERROR" it also prints the "input velocity" end of it.
'ERRROR:.....input veflocity:'

EDIT***

'\n' :)

---

### Post by serlex on 2005-11-11
what would i need to do, if i wanted to do the formula with or without the limits.

---

### Post by David Marrs on 2005-11-11
hehe, maybe it would be easier if you just gave us your assignment. ^^

Seriously though, you'd be doing yourself a favour if you sit down and work it out for yourself. Still, if you're looking to select from a number of options, check out the "switch" statement.

---

### Post by serlex on 2005-11-11
:P, ok fair enough, worth a try. yeah reading helps!

thanks any way

---

### Post by hrapozo on 2005-12-20
[QUOTE=darth_vector]if your compile command is

gcc distance.c

you will get an executable called a.out which can be run by typing

./a.out[/QUOTE]

I know other versions of Unix simplying typing a.out will run that compiled program.  I can accept typing the **./** before the **a.out** but is there a reason why this is so?

And I have two more followup questions relating to this:

1) Where in the documention is the ./ stated that needs to be used?
2) Is there a way to make it so that you can start the executable by simply typing in **a.out** instead of **./a.out**?

---

### Post by thumper on 2005-12-20
If the current directory is not in the PATH then you need to specify the location of the executable. "." specifies the current directory, so "./a.out" defines the location of the executable and hence the PATH is not used.  Without the location specifier the PATH is searched and a.out most likely not found.

---

### Post by darth_vector on 2005-12-20
[QUOTE=hrapozo]Is there a way to make it so that you can start the executable by simply typing in **a.out** instead of **./a.out**?[/QUOTE]

add the following lines to your .bashrc file:

```

PATH=$PATH:.
export path
```

---

