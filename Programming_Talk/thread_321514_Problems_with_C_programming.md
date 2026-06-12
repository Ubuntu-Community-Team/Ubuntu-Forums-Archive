---
title: "Problems with C programming"
date: 2006-12-19
forum: Programming Talk
---

### Post by 2pacalypse on 2006-12-19
I have 3 questions regarding to C/C++ Programming in Linux.

1) Where can i get a Decent Linux IDE for C/C++, I used Ajunta for a while but eversince its latest update i cant get to work.

2)I've been told that in order to take full advantage of the C/C++ Libraries, i need to set a path, however i dont know how to do it.... so an explanasion will be extremely helpful

3) Can i use the library DOS.H or is it protected by the Microsoft copyright? if I cant use it... is there any way to use the DOS.H commands? (clrscr, delay etc.)

---

### Post by ddtrust on 2006-12-19
> **2pacalypse said:**
> I have 3 questions regarding to C/C++ Programming in Linux.

1) Where can i get a Decent Linux IDE for C/C++, I used Ajunta for a while but eversince its latest update i cant get to work.

I personally like to use NetBeans IDE with C-/C++-plugin to develop and compile C- and C++-programs, because I can use the same software for Java programming. But I should warn you that the plugin is beta version.

> **2pacalypse said:**
> 
2)I've been told that in order to take full advantage of the C/C++ Libraries, i need to set a path, however i dont know how to do it.... so an explanasion will be extremely helpful


Don't really know about that. I've had no problems with NebBeans IDE in compiling C-programs. But you might be right.

> **2pacalypse said:**
> 
3) Can i use the library DOS.H or is it protected by the Microsoft copyright? if I cant use it... is there any way to use the DOS.H commands? (clrscr, delay etc.)

You can't use DOS.H library, it's platform specific.

---

### Post by lnostdal on 2006-12-19
> **2pacalypse said:**
> I have 3 questions regarding to C/C++ Programming in Linux.

1) Where can i get a Decent Linux IDE for C/C++, I used Ajunta for a while but eversince its latest update i cant get to work.


Use Scons + Emacs instead. :)

> **2pacalypse said:**
> 2)I've been told that in order to take full advantage of the C/C++ Libraries, i need to set a path, however i dont know how to do it.... so an explanasion will be extremely helpful

Not needed. Just install the dev-packages for stuff you need using aptitude/synaptic and your good to go.

> **2pacalypse said:**
> 
3) Can i use the library DOS.H or is it protected by the Microsoft copyright? if I cant use it... is there any way to use the DOS.H commands? (clrscr, delay etc.)

You want *ncurses*.

---

### Post by ddtrust on 2006-12-19
> **lnostdal said:**
> 
You want *ncurses*.

You're right! :D

---

### Post by 2pacalypse on 2006-12-19
> **ddtrust said:**
> But I should warn you that the plugin is beta version.


well, as long as its running with at least some decent stability and will allow me to do the compilation im ok with it ;) it is decently stable right?

> **ddtrust said:**
> 
 You want ncurses.

what is it?. and how do i use it to do command such as clrscr(); delay etc.?

---

### Post by ddtrust on 2006-12-19
> **2pacalypse said:**
> well, as long as its running with at least some decent stability and will allow me to do the compilation im ok with it ;) it is decently stable right?

I've had no problems with it whatsoever.

> **2pacalypse said:**
> 
what is it?. and how do i use it to do command such as clrscr(); delay etc.?

You should try to google sometimes.. ;)

[http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/)

---

### Post by 2pacalypse on 2006-12-19
Ok, i got NetBeans with the add on and its great ;) though i do have a slight problem... he gives me these errors on output

```

newfile.c:13:42: error: conio.h: No such file or directory
newfile.c:14:22: error: iostream.h: No such file or directory

```

though i am sure that i wrote these libraries correctly, after all the work great when I compile the code on a Windows machine

---

### Post by lnostdal on 2006-12-19
> **2pacalypse said:**
> Ok, i got NetBeans with the add on and its great ;) though i do have a slight problem... he gives me these errors on output

```

newfile.c:13:42: error: conio.h: No such file or directory
newfile.c:14:22: error: iostream.h: No such file or directory

```

though i am sure that i wrote these libraries correctly, after all the work great when I compile the code on a Windows machine

conio.h is not part of standard C++.
iostream.h was "renamed" to just iostream years ago.

---

### Post by 2pacalypse on 2006-12-19
oh ok, then how do i enable it in the NetBeans? And how come that the iostream still gives me that error even though i did it like this

```

#include <iostream>

```

---

### Post by ddtrust on 2006-12-19
> **2pacalypse said:**
> oh ok, then how do i enable it in the NetBeans? And how come that the iostream still gives me that error even though i did it like this

```

#include <iostream>

```

Hmm.. I've had no problems using iostream library.. Does it give an other errors?

---

### Post by lnostdal on 2006-12-19
> **2pacalypse said:**
> oh ok, then how do i enable it in the NetBeans? And how come that the iostream still gives me that error even though i did it like this

```

#include <iostream>

```

Not sure; is it using `gcc' instead of `g++'? Learn how to use the compiler from the terminal first(#1):

```
g++ -g -Wall program.cpp -o program
```

..now is there a way to see how "Netbeans" actually calls gcc/g++?

#1: [http://www.network-theory.co.uk/docs/gccintro/](http://www.network-theory.co.uk/docs/gccintro/) and [http://gcc.gnu.org/onlinedocs/gcc/](http://gcc.gnu.org/onlinedocs/gcc/)
...the reason why this is important is because it enables you to communicate with others. It is almost impossible to guess what's going on behind an IDE - if you cannot tell it to display its call to GCC that is.

---

### Post by 2pacalypse on 2006-12-19
heres the full log
```

Running "rm -rf build/Debug/GNU-Linux-x86/newfile.o" in /home/kronos/Application1


Clean successful. Exit value 0.

Running "make -f nbproject/Makefile-Debug.mk build/Debug/GNU-Linux-x86/newfile.o" in /home/kronos/Application1

mkdir -p build/Debug/GNU-Linux-x86
gcc    -c -g -o build/Debug/GNU-Linux-x86/newfile.o newfile.c
newfile.c:13:42: error: conio: No such file or directory
newfile.c:14:20: error: iostream: No such file or directory
newfile.c:344:8: warning: unknown escape sequence: '\040'
newfile.c:354:8: warning: unknown escape sequence '\_'
make: *** [build/Debug/GNU-Linux-x86/newfile.o] Error 1

Build failed. Exit value 2.


```

---

### Post by lnostdal on 2006-12-19
> **2pacalypse said:**
> heres the full log
```

Running "rm -rf build/Debug/GNU-Linux-x86/newfile.o" in /home/kronos/Application1


Clean successful. Exit value 0.

Running "make -f nbproject/Makefile-Debug.mk build/Debug/GNU-Linux-x86/newfile.o" in /home/kronos/Application1

mkdir -p build/Debug/GNU-Linux-x86
gcc    -c -g -o build/Debug/GNU-Linux-x86/newfile.o newfile.c
newfile.c:13:42: error: conio: No such file or directory
newfile.c:14:20: error: iostream: No such file or directory
newfile.c:344:8: warning: unknown escape sequence: '\040'
newfile.c:354:8: warning: unknown escape sequence '\_'
make: *** [build/Debug/GNU-Linux-x86/newfile.o] Error 1

Build failed. Exit value 2.


```

You're still trying to include `conio'. Also; try renaming `newfile.c' to `newfile.cpp'.

edit:
`conio.h' is an old Borland-extension; it is not standard C nor C++. For similar functionality as what was provided with `conio.h' you need a library and a set of headers called "ncurses".

---

### Post by 2pacalypse on 2006-12-19
```

Running "rm -rf build/Debug/GNU-Linux-x86/newfile.o" in /home/kronos/Application1


Clean successful. Exit value 0.

Running "make -f nbproject/Makefile-Debug.mk build/Debug/GNU-Linux-x86/newfile.o" in /home/kronos/Application1

mkdir -p build/Debug/GNU-Linux-x86
gcc    -c -g -o build/Debug/GNU-Linux-x86/newfile.o newfile.c
newfile.c:13:42: error: conio: No such file or directory
newfile.c:14:20: error: iostream: No such file or directory
newfile.c:344:8: warning: unknown escape sequence: '\040'
newfile.c:354:8: warning: unknown escape sequence '\_'
make: *** [build/Debug/GNU-Linux-x86/newfile.o] Error 1

Build failed. Exit value 2.

```
heres the output... I've looked in my Include library (/usr/include) and I cant find iostream with or without .h, and also i cant find conio both with and without .h

---

### Post by lnostdal on 2006-12-19
> **2pacalypse said:**
> ```

Running "rm -rf build/Debug/GNU-Linux-x86/newfile.o" in /home/kronos/Application1


Clean successful. Exit value 0.

Running "make -f nbproject/Makefile-Debug.mk build/Debug/GNU-Linux-x86/newfile.o" in /home/kronos/Application1

mkdir -p build/Debug/GNU-Linux-x86
gcc    -c -g -o build/Debug/GNU-Linux-x86/newfile.o newfile.c
newfile.c:13:42: error: conio: No such file or directory
newfile.c:14:20: error: iostream: No such file or directory
newfile.c:344:8: warning: unknown escape sequence: '\040'
newfile.c:354:8: warning: unknown escape sequence '\_'
make: *** [build/Debug/GNU-Linux-x86/newfile.o] Error 1

Build failed. Exit value 2.

```
heres the output... I've looked in my Include library (/usr/include) and I cant find iostream with or without .h, and also i cant find conio both with and without .h

Uhm .. yes; you're still doing exactly the same thing .....................

Check this:
```

lars@ibmr52:~$ cat blah.c 
#include <iostream>

using namespace std;

int main()
{
        cout << "Hello World!" << endl;
        return 0;
}
lars@ibmr52:~$ gcc -g -Wall blah.c -o blah
blah.c:1:20: error: iostream: No such file or directory
blah.c:3: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;namespace&#8217;
blah.c: In function &#8216;main&#8217;:
blah.c:7: error: &#8216;cout&#8217; undeclared (first use in this function)
blah.c:7: error: (Each undeclared identifier is reported only once
blah.c:7: error: for each function it appears in.)
blah.c:7: error: &#8216;endl&#8217; undeclared (first use in this function)

```

simplest way is to use g++ to compile/link c++-code:
```

lars@ibmr52:~$ g++ -g -Wall blah.c -o blah
lars@ibmr52:~$ ./blah 
Hello World!

```

..and as already stated, I believe your IDE will call g++ (instead of gcc) if you rename your file to newfile.cpp ....................

edit:
btw:

```
lars@ibmr52:~$ locate iostream
/usr/include/c++/4.1.2/backward/iostream.h
/usr/include/c++/4.1.2/iostream

```

---

### Post by ddtrust on 2006-12-19
NetBeans should call the correct compiler if you have created cc-file (c++-source file). In NetBeans try --> New.. --> C/C++-development --> C/C++-application --> Next --> Finish.

Then right click on source files folder and select new--> Main C++-file.

Then try to include the iostream, at least this works for me:

```

// 
// File:   main.cc
// Author: jk
//
// Created on 19 December 2006, 21:43
//

#include <stdlib.h>
#include <iostream.h>

using namespace std;
//
// 
//
int main(int argc, char** argv) 
{
    cout << "This works for me!";
    return (EXIT_SUCCESS);
}

```

Then save the modified main.cc and select Run-->Run Main Project.

I think the extension of the file changes the used compiler.

---

### Post by 2pacalypse on 2006-12-20
Thanks ;) it solved the iostream prob, however I do get some problems, mainly with ncurse lib... heres the output

```

kronos@kronos-desktop:~/Application1$ g++ -g -Wall 1.cpp -o 1
1.cpp:13:43: error: ncurse: No such file or directory
1.cpp:18: error: &#8216;::main&#8217; must return &#8216;int&#8217;
1.cpp: In function &#8216;int main()&#8217;:
1.cpp:39: error: &#8216;outp&#8217; was not declared in this scope
1.cpp:73: error: &#8216;delay&#8217; was not declared in this scope
1.cpp:90: error: &#8216;delay&#8217; was not declared in this scope
1.cpp:110: error: &#8216;inp&#8217; was not declared in this scope
1.cpp:121: error: &#8216;delay&#8217; was not declared in this scope
1.cpp:146: error: &#8216;delay&#8217; was not declared in this scope
1.cpp:172: error: &#8216;delay&#8217; was not declared in this scope
1.cpp:198: error: &#8216;delay&#8217; was not declared in this scope
1.cpp:344: error: unknown escape sequence: '\040'
1.cpp:354: error: unknown escape sequence '\_'
kronos@kronos-desktop:~/Application1$ 

```

I dont understand why does he give me errors with the simple line:
```

void main()

```

---

### Post by po0f on 2006-12-20
2pacalypse,

It's ncurses.h, unless you do it the C++ way of including C header files:
```
[FONT="Courier New"]// C header files still require the ".h" extension
#include <ncurses.h>

//or

// You can include C header files in C++ by prefixing header name with "c"
// and dropping the ".h" extension
#include <cncurses>
[/FONT]
```

When you go to compile the code, you need to tell g++ that you want to link your program with the ncurses library:
```
[FONT="Courier New"]$ g++ -Wall -g -o my_program my_source.cpp -lncurses[/FONT]
```

The C++ standard says that main() must return an int, that's why you are getting that error.

---

### Post by 2pacalypse on 2006-12-20
> **po0f said:**
> 
The C++ standard says that main() must return an int, that's why you are getting that error.

so what should i write in the void main() ?, I tried to put a variable which is already included in the int, but he gives me this error
```

kronos@kronos-desktop:~/Application1$ g++ -Wall -g -o 1.cpp -lncurses
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
kronos@kronos-desktop:~/Application1$ 

```
 
and pretty much blocks out the rest of the program... so what should i do?

p.s.
from some stange reason it also constantly erases the program after trying to compile.... luckily i have a back up but what is causing it to make this error?

---

### Post by po0f on 2006-12-20
2pacalypse,

```
[FONT="Courier New"]#include <ncurses.h>

int main() {
    initscr();

    printw("Hello World!");
    getch();

    endwin();

    return 0;
}[/FONT]
```

Save as myfile.cpp and compile it:
```
[FONT="Courier New"]$ g++ -Wall -g -o myprogram myfile.cpp -lncurses
$ ./myprogram[/FONT]
```
(The program will pause, press a key to terminate it.)

---

### Post by 2pacalypse on 2006-12-20
nice it works ;) ill try to do int main() too ;)

btw, what is these initscr();, endwin(); commands? will they work on windows too  (with conio or some other library)?

EDIT:

Once again, the same error
```

kronos@kronos-desktop:~/Application1$ g++ -Wall -g -o 1.cpp -lncurses/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
kronos@kronos-desktop:~/Application1$ 

```

ever with the 
```

int main	{
*rest of the program*
[code]

heres my full program, it might shed more light on the problem
[code]
// To be viewed in a 1280x1024

   ///////////////////////////////////////////////////////   //////////////////////////////////////////////////////
//* This program Has been Written by Yaniv Kfir          *//* This Program Allows the User To run All              */
//*                                                      *//* The Possible Operations on his I/O Card              */
//* This program uses the IO card fully,                 *//* From a simple LED Show, to the more complex Speakers */
//* allowing the user to choose how its operate          *//* And He can Even Run them at the same time.           */
   ////////////////////////////////////////////////////////  ///////////////////////////////////////////////////////
   
// Libraries
#include <stdio.h>
#include <stdlib.h>
#include <ncurse.h> 
#include <iostream>
// Activate if on Windows // #include <dos.h>
// Change <ncurse.h> to <conio.h> if on windows 

int main	{

int cho;
int Scho;
int a;
int b;
int x;
/*
Disabled for Maitenance
int j;
int pitch;
int duration=1500;
int cycles;
int lenght;
*/
// Start of porgram

start:
// Disabled for Maitenance
//cycles=duration/lenght;

outp(0x37a,0x03);
system("Color F9");
printf ("\n \n################################################# \n \n################################################# \n## This program has been Written By Yaniv Kfir ## \n## For the I/O Card please choose              ## \n## a component to activate                     ## \n##---------------------------------------------## \n################################################# \n## 1)LED                                       ## \n## 2)Switch's                                  ## \n## 3)Motor                                     ## \n## 4)Buzzer                                    ##  \n## 5)Speaker                                   ##  \n## 6)Mixed                                     ##  \n## 9)Notes                                     ##  \n## 0)Exit Program                              ## \n################################################# \n");
scanf("%d",&cho);
if (cho==1)
{
LEDMenu:
// LED Options
printf (" \n################################################# \n##             LED Options-Choose Option       ## \n##---------------------------------------------## \n################################################# \n## 1)Activate ALL LED's                        ## \n## 2)Deactivate ALL LED's                      ## \n## 3)Simple Running LEDs - Long Version        ## \n## 4)Simple Running LEDs - Short Version       ## \n## 0)Exit to Main Menu                         ## \n################################################# \n");
scanf("%d",&Scho);

if (Scho==1)
{
// All LED's Activate
printf("\n Activating all LED's for a duration of 10 secound,then returning back to LED submenu \n");
outp(0x378,0xFF);
sleep (10);
goto LEDMenu;
}
if (Scho==2)
{
// Deactivate All LED's
printf (" \n All LED's are now OFF,returning to submenu in 3 secounds \n ");
outp(0x378,0x00);
sleep (3);
goto LEDMenu;
}
if (Scho==3)
{
// Simple LED Run - Long Version
printf (" \n Running A simple full LED Display (256 Variations) and returning to submenu \n Estimated Time 1.25 Minutes \n");
b=0x00;
R:
outp(0x378,b);
delay (300);
b++;
if (b==0xFF)
{
goto LEDMenu;
}
else
goto R;
}
if (Scho==4)
{
// Simple LED Run - Short Version
printf (" \n Running A simple LED Display in a loop of 50 times and returning to submenu \n Estimated Time 15 Secounds \n ");
b=0x00;
for (a=0;a<50;a++);
{
outp(0x378,b);
delay (300);
b++;
}
goto LEDMenu;
}
if (Scho==0)
{
goto start;
}
else;
{
printf (" \n Error #1: Bad Input, reverting back to previous option \n ");
goto LEDMenu;
}
}
if (cho==2)
{
SWMenu:
// Switch's
printf ("\n ################################################# \n## Switcher's Features-Patch combination for effect ## \n##---------------------------------------------## \n################################################# \n## Upper Switch -> Run LEDs                    ## \n## Middle Switch->Start Motor                  ## \n## Lower Switch->Start Buzzer                  ## \n## to turn off, reset the switches and press 0 ## \n################################################# \n");
x=inp(0x379);
x=x&07;
if (x==0x01)
{
outp (0x37A,0x03); // Shutting down all other components
for (a=1;a>0;a++)
{
b=0x00;
{
P:
outp(0x378,b);
delay (300);
b++;
}
if (b==0xFF)
{
b=0x00;
goto P;
}
else
goto R;
}
if (x==0x02)
{
outp(0x378,0x00);
outp (0x37a,0x02);
}
if (x==0x03)
{
outp(0x37a,0x02);
for (a=1;a>0;a++)
{
b=0x00;
{
O:
outp(0x378,b);
delay (300);
b++;
}
}
if (b==0xFF)
{
b=0x00;
goto O;
}
else
goto R;
}
if (x==0x04)
{
outp(0x378,0x00);
outp (0x37a,0x07);
}
if (x==0x05)
{
outp (0x37a,0x07);
for (a=1;a>0;a++)
{
V:
b=0x00;
XC:
outp (0x378,b);
delay (300);
b++;
if (b==0xFF)
{
goto V;
}
else
{
goto XC;
}
}
}
if (x==0x06)
{
outp (0x37A,03); // Shutting down LEDs
outp(0x37a,0x06);
}
if (x==0x07)
{
outp(0x37a,0x06);
for (a=1;a>0;a++)
{
b=0x00;
{
Y:
outp(0x378,b);
delay (300);
b++;
}
}
if (b==0xFF)
{
b=0x00;
goto Y;
}
else
goto Y;
}
if (x==0x00)
{
scanf("%d",&Scho);
}
if (Scho==0)
{
goto start;
}
else
{
printf (" \n Error #1: Bad Input, reverting back to previous option \n");
goto SWMenu;
}
}
if (cho==3)
{
MotorMenu:
printf (" \n################################################# \n##            MOTOR Options-Choose Option      ## \n##---------------------------------------------## \n################################################# \n## 1)Turn Motor ON                             ## \n## 2)Turn Motor OFF                            ## \n## 0)Exit to Main Menu                         ## \n################################################# \n");
scanf("%d",&Scho);
if (Scho==1)
{
outp(0x37a,0x07);
goto MotorMenu;
}
if (Scho==2)
{
outp(0x37a,0x03);
goto MotorMenu;
}
if (Scho==0)
{
goto start;
}
else
{
printf (" \n Error #1: Bad Input, reverting back to previous option \n ");
goto MotorMenu;
}
}
if (cho==4)
{
BuzzMenu:
// Start of Buzzer Program
printf(" \n################################################# \n##           Buzzer Options-Choose Option      ## \n##---------------------------------------------## \n################################################# \n## 1)Turn Buzzer ON                            ## \n## 2)Turn Buzzer OFF                           ## \n## 0)Exit to Main Menu                         ## \n#################################################");
if (Scho==1)
{
// Running Buzzer
outp(0x37a,0x07);
goto BuzzMenu;
}
if (Scho==2)
{
outp(0x37a,0x03);
goto BuzzMenu;
}
if (Scho==0)
{
goto start;
}
else;
{
printf("Error #1: Bad Input, reverting back to previous option");
goto BuzzMenu;
}
if (cho==5)
{
// Speaker Options
SpkMenu:
printf (" \n################################################# \n##           Speaker Options-Choose Option      ## \n##---------------------------------------------## \n################################################# \n## 1)Turn Speaker ON                           ## \n## 2)Turn Speaker OFF                          ## \n## 3)Play Yanatan Ha Katan                   ## \n 0)Exit to Main Menu                         ## \n#################################################");
if (Scho==1)
{
outp(0x37a,0x01);
goto SpkMenu;
}
if (Scho==2)
{
outp(0x37a,0x03);
goto SpkMenu;
}
if (Scho==3)
{
printf (" \n Disabled for matinenance \n");
/*
outp(0x37a,0x01);
for (j=1;j<=lenght*500;j++)
outp(0x37a,0x03);
for (j=1;j<=lenght*500;j++)
}
for (pitch=14;pitch<=28;pitch+=2)
note (pitch, duration);
sleep (1);
duration=2000
note(20,duration);
note(24, duration); note(24, duration);
note(22, duration); note(26, duration); note(26, duration);
for (pitch=28;pitch>=20;pitch-=2)
note(20, duration) note(20, duration);
*/
}
}
}    
}
if (cho==6)
{
printf ("\n Under Construction");
goto start;
}
if (cho==9)
{
// General Information
printf (" \n ################################################# \n## Author: Yaniv Kfir                          ##     \n## Date: Wendsday November 8th 2006            ## \n################################################# \n \n################################################# \n##                 Legal Stuff                 ## \n##---------------------------------------------## \n################################################# \n This program was created by Yaniv Kfir For its own personal use \n copying this program without the writers premission is ILLEGAL \n By Internation laws \n This program comes with NO Warrenty or support \n################################################# \n \n################################################# \n##                Writer Notes                 ## \n##---------------------------------------------## \n################################################# \nThis program was created for the I/O Card by Yaniv Kfir \nIn order allows preforming features on the IO Card \nsuch as running LED's or running the Motor \n");
printf ("\n \n ################################################# \n \n################################################# \n##             Technical information           ## \n##---------------------------------------------## \n################################################# \n## Current Version 1.0                         ## \n## Created/Compiled On:                        ## \n##GNU/Linux Ubuntu Dapper Drake LTS (6.06)&Zenwalk## \n## Using GCC 4.0 with Kernel 2.6.18.2 ###\n And Also By Window$ XP SP2 Using Borland C          ## \n## Status: Untested                            ## \n################################################# \n");
F:
printf ("\n press 0 to go to Main Menu \n");
scanf("%d",&Scho);
if (Scho==0)
{
goto start;
}
else
{
printf (" \n Error #1: Bad Input, reverting back to previous option \n");
goto F;
}
}
if (cho==0)
{

printf(" 888      ''' 888 8e  8888 8888  Y8b Y8Y    ,mMMMMm_           \n");
printf(" 888      888 888 88b 8888 8888   Y8b Y    ,MMMMMQmMg          \n");
printf(" 888  ,d  888 888 888 Y888 888P  e Y8b     Mf^TMf'$MM          \n");
printf(" 888,d88  888 888 888  '88 88'  d8b Y8b    4,tI& Q MM          \n");
printf("                                           jW^ ' 'jMM;         \n");
printf("   ___________________________             MMg-mMM QgM,        \n");
printf("  /                           \           j@        MMM_       \n");
printf("  | Join the Open Source       |        ,M@ _       'MMMM.     \n");
printf("  |                            |       ,MM           'MMMM.    \n");
printf("  | Revolution, Get Linux now  |      .MQ             MMMMM    \n");
printf("  |                            |      OMf             'MMMM    \n");
printf("  |           From:            |      MM(             jQQQM    \n");
printf("  |                            |   ywd'  M            MMMMQ,   \n");
printf("  |   http://www.tuxcds.com    |  ]       MM         p'''^ ',  \n");
printf("  |            Or              |  jf               Q@N      _@ \n");
printf("  |   http://www.linux.org     |  4mQg__   jMM  MMMMNg  _y@''  \n");
printf("  \____________________________/     '''MWW@'        'MWWP'    \n");system ("PAUSE");
}
if (cho==7)
{
printf (" \n Error #1: Bad Input, reverting back to previous option \n");
goto start;
}
}
  /////////////////////////////////////////    //////////////////////////
/* End Of Program                          *//* Author:                  */
/*                                         *//*                          */
/* I Hope You Enjoyed Using This Program   *//*         Yaniv            */
/*                                         *//*                 Kfir     */
/*                                         *//*                          */
  /////////////////////////////////////////    //////////////////////////


```

---

### Post by yabbadabbadont on 2006-12-20
> **2pacalypse said:**
> nice it works ;) ill try to do int main() too ;)

btw, what is these initscr();, endwin(); commands? will they work on windows too  (with conio or some other library)?

Those are Curses (or ncurses in this case) commands.  I believe that ncurses has been ported to Windows, so it should work as long as you have the correct libraries installed into your development environment there.

---

### Post by po0f on 2006-12-20
2pacalypse,

initscr(), printw(), getch(), and endwin() are ncurses commands.  They will not work on Windows without getting MinGW and the proper libraries installed.  (I don't do any development on Windows/MinGW so you'll have to ask someone else about that.)

---

### Post by po0f on 2006-12-20
2pacalypse,

Is that what the code looks like (is it actually formatted that way)?  A couple of indents here and there go a long way to help keep the code readable.

It should be "int main**()** {", not "int main {".

---

### Post by 2pacalypse on 2006-12-20
it still gives the same error, both with and without the (), and the code is orginzed like that, but in the gedit it looks much more orginized, especially the drawings (with letters and signs)

---

