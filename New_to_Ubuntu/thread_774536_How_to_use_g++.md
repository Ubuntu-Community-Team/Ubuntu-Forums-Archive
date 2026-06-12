---
title: "How to use g++"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by rednauj on 2008-04-29
Hi I need to know how to use g++ to compile my c++ programs. Please step by step I maybe getting lost in the process.
Please help me, thanks.

---

### Post by spiderbatdad on 2008-04-29
well...make sure you are in the same directory the program is in. Make sure the program is named with a capitol C...like HelloWorld.C

then run ```
g++ HelloWorld.C -o HelloWorld
chmod a+x HelloWorld
```
The second command makes the file executable, so you can run it.

[http://www.intap.net/~drw/cpp/cpp02_01.htm](http://www.intap.net/~drw/cpp/cpp02_01.htm)

---

### Post by rednauj on 2008-04-29
This is what I made:

juan@juan-desktop:~$ g++ HelloWorld.C -o HelloWorld
g++: HelloWorld.C: No such file or directory
g++: no input files

---

### Post by Steveway on 2008-04-29
Instead of HelloWorld.C you need to use the file that you have written.
And don't forget that it is case-sensitive.

---

### Post by rednauj on 2008-04-29
Ok but when I use the file says the same thing.
What's the meaning of this: No such file or directory
I'm missing something?

---

### Post by spiderbatdad on 2008-04-29
It sounds like you are in the wrong directory...assuming you are using the name of your file. If your file is on your desktop. you need to change directory to the desktop like this: ```
cd Desktop
``` Desktop is case sensitive, so cd desktop wouldn't work. You can also use the tab key to auto complete for you, so if you type in "cd De" and hit the tab key, the terminal will complete the command for you. If you only type "cd D" you will get a system beep. This is because Documents is also a folder in your /home/user directory.

---

### Post by rednauj on 2008-04-29
Ok now the problem is, How can I run the program?

---

### Post by spiderbatdad on 2008-04-29
```
./name_of_program
```

---

### Post by spiderbatdad on 2008-04-29
You can also make launchers (icons) to run the program...let's say you right click on the panel and select add to panel...then create custom launcher. Give the program a name and in the command area, put the path. So if it is in your home directory... command: /home/your_user_name/program_name
Now the program is the compiled/executable. You can also change the icon.

---

### Post by stchman on 2008-04-29
> **spiderbatdad said:**
> well...make sure you are in the same directory the program is in. Make sure the program is named with a capitol C...like HelloWorld.C

then run ```
g++ HelloWorld.C -o HelloWorld
chmod a+x HelloWorld
```
The second command makes the file executable, so you can run it.

[http://www.intap.net/~drw/cpp/cpp02_01.htm](http://www.intap.net/~drw/cpp/cpp02_01.htm)

The extension is not important.  Most people use the following:

.c for C programs
.cpp for C++ programs

The executable command is not necessary as gcc/g++ makes the resulting compiled file executable.

Change to the directory where the source is and do the following:

```

g++ -o Helloworld Helloworld.c
./Helloworld

```

---

