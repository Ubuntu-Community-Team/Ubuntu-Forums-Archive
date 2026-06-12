---
title: "Running a Bash script in terminal..."
date: 2010-01-10
forum: Programming Talk
---

### Post by eeeguy on 2010-01-10
Say I have written/copy&pasted a bash script into gedit, what do I save it as to actually *make it * a bash script file? And once I have done that, how do I run the script?

---

### Post by LinuxRules1 on 2010-01-10
if you write a bash script in gedit you save it as a .sh file. then you just go to terminal and do the following,

give 777 permissions

```
chmod 777 file.sh
```

make it executable 

```
chmod +x file.sh
```

hope this helps:)

---

### Post by eeeguy on 2010-01-10
> **LinuxRules1 said:**
> if you write a bash script in gedit you save it as a .sh file. then you just go to terminal and do the following,

give 777 permissions

```
chmod 777 file.sh
```make it executable 

```
chmod +x file.sh
```hope this helps:)

Okay thanks, Ive done that. :D Now, how do I run the script?

---

### Post by Tahakki on 2010-01-10
Run ./file.sh

---

### Post by eeeguy on 2010-01-10
> **Tahakki said:**
> Run ./file.sh
Uh, I typed "Run ./mystupidfile.sh" and "run ./mystupidfile.sh"  Both came up as "Run: command not found"

---

### Post by Hellkeepa on 2010-01-10
HELLo!

I recommend using "chmod u+x file.sh" instead, that way only you can run it.
The first line given by **LinuxRules1** gives *everyone* full permissions on teh file; Read, write, execute. Making this very insecure.
The second line adds execute rights to everyone, so that they can't change it, but still run it.

*Edit, added:* He meant it without the "run" bit, as in "run the command...."

Happy codin'!

---

### Post by eewoz on 2010-01-10
> **eeeguy said:**
> Uh, I typed "Run ./mystupidfile.sh" and "run ./mystupidfile.sh"  Both came up as "Run: command not found"

If you are in the directory that contains mystupidfile.sh then just type ./mystupidfile.sh at the command prompt.  You should not type Run.

---

### Post by eeeguy on 2010-01-11
> **eewoz said:**
> If you are in the directory that contains mystupidfile.sh then just type ./mystupidfile.sh at the command prompt.  You should not type Run.
Oh right yeah, cant expect it to find the file for me can I?
But uh..how do you do that? And when going to my home directory from where ever it is by defalut do I type "home" for my home folder or my username?

---

### Post by Hellkeepa on 2010-01-11
HELLo!

"cd <folder>" to change directories, you can use either static or relative paths. Just "cd" alone brings you to your home folder, but you can also use "cd ~" (tilde).

Happy codin'!

---

### Post by SecretCode on 2010-01-11
If you're in a different directory and the file is in your home directory you can type
```
~/mystupidfile.sh
```
or
```
/home/eeeguy/mystupidfile.sh
```

I'm sure you can work out what to type if you're in your home directory and the script is in a subdirectory like scripts...
```
scripts/mystupidfile.sh
```

By the way, calling it file**.sh** helps but isn't necessary. It doesn't have to have an extension at all.

---

### Post by fluffen on 2010-01-11
Whenever i want to run a bash script i simply type ```
bash scriptname.sh
```

---

