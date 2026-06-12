---
title: "Bash scripting - Where should I put shells file other than main in the filesystem?"
date: 2015-06-19
forum: Programming Talk
---

### Post by flaymond on 2015-06-19
Hi! I'm actually stuck at this point. I just experimenting bash, and after a quite trial and errors, I'm actually wanna go advance by executing these shells file from the /usr/bin. Anyway, this main.sh use other .sh scripts. So here the question, where should I put these 'dependencies scripts' in the filesystem, the right way?


Thanks for all help!

---

### Post by ofnuts on 2015-06-19
Some directory of yours in /usr/lib seems to be the way to do it.

---

### Post by flaymond on 2015-06-19
Thank you for the answer, ofnuts! I think scripts dependencies will gonna be installed in other directory. So, I assume it's just like C programs with header files placement. Now, I know where to put these files.

---

