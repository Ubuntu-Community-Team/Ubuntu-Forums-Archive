---
title: "GTK, MySql and C or C++"
date: 2008-06-14
forum: Programming Talk
---

### Post by anewguy on 2008-06-14
Well, I made it through my first GTK app with everyone's help.  Now I'd like to move on to an app I started in Visual Basic in Windows but never finished.  Obviously, I want this to be in either C or C++ (I don't know anything about C++ but am willing to learn!) and using MySql.  It is to be a genealogy program I want to write to meet my needs and to get some more experience with GTK and MySql.

In VB, I could programatically define and set up my database, then obviously I used various forms for everything I wanted to do, all with imbedded MySql.  Should I be able to do the same thing in C or C++?  Since it's going to be another learning experience, would I do best to try to bite the bullet and work in C++?  Can you point me to any free online guides of beginning C++, including imbedding MYSql?  I'm on disability so I can't afford to buy anything.  I wanted to take a course at our local JC but it's just too expensive for me.

I do have 20+ years (althought it's 12 since I used any of it!!) of experience as a main frame programmer, systems programmer and systems administrator.  I've written code in machine language, assembler, Fortran, RPG, Cobol, Basic, Visual Basic, and C to name a few.  I've worked with low-level things for dealing with devices and high level things as simple as the ubiquitous "hello, world".  I've worked with Oracle, MySql and a CASE tool (which I hated - took the fun out of things).  So, I have the background to pick these things up fairly well, if I can just get my head out of my **tt and start learning/remembering again.

Any pointers, tips on free tutorials, etc., opinions - all are welcome!

Thanks in advance! :)

---

### Post by descendency on 2008-06-14
A pointer for you:
[PHP]#include <iostream>
#include <string>

using namespace std;

int main()
{
	string N = "Hello!";
	string* p = &N;
	
	cout << *p << endl;
	return 0;
}
[/PHP]
(I have an odd sense of humor :$)

Some of this information might seem overly basic, but I will just provide it in-case you feel lost.

Here is a very basic tutorial just in case you consider C++:
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

I use the g++ compiler (sudo apt-get install g++) and geany (sudo apt-get geany) for building .cpps and .h files. 

Here seems to be a very basic idea of what the C code will look like (and the C++ code should look similar):
[http://www.cyberciti.biz/tips/linux-unix-connect-mysql-c-api-program.html](http://www.cyberciti.biz/tips/linux-unix-connect-mysql-c-api-program.html)

SQL tutorial:
[http://www.w3schools.com/sql/default.asp](http://www.w3schools.com/sql/default.asp)

Not sure what else to provide, but if you need anything else, I'm sure someone here knows where to find it.

---

### Post by Can+~ on 2008-06-14
Using GTK and MySQL makes me thing that you're building a local application (although, I might be wrong). You should check sqlite, it's more suitable for local apps (like firefox3, amarok (optional), etc...)

---

### Post by loell on 2008-06-14
probably the closest equivalent to VB RAD  in linux is through

[Kexi]("http://www.kexi-project.org/screenshots.html")

or  openoffice's base 


or  how about web applications? with ORM in ruby or python.

---

### Post by pmasiar on 2008-06-14
> **anewguy said:**
> Obviously, I want this to be in either C or C++ (I don't know anything about C++ but am willing to learn!) and using MySql. 

I would call you "speed-obsessed kiddie" (or something, a term coined by CptPicard) for your "obvious" decision to use C or C++ for a database desktop app, but you are not a kid. So, consider evaluating your options:

Database front-and will spend 90% of runtime in DB calls, so using C++ "for speed" is complete waste of time, and every rational hacker will use flexible language (Python, Perl, Ruby) for development speed instead. 

Also, for an embedded database with single desktop user, using full-features MySQL multiuser database server is certainly overkill. Conveniently, Python 2.5 includes  bindings for SQLite, C DB library which uses no server (just performs SQL queries on datafiles), far more fitting the goals of such app, IMNSHO.

Of course it is your own free time, you are free to waste it in any way you find enjoyable. For me, most important speed is "speed to the market" - how fast I can implement my ideas, and Python is my preferred tool.

---

