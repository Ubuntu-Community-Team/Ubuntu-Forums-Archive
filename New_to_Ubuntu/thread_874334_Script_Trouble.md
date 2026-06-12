---
title: "Script Trouble"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Littlehawk on 2008-07-29
I'm still learning a few things, but this looks simple. I have a script called test.py. It runs fine when I issue ```
/usr/bin/python test.py
``` from a teminal, But it won't run if I issue simply ```
test.py
```

Here is the script. It looks okay to me. What's wrong?

```
#!/usr/bin/python
the_world_is_flat = 1
if the_world_is_flat:
    print "Be careful not to fall off!"

from Tkinter import *
class Application(Frame):
    def __init__(self, master=None):
        Frame.__init__(self, master)
        self.grid()
        self.createWidgets()
    def createWidgets(self):
        self.quitButton = Button ( self, text="Quit",
            command=self.quit )
        self.quitButton.grid()
app = Application()
app.master.title("Sample application")
app.mainloop()

```

Thanks,
Jim

---

### Post by ace007 on 2008-07-29
its not an executable.  

```

sudo chmod +x test.py

```

---

### Post by Littlehawk on 2008-07-29
Thanks. I should have mentioned that, too. Here is the response to ls -l:

```
-rwxrwxrwx 1 jim jim   495 2008-07-29 18:30 test.py

```

So I think I have that covered, and it still won't execute.

---

### Post by ibuclaw on 2008-07-29
"test.py" is not in your bin "$PATH" list. So you must execute is with a **./** infront.
```
./test.py
```
Also, there is no need to specify the location of python,
```
python test.py
```
To know what I am going on about, type in
```
echo $PATH
```
from the output, everything that is an executable in those directories can be run without stating the location to it.

...

755 permissions will be just fine
```
chmod 755 test.py
```

Regards
Iain

---

### Post by Littlehawk on 2008-07-29
> "test.py" is not in your bin "$PATH" list. So you must execute is with a ./ infront.
Code:

./test.py



That works.  Thanks.

---

