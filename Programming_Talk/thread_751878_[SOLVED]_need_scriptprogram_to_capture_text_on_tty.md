---
title: "[SOLVED] need script/program to capture text on tty1 terminal console"
date: 2008-04-11
forum: Programming Talk
---

### Post by @vijay@ on 2008-04-11
is it possible to capture the text on the tty1  terminal console (ctrl+alt+F1)   as it is  (as u see on the monitor)  to a text file    
and update it every 2 secs ???
can someone please give me script or program

thanx in advance

---

### Post by kerry_s on 2008-04-11
hmm, depends on what you want to capture.

for instance using->
command >> command.txt

appends all out put to that text file, using a single " > " will replace any text in the file with the new.

---

### Post by WW on 2008-04-11
Use the **screendump** command; see **man screendump**.

E.g.
[php]
while true; do screendump 1 > screenshot1 ; sleep 2 ; done
[/php]
will copy tty1 to the file screenshot1 every two seconds.  You'll need root privileges to run screendump, so use sudo.

---

### Post by nanotube on 2008-04-11
also consider ttysnoop (the linux equivalent of bsd's 'watch'), which will enable you to monitor any tty "live".

---

### Post by @vijay@ on 2008-04-11
thanx for the quick replies 

@ WW
i want the output to be in text format

@nanotube
how to use ttysnoop ???
i tried "ttysnoop 1"
but it says cannot connect to server :confused:

---

### Post by WW on 2008-04-11
> **@vijay@ said:**
> 
@ WW
i want the output to be in text format

It is.  From the beginning of the man page:
```

DESCRIPTION
       The screendump command dumps the contents of virtual console N , (or the current console
       if N is omitted) to standard out.

```
The file that I called screenshot1 is a text file.

---

### Post by nanotube on 2008-04-11
> **@vijay@ said:**
> thanx for the quick replies 

@ WW
i want the output to be in text format

@nanotube
how to use ttysnoop ???
i tried "ttysnoop 1"
but it says cannot connect to server :confused:

man ttysnoop for details :)

but if all you really want is a text file with the tty content, screendump is probably your best bet, so follow WW's advice.

---

### Post by @vijay@ on 2008-04-13
thanx alot guys tht worked like a charm
screendump 1 > screenshot1 didnt work but
screendump /dev/tty1 > file has done the job :popcorn:

u guys just dont know how much u helped me :lolflag:

AND
is there anyway to get the cursor position like which row and column ????

---

