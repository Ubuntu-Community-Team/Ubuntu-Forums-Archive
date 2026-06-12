---
title: "how to compile and run c and c++ codes in ubuntu"
date: 2011-03-21
forum: Outdated Tutorials &amp; Tips
---

### Post by vivek.pandey on 2011-03-21
hi everyone 
i have seen many noobs asking for a good IDE for c and c++ when they switch to ubuntu.\
here is one of rhe easiest solution for their problem
requirements :
1) a text editor...you can use gedit,vi editor ,nano or kate.. a noob should look for gedit or kate...they are gui based
2) gcc and g++ compiler.. gcc is used for compiling your c codes .one can also use it for assembling assembly level codes though some modifications are required.  g++ is compiler for c++
how to get gcc or g++
gcc and g++ gets installed when you run this command ```
sudo apt-get install packagename 
```
now to get the name of the package . on terminal type gcc or g++ which ever compiler you want. you will get a list of packages(if that compiler is not installed) install the compiler

how to code

open a text editor and write your code

here i give an example of simple c++ hello world code

#include <iostream>
using namespace std;
int main()
{
  cout<<"hello world"<<endl;
  }

save it to the directory you want. if you save in home directory no need of changing your directory while compiling and executing but if you changed in some other directory change your directory to that particular directory using cd directory_path

first compile it

to compile type g++ filename

vivek@NEO:~$ g++ hello.cpp
vivek@NEO:~$ 

alternatively if your file in not in your home directory and you havent changed directory to the on where your file is ,you can compile as

g++ path_to_file
vivek@NEO:~$ g++ /home/vivek/codes/hello.cpp


if no error you will again get a prompt

to run or execute use 
./a.out 

vivek@NEO:~$ ./a.out
hello world
vivek@NEO:~$ 

similarly for c instead of g++ use gcc..

---

### Post by RJ12 on 2011-04-16
You should have also added that using the -o option can specify the file output name. Also do you need to chmod +x the file before you can run it, I usually always do this after compiling my programs.

---

### Post by vivek.pandey on 2011-04-18
> **RJ12 said:**
> You should have also added that using the -o option can specify the file output name. Also do you need to chmod +x the file before you can run it, I usually always do this after compiling my programs.

i guess we dont need to  use chmod +x...any file which can be read will have permissions to be executed... and as far as compiling and executing a program is considered i think this tutorial does it job but i will be very glad if you can explain here something about this 
-o thing as i havent used it..although i can search on net and write something about it but it is always good to ask the person who uses it.. i will be thankful to you

---

### Post by kashikr2 on 2011-04-20
> **RJ12 said:**
> You should have also added that using the -o option can specify the file output name. Also do you need to chmod +x the file before you can run it, I usually always do this after compiling my programs.

I think he is probably right.

---

