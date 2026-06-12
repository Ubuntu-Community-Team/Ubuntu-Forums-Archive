---
title: "launching terminal with script/command"
date: 2011-02-17
forum: Programming Talk
---

### Post by superthermal on 2011-02-17
i have a probably really basic question that i can't figure out... i'm using a mathematical software package (mathematica) which has a Run[] command which lets you run system commands. e.g.,```
Run["rm /home/josh/blah.txt"]
```would delete blah.txt. this works fine, but it doesn't open a terminal or provide a way to dynamically view stdout while whatever command is running. of course i can just save to a log and then use tail -f or something, but that would be pretty inconvenient.

i would like to know a command that would force a terminal to open and immediately execute a script or system command in it--could anyone help me with this? i tried something like```
gnome-terminal -c bash -x [command]
```or something like that, but it didn't work--i could get a terminal to open, but it would say it didn't have a shell to operate it or something.

just to be clear, the Run[] function i'm talking about can run arbitrary commands, including invoking gui programs. e.g.,```
Run["gedit"]
```does indeed launch gedit. so i think what i'm after should be possible...

thanks!

---

### Post by DaithiF on 2011-02-17
Try:
```
Run["gnome-terminal -x bash -c 'your command; read x'"]

```

the purpose of the ; read x is to keep the terminal open after your command exits so that you can view its output -- pressing any key will then close it.

---

### Post by superthermal on 2011-02-17
excellent! thanks daithif. dunno why it didn't work when i tried originally... i was probably missing the ''s.

---

