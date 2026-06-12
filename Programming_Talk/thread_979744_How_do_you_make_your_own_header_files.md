---
title: "How do you make your own header files?"
date: 2008-11-12
forum: Programming Talk
---

### Post by 7raTEYdCql on 2008-11-12
Just as programming practice i want to make a Text Editor using C.
I want to specify my functions which are to be used in this program in a seperate header file. How do i do this.

---

### Post by 7raTEYdCql on 2008-11-12
One more thing. I have never written a program as extensive as the above before. All the programs i have written are the small codes that do not much.Like the eg. they have in the text. This will be the first project like thing i will be approaching. Can someone give me some tips for writing big programs like the one above. Or some examples of long programs which are available online.

Thanking you,
Mehrzad.

---

### Post by dwhitney67 on 2008-11-12
Generally, a header file (in C) has an filename extension of .h.  In C++, some developers use .h or .hpp.

A header file will have a format such as:
[php]
#ifndef FILENAME_H
#define FILENAME_H

// include header files here to allow this header file to compile;  do
// not include header files that are not required by this header file!

// add your function definitions here

#endif
[/php]

The first part of the header file above (the #ifndef and #define) are use to prevent multiple inclusions of this file within another module or header file.  You can read up more about this by Googling.

---

### Post by dwhitney67 on 2008-11-12
> **i.mehrzad said:**
> One more thing. I have never written a program as extensive as the above before. All the programs i have written are the small codes that do not much.Like the eg. they have in the text. This will be the first project like thing i will be approaching. Can someone give me some tips for writing big programs like the one above. Or some examples of long programs which are available online.

Thanking you,
Mehrzad.

I am an command-line user; I never use IDEs because I think they are mere sugar-coating around the command-line.

When I need to compile one or two modules, I instruct gcc to compile/link the modules such as:
```
gcc -Wall -pedantic -std=gnu99 module1.c module2.c
```

Of course, I do not like typing that long gcc statement every time, so I have defined it within my ~/.bashrc file as:
```

alias gcc='gcc -Wall -pedantic -std=gnu99'

```
That means I can then compile with:
```
gcc module1.c module2.c
```

When I dealing with a "formal" project, then I will go out of my way to use a Makefile.  Makefile scripting is a unique language in itself; there are references/tutorials available on the web.

---

### Post by iponeverything on 2008-11-12
:) use apt-get to grab the source for for some of the most basic editors out there, and have a look at them.

vi
pico
nano

---

### Post by Tony Flury on 2008-11-12
I would suggest that you start small, and seperate the User Interface and the application.

I would probably write the text handling code first, storing, reading and writing strings, inserting, finding, deleting, and replacing

once these basic functions work, you can then add a GUI on top - and interface that with the text functions, and work out how to display the text, move the cursor etc.

Also i would sit down with a pen and paper and plan it.and set your self small tasks to complete - that way you can tick them off and feel you are making progress.

---

### Post by hessiess on 2008-11-12
main.c
[PHP]#include <display.h>

int main()
{
	display("Hello World\n");
}[/PHP]

display.h
[PHP]void display(char *text);[/PHP]

display.c
[PHP]#include <stdio.h>
#include <display.h>

void display(char *text)
{
	printf("%s", text);
}[/PHP]

makefile```

main : main.c
	gcc -g main.c display.c -I ./ -o main 
		
clean :
	rm -rf main
```

Note the '-I ./' in the makefile, this tells GCC to look in the current directory for includes.

---

### Post by nvteighen on 2008-11-12
Actually, a text-based text editor in C may be really much difficult than a GUI one: GUI toolkits have widgets that automate the buffering and editing of text, so your work will be related to file handling, interface, etc.

If you go for text-based, you'll need the ncurses library to have a nano-like interface.

As Tony said: **Always** (but I put it in bold!) separate interface from implementation. This is not just referred to User Interfaces, but to any kind of code that calls other lower-level code... Break stuff into pieces and create mechanisms of combination between them and respect those mechanisms by yourself... Even if you know how you implemented the text buffer, you should be able to use it without knowing how it works internally (for example, if you go for a GTK+ based text-editor, you'll be using GtkTextView & friends without ever knowing how it was created).

Good luck, have fun and ask any question you have!

---

### Post by Nemooo on 2008-11-12
Could you provide further explanation on "separate interface from implementation"? I'm not sure I fully understand it.

A little example would be great.

---

### Post by hessiess on 2008-11-12
Seperate the interface drawing into a independent set of functions from the 'core' of the program(keybord input, editing text in the text data structure and the like).

---

### Post by Delever on 2008-11-12
> **Nemooo said:**
> Could you provide further explanation on "separate interface from implementation"? I'm not sure I fully understand it.

A little example would be great.

It means you should divide problems into smaller ones, put solutions to separate functions, group functions into separate files or classes.

Better, look at someone else's code.

---

### Post by nvteighen on 2008-11-12
Separating interface from implementation means that you work using black-boxes (have you ever heard about abstraction?).

For example, say I'm developing a card game (well, actually I am... look at my sig). It's quite logical that I first create a representation for cards as a basic element; I give that object some way to communicate with the world, for example, a function that creates a card with a given value and suit, a function to access a card's value and another one to access a card's suit. These three functions are interfaces to the card's implementation (how I "build" cards) which I haven't even told to you... and you don't even care, because my interface is enough for you to program about cards (you can create them and access the most relevant data from them).

Ok, now I have a card... And with a card "type" (or "class"), I'm able to think about decks, for example. Again, I create a function to create decks and then, ways to access stuff in a deck... That's the interface... no matter how I built the deck. I can even change the whole implementation but keep the interface and you'd never notice (so, I can improve that section of code without breaking the rest). Another "black box": you know what it does (or is supposed to do), but no how it does it.

There are two ideas on how this should be done: top-down programming vs. bottom-up programming. The first one consists on designing the interface before the implementation... and even code relying on "wishful thinking" (you code using objects you haven't implemented yet, but as you already planned what interface they'll have you're alright). The second one is always first implement and then create the interface... and usually going from the most elementary objects (those nearest to the programming language's built-ins) to the most abstract ones (coded almost on top of "black boxes"). If you ask my opinion, I'm more fond of bottom-up style, but sometimes, for convenience, I step into top-down "wishful thinking".

Hope this was clearer. It's partly based on SICP Lecture 1 [http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-10.html#%_sec_1.1](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-10.html#%_sec_1.1) The language used there is Scheme (a Lisp dialect), but the concepts are valid for any language.

---

### Post by Nemooo on 2008-11-12
I understand now and guess that's also how I've been thinking. Create functions for greater abstraction, so the functions can be improved/changed without having to worry about the interface (and vice versa).

Generally it makes changes on the implementation and interface easier because they're seperated and independant?

---

### Post by snova on 2008-11-12
Precisely. By separating interface from implementation you can change the implementation without affecting code that depends on it (hopefully).

The interface says *what* it does, the implementation says *how*. They can be separated, and this is the use of headers. It is even possible, with plugin systems, to replace one with another.

Edit: No, they are not independent, at least not completely. The implementation must always conform to the interface.

---

