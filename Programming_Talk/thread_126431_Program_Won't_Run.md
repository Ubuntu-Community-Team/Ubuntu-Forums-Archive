---
title: "Program Won't Run"
date: 2006-02-06
forum: Programming Talk
---

### Post by Nuptse on 2006-02-06
Hi,
I'm new to this and I'm  teaching myself to program.  My silly little intro program will compile but then the executable won't run.  I get an error saying "bash:a.out:command not found"  So I'm completely lost! Help!
Thanks!

---

### Post by Viro on 2006-02-06
What language are you using? I'm guessing your program is called a.out. If you want to execute it, you need to type the command ./a.out as the current directory isn't part of the PATH and the './' is necessary to execute stuff from the current directory.

---

### Post by Nuptse on 2006-02-06
Wow! That's awesome.  why is that?  I'm writing in C++ and this has been driving me crazy for a week!  You rock!  Thank you thank you thank you!

---

### Post by Keffin on 2006-02-06
[quote=Nuptse]Wow! That's awesome. why is that? I'm writing in C++ and this has been driving me crazy for a week! You rock! Thank you thank you thank you![/quote]

To run a program you need to provide the absolute location of the executable, i.e. /home/keffin/programs/test/a.out, otherwise the system has no idea where to look for it. "./" is shorthand for saying "the absolute location of the current directory", so ./a.out will be expanded to /home/keffin/programs/test/a.out and then executed.

As Viro mentioned, there is a PATH variable (try "echo $PATH" in the terminal), that lets you "cheat" and only type the name of a program to run. The system will then search the directories in PATH in order and execute the first program it finds with the name you gave.

It isn't practical to list too many directories in the PATH variable (think search time for a start), but you could add a directory with the command "export PATH=/home/keffin/programs/test:$PATH". Note the lack of spaces around the "=", and you would need to change /home/keffin/programs/test to the directory where a.out is. You can now just type "a.out" to run your program. This change is local to the terminal you are using, so to make it permanent you can edit ~/.bashrc ("~/" is shorthand for "the absolute location of my home directory") and add the command at the end of there.

Also you should be able to just click the icon of a.out in your file manager and be asked if you want to execute it.

---

