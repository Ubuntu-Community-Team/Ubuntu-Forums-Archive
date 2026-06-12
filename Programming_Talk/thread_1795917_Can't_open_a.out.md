---
title: "Can't open a.out"
date: 2011-07-03
forum: Programming Talk
---

### Post by smilinggoomba on 2011-07-03
In my previous thread, I asked how to find a.out.  I just found it.  Now, I can't open it (I try double-clicking).  Please help.  Pretty please????

---

### Post by Bölvaður on 2011-07-03
I have no idea what you are compiling but normally when I got something like a.out I open the terminal and cd to it and ./a.out

let's say I compiled hello world program which I didnt specify a name for when compiling, and it just is on my... desktop

1. open terminal
2. ```
cd Desktop
```
3. ```
./a.out
```

if necessary I would need to make it executable in the step between 2-3
```
chmod u+x a.out
```

---

### Post by smilinggoomba on 2011-07-03
Thanks!  I forgot that you access the a.out through terminal.

---

### Post by cgroza on 2011-07-03
> **smilinggoomba said:**
> Thanks!  I forgot that you access the a.out through terminal.
If it was a GUI application, double clicking would work. The command line ones need to be started in a shell because they need that command line environment, GUIs don't.

---

### Post by Bachstelze on 2011-07-03
> **cgroza said:**
> If it was a GUI application, double clicking would work. The command line ones need to be started in a shell because they need that command line environment, GUIs don't.

The application does not need a "command line environment" at all (and actually, it doesn't even know what that means).  It is the user who needs the command line environment in order to be able to read the output of the application.  The application will run just fine without one.

---

### Post by cgroza on 2011-07-03
[HTML][/HTML]> **Bachstelze said:**
> The application does not need a "command line environment" at all (and actually, it doesn't even know what that means).  It is the user who needs the command line environment in order to be able to read the output of the application.  The application will run just fine without one.
Well, command line applications they run, but the user can't see it because his is in a GUI while there is no emulator to show and allow interaction with the application.

---

### Post by Bachstelze on 2011-07-03
> **cgroza said:**
> [HTML][/HTML]
Well, command line applications they run, but the user can't see it because his is in a GUI while there is no emulator to show and allow interaction with the application.

Yes but my point was that the application will still run.  If you have a command-line application that deletes a file and you double-click on it in Nautilus, the file *will* be deleted.  You made it sound as if the application would not run at all, and that might be confusing to a beginner, so I clarified, no offense meant. ;)

---

### Post by cgroza on 2011-07-03
> **Bachstelze said:**
> Yes but my point was that the application will still run.  If you have a command-line application that deletes a file and you double-click on it in Nautilus, the file *will* be deleted.  You made it sound as if the application would not run at all, and that might be confusing to a beginner, so I clarified, no offense meant. ;)
Don't worry, that cleared things up for me too.

---

### Post by ThatCoolGuy220 on 2011-07-03
U can change the extension to .sh so it will run on the command line when you click it

---

### Post by Bachstelze on 2011-07-03
> **ThatCoolGuy220 said:**
> U can change the extension to .sh so it will run on the command line when you click it

Renaming a binary to .sh? Sure, you can do that, but why?

---

### Post by Petrolea on 2011-07-03
> **ThatCoolGuy220 said:**
> U can change the extension to .sh so it will run on the command line when you click it

There's no point in doing this.

---

