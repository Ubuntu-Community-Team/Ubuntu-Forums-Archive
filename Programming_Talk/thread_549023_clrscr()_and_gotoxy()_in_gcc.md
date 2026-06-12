---
title: "clrscr() and gotoxy() in gcc"
date: 2007-09-12
forum: Programming Talk
---

### Post by mitchi on 2007-09-12
clrscr()
just add the following to your code to clear the screen first before executing your program.

> 
#include<stdlib.h>
main()
{
system("clear");* //clears the screen*
}


gotoxy()
just add the following to your code to use the gotoxy() function, which changes the position of the cursor to the desired coordinates of your screen.

> 
#include<stdio.h>
*//gotoxy function*
void gotoxy(int x,int y)
{
printf("%c[%d;%df",0x1B,y,x);
}
main ()
{
gotoxy(25,50); *//reposition cursor*
printf("hello world"); *//display text*
}


---

### Post by dwhitney67 on 2007-09-12
Would it not be easier to use ncurses?  All of the "work" has been done to provide one the capability to manipulate the position of the cursor (and output) within an xterm.

[FONT="Courier New"]$ man ncurses[/FONT]

---

### Post by Lux Perpetua on 2007-09-12
```
xxxxxxx@xxxx:temp> a.out
                        hello worldxxxxxxx@xxxx:temp> 

```Is that what program #2 was supposed to do?

And you really should look into ncurses. It's much more flexible than anything you can hack together with system() and printf().

---

### Post by gnusci on 2007-09-12
I think his two functions are much better than use a library, anyway why two use a library just for two functions... Make a code depending of one library just for a couple of functions does not have any sense...!!!

Maybe the functions are not working completely correct but they will work better after fix some bugs...

Thanks for the functions **mitchi**...

---

### Post by adeross6 on 2011-05-27
> **mitchi said:**
> clrscr()
just add the following to your code to clear the screen first before executing your program.



gotoxy()
just add the following to your code to use the gotoxy() function, which changes the position of the cursor to the desired coordinates of your screen.

thanks it works, i have tried to this

---

### Post by ziekfiguur on 2011-05-28
Instead of using system to call an external program, you could also use this:
```

fprintf(stdout, "\033[2J\033[0;0f");
fflush(stdout);

```

---

### Post by liju.g.chacko on 2012-05-25
> **TRY THIS ONE**

#include<stdio.h>
#include<stdlib.h>
int lasti=0,lastj=0;
void goback(int x,int y)
{ 
      printf("\033[%dA",x);
      printf("\033[%dD",y);
}
void gotoxy(int x,int y)
{   
    extern int lasti, lastj;
    goback(lasti, lastj);
    int i;
    for(i=0;i<x;i++)
      printf("\n");
    for(i=0;i<y;i++)
      printf("\t");
      lasti=x;
      lastj=y;

}

int main ()
{
    int i=0;
    while(1)
    {   i=i+1;
        gotoxy(12,5);
        printf("hello   i=%d\r",i); //display text
        gotoxy(10,5);
        printf("hello i-1=%d\r",i-1); 
        usleep(3*1000);
    }
}

---

### Post by ranjanak on 2013-05-06
Hi,
I have tried above code, I am able to change y position in screen but I am not able to change x position, i am passing different x value then then also my x value is 0 only.

---

### Post by ranjanak on 2013-05-06
Hi,
I tried above code but I am not able to move x position, I am passing different value then also x position is 0 only.

---

### Post by nidzo732 on 2013-05-06
The gotoxy and clrscr are functions from Windows C library. They are not available on Linux.

---

### Post by matt_symes on 2013-05-09
Old thread so closed.

---

