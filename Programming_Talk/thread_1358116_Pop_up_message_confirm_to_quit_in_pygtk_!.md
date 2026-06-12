---
title: "Pop up message confirm to quit in pygtk !"
date: 2009-12-18
forum: Programming Talk
---

### Post by e=mc^3 on 2009-12-18
Hello,

I am new to pygtk and want make a very simple "hello world" kind application. I want to create a window, and when people click the x icon to quit the window, i want a button appear to confirm that. I have tried to do that but the problem is whenever i click the x icon, the window disappear without showing up the confirming button ! Note that for the callback function for the destroy event, i even didnt put a line of code to kill the application, but instead some code for display the button !

I am confused here. I tested it by rewriting the function connected to the destroy event, this time only one line of code:

 print "the application has been terminated..."

And when i ran, i clicked x icon, the window disappear ! in the terminal it did write out "the application has been terminated ...". But the application didnt really quit ! (because i did nothing for the destroy event function, just print out something), i have to press ctrl-z to stop it manually . It seems normal, right ?

My question is,** is it true when we click the x icon to quit a program, it just kill the program's UI first** ? If so, how do i make a program that when user click the x icon, a popup message appear to confirm instead of kill the program's UI ?

The second question is what is the different between the function button.connect(...) and button.connect_object(....) ? I cant find it in the document.

DO you think that i should learn to program UI with GTK, C language first before pyGTK ? Is it easy to transfer C code to python code ?There are a lof of document for GTK/C, but pyGTK i really feel confused.

---

### Post by j7%&lt;RmUg on 2009-12-18
ok, ok slow down, i can see your a little distraught.

First of all check out the docs at the pygtk website: [www.pygtk.org](www.pygtk.org)

it has a tutorial and reference docs too.

second of all, simply blurting out that it doesnt work will not get you far here: can you post the code you are having trouble with please?

python tends to be a much easier to learn language than C ever has been, i recommend sticking with this if your a beginner.

---

### Post by nvteighen on 2009-12-18
The idea is that quitting the UI shouldn't terminate the program automatically just because the UI isn't the program, but just a loop inside of it. GTK+ is stopped by using gtk.main_quit(), but that will only "break" the loop... as the widgets will still be allocated in memory because the program is still there.

This example should clarify it a lot. I like to encapsulate the UI in a class so this idea that the UI is just a part of the program which can be loaded (instantiated) any time I want is shown more clearwise.

About the PyGtk documentation, you can install it from the python-gtk2-doc package. Install the devhelper package too to get a nice documentation browser.

```

import pygtk
pygtk.require("2.0")
import gtk

class UI(object):
    def __init__(self):
        self.label = gtk.Label("Hello world!")
        self.window = self.make_window()
        self.window.show_all()

    def make_window(self):
        window = gtk.Window()
        window.set_title("Hi!")
        window.set_default_size(200, 100)

        window.connect("delete-event", self.win_close, None)

        window.add(self.label)

        return window

    def start(self):
        gtk.main()

    def win_close(self, widget, event, data):
        dialog = gtk.MessageDialog(self.window, gtk.DIALOG_MODAL,
                                   gtk.MESSAGE_INFO, gtk.BUTTONS_YES_NO,
                                   "Quit?")
        dialog.set_title(":(")

        response = dialog.run()
        dialog.destroy()
        if response == gtk.RESPONSE_YES:
            gtk.main_quit()
            return False # returning False makes "destroy-event" be signalled
                         # for the window.
        else:
            return True # returning True avoids it to signal "destroy-event"
        
def main():
    myUI = UI()
    myUI.start()

    print "Now we're outside the UI, but still in the program"

main()

```

---

### Post by e=mc^3 on 2009-12-18
> **nvteighen said:**
> The idea is that quitting the UI shouldn't terminate the program automatically just because the UI isn't the program, but just a loop inside of it. GTK+ is stopped by using gtk.main_quit(), but that will only "break" the loop... as the widgets will still be allocated in memory because the program is still there.

This example should clarify it a lot. I like to encapsulate the UI in a class so this idea that the UI is just a part of the program which can be loaded (instantiated) any time I want is shown more clearwise.

About the PyGtk documentation, you can install it from the python-gtk2-doc package. Install the devhelper package too to get a nice documentation browser.

```

import pygtk
pygtk.require("2.0")
import gtk

class UI(object):
    def __init__(self):
        self.label = gtk.Label("Hello world!")
        self.window = self.make_window()
        self.window.show_all()

    def make_window(self):
        window = gtk.Window()
        window.set_title("Hi!")
        window.set_default_size(200, 100)

        window.connect("delete-event", self.win_close, None)

        window.add(self.label)

        return window

    def start(self):
        gtk.main()

    def win_close(self, widget, event, data):
        dialog = gtk.MessageDialog(self.window, gtk.DIALOG_MODAL,
                                   gtk.MESSAGE_INFO, gtk.BUTTONS_YES_NO,
                                   "Quit?")
        dialog.set_title(":(")

        response = dialog.run()
        dialog.destroy()
        if response == gtk.RESPONSE_YES:
            gtk.main_quit()
            return False # returning False makes "destroy-event" be signalled
                         # for the window.
        else:
            return True # returning True avoids it to signal "destroy-event"
        
def main():
    myUI = UI()
    myUI.start()

    print "Now we're outside the UI, but still in the program"

main()

```


Thank you so much for the code. Here is my funny code, instead of display a message box, i display a button. Its my bad that i just glanced at the tutorial.

```

import gtk
import pygtk
class PyApp:
    
    def realquit(self, widget, data=None):
        gtk.main_quit()
   
    def quitt(self, widget, data=None):
        self.button=gtk.Button("are u sure u want to quit ?")
        self.button.connect("clicked",self.realquit,None)
        self.window.add(self.button)
        self.button.show() 
        return True                 # this line of code is so important ! 

    def __init__(self):
        self.window=gtk.Window() 
        self.window.set_title("hello world !")
        self.window.set_default_size(200,200)
        self.window.connect("delete-event", self.quitt)
        self.window.show()
        

pu=PyApp()
gtk.main()

```

---

### Post by frafu on 2010-06-26
> **nvteighen said:**
> 
```

<snip>
        
def main():
    myUI = UI()
    myUI.start()

    print "Now we're outside the UI, but still in the program"

main()

```

If I get the code right, the print "Now we're outside the UI, but still in the program" statement gets executed after the user has confirmed the qui in the dialog; correct?

Moreover, I agree that the print statement is still in the program, but could you please confirm that the program terminates immediately after the execution of the print statement?

Thanks in advance for any reply, 

Francesco.

---

### Post by Bachstelze on 2010-06-26
> **frafu said:**
> but could you please confirm that the program terminates immediately after the execution of the print statement?


Not really immediately, but close enough. There is an implicit [font=monospace]return None[/font] after it, for example.

---

### Post by frafu on 2010-06-26
> **Bachstelze said:**
> Not really immediately, but close enough. There is an implicit [font=monospace]return None[/font] after it, for example.

This seems sensible: whoever started the program might want to get some information when it quits; for example whether everything went right. 

But I assume that in principle after it has returned that information, the python interpreter knows that the program has terminated and might want free the resources used by the program!? Or does the program need to do something else apart calling gtk.main_quit to terminate itself and have the resources it used freed? (I am assuming a simple pygtk program.)

Francesco

---

### Post by Bodsda on 2010-06-27
> **e=mc^3 said:**
> Hello,

I am new to pygtk and want make a very simple "hello world" kind application. I want to create a window, and when people click the x icon to quit the window, i want a button appear to confirm that. I have tried to do that but the problem is whenever i click the x icon, the window disappear without showing up the confirming button ! Note that for the callback function for the destroy event, i even didnt put a line of code to kill the application, but instead some code for display the button !

I am confused here. I tested it by rewriting the function connected to the destroy event, this time only one line of code:

 print "the application has been terminated..."

And when i ran, i clicked x icon, the window disappear ! in the terminal it did write out "the application has been terminated ...". But the application didnt really quit ! (because i did nothing for the destroy event function, just print out something), i have to press ctrl-z to stop it manually . It seems normal, right ?

My question is,** is it true when we click the x icon to quit a program, it just kill the program's UI first** ? If so, how do i make a program that when user click the x icon, a popup message appear to confirm instead of kill the program's UI ?

The second question is what is the different between the function button.connect(...) and button.connect_object(....) ? I cant find it in the document.

DO you think that i should learn to program UI with GTK, C language first before pyGTK ? Is it easy to transfer C code to python code ?There are a lof of document for GTK/C, but pyGTK i really feel confused.

I had some problems when learning pygtk, this was mainly due to the outdated official documentation. I found this site that is IMHO a 'lot' better. 

[http://www.learnpygtk.org/pygtktutorial/index.html](http://www.learnpygtk.org/pygtktutorial/index.html)

After a night of reading that, I was able to write a program that I posted about here:
[http://ubuntuforums.org/showthread.php?p=9288582](http://ubuntuforums.org/showthread.php?p=9288582)

Hope this helps,
Bodsda

---

