---
title: "extremely simple python question..."
date: 2008-04-30
forum: Programming Talk
---

### Post by cartisdm on 2008-04-30
I'm about 10 minutes into my attempt at learning python.  I'm following a beginner's guide from a link I saw in LaRoza's signiture.  The guide uses a lot of screenshots but they are taken within Windows and I'm trying to code in the terminal.

It says go to File --> New Window

> We notice that there's nothing in this new window. What this means is that this file is purely for our commands: Python won't interject with its own responses as we enter the program, that is, not until we tell it to. I'll call this the "Program" window, to distinguish it from the Interpreter window.


How do I do this? So far all I've done is type 'Python' in a terminal....

---

### Post by ryy_ on 2008-04-30
You can write your program in any text editor and save it as a .py file. To run it from terminal, just go to its directory and use:

```
python program_name.py
```

That new window, I guess, is just a text editor that comes with Windows Python installation.

Hope that helps.

---

### Post by olejorgen on 2008-04-30
Maybe an idea to include link?

Anyway, it's a fancy way of telling you to open a text editor instead of the python interpreter.

Save the file as NAME.py, open python, and type import NAME. Now all you definitions inside NAME.py will be available.

---

### Post by cartisdm on 2008-04-30
ohhh...duh. I should've known that.  On another note, would you recommend using a python editor (like something I just find in Add/Remove programs) or by using a text editor?

---

### Post by samjh on 2008-04-30
Just use GEdit for the time being.

It's good to have the plugins too:```
sudo apt-get install gedit-plugins
```

Enable the Python console and Embedded Terminal in the Preferences options, and then enable the bottom-section panel.

Now you have a text editor that will do syntax highlighting for Python code, along with an integrated Python interpreter and embedded terminal to execute your Python code! :)

---

