---
title: "Python from command terminal: creating functions"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by bilaldaya on 2013-12-24
Hello, I am new to Ubuntu. I formerly used to use python on windows, and now I am learning Ubuntu. When I open the command terminal, I type python and press Enter,the symbol (>>>) is shown and I am in IDLE. However, I want to know how I can create functions and classes and the stuff I used to to in Windows. (Modules)
Thanks.

---

### Post by Iowan on 2013-12-24
That would be the interpreter - IDLE is available as a package from the Software Center. You can create classes, modules, etc., via any text editor (if you prefer) and run them from the command line.

---

### Post by bilaldaya on 2013-12-24
So I download IDLE and then try creating classes and functions? Also, how do I run them? what should I type in the terminal? Sorry I am really new.
Thanks a lot btw

---

### Post by Iowan on 2013-12-24
From the editor, you can use F5 (or Run>Run Module) to run a program. You'll need a program to instantiate a class or call a function.
From the command line, **python programname.py** will work. For python3, **python3 programname.py** should work.
Something like the following is sometimes used:
```
if __name__ == '__main__':
    game = Game()
    game.run()
```

---

### Post by The Cog on 2013-12-24
You can do it exactly the same as in windows. Use a text editor to create a file e.g. myprog.py and enter your code in there. Then in a command prompt, run the command 
```
python myprog.py
```

Aditionally, if this is the very first line of myprog.py:
```
#!/usr/bin/python
```
then you can mark myprog.py as executable (right-click in file manager and change the properties) and then you can use it as a command like this:
```
./myprog.py
```

Can I suggest geany as a good text editor for the job. It has a button to run a python program from within the editor, syntax colouring and error highlighting. That said, choice of text editor is quite a personal thing.

---

