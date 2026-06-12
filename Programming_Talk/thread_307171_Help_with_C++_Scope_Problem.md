---
title: "Help with C++ Scope Problem"
date: 2006-11-26
forum: Programming Talk
---

### Post by HamCoder on 2006-11-26
Here is the error message...
APC_Moon.cpp:481: error; 'R_x was not declared in this scope'

Here is LIne 481...
e_Moon = R_x(-eps) * Vec3D(Polar(l_Moon,b_Moon));
R_x is defined in APC_VecMat3D as   Mat3D R_x(double RotAngle)
e_Moon is defined in APC_Moon.cpp as  Vec3D  e_Moon;

Background...
I've been programming almost 40 years and I've used lots of languages on mainframe and PC/Windows platforms.  But I'm new to Linux and very new to C/C++.  I understand scoping, but not in the C++ context.

The program in question came on a CD as part of an astronomy book.  The program calculates sunrise/sunset times.  I compiled and ran it without change on my Windows box with GTK+, Glade, and something else(?).  BTW, I dual-boot the hard way - by swapping one laptop drive for another.  

Under Linux, I'm using Edgy 6.0, with Anjuta as the IDE.  I've also gone to the terminal window and manually executed the MAKE program - with the same results I get with Anjuta.  

My problem is that I'm not sure how to approach the debugging process this time.  The code is moderately complex with some objects, named and unnamed namespaces.  

Thanks for any help and ideas you can offer.  If you want more code snippets, let me know

---

### Post by rvickers on 2006-11-26
'R_x was not declared in this scope' means it doesn't recognize R_x as anything defined yet. My guess is you're missing a library. If you know what library(s) the program uses then you can compile with -Lxxxxx with xxxxx being the library path and name. An example is a program that uses mysql library:
$  g++-4.0 -Wall -g -Llibmysqlpp -lmysqlclient sql_query.cpp

Good Luck

---

### Post by thumper on 2006-11-27
Not necessarily missing a library but missing the function declaration (normally in a header file).

---

### Post by goodfella on 2006-11-27
One thing you also have to be aware of in c++ is where you declare your variables.  For example the following code will not compile:

```
int a;
int b;

if(a == b)
{
    int c;
}

c = a;

```

the error from g++ is "error: ‘c’ was not declared in this scope".  The reason is that the variable c is only declared in the scope of the if statement and can only be used between the braces "{ }" making up the code body of the if statement.  Now if I place a declaration of c outside the code body for the if statement the code compiles.  Here is an example:

```
int a;
int b;
int c;

if(a == b)
{
    int c;
}

c = a;

```

A good book about the c++ programming language its syntax, and uses is called "The C++ Programming Language" by Bjarne Stroustrup.  You could also look at his c++ website [http://www.research.att.com/~bs/C++.html]("http://www.research.att.com/~bs/C++.html")
Hope this helps out.

---

### Post by curvedinfinity on 2006-11-27
But of course, in the second example, the second declaration of c is a seperate stack variable from the first. If c was defined as something outside of the if statement, accessing c inside of the if statement would result in an undefined value.

---

