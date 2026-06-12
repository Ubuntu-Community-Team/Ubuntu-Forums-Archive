---
title: "Running compiled apps in codeblocks?"
date: 2009-03-05
forum: Programming Talk
---

### Post by Axis on 2009-03-05
So I have installed codeblocks and I am running Ubuntu 8.10 if it makes a difference however I don't belive it does.

When I compiled applications in windows it created an executable for me that I could return to, to run again so I could use my application. Well thats not exactly how things work in linux, so I was wondering how is it that I can "re-use" an application that I have compiled using codeblocks.

Thanks!
Axis

---

### Post by Axis on 2009-03-07
Bump...?

If it makes a difference these are C++ applications I am trying to re-run.

---

### Post by Tibuda on 2009-03-07
> **Axis said:**
> When I compiled applications in windows it created an executable for me that I could return to, to run again so I could use my application. Well thats not exactly how things work in linux, so I was wondering how is it that I can "re-use" an application that I have compiled using codeblocks.That's exactly how things work in Linux. The difference is that Linux executables don't have an extension. I don't know how codeblocks works, but after you compile your program, browse your project directory for a extension-less file, that should be your executable.

---

### Post by Axis on 2009-03-07
Its located in the BIN folder of the project folder. And if I navigate to it through terminal then it runs and everything works well. However, if I open it with terminal it doesn't work, and it doesn't do anything when I double click on it either.....

---

### Post by Ferrat on 2009-03-07
> **Axis said:**
> Its located in the BIN folder of the project folder. And if I navigate to it through terminal then it runs and everything works well. However, if I open it with terminal it doesn't work, and it doesn't do anything when I double click on it either.....

that's because of the built in protection stopping things from just doing things without you knowing.. 

in the terminal add ./ before to show you really want to execute it
```
/home/blabla/yourfolder$ ./nameofthefile
```

of right click it in your folder, select properties then permissions and check the box for "Allow executing file as Program" :)

---

