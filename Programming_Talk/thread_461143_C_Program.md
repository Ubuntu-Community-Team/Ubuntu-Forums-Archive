---
title: "C Program"
date: 2007-06-01
forum: Programming Talk
---

### Post by w4llsb4lls on 2007-06-01
Just completed an assignment for end of year at uni, and to get a few extra points im looking to split my program into several files, so that only the main code needs to be compiled each time any changes are made to the code.

Four files should be enough, a header file, a file with my main code, and two seperate files to hold all of the functions.

The tricky part, I attended the lectures but we never actually went through it in the labs, so I'm looking for a few pointers to get me off the ground.

Cheers.

---

### Post by WW on 2007-06-01
For example:
```

$ gcc -c func1.c
$ gcc -c func2.c
$ gcc -c main.c
$ gcc main.o func1.o func2.o -o main
$ ./main

```
If your program uses external libraries, you will need to add the appropriate options to the last gcc command. For example, if you use any math functions (such as cos or sqrt), you will need the option **-lm**:
```

$ gcc main.o func1.o func2.o -o main -lm

```

Once you get beyond a couple files, a Makefile is useful. Here is a simple example:

**Makefile**
```

main: main.o func1.o func2.o
	gcc main.o func1.o func2.o -o main

main.o: main.c header.h
	gcc -c main.c

func1.o: func1.c header.h
	gcc -c func1.c

func2.o: func2.c header.h
	gcc -c func2.c

```
With this file (saved with the file name **Makefile**), you can simply type
```

$ make

```
and only the changed code will be recompiled.

---

### Post by w4llsb4lls on 2007-06-01
That&#8217;s an excellent guide and clears that up for me, I will use the make file option as this would seem easier for the end user. (Meaning the lecturer marking my assignment!).

I need to clarify before I start chopping my program up that the following is how things are split up if possible, this is my understanding from my notes:

**assign.h**
#includes. 
#defines.
function prototypes.
typedefs.
global variables which are referred to using the extern keyword. i.e - extern int counter = 0; etc.

**assign.c**
#include "assign.h"
main(void)
{
}

**func1.c**
#include "assign.h"
functions.

**func2.c**
#include "assign.h"
functions

Once I get this correct I can make a new text file transposing your suggestion for my file names to create a make file which can be compiled using the command make. Does the make file need to have the file extension .c ?

Cheers.

---

### Post by WW on 2007-06-01
The Makefile should not have the extension .c; it is not a C program.  It defines dependencies among the C files.

By default, the **make** command will try to read the file called **makefile** or **Makefile**.  (Actually, GNU make looks for **GNUmakefile** first.)  Take a look at the man page for more details:
```

$ man make

```
(or just google for makefile).

Your organization of the code looks about right.  The compiler will complain if you declare a variable to be **extern** *and* you give it an initializer (e.g. **extern int counter = 0;**), so you should probably avoid that.

---

### Post by w4llsb4lls on 2007-06-02
Ok, I have managed to get the program split into 4 files, and everything compiles using the makefile option.

Problems though!

The program compiles fine without error, but I am having undesired results from the program which I have pin pointed to the extern variables which I am not initializing anymore in the header file.

I have gone through the program when I reference the global variables, and initialized them as required, but I'm totally stuck now as this does not produce the same results as when I run the program from one file which is fine.

---

### Post by w4llsb4lls on 2007-06-02
I think it comes down to trying to use an array as a global variable inside the header file, do I need to initialize the array size inside of the header file?

Or is there an easier way to use an array, and call it in each of the functions that reffer to it?

---

### Post by ruy_lopez on 2007-06-02
Is there a lot of code involved? Without seeing the code, its hard to debug. Is the array accessed from every function, in all the source files?

---

### Post by w4llsb4lls on 2007-06-02
Yeah the array is for a struct which is reffered to in all of the functions throughout the program...

There is only around 300 lines of code, but I have split it into 4 files, to make it more user friendly...

---

### Post by ruy_lopez on 2007-06-03
There's two ways you can have the array accessible to every function. 

You can declare the array as static in one source file. You would then write functions, in the same source file, that do the work of assigning and returning the structures. The other source files would then call these functions.

The other way is to declare the array outside of any function, at the start of one of the source files, say, like this:

```
char array[100];
```

The other source files would then need extern declarations to access the array:

```
extern char array[];
```

This just tells the scope block to use an external array, instead of creating its own.

The scope can be just a function, a source file, or every source file, depending where you put the extern statement.

Putting the extern in the header would give all source files access. Putting the extern inside one function would give only that function access.

---

### Post by w4llsb4lls on 2007-06-04
That makes sense mate, appreciate your input...

At the moment I'm sure I keep missing something, really I could do with someone taking a look at my code incase I am not describing something correctly as I have chopped up the program that many times with no success and I am back to using the one file version again.

---

### Post by ruy_lopez on 2007-06-04
Put the file in a tarball and attach it to your next post.

---

### Post by w4llsb4lls on 2007-06-04
Here it is mate, I have left the .csv files in there too as the program wont run without them.

Previously I had split it into assign.h, assign.c, func.c, func2.c, and menu.c. However when I split it up, although it compiled without errors the results of the program were not correct at all. This single file version works fine though.

I think it was mainly down to how all of the functions were accessing the array which I was declaring as an extern in the header file.

---

### Post by ruy_lopez on 2007-06-04
What was the problem after you split the files? What was the difference in behaviour between the two versions?

---

### Post by w4llsb4lls on 2007-06-04
In single file format all of the results are fine, output files ok, highest country, lowest country etc, but when I split them I get garbled characters instead of integer results in millions of dollars etc..

---

### Post by WW on 2007-06-04
I've broken up your single file into several pieces. It might not be the organization that you want, but it should get you started.  The main point, I think, is that the header file **country_data.h** declares the data structures and the global variables:

**country_data.h**
```

/*
 *  country_data.h
 *
 *  Files with functions that will directly access the global data
 *  must include this header.
 */

typedef struct {
	char year[10];
	double pop;
	double bot;
	double botPerHead;
} Data;

typedef struct {
	char countryName[50];
	char countryCode[4];
	Data yearlyData[11];
} Country;

/*
 *  Global variables.
 */
extern int ccounter;
extern int ycounter;
extern Country countries[];

```

The global variables are *defined* in the C file country.c:
```

...<snip>...

int ccounter = -1;
int ycounter = -1;
Country countries[250];

...<snip>....

```

I also included a Makefile.  To compile and run the program, type
```

$ tar xvf revised.tar
$ make
$ ./main

```

---

### Post by ruy_lopez on 2007-06-04
What WW suggests is right on the money, I did the exact same earlier and ran a diff on the cvs output, with clean results. (Thats why I asked what the problem was).

 I'm a little hazy over the output for the country with the highest balance of trade. Is it supposed to be a ridiculously large number?

Also, the country list is truncated when the screen clears, chopping off the countries below the US, depending on whether the terminal is maximised or not.

Now for some code pointers. When you are deeply nested inside multiple for-loops, rather than nest further with an if-statement, invert the condition and use "continue".

rather than this:

```
for(i = 0; i < 100; i++) {
        if (something) {
                do something;
        }
}
```

try this instead:

```
for (i = 0; i < 100; i++) {
        if (!something)
                continue;
        do something;
}

```
Notice that "do something" is now less indented. It might not seem like much, but when you are two or three loops deep, all the screen space helps.

Other than that, using pointers will save you a lot of typing, especially when it comes to arrays within structures within arrays. I'll take a proper look at the code tomorrow. I'm still interested to know what problems you were having.

---

### Post by w4llsb4lls on 2007-06-04
Guys,

This is brilliant help, I've clicked on what the problem was too.

I was declaring extern's for the global variables and the array, but then I was including a reference to them into every function that called them to try and get around initializing them on the header file. Instead of initializing them outside of the functions on the particular file of code that uses them.

So in essence I was recreating new variables and an array in each function, which would explain why no singular memory allocation was used to provide the consistent stores of information throughout the program.

Absolutely learned a great lesson there guys and I must say WW that's some of the best support I've experienced on the web. You have both been absolute diamonds. :KS

Yeah I noticed the output Country list is truncated, meaning the user has to scroll up to view the Country codes, so I do need to work on that. 

Yes the numbers are very large numbers as your looking at the total wealth of a Country so to speak, it's balance of trade. If you look at the USA before the war it was thousands of millions in the black, and then post war they move into thousands of millions of debt and so on.

I see what you mean about the code layout Ruy, the 'continue' replacement does look easier on the eyes. I need to sort out the truncated issue displaying the Country codes, and comment the code (I should have done this as I wrote the program I know!), So your suggestions will be used as I bring things together. 

I also want to introduce a pause when the files are read in, and then hopefully I can move toward handing things in.

Sincerely guys I'm a very happy and relieved man, I really appreciate both your efforts and time over the last few days.

Thanks again.

---

### Post by ruy_lopez on 2007-06-04
Anytime, mate,

here's my suggestions, mainly just some pointers on using, well, pointers. At first it won't seem as readable, but you should try and get used to it. The thing to remember is, the pointers are just local variables. I only suggest them because some of the code was running away with itself. In general, its a good idea to try and keep your lines from going over 80 columns. In practice its not always possible, but it does serve as a good reminder, for when you are too nested.

Neat little program, you should get a good grade.

---

