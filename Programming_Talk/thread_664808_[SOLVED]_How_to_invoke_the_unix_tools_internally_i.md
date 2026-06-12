---
title: "[SOLVED] How to invoke the unix tools internally in c programming?"
date: 2008-01-11
forum: Programming Talk
---

### Post by fyplinux on 2008-01-11
Hi,

There are lots of useful tools under Unix/Linux, I am wondering how to use these tools when programming. for example, I would like to invoke "ls" to get all the files of a directory, How could I call "ls" when I am programing within C, and how could I get the output of ls.

I think the best way is to merge these tools into my own code, do you have any idea to do this? 

Thank you.

---

### Post by LaRoza on 2008-01-11
You can look into the POSIX C functions, and see if system() fulfils your needs.

---

### Post by fyplinux on 2008-01-11
yeah,System() could execute the command, and the result would be printed to the terminal by default, but how could I capture the output for the further execution of my own program?

---

### Post by LaRoza on 2008-01-11
> **fyplinux said:**
> yeah,System() could execute the command, and the result would be printed to the terminal by default, but how could I capture the output for the further execution of my own program?

You should use the POSIX or other functions, but you could dump the results of the command into a file.

```

system("ls > files.txt");
//open files.txt and read each line

```

---

### Post by Wybiral on 2008-01-11
You should look for "[unistd.h]("http://www.opengroup.org/onlinepubs/007908775/xsh/unistd.h.html")" and check out its various function, I would recommend using one of the [exec]("http://linux.about.com/library/cmd/blcmdl3_execv.htm")'s and a [pipe]("http://www.gnu.org/software/libc/manual/html_node/Creating-a-Pipe.html").

---

### Post by fyplinux on 2008-01-11
> **LaRoza said:**
> You should use the POSIX or other functions, but you could dump the results of the command into a file.

```

system("ls > files.txt");
//open files.txt and read each line

```

What do you mean by "use the posix or other functions"??

---

### Post by stroyan on 2008-01-11
The popen() system call can be used to open a pipe to or from a command.

---

### Post by CptPicard on 2008-01-11
On the other hand, your fundamental idea is wrong. You most certainly don't want to run "ls" to get a list of files in a directory, for example -- the shell "ls" is just a wrapper around filesystem functions that you should be calling directly from your own code instead of taking the detour.

Properly designed command-line tools in general implement the functionality in a library that can be used programmatically, and then just write a small executable to make use of that library.

---

### Post by fyplinux on 2008-01-11
> **CptPicard said:**
> On the other hand, your fundamental idea is wrong. You most certainly don't want to run "ls" to get a list of files in a directory, for example -- the shell "ls" is just a wrapper around filesystem functions that you should be calling directly from your own code instead of taking the detour.

Properly designed command-line tools in general implement the functionality in a library that can be used programmatically, and then just write a small executable to make use of that library.


Could you give some information on how to and where to find these libraries? I am a new comer, and I am eager to know about this. I think it will be very useful. Thanks.

If there is, the most library I want to use is "diff" and "patch",:)

---

### Post by CptPicard on 2008-01-11
Use google :P also, as it's all open source, nothing stops you from actually looking at the insides of, say, diff and even "borrowing" the bits you want.

Same applies to ls -- look at the source and see how it interfaces with the OS.

---

### Post by fyplinux on 2008-01-11
It might be a bit tricky to look at all the code

---

### Post by CptPicard on 2008-01-11
The more code you look at, the better at reading code you become. And in particular in the case of ls, the source can't be too big. All filesystem manipulations in particular should be done using syscalls, not by strange hacks wiring together shell tools from C.

---

### Post by YourSurrogateGod on 2008-01-11
> **fyplinux said:**
> It might be a bit tricky to look at all the code

Google is your friend :) (that's how I got the below file.)

[http://www.ia.pw.edu.pl/~jurek/js/os/w06.pdf](http://www.ia.pw.edu.pl/~jurek/js/os/w06.pdf)

In there you'll find a little bit of info about how to work with chmod and chown in C.

---

### Post by dwhitney67 on 2008-01-11
If all you want to do is find the contents of a directory, then use opendir() to open the directory, then use readdir() in a loop to get the individual contents (i.e. files and/or other directories).

If it is other system commands you want, then system() is generally the choice most often used.  If you require the output, then direct it to a file, then parse the file.

Many system functions have counterparts in the C library, so always check the man-pages.  You can use:

```
man -aw *cmd*
```

---

### Post by Jessehk on 2008-01-12
[http://www.gnu.org/software/libc/manual/html_node/File-System-Interface.html#File-System-Interface](http://www.gnu.org/software/libc/manual/html_node/File-System-Interface.html#File-System-Interface)

It's fairly easy to list the contents of a directory from within C. Read up.

---

