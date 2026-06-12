---
title: "Just something ive been pondering"
date: 2011-04-12
forum: Programming Talk
---

### Post by CaptainMark on 2011-04-12
Are there gui toolkits that work with bash, ive never thought about it before but can you write a bash script that generates a gui or do you have write a gui into say, python and then send commands to a bash shell from the python script????

---

### Post by BkkBonanza on 2011-04-13
You can use [Zenity]("http://freshmeat.net/projects/zenity") to provide simple gui interaction for bash scripts. There's other libraries like this too.

It's not as capable as gtk in python. Depending on how involved the gui interface needs to be you may be better off using python, which isn't so hard. Python also has the advantage it's pretty much always installed by default.

---

### Post by nvteighen on 2011-04-13
The problem with Bash is that it actually doesn't interface to libraries, but to programs and AFAIK the only data structure it knows are strings. This means that you can't do proper GTK+ or Qt programming in bash: you can't access the data structures and manipulate, say a QtApplication or a GtkWindow instance using the features provided by the Bash language. So, yes, the nearest you can get for GTK+ is Zenity, which is a program that takes some arguments and creates a GUI object according to that argument. But as you see, that GUI object is actually under Zenity's control.

If you want something like shell scripting language with native GUI capabilities, maybe you should take a look at Tcl/Tk.

---

