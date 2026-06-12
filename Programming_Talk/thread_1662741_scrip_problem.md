---
title: "scrip problem"
date: 2011-01-08
forum: Programming Talk
---

### Post by amusis on 2011-01-08
i don't know where post so i post here, sorry!

so guys i have a problem,my problem is simple... this is my scrip
first:
#!/bin/bash
archivio=${1%.rar}
xterm -e gedit $archivio.txt   <------------this work

second:
#!/bin/bash
archivio=${1%.rar}
mkdir $archivio <---------------------THIS NOT 

WHY?
the first create a txt file where(exactly) i wont, the second doen't create nothing , but they have the same variable.
archivio is a path. 
p.s.if in terminal i use mkdir /home/........ it works

---

### Post by soltanis on 2011-01-08
It helps us read your script if you use [code] or [php] tags to enclose it.

Does the file you provide contain any special characters, and more importantly, when you go to create the directory with mkdir, do all the parent directories exist? (i.e. if you create /home/amusis/path/archive, does path/ already exist in your home folder)? If not then you can use the -P option to automatically create parent directories.

---

### Post by amusis on 2011-01-08
> **soltanis said:**
> It helps us read your script if you use [code] or [php] tags to enclose it.

Does the file you provide contain any special characters, and more importantly, when you go to create the directory with mkdir, do all the parent directories exist? (i.e. if you create /home/amusis/path/archive, does path/ already exist in your home folder)? If not then you can use the -P option to automatically create parent directories.

the file is /home/......./path/prova2.rar
the script work with nautilus-actions, is an add to menu(right click), and if i use for the first and the second code alway the same actions: right click on the file prova2.rar, click on prova(/home/.......path/prova.sh) i have:
with first code:
/home/..../path/prova2.txt
with second code:
nothing 
i have tried also 
code:

[COLOR=Blue]#!/bin/bash[/COLOR]
[COLOR=DeepSkyBlue]archivio=${1[/COLOR]%.rar[COLOR=DarkRed]}[/COLOR]
xterm - e [COLOR=DarkRed]mkdir[/COLOR]  [COLOR=DeepSkyBlue]$archivio[/COLOR]


but don't work
only 3 rows and it don't work :-( what if i try to make a script more big?the end of word?

---

### Post by luvshines on 2011-01-08
Well, doesn't it throw any error if it fails for mkdir ?

Have you tried running the script directly with some parameter ?

---

### Post by amusis on 2011-01-09
> **luvshines said:**
> Well, doesn't it throw any error if it fails for mkdir ?

Have you tried running the script directly with some parameter ?
 
no, it daesn't throw any error, it seem to ignore the line.
yes, if i write the parameter it work, but without a variable it is useless.

i have try also from terminal ./prova.sh
code:

[COLOR=Blue]#!/bin/bash
[/COLOR][COLOR=DarkRed]echo [COLOR=Plum]"insert the path"[/COLOR]
read [COLOR=Black]a     #a=/home/....../path/prova[/COLOR]
mkdir[/COLOR] [COLOR=DeepSkyBlue]$a   [COLOR=Black]#[/COLOR][/COLOR]make directory /home/....../path/prova
nautilus [COLOR=DeepSkyBlue]$a    [COLOR=Black]#open in nautilus the directory /home/.../path/prova[/COLOR]

[COLOR=Black]is i run it with this code from terminal the mkdir works, so why it doesn't work if i run it from menu(right click)? [/COLOR]
[/COLOR]

---

### Post by amusis on 2011-01-10
i have solved the problem, it was a variable's  problem.
${1%.rar}   is not /home/....../prova, but /home/amus[COLOR=Black]is[/COLOR][COLOR=Black]/file:/ho[/COLOR]me/amusis/...../prova
problem was this-------> " .../file:/home/amusis/....."<--------------
 :cry:

---

