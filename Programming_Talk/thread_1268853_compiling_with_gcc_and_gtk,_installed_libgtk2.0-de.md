---
title: "compiling with gcc and gtk, installed libgtk2.0-dev but needs libgtk1.5-dev"
date: 2009-09-17
forum: Programming Talk
---

### Post by Hansmc on 2009-09-17
I am totally new at programing on Linux and was trying to follow this tutorial: [http://www.gtk.org/tutorial1.2/gtk_tut-2.html](http://www.gtk.org/tutorial1.2/gtk_tut-2.html).

I put the sample code in a file called base.c. Saved it and ran 
```
gcc ~/Documents/gtk/base.c -o ~/Documents/gtk/base `gtk-config --cflags --libs`
```

This is the error it is giving me:
```
The program 'gtk-config' is currently not installed.  You can install it by typing:
sudo apt-get install libgtk1.2-dev
bash: gtk-config: command not found
 . . . 
```

But I did install libgtk2.0-dev, pulse gnome-core-devel and build-essential and libgtk2.0-doc. So I have a few questions.

Is my input file ~/Documents/gtk/base.c?
Is my output file ~/Documents/gtk/base?
Why am I getting that error?

Thanks

---

### Post by MadCow108 on 2009-09-17
edit: overread gtk-1.2
did you install libgtk1.2-dev as told or just 2.0?

for gtk+2 use pkg-config instead:
pkg-config --libs --cflags gtk+-2.0
maybe also works with gtk 1.2 check pkg-config --list-all to see if its there

---

### Post by Ratscallion on 2009-09-17
Ok, your error says that you need to install something, so, 9 times out of ten, if you follow that command, it may help. May I suggest using cd to go to the directory of your input file. For example, if it was (as it seems to be) in ~/Documents/gtk/ then go 
```
cd Documents/gtk
```
gcc/g++ works in the following way:
gcc/g++ (depends on what you want to use, both are practically the same) then a -o parameter for compiling, and then your output, then your input. In the example I'm using wiggle as the name for the source code and the output file/executable

```
gcc/g++ -o wiggle wiggle.cpp
```

Then, if no errors are in the code, you simply go ./wiggle and it runs.

---

### Post by Hansmc on 2009-09-17
> **MadCow108 said:**
> edit: overread gtk-1.2
did you install libgtk1.2-dev as told or just 2.0?
No, is that the best thing or should I try and use the 2.0?

> **MadCow108 said:**
> for gtk+2 use pkg-config instead:
pkg-config --libs --cflags gtk+-2.0
maybe also works with gtk 1.2 check pkg-config --list-all to see if its there

So my command would look like this
```
gcc ~/Documents/gtk/base.c -o ~/Documents/gtk/base `pkg-config --libs --cflags gtk+-2.0`
```
Insted of this:
```
gcc ~/Documents/gtk/base.c -o ~/Documents/gtk/base `gtk-config --cflags --libs`
```

I ran ```
pkg-config --list-all
``` and it listed a lot of stuff, but I am not sure what I am looking for. Thanks

---

### Post by Hansmc on 2009-09-17
> **Ratscallion said:**
> Ok, your error says that you need to install something, so, 9 times out of ten, if you follow that command, it may help. May I suggest using cd to go to the directory of your input file. For example, if it was (as it seems to be) in ~/Documents/gtk/ then go 
```
cd Documents/gtk
```
gcc/g++ works in the following way:
gcc/g++ (depends on what you want to use, both are practically the same) then a -o parameter for compiling, and then your output, then your input. In the example I'm using wiggle as the name for the source code and the output file/executable

```
gcc/g++ -o wiggle wiggle.cpp
```

Then, if no errors are in the code, you simply go ./wiggle and it runs.

Thanks for the info! I will put the -o first (and use cd).

---

### Post by Hansmc on 2009-09-17
Thanks every one. I ran this ```
gcc -o base base.c `pkg-config --libs --cflags gtk+-2.0`
``` and it worked.

---

### Post by Ratscallion on 2009-09-17
Try it without the pkg bits... If it doesn't work, keep them, but if it does, there's no need to add extra code and remember it when you don't need them.

---

### Post by MadCow108 on 2009-09-17
if your using gtk2 now better change to the right tutorial:
[http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)
this is a tutorial for gtk2

---

### Post by Hansmc on 2009-09-17
> **Ratscallion said:**
> Try it without the pkg bits... If it doesn't work, keep them, but if it does, there's no need to add extra code and remember it when you don't need them.

What is pkg bits?

---

### Post by Hansmc on 2009-09-17
> **MadCow108 said:**
> if your using gtk2 now better change to the right tutorial:
[http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)
this is a tutorial for gtk2

Thanks. I was not sure how I was going to make this work. That will make it a lot easer.

---

### Post by Ratscallion on 2009-09-17
These bits
```
`pkg-config --libs --cflags gtk+-2.0`
```

---

### Post by MadCow108 on 2009-09-17
he probably means taking the output of pkg-config and removing unnecessary  libraries and flags.
[http://library.gnome.org/devel/gtk-tutorial/stable/x111.html](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html)
this page maybe helps you decide what you need.

but I'd advise against that in the beginning because the only drawback of using all is (slightly) increased compile time.
The compiler can figure out on its own what it needs and what not.

---

### Post by Ratscallion on 2009-09-17
I was simply saying that you may not need those bits and could therefore try not using them in the terminal.

---

### Post by Hansmc on 2009-09-17
> **MadCow108 said:**
> he probably means taking the output of pkg-config and removing unnecessary  libraries and flags.
[http://library.gnome.org/devel/gtk-tutorial/stable/x111.html](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html)
this page maybe helps you decide what you need.

but I'd advise against that in the beginning because the only drawback of using all is (slightly) increased compile time.
The compiler can figure out on its own what it needs and what not.

> **Ratscallion said:**
> I was simply saying that you may not need those bits and could therefore try not using them in the terminal.

Ok, Thanks. I will just keep going through the tutorial and work more with that after I know a little more about what I am doing. Thanks for the link.

---

