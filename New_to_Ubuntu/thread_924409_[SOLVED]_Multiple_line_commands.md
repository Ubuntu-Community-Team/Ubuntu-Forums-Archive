---
title: "[SOLVED] Multiple line commands"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by getitright on 2008-09-19
Hi,

I am attempting to work with command lines and have a basic problem in that I am unable to enter multiple command lines. Pressing enter only executes the line. For example how would I enter the following:

sudo depmod -a
sudo modprobe ndiswrapper
tail /var/log/messages

---

### Post by Mornedhel on 2008-09-19
You would enter one line, then press enter, then enter the next one, and so on.

Alternatively, you could string them all in one command, as in :

command1 && command2 && command3

The '&&' means "Wait until the previous command has returned ; if it returned OK, continue ; if it didn't, stop here".

---

### Post by Paqman on 2008-09-19
Just do it one line at a time.

However, you can execute multiple commands in one go. The syntax would be:
```

first command && second command && third command

```

Although obviously it might not be sensible to string everything together like this. So just do one at a time if you're unsure. 

Top tip for cut'n'paste in Linux: just highlight the line to copy, then tap the mousewheel to paste into the terminal.

---

### Post by bodhi.zazen on 2008-09-19
Depending on what you want exactly ...

Use semi-colons for multiple commands :

command1; command2; command3

To split on multiple lines, use \

comand1;\ <enter>  #<enter> == hit enter key
>command2;\<enter>
>command3 <enter>

when you enter the second and third lines your prompt will change to a ">"
when you hit the enter after the 3rd command, all 3 will execute.
you can break lines anywhere you wish:

comm\
>and\
1

executes "command1"

==========

Logical constructs :

AND

command1 && command 2 

command 2 runs if command 1 is successful (no error messages)

OR

command1 || command2

command 2 runs if command1 exits with an error

=============

Single &

commmand1 & command2 => runs command1 in background and continues with command2

command1; command2 => runs command1 (in the foreground) then command2

Try :

sleep 10 ; ls
sleep 10 & ls

---

### Post by zvacet on 2008-09-19
On [URL="http://www.ibm.com/developerworks/aix/library/au-badunixhabits.html"]
this[/URL] link you will find basicly same answer as **bodhi.zazen** gave to you,but you will see same other command which you maybe find useful.

---

