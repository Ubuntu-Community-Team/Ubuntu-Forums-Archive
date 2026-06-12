---
title: "python programs wont work without a terminal command"
date: 2008-12-21
forum: Programming Talk
---

### Post by jarrah-95 on 2008-12-21
i have been trying to lern python and have recently moved to ubuntu and dont know to get it to run a python program at the dubble click and it it only a command line program (.py) that i have made
how do i get it to run straght away when i click on it

---

### Post by unutbu on 2008-12-21
Put
```
raw_input()
```
at the end of your python program. This will keep the program from ending until you press enter.

Now when you double-click the program in nautilus, a window should appear asking if you wish to run the program in a terminal, display, cancel or run. Select "Run in terminal".

---

### Post by Taidgh on 2008-12-21
And you're gonna want to put:
```
#!/usr/bin/python
```
as your first line, if you didn't know that. 
This tells the terminal what to do with the program (to run it with python).

---

### Post by days_of_ruin on 2008-12-21
Make it executable:
```
chmod +x spam.py
```

And don't forget make this the first line in your program:
```
#!/usr/bin/env python
```

---

