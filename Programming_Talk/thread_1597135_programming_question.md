---
title: "programming question"
date: 2010-10-15
forum: Programming Talk
---

### Post by Reddoug on 2010-10-15
Hi 
Trying to get a short program to run.
#!/bin/sh
echo "Hello World"

I have changed chmod 755 name. I have to use ./name to get it to display Hello World. Why can't I just type "name" (without quotes) to get it to display Hello World? Trying to learn some programming. name is the file name. I was using vim editor.

Thanks, Doug

---

### Post by worksofcraft on 2010-10-15
The reason is because it is not in one of the folders identified by your PATH variable. Try command "echo $PATH" to find what you have set up.

There are two alternatives solutions:
1. move your script to one of the folders in $PATH
2. add working directory . to the path

---

### Post by ncohea on 2010-10-15
> **Reddoug said:**
> Hi 
Trying to get a short program to run.
#!/bin/sh
echo "Hello World"

I have changed chmod 755 name. I have to use ./name to get it to display Hello World. Why can't I just type "name" (without quotes) to get it to display Hello World? Trying to learn some programming. name is the file name. I was using vim editor.

Thanks, Doug

Hi there. In general, it's because the present working directory . is not in your path. So if you say "name," bash will look in your path including /usr/sbin et al. for a program called "name" and upon not finding one will complain. Typing "./name" means "Bash, please run the program called "name" in the present working directory." Also, while that's a nice gentle introduction, I would not really call echo programming, as echo is a shell command. Programming would be more like

```
#include <stdio.h>

int main(int argc, char** argv)
{
     printf("Hello, World!\n");
     return 0;
}

gcc foo.c -o foo

./foo

Hello, World!
```

C is not exactly gentle, and perhaps you'd prefer Ruby or Python (those who want to engage in language wars may now do so). However, learning any of those can be HIGHLY rewarding and pays great dividends.

---

### Post by endotherm on 2010-10-15
you can also start a new shell (which takes the current dir as working)
by running 
```
sh name
```

not sure if that is more or less annoying from your perspective.

---

### Post by lykeion on 2010-10-15
I have created a ~/bin folder where I put all my own scripts, and I have this path added to $PATH in ~/.bashrc. For my purposes I think this is convenient.

---

### Post by lisati on 2010-10-15
*Thread moved to **Programming Talk**.*

---

### Post by slavik on 2010-10-15
> **lykeion said:**
> I have created a ~/bin folder where I put all my own scripts, and I have this path added to $PATH in ~/.bashrc. For my purposes I think this is convenient.
the better way to do things. :)

---

### Post by Reddoug on 2010-10-15
Hi
Thanks for the reply's. I will see if I can make it work with the suggestions.

Doug

---

### Post by Reddoug on 2010-10-15
Hi
Found a solution to my problem. I used vi and installed this (export PATH=~:$PATH) into .profile. Now program will run just by typing name.

Thanks, Doug

---

