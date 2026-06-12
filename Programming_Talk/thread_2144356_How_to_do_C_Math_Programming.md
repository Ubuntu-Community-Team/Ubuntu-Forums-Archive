---
title: "How to do C Math Programming ?"
date: 2013-05-11
forum: Programming Talk
---

### Post by virus7 on 2013-05-11
Hey I am an absolute bigginer thats why I may be posting this to wrong section, am sorry for this.

well am trying to do some C programming using Ubuntu gedit and compiling with gcc. but recently I was trying to compile a program with function needed from math.h but when I was trying to do that I got an error which is something like this,

" 4.1.o: In function `main': 
  4.1.c:(.text+0x60): undefined reference to `pow'
  collect2: ld returned 1 exit status "

what does it mean?? and how can i relate math function with my code.

thanks in advance .. !!!

---

### Post by matt_symes on 2013-05-11
Thread moved to **programming talk**.

---

### Post by QIII on 2013-05-11
Hi!

It would be good to post the code so that it may be reviewed.

Cheers.

---

### Post by virus7 on 2013-05-11
here is a simple code i was trying to execute :

```
/* Calculating compound interest */

#include <stdio.h>
#include <math.h>
 
int main()

{

 double amount;
 double principal = 1000.0;
 double rate = 0.05;
 int year;

  printf("%4s%21s\n", "year", "Amount on deposit");
 
  for (year=1; year<=10; year++)
    {
     amount=principal * pow(1.0+rate, year);
     printf("%4d%21.2f\n", year, amount);
    }

 return 0;
}
```

---

### Post by xb12x on 2013-05-11
Add -lm to your link options, since pow() is from the math library:


gcc myprogram.c -lm

---

### Post by virus7 on 2013-05-11
> **xb12x said:**
> Add -lm to your link options, since pow() is from the math library:


gcc myprogram.c -lm

hello there, i found this solution on net too.. and thank you very much for your kind help but the thing which makes me really confused that where exactly I should write this -lm :(
well I just want to add something with this, how exactly i am executing my program in terminal 
```

gcc -c 4.1.c
gcc 4.1.o -o 4.1
./4.1

```

but I tired to execute 
gcc -c 4.1.c -lm <which works just fine> 
gcc 4.1.o -o 4.1 <it doesnt work and gives me same error>

thanks...

---

### Post by xb12x on 2013-05-12
> **virus7 said:**
> hello there, i found this solution on net too.. and thank you very much for your kind help but the thing which makes me really confused that where exactly I should write this -lm :( well I just want to add something with this, how exactly i am executing my program in terminal  ```
 gcc -c 4.1.c gcc 4.1.o -o 4.1 ./4.1 
```  but I tired to execute  gcc -c 4.1.c -lm   gcc 4.1.o -o 4.1   thanks...        

```

To compile 4.1.c and link it to the math library, remove the -c option from your build command. 
The  -c option causes the build to not link, it only compiles. 

You need to link to create an executable (and link to the math library). 
Other libraries are  linked by default,  but the math library is not, 
you need to name it specifically (with the -lm option).    

Here is the command:   

gcc 4.1.c -lm  -o 4.1       

To run the output of the compile + link: 

./4.1

And here is the output of your program running on my machine:

year    Amount on deposit
   1              1050.00
   2              1102.50
   3              1157.63
   4              1215.51
   5              1276.28
   6              1340.10
   7              1407.10
   8              1477.46
   9              1551.33
  10              1628.89



```

---

### Post by virus7 on 2013-05-12
thanks a lot..... :D

---

### Post by nvteighen on 2013-05-12
OK, your problem has been solved, but now, please, take your time to read my post in order to **understand** what was happening there.

Contrary to what you might have believed, using *#import <math.h>* does not import the library into your code. Header files (take a look at them... math.h is at /usr/include/math.h) do not have "real" code in them, but they only declare the functions' signatures (the function's name, its return type and types of its parameters). That's it. So, where is the pow() function implemented? In a **library** file, which is a binary compiled in a special way that allows it to be **linked** to your program so that you can access the code inside of it. In the case of the C Math Library, this library is called libm.so (/usr/lib/libmath.so... don't try opening it; it's a binary... but you can download its source via apt-get if you like!).

The C compiler works like this: 1) It first **preprocesses** your source, which in your case means pasting the importing headers into your code exactly like you would do it manually. 2) The source is compiled into Assembly (you can stop your compiler here by using the -S flag, if you're curious what the ASM of your C code is). 3) The ASM code is assembled to a binary, a so-called **object file** (.o file extension)... When you use the -c flag in gcc, you are telling the compiler to stop at this stage. 4) Link all object files together to create an executable. Libraries are a special kind of object file, so here is where they kick into the process. As the header files don't give any information on where the libraries are nor on their names, you have to pass the -l flag (libXYZ.so > -lXYZ, libm.so > -lm, etc.). to the compiler for it to finish the process successfully.

---

### Post by virus7 on 2013-05-16
> **nvteighen said:**
> OK, your problem has been solved, but now, please, take your time to read my post in order to **understand** what was happening there.

Contrary to what you might have believed, using *#import <math.h>* does not import the library into your code. Header files (take a look at them... math.h is at /usr/include/math.h) do not have "real" code in them, but they only declare the functions' signatures (the function's name, its return type and types of its parameters). That's it. So, where is the pow() function implemented? In a **library** file, which is a binary compiled in a special way that allows it to be **linked** to your program so that you can access the code inside of it. In the case of the C Math Library, this library is called libm.so (/usr/lib/libmath.so... don't try opening it; it's a binary... but you can download its source via apt-get if you like!).

The C compiler works like this: 1) It first **preprocesses** your source, which in your case means pasting the importing headers into your code exactly like you would do it manually. 2) The source is compiled into Assembly (you can stop your compiler here by using the -S flag, if you're curious what the ASM of your C code is). 3) The ASM code is assembled to a binary, a so-called **object file** (.o file extension)... When you use the -c flag in gcc, you are telling the compiler to stop at this stage. 4) Link all object files together to create an executable. Libraries are a special kind of object file, so here is where they kick into the process. As the header files don't give any information on where the libraries are nor on their names, you have to pass the -l flag (libXYZ.so > -lXYZ, libm.so > -lm, etc.). to the compiler for it to finish the process successfully.

hello, thank you very much .. I have learned a lot from your step by step explantion .. :)

---

