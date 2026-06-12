---
title: "[SOLVED] C++ in Linux"
date: 2008-02-05
forum: Programming Talk
---

### Post by Hoom@n on 2008-02-05
Hello!
I write some command-line applications with c++(like acm questions) In windows I had tree choices:
[LIST=1]
[*]Open a console application in Visual Studio
[*]Write it in Borland c++ for Dos
[*]Write it using a text-editor and run it with g++
[/LIST]
How can I write a console c++ application in linux? (my program should have standard IO, not buttons)
Thanks.

---

### Post by emarkd on 2008-02-05
#3 is the standard way of doing it in Linux and it works fine.  g++ is already installed in Ubuntu.

If you're a GUI/IDE type of programmer, try Anjuta.  It's in the repositories.

---

### Post by Cypher on 2008-02-05
If you want to compile and run your program entirely in the command line, then you can use a text editor like GEDIT for basic stuff or if you want to go hardcore, Emacs as your code editor and then use the standard G++ command to compile your code..

---

### Post by Hoom@n on 2008-02-05
Thanks you. But how can I compile my program? e.g I have program.cpp and I wanna know how to compile it with g++ in termnal. Please tell it. Thanks.

---

### Post by LaRoza on 2008-02-05
[http://ubuntuprogramming.wikidot.com/](http://ubuntuprogramming.wikidot.com/)

Moved to Programming Talk

---

### Post by Cypher on 2008-02-05
Well the way to compile your program depends on what you are coding..if you are doing something as simple as..
```

#include <iostream>

int main(void)
{
   cout << "Hello World" << endl;

   return 0;
}

```
Then you can compile this code easily with
```

g++ -o hello hello.c

```

If you have multiple files, then you'll want to create .o of them all and then compile them together using any specific libraries you need.

For anything more than a single file, you really should look into Makefile. If you aren't interested in making Makefile,  most IDE's like KDevelop, Ajunta will create one for you and you can uese these IDEs to create your console applications..

---

### Post by Hoom@n on 2008-02-05
Thanks, but what is -o(in the first command)?

---

### Post by Majorix on 2008-02-05
> **Hoom@n said:**
> Thanks, but what is -o(in the first command)?

It is used to link object files.

---

### Post by Cypher on 2008-02-05
> **Hoom@n said:**
> Thanks, but what is -o(in the first command)?
"-o" is Output file name. If you don't use that, the default output name of "a.out" is used.

Doing "man g++" will explain all the flags..

---

### Post by Hoom@n on 2008-02-05
Thank you, so to be sure: "g++ -o <output> <input>" and it'll generate output.exe as output, Am I right?
+++
How can I see all the warnings?
____
Thanks.

---

### Post by aks44 on 2008-02-05
> **Hoom@n said:**
> How can I see all the warnings?

There are many switches to enable warnings, from the top of my head I can only remember -Wall (which contrary to what it seems, doesn't enable *all* warnings)

You should check the g++ manual:
```
man g++ 
```

---

### Post by Hoom@n on 2008-02-05
Thank you. First of all I hadn't g++ installed, so I installed it by apt-get.  And second:
This is a normal program:
```
#include<iostream>
using namespace std;
int main()
{
cout<<"hello";
int i;
cin>>i;
return 0;
}
```
But:
```
hooman@hooman-laptop:~$ cd Desktop
hooman@hooman-laptop:~/Desktop$ g++ -o hello hello.cpp
hooman@hooman-laptop:~/Desktop$ sh hello
hello: 1: Syntax error: "(" unexpected

```
What's the problem?
Thanks.

---

### Post by aks44 on 2008-02-05
Run it using **./hello** rather than **sh hello** (sh is intended to execute scripts, not compiled programs).



EDIT: how did you install g++? On Ubuntu you'd better install it through the **build-essential** package or else be prepared for troubles...

---

### Post by Hoom@n on 2008-02-05
Thank you.
+++
sudo apt-get install g++ and then it installed g++ from my ubuntu cd. Is there any problem? Really I don't like to have a new problem!

---

### Post by LaRoza on 2008-02-05
> **Hoom@n said:**
> Thank you.
+++
sudo apt-get install g++ and then it installed g++ from my ubuntu cd. Is there any problem? Really I don't like to have a new problem!

sudo aptitude install build-essential

---

### Post by Hoom@n on 2008-02-05
Thank you. I did it! Is there any problem now?

---

### Post by BoazAdreal on 2008-02-11
Hey I am a bit new to programming but I am running into a IOStream not found error when I attempt to compile the code you have provided. I have GCC 4.1 and 4.2 installed, but I had the same thing occuring when I had it not installed. Any suggestions would be much appreciated.

---

### Post by Caduceus on 2008-02-11
Are you doing

#include <iostream>

Or

#include <IOStream>

The first one is correct, C++ is dodgy regarding upper and lower case letters.

---

### Post by HueyLuey on 2008-02-11
I'd recommend using an IDE such as Eclipse with CDT. It provides a half decent editor and provides a wrapper over g++ with an easier to use interface for build settings etc.

---

### Post by BoazAdreal on 2008-02-11
> **Caduceus said:**
> Are you doing

#include <iostream>

Or

#include <IOStream>

The first one is correct, C++ is dodgy regarding upper and lower case letters.

The first one. It's the same thing as Java from what I had remembered for case tense.

---

### Post by aks44 on 2008-02-11
> **Caduceus said:**
> The first one is correct, C++ is dodgy regarding upper and lower case letters.

The C++ language doesn't care, it directly passes the filename to the underlying filesystem.

Which means: on case-sensitive filesystems (*nix) the compiler will whine; on case-insensitive filesystems (Windows) it will compile fine.

Again, it has nothing to do with the C++ language or the compiler... ;)

---

### Post by leileicats on 2008-02-12
> **Hoom@n said:**
> Thank you, so to be sure: "g++ -o <output> <input>" and it'll generate output.exe as output, Am I right?
+++
How can I see all the warnings?
____
Thanks.

Using "g++ -Wall -o <output> <input>" will show the detailed warnings and error.

---

### Post by Hoom@n on 2008-02-12
Thank you.

---

