---
title: "[SOLVED] high cpu usage"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by xieu90 on 2008-11-25
hi everyone, 
can someone tell me what does nice mean ? it is the blue thing in the first picture

and when i went to system manager I found that gnome video thumbnail use so much cpu 
i somehow killed it with htop and it was like Ctrl Alt Backspace



so what does "nice" mean ?

and how can i stop things like nice to use my cpu ? (if there is a way)

---

### Post by rockerphil on 2008-11-25
ok, i'm not quite sure what you mean by "nice", i'm personally a minimal Ubuntu user, but if you want to kill some apps that are running in the background just run this:

```
ps -A
```

that'll give you a list of all running programs. you can selectively kill them in one of two ways, either with the killall command, for example, to kill firefox 2 i run this:

```
killall fierfox run-mozilla.sh firefox-bin
```

or you can also look at the process number of the program you want to kill and run "sudo kill" then the process numbers of the programs you want to end. please keep in mind that some programs you'll have to use "sudo kill" to end since the process may belong to root. also, one last thing, Ctrl+Alt+Backspace kills out your X session, which is your graphical desktop, thus taking you back to your login screen. i hope this helps,

Phil

---

### Post by nhasian on 2008-11-25
I think NICE is referring to a processes niceness.

                                                                    The Niceness of a process is how much time the CPU allocates to it compared to everything else on the
system: 19 is the lowest, and –19 is the highest.

---

### Post by xieu90 on 2008-11-25
i dont understand very much about nice, but thanks you guys 
next time i meet that blue one i will try something ^^

---

### Post by nhasian on 2008-11-25
i forgot to mention that the System Monitor in Gnome takes up a lot of resources itself.  instead, open a terminal and use the command *top*.  when you see the process you would like to terminate, press the letter *k*, then enter the PID of the application you would like to stop.

---

