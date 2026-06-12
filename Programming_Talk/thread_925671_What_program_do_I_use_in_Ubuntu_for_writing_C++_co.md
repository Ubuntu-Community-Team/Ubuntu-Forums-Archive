---
title: "What program do I use in Ubuntu for writing C++ code?"
date: 2008-09-20
forum: Programming Talk
---

### Post by Pascal11110 on 2008-09-20
I have tried code::blocks, but cannot get any of my programs to work. Are there any better ones or will I still have dual-boot to get my programming done?

---

### Post by mssever on 2008-09-20
> **Pascal11110 said:**
> I have tried code::blocks, but cannot get any of my programs to work. Are there any better ones or will I still have dual-boot to get my programming done?Code::blocks is one of several C++ IDEs that work. If you post your errors, someone might be able to help.

---

### Post by Pascal11110 on 2008-09-20
One of my problems is that my ubuntu computer isn't working right now, so I can't boot it up and give you the exact problems, but after I would write a program in a console application it would say that my code had errors which it did not because I had just ran that code in Visual C++ 2008 Express Edition in Windows and it worked (it was just a simple hello world application)

---

### Post by mssever on 2008-09-20
Perhaps you should wait to ask until your Linux box is back up. It's somewhere between difficult to impossible to debug a program without having any data to go by.

Since you mentioned Visual Studio, I wonder if you used something specific to VS. I'm not a C++ programmer myself, and I've never used VS, but Microsoft does have a history of making things incompatible.

---

### Post by kavon89 on 2008-09-20
Use an IDE like [NetBeans]("http://download.netbeans.org/netbeans/6.1/final/") which works on both Windows and Ubuntu and supports development in C or C++. Make sure you have Java installed.

Also, to prevent having to reboot so much, consider using VirtualBox or something to run the other operating system virtually.

---

### Post by cmay on 2008-09-21
> One of my problems is that my ubuntu computer isn't working right now, so I can't boot it up and give you the exact problems, but after I would write a program in a console application it would say that my code had errors which it did not because I had just ran that code in Visual C++ 2008 Express Edition in Windows and it worked (it was just a simple hello world application)
a common hello world in c should work in linux if the packages build-essential is installed.
[PHP]#include<stdio.h>
int main(int argc,char **argv)
{
    printf("simple hello application\n");
    return 0;
}
 [/PHP]
and many forget to install this first.
[PHP]sudo apt-get install build-esential[/PHP]
however if you compile cpp soruce with gcc as codeblocs is a c++ IDE it will give and error since the c++ compiler is invoked g++
and further more the include directives in visual studio is not standard. and not the usual ending in many windows hello worlds to keep console window open system("PAUSE"); as it is not a bash command.
so hello windows in visual studio may not work in linux.
[PHP]#include "Stdafx.h"
int main(int argc, char *argv[])
{
printf ("hello visual studio\n");
system("PAUSE");
return 0;
}[/PHP]
i cant remember how the standard in visual looks like but i think it was something like this. "#include "Stdafx.h"" or something that looks like it a bit. but it wont compile under linux since its not a standard header file in c or c++ but specific to this visaul studio IDE.as far as i remember from the hour i used it before returning to devcpp.

if you can post code in question we can see if it should compile under linux and from the compiler message we can see if the build-essential package is missing from the compiler log. if it is not it can be a installation problem with gcc but in many the most cases it turns out to be this build -essentials package that is missing. i have come across more than one post where that has been the solution.

---

### Post by davidcaiazzo on 2008-09-21
I personally use code::blocks for my c++ apps and never had a problem. Like msserver said if you post some errors, or some more specifics I am sure someone can help you figure it out.
```

//C++ hello world
#include <iostream>
using namespace std;

int main(){
	cout<<"Hello World!"<<endl;
	cin.get();/*instead of using System("pause")
			  *which doesn't work in *nix systems
			  */ 
}

```

---

### Post by meastp on 2008-09-21
> **davidcaiazzo said:**
> I personally use code::blocks for my c++ apps and never had a problem. Like msserver said if you post some errors, or some more specifics I am sure someone can help you figure it out.
```

//C++ hello world
#include <iostream>
using namespace std;

int main(){
	cout<<"Hello World!"<<endl;
	cin.get();/*instead of using System("pause")
			  *which doesn't work in *nix systems
			  */ 
}

```

You do not have to use a substitute for "System("pause"). My system does this by default.

Here are my Environment settings :
"shell to run commands in"
/bin/sh -c
"terminal to launch console programs"
gnome-terminal --window-with-profile=codeblocks -t codeblocks--$TITLE -x

(gnome-terminal is mildly customized. You only need the -x after gnome-terminal)

Also, code::blocks do have a ton of useful features, if you just go through the settings.

---

### Post by Nettoyer on 2008-09-22
Definitely use NetBeans, I just made the transition myself.

---

### Post by slavik on 2008-09-22
the stickies address that issue.

---

### Post by mssever on 2008-09-22
I find it fascinating that so many people have proposed answers to an unanswerable question. You can't debug code when you have no information to go by. No error message, no code sample. Therefore, the question is unanswerable.

And switching IDEs won't magically debug a program. I've never used Code::Blocks, so I can't comment on its features, but if it didn't work it wouldn't be one of the more popular C++ IDEs. So suggesting alternate IDEs won't solve the problem, either.

---

### Post by cmay on 2008-09-22
> I find it fascinating that so many people have proposed answers to an unanswerable question. You can't debug code when you have no information to go by. No error message, no code sample. Therefore, the question is unanswerable.

And switching IDEs won't magically debug a program. I've never used Code::Blocks, so I can't comment on its features, but if it didn't work it wouldn't be one of the more popular C++ IDEs. So suggesting alternate IDEs won't solve the problem, either.
exactly why i ask for the compiler log to rule out the most common course of the problem. missing the build-essential package.

judging from this
> One of my problems is that my ubuntu computer isn't working right now, so I can't boot it up and give you the exact problems, but after I would write a program in a console application it would say that my code had errors which it did not because I had just ran that code in Visual C++ 2008 Express Edition in Windows and it worked (it was just a simple hello world application)
and me being far from a expert i would say that was a good guess at least :).
i come from the dev-cpp forums where one is expected to post compiler log short description of problem and the code in question otherwise the answers will be very simply go read **this before you post**.then again if OP had installed other IDE and missing build essentials was in fact the problem there would be no point in installing new IDE.
OP does ask for another IDE to get the programming done.
> I have tried code::blocks, but cannot get any of my programs to work. Are there any better ones or will I still have dual-boot to get my programming done?

even that i maybe not the right one to do so i have often been meaning to suggesting the sticky have a post compiler log code in question and short description of problem as posting rules. maybe even as replacement for HOW TO ASK QUESTIONS THE SMART WAY. since no matter if one already read  document or not this is as far as i can see simply the golden three posting rules that will most ligtly make sure one get a answer from someone that knows a solution based on the actual problem. it will also make others learn much more from reading it .as a matter of my humble opinion. i think i hereby will consider this suggestion made and silently accept if the sticky is out of my reach to influence in such manner. 
one can only hope to do so much anyway. i like to be here in these forums so i will not hopefully not make enemyies over such sticky suggestions. :)

---

