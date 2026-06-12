---
title: "Need some help with acii code"
date: 2009-11-23
forum: Programming Talk
---

### Post by ThaDoctor99 on 2009-11-23
Hi all.
I got this thing in school where I at some point will have to figure out how to use these ascii codes in a application. So I thought it better to find the stuff I need before getting to that.
Anybody in here who can help.

---

### Post by MadCow108 on 2009-11-23
whats your problem?
ascii is just (the probably simplest possible) character encoding scheme.
It only maps characters to numbers:
[http://www.asciitable.com/](http://www.asciitable.com/)
theres nothing special about it

---

### Post by ThaDoctor99 on 2009-11-24
Okay but the thing I need for the assignment is that when the user push Alt+s for instance, then he is getting the save option in the program. I don't really care whether this is done with the ascii code or whatever, anybody got some ideas here.

---

### Post by Zugzwang on 2009-11-24
> **ThaDoctor99 said:**
> Okay but the thing I need for the assignment is that when the user push Alt+s for instance, then he is getting the save option in the program. I don't really care whether this is done with the ascii code or whatever, anybody got some ideas here.

This has nothing to do with ASCII codes. The answer to this question depends on the environment you are using, e.g.:
[LIST]
[*]DOS+Turbo Pascal without GUI library
[*]DOS+Turbo Pascal with Borland GUI Library
[*]C with Linux and NCurses
[*]C++ with QT
[*]etc...
[/LIST]

Without this information, you won't get help. Please also indicate why an answer to this problem would not solve your whole assignment at once.

---

### Post by Arndt on 2009-11-24
> **ThaDoctor99 said:**
> Okay but the thing I need for the assignment is that when the user push Alt+s for instance, then he is getting the save option in the program. I don't really care whether this is done with the ascii code or whatever, anybody got some ideas here.

You leave a lot of things undefined here. It's impossible to help, using only what you've written so far.

"The save option", "the program", I can only guess. Are you writing a program which should be able to do something particular when the user presses Alt-s? What language, what graphic toolkit (if any)?

You're unlikely to get ready-made solutions for homework here, but we can help to clear up misunderstandings or point you to the right direction for looking up more information (which your course material or your teacher really should be doing, of course).

---

### Post by ThaDoctor99 on 2009-11-24
sorry.
There is no graphics to be implemented, and it is first of all c++ on a dos platform, but I would like it to also compile on a linux box so I can test it at home...
The information which I can think of as of right now.
Dos Platform.
C++
I will define feature
I actually only need the help to figure out how to do things for
keyboard events with alt+s or something like that.
My teacher just told us we should look at extended ascii code.

---

### Post by Arndt on 2009-11-24
> **ThaDoctor99 said:**
> sorry.
There is no graphics to be implemented, and it is first of all c++ on a dos platform, but I would like it to also compile on a linux box so I can test it at home...
The information which I can think of as of right now.
Dos Platform.
C++
I will define feature
I actually only need the help to figure out how to do things for
keyboard events with alt+s or something like that.
My teacher just told us we should look at extended ascii code.

This is still very much underspecified, but I can guess some more: "extended ASCII" is the name for the 8-bit character set on MS-DOS which includes a lot of Western European letters, like åäöúß. I suppose pressing Alt-s on your DOS platform generates such a character. So the matter is simply one of detecting whether the character code is larger than 127. BUT, this is not portable at all. The modern way to represent other letters than ASCII is with Unicode. On the other hand you seem to want to use these characters for commands, not entering text. This is more or less what editors like Emacs do in a non-windowy environment. What will your program do? Be an editor? Should it react immediately to the Alt-s or do you have to enter a newline too?

---

### Post by ThaDoctor99 on 2009-11-24
It should be a accounting program so a newline for text input would be ok I suppose.
However I am more intruiged with the unicode is that portable ?

---

### Post by Arndt on 2009-11-24
> **ThaDoctor99 said:**
> It should be a accounting program so a newline for text input would be ok I suppose.
However I am more intruiged with the unicode is that portable ?

If a command followed by newline is alright, then I don't see why you need to bother with Alt-s and such things.

Can you show us the specification of the program?

Unicode is portable, but do you need to handle anything other than ASCII at all?

---

### Post by ThaDoctor99 on 2009-11-24
The reason I would need to bother with the Alt+s key combination is because it is a demand in school, I don't get why but it is.

---

