---
title: "Partitioning Commands"
date: 2007-12-19
forum: Programming Talk
---

### Post by sekinto on 2007-12-19
Does anyone know of place that references all the terminal commands that can be used for partitioning?

The only one I know of is "fdisk"

---

### Post by bernied on 2007-12-19
fdisk works very well.
cfdisk is an ncurses variant - so it has the same functions with a colourful menu.
there is also parted, which I've never used.

Use man for more information (eg. 'man parted')

---

### Post by sekinto on 2007-12-19
Is there a way to have a Python script execute terminal commands? And then a way to retrieve feedback.

For example:
[enter command] - [terminal does command]
[terminal gives result] - [python script prints result for the user]

---

### Post by bernied on 2007-12-19
google!
[Here's something](http://forums.devshed.com/python-programming-11/running-bash-command-110687.html)

---

### Post by dwblas on 2007-12-20
Subprocess allows you to execute commands, retrieve output, and send input.  Doug Hellman has examples  [http://blog.doughellmann.com/2007/07/pymotw-subprocess.html](http://blog.doughellmann.com/2007/07/pymotw-subprocess.html)

---

