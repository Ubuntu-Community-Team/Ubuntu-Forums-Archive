---
title: "Is there any wait function for all OS ?"
date: 2011-05-01
forum: Programming Talk
---

### Post by mert_da on 2011-05-01
Hello!
 
I'm writing a program on C. I'm searching for a function which sleeps the process for any second (or any time unit) but i could not found anythink.
 
The sleep function works great but it works just on Windows :8 But i need a function which works on at least POSIX+Windows systems. 
 
Does anyone know about it?
 
Thank you!

---

### Post by NovaAesa on 2011-05-01
I don't know of anything that will work on both POSIX and Windows. Pthreads is the way to go for POSIX though.

---

### Post by ssam on 2011-05-01
you could use this method
[http://www.hackerthreads.org/Topic-32204](http://www.hackerthreads.org/Topic-32204)

---

### Post by Elfy on 2011-05-01
moved to programming talk

---

### Post by TeoBigusGeekus on 2011-05-01
```
#include <stdio.h>
#include <time.h>
int main(void)
{
    printf("Delay(seconds): ");	
    float secs;
    scanf("%f",&secs);	
    clock_t delay=secs*CLOCKS_PER_SEC; 
    printf("Starting\n");
    clock_t start=clock();
    while (clock()-start<delay)
       ;
    printf("Done\n");
    return 0;
}
```

---

### Post by nvteighen on 2011-05-01
Uh... what are you precisely asking about? In GNU/Linux there's a sleep function and there's also wait, which is completely unrelated.

I think you want sleep, which delays execution for a couple of seconds. It's declared in unistd.h and it's a POSIX function.

If you're working with child processes (fork & friends), then what you want is wait, which makes the parent wait for the child to finish execution. It's declared in sys/wait.h, but you'll need sys/types.h too. Forking functions are part of the "BSD API", which has been included in POSIX too.

---

### Post by mert_da on 2011-05-01
> **TeoBigusGeekus said:**
> ```
#include <stdio.h>
#include <time.h>
int main(void)
{
    printf("Delay(seconds): ");	
    float secs;
    scanf("%f",&secs);	
    clock_t delay=secs*CLOCKS_PER_SEC; 
    printf("Starting\n");
    clock_t start=clock();
    while (clock()-start<delay)
       ;
    printf("Done\n");
    return 0;
}
```

That worked great :) 

Thank you!

Now that already has moved the thread on "programming talk" i need to ask something else... 

This code is just a part of my program:

 if((a==-1) && (!is_empty(arrival_time, islem_adeti)) );
         {
                 printf("%d", a);
                 now++;
                 goto upthere;
         }

The output of printf("%d", a); is always 1. But this is impossible?! right!? Because if a=1 , can not  run the if block. Can someone explain that please ?

I try it on Windows with dev c also on Ubuntu with gcc but both of them make the same output...

Also i note that there is no fork or thread on my program to change the "int a" as 1..

---

### Post by GeneralZod on 2011-05-01
You have a semi-colon after your "if" clause :)

---

### Post by mert_da on 2011-05-01
> **GeneralZod said:**
> You have a semi-colon after your "if" clause :)

Oh my god! :o:o:o:o:o

Dev C need to show me that! :( I am researching about this issue for 2 days...

Thank you again!

---

### Post by SledgeHammer_999 on 2011-05-01
> **mert_da said:**
> That worked great :) 

Thank you!

Check the cpu usage when using that! It will be at 100%(for single core cpus)

Better use the sleep() function mentioned by **nvteighen**


> Dev C need to show me that! I am researching about this issue for 2 days...


Your mistake IS valid C syntax. :p

---

### Post by TeoBigusGeekus on 2011-05-01
> **SledgeHammer_999 said:**
> Check the cpu usage when using that! It will be at 100%(for single core cpus)

Better use the sleep() function mentioned by **nvteighen**


How's the sleep function gonna work in windows+linux?

---

### Post by SledgeHammer_999 on 2011-05-01
Oh I forgot about that.

One way is to use mingw to compile on windows and not msvc.

The other way is to use preprocessor directives(!ifdef) to include the windows.h/unistd.h headers conditionally... (and call the correct function sleep() or Sleep())

---

### Post by mert_da on 2011-05-02
TeoBigusGeekus that worked for me:

#include <stdio.h>
#include <time.h>
int main(void)
{
printf("Delay(seconds): ");	
float secs;
scanf("%f",&secs);	
clock_t delay=secs*CLOCKS_PER_SEC; 
printf("Starting\n");
clock_t start=clock();
while (clock()-start<delay)
;
printf("Done\n");
return 0;
}

But worked just for Windows. It maybe works on Linux too, but the cpu on linux is on high level (also on windows) and it does not seems waits any clock or something. It just put me all text on the screen. But on windows the text are coming very nicely. (with "text" i mean my printf and other proceses of my own program.. )

My teacher told me that to do not use "clock" for wait, because it uses on high level the cpu.

Thats why i go here ( [http://www.hackerthreads.org/Topic-32204](http://www.hackerthreads.org/Topic-32204) )and i copy this code on me :

#ifdef WIN32
#include <windows.h>
#define SLEEP(x) Sleep(x) /* Windows version */
#else
#include <unistd.h>
#define SLEEP(x) sleep(x) /* Linux version */
#endif

It must work but now there is another problem. The devC can not compile the code. It gives me a syntax error. But when i delete just this part of code, my program is compiling, also it works properly. I test it many times.

So ? Is there any problem here : 

#ifdef WIN32
#include <windows.h>
#define SLEEP(x) Sleep(x) /* Windows version */
#else
#include <unistd.h>
#define SLEEP(x) sleep(x) /* Linux version */
#endif

I am sure that i don't have any problem on my own program.

---

### Post by SledgeHammer_999 on 2011-05-02
Your code has an error:
Sleep(x)-> x is the time you in **milliseconds**
sleep(x)-> x is the time in **seconds**

> It must work but now there is another problem. The devC can not compile the code. It gives me a syntax error. But when i delete just this part of code, my program is compiling, also it works properly. I test it many times.

Please post the error message and the relevant code(the lines the error refers to).

---

### Post by ssam on 2011-05-02
> **SledgeHammer_999 said:**
> Your code has an error:
Sleep(x)-> x is the time you in **milliseconds**
sleep(x)-> x is the time in **seconds**


the version at the bottom of the hackerthreads page takes this into account

---

### Post by mert_da on 2011-05-02
> **SledgeHammer_999 said:**
> Your code has an error:
Sleep(x)-> x is the time you in **milliseconds**
sleep(x)-> x is the time in **seconds**



Please post the error message and the relevant code(the lines the error refers to).

I will look  for seconds and milliseconds, after compile the code. Thanks for warning...

The error code i get after add this ifdef part is :

```
C:\school.cpp:31: error: expected unqualified-id before "int"
C:\school.cpp:31: error: expected `)' before "int"
C:\school.cpp:31: error: expected `)' before "int"
C:\school.cpp:31: error: expected `,' or `;' before "int" 
C:\school.cpp: In function `void RR(int, int*, int*, int, int)':
C:\school.cpp:228: error: ISO C++ forbids comparison between pointer and integer
C:\school.cpp:228: error: operands to ?: have different types 
C:\school.cpp: In function `void FCFS(int, int*, int*, int)':
C:\school.cpp:332: error: ISO C++ forbids comparison between pointer and integer
C:\school.cpp:332: error: operands to ?: have different types 
C:\school.cpp: At global scope: 
C:\school.cpp:361: error: expected unqualified-id before "int"
C:\school.cpp:361: error: expected `)' before "int"
C:\school.cpp:361: error: expected `)' before "int"
C:\school.cpp:361: error: expected `,' or `;' before "int"

```

But when i remove the ifdef part the program is compiling and it works properly. I eman the problem is on this part not on my own code.

Look at the error on this line : 
C:\school.cpp:332: error: ISO C++ forbids comparison between pointer and integer

It writess C++. But my code is C. I think this ifdef or whatever, is a feature for C++. Thas why it gives error ? Right ?

---

### Post by SledgeHammer_999 on 2011-05-02
What is in line 31 in school.cpp?

Also if you really code in C, you should name school.cpp to school.c 
.cpp is used for C++ code.

---

### Post by mert_da on 2011-05-03
> **SledgeHammer_999 said:**
> What is in line 31 in school.cpp?

Also if you really code in C, you should name school.cpp to school.c 
.cpp is used for C++ code.

I change the .cpp as .c.

31 line is:
int min(int* arrival_time, int process_max);

There is no any problem on my own code. I can compile and run it properly after i remove the #ifdef part. The errors which give me the compiler is ********.

Are you sure if the ifdef part is true ?

---

### Post by Npl on 2011-05-03
> **mert_da said:**
> I change the .cpp as .c.

31 line is:
int min(int* arrival_time, int process_max);

There is no any problem on my own code. I can compile and run it properly after i remove the #ifdef part. The errors which give me the compiler is ********.

Are you sure if the ifdef part is true ?you probably need to define WIN32, its apparently assumed compilers/IDE on windows do so automatically. This is wrong (for **every** compiler, only the Visual Studio IDE sets this define on new Projects)

---

### Post by SledgeHammer_999 on 2011-05-03
@mert_da
can you post line 30 too? I think the error message refers to the int that's in bold-> **int** min(int* arrival_time, int process_max);

Also please put your code INSIDE [code][/ code] tags

---

### Post by mert_da on 2011-05-04
Sorry , i did not know that i must write the ifdef part inside a function :( now the problem solved. Thank you!

---

