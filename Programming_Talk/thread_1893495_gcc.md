---
title: "gcc"
date: 2011-12-10
forum: Programming Talk
---

### Post by 681ankit on 2011-12-10
i have problem in compiling c or cpp programs ...

error:

no such file conio.h 


i tried following::but dont help me
-> sudo apt-get install build-essential
->sudo apt-get install g++
and also tried ncurses..:(

---

### Post by carranty on 2011-12-10
I can't be sure without more info but I'm guessing your not specifying the path to your file correctly.  Correct usage for compiling a C file is

```
gcc path/to/file

```


Please post your commands along with errors to this thread.

---

### Post by tomdkat on 2011-12-10
> **681ankit said:**
> i have problem in compiling c or cpp programs ...

error:

no such file conio.h 


i tried following::but dont help me
-> sudo apt-get install build-essential
->sudo apt-get install g++
and also tried ncurses..:(
From what I've been reading online, conio.h was used for DOS programs.  In this thread:

[http://www.daniweb.com/software-development/c/threads/17584](http://www.daniweb.com/software-development/c/threads/17584)

someone suggests using ncurses, as you indicated you also tried. What I'm thinking you'll need to do is find the equivalent function(s) in ncurses that would need conio.h for in the program you're trying to compile.

So, if your program calls function "foo()" and that function would be prototyped in conio.h, you would find an equivalent to "foo()" in ncurses, if an equivalent function existed.

Follow me?

Peace...

---

### Post by docbop on 2011-12-10
Here's a workaround if you like....

[How to use conio in gcc]("http://www.techbite.in/2010/05/how-to-use-with-gcc.html")

---

### Post by The Cog on 2011-12-10
Nice link, docbop. I've seen other people wanting to use conio.h as well.

Moved to programming talk.

---

### Post by lkraemer on 2011-12-23
681ankit,
If you have your source code in a subdirectory named testbgi, located
at /home/user, you can just copy the conio.h file from your DOS
machine to your source subdirectory.  Now, with your source.c also there
you will need the following line inserted in your source.c file:
> 
#include "conio.h"

making sure there is no #include <conio.h> line in your source.

Now, assuming you are located at your source diectory, you should be able to
compile your code with:
```

pwd
gcc -g testbgi.c -o testbgi.exe

```
OR use this for more info:
```

gcc -Wall -g testbgi.c -o testbgi.exe

```

To use gdb, install gdb and then use:
```

gdb ./testbgi.exe

```
Once gdb comes up, tap the "l" (lowercase "L") key and you will see a listing.
Reference man gdb for more info.

If you install ddd (Data Display Debugger) you will have lots of fun!
```

man ddd

```
OR just execute your code with:
```

./testbgi.exe

```
 
For linking with additional libs, you will need to setup your paths,
then do something like:
```

gcc -g -DWITH_X -c ufc.c -o ufc.o
gcc -g -DWITH_X ufc.o -o ufc.exe -L. -lTurboCu -lX11 -lpthread -lncurses -lc 
./ufc.exe

```

Let us know how it goes.........

As you get further in the process, if you want more info on setting your paths let me know.
I have created a document that will save you lots of time and headaches.

lk

---

### Post by trent.josephsen on 2011-12-23
What?  Copying the header file into the current directory won't solve anything; you need to link with the libraries that do the real work.  <conio.h> refers to one of half a dozen non-portable libraries that mostly aren't available on Linux and which no self-respecting programmer should even consider using.

This is another one of those things like void main() and fflush(stdin) which should be squished whenever it appears.

---

### Post by lkraemer on 2011-12-23
trent.josephsen,
If you can calm down, quit squaking, and come down from the ceiling.......

Of course you are 100% correct........and just because I forgot to include the TurboC-source library information in the first post is 
no reason to go ballistic.  A Simple question would have been sufficient!

The routines I've included are from the header file, and most are
in the TurboC-source library.  If 681ankit needs some of the ones that
aren't available, perhaps you would be willing to assist him by creating 
them.


clreol		(void);
clrscr		(void);
delline		(void);
gettext		(int left, int top, int right, int bottom,
				 void *destin);
gettextinfo	(struct text_info *r);
gotoxy		(int x, int y);
highvideo	(void);
insline		(void);
lowvideo	(void);
movetext	(int left, int top, int right, int bottom, 
				 int destleft, int desttop);
normvideo	(void);
puttext		(int left, int top, int right, int bottom,
				 void *source);
textattr	(int newattr);
textbackground	(int newcolor);
textcolor	(int newcolor);
textmode	(int newmode);
wherex		(void);
wherey		(void);
window		(int left, int top, int right, int bottom);


cgets		(char *str);
cprintf		(const char *format, ...);
cputs		(const char *str);
cscanf		(const char *format, ...);
getch		(void);
getche		(void);
getpass		(const char *prompt);
kbhit		(void);
putch		(int c);
ungetch		(int ch);

If you'll kindly view my first posting you should see some reference to
-lTurboCu, which you already know about.

After all, we are all here to learn, and we all learned a lot from your
three line post.  Thanks for your valuable input!  Enough Said!

Good Day Sir!

Moderators:  Please Monitor!

lk

---

### Post by trent.josephsen on 2011-12-23
Why would I bother implementing non-standard functions in an archaic library that has literally been outdated since I was a babe in arms?

There is no excuse for using <conio.h> in new code.

---

### Post by nothingspecial on 2011-12-23
Can we stick to answering the question please. Discussing whether or not it should be used is for a different thread :)

Thank you.

---

### Post by Bachstelze on 2011-12-23
> **nothingspecial said:**
> Can we stick to answering the question please.

What was the question? ;)

---

### Post by Arndt on 2011-12-23
> **lkraemer said:**
> trent.josephsen,

If you'll kindly view my first posting you should see some reference to
-lTurboCu, which you already know about.




Where does one obtain this libTurboCu? The usual repositories don't seem to have it.

---

