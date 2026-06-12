---
title: "Tkinter (Python) running from command line."
date: 2009-07-27
forum: Programming Talk
---

### Post by Java Geek on 2009-07-27
Hello, I have built a program that uses Tkinter as its GUI wrapper. I am trying to run it from the command line with
```

$ python SimpleMenu.py

```
but nothing happens and the command line moves on to the next line.

However, if I type
```

$ python
>>> import SimpleMenu
>>> SimpleMenu.App()

```

The program works fine with that call. I am having the same issue with multiple Tkinter applications but here is the code fro a simple one. (In Python)

```

from Tkinter import *

class App:

    def __init__(self):
        self.root = Tk()
        self.root.title("Notpad")
        self.root.minsize(width=500,height=400)
                
        # Set up basic Menu
        menubar = Menu(self.root)

        menubar.add_command(label="Button")
        
        self.root.config(menu=menubar)

if __name__ == '__main__':
    App()

```

I am hoping that you experts can help me.> [QUOTE][/QUOTE][HTML][/HTML]

---

### Post by monraaf on 2009-07-28
I'm not familiar with Tkinter, but the usual way GUI programs work is that after settings things up you'll enter an event loop. I don't see anything in your program that resembles an event loop, so after creating your app object your program just exits.

---

### Post by stevescripts on 2009-07-28
Java Geek - 

Indeed monraaf is correct in assuming you have not started Tk's event loop.

```

#!/usr/bin/python

from Tkinter import *

class App:

    def __init__(self):
        self.root = Tk()
        self.root.title("Notpad")
        self.root.minsize(width=500,height=400)
                
        # Set up basic Menu
        menubar = Menu(self.root)

        menubar.add_command(label="Button")
        
        self.root.config(menu=menubar)

if __name__ == '__main__':
	app = App()
	app.root.mainloop()

```

Note a couple of things -

First I added the shebang line (which we will use in a minute)

Second I added the necessary call to start the Tk event loop running.

Note also that it is not necessary to use the if __name__ == '__main__':
trick to kick off the script - I find this a bit simpler personally:

```

#!/usr/bin/python

from Tkinter import *

class App:

    def __init__(self):
        self.root = Tk()
        self.root.title("Notpad")
        self.root.minsize(width=500,height=400)
                
        # Set up basic Menu
        menubar = Menu(self.root)

        menubar.add_command(label="Button")
        
        self.root.config(menu=menubar)

app = App()

app.root.mainloop()

```

And now for the shebang - 
Edit your script, save it as say simplemenu.py
from the command line 
```

chmod +x simplemenu.py

```
then you can run it from the command line by simply typing
```

./simplemenu.py

```

Hope this helps a bit.

Steve

---

### Post by Java Geek on 2009-07-28
H...WOW...THANKS stevescripts...like A LOT, You just saved me 4 programs.

---

### Post by Paul Miller on 2009-07-28
This, too, may be sort of obvious, but if you have the shebang line, you don't need to name the file ending with ".py" to get Python to recognize it.  So, you could even save your file as "simplemenu" and then run it with "./simplemenu".

---

### Post by stevescripts on 2009-07-29
Java Geek - My pleasure ;)

> **Paul Miller said:**
> This, too, may be sort of obvious, but if you have the shebang line, you don't need to name the file ending with ".py" to get Python to recognize it.  So, you could even save your file as "simplemenu" and then run it with "./simplemenu".

Paul - quite true, however, since nearly everything I write has to run on linux and windoze, I am in the habit of using file extensions virtually always.

Steve

---

