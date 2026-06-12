---
title: "creating an executable file"
date: 2009-01-06
forum: Programming Talk
---

### Post by jboy012000 on 2009-01-06
Hi All,

I have just started to learn c++, I have started with the first program Hello World, I have written my source code in GEDIT and saved it as a .cpp file, now what is the procedure in terminal to turn my .cpp file into an executable file.

Thanks very much.

John

---

### Post by Bachstelze on 2009-01-06
```
c++ -o helloworld helloworld.cpp
./helloworld
```

---

### Post by jboy012000 on 2009-01-06
Hi,

I typed the code as you suggested but I got the following reply

john@three-peaks:~$ c++ -o helloworld helloworld.cpp
c++: helloworld.cpp: No such file or directory
c++: no input files
john@three-peaks:~$ c++ -o helloworld helloworld.cpp ./helloworld
c++: helloworld.cpp: No such file or directory
c++: ./helloworld: No such file or directory
c++: no input files


Did I do something wrong, do I have to add the location of the file?

Thanks

---

### Post by jespdj on 2009-01-06
You have to do that in the directory that contains the source file. It's a good idea to learn the basics of the terminal (the shell, bash).

Also, before you do it, make sure you install the compiler and necessary supporting files:
```
sudo apt-get install build-essential
```
People usually use the GNU C++ compiler on Ubuntu, which is called **g++** instead of c++.

To compile:
```
g++ helloworld.cpp -o helloworld
```

And then to run your program:
```
./helloworld
```

Also please read the sticky topic at the top of the forum: [Programming Tools and References](http://ubuntuforums.org/showthread.php?t=1006662) and especially [FAQ: Compiling your first C or C++ programs](http://ubuntuforums.org/showthread.php?t=689635)

---

### Post by kcode on 2009-01-06
Install the virtual package by issuing the following command:

```

sudo apt-get install build-essential

```

EDIT: Ok...its solved above!.

---

### Post by jboy012000 on 2009-01-07
I think I will do as you suggest and learn the basics of BASH shell before I go any further.

Thanks very much

John

---

