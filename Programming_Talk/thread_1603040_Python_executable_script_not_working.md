---
title: "Python executable script not working"
date: 2010-10-22
forum: Programming Talk
---

### Post by noneofthem on 2010-10-22
Hello everybody,

today I started learning how to program using the Python programming language. I have to point out that am a newbie when it comes to programming. I am eager to learn this language as fast as possible however I got stuck in the very beginning when trying to write a simple executable script.

I simply created a file called "brian" including this code:

#!/usr/bin/python
print 'the bright side ' + 'of life'

I then typed

chmod +x brian

in the terminal.

When I try to run "brian" I get this message:

brian: command not found

What am I doing wrong?

Here are more details on my system:

- Ubuntu 10.10
- Linux 2.6.35.22-generic
- Gnome 2.32.0
- Python 2.6.6

I did try to find information about my problem here and in some Python forums, but I couldn´t find any answers. I would be glad for any hint you can give me so I can keep on learning.

Thanks a lot!


none of them

---

### Post by DaithiF on 2010-10-22
try:
```
./brian

```
you need to tell the shell where the script you want to execute is, unless that script is in a directory which is in your $PATH

---

### Post by noneofthem on 2010-10-22
Thanks a lot! That did it for me.

---

