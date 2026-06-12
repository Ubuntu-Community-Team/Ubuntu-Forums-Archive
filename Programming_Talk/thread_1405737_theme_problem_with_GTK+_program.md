---
title: "theme problem with GTK+ program"
date: 2010-02-13
forum: Programming Talk
---

### Post by siukimfong on 2010-02-13
I've found that the theme of my own gtk+ program doesn't look like that of the system. It looks ugly, just like the theme in Windows98. but strangely, the themes of gtk+ programs that downloaded from the Source are in accordance with the system's.

what's the solution? :?:

---

### Post by nvteighen on 2010-02-13
The only reason I can think of is that you're developing your program using GTK+ 1.x instead of GTK+ 2.x... Please post the command you're using to compile.

---

### Post by siukimfong on 2010-02-13
> **nvteighen said:**
> The only reason I can think of is that you're developing your program using GTK+ 1.x instead of GTK+ 2.x... Please post the command you're using to compile.

I use a makefile. 

```

CC = gcc
all:
	$(CC) `pkg-config --cflags --libs gtk+-2.0` gtktest.c -o gtktest

```

---

### Post by SledgeHammer_999 on 2010-02-13
Can you show us some code? eg the first lines that compose the mainwindow?

---

### Post by nvteighen on 2010-02-13
Yes, please post some code and also a screenshot of how your application is showing up. This is really weird.

---

### Post by Lux Perpetua on 2010-02-14
Also, I hope you're not running your program with sudo. That would bypass your user's GTK theme.

---

### Post by siukimfong on 2010-02-14
yes, run the GTK+ program in the terminal will lose the theme style of the system. so just double click it.

---

### Post by Lux Perpetua on 2010-02-14
I don't think simply launching your programs from a terminal would do it, unless you were running the terminal as root. Can anyone confirm or refute that? I get the feeling the real problem hasn't been solved.

---

