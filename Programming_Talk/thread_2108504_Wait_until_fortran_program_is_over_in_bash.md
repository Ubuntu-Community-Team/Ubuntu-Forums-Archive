---
title: "Wait until fortran program is over in bash"
date: 2013-01-24
forum: Programming Talk
---

### Post by Laura Joana on 2013-01-24
Hi!
I have a bash script that runs a fortran 95 program. This program writes many things in the screen until it is over. So, I want my bash script to wait the program to finish and run another command. While I'm waiting I want to see all the program output in the screen normally.
I tried using wait, but it didn't work! When I try wait $PPID this come up:
bash: wait: pid 2489 is not a child of this shell

Thanks! Sorry for my bad english!

---

### Post by Vaphell on 2013-01-25
doesn't that happen by default? you need to explicitly put the process in the background (& at the end) to make another one run without waiting.
When you run *command1; command2;* (semicolon and newline are equivalent), command2 will run only after command1 finishes.

---

### Post by Laura Joana on 2013-01-25
I thought this was the default also, but it doesn't work. I'm doing:

```
echo 'co2.ff' | ./FFncross | echo 'finish'
```co2. ff is the input for the FFncross fortran 95 program. What I get is just:
```
finish
```So, I don't see the program output in terminal like I should!

---

### Post by Laura Joana on 2013-01-25
Ok!
I was doing the commands separated with | instead of ; !!!! That's the problem. So the solution is:
```
echo 'co2.ff' | ./FFncross ; echo 'finish'
```
It works! Thanks s lot! It seams so simple now!!!! :D

---

### Post by jwbrase on 2013-01-25
Yes, every command in a pipe (a string of programs joined by |) is started immediately, and, as the previous program produces output, takes that output as its input instead of taking input from the keyboard.

You could also split it up across two lines:

```
echo 'co2.ff' | ./FFncross
echo 'finish'
```

---

