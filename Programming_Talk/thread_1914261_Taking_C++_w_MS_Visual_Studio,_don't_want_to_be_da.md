---
title: "Taking C++ w/ MS Visual Studio, don't want to be damaged goods..."
date: 2012-01-24
forum: Programming Talk
---

### Post by earthpigg on 2012-01-24
So, no real choice in the matter. Last semester at community (PolSci major) and had to find fluff units before transferring to a 4 year. It was c++ with MS Visual Studio or nothing.

Concerns:
-Don't want to be locked into Visual Studio.
-Don't want to learn something unique to C++ and regard it as the 'only' way to do it.
-Want to be aware of things in C++ that aren't in C, and be sure I can do it both ways.
-Ideally, I'd finish the semester basically literate in both.
-Also don't want to spend a lot of time on the IDE thing. I know I can do it all with just a text editor and compiler, and I know I can put the time in to learn vi/emacs.
-I'd like my tinkering at home to re-enforce what I'm learning in class.

1) Any small/simple pointers as to what I should be aware of that I'm learning in C++ that wont apply? Prof said the last half of semester would be "Object Oriented" and the first half would be... the, um, other kind.

2) Suggestions on IDE? Would like to spend minimal time on learning an IDE, and since I'll be on MSVS at school it may as well be similar to that. I can play with vi/emacs/gedit+make later on in life. That little "compile and run" play button seems nifty enough for the small and quickly compiled stuff I'll be doing at this point.

EDIT: Or, I'll do you one better than any IDE at all. If I'm in the same directory as the cpp file, what would the commands be to quickly compile and then run the thing? For now at least, it'll all be terminal stuff and don't really need special compile-time flags... Well, maybe the "use more than 1 core on this i7 machine" flag.

---

### Post by satsujinka on 2012-01-24
Assuming you have the GNU Compiler Collection (gcc)
For C:
gcc -o targetname filename.c
For C++:
g++ -o targetname filename.cpp

replace targetname with the name you want for the executable and replace filename with the name of your source code file.

As for IDE, I typically use geany. It's lightweight and does pretty much everything. It really shouldn't take any extra time to learn it, just type, save, then go to Build->Build (F9), and Build->Execute(F5). Geany also has a Build->Compile option, but at least for C/C++ it doesn't work with the execute command (if you change it to:
gcc -o "%e" "%f"
or
g++ -o "%e" "%f"
it'll work though.)

As for what is C and what is C++...
C++ adds classes, templates, and various other things not in C. C++ also has different libraries from C

A trivial example of different libraries involving input/output. Notice that C calls libraries with a .h at the end. C++ can call them as well, but C can't call C++ libraries (the example bellow being iostream.)
C:
```
#include <stdio.h>/*include standard I/O library*/
int main(){
    puts("Who are you?");         /*simple print string to console: Who are you?*/
    char name[10];                /*a string*/
    fgets(name,10,stdio);         /*gets input from the console*/
    printf("Hello, %s \n", name); /*formated print to console: Hello, <then whatever you put in for name>*/
    return 0; /*exit*/
}
```C++:
```
#include <iostream> //include standard C++ I/O library
int main(){
    using namespace std; //cout and cin are in std, this allows you to omit std:: before calling them
    cout<<"Who are you?"<<endl;
    string name;
    cin >> name;
    cout<<"Hello, "<<name << endl;
}
```

---

### Post by 3Miro on 2012-01-24
Once you know C/C++ well enough, other languages would be easier. Other than memory management, I can't think of anything in C/C++ that wouldn't be generally useful in say Python. But you should learn at least basic memory management anyway.

The main difference between C and C++ is in the Objects (i.e. classes). The rest is minor syntax differences (although you can argue that classes are simply a bigger syntax difference).

If you want a simple IDE, I also recommend Geany. For its simplicity, it is incredibly powerful.

On simple command line and the C++ fundamentals, VisualStudio is the same as GCC (i.e. the compiler on Linux). For visual stuff, they are completely different. For Linux GUI programming you can look at GTK (the core of Gnome, XFCE, LXDE) and QT (the core of KDE) or some smaller utility like SDK or GLUT. However, before I go into visual code, I would go for good fundamentals.

---

### Post by JDShu on 2012-01-24
My first class in programming was C++ with visual studio. Learning how  to write C++ code later with emacs and compiling with gcc and whatever  is trivial. So don't worry, you won't be locked in.

---

### Post by Simian Man on 2012-01-25
> **earthpigg said:**
> Don't want to be locked into Visual Studio.
Don't worry, the IDE or editor you use is a fairly trivial matter.  People blow it out of all proportion with the Emacs/Vi discussions, but moving between IDEs and editors is not a big deal.

> **earthpigg said:**
> Don't want to learn something unique to C++ and regard it as the 'only' way to do it.
I'd recommend just focusing on C++ as your first language.  Don't try to learn how all of the languages out there work at once.  Just learn how to solve problems with C++.  Then you can learn different languages and see how they go about things.

> **earthpigg said:**
> Want to be aware of things in C++ that aren't in C, and be sure I can do it both ways.  Ideally, I'd finish the semester basically literate in both.
Again, I wouldn't worry about that.  You will sometimes see people write C/C++ as if they are one and the same, but really they are two very different languages with very different styles and methodologies.  Learn one first, then worry about the other if you need it.  I would recommend learning something like Python for your second language rather than C.

> **earthpigg said:**
> Also don't want to spend a lot of time on the IDE thing. I know I can do it all with just a text editor and compiler, and I know I can put the time in to learn vi/emacs.
Don't worry about that at first.  Just learn to program first with whatever tool you want to start with.  Later you can learn a more advanced editor.

> **earthpigg said:**
> I'd like my tinkering at home to re-enforce what I'm learning in class.
Good idea!

> **earthpigg said:**
> Any small/simple pointers as to what I should be aware of that I'm learning in C++ that wont apply? Prof said the last half of semester would be "Object Oriented" and the first half would be... the, um, other kind.
I'm guessing he said procedural or imperative.  What do you mean by "won't apply"?  The best pointer I have is to tinker and experiment on your own in addition to the class assignments.  Try adding new features to the programs you write in class.

> **earthpigg said:**
> Suggestions on IDE? Would like to spend minimal time on learning an IDE, and since I'll be on MSVS at school it may as well be similar to that. I can play with vi/emacs/gedit+make later on in life. That little "compile and run" play button seems nifty enough for the small and quickly compiled stuff I'll be doing at this point.
If you want something like MSVS, I'd recommend Code::Blocks.

---

### Post by earthpigg on 2012-01-26
Sweet guys ty, exactly what I was hoping for. Playing with Geany, good enough. 

Very minor question:

I ran the basic 2nd day of class stuff, and geany gave me an error message for a 

```
system("pause");
```

that is being taught as the normal thing to have right before

```
return 0;
```

I can comment it out and runs fine, but 1) Any idea what's up with that and 2) How successful am I going to be at coding at home then bringing it into class and expecting it to work on MS Visual Studio?

---

### Post by earthpigg on 2012-01-26
Completely inappropriate for this forum, but...

When playing around with the exact same code in Geany for Windows that runs on Linux geany and Windows MSVS, I get:

```
'"/.test"' is not recognized as an internal or external command, operable program or batch file.
Press any key to continue...
```

---

### Post by r-senior on 2012-01-26
> **earthpigg said:**
> I ran the basic 2nd day of class stuff, and geany gave me an error message for a 

```
system("pause");
```

that is being taught as the normal thing to have right before

```
return 0;
```

I can comment it out and runs fine, but 1) Any idea what's up with that and 2) How successful am I going to be at coding at home then bringing it into class and expecting it to work on MS Visual Studio?
The system() function runs a shell command, as though you had typed it into a terminal. If you do the same on Linux, you'll find you don't have a pause command. DOS does.

This is a good example of why system() can create code that doesn't translate between platforms.

As far as how successful you are going to be ... you may or may not be successful. You may run into problems. But you will learn things along the way that your tutors are not teaching you. Which is a good thing. :)

---

### Post by Simian Man on 2012-01-26
> **earthpigg said:**
> I ran the basic 2nd day of class stuff, and geany gave me an error message for a 

```
system("pause");
```

that is being taught as the normal thing to have right before

```
return 0;
```
What that command does is invoke another program called "pause".  Pause is a DOS program that gives the "Press any key to continue" message and waits for input.  It is bad practice to put that in your code because it is not platform independent and also if you put a pause.exe in the same directory as your program, it will be invoked instead.

Last time I used MSVS, when you ran programs from the IDE it held the terminal window open after the program was done executing, so I'm not sure why that's being taught.  You should either remove that line when running it on Linux, or put the following script in "~/bin/pause".
```

#!/bin/bash

echo "Press [Enter] to continue"
read dummy

```


> How successful am I going to be at coding at home then bringing it into class and expecting it to work on MS Visual Studio?
You should be fine for the most part.  There are some little things like this that system nuances, but for the most part you should not run into many in a beginners class.  There are also extensions to C++ that GCC has, and other extensions that MSVS has, but you should try to avoid them.  With GCC, if you pass the "-pedantic" flag, it will give you errors if you accidentally use GCC-specific features.

> **earthpigg said:**
> When playing around with the exact same code in Geany for Windows that runs on Linux geany and Windows MSVS, I get:

```
'"/.test"' is not recognized as an internal or external command, operable program or batch file.
Press any key to continue...
```
That just sounds like your project settings are messes up in MSVS.  I assume it should be "./test" instead of "/.test".  I haven't used MSVS in a while, so I don't know what help I can be.  I'd try making a new project and pasting the code in as it seems to be a setup issue rather than a code issue.

---

### Post by earthpigg on 2012-01-26
Thanks again folks.

> **Simian Man said:**
> 
That just sounds like your project settings are messes up in MSVS.  I assume it should be "./test" instead of "/.test".  I haven't used MSVS in a while, so I don't know what help I can be.  I'd try making a new project and pasting the code in as it seems to be a setup issue rather than a code issue.

I was using Geany for Win when I encountered that problem, not MSVS.

edit: and it was a c+p job. :)

edit2: ill play with it a bit more before anyone spends more brain time on it.

---

### Post by earthpigg on 2012-03-13
Question about porting code from Visual Studio to Geany.

We're doing functions now.

I can make it all be one big file, but is there a way to have it as three separate files that reference each other?

He wants to have it in three separate files: header file that describes functions, file that defines them, and main() file for reasons X, Y, and Z that I've no choice but to accept and that thus aren't particularly relevant. 

Snip from today's introductory example (ignore the 'math' in the filenames, mentally replace it with an appropriate name - I also haven't done data validation yet, so ignore that too):

**math_H.h**

```
#include <iostream>
using namespace std;

#ifndef randomManip
#define randomManip

double employeeGrossPay (int hours, double wage);
//Preconditions: both are non-negative numbers, hours is an intiger and wage is a decimal value.
//Postconditions: Returns the gross pay of one employee, giving time and a half for hours past 40.

double totalGrossPay (double currentTotal, double latestEmployee);
//Preconditions: both are non-negative numbers, currentTotal is the running tally and latestEmployee
// is to be added to that.
//Postconditions: Running tally of total gross pay is updated by summing the two numbers.

#endif
```

**math_Imp.cpp**

```
#include <iostream>
#include "math_H.h"
using namespace std;

#ifndef randomManipImp
#define randomManipImp

double employeeGrossPay (int hours, double wage)
{
	int hoursOver40 = 0;
	double grossPay = 0.0;
	if (hours > 40) // separate normal time from overtime hours
	{
		hoursOver40 += hours - 40;
		hours = 40;
	}
	grossPay = (hours * wage) + (hoursOver40 * 1.5 * wage);
	return grossPay;
}

double totalGrossPay (double currentTotal, double latestEmployee)
{
	return currentTotal + latestEmployee;
}
```

**math_test.cpp**

```
#include <iostream>
#include <ctime>
#include <iomanip>
#include "math_H.h"
using namespace std;

int main()
{
	int hours = 0;
	double wage = 0.0;
	char more = 'y';
	int counter = 0;
	double allEmployeesTotal = 0;

	do // main loop for entering employee info
	{
		counter++;
		cout << "Enter hours for employee #" << counter << ":\t";
		cin >> hours;
		cout << "Enter wage for employee:\t$";
		cin >> wage;
		cout << "Gross Pay for that employee:\t$" << setprecision(2) << fixed 
			<< employeeGrossPay(hours, wage) << endl;

		//update running total for total pay for all employees.
		allEmployeesTotal = totalGrossPay(allEmployeesTotal, employeeGrossPay(hours, wage)); 
		cout << "More employees? (y/n)\t";
		cin >> more;
		more = tolower(more);
	} while (more != 'n');

	cout << "Total gross pay for all " << counter << " employees:\t$" << setprecision(2) << fixed 
		<< allEmployeesTotal << "." << endl;
	return 0;
}
```

---

### Post by muteXe on 2012-03-13
What are you asking? Are you saying these 3 files moved to geany doesn't compile anymore?

---

### Post by earthpigg on 2012-03-13
If I put the three files in the same directory and then open them at once in geany in three different tabs, it doesn't seem to automatically recognize that they're related. Replacing #include "math_H.h" with #include "/path/to/math_H.h" doesn't seem to do it either.

If I amalgamate them into one .cpp file, it works fine. But, trying to go along with the way we're being taught in class I'd like them in three.

EDIT: In Visual Studio, we are taught to start off the lab time by creating a new "project", and through some wizardry any files just created or added are thus automatically associated and through some other magic I do not understand built/compiled together. I see a "project" menu in geany, but the paradigm stops there and I don't seem to see a "add file to project" dialog anywhere. 

Trying to stomp the vendor lock-in bugs as they pop up. :)

---

### Post by muteXe on 2012-03-14
I've not used geany i'm afraid (visual studio all the way for me), but yea there should be a project file somewhere.
maybe create a blank project in geany with a few cpp and h files, then try and locate the project file created and use this as a basis for creating your own project file.

In fact, even better. Create a new project with files called the same as yours and just copy your code into each of the files.

---

### Post by r-senior on 2012-03-14
I think I'd go the route of getting the program to compile from the command line. Geany is a lightweight tool rather than a complete IDE and you'll probably need a makefile or at least modify Geany's build command for the project. Geany's project file is just a collection of open files and overall project preferences.

Something like

```
g++ -o mathimp math_Imp.cpp math_test.cpp
```

---

### Post by earthpigg on 2012-03-14
OK thanks for the advice. I got it working the way we were taught in codeblocks (see screenshot).

Would still be interested if someone is aware of a way to make geany do that.

---

### Post by dwhitney67 on 2012-03-14
> **earthpigg said:**
> OK thanks for the advice. I got it working the way we were taught in codeblocks (see screenshot).

Would still be interested if someone is aware of a way to make geany do that.

My $0.02... focus more on the quality of your code and not so much on the IDE.


Here's some issues I saw in your code:

1.  Unnecessary header files included in the .h file

2.  Unwarranted "using namespace" directive in .h file; NEVER do this.

3.  Unnecessary header files and/or "using namespace" directive included in .cpp file(s).

4.  System header files should not be included before project header files.

5.  Redundant code.

---

### Post by matt_symes on 2012-03-14
Hi

> employeeGrossPay (int hours, 

> Preconditions: both are non-negative numbers, hours is an integer

If the above is so, why is hours a signed integer ?

Kind regards

---

### Post by earthpigg on 2012-03-16
A lot of that is

> for reasons X, Y, and Z that I've no choice but to accept and that thus aren't particularly relevant. 

And some because he isn't being nit-picky, and why should I be? Once we're done with the lab assignment, we're done and can leave. The above is good enough for 30/30 on the lab assignment. On my own time *out* of school, I've at this point got a nifty little pong game up and running using SDL and OpenGL. :P

---

### Post by earthpigg on 2012-03-16
The only reason I "worry" about the IDE is so I don't have to do the homework assignments in class and can do them at home. It's cool though, codeblocks solved it for me.

---

### Post by Dragaan on 2012-03-24
I took a class in C++ last semester and figured some stuff out about system() function.

In most IDEs, you need to #include <cstdlib> to be able to use it.  Also, whatever goes in the quotes must be in CAPS (ie. system("PAUSE") ).  I also noticed MSVC allowed me to use it without including anything.

Also, as I'm sure you've realized by now, you don't need to use that line to get your program to pause after it finishes running in every IDE.  Most IDEs I've used have that built-in as a feature.  MSVC does it if you run+debug (I think - could be the other one), Code::Blocks does it, Geany does it.

Kinda useless info but I figured I'd reply anyway, lol.

---

