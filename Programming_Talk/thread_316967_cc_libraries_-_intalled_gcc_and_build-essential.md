---
title: "cc libraries - intalled gcc and build-essential"
date: 2006-12-11
forum: Programming Talk
---

### Post by rich.bradshaw on 2006-12-11
Hi,

How do you set gcc up to compile any c files? I have installed build-essential, and am fully updated. Do I have to tell gcc where the
libraries are? It can't find any of them, for example stdio.h. As I can't really be bothered to rewrite all the core libraries in each program I wonder if any one knows what to do?

Rich

---

### Post by hod139 on 2006-12-11
I don't think I understand your question.  If you have installed the build-essential package then you can compile and valid c code using the gcc command and any valid c++ code using the g++ command.  What is the error message you are getting?

---

### Post by rich.bradshaw on 2006-12-12
/tmp/ccj19p7L.o: In function `main':
ants29.11.06.c:(.text+0x4bb): undefined reference to `sqrt'
ants29.11.06.c:(.text+0x513): undefined reference to `acos'
ants29.11.06.c:(.text+0x80e): undefined reference to `cos'
ants29.11.06.c:(.text+0x872): undefined reference to `sin'

Is what I get...

---

### Post by toojays on 2006-12-12
GCC doesn't link against the math library by default. Add '-lm' to your command line.

---

### Post by rich.bradshaw on 2006-12-12
> **toojays said:**
> GCC doesn't link against the math library by default. Add '-lm' to your command line.

Thank You!

I was so caught up in trying to install various packages I forgot to do the basics!

Another quick question whilst I'm here - why do my shell scripts need to have the whole path to them - that is, a script called batchrun.sh won't run unless I type /home/richard/ants/batchrun.sh , even if I am in the same directory as it - I have chmod +x it, but that doesn't seem to make any difference... 


Rich

---

### Post by kaamos on 2006-12-12
> 
Another quick question whilst I'm here - why do my shell scripts need to have the whole path to them - that is, a script called batchrun.sh won't run unless I type /home/richard/ants/batchrun.sh , even if I am in the same directory as it - I have chmod +x it, but that doesn't seem to make any difference...

An executable is started with "./", so you should type "./batchrun.sh"

---

### Post by hod139 on 2006-12-12
> **kaamos said:**
> An executable is started with "./", so you should type "./batchrun.sh"
Not quite.  But adding the "./" you are adding the current directory to the execute command.  It think what rich.bradshaw wants to do is be able to type batchrun.sh (without the ./).  To do this you need to edit 
```

~/.bash_profile

```
where ~ is a shortcut to your home directory.  As you can see ubuntu does not add the current path to PATH, but they do add 
```
~/bin
```.  This means if you create a bin file and put all of your scripts there you can run them.  If you really want your home directory to be included in the PATH (not recommended by me) you have to append it (I would suggest append so a system command would take preference, but you can prepend it if you want your home directory to take preference) to PATH here similar to how they added private bin.

---

### Post by rich.bradshaw on 2006-12-12
Ok, so I can just use ./batchrun.sh . Using Unix I didn't have to include the ./ , but I guess that makes sense!

Thanks a lot - forums are very helpful here!

---

