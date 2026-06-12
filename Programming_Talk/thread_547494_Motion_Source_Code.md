---
title: "Motion Source Code"
date: 2007-09-10
forum: Programming Talk
---

### Post by abuntu-handicapped on 2007-09-10
Hi all,

Im trying to access the source code for motion in linux. Somebody said i can access the source at the address below but i cant find it...and not really sure what im looking for.

I actually have more than 1 question.

1. If i have the source code, can i run the code and it will capture motion just like when run in linux?

2. What is the best program to use to view this source code? Where can i download this program?

3. Would someone pls mind checking out the web site i was given and see if they can find the source code? Im not lazy or anything but im not exactly sure what im looking for and have been looking ages.

[http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)

Thanks in advance

Abuntu_handicapped

---

### Post by loell on 2007-09-10
you can get the source code from ubuntu repo

by doing

```
apt-get source motion
```

navigate to the current directory where you invoke the command, usually in your home directory.


depends on what viewer you like, you can use gedit for a starter ,

or anjuta or vim.

---

### Post by abuntu-handicapped on 2007-09-10
thanks for hte speedy reply loell.

Downloaded it. Thanks. much easier that way.

I think if i explain what i am trying to do it might make things bit easier.

I want to have the code so that when i 'run' the code in whatever program i view the code, the webcam will start capturing and saving frames. 

 'motion_3.2.3-2.1.dsc'
 'motion_3.2.3.orig.tar.gz'
 'motion_3.2.3-2.1.diff.gz'

these are the files that were downloaded. whats the easiest way to go about this?

---

### Post by loell on 2007-09-10
unpack or extract 'motion_3.2.3.orig.tar.gz'

compile the code by , .**/configure** , **make**

then execute **./motion -c any_confi_filename.conf**

---

### Post by abuntu-handicapped on 2007-09-10
loell, thanks for taking the time to help but i dont think im on the same page as you.

i have extracted the file and it is now on my desktop motion_3.2.3-2.1.diff

I then go to terminal-neil@neil-desktop and 
cd motion-svn
cd trunk

i type 
./configure
and it does a whole lot of stuff

i type
make

i type
sudo ./motion -c any_confi_filename.conf 

and the webcam starts capturing.

My problem is that my lecturer wants to see the code and click on a button to run it and THEN it starts capturing. So i should be in some sort of programming program, no?

Abuntu_handicapped

---

### Post by loell on 2007-09-10
you could open it and run it in anjuta IDE.

---

### Post by abuntu-handicapped on 2007-09-10
my friend sitting next to me says that it is not C++

Is the code in C++?

is it maybe visual basic?

is motion_3.2.3-2.1.diff the correct source code file ?

I have checked motion.c and it looks like C++. Is this the source code?

---

### Post by Tomosaur on 2007-09-10
> **abuntu-handicapped said:**
> my friend sitting next to me says that it is not C++

Is the code in C++?

is it maybe visual basic?

is motion_3.2.3-2.1.diff the correct source code file ?

I have checked motion.c and it looks like C++. Is this the source code?

If the filename ends with '.c', then it is likely the code is C. C++ code filenames usually end with .cpp.

Are you sure your lecturer doesn't want **you** to program the interface to Motion?

---

### Post by abuntu-handicapped on 2007-09-10
**Are you sure your lecturer doesn't want you to program the interface to Motion? **

Yeah im sure.

Thanks will see what i can do with that c file

---

### Post by abuntu-handicapped on 2007-09-11
Okay, I got the source code (i think its the source code) from motion.c. I compiled it and ran it and it started the web cam and started capturing etc.I was happy.

Then just to see what it would do i deleted everything in motion.c (made a backup cope first) and compiled and executed it again. It worked fine?? Does anyone know why this is?

Perhaps i should delete motion from the system and run the source file afterward?

---

### Post by fct on 2007-09-11
Wait, you're supposed to program an interface to a C program and you can't even tell C from Visual Basic? Shouldn't you be learning the language?

---

### Post by Tomosaur on 2007-09-11
> **abuntu-handicapped said:**
> Okay, I got the source code (i think its the source code) from motion.c. I compiled it and ran it and it started the web cam and started capturing etc.I was happy.

Then just to see what it would do i deleted everything in motion.c (made a backup cope first) and compiled and executed it again. It worked fine?? Does anyone know why this is?

Perhaps i should delete motion from the system and run the source file afterward?

I'm a bit confused :S

Can you lead us through everything you've done so far?

What do you mean by 'deleted everything in motion.c'? Do you mean you opened the text file, deleted every line in the file, then saved it?

---

### Post by loell on 2007-09-11
> **abuntu-handicapped said:**
> Okay, I got the source code (i think its the source code) from motion.c. I compiled it and ran it and it started the web cam and started capturing etc.I was happy.

Then just to see what it would do i deleted everything in motion.c (made a backup cope first) and compiled and executed it again. It worked fine?? Does anyone know why this is?

Perhaps i should delete motion from the system and run the source file afterward?

are you sure there are no errors outputted by the compiler when you did this?


or it could be that there's an existing motion program in your system installed ,

and executed **motion** rather than going to the source directory and execute

**./motion**

---

