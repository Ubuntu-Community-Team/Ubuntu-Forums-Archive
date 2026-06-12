---
title: "C++ Problem with passing arrays as arguments"
date: 2009-11-17
forum: Programming Talk
---

### Post by jdunn on 2009-11-17
I'm fairly new to C++ and haven't gotten used to memory allocation yet.  I wrote a small program that reads a file (one-line at a time) as a string and parses data from it into 2-dimensional arrays of different sizes.  Then another function (I call it "foo" here) takes each array as an argument and performs calculations.  The program works as expected when compiling and running with GNU G++ in linux.  However, the same simple program crashes or produces weird results with MingW or Visual C++ (in Vista).  I suspect I'm doing something wrong with the memory allocation here.  help.

```

#include <iostream>
#include <fstream>
#include <string>
#include <sstream>
using namespace std;

class Assemble
{
public:
    string s;       
    int lnum;       
	
    
    int** A;        
    int** T;    

    void readfile()
    {
        ifstream in("input.txt");
        getline(in, s);         
        stringstream ss(s);
        ss >> lnum;
								
        A = new int*[3];
        T = new int*[3];
       
        for (int j = 0; j <= lnum; j++)
            A[j] = new int[3];              
        for (int j = 0; j < lnum; j++)
            T[j] = new int[3];   

                parser(lnum, A, 1);
                parser(lnum, A, 2);
                parser(lnum - 1, T, 1);
                parser(lnum - 1, T, 2);

                foo(lnum, A, 1);
                foo(lnum, A, 2);
                foo(lnum - 1, T, 1);
                foo(lnum - 1, T, 2);
    }

    void parser(int arsize, int** GenAr, int i)
    {
       // data gets parsed from string and stored in array
    }

    void foo(int arsize, int** GenAr, int i)
    {
       // crash occurs when calling this function
    }

```

---

### Post by b&amp;m on 2009-11-17
Try with

for (int j = 0; j < lnum; j++)

instead of

for (int j = 0; j <= lnum; j++)

;)

---

### Post by jdunn on 2009-11-17
> **b&m said:**
> Try with

for (int j = 0; j < lnum; j++)

instead of

for (int j = 0; j <= lnum; j++)

;)

The Array A is has one more column than Array T...Two two-dimensional arrays of different sizes.  This is also why the function calls use slightly different arguments.  Also, I'm not using index 0 in the arrays...I'm using 1 to lnum for A and 1 to (lnum - 1) for T.

---

### Post by b&amp;m on 2009-11-17
Try

foo(lnum, A, 2);

instead of

foo(lnumm, A, 2);

---

### Post by jdunn on 2009-11-17
> **b&m said:**
> Try

foo(lnum, A, 2);

instead of

foo(lnumm, A, 2);

Oops.  Thanks.  However, that was not an error in my actual code.  It was an error in my edit after cut&paste.  Should be fixed now.

---

### Post by Arndt on 2009-11-17
> **jdunn said:**
> The Array A is has one more column than Array T...Two two-dimensional arrays of different sizes.  This is also why the function calls use slightly different arguments.  Also, I'm not using index 0 in the arrays...I'm using 1 to lnum for A and 1 to (lnum - 1) for T.

Maybe you should run the program with 'valgrind'. It shows all memory errors, not only those which immediately cause a crash.

---

### Post by Arndt on 2009-11-17
> **jdunn said:**
> I'm fairly new to C++ and haven't gotten used to memory allocation yet.  I wrote a small program that reads a file (one-line at a time) as a string and parses data from it into 2-dimensional arrays of different sizes.  Then another function (I call it "foo" here) takes each array as an argument and performs calculations.  The program works as expected when compiling and running with GNU G++ in linux.  However, the same simple program crashes or produces weird results with MingW or Visual C++ (in Vista).  I suspect I'm doing something wrong with the memory allocation here.  help.

```

#include <iostream>
#include <fstream>
#include <string>
#include <sstream>
using namespace std;

class Assemble
{
public:
    string s;       
    int lnum;       
	
    
    int** A;        
    int** T;    

    void readfile()
    {
        ifstream in("input.txt");
        getline(in, s);         
        stringstream ss(s);
        ss >> lnum;
								
        A = new int*[3];
        T = new int*[3];
       
        for (int j = 0; j <= lnum; j++)
            A[j] = new int[3];              
        for (int j = 0; j < lnum; j++)
            T[j] = new int[3];   

                parser(lnum, A, 1);
                parser(lnum, A, 2);
                parser(lnum - 1, T, 1);
                parser(lnum - 1, T, 2);

                foo(lnum, A, 1);
                foo(lnum, A, 2);
                foo(lnum - 1, T, 1);
                foo(lnum - 1, T, 2);
    }

    void parser(int arsize, int** GenAr, int i)
    {
       // data gets parsed from string and stored in array
    }

    void foo(int arsize, int** GenAr, int i)
    {
       // crash occurs when calling this function
    }

```

Are you sure the crash occurs when foo is called, and not inside foo? Can you remove some foo calls and still get the crash?

---

### Post by jdunn on 2009-11-17
> **Arndt said:**
> Maybe you should run the program with 'valgrind'. It shows all memory errors, not only those which immediately cause a crash.

sounds interesting.  I'll keep it in mind but installing extra software is not going to be one of my first options to fix this.  Is GenAr not getting deallocated?  I figured once outside the function, GenAr is out of scope.

---

### Post by jdunn on 2009-11-17
There is info on the web and my book about dynamic memory allocation for arrays but none for multi-dim arrays.  I had a friend look at my code and point out the errors.  It is now fixed.  This is how the code reads now:

```
							
        A = new int*[3];
        T = new int*[3];
       
        for (int j = 0; j <= 2; j++)
            A[j] = new int[lnum];              
        for (int j = 0; j <= 2; j++)
            T[j] = new int[lnum - 1]; 

```

---

### Post by dwhitney67 on 2009-11-17
> **jdunn said:**
> There is info on the web and my book about dynamic memory allocation for arrays but none for multi-dim arrays.  I had a friend look at my code and point out the errors.  It is now fixed.  This is how the code reads now:

```
							
        A = new int*[3];
        T = new int*[3];
       
        for (int j = 0; j <= 2; j++)
            A[j] = new int[lnum];              
        for (int j = 0; j <= 2; j++)
            T[j] = new int[lnum - 1]; 

```
It's too bad your friend was not able to point out that you could combine the initialization steps.
```

for (int j = 0; j < 3; ++j)
{
   A[j] = new int[lnum];
   T[j] = new int[lnum - 1];
}

```
Also, too bad that your friend could not have persuaded you to use variables names that are more descriptive.

---

### Post by jdunn on 2009-11-18
> **dwhitney67 said:**
> It's too bad your friend was not able to point out that you could combine the initialization steps.
```

for (int j = 0; j < 3; ++j)
{
   A[j] = new int[lnum];
   T[j] = new int[lnum - 1];
}

```
Also, too bad that your friend could not have persuaded you to use variables names that are more descriptive.

A)  I already cleaned up my code, just not for you.
B)  I use plenty of comments when variable names aren't so "descriptive" but I often omit them when posting my code on a forum.

---

### Post by TennTux on 2009-11-19
In your original code you had:
```

        A = new int*[3];
        T = new int*[3];
       
        for (int j = 0; j <= lnum; j++)
            A[j] = new int[3];              
        for (int j = 0; j < lnum; j++)
            T[j] = new int[3];   

```
The initialization of A and T suggests that A and T have three elements each, however, you loop from 0 to lnum which suggests A has lnum+1 elements and T has lnum elements. And each element is an array of three elements Thus you really wanted something like:
```

	A = new int*[lnum+1] ;
	T = new int*[lnum] ;
        for (int j = 0; j <= lnum; j++)
            A[j] = new int[3];              
        for (int j = 0; j < lnum; j++)
            T[j] = new int[3];   

```
However, dwhitney67 has correctly provided the complement where A and T each have exactly 3 elements and each element is an array of lnum+1 or lnum elements. As below:
```

	A = new int*[3] ;
	T = new int*[3] ;
        for (int j = 0; j < 3; j++)
            A[j] = new int[lnum+1];              
        for (int j = 0; j < 3; j++)
            T[j] = new int[lnum];   

```
Which one is correct depends on what you are trying to do.

On the larger issue you may want to think about using a typedef to simplify things. For example:
```

typedef int* SubArray ;
SubArray*	A = new SubArray[3];
SubArray*	T = new SubArray[3] ;

```
or possibly
```

typedef int[3] SubArray3 ;
SubArray3*	A = new SubArray[lnum+1] ;
SubArray3*	T = new SubArray[lnum] ;

```
By using the typedef it starts you thinking of the SubArray as its own type and can help keep the parts separate in your mind. But that's my opinion. :)

---

