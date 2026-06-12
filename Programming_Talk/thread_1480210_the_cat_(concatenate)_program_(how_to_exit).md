---
title: "the cat (concatenate) program (how to exit)"
date: 2010-05-11
forum: Programming Talk
---

### Post by i8163264128 on 2010-05-11
I need to write a program that emulates cat but I couldn't find anywhere how (or if) you can exit cat when you open it with no arguments and it just concatenates stdin to stdout. 

Is it possible to exit cat in that case ? if yes, what is the trigger ?

---

### Post by John Bean on 2010-05-11
EOF (End Of File) character - Ctrl+Z from keyboard.

---

### Post by i8163264128 on 2010-05-11
thanks.

---

### Post by Bachstelze on 2010-05-11
> **John Bean said:**
> EOF (End Of File) character - Ctrl+Z from keyboard.

Er, no, EOF is Ctrl-D. Ctrl-Z will just suspend it.

---

### Post by i8163264128 on 2010-05-11
anyone with a third opinion ? :)

anyway, I'll implement suspend too then. damn, this is so boring... :(

---

### Post by John Bean on 2010-05-11
> **Bachstelze said:**
> Er, no, EOF is Ctrl-D. Ctrl-Z will just suspend it.

Ctrl-D is EOT (end of transmission) not EOF.

---

### Post by John Bean on 2010-05-11
> **i8163264128 said:**
> anyone with a third opinion ? :)

anyway, I'll implement suspend too then. damn, this is so boring... :(

Heh. Have fun :-)

PS: EOF really is Ctrl+Z ... but of course "end of file" isn't the only way to end the read from stdin.

---

### Post by jwbrase on 2010-05-11
> **i8163264128 said:**
> anyone with a third opinion ? :)

anyway, I'll implement suspend too then. damn, this is so boring... :(

No... Suspending is acted upon by the OS, not the program (though the OS does notify the program and the program can choose to handle the signal in a special manner, up to and including not suspending). Ctrl-Z is the key for end-of-file, but on UNIX like systems it's generally also the key for suspend (unless suspend is set to another key combo).

Cat does end on Ctrl-D. It may also do so on Ctrl-Z when the OS doesn't intercept it first, but I don't know if that's true or not. When the OS does intercept Ctrl-Z, it sends the process a signal, and I don't think cat does anything with that signal, so you shouldn't have to do anything to implement suspending. You'd have to do something to implement *not* suspending, as I understand it.

---

### Post by trent.josephsen on 2010-05-11
cat ends on EOF, wherever that is encountered.  By design, there is no way to put a literal EOF in your file.  Ctrl-D is a key shortcut used to send an EOF to the currently running program (I believe it is used by the shell).  Similarly, Ctrl-Z is a shortcut used to suspend the currently running program.  Ctrl-C, Ctrl-S, Ctrl-@, Ctrl-Q and Ctrl-V are all captured and interpreted by the shell as well.

You can embed ^C, ^D, ^S, ^Z and all the others into a stream by using Ctrl-V first.  cat will willingly read these bytes and print them back out as it is designed to do -- they aren't meaningful to cat itself.

---

### Post by i8163264128 on 2010-05-11
thanks everyone for the input. I guess I'll make it exit on EOF and be done with it. whether the shell catches it first isn't that big of an issue since as I see it the reading stops anyway on pressing ^z or ^d.

---

### Post by trent.josephsen on 2010-05-11
When Ctrl-Z is pressed, cat may well stop reading, but it won't return or print output either because its process has been suspended.  Type 'fg' to bring it back to the foreground, at which point it will resume what it was doing -- and if it was waiting for input when you suspended it with Ctrl-Z, it will continue waiting for input until you send it an EOF with Ctrl-D or kill it.

This thread called to mind a very concise implementation of cat, in Perl:

```
#!/usr/bin/perl -p
```
;)

---

### Post by Cracauer on 2010-05-11
cat(1) wouldn't be my first choice as a base for an interactive program.

What is the objective here, anyway?

---

### Post by i8163264128 on 2010-05-11
> **Cracauer said:**
> cat(1) wouldn't be my first choice as a base for an interactive program.

What is the objective here, anyway?

no objective, just "homework".

---

### Post by trent.josephsen on 2010-05-11
What language are you using?

```
#!/usr/bin/perl -p
```;)

---

### Post by Lux Perpetua on 2010-05-11
> **John Bean said:**
> EOF (End Of File) character - Ctrl+Z from keyboard.> **John Bean said:**
> Heh. Have fun :-)

PS: EOF really is Ctrl+Z ... but of course "end of file" isn't the only way to end the read from stdin.I don't know what you're talking about. EOF isn't a character; a file ends because it ends, not because it contains a specific character. This is obviously a problem if the input "file" is interactive input from a terminal, so the terminal needs a way to simulate "ending" the input file. That's what Ctrl+D does (typically). 
> **i8163264128 said:**
> anyone with a third opinion ? :)

anyway, I'll implement suspend too then. damn, this is so boring... :(
No, I'm afraid you don't get to implement suspend; your program simply "gets suspended." You cannot catch SIGSTOP (the suspend signal).

---

