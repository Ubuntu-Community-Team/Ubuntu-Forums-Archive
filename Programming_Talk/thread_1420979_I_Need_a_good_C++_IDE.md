---
title: "I Need a good C++ IDE"
date: 2010-03-03
forum: Programming Talk
---

### Post by cmommsen on 2010-03-03
Anyone know of a good C++ IDE that I can use to write and compile basic programs on my laptop running Ubuntu Karmic?   I've tried pretty much all the ones in the Ubuntu Software Center and while I really like a few of them, I havn't been able to get a single program to compile and run.  (actually, I've got one IDE to work good but it's Bloodshed's DevC++ for windows, and I have to run it through Wine, and I don't like it.)

I'm just starting to learn C++, mostly on windows using basic funtions like IOSTREAM, so I don't know much about programming on linux.... but I can still use the same libraries like the standard library, right???  Or is it a simple matter of installing the appropriate libraries? :-k

---

### Post by gumpish on 2010-03-03
If you're just starting (as in, "Hello, world!") my advice would be to use a plain text editor and invoke the compiler and linker manually from the command line just to get an appreciation for what the IDE does.

For more complex code, I personally enjoy using the Eclipse C++ package.

---

### Post by cmommsen on 2010-03-03
ok, so what is the command for compiling a file, say helloWorld.cpp?  Does Ubuntu come with a built in compiler?  Oh, and when I write the source file, I need it to be saved as .cpp so I can attach it to an email and turn it in (I'm taking a C++ class...)  So what is the software I need to make that happen?

---

### Post by dwhitney67 on 2010-03-03
You do not need an IDE.  Just use a gnome-terminal, and from within it, run 'vi'.  If you don't know 'vi', then use gedit.

From the command line, you can compile your works of art using a command similar to the following:
```

g++ HelloWorld.cpp -o HelloWorld

```
Then to run the app:
```

./HelloWorld

```

---

### Post by cmommsen on 2010-03-03
OK cool! I made my first program with gedit and it compiled and ran... It even made my source code all nice and color coded after I saved it as .cpp!  A whole new world has opened before my eyes...  :P

But it outputted the text "hello world" to the terminal window... is there a way to make it go into a new window like in... Windows?  

Could you give me a break down of 

g++ helloworld.cpp -o HelloWorld

I'm a curious young bass terd...

---

### Post by cmommsen on 2010-03-03
Also, back to my original question:

Why don't the compilers in Ubuntu Software Center accomplish compiling and debugging?
I tried Anjuta, MonoDevelop, Code::Blocks, and QT Creator... I really like QT C, it's so well designed...  I just wish it would do something when I hit 'play'  :-|

---

### Post by dwhitney67 on 2010-03-03
An IDE is not a compiler.  GCC, on the other hand, is a compiler.  A typical IDE, when setup for C or C++ projects, will use GCC as it's compiler.  If you don't have GCC installed on your system, then regardless of whether you use an IDE or the command line, you won't be able to compile.

'gdb' is the Gnu Debugger.  It is a separate package from GCC, but typically it is included if you install "build-essential".

'ddd' is yet another application, that is a GUI front-end to many debuggers, most notably 'gdb'.

Concerning building an app from the command line, here's a breakdown of that statement I provided earlier:

'g++' is the C++ compiler, and '-o' is the output option used to specify what you want to name the executable program.  Without the option, 'g++' defaults to naming executables a.out.

---

### Post by Queue29 on 2010-03-03
> **dwhitney67 said:**
>   If you don't have GCC installed on your system, then regardless of whether you use an IDE or the command line, you won't be able to compile.

There are a lot of other compilers besides gcc.

---

### Post by cmommsen on 2010-03-03
Oh, ok I understand.  So I think what I need to do is choose an IDE that I like, say QT Creator, and then proceed to set it up to compile and run C++ programs.  

Can you offer any advice on how to do that, or is it too general?  So far, I ran

sudo apt-get g++

and now I'm able to compile a .cpp file from terminal. (what's "linking")  
Do I need to get other packages?
And how do I point QT Creator to GCC?  Are there any gereral "settings" that I should be changing in QT C's setup?  There's something about a "build environment... path"?

---

### Post by cmommsen on 2010-03-03
Oops, that's

sudo apt-get install g++

---

### Post by Queue29 on 2010-03-03
> **cmommsen said:**
> Oh, ok I understand.  So I think what I need to do is choose an IDE that I like, say QT Creator, and then proceed to set it up to compile and run C++ programs.  

Can you offer any advice on how to do that, or is it too general?  So far, I ran

sudo apt-get g++

and now I'm able to compile a .cpp file from terminal. (what's "linking")  
Do I need to get other packages?
And how do I point QT Creator to GCC?  Are there any gereral "settings" that I should be changing in QT C's setup?  There's something about a "build environment... path"?

If you create a project in qt creator, and then add your source files to that project, it will automatically take care of making a Makefile for you, and you'll be able to just hit the big play button and watch it run.

---

### Post by dwhitney67 on 2010-03-03
> **Queue29 said:**
> There are a lot of other compilers besides gcc.

Not in my "world".

---

### Post by cmommsen on 2010-03-06
Can someone give a list of packages to install along with GCC?  Or is there a meta package...  I don't know alot about programming and libraries but here's what I need:

Compiler, Debugger

And the following libraries:

iostream

cstdlib

string

vector 

alorithm

Or if this is too general, can you outline the steps for finding a C++ library in say, Package Manager, and getting it to work in my IDE?

---

### Post by LKjell on 2010-03-06
> **cmommsen said:**
> Can someone give a list of packages to install along with GCC?  Or is there a meta package...  I don't know alot about programming and libraries but here's what I need:

Compiler, Debugger

And the following libraries:

iostream

cstdlib

string

vector 

alorithm

Or if this is too general, can you outline the steps for finding a C++ library in say, Package Manager, and getting it to work in my IDE?

```
sudo apt-get install build-essential vim
```

That should give you a good text editor that you need to _learn_ to use and everything setup to write C++ codes.

---

### Post by cmommsen on 2010-03-06
Is that like vi?  I tried running vi from within the terminal and it was kinda confusing... 

The main reason for this thread is I'm trying to get and set up a good IDE for writing assignment programs for my beginning C++ class.  Most others in the class are using Windows, and we were given software (DevC++) to install and use for all the projects.  I'm guessing the CD it came on contained all the necessary libs and files to make work, because I was able to install it on my laptop via Wine, and it does everything ok.  (except graphics)

I know I could just write all my code with gedit and compile them in the terminal, but I really want to know how to set up a good programming environment that has everything right there and is smoother for debugging and also looks cool, especially since I'm trying to get some of my friends into programming as well.  After all, isn't that the main point of IDE's? 

And I want to progress further than just using iostream and 'cin', 'cout'...

---

### Post by mmix on 2010-03-06
There is gedit plugin called "Embedded Terminal".

Oh yeah, and you can compile source code with short cut key in gedit.

Another IDE is anjuta, acme, 
But, these thing is heavy or mouse-oriented.

---

### Post by gnometorule on 2010-03-06
If you just try to get off the ground and focus on learning C++ under Ubuntu, don't use vim. It's geek central - powerful but you feel transported back to 1979. I would also not even try to use an IDE - had trouble myself with getting those started when I flipped from Visual C++ (under windows) to Ubuntu. 

As several have mentioned above, gcc is the way to go. I agree with DWhitney - why would you use anything else if you work in Ubuntu? It's very easy to learn, even for beginners. And edit with 'nano', which should be installed on your system (take note of one command that's not directly visible but you'll use a lot is 'alt-6' == copy). Here is your package that will have you up and running in a few hours:

- nano
- gcc for C, g++ for C++ (both come under build-essential, that's all you'll need) (man page is "man gcc" for both)

Bookmark, browse, and refer to (or buy):

[http://www.network-theory.co.uk/docs/gccintro/gccintro_42.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_42.html) 
[http://www.delorie.com/gnu/docs/gdb/gdb_toc.html](http://www.delorie.com/gnu/docs/gdb/gdb_toc.html)

I find coding using this simple but not uebergeek setup extremely enjoyable. Gl.

---

### Post by LKjell on 2010-03-07
The problem when people try learn Vim is that they try to remember too much.
If you are going to code much, Vim is a very good investment. But writing touch might help too...

---

### Post by cmommsen on 2010-03-07
Ok so I set up gedit to color coding for C++ and all that, and added the "external tools" plugin.  Now I can write a program and hit <ctrl F9> and it tries to compile.  But I keep getting this error:
> 
Running tool: Build

No Makefile found!

Done.
I have installed gcc I think... i typed:
```

sudo apt-get install gcc

```into terminal....   Does anyone know what else could be wrong?

---

### Post by LKjell on 2010-03-07
> **cmommsen said:**
> Ok so I set up gedit to color coding for C++ and all that, and added the "external tools" plugin.  Now I can write a program and hit <ctrl F9> and it tries to compile.  But I keep getting this error:
I have installed gcc I think... i typed:
```

sudo apt-get install gcc

```into terminal....   Does anyone know what else could be wrong?

Means you need to write a makefile and put it in the current directory.

---

### Post by wreck47 on 2010-03-07
It is looking for a makefile. You can either use a make file or use the command prompt. 
Using a make file is very useful when compiling multiple source file with dependencies. 

Try doing this: 
1. Create a file named "Makefile"
2. Paste this contents into the file:

DEBUG= -g

executable: fileName.o
    g++ -O -o executable fileName.o

fileName.o:  
    gcc -O -c $(DEBUG) fileName.cpp

clean:
    rm -rf *.o executable

(I have just written this from the top of my head, there might be some syntactical error, give it a shot.
Replace the executable with the name you want for you executable and the fileName with your .cpp file)

---

### Post by wreck47 on 2010-03-07
BTW, If you want to execute the program using command prompt using makefile, the command is:
1. To build: make
2. To clean: make clean

if you dont have make installed, you can get it using:
sudo apt-get install make

---

### Post by cmommsen on 2010-03-07
Sorry I have no idea what that means.  Can you explain how?

Oh wait nevermind.  I was on the second page...

---

### Post by kalos on 2010-03-07
While you're fine using gedit, gvim, or emacs instead of an IDE, if you do serious programming, you will want a debugger.

gdb, ddd, and insight are debuggers that are easy to get running. Just run ```
insight executable
``` (where executable is the name of your program) to get started. (I remember using ddd for my C++ class and found that despite it's old graphics look, the [data visualiser]("http://www.gnu.org/software/ddd/all.jpg") was really impressive.) 

If you want something fancier, you can get an IDE with debugging abilities. Try [Code::Blocks]("http://www.codeblocks.org/") or [Eclipse]("http://www.eclipse.org/cdt/") or something else mentioned above.

Oh, and did you run apt-get install build-essential? Having that will prevent a lot of build issues later on (it installs a bunch of tools for building c++ applications).

---

### Post by cmommsen on 2010-03-07
Thanks!  I made the file thus:

> DEBUG = -g

Test: test.o
g++ -O -o Test test.o

test.o:
gcc -O -c $(DEBUG) test.cpp

clean:
rm -rf *.o TestAnd this is what I get when I build:

> Running tool: Build

Using makefile from ~
make: Entering directory `/home/curtis'
makefile:4: *** missing separator.  Stop.
make: Leaving directory `/home/curtis'

Exited: 512Is this good?

---

### Post by Zugzwang on 2010-03-07
> **cmommsen said:**
> 
Is this good?

The GNU Make utility expects a tabulator in front of lines "that tell GNU Make what to do". So first of all configure your text editor *not* to replace TABs with 4 whitespaces or so and then try the following Makefile (replace "<TAB>" by the tabulator):

```

DEBUG = -g

Test: test.o
<TAB>g++ -O -o Test test.o

test.o:
<TAB>gcc -O -c $(DEBUG) test.cpp

clean:
<TAB>rm -rf *.o Test 

```

Something to add is that you probably want "default:" instead of "Test:" in the third line such that you only have to type "make" instead of "make Test" on the terminal.

---

### Post by dwhitney67 on 2010-03-07
The most basic way to use 'make' does not require the use of a Makefile because 'make' has built-in rules for common file types.  So for instance, if you wanted to build an app from a single source module called MySource.cpp, then the following would suffice:
```

make MySource

```
This will compile the C++ source file MySource.cpp and produce an executable named MySource.  You can specify compiler flags on the command line as well; for instance:
```

make CXXFLAGS=-Wall MySource

```
After a while, you might find this a bit cumbersome, thus the need to create a Makefile becomes desirable.  Here's a simple Makefile:
```

# application name
APP      = myAppName

# list of source file(s)
SRCS     = MySource.cpp
OBJS     = $(SRCS:.cpp=.o)

# handy definitions
DEBUG    = -g
INCLUDE  = -I./

# compiler flags
CXXFLAGS = $(DEBUG) -Wall -ansi $(INCLUDE)

# for library specification and paths
LDFLAGS  = -L./

# link the app (note, 'make' takes care of compiling object files automatically)
$(APP) : $(OBJS)
        $(CXX) $^ $(LDFLAGS) -o $@

# clean up
clean:
        $(RM) $(OBJS) $(APP)

```

---

### Post by cmommsen on 2010-03-08
Thanks people, both of these above makefiles work great!  I'm now able to write, compile, and run my own programs from within Gedit with relative ease.  (I still have to go into terminal to actually run the apps, cause when I do it from within Gedit it just prints all the 'cout's and returns 0 from 'int main()' but that's fine by me)

For anyone who read through this thread for advice, here's what I ended up doing:

1. Install GCC:

```
sudo apt-get install build-essential
```2. Create makefile:
Refer to either Dwhitney67's or wreck47's posts above.
If you end up copy-pasting, make sure you replace all tabs by backspacing all the way and hitting <TAB>.

3. Setup Gedit:  
In preferences, make sure 'INSERT SPACES FOR TABS' is unchecked.
In plugins, turn on "External Tools".
In View > Highlight Mode > Sources,  check "C++".

You can then proceed to write your program.  Next, save it as "MySource.cpp" (if using Dwhitney67's example) 
Next press <Ctrl F8> to build the App.  It will be called "myAppName" unless you want to change the makefile.

4. Finally open Teminal to run it:

```
./myAppName
```

---

### Post by cmommsen on 2010-03-08
And here is my first succesful program!  Any offers of criticism/advice?

```

//Calculates the number of days till Christmas.
#include <iostream>

#include <string>//I include this file so I can utilize string objects.



using namespace std;



int main()//This is the Main funtion of the program.

{

string month;//This holds the user input for what month they choose.

int date;//This holds the user input for what date they choose.
const int days_left = 6;//days between christmas and new year.
int month_value = 0;//This will hold the number of days from "month" till end of year.
int position = -1;//used to caluculate value for month entered by user.
int days_till_christmas;//This will hold the number of days till christmas.

string MONTH[] = {"JANUARY", "FEBRUARY", "MARCH", "APRIL", "MAY", "JUNE",
 "JULY", "AUGUST", "SEPTEMBER", "OCTOBER", "NOVEMBER", "DECEMBER"};
//The array defines 12 months as variables and assigns them values from 1 - 12.

int daysPerMonth[] = {31,28,31,30,31,30,31,31,30,31,30,31};
//This array represents the number of days in each month of the year in order.

cout << "\nWelcome to the Days Before Christmas Calculator! " << endl;//Welcome user.

cout << "After you provide a date, it will tell you how many days/n";

cout << "Are left until Christmas!\n" << endl;

cout << "Please enter a month: ";//Promt user to enter month.

cin >> month;//Store their input in variable "month".

cin.get();//pause

for (int i = 0; i < month.size(); ++i)//Convert string "month" to upper case.
    month[i] = toupper(month[i]);


cout << "\nThank you for entering " << month << "." << endl;//Echo user input.

cout << "\nNow enter the day of the month: ";//Promt user to enter date.

cin >> date;//Store their input in variable "date".

cin.get();

for (int i = 0; i < 12 && position == -1; ++i)
    if (month == MONTH[i])
        position = i;//Set variable to index value of "month".

for (int i = position; i < 12; ++i)
    month_value += daysPerMonth[i];

days_till_christmas = (month_value - date - days_left);//Calculates days till Christmas.


cout << "\nThere are " << days_till_christmas << " days left until Christmas!" << endl;

//Finally, I display the result, and an ending message.

cout << "\nPress 'Enter' to end. " << endl;

cin.get();

return 0;//End of program.

}
```

---

### Post by dwhitney67 on 2010-03-09
Comments concerning the code:

1.  There are too many comments; don't comment obvious stuff.  Too many comments can actually make the code harder to read.

2.  Add defensive code should the user enter a month string that is *not* defined in the array (eg. "foo").

3.  Similarly, add defensive code should the user not enter the appropriate data expected of them; for example, if you prompt for a number, and the user enters "abc".

4.  Break the habit of declaring all of your variables at the entrance of a function; that used to be required by old-style C programs, but since 1999, that is no longer the case.  Declare/initialize variables at the closest point where they will be used by the program.

5.  Employ the use of STL stream objects (eg. cout) to their fullest, rather than calling them multiple times for outputting data.  For example:
```

cout << "This program does absolutely nothing worthwhile\n"
     << "other than to output the following statement.\n\n"
     << "Press the <Return> key to continue: ";
cin.get();

```


P.S.  I suggest changing your 'date' variable to be 'day'; after all, it represents the *day of the month*, not an actual date.

---

### Post by cmommsen on 2010-03-09
Cool, that's good to know about cout statements.  Okay, less comments. :D
 
How do I "defend" against erroneous input?  For example, I cant test an 'int' variable for a char value... or can I?

---

### Post by dwhitney67 on 2010-03-09
> **cmommsen said:**
>  
How do I "defend" against erroneous input?  For example, I cant test an 'int' variable for a char value... or can I?

First, ensure that the cin stream is reporting that all is well; for example:
```

int number = 0;

cout << "Enter a number: ";
cin  >> number;

if (!cin.good())
{
   // cin failed to parse an int value; in other words the
   // user gave erroneous input.
   //
   // What to do now?  Will you prompt the user again, letting
   // them know of their mistake?  Or will you just exit the
   // program?
}

```
If you decide that you want to prompt the user for input until they get it right, then you would need to use a loop (ie while-loop or for-loop) to repeatedly ask them for input.  With each iteration, the cin stream flags would need to be reset, and any remaining garbage in the stream would need to be cleared out.

You can read how to reset the state of the cin stream here:
[http://www.cplusplus.com/reference/iostream/ios/clear/](http://www.cplusplus.com/reference/iostream/ios/clear/)

For how to remove unwanted characters from the cin stream, read here:
[http://www.cplusplus.com/reference/iostream/istream/ignore/](http://www.cplusplus.com/reference/iostream/istream/ignore/)

To test what you have 'hopefully' learned from your reading, initially run your program that you posted earlier, and type in "Febuarie" for the month.  For the day of the month, enter "-2000", or "abc".  Then attempt to fix your code so that these input errors are handled properly.

---

### Post by cmommsen on 2010-03-09
Ok this is what I understand from your example...
 
So the 'good()' funtions returns a boolean value on whether or not the contents of the input buffer match the type of variable that the stream is being sent to? And if they don't match, it returns "false", correct?
 
And it probably makes the most sense to keep looping the prompt until the user either manages to satisfy cin.good() or they enter a keyword like "quit"....

---

### Post by dwhitney67 on 2010-03-10
> **cmommsen said:**
> 
So the 'good()' funtions returns a boolean value on whether or not the contents of the input buffer match the type of variable that the stream is being sent to? And if they don't match, it returns "false", correct?

Is there any other possibility with a boolean (other than True/False)?

---

### Post by cmommsen on 2010-03-11
No, but I meant, is that what is being tested by the funtion.  Cause I need to know exactly what is being tested in order to plan out the implementation of it.

The reason I'm dwelling on this over multiple posts is, this is the most troublesome part of programming for me so far:  I can't seem to be able to come up with a good way to defend against **any** possible user input.  I've tried making a bool variable:

bool error = true;
char var;

and then do all my cout statements inside a while loop:

while (error){
cout << "Yes or No?  Enter y/n: " <<endl;
cin >> var;
if (var == 'y' || var == 'n')
    error = false;
else
    cout << "Invalid response.  Please try again..." << endl;
}

This works unless they've entered a string of letters or numbers, which causes a infinite loop which fills the screen with all the cout's in the 'while' loop. :(

Any suggestions on how to implement the cin.good() funtion here?

---

### Post by dwhitney67 on 2010-03-11
> **cmommsen said:**
> 
This works unless they've entered a string of letters or numbers, which causes a infinite loop which fills the screen with all the cout's in the 'while' loop. :(

Any suggestions on how to implement the cin.good() funtion here?

Carefully re-read this [post]("http://ubuntuforums.org/showpost.php?p=8942504&postcount=32"):
[http://ubuntuforums.org/showpost.php?p=8942504&postcount=32](http://ubuntuforums.org/showpost.php?p=8942504&postcount=32)

The answer you seek is documented there.


P.S.  You are on the right track; now you must figure out what to do with the cin stream after you have detected the error.

---

### Post by linuxgurumaniac on 2010-03-11
Regarding the IDE u can always use  netbeans [http://netbeans.org/](http://netbeans.org/).
It support multiple programing, scripting languages and many more 
include C/C++.

P.S. 1: you need to install the java JRE to make it work.
P.S. 2: you still need to have a compiler installed to benefit from eg. gcc / g++.

---

