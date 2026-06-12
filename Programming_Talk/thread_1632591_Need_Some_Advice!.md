---
title: "Need Some Advice!"
date: 2010-11-28
forum: Programming Talk
---

### Post by Arthur.Felty on 2010-11-28
Hello Everyone!

Name's Art, I'm pretty new to the Ubuntu Operating system, but as of right now windows 7 is giving me a ration of crap as far a c compiling and executing goes. I've tried Windows XP to no success. I'm currently pursuing an associates degree in computer programming C Basic. My teach has referred me to Linux for my Course work. So here is my question, Windows versus Linux? Which one has more functionality with what I'm looking for and what resources should I download for this? 



Arthur Felty
SPC US Army
[EMAIL="Arthur.Felty@gmail.com"]Arthur.Felty@gmail.com[/EMAIL]

---

### Post by trent.josephsen on 2010-11-28
Linux unquestionably has more flexibility and better resources when it comes down to C programming.  As for resources, all you need is an editor and a compiler.

I use Vim for an editor, but it has a steep learning curve, so if you don't like it, I recommend jEdit.  As for a compiler, there are several, but gcc is the big name and you're unlikely to need anything else.  The build-essential package contains gcc and everything else you're likely to need for building C projects.

Both can be installed from the repositories.  From a terminal:
```
$ sudo apt-get install jedit build-essential
```
That command line will install jedit and all the packages in build-essential.  (I'd tell you how to do it in the GUI, but I've actually forgotten.)

Once you have everything installed, save your source file with a .c extension and run
```
gcc -o binary source.c
```
to compile source.c and put the output in a file named binary.  Then you can run the resulting program with
```
./binary
```

Hope this helps you get started!

---

### Post by Arthur.Felty on 2010-11-28
trent.josephsen thank you for the post! Thats exactly what I needed. C basic is like learnin russian its crazy. I downloaded them and compilation is going smooth. But debugging is another story man.

---

