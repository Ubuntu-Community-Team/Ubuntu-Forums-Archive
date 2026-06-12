---
title: "ubuntu noob python trouble"
date: 2008-03-23
forum: Programming Talk
---

### Post by A_B on 2008-03-23
hi,

I learned python while I was still using windows, When I switched to ubuntu I installed IDLE and tried to run some of my old scrips. 2 problems though.

1. How can I run a script without using IDLE? Only by double clicking (or open with) the .py file.

2. sys.exit doesn't work properly.If the script runs exit() (in IDLE because thats the only way I can run scripts so far), It asks to quit all together or only the current program. Quitting all together causes entire IDLE to quit, which is not good. If I then choose to exit the current running program only (so that I keep the IDLE editor and the script in IDLE) I get the following error and python/pygame freezes:

Traceback (most recent call last):
  File "/home/alex/Documents/programming/bpwpapcode/Chapter03/helloworld.py", line 22, in <module>
    exit()
SystemExit

This makes testing a script very annoying and time consuming as I have to force IDLE to quit every time and restart it.

Thanks 
Alex

---

### Post by LaRoza on 2008-03-23
See the sticky and [http://ubuntuprogramming.wikidot.com/Python](http://ubuntuprogramming.wikidot.com/Python)

You don't have to use IDLE (in fact, I found IDLE to be not very good). I use Gedit (Text Editor) and its plugins.

---

### Post by pmasiar on 2008-03-23
Re 1): use [shebang](http://en.wikipedia.org/wiki/Shebang_%28Unix%29) in first line: #!/usr/env python , and make file executable

Re 2): this is proper behavior of sys.exit() in that situation. If you don't sys.exit(), script ends running when finishes last statement, sys.exit() is for premature exit.

IDLE is OK for me, but I agree it looks ugly in ubuntu (Windows is OK), try something else if you want. I like SPE.

---

### Post by A_B on 2008-03-23
Thanks for the quick replies!

LaRoza, I got the script to run using the terminal and it all worked as it should.  Is there no faster way to do it though? No way I can run a script by just double clicking the .py file? I haven't got the "if the script is marked executable" part working yet though (I did mark the py executable in case you would wonder)
I allways get the error:
: No such file or directory
I have the terminal in the script's directory though.

pmasiar: The script had #!/usr/bin/env python already, I also tried #!/usr/env python but it didn't work.

Is that really how sys.exit() is supposed to work?
It did only close the running program without closing IDLE in windows...


Thanks
Alex

---

### Post by CptPicard on 2008-03-23
You should learn to love the command line, that's the Linux way. Real programmers don't double-click their scripts in fancy GUIs to run them. By using the shell, you get to see all the output the easiest way, and a re-run is a simple "<up-arrow> <enter>".

---

### Post by Can+~ on 2008-03-23
Executing it directly:
```
python myfile.py
```

Double clicking:
-Change permissions to Execute
-Add the "#!/usr/bin/env python"

Although, I suggest you to use a IDE, such as geany, since it makes it easy to execute, and safer (as you don't have to grant +x permissions).

---

### Post by A_B on 2008-03-23
Well... so be it. 
Using the terminal works fine and I can keep the terminal open in the same directory while editing my .py files so I can still test my scrips while I edit them. Typing 2 words won't kill me :)

Thank a lot
Alex

---

### Post by LaRoza on 2008-03-23
> **A_B said:**
> Well... so be it. 
Using the terminal works fine and I can keep the terminal open in the same directory while editing my .py files so I can still test my scrips while I edit them. Typing 2 words won't kill me :)

Thank a lot
Alex

Press the up arrow to get the history. When compiling and running other programs, I rarely type anything in the terminal because of that.

---

