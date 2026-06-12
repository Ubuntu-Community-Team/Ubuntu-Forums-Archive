---
title: "Java Shortcuts"
date: 2009-05-15
forum: Programming Talk
---

### Post by slimx3m on 2009-05-15
alright, i have a simple question (i think :confused:).... i just finished compiling a java application and i got my *.jar.  i am able to execute the *.jar with no problem by typing it on the terminal.

so, how about if i would like to take it to the next level. anybody know how i could create a shortcut for users to just double click instead of going to the terminal and typing it every time?

i would like to at least create the shortcuts for windows users since they don't have a clue on what the hell they have to do. but, i would like shortcuts for linux, mac, and win users eventually.

thanx in advance.

---

### Post by Reiger on 2009-05-15
Quite simply for Win:

Target: "P:\ath\to\me\file.jar" -optional -program -arguments (Alternatively, use: "C:\path\to\java" -jar "P:\ath\to\me\file.jar" -optional -program -arguments)
StartIn: "P:\ath\to\me\"

In Linux you create a .desktop file (look at the files in /usr/share/applications/ to see how it's done, it has rather more elaborate semenatics). Altough typically you would also want to supply a shell script to be dropped in /usr/bin or /usr/local/bin which is what is actually called by executing your desktop file. See the "installing eclipse in hardy" tutorial in these forums for an example -- this allows for easy xterm access to your app.

In OS X? I dunno, never used that.

---

### Post by slimx3m on 2009-05-15
thnx for your help.

that worked beautifully!!! :)

i knew it was simple :P

---

