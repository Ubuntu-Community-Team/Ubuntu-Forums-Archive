---
title: "New To Ubuntu, and need help"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Xarver on 2008-08-26
Hi I just installed Wubi Ubuntu Installer about a few hours ago and need some help. I just installed SciTE and want to know how I can run this program I made to test it:
```
#include <iostream>
using namespace std;

int main()
{
	cout << "Hello, SciTE!";
	cin.get();
	return 0;
}

```
I click build and it works but when I click compile it says:
>make
make: *** No targets specified and no makefile found.  Stop.
>Exit code: 2

I see an executable and I can't run it.
Any help appreciated!!!

---

### Post by damis648 on 2008-08-26
I have no idea what I am talking about. :popcorn: Removed.

---

### Post by Xarver on 2008-08-26
Uh, what?
I have no idea what you're trying to say here!

---

### Post by WRDN on 2008-08-26
For C++, you would use a makefile or you may use GCC when compiling.

To compile with GCC, use the command:

```

g++ file.cpp -o executable_name

```

For creating Makefiles, [this]("http://mrbook.org/tutorials/make/") tutorial may be of use.

Remember that, before you can compile, you will need the [essentials]("http://packages.ubuntu.com/hardy/build-essential"):

```
sudo apt-get install build-essential
```

---

### Post by damis648 on 2008-08-26
Removed.

---

### Post by Dougie187 on 2008-08-26
You can't use make because you didn't make a makefile.

A makefile is just a series of commands that run to "make" a project.

To compile your program, you need to use the following commands.
```
sudo apt-get install build-essential
```
After this installs. You have to move to the directory.
Since this is a C++ project, you need to use the g++ compiler. To use it you would type
```
g++ filename.cpp
```
and then to run. Simply type
```
./a.out
```

If you want to make a makefile, once you are in the directory with your c++ file, just make a file called "Makefile" and add the following code to it, replacing filename with the name of the c++ file.
```
all:
     g++ filename.cpp
     ./a.out
```

Then you can just type make and it will compile and run the program for you.

---

### Post by WRDN on 2008-08-26
> **damis648 said:**
> Sorry, my bad. I do not know much about "make" and compiling, but I beleive the "makefile" wold be the file containg the source code, correct me if I am wrong. Take your source code and save it in some directory, call it "makefile". Now use "cd" to change into that directory and then try using "make" again.

A makefile doesn't contain source code. It contains instructions to the compiler for what files to compile, and what output(s) to create.

---

### Post by Xarver on 2008-08-26
So that's how to run it?
I have to run the terminal, and type ./testing and it works?
Cool...
But when I double click testing, it doesn't run...
Why?

:)

---

### Post by starcannon on 2008-08-26
Heres a little guide to a hello world program using c++ on a linux box.
The author used vi for his text editor, but scite will work fine as well.

[http://www.linuxquestions.org/linux/answers/Programming/Building_C_programs_on_Linux_0](http://www.linuxquestions.org/linux/answers/Programming/Building_C_programs_on_Linux_0)

Hang in there, you'll figure out the basics pretty quickly.

---

### Post by Xarver on 2008-08-26
Thanks, does anybody know of any guide that teaches most/all of the basic linux commands???

---

### Post by starcannon on 2008-08-26
> **Xarver said:**
> So that's how to run it?
I have to run the terminal, and type ./testing and it works?
Cool...
But when I double click testing, it doesn't run...
Why?

:)

It needs somewhere to put te cout, in this case a terminal. You will need to write a more complex program to have it open a window and put the text on it when you click the executable file. You could write a little bash script to do this for you. Something say like this:
Open a new text file using your favorite editor and enter:
```

#!/bin/sh
/home/user_name/some/path/to/executable_name
exit 0

``` 
save to a meaningfulname, say executable_name.sh

Then in terminal make the sh script executable:
```
chomod a+x ./script_name
```

and finally click on the script and choose the "Run in Terminal" option.

Enjoy.

---

