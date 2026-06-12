---
title: "C++ compilation"
date: 2010-09-16
forum: Programming Talk
---

### Post by santanu.csc on 2010-09-16
[SIZE=2]when I compile the following program in Anjuta IDE[/SIZE]

[B][FONT=Courier New][SIZE=2]#include<iostream>
class person
{
char name[30];
int age;
public:
void getdata(void);
void display(void);
};
void person : :  getdata(void)
{
cout << "Enter  Name";
cin >> name;
cout << "Enter  age";
cin >> age;
}
void person : : display(void)
{
cout << "\nName : "<< name;
cout << "\nAge : "<<age;
}
int main()
{
person p;
p.getdata();
p.display();
return 0;
}
[/SIZE][/FONT][/B]
[SIZE=2]Then the following error Occour[/SIZE]

[SIZE=2][B]a.cxx:10: error: function definition does not declare parameters
a.cxx:17: error: function definition does not declare parameters[/B][/SIZE]
                                                        
                            [SIZE=4]  ***Please Help Me.........How to compile and also all steps clearly..***[/SIZE]
                                                                             Thankfully
                                                                              Santanu

---

### Post by NovaAesa on 2010-09-16
I'll give you a hint, you have a problem where you are trying to fully qualify the functions you are defining.

Do you understand what the "person : : " part before getdata(void) is meant to do?

---

### Post by santanu.csc on 2010-09-16
Please Say clearly

---

### Post by NovaAesa on 2010-09-16
I've given you a hint towards solving your problem. You still haven't answered my question "Do you understand what the 'person : : ' part before getdata(void) is meant to do?".

Did you write the code yourself or is it an example from a book or the Internet?

---

### Post by ChurroLoco on 2010-09-16
You are mixing up your declaration with your definition.  Classes in C++ should generally consist of two file.  The .cpp (Implementation file) and .h (Declaration File).

Here is a little blurb about declaration/definition
[http://www.edaboard.com/thread124112.html](http://www.edaboard.com/thread124112.html)

You are mostly showing what should be in the .h file the problem is you are also trying to say what the function do in this file.  You are only supposed to list there names, return type, and parameters.

so
```
void GetData();
```
[Notic you don't need "Person::" in the header because your within the class curly braces]

In a seporate c++ file you should include this header and fill in the implementation. for each function.  So something like:

```
#include "person.h"

void person::getdata()
{
   cout << "Enter Name";
   cin >> name;
   cout << "Enter age";
   cin >> age;
}

//...The rest of your person:: method definitions go here

```

Check this page out to learn more about C++ classes.
[http://pages.cs.wisc.edu/~hasti/cs368/CppTutorial/NOTES/CLASSES-INTRO.html](http://pages.cs.wisc.edu/~hasti/cs368/CppTutorial/NOTES/CLASSES-INTRO.html)

Hope this helps

---

### Post by vijushimpi on 2010-09-16
the above program successfully complied under code::blocks IDE, I just added using namespace std;

---

### Post by NovaAesa on 2010-09-16
> **vijushimpi said:**
> the above program successfully complied under code::blocks IDE, I just added using namespace std;
That's rather interesting, because it doesn't compile with g++ even after adding using namespace std. Which compiler are you using with code::blocks?

---

### Post by dwhitney67 on 2010-09-16
> **ChurroLoco said:**
> You are mixing up your declaration with your definition.  Classes in C++ should generally consist of two file.  The .cpp (Implementation file) and .h (Declaration File).

Incorrect information never helps.

---

### Post by dwhitney67 on 2010-09-16
> **NovaAesa said:**
> That's rather interesting, because it doesn't compile with g++ even after adding using namespace std. Which compiler are you using with code::blocks?

Agreed; the compiler will definitely complain about a syntax error.  Here are the errors I get:
```

g++ -Wall -pedantic ubuntu.cpp
ubuntu.cpp:11: error: expected initializer before ‘:’ token
ubuntu.cpp:18: error: expected initializer before ‘:’ token

```
This tells me that the syntax of ": :" should be "::" (ie no white-space allowed).

---

### Post by schauerlich on 2010-09-16
There are only a few small mistakes which are simple and easy to fix; they have all been highlighted in this thread. Look at the line numbers the compiler gives, and try to figure out what's wrong. Hint: ':' and '::' have quite different meanings in C++.

EDIT: looks like dwhitney ninja'd me with the answer... oh well.

---

### Post by vijushimpi on 2010-09-21
when I copied from website to IDE it automatically converted ": :" into "::" that is why I unaware of it, by the way I am using default compiler ie, G++

---

