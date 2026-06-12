---
title: "Novice in bash scripting needs help"
date: 2010-09-30
forum: Programming Talk
---

### Post by Irdis Evalle on 2010-09-30
Hello! I am novice in Linux and bash scripting and need a little help in bash scripting. My version of Linux is 10.04 and bash ver. 4.1.5

So, I got this hometask from my university:

1) Create variable $hil amd store this string in it "Data files stored at ~/data"
Output its content on screen, then show first 6 symbols of it.

2) Add "Access granted (for user)" to the end of $hil.
Output it and exchange every letter "t" to "%%".

3) Write a command that will show "Yes" or "No" depending on if file "/proc/bus" is empty or not.

4) Show the the last line of file with extension .h from "/usr/include/linux" that begins with the word "If".

5) Write line 14 of file /usr/include/asm/errno.h in to the variable hl_2.


I have managed to do this:
```

hil="Data files stored at ~/data"
echo ${hil:1:6}
hil=${hil}"Access granted (for user)"
echo $hil
echo ${hill/t/%%}

```

So, i have managed to make first 2 tasks.

Please help me with the other 3. And, if possible, describe why this operator or that, so I will really learn something and not just Ctrl+C + Ctrl+V it in my *.sh file :)

---

### Post by sisco311 on 2010-09-30
Hi and welcome to the forums!

Check out: [thread=717011]Posting Homework Problems[/thread]

and
```
man bash | less +/^"CONDITIONAL EXPRESSIONS"
man bash | less +/"Pipelines"
man tail
man head
man grep
```

---

### Post by s.fox on 2010-09-30
Homework - Thread Closed.

From the Code of Conduct:

> Ubuntu Forums should not be thought of as a homework service. Please do  not post your homework assignments expecting someone else to do it for  you.

---

