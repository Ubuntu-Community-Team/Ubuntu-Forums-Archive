---
title: "Python help"
date: 2011-07-03
forum: Programming Talk
---

### Post by KoolPenguin on 2011-07-03
I'm trying to call a message dialog if the try statement returns an error exception but, for some reason the dialog will not display.  I tested the message dialog and it does display but not when called from this statement.  The functions are def playMine and def startServ.  Not sure what I'm doing wrong or if this is even possible within the try statement.

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-

import os, sys

try:  
    import pygtk  
    pygtk.require("2.0")  
except:  
    pass  
try:  
    import gtk  
except:  
    print("GTK+ not availible...")
    sys.exit(1)
        
class craftyGui:

    def playMine(self,widget):
        try:
            os.system("minecraft &")
        except OSError:
            result = self.msg.run()
            self.msg.destroy()

    def startServ(self,widget):
        try:
            os.system("minecraft_server &")
        except OSError:
            result = self.msg.run()
            self.msg.destroy()

    def aboutCrafty(self,widget):
        result = self.about.run()
        self.about.destroy()

    def quit(self,widget):
        sys.exit(0)

    def __init__(self):
        builder = gtk.Builder()
        builder.add_from_file("shrewds-crafty-gui.ui")

        self.about = builder.get_object("aboutdialog")
        self.msg   = builder.get_object("messagedialog")
        
        builder.connect_signals(self)
        
craftyGui = craftyGui()
gtk.main()

```

Thanks
--
Chris

---

### Post by ziekfiguur on 2011-07-03
os.system does not throw an error if minecraft fails, it just returns minecrafts exit code.
So, instead of using a try .. except block you could use something like
```
if os.system("blah") != 0:
    self.msg.run()
    self.msg.destroy()

```

---

### Post by KoolPenguin on 2011-07-03
> **ziekfiguur said:**
> os.system does not throw an error if minecraft fails, it just returns minecrafts exit code.
So, instead of using a try .. except block you could use something like
```
if os.system("blah") != 0:
    self.msg.run()
    self.msg.destroy()

```

I tried that but the result is still the same, if minecraft exists it will execute it but if not, no message dialog.
```

    def playMine(self,widget):
        if os.system("minecraft &") != 0:
            self.msg.run()
            self.msg.destroy()

```

I'm learning Python by porting my project over from Kommander/script so plz bare with me. :)

I just don't understand why it won't display the dialog, if I don't use the os call it will display it.

Thanks
--
Chris

---

### Post by cgroza on 2011-07-03
The code after the Minecraft execution will run only when os.system() returns, which is after Minecraft exits. os.system starts a process and waits for it to exit before returning the exit code.

So basically, your dialog code is never reached if Minecraft does not exit.

I have no experience with Minecraft but I am pretty sure that this is not the right way to do it.

---

### Post by ziekfiguur on 2011-07-03
It does work if you use subprocess instead of os.system (that is recomended in the python documentation anyway) 
if you want the program to wait untill minecraft is terminated use:
```

try:
    proc = subprocess.Popen("minecraft")
    proc.wait()
except OSError:
    self.msg.run()
    self.msg.destroy()

```
proc.wait() gives the return value so you can check if minecraft crashed.
If you dont want your program to wait for minecraft just skip the line with `proc.wait()` dont use the & like in os.system, because subprocess doesn't run the command through a shell but directly.

---

### Post by cgroza on 2011-07-03
> **ziekfiguur said:**
> It does work if you use subprocess instead of os.system (that is recomended in the python documentation anyway) 
if you want the program to wait untill minecraft is terminated use:
```

try:
    proc = subprocess.Popen("minecraft")
    proc.wait()
except OSError:
    self.msg.run()
    self.msg.destroy()

```proc.wait() gives the return value so you can check if minecraft crashed.
If you dont want your program to wait for minecraft just skip the line with `proc.wait()` dont use the & like in os.system, because subprocess doesn't run the command through a shell but directly.
Yes, bit it seems he needs the exit code of minecraft, and trying to get it would involve waiting for it to terminate again.

---

### Post by ziekfiguur on 2011-07-03
Also, if os.system("minecraft") != 0 works if you don't use the &

---

### Post by ziekfiguur on 2011-07-03
> **cgroza said:**
> Yes, bit it seems he needs the exit code of minecraft, and trying to get it would involve waiting for it to terminate again.

In #3 he said it wasn't about minecrafts exit code, but whether minecraft exists or not

---

### Post by KoolPenguin on 2011-07-03
I'll try and explain what I am trying to do.

The 'minecraft' file is a script that executes a java file called 'minecraft.jar'.  I need to make sure the 'minecraft' file exists, then execute it but release the program that called it, thats why I use 'minecraft &' and if the minecraft file does not exist, call the messagedialog to display information to the user it's not installed,etc.

So, maybe I should do a if statement to see if it does exist, then execute it else show the message dialog??

So far nothing works that way I would like it to.

Appreciate the help, any other suggestions?

Thanks
--
Chris

---

### Post by ziekfiguur on 2011-07-03
```

def playMine(self,widget):
    if not os.path.exists("./minecraft"):
        result = self.msg.run()
        self.msg.destroy()
        return
    else:
        subprocess.Popen("./minecraft")

```
this should work, make sure that the current program exits before minecraft though or it will leave a zombie.

---

### Post by KoolPenguin on 2011-07-03
> **ziekfiguur said:**
> ```

def playMine(self,widget):
    if not os.path.exists("./minecraft"):
        result = self.msg.run()
        self.msg.destroy()
        return
    else:
        subprocess.Popen("./minecraft")

```
this should work, make sure that the current program exits before minecraft though or it will leave a zombie.

That probably will work, this is what I came up with and it worked but, I will try your way too since this is a learning experience for me! :)

```

    def playMine(self,widget):
        if os.path.exists("/usr/local/bin/minecraft"):
            os.system("minecraft &")
        else:
            self.msg.run()
            self.msg.destroy()

```

Thanks
--
Chris

---

### Post by cgroza on 2011-07-03
> **ziekfiguur said:**
> In #3 he said it wasn't about minecrafts exit code, but whether minecraft exists or not
Yes, you check that with the exit code. If you have an exit code, then it means it exited.

---

### Post by ziekfiguur on 2011-07-03
> **cgroza said:**
> Yes, you check that with the exit code. If you have an exit code, then it means it exited.

exiST, not exiTS

---

