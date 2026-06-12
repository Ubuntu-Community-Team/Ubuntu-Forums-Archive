---
title: "C++ source file has become corrupt or something after running program"
date: 2012-08-10
forum: Programming Talk
---

### Post by Crash525 on 2012-08-10
In new to Linux and so far I like it. I am trying to learn how to write c++ programs and compile them using terminal and gedit. I have used Microsoft Visual Studio to make c++ programs before but I want to learn to do in in Linux. 

I had made a very simple c++ program. After I compile the program and run. The source file gets corrupted. It shows as a very long list of characters. I had made two programs so far, "Hello World" and a program that asks for your age and displays your age. The Helloworld program runs fine and I can go back to the source file and edit it if I want to. When I run the age program, after its been compiled it non usable.

I get this in my source file but its color different colors such asred green pink. I would post a screen shot but I have not figured out how to do that yet.

ELF\00\00\00\00\00\00\00\00\00\00\00\00\00\00P\854\00\00\00\\00\00\00\00\00\004\00 \00    \00(\00\00\00\00\00\004\00\00\004\804\80 \00\00 \00\00\00\00\00\00\00\00\00\00\00T\00\00T\81T\81\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\80\00\80    \00\00    \00\00\00\00\00\00\00\00\00\00\00\F8\00\00\F8\9E\F8\9E0\00\00\80\00\00\00\00\00\00\00\00\00\00\00\00\00\9F\9F\E0\00\00\00\E0\00\00\00\00\00\00\00\00\00\00\00\00h\0

Does anyone know why this is happening? 
Also if this is a repeat post im sorry I missed the original one.

Thanks.

---

### Post by Bachstelze on 2012-08-10
We can't help if you don't show us the code and the command(s) you are running.

---

### Post by nvteighen on 2012-08-10
You've overwritten your source file with your binary file (it starts with "ELF"), very possibly because you accidentally wrote the input filename as the output when invoking g++. There is no way to recover your source file from there... well, you can disassemble it, but you'll get ASM code, not C++.

---

### Post by Crash525 on 2012-08-10
heres the commands for terminal. I know i messed up some of the commands but here it is.

crash@crash-PC:~$ cd cpp/age
crash@crash-PC:~/cpp/age$ gedit age2.cpp
crash@crash-PC:~/cpp/age$ g++ age2.cpp -o age2.cpp
age2.cpp: In function &#8216;int main()&#8217;:
age2.cpp:7:7: error: &#8216;age&#8217; was not declared in this scope
crash@crash-PC:~/cpp/age$ g++ age2.cpp -o age2.cpp
crash@crash-PC:~/cpp/age$ ./ age2.cpp
bash: ./: Is a directory
crash@crash-PC:~/cpp/age$ ./age2.cpp
whats your age 25

 your age is 25.crash@crash-PC:~/cpp/age$ 



well heres the source code for it.

#include <iostream> 
using namespace std;

int main ();

{
int age;
cout<< "whats your age --> ";
cin>> age;
cout<< "\nYour age is " << age << ".\n";

return 0;
}

as nvteighen said it over written it with a binary file. I created a helloworld program and I did not over write it. how do I prevent it in this case? I can run the helloworld file as many times as I want and it will not overwrite it?

---

### Post by Bachstelze on 2012-08-10
The -o flag specifies the name of the file that the compiler writes. If it's the same as the name of the input file, it will be overwritten. Just specify a different name.

---

### Post by Crash525 on 2012-08-10
Awesome. Thank you for the info. Is there a way to not have it write another file, but only run the program? Like I said im still new to terminal and the commands.

---

### Post by Bachstelze on 2012-08-10
No, not with g++. The tcc compiler can do this, but it's a C compiler, not C++. If there's a C++ equivalent, I don't know it.

---

