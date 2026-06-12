---
title: "Tkinter (Python) is very strange, IDLE don't work anymore and crash the whole system!"
date: 2008-03-24
forum: Programming Talk
---

### Post by Repgahroll on 2008-03-24
Hello! :D
I just installed Ubuntu and IDLE on a new computer for Python development, but i don't know what's wrong, cause the Tkinter don't work properly.

Any script that uses it don't work, including the IDLE.

As you can see on the attached image, the cursor is huge, and the program starts at the Line 13, Col 3, and if i press any key, the system beeps. AND, if i click "Open", a huge window appear, and if i click "Configure IDLE" or "Print Window" the WHOLE system CRASH!!! Other menu entries just don't do nothing.

I don't know if the problem is Tkinter or other thing, but probably is the Tkinter.

Thanks and sorry my english.

---

### Post by stevescripts on 2008-03-24
Possibly dumb question - you did install Tkinter?

I have no problems with recently installed tkinter and IDLE here.

Typical hello world script, this should run:
```

#!/usr/bin/python

from Tkinter import *

root = Tk()

root.title("Hello World!")

root.resizable(0, 0)

w = Label(root, text="Hello World!", width=16)

w.grid(row=0, column=0)

root.mainloop()

```

Hope this helps.

Steve

---

### Post by LaRoza on 2008-03-24
Are you using Compiz?

If so, disable it and see if that works. (Personal experience here)

You also shouldn't be running Tkinter from IDLE, as IDLE is written with Tkinter.

---

### Post by Repgahroll on 2008-03-24
> **stevescripts said:**
> Possibly dumb question - you did install Tkinter?

I have no problems with recently installed tkinter and IDLE here.

Typical hello world script, this should run:
```

#!/usr/bin/python

from Tkinter import *

root = Tk()

root.title("Hello World!")

root.resizable(0, 0)

w = Label(root, text="Hello World!", width=16)

w.grid(row=0, column=0)

root.mainloop()

```

Hope this helps.

Steve

:D Of course, it's installed! :D
IDLE depends on Tkinter(python-tk).:lolflag:

Your script just ran without problems, but for example, this one:
```
from Tkinter import*
class Soma:
    def __init__ (self,f):
        self.f=f
        self.f.title('Sum')
        
        Label(self.f,text='Num 1').grid(row=1,column=1,sticky=W,pady=3)
        Label(self.f,text='num 2').grid(row=2,column=1,sticky=W,pady=3)
        
        self.msg=Label(self.f,text='Sum of 2 numbar')
        self.msg.grid(row=3,column=1,columnspan=2)
        
        self.campo1=Entry(self.f,width=10)
        self.campo1.grid(row=1,column=2,sticky=E+W,pady=3)
        self.campo1.focus_force()
        
        self.campo2=Entry(self.f,width=10)
        self.campo2.grid(row=2,column=2,sticky=E+W,pady=3)
        
        self.botao=Button(text='Resultado',width=8,command=self.somar)
        self.botao.grid(row=4,column=1,padx=2,pady=3)
        
        self.botao1=Button(text='Sair',width=8,command=self.sair)
        self.botao1.grid(row=4,column=2,padx=2,pady=3)
        
    def somar(self):
        self.msg['text']='summin %d numbs'%(campo1+campo2)
    
    def sair(self):
        self.f.destroy()
        
inst=Tk()
Soma(inst)
inst.mainloop()
```
Just crash my system :(

Thank you guy!

> **LaRoza said:**
> Are you using Compiz?

If so, disable it and see if that works. (Personal experience here)

You also shouldn't be running Tkinter from IDLE, as IDLE is written with Tkinter.

Nope! I just installed Ubuntu 7.10 from the liveCD, added via Synaptic some extra repositories (multiverse, universe, etc), installed Kexi and some more programs, including the IDLE, wich isn't working :(

I am not trying to run Tkinter from IDLE, i'm actually just trying to run the IDLE itself...

Thank you all very much guys!
Sorry my english!

---

### Post by stevescripts on 2008-03-24
Does this shed a little light on your problem?

(results from running your code):
```

Exception in Tkinter callback
Traceback (most recent call last):
  File "lib-tk/Tkinter.py", line 1406, in __call__
    return self.func(*args)
  File "/home/steveo/test.py", line 27, in somar
    self.msg['text']='summin %d numbs'%(campo1+campo2)
NameError: global name 'campo1' is not defined

```

Steve

---

### Post by LaRoza on 2008-03-24
> **Repgahroll said:**
> 
Nope! I just installed Ubuntu 7.10 from the liveCD, added via Synaptic some extra repositories (multiverse, universe, etc), installed Kexi and some more programs, including the IDLE, wich isn't working :(

I am not trying to run Tkinter from IDLE, i'm actually just trying to run the IDLE itself...

Thank you all very much guys!
Sorry my english!

Ubuntu 7.10 has Compiz by default. Make sure it is disabled. Go to Sistema->Preferencias->Apariencia and change the Efectos visuales to Ninguno if it isn't there already.

I have had a bad time with Tkinter and Compiz before, and eliminating this as the problem would help narrow it down, and it may solve it.

(If your system isn't in Spanish, which I am inferring from your location, let me know. Mine is in Spanish)

---

### Post by Repgahroll on 2008-03-24
> **stevescripts said:**
> Does this shed a little light on your problem?

(results from running your code):
```

Exception in Tkinter callback
Traceback (most recent call last):
  File "lib-tk/Tkinter.py", line 1406, in __call__
    return self.func(*args)
  File "/home/steveo/test.py", line 27, in somar
    self.msg['text']='summin %d numbs'%(campo1+campo2)
NameError: global name 'campo1' is not defined

```

Steve

What? =/ =/ Here the code opens a big window, and the mouse begin to lag, then the system just crash...

[http://academic.evergreen.edu/curricular/modelingmotion/ExampleCode/gui/gui.php](http://academic.evergreen.edu/curricular/modelingmotion/ExampleCode/gui/gui.php)
The code gridexample.py here just crash my system, the hello.py is okay, and the hello2.py opens in a fullscreen window, but it works.

> **LaRoza said:**
> Ubuntu 7.10 has Compiz by default. Make sure it is disabled. Go to Sistema->Preferencias->Apariencia and change the Efectos visuales to Ninguno if it isn't there already.

I have had a bad time with Tkinter and Compiz before, and eliminating this as the problem would help narrow it down, and it may solve it.

(If your system isn't in Spanish, which I am inferring from your location, let me know. Mine is in Spanish) Oh yeah, i forgot that! But compiz was disabled... i'm using the generic driver for now. My system is in Portuguese :D (Sistema>Preferencias>Aparência>Efeitos Visuais>Nenhum) :D

Thanks guys :D


EDIT:

When i ran this code:

```
from Tkinter import *
import tkMessageBox

class App(Frame):
  def __init__(self, master):
    Frame.__init__(self,master)
    self.master.title("Wierd Menu")
    self.configure(height=200,width=200)
    self.grid(padx=15, pady=15,sticky=N+S+E+W)       
    self.menu = Menu(self)
    self.master.config(menu=self.menu)
    self.tkMenu = Menu(self.menu)
    self.menu.add_cascade(label="MenuItem", menu=self.tkMenu)
    self.tkMenu.add_command(label="Test", command=self.Test)
  def Test(self):
    tkMessageBox.showinfo("Test", "Test")
if __name__ == "__main__":
  root = Tk()
  app = App(root)
  root.mainloop()
```
from: [http://bugs.python.org/issue1601](http://bugs.python.org/issue1601)

It was okay, but when i clickd on the only menu entry, a giant blank window appeared, and the mouse began to lag, but the system didnt crash, but i need to force the window to quit.

---

### Post by LaRoza on 2008-03-24
> **Repgahroll said:**
> 
 Oh yeah, i forgot that! But compiz was disabled... i'm using the generic driver for now. My system is in Portuguese :D (Sistema>Preferencias>Aparência>Efeitos Visuais>Nenhum) :D

When i ran this code:

from: [http://bugs.python.org/issue1601](http://bugs.python.org/issue1601)

It was okay, but when i clickd on the only menu entry, a giant blank window appeared, and the mouse began to lag, but the system didnt crash, but i need to force the window to quit.

Close enough :)

That code worked fine for me. What are your specs and hardware? Is it possibly a hardware issue? Doubt it, but you never know.

---

### Post by stevescripts on 2008-03-24
> **Repgahroll said:**
> http://bugs.python.org/issue1601[/url]

It was okay, but when i clickd on the only menu entry, a giant blank window appeared, and the mouse began to lag, but the system didnt crash, but i need to force the window to quit.

From what I gather, issue1601 is a windows issue.

The code you posted runs as expected here (opensuse10.3)

You appear to have either a buggy software install, or a hardware issue.

Steve

---

### Post by Repgahroll on 2008-03-25
> **LaRoza said:**
> Close enough :)
That code worked fine for me. What are your specs and hardware? Is it possibly a hardware issue? Doubt it, but you never know.

Actually there is the possibility to be a hardware problem, i think, but not sure, i don't know much about the compatibility of hardware in such cases.

> **stevescripts said:**
> From what I gather, issue1601 is a windows issue.
The code you posted runs as expected here (opensuse10.3)
You appear to have either a buggy software install, or a hardware issue.
Steve

I know that is a windows problem, but it is a little bit similar to what I am taking, and I took only the code for testing.


I will try to switch to the Debian Testing repositories and reinstall everything that is related.

The computer is not mine, it's from my enterprise, so I don't know what is the motherboard, later I'll see in the bios and edit here, but for now the computer needs to stay on-line. I know that is a Gigabyte.

Is a celeron processor and has 512MB of memory.

Graphics Card is a nvidia geforce 7300 le, 256mb, 64 bit.

I already installed the nvidia driver to test, but the same thing happens.


**Thank you all for the help!:)**

Sorry my english.:(

---

### Post by LaRoza on 2008-03-25
> **Repgahroll said:**
> 
The computer is not mine, it's from my enterprise, so I don't know what is the motherboard, later I'll see in the bios and edit here, but for now the computer needs to stay on-line. I know that is a Gigabyte.

Is a celeron processor and has 512MB of memory.

Graphics Card is a nvidia geforce 7300 le, 256mb, 64 bit.

I already installed the nvidia driver to test, but the same thing happens.


It should work with that hardware. Would it be possible to create a new user account just to see if it is the setting in the account you are using?

---

### Post by Repgahroll on 2008-03-25
Thanks, but didn't work :(
I logged as root, and didn't work, so i made a new user, and the same thing happens :(

I also tried to install the HARDY* packages for the IDLE and related. (i tried the debian repository, but the apt asks me to remove all the other packages when trying to install just the python ones)

Thanks for the help :D

Maybe i'll try the latest Hardy testing(alpha) release... i think it could be a lot stable... right?

---

### Post by LaRoza on 2008-03-25
> **Repgahroll said:**
> 
Maybe i'll try the latest Hardy testing(alpha) release... i think it could be a lot stable... right?

Hardy is in Beta now, and it is quite good from what I see. It is on my laptop. Ubuntu had issues with my laptop in 7.04 and 7.10 (DVD drive, and Compiz blacklisting respectively), but 8.04 works flawlessly and with great speed.

You can try it, but I don't think it is the solution. This problem is strange.

---

### Post by Repgahroll on 2008-03-25
Thanks guy, but i just found an "old" 7.10 amd64 CD, and installed it, now everything works just fine :D.

Thank you very much for the help! Maybe it was a CD-image problem... don't know... the md5 was right... i'll try to install the 32-bit hardy later.

---

### Post by stevescripts on 2008-03-25
Good! glad to hear it

---

