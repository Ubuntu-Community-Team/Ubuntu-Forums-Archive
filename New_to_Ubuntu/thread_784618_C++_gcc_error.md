---
title: "C++ gcc error"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Chicken Dinner on 2008-05-06
I am having trouble with gcc.  I tried making a "hello world" program in Vim, and I received an error when I tried to compile it with this code (which I found on the internet).

gcc -Wall -o foo ubuntu.cpp

Ubuntu is the name of the file.
After entering it after a colon (Ex: mode), this is the error I receive.

gcc: error trying to exec 'cc1plus': execvp: No such file or directory

Does gcc not come with everything to compile C++ code?  If anyone can help me that far, I also haven't a clue how to run the program after its compiled, so any help with that would be great too.  I'm an absolute beginner so any answers will be helpful.

Thank you.

---

### Post by Sef on 2008-05-06
Have you installed build-essetial?

Applications > Accessories > Terminal

```
sudo apt-get update
```

```
sudo apt-get install build-essential
```

---

### Post by Monicker on 2008-05-06
I believe you will need to use g++.  If do not already have it, install the build-essential package.

---

### Post by Dougie187 on 2008-05-06
I think you do need g++ for c++ code, but for a simple hello world program you shouldnt need c++ really.

---

### Post by Chicken Dinner on 2008-05-06
Well now I feel stupid!  I could've sworn I installed g++, but apparently not.  Thanks for the help.  That would've taken hours for me to figure out.

---

### Post by Oldsoldier2003 on 2008-05-06
> **Chicken Dinner said:**
> Well now I feel stupid!  I could've sworn I installed g++, but apparently not.  Thanks for the help.  That would've taken hours for me to figure out.
the compiler tools are not installed in a default ubuntu installation, its been the subject of quite a few spirited discussions :)

---

