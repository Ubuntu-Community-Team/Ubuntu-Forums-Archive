---
title: "Python keybord output"
date: 2009-01-17
forum: Programming Talk
---

### Post by h12 on 2009-01-17
Hi.

I'm looking for a way to type use python to simulate key presses . I have already tried xvkbd,(found from here: [http://www.python-forum.org/pythonforum/viewtopic.php?f=18&t=9513](http://www.python-forum.org/pythonforum/viewtopic.php?f=18&t=9513) ) and it works. The problem is when it is used with a computer game, I cannot get any response, even when using the virtual keyboard alone. I was wondering if there were any other ways to output keystrokes with python, or with command line.

---

### Post by h12 on 2009-01-18
Found a solution: xmacro with:

os.system("echo \"KeyStrPress Right\"| xmacroplay -d 10 :0.0")  

and

os.system("echo \"KeyStrRelease Right\"| xmacroplay -d 10 :0.0")

to enter or release a keystroke (in this case "right").

---

