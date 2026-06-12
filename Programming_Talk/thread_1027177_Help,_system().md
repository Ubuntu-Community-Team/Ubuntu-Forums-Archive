---
title: "Help, system()"
date: 2009-01-01
forum: Programming Talk
---

### Post by Nemix on 2009-01-01
ok i've been working with the system() function in C++, and i see that i can use it like i use the terminal. One thing i cant figure out how tp use a variable with it.

```
char name;
cin >> name;
system("mkdir /Coding/C++/<name>"); 
``` 

yeah that wont work but hopefully you will see what im trying to do =D

the project im working on is kinda more of a learning project, ill be trying to make a program which will make project folders and put a default main.cpp file in it and at the same time tell g++ to compile all the .cpp file with in a certain project folder =D
i kinda figured ill be using system() a lot within this.

---

### Post by jpkotta on 2009-01-01
There is probably a C++ way to do it, but I would use snprintf() from C.

You probably should use make instead of writing your own program.  This is exactly what make is for.

---

### Post by dwhitney67 on 2009-01-01
Are you just trying to create a new directory?  If so, use mkdir().

[php]
std::string dirname("/Coding/C++/");
std::string name;
int mode = 0755;

std::cin >> name;
dirname += name;

mkdir(dirname.c_str(), mode);
[/php]

---

### Post by Nemix on 2009-01-01
thanks for you replies:KS

the main reason as i said for me doing this project is to improve my skills in C++. 
may i ask whats the purpose is of:
```
int mode = 0755;
```

---

### Post by dwhitney67 on 2009-01-01
> **Nemix said:**
> thanks for you replies:KS

the main reason as i said for me doing this project is to improve my skills in C++. 
may i ask whats the purpose is of:
```
int mode = 0755;
```
The 'mode' is a bit-mask used in the mkdir() call to specify the permissions for the directory to be created.

In the example I provided, if the directory is created, it would have the following permissions:   rwxr-xr-x

rwx = %111 = 0x7
r-x = %101 = 0x5

---

### Post by jpkotta on 2009-01-02
When a numeric literal starts with 0, it is octal.  A better notation would have been, IMHO, 0o (like 0x), but we are stuck with it.  Permissions are often specified in octal because each digit has exactly three bits corresponding to read/write/execute.
```
man chmod
man 2 mkdir
```

---

