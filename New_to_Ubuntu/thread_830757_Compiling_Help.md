---
title: "Compiling Help"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Tharakanuwanpro on 2008-06-16
If we downloaded a source code then how do we compile it . Tell me the Packages .There is a package that comes with Ubuntu Hardy , I installed it from the Synaptic Package Manager but i can't find the menu where its at . Tell me how to compile source codes .

---

### Post by hyper_ch on 2008-06-16
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by pedro_orange on 2008-06-16
Sorry, but this post makes no sense.

If you are trying to compile from source you will need to have a compiler installed:

```
sudo apt-get install build-essential
```

And you will need to follow the packages instructions for compiling it. Eg. ./configure or make all etc.

Also what package did you install from Synaptic?

---

### Post by nothingspecial on 2008-06-16
If you installed with synaptic you don`t need to compile it. What did you install?

---

### Post by Tharakanuwanpro on 2008-06-16
G++ or something like that . But i can't find where it is. Its not on the menu

---

### Post by jcr1 on 2008-06-16
Is the question basically, after installing something new, it does not always automatically put a new shortcut in the menu structure, therefore new users being not sure how to fire up the newly installed app.?

If so, this is a question I would like to see an answe to too.

---

### Post by Sef on 2008-06-16
> Is the question basically, after installing something new, it does not always automatically put a new shortcut in the menu structure, therefore new users being not sure how to fire up the newly installed app.?


Three possibilities:

1) System > Preferences > Main Menu > Check for it and tic the box next to the app.

2) Alt+F2: type name of app (exactly as it is spelled)

3) Applications > Accessories > Terminal: type name of app.  It will come up, but it will be closed if the terminal is closed.

---

### Post by pedro_orange on 2008-06-16
> **Tharakanuwanpro said:**
> G++ or something like that . But i can't find where it is. Its not on the menu

G++ is the GNU C++ compiler.

It is included in the build-essential package. Therefore, open a terminal and type in:

```
sudo apt-get install build-essential
```

That will install G++ along with a few other compilers.

Using G++; it's not in the menus. It's a compiler, not an application.
If you need to know how to use it, there are tons of guides on the net. But it's a command line compiler.

So to compile something I'd so something like:

```
g++ -Wall -pedantic input.c -o output.o
```

To compile input.c and create an object.o file to run/execute.
To see the manual of g++ open a terminal and type the following:

```
man g++
```

---

### Post by markbuntu on 2008-06-16
Many, many of the applications available in Synaptic are not graphical applications and so will not show up in the menus but can be used from the terminal. 

Many applications do not come with their own launchers so you need to make a launcher if you want it in your menus or panels.

---

### Post by jcr1 on 2008-06-17
Just a small example, I installed firefox-3 from apt-get and this did not replace my firefox 2 launcher button, nor give me the option to get rid and 2 and use 3 as default. It did not add a launcher in the menu... it took me a while to figure out how to open it... had to open from terminal and find out exactly what I needed to type... something like firefox-3.0 or similar. 

Bit of a pain, but I'm not complaining...its just difficult and not always obvious how to launch some newly installed apps.

(upgraded since to hardy, and firefox3 is default)

---

