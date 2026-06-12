---
title: "C++ why won't this text book sample code run in Linux."
date: 2010-03-14
forum: Programming Talk
---

### Post by Jonas thomas on 2010-03-14
I've been running through the sample code of all the text sample provided on the cd and this is the first time, I've had an issue running in Linux.
I don't understand the issue..
Sample code is from Starting out with C++ from Control Structure through Objects sixth Edition by Tony Gaddis. Program 7-10

```

// This program stores, in an array, the hours worked by
// employees who all make the same hourly wage.
#include <iostream>
#include <iomanip>
using namespace std;

int main()
{
   const int NUM_EMPLOYEES = 5;
   int hours[NUM_EMPLOYEES];
   double payrate;

   // Input the hours worked.
   cout << "Enter the hours worked by ";
   cout << NUM_EMPLOYEES << " employees who all\n";
   cout << "earn the same hourly rate.\n";
   for (int index = 0; index < NUM_EMPLOYEES; index++)
   {
      cout << "Employee #" << (index + 1) << ": ";
      cin >> hours[index];
   }

   // Input the hourly rate for all employees.
   cout << "Enter the hourly pay rate for all the employees: ";
   cin >> payrate;

   // Display each employee's gross pay.
   cout << "Here is the gross pay for each employee:\n";
   cout << fixed << showpoint << setprecision(2);
   for (index = 0; index < NUM_EMPLOYEES; index++)
   {
      double grossPay = hours[index] * payrate;
      cout << "Employee #" << (index + 1);
      cout << ": $" << grossPay << endl;
   }
   return 0;
}

```

When I compile I get this.
```

----------Build Started--------
"make"  -j 2 -f "Chapter7_wsp.mk"
----------Building project:[ Pr7-10 - Debug ]----------
g++ -c  "/home/jonas/.codelite/CppClass/Chapter7/SampleCode/Pr7-10/Pr7-10.cpp" -g  -o ./Debug/Pr7-10.o "-I." "-I." 
/home/jonas/.codelite/CppClass/Chapter7/SampleCode/Pr7-10/Pr7-10.cpp: In function ‘int main()’:
/home/jonas/.codelite/CppClass/Chapter7/SampleCode/Pr7-10/Pr7-10.cpp:30: warning: name lookup of ‘index’ changed
<built-in>:0: warning:   matches this ‘char* index(const char*, int)’ under ISO standard rules
/home/jonas/.codelite/CppClass/Chapter7/SampleCode/Pr7-10/Pr7-10.cpp:17: warning:   matches this ‘index’ under old rules
/home/jonas/.codelite/CppClass/Chapter7/SampleCode/Pr7-10/Pr7-10.cpp:30: error: assignment of function ‘char* index(const char*, int)’
/home/jonas/.codelite/CppClass/Chapter7/SampleCode/Pr7-10/Pr7-10.cpp:30: error: cannot convert ‘int’ to ‘char*(const char*, int)’ in assignment
/home/jonas/.codelite/CppClass/Chapter7/SampleCode/Pr7-10/Pr7-10.cpp:30: error: ISO C++ forbids comparison between pointer and integer
/home/jonas/.codelite/CppClass/Chapter7/SampleCode/Pr7-10/Pr7-10.cpp:30: error: ISO C++ forbids incrementing a pointer of type ‘char* (*)(const char*, int)’
/home/jonas/.codelite/CppClass/Chapter7/SampleCode/Pr7-10/Pr7-10.cpp:30: error: lvalue required as increment operand
/home/jonas/.codelite/CppClass/Chapter7/SampleCode/Pr7-10/Pr7-10.cpp:32: error: invalid types ‘int [5][char*(const char*, int)]’ for array subscript
/home/jonas/.codelite/CppClass/Chapter7/SampleCode/Pr7-10/Pr7-10.cpp:33: warning: pointer to a function used in arithmetic
make[1]: *** [Debug/Pr7-10.o] Error 1
make: *** [All] Error 2
----------Build Ended----------
0 errors, 0 warnings

```
Hmm...index is not a reserved word... This has me befuddled...

---

### Post by LKjell on 2010-03-14
on the second for loop at line 30 have for ([COLOR="Red"]int[/COLOR] index ...

---

### Post by Jonas thomas on 2010-03-14
```

// This program stores, in an array, the hours worked by
// employees who all make the same hourly wage.
#include <iostream>
#include <iomanip>
using namespace std;

int main()
{
   const int NUM_EMPLOYEES = 5;
   int hours[NUM_EMPLOYEES];
   double payrate;

   // Input the hours worked.
   cout << "Enter the hours worked by ";
   cout << NUM_EMPLOYEES << " employees who all\n";
   cout << "earn the same hourly rate.\n";
   for (int iindex = 0; iindex < NUM_EMPLOYEES; iindex++)
   {
      cout << "Employee #" << (iindex + 1) << ": ";
      cin >> hours[iindex];
   }

   // Input the hourly rate for all employees.
   cout << "Enter the hourly pay rate for all the employees: ";
   cin >> payrate;

   // Display each employee's gross pay.
   cout << "Here is the gross pay for each employee:\n";
   cout << fixed << showpoint << setprecision(2);
   for (int index = 0; index < NUM_EMPLOYEES; index++)
   {
      double grossPay = hours[index] * payrate;
      cout << "Employee #" << (index + 1);
      cout << ": $" << grossPay << endl;
   }
   return 0;
}

```
Ok... Now this works... I think the issue is with scope. 
I wonder if this is a flat out bug... Or a difference between how MS and g++ compile?

---

### Post by Jonas thomas on 2010-03-14
Ok... I just figured out what the issue was...
The source code printed out in the book was correct. (with the int in the second loop)
The source code provided on the CD is missing it, which result in the error.
Duhh....

---

### Post by LKjell on 2010-03-14
Time to toss the cd away. You learn to actually write the code rather than read it. Programming is all about writing. Beside you also get the finger exercise.

---

### Post by Jonas thomas on 2010-03-14
> **LKjell said:**
> Time to toss the cd away. You learn to actually write the code rather than read it. Programming is all about writing. Beside you also get the finger exercise.
I totally agree with you up to a point.  I like to skim through the text book and then run the code. I make it a point to hack up the code to enhance it or break it to see if I understand the underlying concepts.

Writing out the same code again and again might be  good typing exercise but doesn't enhance my knowledge. I started out just setting up one project and rewriting the code running through the examples.. Some of the examples are so lame.. I got bored.. I wound up writing an app(which is still a work in project) which would generate the project files so I can rip through the examples.  
As I said, I agree with you, but this works for me.

---

### Post by MadCow108 on 2010-03-14
> **Jonas thomas said:**
> [CODE]
Ok... Now this works... I think the issue is with scope. 
I wonder if this is a flat out bug... Or a difference between how MS and g++ compile?

the reason is that initializations in for loops was not standardized before C99
so compiler writers could choose to implement it as an extension however they wished.
Some choose that such an initialization has scope only inside the loop, others choose that it had scope outside of the loop.

the C99 standard now defines it like gcc did: only in scope inside the loop
ms seemingly choose the other way

So if you want to write C89 code, don't use these kind of initializations to be portable

---

### Post by jpkotta on 2010-03-15
> **MadCow108 said:**
> So if you want to write C89 code, don't use these kind of initializations to be portable

OP is writing C++.  IIRC, declaring in the loop was always legal in C++.

---

### Post by MadCow108 on 2010-03-15
I'm sorry I missed that its c++
I guess its then related to the fact that C++ did not have a standard before 1998 and the compiler ms uses keeps that non conforming behavior as default for backward compatibility
(or of course the textbook example is just wrong)

---

