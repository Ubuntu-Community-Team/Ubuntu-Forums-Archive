---
title: "Cant view my C program"
date: 2006-09-19
forum: Programming Talk
---

### Post by JonasE on 2006-09-19
I know a little C and am new to Linux and have only ever used Visual Studio before on my windows. So anyways... I made a simple program in C using gedit and when I use gcc to compile it I use this command in the terminal:

gcc -o test test.c

Now I can see that there is an executable in the folder, but when I try to type in "test" into the terminal (no quotes) it doesnt do anything and just goes to the next line waiting for another command and nothing is printed to the screen.

I am very new to gcc and linux programming so im sure that its something stupidly simple and im just missing it, but if you could help me that would be awesome. Thanks.

---

### Post by po0f on 2006-09-19
What your getting is the system command test.  Since (most probably) your current directory isn't in your PATH, it looks for the command test in a predefined set of directories (at a terminal, "echo $PATH").  That is not what you want.  To execute a binary in your current directory, prepend a "./" to the command so it looks thus:```
$ ./test
```

---

### Post by JonasE on 2006-09-19
Thanks for the help. That worked out great.

God bless.

---

