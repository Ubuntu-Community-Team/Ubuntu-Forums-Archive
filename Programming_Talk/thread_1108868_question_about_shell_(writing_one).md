---
title: "question about shell (writing one)"
date: 2009-03-28
forum: Programming Talk
---

### Post by cmay on 2009-03-28
hi .
i am at the beginning of following this small tutorial on how to write a shell. 
[http://linuxgazette.net/111/ramankutty.html](http://linuxgazette.net/111/ramankutty.html)
which is a basic hello world shell example with no build in commands and of course no features such as redirection and programmable language constructions.

the question i have is as follows and please bear in mind i am not a student nor taking some kind of education and have no programming experience as such.

as i have gathered from around my understanding is as follows 
when the shell or a program sends out the message '\n' the kernel and not the commandline interprenter thinks it should react to this and move the cursor to next linje 
and so it is whit '\a' which also triggers a kernel call that makes computer go bleep 
and thats  why a language contruct is almost always the same as in c regarding the escape sequenses. also why a '\\' is needed to print out the actual '\' sign it self. 

it is possible to use the ascii codes to print a file and so on which is not a feature of the shell but a bunch of system calls or interupts that goes from keyboard input into codes that then goes into kernel that will react to as example '\a' as make beep or just print the letters abc to what ever stdin,stdout,stderr is defined as in the context of user pressing letter 'a'.

all i want to know  is if this right or am i wrong in this perception. 

 i hope the question is formulated proper enough so what i am asking is clear enough.
 i am looking for ressurces in my own language which i had no luck wiht and the closest i got is a book from early  days of programming microproccesors and dos assemler programming and turbo pascal 5.0 i had from the library. 
 its not exactly what i needed but i read the whole thing and tried to make as much sense out of it as i could. which is not that much. 
 
 any pointers in the right direction for writing a shell that actually works and ease my procces of understanding of what goes on 
 would be very great. 
 
 thanks for the time.

---

### Post by stroyan on 2009-03-28
There are several participants in terminal input and output.
It can be very complicated if you want to follow through every level.
The two very common situations are using a terminal emulator in X or using the linux console.
It is also common to use ssh from a remote system.
Some folks still use serial terminals as well.

Here is a sketch of the steps in input and output for the gnome-terminal and linux console-

INPUT
user - keyboard - kernel(kbd) - X server - gnome-terminal - kernel(pty/termios) - shell
or
user - kernel(console) - kernel(termios) - shell

OUTPUT
shell - kernel(termios) - gnome-terminal - X server
or
shell - kernel(termios) - kernel(console)

The various possible situations are made to look somewhat similar by conventions that present the same basic termios interface to the shell.  But there can be differences in the escape sequences that different terminals or terminal emulators use.  That is handled by the terminfo API that describes what escape sequences and other terminal features a particular terminal or terminal emulator uses.

You can learn a lot about the different layers by reading the following man pages-

man console_codes
man kbd
man termios
man pty
man stty
man terminfo

Backslash quoting is actually applied directly by the shell and by the C compiler.  They just both use the same convention.
It is a common convention used by many parsers.

Newline character interpretation is a little bit in termios and a lot in the terminal emulator.  (Termios may map \n to \n\r.)

Bell character interpretation is all in the terminal emulator.

---

### Post by cmay on 2009-03-28
thanks. i must have gotten many things a bit wrong i can tell. 
nice to know that.

 i am very happy with the information and tonight when i have some time i going to read trough the tutorial i linked to and i am going to write the shell as a first exercise.
i read it trough last night at 4 in the morning actually before i went to bed but i am going to read it proper again later. i have also snooped around in the bashshell sources to see what is there and its a lot of work if one wants a shell like that. i am happy to settle for a hello world shell . 

thanks for your time it means a lot to me.

---

