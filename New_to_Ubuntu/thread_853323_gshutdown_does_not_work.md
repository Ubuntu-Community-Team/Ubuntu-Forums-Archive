---
title: "gshutdown does not work"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by melrokz on 2008-07-08
[FONT="Comic Sans MS"][SIZE="3"]Hi! I'm Melvin from India. I need to auto-shutdown my PC after leaving it for 6 hours download in the night. So, I installed gshutdown, but it does not shutdown, it only logs off the system. First, how do i get to auto-shutdown my system after 6 hours? Next, what is the terminal command for shutdown and logoff my PC, please?[/SIZE][/FONT]

---

### Post by billgoldberg on 2008-07-08
> **melrokz said:**
> [FONT="Comic Sans MS"][SIZE="3"]Hi! I'm Melvin from India. I need to auto-shutdown my PC after leaving it for 6 hours download in the night. So, I installed gshutdown, but it does not shutdown, it only logs off the system. First, how do i get to auto-shutdown my system after 6 hours? Next, what is the terminal command for shutdown and logoff my PC, please?[/SIZE][/FONT]

just "shutdown".

No need to install something.

If you want the system to be log off and power off the pc lets say at 23.15h, use this command

```
sudo shutdown 23:15 -P
```

OR in 6 hours (360 minutes) use this command

```
sudo shutdown +360 -P
```

To cancel the shutdown:

```
sudo shutdown -c
```

---

### Post by fadelvato on 2008-07-08
i had the same problem with that program , i hope next time i use it the commands will work .

---

### Post by Maxime81 on 2008-07-25
Hi,

If gshutdown doesn't halt your computer, you have two solutions :

- Recompile gshutdown from the source using the development version (until the next release)
- run gshutdown as root : Alt+F2 > gksu gshutdown and then manually set the shutdown command (shutdown -h now or halt)

---

### Post by Big Wig !!! on 2008-07-26
Get SuperAwesomeTimer2000 at: [http://sat2000.sourceforge.net/](http://sat2000.sourceforge.net/). Works great for me.:)

---

