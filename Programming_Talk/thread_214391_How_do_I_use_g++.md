---
title: "How do I use g++?"
date: 2006-07-12
forum: Programming Talk
---

### Post by s_h_a_d_o_w_s on 2006-07-12
I have my .cpp file, how do I make g++ turn it in to a executable file? What file type will it be? .exe? .tar.bz2?

---

### Post by mgor on 2006-07-12
in a terminal,
```
g++ source.cpp
```
will compile a binary file named 'a.out', look in the current directory for it, you can execute it with,
```
./a.out
```

for more information, read the manual page for g++.

---

### Post by s_h_a_d_o_w_s on 2006-07-12
what if i want a .exe?

---

### Post by ifokkema on 2006-07-12
> **s_h_a_d_o_w_s said:**
> what if i want a .exe?
.exe is a WINDOWS executable name. In Linux, you don't have to call your file with any extension. You could
```
g++ -o file.exe file.cpp
```
but that will not make your executable work on Windows.

---

### Post by mostwanted on 2006-07-12
The default is to not have any extension in UNIXes

```
g++ -o myprogram source.cpp
```

---

### Post by s_h_a_d_o_w_s on 2006-07-12
How can I tell g++ to use another name? Every time it writes over a.out , but say if i want b.out or numberdoubler.out ?

---

### Post by ifokkema on 2006-07-12
> **s_h_a_d_o_w_s said:**
> How can I tell g++ to use another name? Every time it writes over a.out , but say if i want b.out or numberdoubler.out ?

Like I (and mostwanted) said:

> **ifokkema said:**
> ```
g++ -o file.exe file.cpp
```
So
```
g++ -o <name_you_want_for_your_outfile> <your_source.cpp>
g++ -o numberdoubler.out source.cpp
g++ -o my_executable source.cpp

```etc, etc...

---

### Post by mostwanted on 2006-07-12
Might wanna do a

```
man g++
```

as well.

---

### Post by s_h_a_d_o_w_s on 2006-07-12
thanks a lot! I just used it to write my first program. I am learning C++, and I couldn't find any good compilers. Seems like noone really has any gui for such programs.

---

### Post by Somenoob on 2006-07-12
What other programming languages can it compile files from?

---

### Post by ifokkema on 2006-07-13
> **Somenoob said:**
> What other programming languages can it compile files from?
Just C and C++. See man g++:
```
gcc - GNU project C and C++ compiler
```

---

### Post by thumper on 2006-07-13
The gnu compiler collection can also do ADA, fortran, java, and I'm sure there is more.

---

### Post by asimon on 2006-07-13
> **thumper said:**
> The gnu compiler collection can also do ADA, fortran, java, and I'm sure there is more.
You've forgot [Objective C](http://en.wikipedia.org/wiki/Objective-C). ;-)

---

### Post by s_h_a_d_o_w_s on 2006-07-16
Can I update g++? I don't think it's up to ANSI standards or something, in the compile error log, it wants me to add lots of semi-colons in front of cout , and in my c++ book, c++ for dummies, they're not ther?

---

### Post by ifokkema on 2006-07-16
Could you post the error message and the respective piece of code?

---

### Post by s_h_a_d_o_w_s on 2006-07-16
Sure, here it is. But I should say I started learning two weeks ago, well, and i'm 13 yrs old.

Source:

#include <iostream>
using namespace std;

int main()
{

int orgnum;

cout << "Enter a number for me to double... ";
cin >> orgnum;

int dorgnum;
dorgnum = orgnum * 2

cout << "Double your original number is: ";
cout << dorgnum << endl;

system("PAUSE");
return 0;
}



and the error log:

ubuntu@ubuntuzilla:~$ g++ /home/ubuntu/Desktop/numdoubler.cpp
/home/ubuntu/Desktop/numdoubler.cpp: In function &#8216;int main()&#8217;:
/home/ubuntu/Desktop/numdoubler.cpp:15: error: expected `;' before &#8216;cout&#8217;


If I am correct, in my book there are never any semi-colons in front of cout. Maybe I am wrong.

---

### Post by EchoRevamped on 2006-07-17
You need a semicolon after "dorgnum = orgnum * 2".  Simple mistake, we all make them. :)

---

### Post by s_h_a_d_o_w_s on 2006-07-17
Ooops, thanks. guess I was going too fast.

---

### Post by s_h_a_d_o_w_s on 2006-07-17
Do you know of any simple programs for writing and compiling? I need programs that i can destribute, like. deb or something. And are there any for MS? I've tried anjuta, eclipse, etc. but they're too complicated. I just want to write the code and click a ''compile'' button.

---

### Post by ifokkema on 2006-07-17
I've never used it, but I believe [Codeblocks]("http://www.codeblocks.org/") does what you need.

---

### Post by sjenks1 on 2006-07-17
Hi

g++ is best used from the command line i.e.

g++ -g -Wall -o<file1> <file1.cc>

file1 = name you want to output to (the executable dont include an EXE extension :D )

file1.cc is whatever your source code is called with the .cc extension

----------

you can try man g++ on the command line to learn the different bits of the compiler :-D

If my memory serves me right its best to use #include<iostream.h> as well ??

---

