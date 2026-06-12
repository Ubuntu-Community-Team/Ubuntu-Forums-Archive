---
title: "Running py file from an icon????"
date: 2011-03-06
forum: Programming Talk
---

### Post by davidschandler on 2011-03-06
I am used to programming in Python in Windows.  I am trying to convert to Ubuntu for Python programming.

I was under the impression that by including
#!/usr/bin/python or #!/usr/bin/env python
as the first line in a python program I could execute it by double clicking on the <program>.py icon.  What I get is a popup that asks if I want to run or run in a shell.  If I say Run, I get nothing.  If I answer Run in a Shell, I get a brief flash, then nothing.

Are my expectations off?  What does it take to be able to run from an icon?

---

### Post by Vaphell on 2011-03-06
program is executed in both cases (assuming it's valid)
when you use Run option you tell system to run program but not show its standard output to you. It means one of 2 things - you are completely uninterested in command line input/output or you use some GUI library to provide user interface.
When you use Run in shell, terminal window is opened just for the program and it is killed when program ends. If your program executes in 0.01 sec all you see is a brief flash. To prevent that from happening just add user input at the end of program - input() or raw_input() is enough.

---

### Post by cgroza on 2011-03-06
> **Vaphell said:**
> program is executed in both cases (assuming it's valid)
when you use Run option you tell system to run program but not show its standard output to you. It means one of 2 things - you are completely uninterested in command line input/output or you use some GUI library to provide user interface.
When you use Run in shell, terminal window is opened just for the program and it is killed when program ends. If your program executes in 0.01 sec all you see is a brief flash. To prevent that from happening just add user input at the end of program - input() or raw_input() is enough.
This. Also this may happen when the interpreter throws an error.

---

