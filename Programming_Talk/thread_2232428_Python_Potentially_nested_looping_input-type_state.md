---
title: "Python: Potentially nested looping input-type statement in GUI"
date: 2014-07-01
forum: Programming Talk
---

### Post by kumoshk on 2014-07-01
I just figured out a way to make something similar to an input statement (raw_input in Python 2.x) that you can use inside a GUI. So, I thought I would share.

For those who aren't aware&#8212;normally, GUI user-input from a text entry widget can't inherently be handled with nested loops like the Python input statement can. This happens for a few reasons.

Firstly, it's important to know that GUIs have a mainloop. This means, they're already looping. Putting another loop on top of that will effectively stop your GUI from doing anything except for your loop that you put on top of it (which won't stop at the end of each iteration like the input statement will cause a loop to do when inside of one).

So, I studied up the threading module and figured out how to use threads and events to remedy this situation.

What you need:
1. A GUI with an entry widget and a text widget (or label).
2. Only one threading.Event object (create it in your constructor); e.g. self.event=threading.Event()
3. Only one threading.Thread object (set to be a daemon) besides the main thread you're already using. Make it right after your event. Set the target to the method mentioned in no. 5 of this list. You don't need to make a complicated mess with lots of threads communicating with each other, nor do you need to mess around with queues, signals, conditions or anything like that.
4. The event-handler on your entry widget should simply set your event. Optionally, you might want it to echo user-input, first (as a command-line would).
5. Have a method to evaluate the text in the entry widget. Put your looping evaluation in it, just as you might with the Python input statement. However, at the beginning of each while loop, clear the event and cause it to wait instead of putting an input statement there.

That's it.

Caution: If you want your GUI to manipulate the text widget or the entry widget (rather than just having the new thread manipulate it), you should really make sure things are thread-safe. The sorts of programs that will need this often won't require that to a high degree, if so, though. One solution would be to disable the Entry widget (or remove the binding on it) while your GUI is doing stuff with them, and make sure the GUI won't start to do stuff if the extra thread isn't waiting.

I'm about to give the code for a working Python 3.x example. However, realize that this program merely demonstrates an answer to certain needs. It does not say what the needs are. To gain a better understanding of why this might actually be helpful, I might suggest trying to make a full-featured text adventure SDK and runtime environment in a GUI (from scratch) before criticizing this code. Probably the most practical use of this, however, is allowing command-line tools a quick and easy way to convert to GUI-based tools that allow command-input (without changing how things are structured). Whatever the case, my longstanding quest to solve this simple problem is over.

```
from tkinter import *;
import threading;
    
class Input_replacement:
    def __init__(self):
        self.tk=Tk();
        self.tk.protocol("WM_DELETE_WINDOW", self.quit); #Binding the X close button for the window.
        self.frame=Frame();
        self.create_widgets();
        self.frame.pack();
        self.tk.mainloop();
    def create_widgets(self):
        self.text=Text(self.frame);
        self.text.pack();
        self.entry=Entry(self.frame);
        self.entry.pack();
        self.entry.bind("<Return>", self.evaluate)
        self.entry.focus_set();
        #Start a new prompt/input thread here. Pause it. The evaluate method should unpause it, and it will pause itself when it needs to.
        self.event=threading.Event();
        self.pt=threading.Thread(target=self.prompt); #prompt thread
        self.pt.setDaemon(True); #This allows the program to quit to the command-prompt.
        self.pt.start();
    def pr(self, text=None, clear=False):
        if clear==True:
            self.text.delete("1.0", END);
        if text==None:
            text=self.entry.get();
        if self.text.compare("end-1c", "==", "1.0"):
            self.text.insert(END, text);
        else:
            self.text.insert(END, "\n"+text);
    def evaluate(self, event=None):
        self.pr();
        self.event.set();
        return "break";
    def prompt(self):
        while 1:
            print("looping");
            self.event.clear();
            self.event.wait(); #This should be at the beginning of each loop that you want to pause.
            prompt=self.entry.get();
            if prompt=="cls":
                self.pr("", True);
            elif prompt=="quit":
                self.quit();
            elif prompt=="name":
                self.pr("What is your name?");
                name=email=None;
                while name==None or email==None:
                    self.event.clear();
                    self.event.wait();
                    name=self.entry.get();
                    self.pr("Welcome, " + name+". What is your email?");
                    while email==None: #Yes, this doesn't have to be nested, but it demonstrates how to nest it (which is more useful to be able to do in other contexts).
                        self.event.clear();
                        self.event.wait();
                        email=self.entry.get();
                        self.pr("Thank you, "+name+"! Your email is <"+email+">.");
            else:
                pass;
            self.entry.focus_set();
    def quit(self, event=None):
        try:
            self.tk.destroy();
        except:
            pass;
        sys.exit(0);
        return "break";

GUI=Input_replacement();
try:
    GUI.tk.destroy();
except:
    pass;
```

---

