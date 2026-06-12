---
title: "problems with gcc.....(permission denied)"
date: 2006-09-06
forum: Programming Talk
---

### Post by navneet.net on 2006-09-06
hello..
the problem is that when i try to run the .o file , i get an error message..permission denied.
the file was compiled with no errors.
iv done c prgs. on FC before but never faced such a problem..

??

---

### Post by electricshoes on 2006-09-06
are you running with sudo ?

---

### Post by navneet.net on 2006-09-07
no.....actually its not clear how to use sudo exactly?
does it make any diff?

---

### Post by woody_green on 2006-09-07
How about sudo -s?
Then try to run it.

---

### Post by navneet.net on 2006-09-07
this is what exactly happens or is happening now.....

navneet@ubuntu4fedora:~/C$ sudo -s
root@ubuntu4fedora:~/C# ./try1.o
bash: ./try1.o: cannot execute binary file
root@ubuntu4fedora:~/C#

---

### Post by thumper on 2006-09-07
The .o is an object file, not an executable file.  It needs to be linked before it is executable.

```
gcc -o try1 try1.c
./try1
```
You may be using the -c flag which says "just compile, don't link".

---

### Post by thumper on 2006-09-07
Damn non-responsive server.

---

### Post by navneet.net on 2006-09-07
hello..
thanks a lot...
its working now.....
though strange as when i used FC it never happened to be the case....
moreover then what is the significance of gcc -c  ?

thanks again.

---

### Post by thumper on 2006-09-07
You use the -c flag when you are compiling multiple files but you then want to link into a single executable.
```

gcc -c -o foo.o foo.c
gcc -c -o bar.o bar.c
gcc -o foobar foo.o bar.o

```

---

### Post by navneet.net on 2006-09-07
so basically you want to say there is a diff b/w an object file and an executble ?

then how is it so that we can straight away run the binaries? they are object files or execs.?

---

### Post by thumper on 2006-09-07
Yes there is a difference between an object file and an executable.

The command "gcc -o foo foo.c" does both the compile and link phase and doesn't leave you with an object file lying around.

You cannot execute an object file.

---

### Post by navneet.net on 2006-09-10
thanks a lot thumper....that really helped.
one more thing.......iv made a small program to check password  entered by the user..now i want to implement it as the default login prg for my pc....i.e,when a user logs on to ubuntu on my pc ...he gets instead of default login screen ,he sees my passwd prg. 
how should i do away with that?
thank you.

---

### Post by thumper on 2006-09-10
That would be a really bad idea.

---

