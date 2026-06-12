---
title: "Taking Programing course in C++, none of the programs I write compile"
date: 2009-11-12
forum: Programming Talk
---

### Post by Brando753 on 2009-11-12
Ive been trying to write programs in C++ for a programming class, rather then using the windows application, however, the programs that compile fine in windows do not in ubuntu. Tried both Monodevelop & MinGW for linux. Here is a copy of the code.

//Hello World

#include <iostream>

void main()
{
//Declare and initialize variables
short num = 0;
short numCubed = 0;
//enter input item

cout << "enter a number between 1 and 20: ";
cin >> num;

//call function to cube number
numCubed = cube(num);

//display output item
cout << "the cube is " << numCubed << end1;
}
//end of main function

Tried both <iostream.h> and <iostream> and get these errors

Compiling source to object files
gcc -MMD "/home/brandon/Projects/Hello World/Hello World/starter.c" -g -O0 -DDEBUG -DMONODEVELOP -I"/home/brandon/Projects/Hello World/Hello World/.prec/Debug" -c -o "/home/brandon/Projects/Hello World/Hello World/bin/Debug/starter.o"
/home/brandon/Projects/Hello World/Hello World/starter.c:4:20: warning: iostream: No such file or directory
/home/brandon/Projects/Hello World/Hello World/starter.c: In function ‘main’:
/home/brandon/Projects/Hello World/Hello World/starter.c:13: error: ‘cout’ undeclared (first use in this function)
/home/brandon/Projects/Hello World/Hello World/starter.c:13: error: (Each undeclared identifier is reported only once
/home/brandon/Projects/Hello World/Hello World/starter.c:13: error: for each function it appears in.)
/home/brandon/Projects/Hello World/Hello World/starter.c:14: error: ‘cin’ undeclared (first use in this function)
/home/brandon/Projects/Hello World/Hello World/starter.c:20: error: ‘end1’ undeclared (first use in this function)
Build complete -- 5 errors, 0 warnings

If someone could tell me what I did wrong, and what the differences between programming in windows vs Ubuntu is. Why if it works in windows dosent it work in ubuntu, its the same language right?

Help Anyone? Thanks in advance.

---

### Post by samjh on 2009-11-12
You're using the wrong compiler.  You should be using g++, since the code you're writing is C++.

Also make sure you have the build-essential package installed:
```
sudo apt-get install build-essential
```

---

### Post by korvirlol on 2009-11-12
you will either have to add:

> using namespace std;or user std::cout and std::cin to use the iostream library

end1 should be endl (end "L")

---

### Post by Brando753 on 2009-11-12
Alright I see that, I said new C file not C++ file in Monodevelop copying and pasting the same code in a c++ file builds fine, however it wont let me run, debug, or build a package.


**Build results:**

Building: test (Debug)

Building Solution test

Building: test (Debug)
Performing main compilation...

Precompiling headers

Compiling source to object files

Generating binary "test" from object files
gcc -o "/home/brandon/Projects/test/test/bin/Debug/test"   
gcc: no input files
Build complete -- 0 errors, 0 warnings

---------------------- Done ----------------------

Build successful.

**Run Error**

Cannot execute "test". ApplicationName='/home/brandon/Projects/test/test/bin/Debug/test', CommandLine='', CurrentDirectory='/home/brandon/Projects/test/test/bin/Debug'.

**Package Error**

Creating packages

Package: Archive of Binaries

Building: test (Debug)
Performing main compilation...

Precompiling headers

Compiling source to object files

Generating binary "test" from object files
gcc -o "/home/brandon/Projects/test/test/bin/Debug/test"   
gcc: no input files
Build complete -- 0 errors, 0 warnings

Package creation failed. /home/brandon/Projects/test/test/bin/Debug/test does not exist

Any ideas?

---

### Post by Bodsda on 2009-11-12
> **Brando753 said:**
> 

Generating binary "test" from object files
gcc -o "/home/brandon/Projects/test/test/bin/Debug/test"   
gcc: no input files
Build complete -- 0 errors, 0 warnings

Package creation failed. /home/brandon/Projects/test/test/bin/Debug/test does not exist

Any ideas?

This section looks odd. I am guessing its an IDE or something else that is initiating this compilation. It is not specifying an input source file, just an output file and as there is no input, there cant really be any output. I suggest you run the compilation yourself

```

gcc inputfile -o outputfile

```

---

### Post by Brando753 on 2009-11-12
> **korvirlol said:**
> you will either have to add:

or user std::cout and std::cin to use the iostream library

What do you mean? Book says nothing of std::

---

### Post by Brando753 on 2009-11-12
> **Bodsda said:**
> This section looks odd. I am guessing its an IDE or something else that is initiating this compilation. It is not specifying an input source file, just an output file and as there is no input, there cant really be any output. I suggest you run the compilation yourself

```

gcc inputfile -o outputfile

```

Im thinking its the compiler same problem in the MinGW for linux and when a made an empty file pasted the code in it and named it Test.cpp

Code from Terminal

brandon@brandon-laptop:~/Desktop$ gcc Test.ccp -o outputfile
gcc: Test.ccp: No such file or directory
gcc: no input files
brandon@brandon-laptop:~/Desktop$ g++ Test.ccp -o outputfile
g++: Test.ccp: No such file or directory
g++: no input files
brandon@brandon-laptop:~/Desktop$ ls
Binary          fakeNET11.reg                      new file~
config.php      History homework due thursday.odt  Porgraming Class Work
D&D4eicons.ttf  Laptop Drop Folder                 Programing Class
Direct3D.reg    Login                              Test.cpp
Direct3D.reg~   Login~                             Test.cpp~

---

### Post by korvirlol on 2009-11-12
the errors from your compiling say it cant find the operations cout and cin, this is because it is looking in your default namespace, which they are defined in std.

You can use the functions from using namespace std; or prefixing them with std::


to compile your program:

> sudo apt-get install g++

> g++ -o outputname inputname.cc

---

### Post by Brando753 on 2009-11-12
brandon@brandon-laptop:~/Desktop$ g++ '/home/brandon/Desktop/Test.cpp'
/home/brandon/Desktop/Test.cpp:8: error: &#8216;::main&#8217; must return &#8216;int&#8217;
/home/brandon/Desktop/Test.cpp: In function &#8216;int main()&#8217;:
/home/brandon/Desktop/Test.cpp:19: error: &#8216;cube&#8217; was not declared in this scope

---

### Post by korvirlol on 2009-11-12
seems like progress, but just posting your errors doesnt exactly mean anything....


generally, a program running in linux on the terminal must return an integer value. so, change your programs definition of main to:

```
int main()
```
you then of  course must return something at the end of your program, typically 0

you will also have to create your "cube" subroutine before you can call it on your main program

---

### Post by Bodsda on 2009-11-12
> **Brando753 said:**
> brandon@brandon-laptop:~/Desktop$ g++ '/home/brandon/Desktop/Test.cpp'
/home/brandon/Desktop/Test.cpp:8: error: &#8216;::main&#8217; must return &#8216;int&#8217;
/home/brandon/Desktop/Test.cpp: In function &#8216;int main()&#8217;:
/home/brandon/Desktop/Test.cpp:19: error: &#8216;cube&#8217; was not declared in this scope

This is a coding issue. The first error relates to the main function which I think but am not sure, has to return an int, so   
```

int main()
{
    <code>
    return 0;
}

```The second line also relates to this problem. And the third line refers to the 'cube(num)' section. You never define cube(), perhaps you are missing an include?

Also, your couts and cins will all make the program fall over because they are also not defined. Add 'using namespace std;' underneath your includes.

---

### Post by Brando753 on 2009-11-12
Code So Far:


//Hello World
//This program uses a programmer defined header that is locatted in a diffren folder

#include <iostream>

using namespace std; 

int main()
{
    <code>
    return 0;
}

void main()
{
	//Declare and initialize variables
	short num = 0;
	short numCubed = 0;
	//enter input item
	
cout << "enter a number between 1 and 20: ";
cin >> num;

//call function to cube number
numCubed = cube(num);

//display output item 
cout <<"the cube is " <<numCubed << endl;
}
//end of main function


Errors So Far:

/home/brandon/Desktop/Test.cpp: In function &#8216;int main()&#8217;:
/home/brandon/Desktop/Test.cpp:10: error: expected primary-expression before &#8216;<&#8217; token
/home/brandon/Desktop/Test.cpp:10: error: &#8216;code&#8217; was not declared in this scope
/home/brandon/Desktop/Test.cpp:11: error: expected primary-expression before &#8216;return&#8217;
/home/brandon/Desktop/Test.cpp:11: error: expected &#8216;;&#8217; before &#8216;return&#8217;
/home/brandon/Desktop/Test.cpp: At global scope:
/home/brandon/Desktop/Test.cpp:14: error: &#8216;::main&#8217; must return &#8216;int&#8217;
/home/brandon/Desktop/Test.cpp: In function &#8216;int main()&#8217;:
/home/brandon/Desktop/Test.cpp:14: error: redefinition of &#8216;int main()&#8217;
/home/brandon/Desktop/Test.cpp:8: error: &#8216;int main()&#8217; previously defined here
/home/brandon/Desktop/Test.cpp:25: error: &#8216;cube&#8217; was not declared in this scope

---

### Post by korvirlol on 2009-11-12
stay in school ;P

---

### Post by Arndt on 2009-11-12
> **Brando753 said:**
> Code So Far:


//Hello World
//This program uses a programmer defined header that is locatted in a diffren folder

#include <iostream>

using namespace std; 

int main()
{
    <code>
    return 0;
}

void main()
{
	//Declare and initialize variables
	short num = 0;
	short numCubed = 0;
	//enter input item
	
cout << "enter a number between 1 and 20: ";
cin >> num;

//call function to cube number
numCubed = cube(num);

//display output item 
cout <<"the cube is " <<numCubed << endl;
}
//end of main function


Errors So Far:

/home/brandon/Desktop/Test.cpp: In function ‘int main()’:
/home/brandon/Desktop/Test.cpp:10: error: expected primary-expression before ‘<’ token
/home/brandon/Desktop/Test.cpp:10: error: ‘code’ was not declared in this scope
/home/brandon/Desktop/Test.cpp:11: error: expected primary-expression before ‘return’
/home/brandon/Desktop/Test.cpp:11: error: expected ‘;’ before ‘return’
/home/brandon/Desktop/Test.cpp: At global scope:
/home/brandon/Desktop/Test.cpp:14: error: ‘::main’ must return ‘int’
/home/brandon/Desktop/Test.cpp: In function ‘int main()’:
/home/brandon/Desktop/Test.cpp:14: error: redefinition of ‘int main()’
/home/brandon/Desktop/Test.cpp:8: error: ‘int main()’ previously defined here
/home/brandon/Desktop/Test.cpp:25: error: ‘cube’ was not declared in this scope

<code> was not meant as something you should insert literally in your code. Whatever would C++ do with it? It means that you should insert whatever your actual code is at that place, since the important point of the post was the "return 0;" following it.

Wrapping things in < > is common practice to differentiate literal text from named entities of some kind. When available, italics is often used instead.

---

### Post by ac7nj on 2009-11-13
> **Brando753 said:**
> What do you mean? Book says nothing of std::

I had this same problem it turned out the book was old and things had changed the advice posted here shows two differant ways to make it work. 

What Id like to know is how to have found the correct syntax in the first place for <iostream> 

Randy

---

### Post by ac7nj on 2009-11-13
Look at the example you were given

int main()// main is a function with a value if intiger you can tell this because it has "()" after the function name
{
<code>  //write your code here

return 0; //all functions have to return a value if you need them to or not
}



> **Brando753 said:**
> Code So Far:


//Hello World
//This program uses a programmer defined header that is locatted in a diffren folder

#include <iostream>

using namespace std; 

int main()
{
    <code>
    return 0;
}

void main()
{
	//Declare and initialize variables
	short num = 0;
	short numCubed = 0;
	//enter input item
	
cout << "enter a number between 1 and 20: ";
cin >> num;

//call function to cube number
numCubed = cube(num);

//display output item 
cout <<"the cube is " <<numCubed << endl;
}
//end of main function


Errors So Far:

/home/brandon/Desktop/Test.cpp: In function ‘int main()’:
/home/brandon/Desktop/Test.cpp:10: error: expected primary-expression before ‘<’ token
/home/brandon/Desktop/Test.cpp:10: error: ‘code’ was not declared in this scope
/home/brandon/Desktop/Test.cpp:11: error: expected primary-expression before ‘return’
/home/brandon/Desktop/Test.cpp:11: error: expected ‘;’ before ‘return’
/home/brandon/Desktop/Test.cpp: At global scope:
/home/brandon/Desktop/Test.cpp:14: error: ‘::main’ must return ‘int’
/home/brandon/Desktop/Test.cpp: In function ‘int main()’:
/home/brandon/Desktop/Test.cpp:14: error: redefinition of ‘int main()’
/home/brandon/Desktop/Test.cpp:8: error: ‘int main()’ previously defined here
/home/brandon/Desktop/Test.cpp:25: error: ‘cube’ was not declared in this scope

---

### Post by HarrisonNapper on 2009-11-13
```



//Hello World
//This program uses a programmer defined header that is locatted in a diffren folder

#include <iostream>

using namespace std; 

int main()
{
    //Declare and initialize variables
    short num = 0;
    short numCubed = 0;
    //enter input item
    
cout << "enter a number between 1 and 20: ";
cin >> num;

//call function to cube number
numCubed = cube(num);

//display output item 
cout <<"the cube is " <<numCubed << endl;

return 0;
}
//end of main function

```This is your code with the suggested int main() change made. Compare it to your old code and read through the suggestions one more time. It will show you a bit about the nomenclature that people use when they're talking about code.

When you have some free time:
> 
[http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-001Spring-2005/CourseHome/index.htm](http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-001Spring-2005/CourseHome/index.htm)> 
[http://webcast.berkeley.edu](http://webcast.berkeley.edu) might have a more recent set of video lectures.

Lastly, I should note I didn't change anything else in your code; that was a push in the right direction, but we can't write it for you. You still haven't defined cube() either in your program or with a library.

---

### Post by meson2439 on 2009-11-14
Those original codes won't even run on windows.. lol. These codes work on most old compilers (Turbo C++ 4.0 or even lower) that you have at school, but no modern compilers will compile it, not on windows or linux. These older compilers will even compile a *.c files as if it is *.cpp (using iostream in c files) and won't even squeal about it.

---

### Post by dribeas on 2009-11-16
> **korvirlol said:**
> 
generally, a program running in linux on the terminal must return an integer value. so, change your programs definition of main to:

```
int main()
```
you then of  course must return something at the end of your program, typically 0

That has nothing to do with the environment, but rather with the standard. The two possible signatures for the main function (entry point of the application) are:

```

int main(); // ignore arguments
int main( int, char** );

```

In both cases, 'main' is a special function and in particular the only function in the standard that while having a return type is allowed not to return anything. In that case the standard states that it is equivalent to returning 0 at the end of the main function.

Note that, sadly, gcc will allow you to write functions with return type and not returning anything from them, even if the standard states that as an ill-formed program. Up to gcc 4 (I have not tested this particular later than that), even with -Wall that condition was undetected by the compiler and you were required to add -Wreturn-types for the compiler to flag the error (as a warning, but at least tell you)

---

### Post by jujum4n on 2009-11-17
Here is your program compiled and running sans the cin functionality (due to web compiler) [http://codepad.org/AEoxJzbL](http://codepad.org/AEoxJzbL) .
 
You call the function cube on the number but did not define or write the function included in my code is an example on how to define and use a function.

---

### Post by HarrisonNapper on 2009-11-17
Now that you have a pretty good working example, try playing around with the functionality to make it do other things. As you learn more about writing functions, try doing these things using only basic built in functions and arithmetic:

Take the number to an exponent of itself
Square root the number

Well, I probably don't need to list every way to transform numbers, but you get the idea.

Cheers.

---

### Post by ashmew2 on 2009-12-26
you need an IDE for starters lol..how about codeblocks ?

---

