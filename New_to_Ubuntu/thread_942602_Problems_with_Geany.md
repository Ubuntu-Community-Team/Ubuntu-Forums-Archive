---
title: "Problems with Geany"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by kvorion on 2008-10-09
I have come back to the forum after a long time and I could not find the programming talk section because the forum seems to be reorganized. Hence I post here (it would be great if someone could give me a direct link to programming talk).

Nevertheless.....I installed Geany yesterday for some general purpose programming in C and C++. It worked great till the time I had to execute my program.

I had a program called LinkedList.c open. When I said compile, it executed the following command:

```
gcc -Wall -c LinkedList.c
```

This creates a file called LinkedList.o in the same folder, but this file is not an executable binary. I tried executing the same command on the terminal and the result was the same file.
As a result I cannot execute this file and neither can Geany.

When I click on the execute button, I get the following error:

```
11:30:49: Failed to execute "/home/kv/Code/linkedList/LinkedList" (make sure it is already built)
```

When I type the following on command line, it works fine and gets executed:

```
gcc LinkedList.c -o LinkedList
```

Help appreciated.

---

### Post by kvorion on 2008-10-09
Rookie mistake. Found the solution.

---

