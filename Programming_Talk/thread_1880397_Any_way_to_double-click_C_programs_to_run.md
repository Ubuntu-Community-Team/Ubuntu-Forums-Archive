---
title: "Any way to double-click C programs to run?"
date: 2011-11-13
forum: Programming Talk
---

### Post by gavin_attoe on 2011-11-13
I've been doing quite a bit of C programming lately, and was wondering if there was a way to make the program files able to execute with a double click.  I have been using "./" to run everything in the terminal window thus far.  Like is there any way to just compile it so it would have that ability like .exes do in Micro$oft OSs?

Any suggestions appreciated. :)

---

### Post by t1497f35 on 2011-11-13
It's unclear what you mean since C programs if compiled properly do execute at double click on any OS including Linux.

---

### Post by suspect x on 2011-11-13
You Can Try to use IDE tools such as ECLIPS and many others available for free

---

### Post by cgroza on 2011-11-13
I think you will need to create a launcher for your executable.
But really, using a text editor such as Geany will make it a lot easier.

---

### Post by jwbrase on 2011-11-13
> **t1497f35 said:**
> It's unclear what you mean since C programs if compiled properly do execute at double click on any OS including Linux.

I think what he's running into is that Linux DE's generally don't automatically open a terminal for programs that interact via the command line. So his program is running, but he's not seeing any evidence of it.

A kludgy fix (I'm not aware of a better one), would be to write a shell script named InsertProgramNameHere.sh that would call the program:

```
#/bin/bash
exec InsertProgramNameHere
```

Then, by double clicking on the shell script, he could get the Run/View dialog that you get for shell scripts (on GNOME at least), which has an option "Run in Terminal".

---

### Post by gavin_attoe on 2011-11-14
> **t1497f35 said:**
> It's unclear what you mean since C programs if compiled properly do execute at double click on any OS including Linux.

Actually I'm not seeing any evidence of my command line programs running when double-clicked, even those that take user input when run with "./"

[QUOTE=suspect x]
You Can Try to use IDE tools such as ECLIPS and many others available for free[/QUOTE]

[QUOTE=cgroza]I think you will need to create a launcher for your executable.
But really, using a text editor such as Geany will make it a lot easier.[/QUOTE]

I haven't tried compiling with an IDE such as Eclipse or Geany yet.  I'll give that a shot.  I've just been using gedit so far.

[QUOTE=jwbrase]Then, by double clicking on the shell script, he could get the Run/View dialog that you get for shell scripts (on GNOME at least), which has an option "Run in Terminal".[/QUOTE]

I was really hoping to avoid shell scripts, but you're right; they do work.  You can actually just type scripts into a text file without the ".sh" extension, then use properties to make them execute in the terminal, as you said.

BTW I'm using Ubuntu 10.04 Lucid Lynx.  I didn't want to risk an upgrade, but did pick up some Natty Narwhal desktop backgrounds for it :D


Edit:  I'm going with the IDE Geany that cgroza suggested.  It's very lightweight as opposed to Eclipse, and has the ability to run programs after compiling with some quick key shortcuts.  The built/compiled program still doesn't open on double click, but if I design a large program that I really need that for I'll go with either a launcher, or shell script like jwbrase suggested.  Thank you all for submitting answers.

---

