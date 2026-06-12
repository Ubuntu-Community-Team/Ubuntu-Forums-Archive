---
title: "ANJUTA can not find GCC -"
date: 2007-02-18
forum: Programming Talk
---

### Post by ubuntu1sttimer on 2007-02-18
I am a fairly recent UBUNTU user with 6.06. I would like to try to learn to do some simple programing in C++. I used Synaptic Package Manager to install ANJUTA 1.2.4a and Glade. Interested in ANJUTA for now.  Tried "Hello World" and get the following:

Compiling file: main.c ....
gcc -Well -g -cc "main.c" -o "main.o"
sh: gcc: command not found

I checked in terminal and gcc is not found. I do have gcc-4.0 which seems to work using it's name in terminal. Do not know if this is a UBUNTU or ANJUTA problem. Have not found a way to get ANJUTA to use gcc-4.0.

What do I need to do to get this working? Any assistance will be most appreciated.

---

### Post by Wybiral on 2007-02-18
Have you installed "build-essential"?

Why is it using gcc and a ".c" file for a c++ project?

---

### Post by ubuntu1sttimer on 2007-02-18
Was not aware that I needed "build-essential".  Have installed it and ANJUTA now compiles my hello world. If I follow correctly, it should now make it into an executable file. That is not happening. Is there some other package that needs to be installed. 

While on that, is there a way for me to find out what other packages like "build-essential" need to be installed? I was under the apparently incorrect impression that Synaptic does that automatically.

---

### Post by Wybiral on 2007-02-18
You might want to consider using g++ and gcc from the command line first, instead of having to learn an IDE and C/C++ at the same time.

If simple C/C++ programming is all you need to do, then a text editor and the command line are more than enough to program with.

Wish I could help you as far as anjuta goes... But I don't use it.

"build-essential" is basically all you need to use gcc/g++ (unless you are using non-standard libraries in your code)

---

