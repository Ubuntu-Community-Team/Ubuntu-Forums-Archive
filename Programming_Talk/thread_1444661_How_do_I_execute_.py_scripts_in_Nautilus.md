---
title: "How do I execute *.py scripts in Nautilus?"
date: 2010-04-01
forum: Programming Talk
---

### Post by MCVenom on 2010-04-01
Hey guys, I've run into some problems with my first Python 3.1 script (I'm using Python 3.1 because that's what my book uses) on Ubuntu. I'm trying to execute it directly from Nautilus, but when I double-click it, nothing happens; I've changed permissions to be executable, and added the shebang to the beginning of the script:

```
#!/usr/bin/env python
# Game Over
# Demonstrates the print function
print("Game Over")
input("\n\nPress the enter key to exit.")
```

I will admit, I'm not sure what the output would be :???: (haven't done much programming on Linux), but I assume it would throw up a window similar to when you execute a Python script in Windows if I could get it to execute. I'd appreciate it if someone could clear this up for me. :)

---

### Post by geirha on 2010-04-01
When you double click it, you'll get a question about what to do with it. Since it's a terminal program, make sure you choose «Run in terminal» and not just «Run». 

If you don't get that question when you double click it, it's probably not made executable yet. Right-click it -> Properties -> Permissions tab and check the box at the bottom to make it executable.

EDIT: Oh, and you should use raw_input() rather than input().

---

### Post by MCVenom on 2010-04-01
I made sure it was executable; however I'm still not getting that dialog. If I remember correctly though the option to open it in the terminal is there on the right click menu, so I'll try that.

I don't think this would have any bearing on it, but I'm using Linux Mint 8, not pure Ubuntu.

EDIT: Nope... there's no option to open in the terminal on right click.

---

### Post by lykwydchykyn on 2010-04-01
Does it work if you execute it from the terminal?

Python is an integral part of Ubuntu, chances are even if you have 3.1 installed it's NOT the default version that will get called when you run "python".  

Also, on further reflection, even if it did run properly, you'd see no output running it from nautilus.  Though if you did:
```

tail ~/.xsession-errors

```
You'd probably see your intended output there.

---

### Post by geirha on 2010-04-01
It's very possible that Mint's default values regarding this differs from Ubuntu. Run gconf-editor from a terminal or Alt+F2, browse to /apps/nautilus/preferences and see what "executable_text_activation" is set to. On my Ubuntu 9.10 system, it is set to "ask".

---

### Post by MCVenom on 2010-04-01
> **lykwydchykyn said:**
> Does it work if you execute it from the terminal?

Python is an integral part of Ubuntu, chances are even if you have 3.1 installed it's NOT the default version that will get called when you run "python".  

Also, on further reflection, even if it did run properly, you'd see no output running it from nautilus.  Though if you did:
```

tail ~/.xsession-errors

```
You'd probably see your intended output there.

It runs, but there's an error given at the point where the script is supposed to end (after enter is pressed):

```
Game Over


Press the enter key to exit.
Traceback (most recent call last):
  File "./GameOver.py", line 5, in <module>
    input("\n\nPress the enter key to exit.")
  File "<string>", line 0
    
    ^
SyntaxError: unexpected EOF while parsing

```

Also, this was in my xsession-errors file:

```
Game Over


Press the enter key to exit.Traceback (most recent call last):
  File "/home/blackotaku/Python/GameOver.py", line 5, in <module>
    input("\n\nPress the enter key to exit.")
EOFError: EOF when reading a line

```

---

### Post by MCVenom on 2010-04-01
> **geirha said:**
> It's very possible that Mint's default values regarding this differs from Ubuntu. Run gconf-editor from a terminal or Alt+F2, browse to /apps/nautilus/preferences and see what "executable_text_activation" is set to. On my Ubuntu 9.10 system, it is set to "ask".
I went through it and it was set to launch; I changed it to ask and it gave me the dialog box and I was able to run the script without issue! Thanks a million :D

---

