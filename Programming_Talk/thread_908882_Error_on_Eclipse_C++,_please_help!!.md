---
title: "Error on Eclipse C++, please help!!"
date: 2008-09-02
forum: Programming Talk
---

### Post by kiragn01 on 2008-09-02
I have problem with my Eclipse C++ version 3.4.0

it is shown on the pictures...please anyone help
Thank you!!

[IMG]http://img143.imageshack.us/img143/1931/11wo7.jpg[/IMG]

[IMG]http://img143.imageshack.us/img143/8030/83282411hr8.jpg[/IMG]
i try to put in:
[color=red]
#include <iostream>
using namespace std;
 
int main()
{
     cout << "Hi, Mom!" << endl;
 
     // Compute and print the sum of the first ten integers
     double sum = 0;
     for (int i = 1; i <= 10; i++)
          sum += i;
     cout << "The sum of the integers from 1 to 10 is: " << sum;
 
     return 0;
} [/color]


I dont know why there is a red line under #include <iostream> 

[IMG]http://img402.imageshack.us/img402/6649/79141325rd6.jpg[/IMG]
[IMG]http://img300.imageshack.us/img300/6725/83231845wl7.jpg[/IMG]

---

### Post by FFfanatic on 2008-09-02
Don't you need args for main?
Like the default:
```

int main(int argc, char* argv[])
{}
```

---

### Post by cmay on 2008-09-02
from what the pictures error message say it looks like you are on windows. i dont know this IDE but its maybe something to do whit the / in documents and settings. i think i see that it cant locate it from there . its same problem whit dev c++ and mingw compiler when some one puts their source files in documents and settings.the mingw compiler which i guess is the compiler used here does not like these spacedelimiters that are on windows as its sort of used to these/ from linux.  if i am right about that then try put it in just c:\ and see if it can locate it from there.the information from these pictures is not enough however. please include compiler log operative system and a short description of the problem. it will be more easy to find out what is wrong. pictures only say something to those who knows the ide whereas if you tell people what is the problem and show the code and compiler log then there is a greater chance that some one can help you. i am going to bed now but if you post these things i am sure someone can help a bit more than me.

---

### Post by cmay on 2008-09-03
hi again.
good to see that you have included the code now, from what the error message say there is an error launching external scanning info generator /documents and settings/winxp/ de: mat1 and make cant be executed. to me it looks like windows as operative system.are you running the program under windows or linux ? . however there is nothing wrong whit the code and it should compile just fine. can you post the whole compiler log. that will tell a bit more about why it will not compile.

---

### Post by cb951303 on 2008-09-03
I remember getting the same error on windows. I remember adding mingw/bin directory to environment variable "path" to fix it.
PS: You may need a restart after doing that

---

### Post by cmay on 2008-09-03
> I remember getting the same error on windows. I remember adding mingw/bin directory to environment variable "path" to fix it.
PS: You may need a restart after doing that
its something like that i been trying to tell him :)
i dont know this IDE but i know that if you try compile something in the style of /documents and settings/projects/myc++folder/hello.cpp whit devc++ and gcc/mingw compiler it will trow a fit and plain refuse to do it. looks like the same type of problem here.

---

### Post by kiragn01 on 2008-09-03
> **cb951303 said:**
> I remember getting the same error on windows. I remember adding mingw/bin directory to environment variable "path" to fix it.
PS: You may need a restart after doing that

I am sorry. Can you explain in detail??
Because i am a beginner...i am good at C++...Thx

---

### Post by jespdj on 2008-09-03
So, this is a question about Eclipse and C++ on **Windows**, right? It doesn't really have anything to do with Ubuntu. Why are you asking it on the Ubuntu forums?

Do you have gcc (the compiler) installed on your Windows machine? Note that Eclipse is only an IDE, the C++ compiler is not included. You need to install gcc separately and then tell Eclipse where to find it.

---

### Post by cmay on 2008-09-03
[http://www.mingw.org/](http://www.mingw.org/)
in case you have not the compiler installed then link  is the mingw compiler. its the gcc compiler for windows. it cant handle the space delimiters in windows that well. so if you install it in c:\ and put your cpp files in also c:\ or a folder close by then maybe it will not be a problem.i dont know eclipse but the mingw compiler i know from the devcpp IDE. it should work whit eclipse i assume anyway there is install instructions  with it . as for the problems i have had with it has always been with putting the files in too many folders and gcc dont like that very much.that is all i can do but i hope you get it to work.
hope it helps.

---

### Post by Sinkingships7 on 2008-09-03
> **jespdj said:**
> So, this is a question about Eclipse and C++ on **Windows**, right? It doesn't really have anything to do with Ubuntu. Why are you asking it on the Ubuntu forums?
[quote=Ubuntu Forums]
**Programming Talk**
This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any programming language is allowed. 
[/quote]

Also, it would appear that your problem is with your compiler. You're using GCC, which is a C compiler. You need to be using G++ or something similar, like MinGW.

---

### Post by kiragn01 on 2008-09-04
now, all the problems were solved after i installed the MinGW compiler
But the new problem can out after use the same code:

[color=red]#include <iostream>
using namespace std;

int main()
{
cout << "Hi, Mom!" << endl;

// Compute and print the sum of the first ten integers
double sum = 0;
for (int i = 1; i <= 10; i++)
sum += i;
cout << "The sum of the integers from 1 to 10 is: " << sum;

return 0;
}[/color] 

when i click build all...
this error came out:

/mingw/lib/libmingw32.a(main.o):main.c: undefined reference to `WinMain@16'

Then i just ignore and click on run ..
the message->>>>> launch failed. Binary not found<<<<<< come out

anyone please help

thx alot

---

### Post by Zugzwang on 2008-09-05
If you used a Windows IDE, I would say that you set your project type to "Windows Application" instead of "Console application". Don't know about eclipse. Look at the documentation of MinGW about that issue. And never forget that you can simple google for the error you get (always the first one!).

---

### Post by cb951303 on 2008-09-05
try adding "-mwindows" to the compiler line in your project settings. also 
it should be "main(int argc, char *argv[])"

cheers

---

### Post by cmay on 2008-09-05
> undefined reference to `WinMain@16'
try to save your cpp file in c:\ and compile it.
i think maybe this has something to do whit the spaces / in windows
mingw compiler dont like these spaces. i had this error many times for that reason with devcpp IDE and the mingw comiler. so i had my folder with cpp files in c:\and that worked. it should work if your comipler is set up right and the projects folder is not in a path like c:\documents  and   settings\c++folder\the_c++_project. having too long a path with too many \ confuse the mingw compiler.

---

### Post by kiragn01 on 2008-09-05
> **cmay said:**
> try to save your cpp file in c:\ and compile it.
i think maybe this has something to do whit the spaces / in windows
mingw compiler dont like these spaces. i had this error many times for that reason with devcpp IDE and the mingw comiler. so i had my folder with cpp files in c:\and that worked. it should work if your comipler is set up right and the projects folder is not in a path like c:\documents  and   settings\c++folder\the_c++_project. having too long a path with too many \ confuse the mingw compiler.

It's work now after save...thank you very much..appreciated.

---

### Post by cmay on 2008-09-05
thanks for letting us know.
and good luck to you whit your programming :)

---

