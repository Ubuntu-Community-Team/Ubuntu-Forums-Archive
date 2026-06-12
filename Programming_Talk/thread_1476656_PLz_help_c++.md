---
title: "PLz help c++"
date: 2010-05-08
forum: Programming Talk
---

### Post by Muhammad Ahmed on 2010-05-08
Please tell me how to run c++ file in UBUNTU, i have tried following

g++ file file.cpp
gcc file.cpp
./file.cpp

NOTHING WORKS

---

### Post by lisati on 2010-05-08
Moved to "Programming talk"

What error messages are you getting?

---

### Post by Muhammad Ahmed on 2010-05-08
line 8 syntax error near unexpected token
line 8 main()

---

### Post by ubun2warrior on 2010-05-08
you have to install a compiler so that you can run c++ files. If you are looking at a graphical development platform you can go with anjuta.just search for it in synaptics and install.

---

### Post by Muhammad Ahmed on 2010-05-08
errors are as such that no function is running and the error message is like this

error 'endl' was not declared in this scope
error 'cout' was not declared in this scope
error 'getch' was not declared in this scope

and no libraries are getting defined

error 'DOS' was not declared in this scope
error 'conio' was not declared in this scope
error 'iostream' was not declared in this scope
error 'iomanip' was not declared in this scope
error 'stdlib' was not declared in this scope
error 'stdio' was not declared in this scope

---

### Post by Linteg on 2010-05-08
It would be great if you could show the code in question as it would make it a lot easier to help with the debugging. My guess is that you've at least forgot to add "using namespace std;".
And finally, to compile c++ code:
```
g++ myfile.cpp myotherfile.cpp -o myprogramname
```

---

### Post by MadCow108 on 2010-05-08
another conio problem ...

search the forum for that keyword you'll find millions of threads

and please show code error messages alone seldom help solving the problem

---

### Post by Muhammad Ahmed on 2010-05-08
#include<conio>
#include<iomanip>
#include<iostream>
#include<stdio>
#include<stdlib>
#include<DOS>

main()
{

int a; int b=6; char c='*'; int i;int x;int q=1;
for(i=5;i>=1;i--)
{ cout<<endl; b--;  q++
for(x=q;x>=0 && x<=6;x--)
{
cout<<" ";
}
for(a=b;a<=5 && a>=1;a--)
{cout<<c<<"\a";}


}
getch();
}

---

### Post by MadCow108 on 2010-05-08
urg where did you find that code ...

here is how to get it to compile:
remove
#include<DOS> // dos won't work on linux
#include<conio> // outdated dos stuff
#include<stdio> // does not exist, probably cstdio was meant, but unused anyway
#include<stdlib> // does not exist, probably cstdlib was meant, but unused anyway

add a using namespace std; after the includes (or replace cout and endl with std::cout, std:endl)

add a semicolon after q++

remove getc() (it is not necessary when started from a shell) or replace it with getchar() defined in cstdio or cin << somevar;

and compile with g++, not gcc

I recommend you go over a recent C or C++ tutorial before trying to compile code written by someone 15 years ago
this one is quite ok:
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by Muhammad Ahmed on 2010-05-08
i made it my self it works on all Windows compilers how can i get it wrking on ubuntu

---

### Post by radeon21 on 2010-05-08
This is a portable equivalent of what you wrote (cleaned up for readability):

```

#include <iostream>

using namespace std;

int main()
{
	int a;
	int b = 6;
	int i;
	int x;
	int q = 1;
	
	char c = '*';
	
	for(i=5;i>=1;i--)
	{
		cout << endl;
		b--;
		q++;
	
		for(x = q; x >= 0 && x <= 6; x--)
		{
			cout << " ";
		}
		
		for(a = b; a <= 5 && a >= 1; a--)
		{
			cout << c << "\a";
		}
	}
	
	//wait for user to hit enter to quit
	cin.ignore();
	
	return 0;
}

```

---

### Post by trent.josephsen on 2010-05-08
> **Muhammad Ahmed said:**
> i made it my self it works on all Windows compilers how can i get it wrking on ubuntu

You can't, as far as I know, nor should you want to.  Linux is not related to DOS, and conio.h was already old in 1989 when ANSI standardized C.  You shouldn't be using it even in Windows programs since version 3 point something.  Write portable code like radeon21's example.

---

