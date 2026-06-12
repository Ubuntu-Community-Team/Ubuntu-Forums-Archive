---
title: "is this a piping/redirection question?"
date: 2009-02-17
forum: Programming Talk
---

### Post by J05HYYY on 2009-02-17
okay, say if i had a file and a command
and i wanted to open the file with the command
how would i go about doing this using ksh?

there must be a standard way ...

help much appreciated

---

### Post by Tony Flury on 2009-02-17
It really does depends on the file type and the command you want to run.

Some commands will take the file directly as an input parameter.

Some commands will take is data off stdin(and therefore you need to either redirect or pipe the file into the command).

A pipe is normally used to connect stdout of one command to std in of another, where as a redirect will connect a file to stdout - or stdin - of a command.

The convention seems to be that if the input would normally expected to be in a file (for instance it could be a large file or not something that would be typed for each use) then the command will accept a file name as an input pramater.

the best thing to do is at a terminal 
```

man <command>

```
where <command> is the name of the command you are interested in (without the <,>).
That will provide you with the manual page for the command, and will tell you how you should use it.

---

### Post by J05HYYY on 2009-02-17
[I]Okay, let me rephrase.
I am using eeebuntu so please excuse the screenshots[/I]
[B]
Say I have a file at the directory located at /Programming/redirection/redirect.txt :[/B]
[CENTER]
[IMG]http://www.deviantart.com/download/113256075/J05HYYY__s_question_by_legizlegun.jpg[/IMG][/CENTER]


**I right click on the file and choose 'open with other application':**
[CENTER]
[IMG]http://www.deviantart.com/download/113256819/J05HYYY__s_question_2_by_legizlegun.jpg[/IMG][/CENTER]

[B]
I get this window:[/B]
[CENTER]
[IMG]http://www.deviantart.com/download/113257330/J05HYYY__s_question_3_by_legizlegun.jpg[/IMG][/CENTER]


**And using this textbox (etc.) I can use a 'custom command' to open the file **

[CENTER][SIZE="4"]... but how does this work?[/SIZE][/CENTER]

---

### Post by digitalvectorz on 2009-02-17
Wouldn't it just be something like:

```

prompt$ *program* file

```

I.E. (opening redirect.txt with vim and gvim)
```

prompt$ vim /Programming/redirection/redirect.txt
prompt$ gvim /Programming/redirection/redirect.txt


```

---

### Post by Can+~ on 2009-02-17
I don't know how really it is, but I'm guessing it's something like:

name: Text Editor
icon: etc etc
command: gedit %n

Where %n will be replaced with the path of the file.

---

### Post by J05HYYY on 2009-02-18
well it seems to work as required for most programs. although, I tried dosbox and it didn't load the sound as usual so included the use of sudo:

sudo <command> %n

sudo isn't portable ( ... but thats a different story.)
thank you everyone for your replies; they have helped crazily :D

---

