---
title: "Registering a program"
date: 2007-09-03
forum: Programming Talk
---

### Post by nzadLithium on 2007-09-03
Hey

I'm developing a program. I'm wondering how to make it so when you just type the program name in the terminal it executes it (instead of having to navigate to the directory then execute it). I mean like how you can go into the terminal and type firefox. Then it will launch firefox.

Thx

---

### Post by ewankho on 2007-09-03
Maybe you can use something like the PATH variable in your program.

---

### Post by fct on 2007-09-03
The PATH environment variable contains the list of directories in the system where programs are expected to be installed. Any file in those directories will be called as you want.

I suggest you use /usr/local/bin, that's where programs not included in the distribution are supposed to be installed to.

Oh, and you can add a directory to the PATH variable like this:

$ export PATH=$PATH:/new/directory

That way you don't need to move the files, but will only work for a session. If you want it to work again whenever you login, you can add a line like the one above to the .bashrc file in your home directory.

---

### Post by nzadLithium on 2007-09-04
ah thx. ill try that.

---

### Post by rbprogrammer on 2007-09-04
what i usually do is have all of my files in the directories that i want them in, then i just make a symlink in something like [FONT="Courier New"]/usr/bin[/FONT].  this is most helpful for me if there is just one executable. 

for my, putting a new directory in the PATH variable is cumbersome.  *but thats just my opinion*.  i think that because what if i create a executable that has the same name as some other executable on the system.

---

### Post by bobbocanfly on 2007-09-04
write a simple bash script that cds to the directory and executes the app then place it in /usr/bin with the name of the app you are developing.

```
cd /home/bobbo/code/passgen
./passgen
```

---

