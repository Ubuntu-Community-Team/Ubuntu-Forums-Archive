---
title: "Tutorial: Programming C/C++ in Ubuntu using an IDE (Kdevelop&amp;QMake)"
date: 2009-09-05
forum: Programming Talk
---

### Post by Zugzwang on 2009-09-05
Hi all,

this text is made for those people wanting to program in C and/or C++ in a Linux environment and originally come from Windows, i.e., they either worked with something like the Borland C++ Builder or Visual studio. It contains some background information useful for a quick and informed start into programming in Linux and repeats a little bit about the basics of compiling programs, as it is extremely helpful to keep them in mind when programming in Linux, whereas such information is normally necessary in the Windows context. Then, it describes first steps for compiling programs, how to set-up an IDE (here, KDevelop is taken), how to debug programs and how to use libraries. We will use Ubuntu as example Linux distribution.

**Warning: Starting with Ubuntu 9.10, the version of KDevelop shipped no longer supports QMake projects. This makes this tutorial a little bit out-dated. Also the IDE look-and-feel itself is different, so much of the stuff written here doesn't hold any longer. I'll see if I have time for a new CMake-based versions in the next weeks.**

============================================
1. The choice of programming language
============================================
Before we actually start, there is something to mention: Unlike in Windows, where all "commercial" programs have are compiled in order to look "professional" and thus, many are written in C# or C++, there is no reason for such an attitude in Linux. In fact, for example, for Ubuntu, many of the Ubuntu-specific setting-up tools for your system are written in Python, which is a scripted language. As you can see, as a user, you will not notice, not even in terms of speed for applications which do not do sophisticated stuff. In fact, Python, for example, is much simpler to learn for beginners and you do not have to deal with compiling&linking of such programs before being able to run them. Debugging also tends to be simple. So please be advised that C/C++ is not always a good choice. However, some reasons to take it anyway include:

- You are already an expert in C and/or C++ and find it unlikely that you are doing enough projects in the future which would justify learning another language
- You need to use C and/or C++ (for example, if you are taking a college course which deals with precisely this language(s))
- You are developing an application for which execution speed is to utterly important in *all* of its parts such that other choices are unreasonable.

============================================
2. Some specialities in Linux
============================================
Now that we have done the preliminaries, some background information might be useful for you. The usual way to learn programming is to buy a book or to read tutorials/HOWTOs on the web. There is however a problem: Most of them are so outdated such that the descriptions given in them often do not work as expected. You will come across this problem. For this reason, it is important that you know the basics behind the scenes in order to understand error messages you will encounter during your tries. If you, for example, search for some basic code for displaying some basic user interface, it is not unlikely that the example you find will not compile since the library function names have changed. 

The solution to this problem is to search for tutorials for the version of the respective library that is currently up-to-date and to use the official documentation, whenever possible, and, to learn how to identify the source of your problems. We will do that here. Note that this tutorial will, at some time, also be out of date.

On the other hand, you also have an easier time in Linux in some respects: Libraries can be installed using the package manager, saving you the work to download them, storing them to some well-defined location. You also do not have to download a compiler or even choose one: It suffices to be able to handle the GNU compiler. Everyone is using it anyway.

When it comes to integrated development environments (IDE), however, things change again: You will hardly find any useful information on how to, for example, use some library in the IDE you have chosen. The reason is that the makers of the libraries are normally using different tools than the users: Since there are so many choices in Linux, chances are slim that both parties are using the same tools. Therefore, in most of the cases, only instructions for using from the command line/terminal are given and it left to the user how to integrate the libraries into their environment. This situation even becomes worse when different people work on the same project using different tools. But no worry, we will explain a way around that problem here!

============================================
3. Basic installation
============================================
Before we start, you will have to make sure that the GNU compiler collection and the basic development libraries are installed on your system. In Ubuntu, that's simple: Type "sudo apt-get install build-essential" in the terminal, give your password (You might have to use a different user, though, if yours does not have sudo-rights. If you are not the administrator of the computer your are working on, ask yours to install the build-essential package if this is not already the case).

Then we can try to see if it works correctly:
[LIST]
[*] Create a directory (e.g. /home/me/firststeps)
[*] Go into that directory in the terminal ("cd /home/me/firststeps")
[*] Start an editor ("gedit first_try.cpp")
[*] Type in a basic program:

[PHP]
#include <iostream>

int main(int argc, char **argv) {
	std::cout << "Hello world!\n";
	return 0;
}
[/PHP]
[*] Save and close the editor.
[*] Compile & link it in one step using "g++ -o first_try first_try.cpp". "g++" is the name of the compiler, the option "-o first_try" tells the compiler that it should name the output "first_try". The list of source files is usually given after the option list.
[*] Run it by typing "./first_try". As we have told the compiler to call the resulting program "first_try", it should be there. In Linux, to execute a program from the current directory, you have to explicitly refer to the current directory, thus the "./".
[/LIST]

You should see the famous hello world message. You've just made your first program. Congratulations. If it did not work, search in the Ubuntu forums for possible reasons using the error message you've got. If you want to program in C instead, try the "gcc" command instead of the "g++" command (and use a C hello world program). 

============================================
4. Compiling & Linking 
============================================
You might have made projects containing multiple source files. The reasons for splitting your programs in multiple such files is sound: You normally only change parts of your project, so by splitting it up, you only need to recompile the parts you have changed. Apart from that, it often improves the overview of your project. In Windows, the IDE took care of compiling all these files into one big program (Note that apart from programs, you also might want to make libraries. This is also fine, but we will restrict ourselves to programs for the time being. You should be able to compile them first). Here, you should consider this to be your responsibility. This is because there are dozens of ways how to do this. 

First of all, we repeat some basics. The compiler is a program that takes a C/C++ source file and compiles it into a so-called object file containing machine-dependent code that does what you described in your source file. Object files contain the function/variable/object definitions given in the source file. Here is an example. Create a file "uno.cpp" with the following source:
[PHP]
void hello();

int main(int argc, char **argv) {
	hello();
	return 0;
}
[/PHP]
It contains a declaration of a function "hello" which is then used in the main function. Now try to build a program from it ("g++ -o uno uno.cpp"). You will get an "undefined reference" error. This is because we have used a function that we did not define. We just declared that it exists somewhere. On the other hand, we define the main function in the text, as we give an implementation for it. Keep in mind the differences between declarations and definitions! Now try something else: "g++ -c uno.cpp". You will see that it works! Note that you have only compiled (this is what the "-c" stands for) the source file, thus you did not receive an executable program, but rather an object file called "uno.o", which, by itself is not of any use. Now think about how you would make a whole program out of what you have so far. Well, actually, there is only an implementation for the "hello" function missing, so it should be possible to complete the program accordingly. So we just try this now. Create a new file called "dos.cpp" and fill it with an implementation of the hello function:
[PHP]
#include <iostream>

void hello() {
	std::cout << "Hello world!\n";
}
[/PHP]
Now compile it as well: "g++ -c dos.cpp". Works well, right? However, you do not have a program yet. Why this? Because you only have a bunch of object files. You still need to lump them together to a program. This is done by the linker: It takes the object files, connects the links between them and produces an executable. We again use the command "g++" for it - This is something that I personally think is not so good about the GNU compiler suite: Since you use the same command for everything, you don't see explicitly what you are just doing. For linking, you just use the "g++" command and supply it with a list of object files you want to make your program of. So we try "g++ -o second_try uno.o dos.o". And, voila, you get an executable called "second_try". And it works!

By now you should know that for making your program, you will need to compile all source files and link the object files together. You can refer to functions in other source files if you declared them before using them. In fact, it is normally common to declare them once in a header file (.h) and to include this header file in each source file (if needed). For simplicity, we did not do it in this example. Also note that we can do both steps at once by invoking "g++ -o second_try uno.cpp dos.cpp". In this case, the "g++" command will automatically invoke the compiler and linker for both source files. Now you might wonder why to even bother with splitting the steps then?

Assume that you have a big project. It would be very cumbersome to do recompile all ~200 .cpp files every time you change something. In fact, it would be nice if the computer kept track of which files have been changed and just recompiles these. That's pretty much precisely the task of a "Make" utility.

There are many make utilities to choose from: The classical GNU make, Scons, QMake, CMake and some more. There are also tools doing more sophisticated stuff, like the "autotools", which, for example, examine your computer before compiling to find out some parameters which are then used in the compilation process (Example: An audio player program can examine the computer on which codecs are installed and then compiles with support for precisely these). The GNU make utility is a well-used one, but for simplicity, we will use "qmake" here. Mainly because it's easy. And it works. We cover this in the next section. QMake is part of a library called "QT" that contains a lot of goodies for GUI & network programming. In fact, it contains functions for pretty much everything. But for the time being, we will only use the QMake tool.

============================================
5. QMake
============================================
We start by installing the tool: "sudo apt-get install qt4-qmake". Then, we create a so-called project file containing information about our project. Open up an editor, add the following lines:
```

# QMake Build file
TEMPLATE = app console
QT -= gui core
TARGET = third_try

SOURCES += uno.cpp \
  dos.cpp

```
The first line is a comment. When writing a project file, commands start with "#". The second line tells QMake that we want to build a console application. As the QMake utility is part of the "QT4" library distribution and we do not want to use it right now, we have to tell qmake not to include some default parts of that library. That's what the first line is for. And then, there is a list of source files that need to be considered in the project. the "\" character marks a line continuation, so the utility does not consider the source list to end after uno.cpp. Actually, what this project file does is to modify some "variables" which have certain meanings. More details can be found in the QMake documentation. For the time being, all we need is to be able to add source files. And that's easy. Save the project file under "Hello.pro". Now type "qmake Hello.pro" in the terminal in order to make a make file for the GNU make utility from it (in fact, QMake just converts these project files to "native" makefile). Finally, hit "make" to actually start building the program. 

You will see the commands that are actually executed. You will notice that you actually receive warnings for "uno.cpp" as the parameters in the main function are not being used. This is because QMake adds some compiler option telling the compiler to produce more warnings by default. This is actually a good thing as it is likely to point out problems with your code.

============================================
6. Using an IDE - Basics.
============================================
Ok, so let's import our "project" into kdevelop. I would always suggest to first create some source file and a project file and then importing it, as this way, the project "stays in your own style". The default settings for new projects in kdevelop are not always what your want. So, first of all, install the KDevelop package (kdevelop-kde4). Then, start it up and choose "Project->Import existing". Select your project directory and hit OK. It will choose "QT C++ application (QMake based) as type and that's ok. Now try changing the main function in uno.cpp (click onto the file name and start editing) by, for example, duplicating the call to "hello". Choose "Build->Build" and see the IDE in action. It should report the success. Now, before you may run your application, you have to tell the IDE the name of the executable. Go to "Project->Project Options", go to "Run Options", check the main program check box and select the "third_try" executable. After hitting OK, you can also use the "Project->Execute main program" menu entry. Now you can work in the IDE. Note that it adds files to the "sources" list in the project file automatically if you choose the "File->New" menu entry.

============================================
7. Using an IDE - Debugging.
============================================
When it comes to debugging, things get slightly more complicated. In fact, you cannot debug the executable we are building right now very well. The reason is that it does not contain debugging information, so the debugger program cannot tell us much about the execution. The solution is to add the line "CONFIG += debug" to the project file. Then choose "Build->Clean Project" (No, QMake won't do this automatically for us). By the way: Whenever the IDE asks you whether to reload the project file, choose "Reload". It does not expect us to modify it directly, but that's fine anyway. Then build it again. Now set a break-point in the main function (right click onto the left border of the source code text view and choose "breakpoint") and choose "Debug->Start" from the menu. The program will stop at the break-point and you will be able to step into or over other functions (try it with the hello function!) and to inspect local variables (which, however, with complex data types does not work very well).

============================================
8. Using libraries
============================================
..... TODO!

============================================
9. Finally, .....
============================================
Please post corrections below this post, I will add them to the text when I've got time for that!

---

### Post by Gorgamel on 2009-10-22
Good tutorial.
Learned some minor things I had no idea about :)

---

