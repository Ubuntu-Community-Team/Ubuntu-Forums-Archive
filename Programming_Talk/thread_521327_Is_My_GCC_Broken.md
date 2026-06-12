---
title: "Is My GCC Broken?"
date: 2007-08-09
forum: Programming Talk
---

### Post by Noodels on 2007-08-09
Okay, for a while now I've been having problems with my gcc, I've been unable to put source programs together with the MAKE and the MAKE INSTALL commands. But today I found something new. I was trying to write a basic code for playing trading/merchanting games on the internet and the code is as follows.

```
#include <stdio.h>

int main()
{
 int money, cost;
 float amount;

 printf("Enter money : ");
 scanf("%d", money);
 printf("Enter cost  : ");
 scanf("%d", cost);
 amount = money / cost ;
 printf("You can buy : %d\n", amount);
 return 0;
}
```

And I compile it, the following comes up to indicate a smooth compile.

```
noodels@noodels-desktop:~/prg$ gcc -o mnt mrchnt.c
noodels@noodels-desktop:~/prg$ 

```

So I assume there are no problems there. The problems come once I tested the program like so.

```
noodels@noodels-desktop:~/prg$ ./mnt
Enter money : 10
Enter cost  : 10
You can buy : 0
noodels@noodels-desktop:~/prg$ ./mnt
Enter money : 100
Enter cost  : 10
You can buy : 0
noodels@noodels-desktop:~/prg$ ./mnt
Enter money : 10000000
Enter cost  : 10
You can buy : 0
noodels@noodels-desktop:~/prg$ 

```

To check if there was a problem in the calculation step I altered the code so that the money would be multiplied by the cost (makes no sense but I wanted to check it was working) and the following was displayed.

```
noodels@noodels-desktop:~/prg$ ./mnt
Enter money : 10
Enter cost  : 10
You can buy : 0
noodels@noodels-desktop:~/prg$ ./mnt
Enter money : 100
Enter cost  : 10
You can buy : 0
noodels@noodels-desktop:~/prg$ 

```

But when I replaced the floating point with an integer to be the factor the following appeared.

```
noodels@noodels-desktop:~/prg$ ./mnt
Enter money : 10
Enter cost  : 10
You can buy : -1723955168
noodels@noodels-desktop:~/prg$ ./mnt
Enter money : 10
Enter cost  : 10
You can buy : -1882181280
noodels@noodels-desktop:~/prg$ ./mnt
Enter money : 10
Enter cost  : 10
You can buy : -1383338592
noodels@noodels-desktop:~/prg$ 

```

Which makes no sense at all. Can anyone put this code in their compiler and tell me what they get? Is it my code or my compiler? And if no-one can help at least I know how to generate random numbers now :) .

---

### Post by Wybiral on 2007-08-09
GCC isn't broke...

You need to change:
```

 printf("You can buy : %d\n", amount);

```
to
```

 printf("You can buy : %f\n", amount);

```
Since it's a float, NOT a signed int.

Also, "scanf" expects pointers, not integers.

```

 printf("Enter money : ");
 scanf("%d", &money);
 printf("Enter cost  : ");
 scanf("%d", &cost);

```

Try compiling with:

```

gcc my_program.c -Wall

```

The "-Wall" flag will tell it to be more observant about warnings (and will tell you that you were using scanf incorrectly).

---

### Post by Jessehk on 2007-08-09
```

#include <stdio.h>
#include <stdlib.h>

#define BUFFSIZE 64

int main( void ) {
    char buffer[BUFFSIZE];
    int money, cost;
    
    /* Should be an integer, because you're dealing */
    /* with the amount of something you can buy. */
    int amount;
    
    printf( "Enter money: " );
    
    /*
     * First read input as a string of characters
     * BUFFSIZE chars long using fgets.
     *
     * This means to get input a maximium input
     * of BUFFSIZE (which we #define'd as 64) characters,
     * put in into buffer, and read from stdin (which is the
     * standard input).
     *
     * If there was an error readding the input, 
     * fgets returns NULL. We really should check for errors, but
     * for simplicity, we're not going to.
     */
    fgets( buffer, BUFFSIZE, stdin );
    
    /*
     * Use the sscanf (not scanf, _s_scanf) function to convert
     * the input we got into the type that we wanted. In this case,
     * we're going to convert the string of characters to an integer.
     * sscanf returns the number of arguments it successfully converted.
     * If that number is less than what you want, the string could not
     * be converted. Once again, for simplicity's sake, we're not going
     * to check for errors but you really should.
     */
    sscanf( buffer, "%d", &money );
    
    /* Repeat for "cost"; */
    printf( "Enter cost: " );
    fgets( buffer, BUFFSIZE, stdin );
    sscanf( buffer, "%d", &cost );
    
    amount = money / cost;
    
    printf( "You can buy: %d\n", amount );
    
    return 0;
}

```

---

### Post by Noodels on 2007-08-09
Okay thanks you two. I usually use integers in my codes and I don't have a reference so that's why I used %d rather than %f. I want to use a float because sometimes the money may not go into cost perfectly and if possible I would prefer it rounds it down. But I'm not sure how to do that. Doesn't explain why I can't compile programs from source but I'm probably doing something stupid there too.

Jessek, you kinda lost me with those explanations, I'll do as you say and try to work out what it's doing on my own though.

---

### Post by Rocket2DMn on 2007-08-09
If you use an integer for amount, you should be good since it will always round down.  When you scanf(), you should be using pointers to store the values input, so you put the & sign in front of the variables, ex:
```
printf("Enter money : ");
scanf("%d", &money);
```
You do not want the & for printf()'s.

---

### Post by rbprogrammer on 2007-08-09
Noodels, check out this site: [http://www.cplusplus.com/reference/clibrary/cstdio/](http://www.cplusplus.com/reference/clibrary/cstdio/)

particularly for printf() and scanf() functions.  as someone who was taught c++ first, i now find myself loving to program with just C. so i'm constantly referencing that website.

---

