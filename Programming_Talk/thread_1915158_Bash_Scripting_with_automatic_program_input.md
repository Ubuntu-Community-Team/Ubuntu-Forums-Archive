---
title: "Bash Scripting with automatic program input"
date: 2012-01-25
forum: Programming Talk
---

### Post by dsmo223 on 2012-01-25
I am trying to write a bash script which will run a program and give the program input. The program is developed to take one input (a file name) and then it asks for another input (a second file name). I have tried the bellow posted code, but it went into a crazy infinite loop. Can any body help me?

```
  program < text.txt \n file.csv
```Thank you

---

### Post by Cookieh on 2012-01-25
Im not that used to bash shell scripting, but try to use pause to get out of the loop, there is something like IF THEN ELSE attributes which  would help you get out of loop

---

### Post by dsmo223 on 2012-01-26
I figured out the problem, when I was trying to pass littereals into the program, I was actually passing the entire files, so what I did was to make a file which holds my input for the program, and redirect that into the program.

---

