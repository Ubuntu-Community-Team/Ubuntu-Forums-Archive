---
title: "Can`t write a simple C program"
date: 2014-04-10
forum: Programming Talk
---

### Post by spacerocket on 2014-04-10
Hello!

Ok. First step. I go to text editor and write: 

#include <stdio.h>

void main()
{
    printf("\nHello World\n");
}

Then I save it in **my documents** with the name hello.c

Then I go to terminal window and type:

gcc Documents/hello.c (gcc hello.c does not work, I specified the full path) -> nothing

The result is that the characters `` Hello World'' are printed out, preceded by an empty line. Not for me when I type hello.c -> command not found. I missed something?

---

### Post by slickymaster on 2014-04-10
Moved to Programming Talk.

---

### Post by steeldriver on 2014-04-10
The command

```

gcc Documents/hello.c

```

compiles (and links) the source code file **hello.c from the documents directory** and creates an executable file called **a.out in your current directory**. If you get no error messages that means the command completed successfully. To execute the program file, you would type

```

./a.out

```

If you want the executable output file to have a more memorable name, you can specify that on the gcc command line using the -o flag e.g.

```

gcc **-o hello** Documents/hello.c

```

You can then execute the program as

```

./hello

```

FWIW I recommend that you get in the habit of adding at least one more flag on the gcc command line: -Wall (which turns on some compiler warnings):

```

gcc **-Wall** -o hello Documents/hello.c

```

---

### Post by spacerocket on 2014-04-10
Thanks! Very instructive. Now I moved to part 2 **Let`s Compute**     [http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/c_tutorial.html](http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/c_tutorial.html)

I copied this to text editor:

#include < stdio.h>
#include < math.h>

void main()
{
    int    angle_degree;
    double angle_radian, pi, value;

                    /* Print a header */
    printf ("\nCompute a table of the sine function\n\n");

                    /* obtain pi once for all */
                    /* or just use pi = M_PI, where
                       M_PI is defined in math.h     */
    pi = 4.0*atan(1.0);
    printf ( " Value of PI = %f \n\n", pi );

    printf ( " angle     Sine \n" );

    angle_degree=0;            /* initial angle value          */
                    /* scan over angle          */

    while (  angle_degree <= 360 )    /* loop until angle_degree > 360 */
    {
       angle_radian = pi * angle_degree/180.0 ;
       value = sin(angle_radian);
       printf ( " %3d      %f \n ", angle_degree, value );

       angle_degree = angle_degree + 10; /* increment the loop index     */
    }
}

and saved as **sine.c** 

Then I went to terminal window: 

gcc Documents/sine.c -lm
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 0 has invalid symbol index 11
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 1 has invalid symbol index 12
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 2 has invalid symbol index 2
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 3 has invalid symbol index 2
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 4 has invalid symbol index 11
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 5 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 6 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 7 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 8 has invalid symbol index 12
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 9 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 10 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 11 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 12 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 13 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 14 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 15 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 16 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 17 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 18 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 19 has invalid symbol index 21
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_line): relocation 0 has invalid symbol index 2
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../x86_64-linux-gnu/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: error: ld returned 1 exit status

[COLOR=#ff0000]Now there is some error I can`t identify[/COLOR]. I think I need to understand this tutorial completely to be able to write a board representation for my chess engine.

---

### Post by Warren Hill on 2014-04-10
Try changing

```
gcc Documents/sine.c -lm
```

To 

```
gcc -lm Documents/sine.c
```

Does this help?

gcc links the objects in order so that since code in sine.o the object file created by sine.c relies on the math library it has to be linked first.

I wouldn't of expected that error message though.

I'll try compiling your code later if you are still having problems. To try and help further.

---

### Post by R33D3M33R on 2014-04-10
Why don't you use **int main()** and **return 0;** if everything is ok and **return 1;** if something goes wrong?

---

### Post by steeldriver on 2014-04-10
First of all, the C code example that you linked to appears to have a couple of typos that I mentioned [in your previous thread]("http://ubuntuforums.org/showthread.php?t=2215649&page=3")

```

#include < stdio.h>
#include < math.h>

```

(note the spaces before the header file names). However that should result in a different compiler error:

```

$ gcc Documents/sine.c -lm
Documents/sine.c:9:20: fatal error:  stdio.h: No such file or directory
 #include < stdio.h>
                    ^
compilation terminated.

```

Let's assumed you fixed those. Warren Hill brings up a good point - however in this case the original order is correct, I think

```

$ gcc -lm Documents/sine.c
/tmp/cclPYt3F.o: In function `main':
sine.c:(.text+0x78): undefined reference to `sin'
collect2: error: ld returned 1 exit status

```

whereas

```

$ gcc Documents/sine.c -lm
$ 

```

executes OK. I'm more inclined to believe it's something messed up in your build environment, but I can't figure out what.

---

### Post by spacerocket on 2014-04-10
Ok thanks steeldriver and others

Now seems to work:

 user@user-MS-7817:~$ gcc Documents/sine.c -lm
user@user-MS-7817:~$

./a.out

Compute a table of the sine function

 Value of PI = 3.141593 

 angle Sine 
   0 0.000000 
   10 0.173648 
   20 0.342020 
   30 0.500000 
   40 0.642788 
   50 0.766044 
   60 0.866025 
   70 0.939693 
   80 0.984808 
   90 1.000000 
  100 0.984808 
  110 0.939693 
  120 0.866025 
  130 0.766044 
  140 0.642788 
  150 0.500000 
  160 0.342020 
  170 0.173648 
  180 0.000000 
  190 -0.173648 
  200 -0.342020 
  210 -0.500000 
  220 -0.642788 
  230 -0.766044 
  240 -0.866025 
  250 -0.939693 
  260 -0.984808 
  270 -1.000000 
  280 -0.984808 
  290 -0.939693 
  300 -0.866025 
  310 -0.766044 
  320 -0.642788 
  330 -0.500000 
  340 -0.342020 
  350 -0.173648 
  360 -0.000000 

Now how do I know each time to what program ./a.out refers? Possible solution: maybe change the name like you told earlier with o-flag

So this is complete table of sine function?

---

### Post by steeldriver on 2014-04-10
It may be good practice to define main to return an int, but your code should compile and run as-is

Let's be certain that your .c file didn't get corrupted / saved in a different place from where you think - from the same directory where you ran the gcc command, please run

```
cat Documents/sine.c
```

and check the output - if you want to copy and paste it here please put it inside [CODE] tags

---

### Post by Warren Hill on 2014-04-10
Correction

I've compiled this program

```
#include <stdio.h>
#include <math.h>

void main()
    {
    int angle_degree;
    double angle_radian, pi, value;

    /* Print a header */
    printf ("\nCompute a table of the sine function\n\n");

    /* obtain pi once for all */
    /* or just use pi = M_PI, where
        M_PI is defined in math.h */
    pi = 4.0*atan(1.0);
    printf ( " Value of PI = %f \n\n", pi );

    printf ( " angle Sine \n" );

    angle_degree=0; /* initial angle value */
    /* scan over angle */

    while ( angle_degree <= 360 ) /* loop until angle_degree > 360 */
    {
        angle_radian = pi * angle_degree/180.0 ;
        value = sin(angle_radian);
        printf ( " %3d %f \n ", angle_degree, value );

        angle_degree = angle_degree + 10; /* increment the loop index */
    }
}
```


And compiled and tested thus

```
warren@dell:~/test$ gcc -o sine  sine.c -lm
warren@dell:~/test$ ./sine

Compute a table of the sine function

 Value of PI = 3.141593 

 angle Sine 
   0 0.000000 
   10 0.173648 
   20 0.342020 
   30 0.500000 
   40 0.642788 
   50 0.766044 
   60 0.866025 
   70 0.939693 
   80 0.984808 
   90 1.000000 
  100 0.984808 
  110 0.939693 
  120 0.866025 
  130 0.766044 
  140 0.642788 
  150 0.500000 
  160 0.342020 
  170 0.173648 
  180 0.000000 
  190 -0.173648 
  200 -0.342020 
  210 -0.500000 
  220 -0.642788 
  230 -0.766044 
  240 -0.866025 
  250 -0.939693 
  260 -0.984808 
  270 -1.000000 
  280 -0.984808 
  290 -0.939693 
  300 -0.866025 
  310 -0.766044 
  320 -0.642788 
  330 -0.500000 
  340 -0.342020 
  350 -0.173648 
  360 -0.000000 
 warren@dell:~/test$ 

```

This suggests your problem is that you don't have the math library installed how did you install gcc?

I'd suggest you try

```
sudo apt-get install build-essential
```

This should bring in all the tools necessary and try again.  Let me know how you get on.

---

### Post by spacerocket on 2014-04-10
I already have the build-essential....    
> cat Documents/sine.c
#include <stdio.h>
#include <math.h>

void main()
{
int angle_degree;
double angle_radian, pi, value;

/* Print a header */
printf ("\nCompute a table of the sine function\n\n");

/* obtain pi once for all */
/* or just use pi = M_PI, where
M_PI is defined in math.h */
pi = 4.0*atan(1.0);
printf ( " Value of PI = %f \n\n", pi );

printf ( " angle Sine \n" );

angle_degree=0; /* initial angle value */
/* scan over angle */

while ( angle_degree <= 360 ) /* loop until angle_degree > 360 */
{
angle_radian = pi * angle_degree/180.0 ;
value = sin(angle_radian);
printf ( " %3d %f \n ", angle_degree, value );

angle_degree = angle_degree + 10; /* increment the loop index */
}
}



"It may be good practice to define main to return an int"  Sorry but I  don`t understand. What is the fuction of Main? Int is integrer variable?  What does that do?

 [COLOR=#ff0000]"The void preceeding ``main'' indicates that main is of ``void'' type--that is, it has *no* type associated with it, meaning that it cannot return a result on execution."  [/COLOR][COLOR=#000000][/COLOR]I don`t understand this statement.

---

### Post by Warren Hill on 2014-04-11
Strictly speaking main should return  an **int**
The function prototype for main is

```
int main(int argc, char **argv);
```

Where **argc** is the number of arguments passed to the program and **argv **is an array containing those arguments.

You often also see

```
int main(void);
```

Indicating that this particular program does not care about any command line arguments (or parameters)

The convention is that a program returns 0 to say the program worked without error and another value if not.

The point of this is that the value is passed back to the OS and other programs or scripts can use the return  value to decide what to do next.

---

### Post by spacerocket on 2014-04-11
OS= Original Script? Next moving to part 3#

Arrays are used to build bitboards?

[URL="http://chess.stackexchange.com/questions/2831/how-to-represent-chess-state-with-a-bitboard"]http://chess.stackexchange.com/questions/2831/how-to-represent-chess-state-with-a-bitboard

[COLOR=#000000]Though C# IS NOT what we want... [/COLOR]
[/URL]

---

### Post by Warren Hill on 2014-04-11
By OS I meant operating system.  What ever called the program it could be a script but not necessarily

---

### Post by spacerocket on 2014-04-11
[URL="http://chessprogramming.wikispaces.com/Array"]http://chessprogramming.wikispaces.com/Array

[COLOR=#000000]Myabe first step: 

[http://chessprogramming.wikispaces.com/Bitboard+Board-Definition](http://chessprogramming.wikispaces.com/Bitboard+Board-Definition)

My C-skills allow to move to this part[/COLOR]
[/URL]

---

### Post by 23dornot23d on 2014-04-11
You might be interested in looking at python ...... 

The code is at least easier to follow ... have a look here
[http://www.pygame.org/project-Python+Chess-1099-.html](http://www.pygame.org/project-Python+Chess-1099-.html)

Then here

The source and a working game are here too [http://yakinikuman.wordpress.com/python-chess/](http://yakinikuman.wordpress.com/python-chess/)

I have just tried it this minute to make sure it is working ..... the requirement is that you have python which is usually already pre installed
and then the only other requirement on my own system was to install python-pygame

**sudo apt-get install python-pygame**

After downloading into /Downloads/ the only command needed then is

/Downloads/PythonChess$ **python PythonChessMain.py**

[IMG]http://i.minus.com/ibn9EXYeHgl00J.png[/IMG]

Not to put you off C ........ you can still carry on - with your quest but it may be worth a look to see how
to start setting things out ........

C takes some understanding and lots of work even just to get a foot in the door
so to speak ........... reason I say this is because I have spent a lot of time and effort with C and got very
small limited results virtually from running other peoples examples and code - but understanding all the background 
behind it is another matter - have plenty of books to reference too in C ..... many are online now - but I prefer
having a paperback alongside me when working through examples and checking off each thing as I go along.


At least with Python you may get some early visible results and code that is
in a form that is more readable ......... at least all the source code is available on that site above too .........

Reasoning for using C ......... speed of execution of programs ........ but not for ease of writing or readability IMHO

---

### Post by spacerocket on 2014-04-11
Hello!

Hi 23dornot23d. I need to look at python at some point. Now however my project on this tutorial: [http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/c_tutorial.html](http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/c_tutorial.html)    is **incomplete**.  I was just moving to part 3: Loops when I got sidetracked to bitboards. I need to carry on.

2) Just a little question: I installed some package with this command: 

> sudo apt-get install texi2html texinfo xserver-xorg-dev libxt-dev xaw3dg xaw3dg-dev libxaw7 libxaw7-dev fairymax




....And now I`m having fairymax engine playing in xboard. Do you know how I can uninstall it?

---

### Post by trent.josephsen on 2014-04-11
Have you programmed before? C is a challenging language; you cannot go from "hello, world" to making a chess AI in a couple of days. It would be difficult even for someone who was already an expert in some other language. If you want to get started somewhat faster, I agree with 23dornot23d that Python might be a good choice.

However, assuming you intend to learn C, I recommend that you not rely solely on online tutorials, and in particular I suggest you avoid that one. It contains a number of simple-minded errors and bad practices, as one might expect from a physics department dabbling in programming. There are better resources elsewhere, although I haven't really been happy with any online tutorial I've seen; you should really buy a book. I'm afraid I can't recommend a C book for new programmers, and threads about books tend to get derailed easily, but if you search the forums you'll probably find some useful advice -- if not, always feel free to post a new question.

---

### Post by steeldriver on 2014-04-11
Amen - from a physicist who dabbles in programming :)

---

### Post by 23dornot23d on 2014-04-11
I also put fairymax in - it should just be a case of

[B]sudo apt-get remove fairymax

Just a confirmation here that removing it is ok - just done it on mine and it will take you back to
how it was before with a warning that fairymax engine is not available .......

But if you look on the top of the menu line there is a option for changing engines should you require to
do so ....... 

[IMG]http://i.minus.com/iZzcetfDzkvri.png[/IMG]



Herbert Schildt is the Author of one of my C books that is quite easy to follow - and there were
some online versions ..... as I did a search on them - The Complete Reference is one that is informative
and easy to take in ....... but as said there will be many others and everyone will have their own
preference . Often depends on if the Author speaks or explains in ways that suit your own way
of thinking ...... ( C++ Program Design is another that explains some concepts and has many examples too )
can get pulled across and around all over the place with programming though ...... but when I have bought
books in the past - I tend to get the ones with the included CDs and examples.

Thing is nowadays you can search online and many of the examples and pdfs exist that you can simply look
up ........ and then start to work through ....... 

A course may be better though .... best advice I think I can give with my limited experience - but you are in
the right place here to get expert advice on the matter ...... maybe best to keep plugging away and follow
a road without veering off it too much ........ like branches on a tree ( I think I followed all of them - but it 
tends to lead you to know a little about everything ) jack of all trades master of none as my Dad used to say.

Hope something there helps .
[/B]

---

### Post by spacerocket on 2014-04-11
**H**ello!

I have now Pythonchess in downloads (filefolder). To run it, I need [https://www.python.org/download/](https://www.python.org/download/)  and [http://www.pygame.org/download.shtml](http://www.pygame.org/download.shtml)  Possibly. 

Then run **python PythonChessMain.py **maybe.

python PythonChessMain.py
python: can't open file 'PythonChessMain.py': [Errno 2] No such file or directory

---

### Post by 23dornot23d on 2014-04-11
Python will already be installed on your system - so do not go changing that .....

The file you downloaded is a zip file ........

This command needs doing too do not know if you have already done it following post #16
but that explained python is already installed so the only thing extra you really need is pygame
which will install with this command below.

> 
**sudo apt-get install python-pygame**


do you have the PythonChess_v0.7.zip in your downloads folder ....

You first have to right click the zip file to extract it from its archive to a folder - * (should be an option  >>>  Extract Archive to here) .....

Then you need to **go in to a terminal** and type in

**cd /Downloads/PythonChess**

then you can use the command .........

**python PythonChessMain.py**

and it should run ......

---

### Post by spacerocket on 2014-04-11
Now I installed python-tk and works but I have to admit when seeing the chessboard-**bad quality**!

---

### Post by Warren Hill on 2014-04-11
Python should be on your system already

Check with
```
python --version
```

If you get something like

```
Python 2.7.3
```

It's installed

from a terminal **cd** to the directory where you have installed it

To check you are in the correct directory type 

```
ls
```

and you should see something like this

```
warren@dell:~/test/PythonChess$ ls
ChessAI.py           ChessGUI_text.pyc    PythonChessAIStats.py
ChessAI.pyc          ChessPlayer.py       PythonChessMain.py
ChessBoard.py        ChessPlayer.pyc      PythonChessMain.py~
ChessBoard.pyc       ChessRules.py        random_seeds_100.txt
ChessGameParams.py   ChessRules.pyc       results.txt
ChessGameParams.pyc  gpl.txt              ScrollingTextBox.py
ChessGUI_pygame.py   images               ScrollingTextBox.pyc
ChessGUI_pygame.pyc  pygame2exe_Chess.py  Thumbs.db
ChessGUI_text.py     PySetup.py
warren@dell:~/test/PythonChess$ 

```

Now run the program

```
python PythonChessMain.py
```

and it should just work.  If not then then it probably means **pygame **has not been installed.  If this is the case try

```
sudo apt-get install python-pygame
```

and run it again

---

### Post by 23dornot23d on 2014-04-11
All the images are in /PythonChess/images/

Check them out - you can always replace things like this with your own ......... or from another game ......... 
but the quality looks ok on my system ........ maybe show us a screen shot ( it could be some other issue )

Its a base system to look at and to improve then possibly ....... just thought it might be a help to you .

As I said before .... do not let it stop you on your quest .

---

### Post by spacerocket on 2014-04-11
Yep!

How about going through [http://www.cplusplus.com/doc/tutorial/variables/](http://www.cplusplus.com/doc/tutorial/variables/)  Basics of C++, Program Structure and compound datatypes with your and my assistance!

I want to learn something concrete now and yes, I should buy C/C++ book. I even found one: [http://www.cprogramming.com/c++book/?inl=sb](http://www.cprogramming.com/c++book/?inl=sb)

I have pythonchess installed but I just can`t understand the program compleletely... Sorry. Maybe I should have a look some time. 

I think the above is a good tutorial.

We can always continue the pythin project.

We can continue the python project after that **100% **. I always have it installed.

---

### Post by 23dornot23d on 2014-04-11
( ensure you have g++ installed )
[B]sudo apt-get install g++

By the way this is C++ now .... not C ..... for anyone looking at this thread.[/B]


Have you got the first program into a file .......

> 
// operating with variables

#include <iostream>
using namespace std;

int main ()
{
  // declaring variables:
  int a, b;
  int result;

  // process:
  a = 5;
  b = 2;
  a = a + 1;
  result = a - b;

  // print out the result:
  cout << result;

  // terminate the program:
  return 0;
}


gedit var1.c

and paste in the above text ........

_____________________________

Then run ........ to make sure it works .......

g++ -o var var1.c

Will produce these files

> 

keith@keith-K53SV:~/c$ g++ -o var var1.c 

keith@keith-K53SV:~/c$ ls



var  var1.c  var1.c~

This line will run it ./var
keith@keith-K53SV:~/c$ ./var

Will then return 4

as the answer .........

____________________________________
Simple explanation of Integers and Real Numbers
[http://www.eskimo.com/~scs/cclass/mathintro/sx1.html](http://www.eskimo.com/~scs/cclass/mathintro/sx1.html)
____________________________________
( ensure you have g++ installed )
[B]sudo apt-get install g++
____________________________________
For information on g++
[http://homepages.gac.edu/~mc38/2001J/documentation/g++.html](http://homepages.gac.edu/~mc38/2001J/documentation/g++.html)
[http://courses.cs.washington.edu/courses/cse373/99au/unix/g++.html](http://courses.cs.washington.edu/courses/cse373/99au/unix/g++.html)
[/B]

---

### Post by spacerocket on 2014-04-11
user@user-MS-7817:~$ g++ -o var Documents/var1.c
user@user-MS-7817:~$ ./var
4user@user-MS-7817:~$ 

Perfect!

[h=3]Initialization of variables[/h] When the variables in the example above are declared, they have an  undetermined value until they are assigned a value for the first time.  But it is possible for a variable to have a specific value from the  moment it is declared. This is called the *initialization* of the variable.

In C++, there are three ways to initialize variables. They are all  equivalent and are reminiscent of the evolution of the language over the  years:

The first one, known as *c-like initialization* (because it is  inherited from the C language), consists of appending an equal sign  followed by the value to which the variable is initialized:

type identifier = initial_value; 
For example, to declare a variable of type int called x and initialize it to a value of zero from the same moment it is declared, we can write:

[TABLE="class: snippet"]
[TR]
[TD="class: rownum"] [/TD]
 [TD="class: source"]int x = 0;[/TD]
[/TR]
[/TABLE]

 

A second method, known as *constructor initialization* (introduced by the C++ language), encloses the initial value between parentheses (()):

type identifier (initial_value); 
For example:

[TABLE="class: snippet"]
[TR]
[TD="class: rownum"] [/TD]
 [TD="class: source"]int x (0);[/TD]
[/TR]
[/TABLE]

 

Finally, a third method, known as *uniform initialization*, similar to the above, but using curly braces ({}) instead of parentheses (this was introduced by the revision of the C++ standard, in 2011):

type identifier {initial_value}; 
For example:

[TABLE="class: snippet"]
[TR]
[TD="class: rownum"] [/TD]
 [TD="class: source"]int x {0}; [/TD]
[/TR]
[/TABLE]

[COLOR=#ff0000]I don`t understand![/COLOR]  Maybe johanes could help us: [http://www3.nd.edu/~johanes/parrot.html](http://www3.nd.edu/~johanes/parrot.html)  ask what he thinks about this. He`s at least professional, like you. Maybe I ask him. Reply wouldn`t be guaranted though....

---

### Post by 23dornot23d on 2014-04-11
You need to work through the examples - slowly ........

and understand why different variables have different names ...... the terminology will then help towards understanding
what the errors mean when you get them back.

I had a quick download of parrot .... will have a look see what it does first ....... the makefile needs the line uncommenting
for g++ and the others need # infront of them ....... but then there is a error with the next part ........

> 
keith@keith-K53SV:~/parrot$ make
gcc         -Wall -prof_use -g -O3 -DLINUX -D_REENTRANT -DHANDICAPPED_OPPONENT -c parrot.c
gcc: error: unrecognized command line option &#8216;-prof_use&#8217;
make: *** [parrot.o] Error 1



What is it meant to do - I see it goes into your xchess program as an addition ......... dumbs the game down

Well I got it to make it .... but not sure what it does ..... yet ......

The alterations to the Makefile are here .... but will it work now ... and how does it work ?

```

# The C compiler
CC = **[COLOR=#ff0000]g++[/COLOR]**        # GNU C Compiler
#CC = icc        # free Intel C Compiler for Linux
#CXX= icpc       # free Intel C++ Compiler for Linux


# flags for Condor
#CFLAGS = -Wall -g -O3 -DLINUX 

# flags for FICS
#CFLAGS = -Wall -prof_genx -g -O3 -DLINUX -D_REENTRANT
#CFLAGS = -Wall -prof_use -g -O3 -DLINUX -D_REENTRANT

# flags for debugging
#CFLAGS = -Wall -g -O3 -DLINUX -D_REENTRANT -DDEBUG -DVERIFY

# flags for handimatch
#CFLAGS = -Wall -prof_genx -g -O3 -DLINUX -D_REENTRANT -DHANDICAPPED_OPPONENT
#CFLAGS = -Wall -prof_use -g -O3 -DLINUX -D_REENTRANT -DHANDICAPPED_OPPONENT

# flags for tournament
#CFLAGS = -Wall -prof_genx -g -O3 -DLINUX -D_REENTRANT -DTOURNAMENT
#CFLAGS = -Wall -prof_use -g -O3 -DLINUX -D_REENTRANT -DTOURNAMENT

# flags for tree dump
#CFLAGS = -Wall -g -O3 -DLINUX -DVERIFY -DTREEDUMP


LINT = splint
LFLAGS = -redef -boolops -retvalother -predboolint -compdef -usedef \
    -unreachable -predboolothers -fixedformalarray -warnposix -nullpass \
    -formattype -retvalint +charint -realcompare -bufferoverflowhigh \
    -duplicatequals -temptrans -unqualifiedtrans -mayaliasunique \
    -exportlocal +matchanyintegral +relaxtypes +boolint -unsignedcompare \
    -DLINUX -DVERIFY

# Include and object files
INC = aliases.h values.h constants.h eval.h prototypes.h variables.h
SOURCE = main.c attack.c book.c command.c egtbprobe.c eval.c hash.c init.c \
    move.c pmRandom.c search.c util.c
OBJ = parrot.o egtb.o


# The programs
PROGRAMS = parrot
all: $(PROGRAMS)

parrot: $(OBJ)
#    $(CC) $(CFLAGS) -o parrot $(OBJ) libstdc++.so.6 -lpthread
**[COLOR=#ff0000]    $(CC) $(CFLAGS) -o parrot $(OBJ) -lstdc++ -lpthread[/COLOR]**

# The source
parrot.c: $(SOURCE)
    @/bin/cat $(SOURCE) > parrot.c

parrot.h: $(INC)
    @/bin/cat $(INC) > parrot.h


# The objects
parrot.o: parrot.c parrot.h
    $(CC) $(CFLAGS) -c parrot.c

parrot.s: parrot.c parrot.h
    $(CC) $(CFLAGS) -S parrot.c

egtb.o: egtb.cpp tbdecode.h
    $(CXX) $(CFLAGS) -c egtb.cpp


# utities
lint:
    $(LINT) $(LFLAGS) parrot.c

clean:
    -rm -f $(PROGRAMS) parrot.c parrot.h *.o *~
    cp -p egtb.o.icc egtb.o

```

My only alterations are in red ..... but one of those CFLags Lines probably needs uncommenting too ..... but still not sure which ....

Ok I now see what you are trying to do .......

 I let it play automatically on FICS unattended.  Pretty soon parrot got up to about 2400 blitz rating on FICS.

[http://en.wikipedia.org/wiki/Fast_chess](http://en.wikipedia.org/wiki/Fast_chess)

---

### Post by spacerocket on 2014-04-11
Ahh, If I understand you right  you want to see how parrot is build in C++ to get more knowledge... Makefile is propably then correct...

[COLOR=#008000]I also Downloaded parrot`s source code and can access the makefile. Makefile is obviously needed for the program. Does the makefile include also the board representation? (arrays,bitboards)

What is **CFlags Line**? What is the mission of [/COLOR]
**[COLOR=#ff0000]$(CC) $(CFLAGS) -o parrot $(OBJ) -lstdc++ -lpthread [/COLOR]**[COLOR=#000000]

in the program?
[/COLOR]

---

### Post by 23dornot23d on 2014-04-11
Just interested in what it does now and how it works ....... this is also in the README

> 
To compile, just type
        make

To play parrot, put sqvalue and parrot.cfg files in the current directory.
On command line mode:
        ./parrot
With xboard interface, use "./parrot xboard".  Look at xboard man page.  
For example,
        xboard -mps 40 -tc 5 -fcp "./parrot xboard"
parrot supports most xboard commands (look at command.c).  

To play parrot on FICS, you have to compile xboard with zippy support, then do 
something like
        xboard -debug -xdrag -xanimate -xautoraise -xexit -xpopup -zp \
          -ics -autocomm -autoflag -icsport 5000 -icshost 64.71.131.140 \
            -telnet -telnetProgram timeseal -icslogon .your_fic_rc \
              -fcp "./parrot xboard" -size small -sgf FICS -iconic

If you want to use Nalimov's endgame tablebase, download it into subdirectory 
tablebase.



Nope not working .... seg faults on the above commands ....... but I have not got the full makefile until I edit out
one of the CFLAGS lines ........... but which one will work is anyones guess. ( debugging to start with probably )

Not getting anywhere fast with that one ..... maybe I need to find some more information out about what its meant
to do ..... but did try a couple more of the CFLAGS and although it builds ok ....... it still segfaults.

The idea is that you wanted to write in C though - so will leave you to continue further on your course of discovery
and then will check back later ....

---

### Post by spacerocket on 2014-04-14
I would like to continue that python project but don`t know how to code anything with that.

Maybe follow this tutorial: [http://www.learningpython.com/2006/03/12/creating-a-game-in-python-using-pygame-part-one/](http://www.learningpython.com/2006/03/12/creating-a-game-in-python-using-pygame-part-one/)

---

### Post by 23dornot23d on 2014-04-14
That is a 2006 tutorial using very old methods and a very old version of python.

> 
Maybe follow this tutorial: [http://www.learningpython.com/2006/0...game-part-one/]("http://www.learningpython.com/2006/03/12/creating-a-game-in-python-using-pygame-part-one/")


__________________________________________________

Do me a favour ..... and just follow this one tutorial to get a **gui **up ..... that will be a start point ......... or even
go back to the start of his tutorials ...... 

I stepped in here because I wanted to do graphics - he is easy to follow .... too and explains things as he goes along.

[http://youtu.be/KEnDTjBMLhU](http://youtu.be/KEnDTjBMLhU)

most games have a need for some sort of a graphical display - for programs to work nowadays ...........

__________________________________________

Then tell me when you completed it ...... 

The guy who does these tutorials is good in the way that he leads you into things slowly
and sets out foundations for doing more things from the same program he starts off with.

The way we can do this is simple - I will see if I can find things that may be useful for what you need ...... then you can
start putting things together and playing with the code - to do things on screen - so you can see what it achieves.

If there are things we do not know then we both can go searching for them and work out what it is they do.

Tell me anything that will not work as sometimes separate parts of python code need to be loaded in like
python tkinter - load it using synaptic as below ........ or on the command line as the line underneath the picture.

[IMG]http://i.minus.com/ibby0sk7wauC7y.png[/IMG]

**sudo apt-get install python-tk**

I can only show you some basics .... as I am only learning too (but I have a lot of years behind me where I tried many things) - 
so if you want we can go through things and people can correct us - or try to add some helpful hints towards making things better ........

Best I can do at the moment ....... 

( but I doubt we can just go into writing a full game without at least some background ideas and worked examples )

Hacking other peoples code is easier .... but still needs a lot of thought - into how they are creating loops and how they
break out of the loops to move to other parts of a program ......... also which parts of the code pick up mouse or keyboard interaction
with the program ...... and what commands allow that to take place.

That is about all I can say for now ........ just to do one thing ..... get it done ..... reply with the code and a screen shot and how you got
it working ...... also give any problems back that you encounter.

*[SIZE=1]Small steps ......... we crawl before we can walk ( and we walk before we can run ........... ) ............[/SIZE]*

---

### Post by spacerocket on 2014-04-14
Just a little note..

I don`t have sound in this PC so would it be possible to work out how python works without youtube....

Thanks anyway for your interest.

---

### Post by steeldriver on 2014-04-14
You may find this resource useful --> [http://www.greenteapress.com/thinkpython/thinkpython.html](http://www.greenteapress.com/thinkpython/thinkpython.html)

> *Think Python* is an introduction to Python programming for beginners.  It starts with basic concepts of programming, and is carefully designed to define all terms when they are first used and to develop each new concept in a logical progression. Larger pieces, like recursion and object-oriented programming are divided into a sequence of smaller steps and introduced over the course of several chapters.

It is a very step-by-step introduction to Python (and to programming in general - it should answer a lot of basic questions about "what is a variable?" "what are variable types?" and so on)

I have the print copy but the whole thing is available as a pdf and/or html doc online

---

### Post by 23dornot23d on 2014-04-14
The links above in the moderators thread are better ......

________________________________________________________

---

### Post by spacerocket on 2014-04-15
Ok so if I understand this : [http://www.greenteapress.com/thinkpython/thinkpython.pdf](http://www.greenteapress.com/thinkpython/thinkpython.pdf)   completely I can move to C++ language.

Before that I can continue reading until that point I can write a program in python and ask here if I have any questions.

---

