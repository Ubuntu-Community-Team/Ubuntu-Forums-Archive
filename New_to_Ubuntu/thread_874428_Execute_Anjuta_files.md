---
title: "Execute Anjuta files"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Daswebmastri on 2008-07-29
This probably needs to go under programming, but I'm still a newbe when it comes to programming in Linux.

For years, I used a language called BlitzBasic. The IDE was simple, you compile and run, and then build an .exe

In anjuta, I can get a standard "hello world" program to run in the IDE, but how do I get that file to run alone without an IDE up? How do I make it a true executable? Thanks.

---

### Post by KIAaze on 2008-07-31
Once you compile it, you automatically get an "exe".
Look in "~/Projects/<projectname>/src". It should contain a file with the same name as the project, which is executable.

You can run it from any terminal by typing ./<programname> once you are in the src directory, or by typing the full path to it (/home/.../src/<programname>).

It's also possible to run it by double-clicking it in a file-browser, but then the output will probably not stay open (it quits once the program is finished).

Anjuta also allows you to create a tarball (configure/make/make install system) or to install it on your PC so you can run it like any other program without entering the whole path.
Look in the Build menu for those options.

---

### Post by Daswebmastri on 2008-08-01
THANK YOU!!! But why the ./ in front of the command line??? Thanks again!

---

### Post by Daswebmastri on 2008-08-01
Also, it won't run by double clicking it. I'm running Hardy, btw.

---

### Post by KIAaze on 2008-08-01
The ./ is necessary because the program isn't located in one of the directories of the PATH system variable.

It also makes sure that you run the program from the current directory instead of another with the same name contained in one of the PATH directories.

You can see the contents of the PATH variable by typing:
```
echo $PATH
```

> Also, it won't run by double clicking it. I'm running Hardy, btw. 
Check its properties to see if it's executable. (right-click->properties)
You can also easily make it executable from command-line by doing:
```
chmod +x <progname>
```
To check properties from command-line:
```
ls -l <progname>
```
It should contain some "x"s like this for example: rwxr-xr-x

r=read
w=write
x=execute

rwx/rwx/rwx
usr/grp/other

---

### Post by Daswebmastri on 2008-08-04
Okay, when I check the properties, it wants to use wine to open it. What program should I associate it with to run it by double clicking?

THanks again for your help

---

### Post by KIAaze on 2008-08-06
Sorry for the delay.

Yes, I just tested it myself, and indeed, by default, it tries to use Wine.

Just associate it with "xterm" (type it manually because it won't be in the list).

Even better would be "xterm -hold" because it will keep the terminal window open once the program is done. ;)

Note: I did a few tests and it seems you can only make the association work by default if the program has an extension like ".exe".
Otherwise, you can still open it easily by doing right-click -> open with xterm.

The name of the executable can be changed somewhere in the project options of Anjuta.

---

