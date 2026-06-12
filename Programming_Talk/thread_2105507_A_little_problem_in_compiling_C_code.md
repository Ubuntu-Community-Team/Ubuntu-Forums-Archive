---
title: "A little problem in compiling C code"
date: 2013-01-16
forum: Programming Talk
---

### Post by vishurockssrivastava on 2013-01-16
Hello Everyone!!
I am new here and this is my first post. I am running Ubuntu 12.04 on my desktop and I am facing a problem compiling my C code (which works perfectly on my Windows Laptop). I tried Hello World program to test it out-
```
#include<stdio.h>
#include<conio.h>
void main()
{
clrscr();
printf("Hello World!!");
getch();
}
```
Then, I try compiling this code using the following command from terminal-
```
gcc -o Output Hello.c
```
where (as is obvious), I stored the file with the name Hello.c .
I get the following error (copied as is from the terminal)-
```
Hello.c:2:18: fatal error: conio.h: No such file or directory
compilation terminated.
```
It gives the same error when I try-
```
g++ -o Output Hello.c
```
Since this is the simplest of the C programs I have seen, I'm not sure why either of the 2 compilers is not able to work with conio.h . I looked it up in my help file on my Windows laptop and it said that the conio.h header file was not compatible with Unix even when it was compatible with DOS. So, is this the reason I'm not able to compile the code? If yes, then please suggest me some header files which are-
1. Compatible only with GNU/Linux
2. Platform independent
which I can use instead of conio.h and yet get the full functionality of it.
conio.h is the most used header file in C/C++ (more than stdio.h and iostream.h and I haven't seen one of my programs written without it). So even if the header file must change, it must be able to provide the entire functionality of conio.h . I actually didn't expect this when I switched to Linux (which I hear is created entirely in C but I may be wrong). This is a bit of a disappointment for me...

---

### Post by muteXe on 2013-01-16
Welcome.
[http://stackoverflow.com/questions/6565924/g-conio-h-no-such-file-or-directory](http://stackoverflow.com/questions/6565924/g-conio-h-no-such-file-or-directory)

Have a google first with the compiler message.

---

### Post by Tony Flury on 2013-01-16
> **vishurockssrivastava said:**
> Hello Everyone!!
I am new here and this is my first post. I am running Ubuntu 12.04 on my desktop and I am facing a problem compiling my C code (which works perfectly on my Windows Laptop). I tried Hello World program to test it out-
```
#include<stdio.h>
#include<conio.h>
void main()
{
clrscr();
printf("Hello World!!");
getch();
}
```
Then, I try compiling this code using the following command from terminal-
```
gcc -o Output Hello.c
```
where (as is obvious), I stored the file with the name Hello.c .
I get the following error (copied as is from the terminal)-
```
Hello.c:2:18: fatal error: conio.h: No such file or directory
compilation terminated.
```
It gives the same error when I try-
```
g++ -o Output Hello.c
```
Since this is the simplest of the C programs I have seen, I'm not sure why either of the 2 compilers is not able to work with conio.h . I looked it up in my help file on my Windows laptop and it said that the conio.h header file was not compatible with Unix even when it was compatible with DOS. So, is this the reason I'm not able to compile the code? If yes, then please suggest me some header files which are-
1. Compatible only with GNU/Linux
2. Platform independent
which I can use instead of conio.h and yet get the full functionality of it.
conio.h is the most used header file in C/C++ (more than stdio.h and iostream.h and I haven't seen one of my programs written without it). So even if the header file must change, it must be able to provide the entire functionality of conio.h . I actually didn't expect this when I switched to Linux (which I hear is created entirely in C but I may be wrong). This is a bit of a disappointment for me...

Conio is a windows only functionality and getch is a windows only call - you will need to write your own version of getch - if you really need it.

As i understand it - getch here is used to keep the terminal open once you run the program in windows - windows executables will automatically open a terminal for you if you double click on a program which needs a terminal. If you don't use getch on windows, then the terminal closes immediately and you wont see the output.

On Linux, a terminal is not automatically opened for you, so if you open a terminal to run your code - which you will need to do, then you don't need getch (or anything like it) since the terminal stays open.

The first thing you need to is get away from the thought that WIndows and Linux will behave the same way - they wont - they are different OSes - conio and getch are just one example where Windows has added generally non-standard functionality.

---

### Post by Warren Hill on 2013-01-17
There are some windows only bits to your code.  However with slight modification this works
```
#include<stdio.h>

void main()
{
  printf("Hello World!!");
  getchar();
}
```

it compiles with 

gcc -o Output Hello.c

However, the C standard defines that main must return an int.  g++ complains and won't compile it. 

so 
```
#include<stdio.h>

int main()
{
  printf("Hello World!!");
  getchar();
  return 0;
}
```

Is better and compiles with both

gcc -o Output Hello.c

and

g++ -o Output Hello.c

---

### Post by Bachstelze on 2013-01-17
>  However, the C standard defines that main must return an int. g++ complains and won't compile it. 

I don't see how that's relevant, since g++ compiles C++, not C. Also, in C99 main() implicitly returns 0 if no explicit return statmeent is present.

---

### Post by trent.josephsen on 2013-01-17
> **Bachstelze said:**
> Also, in C99 main() implicitly returns 0 if no explicit return statmeent is present.

But is still not permitted to be void, on a hosted implementation.

---

### Post by Ghostmn on 2013-01-20
```

#include <stdio.h>
#include <termios.h>
#include <unistd.h>

int mygetch( ) {
  struct termios oldt,
                 newt;
  int            ch;
  tcgetattr( STDIN_FILENO, &oldt );
  newt = oldt;
  newt.c_lflag &= ~( ICANON | ECHO );
  tcsetattr( STDIN_FILENO, TCSANOW, &newt );
  ch = getchar();
  tcsetattr( STDIN_FILENO, TCSANOW, &oldt );
  return ch;
}

```This should give you the same functionality of getch from windows.

I don't expect you to know what's going on which is fine, but feel free to copy and paste the code.

---

### Post by boazjones on 2013-01-21
Sorry guys; but I have a C# ASP.NET question.

Unfortunately, I have to deal with C# - and so, my question is about developing Winform applications in MonoDevelop.

I have been to other threads dealing with Mono Winforms - such as:

1. [http://ubuntuforums.org/showthread.php?t=885948&highlight=winform+mono](http://ubuntuforums.org/showthread.php?t=885948&highlight=winform+mono) (I've tried to install sudo apt-get mono-winforms - as the thread suggests; but I have encountered problems similar to those in item #2 listed below.

2. [http://ubuntuforums.org/archive/index.php/t-468183.html](http://ubuntuforums.org/archive/index.php/t-468183.html)

3. [http://ubuntuforums.org/showthread.php?t=449479&highlight=winform+mono](http://ubuntuforums.org/showthread.php?t=449479&highlight=winform+mono)

Regretfully, I am asking this question because of a class at school. I don't want to bash Msft; but, I have gotten use to actually controlling my own computer through Linux Ubuntu. It seems as though I may have to deal with Northwind Traders(lol) after all.

Any help you can provide would be greatly appreciated. I can't use Gtk or any other programming options; Microsoft is my prom date. :cry:

Thank you in advance for you consideration...

---

### Post by gbsmailadd on 2013-01-22
Hello forum,
I am an absolute beginner in ubuntu 12.04 LTS. I have two problems which are as follows:

01. 

I am having problem getting the output of a C code. I wrote the code in gedit and saved it as hello.c  on desktop. The code is as follows:

```

#include<stdio.h>
void main()
{
    printf("Hello world\n");
}

```

In order to run and compile the hello.c file, I wrote ```
gcc hello.c
``` and got "a.out" file on desktop but I don't see any output "Hello world". I want to see the "Hello world" output. So, help me on how I can see that "Hello world" output and also how to run a.out file or what to do with a.out file.


02. 

I read some of the posts and I saw that the instruction to open a terminal is > Application>Accessories>Terminal But I can't find the "Application". If anybody can help me to locate the Application tab or folder or icon will be appreciated. 

P:S: I do know how to open a terminal window but only using the shortcut ctrl+Alt+T :D But I want to learn the other ways to do so.

Apologies if I made any mistake regarding the post or anything. Thanks.

---

### Post by Warren Hill on 2013-01-22
1.  Application>Accessories>Terminal

is the old way to get a terminal, It still works if you use the "Gnone Classic" desktop but if you are using Unity you don't have it any more.  You can search for it in the Dash or press CTRL, ALT and T together to get the terminal

2. a.out is the default output file name.   If you want it to be called something else you have to tell it what.  Your command should have been

gcc -o HelloWorld Hello.c

then to run it enter

./HelloWorld

In a terminal once you are in the correct directory.

------
Alternativley if you are happy for the program to be called "a.out"

./a.out

should run it

---

### Post by dwhitney67 on 2013-01-22
> **boazjones said:**
> Sorry guys; but I have a C# ASP.NET question.

Open a new thread; your question does not belong in this one.

---

### Post by dwhitney67 on 2013-01-22
> **gbsmailadd said:**
> Hello forum,
I am an absolute beginner in ubuntu 12.04 LTS. I have two problems which are as follows:

01. 

I am having problem getting the output of a C code.
Welcome to the forums.

In the future, please open a new thread.  It is impolite to hijack another thread to post an unrelated query.

---

### Post by gbsmailadd on 2013-01-22
> **Warren Hill said:**
> 

2. a.out is the default output file name.   If you want it to be called something else you have to tell it what.  Your command should have been

gcc -o HelloWorld Hello.c

then to run it enter

./HelloWorld

In a terminal once you are in the correct directory.

------
Alternativley if you are happy for the program to be called "a.out"

./a.out

should run it

Thanks. It worked. Is there any other way to get the output directly in the terminal without creating any output file?

---

### Post by gbsmailadd on 2013-01-22
> Welcome to the forums.

In the future, please open a new thread.  It is impolite to hijack another thread to post an unrelated query.

Ohh! I'll keep that in mind.

---

