---
title: "system() question"
date: 2006-12-27
forum: Programming Talk
---

### Post by HokeyFry on 2006-12-27
im making a program in C++ that basically will run mpg321 or 123 (user chooses) and loop-play a folder X number of times. when i tell it to play through the folder once, this is what it passes to system(char*) :

```
mpgXXX *.mp3
```

and this runs fine. however... when i tell it to loop 2 or more times the string i pass looks somewhat like this:

```
mpgXXX *.mp3 *.mp3 *.mp3
```


and it says that *.mp3 cannot be found. I dont understand why this happens when running "mpgXXX *.mp3 *.mp3 *.mp3" from the terminal manually will successfully loop three times.

---

### Post by po0f on 2006-12-27
HokeyFry,

Can you not just loop it like this? (Assuming it's C):
```
[FONT="Courier New"]int i;
for (i = 0; i < num_loops; i++)
    system("mpgXXX *.mp3");[/FONT]
```

---

### Post by HokeyFry on 2006-12-28
i get the same error. i did it the way i mentioned because i got the error first doing it your way.

---

### Post by po0f on 2006-12-28
HokeyFry,

Have you tried using [exec()](http://www.netadmintools.com/html/3exec.man.html)?

---

### Post by Wybiral on 2006-12-28
Could you post the actual function or chunk of code, maybe it's a little error or something in the C++ code. Not sure how... But I don't see why the for loop wouldn't have worked.

---

### Post by amo-ej1 on 2006-12-28
quoting man system
```

       system()  executes a command specified in command by calling /bin/sh -c
       command, and returns after the command has been completed.  During exe&#8208;
       cution  of the command, SIGCHLD will be blocked, and SIGINT and SIGQUIT
       will be ignored.

```

So this can be reproduced from commandline: 

```

edb@rogue:~$ ls * * * | wc -l
114
edb@rogue:~$ ls -d * * * | wc -l
18
edb@rogue:~$ /bin/sh -c ls * * * | wc -l
6

```

so in my opinion it relates to environment of the 'regular' bash shell.


anyhow, the task you're trying to do smell like shellscripting, it doesn't smell like C/C++ at all ;)

---

### Post by HokeyFry on 2007-02-16
yeah it would be better for a shell script i kinda knew that but i didnt have the resources at the time to learn scripting but i know basic C++ pretty well so...... yeah. but thanks for all of the responses

---

