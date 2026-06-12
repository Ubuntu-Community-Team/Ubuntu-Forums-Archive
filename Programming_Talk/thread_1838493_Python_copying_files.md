---
title: "Python copying files"
date: 2011-09-03
forum: Programming Talk
---

### Post by Metul Burr on 2011-09-03
I am taking an Object Orienting Programming class in college using Python.
I wrote the "hello world" program and it runs if i input
```
./helloworld.py
```i don't understand what this page is trying to convey? Could someone put this in more simple terms please?
```
Executable Python Programs
This applies only to Linux/Unix users but Windows users might be curious as well about the
first line of the program. First, we have to give the program executable permission using
the chmod command then run the source program.
$ chmod a+x helloworld.py
$ ./helloworld.py
Hello World
The chmod command is used here to change the mode of the file by giving execute
permission to all users of the system. Then, we execute the program directly by specifying
the location of the source file. We use the ./ to indicate that the program is located in the
current directory.
To make things more fun, you can rename the file to just helloworld and run it as
./helloworld and it will still work since the system knows that it has to run the program
using the interpreter whose location is specified in the first line in the source file.
What if you don't know where Python is located? Then, you can use the special env
program on Linux/Unix systems. Just change the first line of the program to the following:
#!/usr/bin/env python
The env program will in turn look for the Python interpreter which will run the program.
So far, we have been able to run our program as long as we know the exact path. What if
we wanted to be able to run the program from anywhere? You can do this by storing the
program in one of the directories listed in the PATH environment variable. Whenever you
run any program, the system looks for that program in each of the directories listed in the
PATH environment variable and then runs that program. We can make this program
available everywhere by simply copying this source file to one of the directories listed in
PATH.
$ echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/X11R6/bin:/home/swaroop/bin
$ cp helloworld.py /home/swaroop/bin/helloworld
$ helloworld
Hello World
We can display the PATH variable using the echo command and prefixing the variable name
by $ to indicate to the shell that we need the value of this variable. We see that
/home/swaroop/bin is one of the directories in the PATH variable where swaroop is the
username I am using in my system. There will usually be a similar directory for your
username on your system. Alternatively, you can add a directory of your choice to the PATH
variable - this can be done by running PATH=$PATH:/home/swaroop/mydir where
'/home/swaroop/mydir' is the directory I want to add to the PATH variable.
This method is very useful if you want to write useful scripts that you want to run the
program anytime, anywhere. It is like creating your own commands just like cd or any
24
Python en:First Steps
other commands that you use in the Linux terminal or DOS prompt.

```

---

### Post by LemursDontExist on 2011-09-03
The info you quoted is all about how the linux shell interprets a script.

By default for the shell to be able to run a script, the script must start with a shebang - something like ```
#!/usr/bin/env python
``` which tells the shell what program to use to interpret the script, otherwise the shell has no way to know how to interpret the script.  The env program tells the shell to run the python program using the standard system environment including the path.  Since env is always located in /usr/bin this allows the shell to find the python executable on any system even if it isn't stored in a standard location as long as it's in the system path.

The script must also be marked as executable that's what ```
chmod a+x helloworld.py
``` is about.  Otherwise any old script could easily be accidentally run, potentially doing damage to your system.  If you're curious you can read all about chmod [here]("http://en.wikipedia.org/wiki/Chmod").

These two factors will allow you to run the script using ```
./helloworld.py
``` if you're in the directory containing the script - and presumably your script already does this.  The './' is to tell the shell where to find the script - i.e. in the current folder, since by default the shell doesn't look in the current folder for programs to execute.

If, furthermore, you'd like to be able to run the script from any directory it needs to be in the system path - the list of directories the shell searches for commands.  Generally, /home/username/bin is a normal part of your user's path variable so you can run files you put in there without the './'.  Finally, the '.py' on the file is entirely unnecessary for it to run, and conventionally, scripts that you want to run as commands have no extension, so you rename the file to 'helloworld' instead of 'helloworld.py'.  All this lets you run your program from the shell just by entering

```
helloworld
```

All in all, this has nothing really to do with python, and everything to do with the linux shell.  For your programming class, I wouldn't imagine you really need to worry about this.  I hope this answers your question!

---

### Post by Pynalysis on 2011-10-05
> **lemursdontexist said:**
> the info you quoted is all about how the linux shell interprets a script.

By default for the shell to be able to run a script, the script must start with a shebang - something like ```
#!/usr/bin/env python
``` which tells the shell what program to use to interpret the script, otherwise the shell has no way to know how to interpret the script.  The env program tells the shell to run the python program using the standard system environment including the path.  Since env is always located in /usr/bin this allows the shell to find the python executable on any system even if it isn't stored in a standard location as long as it's in the system path.

The script must also be marked as executable that's what ```
chmod a+x helloworld.py
``` is about.  Otherwise any old script could easily be accidentally run, potentially doing damage to your system.  If you're curious you can read all about chmod [here]("http://en.wikipedia.org/wiki/chmod").

These two factors will allow you to run the script using ```
./helloworld.py
``` if you're in the directory containing the script - and presumably your script already does this.  The './' is to tell the shell where to find the script - i.e. In the current folder, since by default the shell doesn't look in the current folder for programs to execute.

If, furthermore, you'd like to be able to run the script from any directory it needs to be in the system path - the list of directories the shell searches for commands.  Generally, /home/username/bin is a normal part of your user's path variable so you can run files you put in there without the './'.  Finally, the '.py' on the file is entirely unnecessary for it to run, and conventionally, scripts that you want to run as commands have no extension, so you rename the file to 'helloworld' instead of 'helloworld.py'.  All this lets you run your program from the shell just by entering

```
helloworld
```

all in all, this has nothing really to do with python, and everything to do with the linux shell.  For your programming class, i wouldn't imagine you really need to worry about this.  I hope this answers your question!

+1

---

