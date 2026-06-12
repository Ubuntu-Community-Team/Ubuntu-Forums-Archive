---
title: "System Moniter"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by dsa202 on 2008-07-14
Is there a ctrl-alt-delete equivalent in Ubuntu? If not is there a way I could set it up? Thanks in advance.

---

### Post by ET! on 2008-07-14
you can use top to see the processes

---

### Post by ET! on 2008-07-14
type that command in terminal

---

### Post by dsa202 on 2008-07-14
I'm sorry I am fairly new to Linux. What do you mean by top? I realize that this must be a fairly stupid question, sorry and thanks.

---

### Post by Vivaldi Gloria on 2008-07-14
system monitor is in the top panel > system > admin.

Or press ALt+F2 and start

```
gnome-system-monitor
```

You can also add it to a panel. Right click to an empty area in panel, choose add to panel and find sys. mon.

---

### Post by AOZ on 2008-07-14
right click top panel
add to panel
System monitor

---

### Post by hellzkeeper1216 on 2008-07-14
If you want something less fancy and takes up less resources use htop
open your teminal and type
Code:
sudo apt-get install htop

then when ever you want to run the system monitor open your terminal and type 
htop

---

### Post by ET! on 2008-07-14
top is a command you type in terminal

to open the terminal goto 
applications->accesories->terminal

you will get a window which is similar(well not exactly)to the command prompt in windows...type "top" in it..you will be able to see all the processes running..

i hope that is descriptive enough

---

### Post by Vivaldi Gloria on 2008-07-14
> **dsa202 said:**
> I'm sorry I am fairly new to Linux. What do you mean by top? I realize that this must be a fairly stupid question, sorry and thanks.

To open a Terminal choose Applications &#8594; Accessories &#8594; Terminal; or press Alt+F2 and type gnome-terminal. You then write

```
top
```

there to see a list of running processes. I suggest you also read

[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

---

