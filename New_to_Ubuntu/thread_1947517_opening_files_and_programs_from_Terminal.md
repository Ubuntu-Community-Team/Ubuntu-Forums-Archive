---
title: "opening files and programs from Terminal"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by MaWiSo on 2012-03-26
I want to open files and programs from terminal

for programs i can just type the program name
for example : rhythmbox
for files i use gnome-open command

the problem is this keeps the terminal busy
if i use ctrl + c it terminates the program or file


how can i open programs and files without keeping the terminal busy ?

---

### Post by cybpabeofm on 2012-03-26
Are you asking how to open stuff from terminal without keeping the same terminal session busy with the program your running? You could open another windows (its under file) or open another tab (also under file, I think ctrl+T might also work).

---

### Post by papibe on 2012-03-26
Hi MaWiSo.

Just add an '&' at the end of the command (it means 'run' in the background).

For instance:
```
rhythmbox &
```

In the case you forgot it, you can send the program to a 'stopped' state by using ctrl+z and you'll see something like:
```
[1]+  Stopped                 rhythmbox
```
To send it to the background (just as you had put the ending &) run:
```
bg 1
```

Hope that helps.
Regards.

---

### Post by jerome1232 on 2012-03-26
Might want to make that

```
rhythmbox &> /dev/null &
```

That redirects all output from the program to /dev/null, which is a blackhole that destroy's everything going into it, meaning your just discarding the output, so your terminal doesn't get cluttered with chatter from the program you run.

---

### Post by MaWiSo on 2012-03-26
Thanks Guys ,

That worked well.

---

