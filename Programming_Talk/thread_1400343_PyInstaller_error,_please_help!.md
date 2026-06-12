---
title: "PyInstaller error, please help!"
date: 2010-02-06
forum: Programming Talk
---

### Post by Eremis on 2010-02-06
Hi!

I am trying to make an .exe for windows from my python script.
I made a simple script that uses tkinter as a gui, and displays 'hello world'

heres my code:

```

# File: hello.py

from Tkinter import *

root = Tk()
button = Tkinter.Button(root, text = "Hello World").grid()
root.mainloop()

```

when I run: 
```
python Makespec.py --tk /home/username/Desktop/hello.py
```
everything goes well, but after I run: 
```
python Build.py /home/username/Desktop/hello.py
``` 
I get an error: 

```

Traceback (most recent call last):
  File "Build.py", line 1158, in <module>
    main(args[0], configfilename=opts.configfile)
  File "Build.py", line 1146, in main
    build(specfile)
  File "Build.py", line 1109, in build
    execfile(spec)
  File "/home/andriy/Desktop/hello.py", line 6, in <module>
    button = Tkinter.Button(root, text = "Hello World").grid()
NameError: name 'Tkinter' is not defined

```

I think it cant use tkinter... Why? I used the --tk option... even when I leave it off I still get that error...

Can someone help me figure this out? I also tried GTK+ lib to make the gui, and it also failed...

How can I use PyInstaller to make an .exe from a script that has a gui (tkinter, or GTK+...) ???

---

### Post by diesch on 2010-02-06
```
from Tkinter import *
``` doesn't define a name space Tkinter but imports the symbols from Tkinter into the current name space. So you have to use
```
Button(root, text = "Hello World").grid()
``` instead of
```
Tkinter.Button(root, text = "Hello World").grid()
```

---

### Post by Eremis on 2010-02-06
It worked!

Thanks,

Do you know a way to use GTk+ instead of tkinter with PyInstaller?

---

