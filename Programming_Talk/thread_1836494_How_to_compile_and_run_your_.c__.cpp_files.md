---
title: "How to compile and run your .c / .cpp files"
date: 2011-08-31
forum: Programming Talk
---

### Post by Sepehr_M on 2011-08-31
Hello,
I'm just a newbie in Ubuntu and I put my time searching for a way on how to compile and run **.c**/**.cpp** files in terminal and I'd like to share what I got with you. If you have an [IDE]("http://en.wikipedia.org/wiki/Integrated_development_environment"),  you're almost done, you can easily code your program and execute it via  specified IDE but what if you don't have? You can just download  [Code::Blocks]("http://www.codeblocks.org/") which is a light-weight IDE and compile/run your desired  file or you can follow the following steps to simply compile and run it  through your terminal :wink:

1. [B]Installing the build-essential package 
[/B]You can easily install build-essential by typing the following command in your terminal (Ctrl + Alt + T):```
*sudo apt-get install build-essential*
```2. **Installing g++**
You need g++ compiler to compile and run your source code, for getting it, simply type the following command in your terminal:
```
sudo apt-get install gcc g++
```3. [B]Source code 
[/B]Create a file with **.c** extension for a C program or **.cpp** if it's a C++ program.

4.[B] Directory
[/B]Now go to the directory in which you saved your file using **cd **command. (e.g. *cd Desktop*)

5. [B]C program compiling
[/B]I assume your filename is **test.c **if you have saved it as  another name, you can simply change the command with the correct  filename. For compiling and running, simply type the following command  in terminal:
```
gcc test.c -o test
```6.[B] C++ program compiling
[/B]If your file is a **.cpp**, simply change the previous command to the following one:
```
g++ test.cpp -o test
```7. [B]Permission
[/B]If you got a permission error, you need to change file to an  executable one. For doing such, simply type the following command in  terminal:
```
chmod +x test.cpp
```8. [B]Running program
[/B]Now that all is done, you can run your source code by typing the following command in terminal:
```
./test
```**Note : **If you don't use *-o *option while compiling, the name of the executable file will be **a.out** by default.

---

### Post by kbaumen on 2011-08-31
This is nothing new and probably there are already hundreds of tutorials for doing this, but still, kudos for making it clear and elaborate. Definitely helpful if you're just starting out.

---

