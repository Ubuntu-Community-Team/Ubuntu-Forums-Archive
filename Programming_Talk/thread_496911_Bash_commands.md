---
title: "Bash commands"
date: 2007-07-09
forum: Programming Talk
---

### Post by sdmike on 2007-07-09
Does anyone have a bash command list?

I have one of my computers running Ubuntu and I putty into it via SSH.

So all I see is command line. I mostly use this computer for programming. 

But I don't know commands for downloading things from it to the computer I'm on or how to copy, paste, move files, and stuff like that.

Also what do I use to write with when I programming in command? 

I know when I was using the gui I would use the notepad like default program.

Future thanks!

---

### Post by Nekiruhs on 2007-07-09
cp START DESTINATION = copy from start to destination
mv START DESTINATION = move from start to destination
cd DESTINATION = change directory to DESTINATION

 Type man command to learn more about a command.

linuxcommand.org is a great site for command line stuff.

also nano is the text editor
nano /PATH/TO/FILE

---

### Post by Mr. C. on 2007-07-09
The bash built-in commands are available via 

```
man bash
```

System commands and utilities are numerous.   Start with some introductory Unix/Linux material that will get you on your feet.  Look at the course notes and homeworks here:

[http://cis68a.mikecappella.com](http://cis68a.mikecappella.com)
[http://cis68b1.mikecappella.com](http://cis68b1.mikecappella.com)

for starts.

MrC

---

### Post by AlexThomson_NZ on 2007-07-09
A little tip you might be interested in the the apropos command, which shows commands related to the task you are trying to perform, eg:

apropos passwords

Shows a bunch of commands related to "passwords".  It quite a good way to find some of those more 'obscure' useful commands!

---

### Post by Rui Pais on 2007-07-10
> **sdmike said:**
> Does anyone have a bash command list?

I have one of my computers running Ubuntu and I putty into it via SSH.

So all I see is command line. I mostly use this computer for programming. 

But I don't know commands for downloading things from it to the computer I'm on or how to copy, paste, move files, and stuff like that.

Also what do I use to write with when I programming in command? 

I know when I was using the gui I would use the notepad like default program.

Future thanks!

Bash command list is huge. Bash is very powerful and featured :)
I think only repeated use can get a user a comfortable level of usage.

I printed this [Bash reference card]("http://www.digilife.be/quickreferences/QRC/Bash%20Quick%20Reference.pdf") from the [Quick Refrence Cards]("http://www.digilife.be/quickreferences/quickrefs.htm") site and keep it at hand.

There are too some nice manuals on line:
[http://www.delorie.com/gnu/docs/bash/bashref_toc.html](http://www.delorie.com/gnu/docs/bash/bashref_toc.html)
or the official: [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

My favorites tips and shortcuts:
Use [TAB] key to auto-completion, for everything (not only paths), example
**sudo apt-get ins**[TAB] -> **sudo apt-get install**
**sudo apt-get install bash**[TAB] -> list of all packages with name started with bash.

**cd ***(with no path)* -> move to /home/user folder directly

**history | grep *<a_word>* ** gives a list of previously used commands with <a_word> on it.

**!XX** where XX is a line number from history runs that line (very useful in conjugation with above)

**nano -w** is an excellent and easy editor for console (-w to disable wrapping of long lines). It can even be set to do color syntax. 
If you are really on programming then vim may be a better choice (much harder to learn, but thats a different topic then bash commands :))

**wget -c <internet_location_file>** will download file at <internet_location_file> -c flag will recover a previous uncompleted download.

```
sftp username@some.server:file1 
``` will copy file1 from some.server accessed by *username* to your actual location.

```
scp file2 username@some.server:
``` will copy file2 from your local path to the /home/username/ folder on some.server.

hth a little :)

---

