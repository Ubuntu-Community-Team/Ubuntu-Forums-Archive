---
title: "[SOLVED] A question on zenity and input-output redirection"
date: 2008-12-11
forum: Programming Talk
---

### Post by skotos on 2008-12-11
OK, HTML sanitazation destroys the message so I will split it in parts: First, I would like to run a script using the following zenity syntax:```
zenity --notification --listen
```but I cannot find any sample nor documentation on how to get zenity 2.22.1 reading the information I am going to provide.

---

### Post by skotos on 2008-12-11
I am thinking at something like this```
exec 3>myfile.txt; zenity --notification --listen < & 3
```

---

### Post by skotos on 2008-12-11
And in another script:```
echo Starting > myfile.txt; echo Ending > myfile.txt
```

---

### Post by skotos on 2008-12-11
Any idea on how to update the notification tooltip or on where to find further info on the zenity --notification --listen tool?

---

### Post by mssever on 2008-12-11
> **skotos said:**
> And in another script:```
echo Starting > myfile.txt; echo Ending > myfile.txt
```
The > overwrites the file. I think you mean >>.
> **skotos said:**
> Any idea on how to update the notification tooltip or on where to find further info on the zenity --notification --listen tool?If it's possible to switch language, this task is much easier with Python's subprocess module.

Getting input into zenity is rather easy on the command line, but as you say,zenity's docs are incomplete. ```
zenity --notification --listen
--text=HI
could not parse command from stdin
--text="Hi"
could not parse command from stdin
text=hi
could not parse command from stdin
hi
could not parse command from stdin
```

---

### Post by mssever on 2008-12-11
Googling for ```
zenity "--listen"
```turned up [this post]("http://ubuntuforums.org/showpost.php?p=5872404&postcount=2"), which solves your problem.

---

### Post by skotos on 2008-12-11
> **mssever said:**
> [this post]("http://ubuntuforums.org/showpost.php?p=5872404&postcount=2"), which solves your problem.

Thank you!

---

