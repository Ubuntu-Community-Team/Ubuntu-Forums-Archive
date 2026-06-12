---
title: "Chmod does not make file executable"
date: 2020-02-07
forum: New to Ubuntu
---

### Post by kipchip on 2020-02-07
Hey, I'm new to Ubuntu and currently trying to get this testfile/script to run a program I'm writing. I used "chmod +x filename" to mark the file as executable but when I got to execute the file I get:
"Error: Must provide executable file name."
I have no idea what to do from here, and I've already checked to see if it was actually marked (which it was). Is there something I'm missing or I need to do?
Thanks

---

### Post by CatKiller on 2020-02-07
Whichever other programs you're running from within your script would need to be executable, too, if you want to execute them.

---

### Post by yancek on 2020-02-07
What programming language is your executaable file.  What is the exact command you used to execute it?

---

### Post by guiverc on 2020-02-07
It could also be the file you're trying to execute is in $PWD (your current directory or "."), and your current directory is not located in $PATH (where commands are looked for).

---

### Post by kevdog on 2020-02-08
Is it's a script file (or really any executable in the directory) you need to run it with:
./<filename>

The ./ = current directory
You can't just type the filename at the command line by itself.

---

