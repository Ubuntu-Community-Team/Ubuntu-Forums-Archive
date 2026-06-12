---
title: "Programming IDE's"
date: 2012-03-04
forum: Programming Talk
---

### Post by Nolicus on 2012-03-04
I program in C++ (for a class that I'm taking) and have attempted to use several IDE's, but none of them work. I downloaded them directly from the software center and I have been getting a problem with them not recognizing certain commands. Codelight would not recognize system ("pause"); and other basic functions. And in eclipse it wont even let me set up the headers without displaying errors. I suspect that I don't have a compiler set up right. Do you have any ideas where to start?

---

### Post by Lokireloaded on 2012-03-04
system(""); is ok, the problem is the pause.
There are several ways of getting around this.

---

### Post by Nolicus on 2012-03-05
I used a cin(cin()); and some other sequences and they all didn't work. I have used this bit of code in Visual Studio and other IDE's in window 7 and know that it is part of the language. Eclipse won't even take my header statements and I promise that they are syntactically correct. I am almost convinced that it is something under the hood that is malfunctioning. would i have to set up new functions within the IDE to over come this?

---

### Post by nothingspecial on 2012-03-06
*Thread moved to **Programming Talk**.*

---

### Post by r-senior on 2012-03-06
Have you installed the build-essentials package and tried compiling Hello World in C++ from the command line so that you take the IDE out of the equation?

```
$ cat hello.cpp
#include <iostream>

int main()
{
	std::cout << "Hello" << std::endl;
}
$ g++ -o hello hello.cpp
$ ./hello
Hello

```

---

### Post by Barrucadu on 2012-03-06
Give an example of something you believe is correct which is failing.

Your "system("pause")" is failing because there is no pause command on Linux. I am not a C++ programmer, but "cin(cin())" looks utterly wrong to me, the only usage I have seen is "cin >> variable".

---

### Post by overcast on 2012-03-06
system ("pause") works on windows and not on linux. I think you need to find something that works on linux. YOu can use getchar() if you want instead of system("pause") or cin.get as explained earlier.

---

### Post by hakermania on 2012-03-06
As for a good IDE for C++, QtCreator rulez

---

