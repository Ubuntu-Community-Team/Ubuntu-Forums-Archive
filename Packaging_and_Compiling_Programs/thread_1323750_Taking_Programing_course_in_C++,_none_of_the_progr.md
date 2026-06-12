---
title: "Taking Programing course in C++, none of the programs I write compile"
date: 2009-11-12
forum: Packaging and Compiling Programs
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
gcc  -MMD "/home/brandon/Projects/Hello World/Hello World/starter.c" -g -O0 -DDEBUG -DMONODEVELOP -I"/home/brandon/Projects/Hello World/Hello World/.prec/Debug"  -c -o "/home/brandon/Projects/Hello World/Hello World/bin/Debug/starter.o"
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

### Post by SevenMachines on 2009-11-12
you should post this question to the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39"), theres a few coding problems in your example rather than compiling/packaging issue. at a quick glance, your using a c compiler,gcc, not a c++ compiler, g++. and you're using the standard namespace with things like cout without specifying it either with std:: or using namespace std; and your main function should return int in the form its in. but you'll get more advice in the programming forum on language

---

### Post by Elfy on 2009-11-12
Closed - duplicate [http://ubuntuforums.org/showthread.php?t=1323786](http://ubuntuforums.org/showthread.php?t=1323786)

---

