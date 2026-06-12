---
title: "A confusing problem"
date: 2006-06-06
forum: Programming Talk
---

### Post by gordonyb0 on 2006-06-06
Wow,Here i have a question
I use execl() to display the result of "ps -l",but i don't want it to be shown in the stdout but in a file call "temp" instead.
i try to write like execl("/bin/ps","ps","-l",">","$HOME/temp",(char *)0);
It doesn't work.
so,is there any other function which can solve my problem? Pls tell me.:confused:

---

### Post by LordHunter317 on 2006-06-06
Adjust the stdout file descriptor (FD 1) to point to the file temp before you make the execl() call.

---

### Post by thumper on 2006-06-06
It depends on the language, but there are normally other commands that instead of writing to stdout, stderr give you access to the file handles.
You cand then do what ever you want with the output.

---

