---
title: "Any help?"
date: 2012-05-06
forum: Programming Talk
---

### Post by ALBUL on 2012-05-06
This is my calculator:

```
#include <stdio.h>
#include <ctype.h>
#include <iostream>
#include "myconio.h"
using namespace std;
main()
{
float x, y, c;
int z,i;
printf("CEL MAI TARE CALCULATOR!!!!\n");
start:
printf("Primul numar: ");
if(scanf("%f", &x)!=1){
printf("Nu ati introdus un numar sau o cifra!");
getch();
fflush(stdin);
clrscr();
goto start;
}
printf("Al doilea numar: ");
if(scanf("%f", &y)!=1){
printf("Nu ati introdus un numar sau o cifra!");
getch();
clrscr();
fflush(stdin);
goto start;
}
printf("Apasati: 1.Adunare 2.Scadere 3.Inmultire 4.Impartire: ");
if(scanf("%d", &z)!=1){
printf("Nu ati introdus o cifra!");
getch();
clrscr();
fflush(stdin);
goto start;
}
if (z == 1)
{
c = x+y;
printf("Rezultatul este: %.2f\n", c);
getch();
clrscr();
goto fin;
}
if (z == 2)
{
c = x-y;
printf("Rezultatul este: %.2f\n", c);
getch();
clrscr();
goto fin;
}
if (z == 3)
{
c = x*y;
printf("Rezultatul este: %.2f\n", c);
getch();
clrscr();
goto fin;
}
if (z == 4)
{
if (y == 0) {
printf("Nu se poate imparti la zero!!!!!!!");
getch();
clrscr();
goto start;
} else {
c = x/y;
printf("Rezultatul este: %.2f\n", c);
getch();
clrscr();
goto fin;
}
}
if (z != 1 || 2 || 3 || 4)
{
printf ("Ati apasat un buton gresit... Va vom duce inapoi la inceput!");
getch();
clrscr();
fflush(stdin);
goto start;
}
fin:
printf ("Apasati: 1.Continuare 2.Iesire: ");
if(scanf("%d", &i)!=1){
printf("Nu ati apasat pe o cifra! Programul se va inchide!");
getch();
goto end;
}
if (i == 1)
{
clrscr();
goto start;
}
if (i == 2)
{
puts ("La revedere!");
getch();
goto end;
}
if (i != 1 || 2)
{
printf ("Raspunsul aleatoriu se va lua drept iesire. La revedere!");
getch();
}
end:

;}

```And myconio.h

```
#include <termios.h>
#include <unistd.h>

int getch(void)
{
struct termios oldt,
newt;
int ch;
tcgetattr( STDIN_FILENO, &oldt );
newt = oldt;
newt.c_lflag &= ~( ICANON | ECHO );
tcsetattr( STDIN_FILENO, TCSANOW, &newt );
ch = getchar();
tcsetattr( STDIN_FILENO, TCSANOW, &oldt );
return ch;
}

int clrscr(void)
{
    printf ("\x1B[2J");
    printf ("\x1B[0;0H");
}

```I use a modified getch() from myconio.h. It does well until (the code under) where it must add x to y if was selected first option (adding). At this part of code it doesn`t want to pause and goes directly at fin.
 ```
if (z == 1)
{
c = x+y;
printf("Rezultatul este: %.2f\n", c);
getch();
clrscr();
goto fin;
}
```

---

### Post by Bachstelze on 2012-05-06
[http://c-faq.com/stdio/stdinflush.html](http://c-faq.com/stdio/stdinflush.html)

---

### Post by ALBUL on 2012-05-06
Like this?

```
if (z == 1)
 {
 c = x+y; 
printf("Rezultatul este: %.2f\n", c);
fflush(stdin);
getch();
 clrscr();
 goto fin; 
}
```

---

### Post by Bachstelze on 2012-05-06
No. fflush(stdin); does not do what you think it does. Read the link.

(This is my last message in this thread, this code is so dirty I want to take a shower now, even though I took one two hours ago.)

---

### Post by mehaga on 2012-05-06
> **Bachstelze said:**
> 
(This is my last message in this thread, this code is so dirty I want to take a shower now, even though I took one two hours ago.)

That will surely help him :/

---

### Post by PeterP24 on 2012-05-06
Hey @ALBUL - here is some constructive criticism:
First of all: "bine ai venit pe forumul Ubuntu!"
Second: you appear to mix C with C++ code by using both <stdio.h> and <iostream> - however, what follows after your inclusions it is not C++ code as far as I can tell;
Third: goto instruction is a no no as far as I can tell; There are people that claim that goto has is uses - but you are not using it in that particular direction;
Fourth: It helps to write in plain English the strings in your program if you want to get some help. Last time I checked, Romanian was not an international language spoken and understood by people all over the world. 

Best regards,

Petre

---

### Post by r-senior on 2012-05-06
> **PeterP24 said:**
> Third: goto instruction is a no no as far as I can tell; There are people that claim that goto has is uses - but you are not using it in that particular direction;
IMO there's nothing wrong with goto in C if used sensibly. It's often to provide a single exit point from a function without heavily nested conditionals. Something along the lines of:

```
a = fn_a();
if (a < 0) {
    perror("fn_a");
    goto cleanup;
}

b = fn_b()
if (b < 0) {
    perror("fn_b");
    goto cleanup;
}

do_something_interesting()

cleanup:
    close_a_and_b();

```

You'll see code like this all over the Linux kernel, and in other places.

Petre used the word direction and direction is a large part of it. Gotos that go forward to an exit point flatten out the structure of a function and make it more readable. It's the same idea as a try ... finally block in languages that have those structures. 

Gotos that go backward can easily get out of hand and create spaghetti code. They don't delimit the loop very well and the exit conditions can become fragmented. It's easy to get into a mess using goto like that.

At the end of the day, it's all about using constructs tastefully. Some companies/tutors don't seem to trust their employees/students to do so and come up with rules about no gotos, no ternary expressions, singletons are evil and so on.

---

