---
title: "Compiled in Terminal. Will not open from Desktop."
date: 2010-10-22
forum: Packaging and Compiling Programs
---

### Post by adam.bevelhymer on 2010-10-22
Hi,

I am a recent Ubuntu convert who is trying to get into a little programming in C++. I have successfully compiled and run a short program named "fibonacci.cpp" using g++ from the terminal.

     g++ fibonacci.cpp -o fibonacci
     ./fibonacci

The program runs flawlessly from the terminal, but when I navigate to it from the desktop, I find the file, double-click it, and nothing happens. I have the box under Properties > Permissions > Allow Executing File checked. Is there some code I need to add at the beginning of my program to cause a Terminal window to open? Do I need to use an IDE to compile rather than the Terminal? I would really like it if I could simply click on the icon to make it run.

Here's a copy of my code:

#include <iostream>
using namespace std;

int main()
{
cout << "This program produces the Fibonacci series to a specified number of values.\n";

cout << "Specify number of values (must be > 2):";
unsigned int number;
cin >> number;
	
unsigned int value1=0;
unsigned int value2=1;
unsigned int value3;
	
cout << value1 << ", "<< value2;
	
for (int n=0; n<number-2; n++){
	value3 = value1 + value2;
	cout << ", " << value3;
	value1 = value2;
	value2 = value3;}	

cout << "\n";

return 0;
}
 
I will appreciate any help I get!!!

---

### Post by GregBrannon on 2010-10-22
How do you know it's not running and you just can't see it?  If you run it from the GUI interface but the program only sends output to the terminal, you might not see anything happen in the GUI.

BTW - these kind of programming questions are best in the Programming Talk sub-forum.

---

### Post by adam.bevelhymer on 2010-10-22
Okay, I have posted it there as well. Thank you for your advice.

---

