---
title: "Getting started with Python GUI programming"
date: 2009-03-31
forum: Programming Talk
---

### Post by Nevon on 2009-03-31
I just realized that making GUI applications in Python isn't really all that much harder than writing CLI scripts, however, I seem to have hit a snag. I'm trying to rewrite a number guessing game that I wrote to be used in CLI form, but I think the logic flow is confusing me. When I try to run the program it says I'm referencing the variable "thistime" before assigning a value to it. Why is that? And how do I fix it?

```
#!/usr/bin/env python
#
# A number guessing game with GUI
#
import random
import sys
try:  
    import pygtk  
    pygtk.require("2.0")  
except:  
    pass  
try:  
    import gtk  
    import gtk.glade  
except:  
    print("GTK Not Availible")
    sys.exit(1)

class guihandler:

    wTree = None

    def __init__( self ):
        self.wTree = gtk.glade.XML( "mainGUI.glade" )
        
        dic = { 
            "on_quit_clicked" : self.quit,
            "on_ok_clicked" : self.guess,
            "on_window1_destroy" : self.quit,
        }
        
        self.wTree.signal_autoconnect( dic )
        
        gtk.main()
    
    def guess(self, widget):
        try:
            thistime = guesser( self.wTree.get_widget("entry").get_text() )
        except ValueError:
            self.wTree.get_widget("warningbox").show()
            self.wTree.get_widget("entry").set_text("ERROR")
            return 0
        self.wTree.get_widget("warningbox").hide()
        self.wTree.get_widget("textview").set_text(thistime.giveResult())
    def quit(self, widget):
        sys.exit(0)
        
class guesser:
    def __init__(self, gnum):
        if thistime == rnum:
            thistime = str(thistime)
            self.result = thistime + " is the magic number!"
        elif thistime < rnum:
            thistime = str(thistime)
            self.result = thistime + " is too low."
        elif thistime > rnum:
            thistime = str(thistime)
            self.result= thistime + " is too high."
        
    def giveResult():
        return str(self.result)
rnum = random.randint(1,100)
start = guihandler()
```

```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.5 on Tue Mar 31 17:23:54 2009 -->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <property name="visible">True</property>
    <signal name="destroy" handler="on_window1_destroy"/>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkVBox" id="vbox2">
            <property name="visible">True</property>
            <child>
              <widget class="GtkLabel" id="label1">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Guess a number between 1-100!</property>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="padding">5</property>
              </packing>
            </child>
            <child>
              <widget class="GtkScrolledWindow" id="scrolledwindow1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="hscrollbar_policy">GTK_POLICY_AUTOMATIC</property>
                <property name="vscrollbar_policy">GTK_POLICY_AUTOMATIC</property>
                <child>
                  <widget class="GtkTextView" id="textview">
                    <property name="height_request">157</property>
                    <property name="visible">True</property>
                    <property name="sensitive">False</property>
                    <property name="can_focus">True</property>
                    <property name="left_margin">2</property>
                    <property name="right_margin">2</property>
                    <property name="accepts_tab">False</property>
                  </widget>
                </child>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <child>
              <widget class="GtkVBox" id="vbox3">
                <property name="visible">True</property>
                <child>
                  <widget class="GtkHBox" id="warningbox">
                    <child>
                      <widget class="GtkImage" id="warningimg">
                        <property name="visible">True</property>
                        <property name="stock">gtk-dialog-warning</property>
                      </widget>
                      <packing>
                        <property name="expand">False</property>
                        <property name="fill">False</property>
                        <property name="padding">3</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="GtkLabel" id="warningmsg">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">Value is not a valid number. Use only numbers!</property>
                      </widget>
                      <packing>
                        <property name="position">1</property>
                      </packing>
                    </child>
                  </widget>
                  <packing>
                    <property name="expand">False</property>
                    <property name="fill">False</property>
                    <property name="padding">5</property>
                  </packing>
                </child>
                <child>
                  <widget class="GtkEntry" id="entry">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                  </widget>
                  <packing>
                    <property name="expand">False</property>
                    <property name="fill">False</property>
                    <property name="padding">1</property>
                    <property name="position">1</property>
                  </packing>
                </child>
              </widget>
            </child>
            <child>
              <widget class="GtkButton" id="ok">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">gtk-ok</property>
                <property name="use_stock">True</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_ok_clicked"/>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="padding">3</property>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <widget class="GtkButton" id="quit">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">gtk-quit</property>
                <property name="use_stock">True</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_quit_clicked"/>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="padding">2</property>
                <property name="position">2</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>
```

---

### Post by dandaman0061 on 2009-03-31
Just after a basic look at it... It looks like your 'guesser' class which is initialized with:
```

        try:
            thistime = guesser( self.wTree.get_widget("entry").get_text() )
        except ValueError:

```

The class __init__ method assigns whatever the get_text() returns to 'gnum'
This is where I'd guess 'thistime' is being used before being set
```

class guesser:
    def __init__(self, gnum):
        if thistime == rnum:
            thistime = str(thistime)
            self.result = thistime + " is the magic number!"
        elif thistime < rnum:

```
As far as the __init__ function can see, there is no visible 'thistime' variable, and you try to compare it with 'rnum'.
I wonder if this is a typo and you meant to compare 'gnum' instead, as I don't see you using 'gnum' at all...

---

### Post by Nevon on 2009-04-01
> **dandaman0061 said:**
> Just after a basic look at it... It looks like your 'guesser' class which is initialized with:
```

        try:
            thistime = guesser( self.wTree.get_widget("entry").get_text() )
        except ValueError:

```

The class __init__ method assigns whatever the get_text() returns to 'gnum'
This is where I'd guess 'thistime' is being used before being set
```

class guesser:
    def __init__(self, gnum):
        if thistime == rnum:
            thistime = str(thistime)
            self.result = thistime + " is the magic number!"
        elif thistime < rnum:

```
As far as the __init__ function can see, there is no visible 'thistime' variable, and you try to compare it with 'rnum'.
I wonder if this is a typo and you meant to compare 'gnum' instead, as I don't see you using 'gnum' at all...
Oh, that's right! For some reason I was using thistime instead of gnum. gnum stands for guessed number, and rnum stands for right number. So obviously I want the number in the text input to be assigned to gnum, which is what I then want to compare. 

However, now I seem to be having some problems with my textview. I guess set_text() is not the correct attribute for textviews. How do I print the return from the class guesser to appear in the textview when the player presses OK? Also, the next time the player guesses I want the return to appear on a new line, not just replace what was there before.

Anyone know how to do that?

---

### Post by G|N| on 2009-04-01
You have to use a buffer on a textview:

```

log_buffer = self.wTree.get_widget("textview").get_buffer()
log_buffer.set_text(thistime.giveResult())

```

to clear the textview:
```

start = log_buffer.get_start_iter()
end = log_buffer.get_end_iter()
log_buffer.delete(start, end) 

```

More information on the gtk.TextBuffer: [http://www.pygtk.org/docs/pygtk/class-gtktextbuffer.html](http://www.pygtk.org/docs/pygtk/class-gtktextbuffer.html)

---

### Post by Nevon on 2009-04-01
Great! Now after some minor adjustments to the function getResult(), it seems to be working. However, the textview gets overwritten every time I make a guess. I'm going to take a look at that link G|N| gave me, and see if that helps. But feel free to give me a pointer if you know how to fix it.

Oh, by the way, getResult() now looks like this: 
```
def giveResult(self):
    return str(self.result)
```

---

### Post by G|N| on 2009-04-01
To append the text instead of overwriting it:
```

text = log_buffer.get_text()
text += thistime.giveResult() + "\n"
log_buffer.set_text(text)

```

---

### Post by Nevon on 2009-04-01
> **G|N| said:**
> To append the text instead of overwriting it:
```

text = log_buffer.get_text()
text += thistime.giveResult() + "\n"
log_buffer.set_text(text)

```

Oh, I solved it by changing the insert function to insert_at_cursor and then appending each string with a newline. 

However, now the actual game seems to be borked. :p For some reason rnum keeps changing its value everytime I enter a guess, and even if I guess a number that's lower than the random number it still says gnum is higher than rnum.

```
#!/usr/bin/env python
#
# A number guessing game with GUI
#
import random
import sys
try:  
    import pygtk  
    pygtk.require("2.0")  
except:  
    pass  
try:  
    import gtk  
    import gtk.glade  
except:  
    print("GTK Not Availible")
    sys.exit(1)

class guihandler:

    wTree = None

    def __init__( self ):
        self.wTree = gtk.glade.XML( "mainGUI.glade" )
        
        dic = { 
            "on_quit_clicked" : self.quit,
            "on_ok_clicked" : self.guess,
            "on_window1_destroy" : self.quit,
        }
        
        self.wTree.signal_autoconnect( dic )
        
        gtk.main()
    
    def guess(self, widget):
        try:
            gnum = guesser( self.wTree.get_widget("entry").get_text() )
        except ValueError:
            self.wTree.get_widget("warningbox").show()
            self.wTree.get_widget("entry").set_text("ERROR")
            return 0
        self.wTree.get_widget("warningbox").hide()
        log_buffer = self.wTree.get_widget("textview").get_buffer()
        log_buffer.insert_at_cursor(gnum.giveResult())
#        self.wTree.get_widget("textview").set_text(gnum.giveResult())
    def quit(self, widget):
        sys.exit(0)
        
class guesser:
    def __init__(self, gnum):
        try:
            rnum
        except UnboundLocalError:
            rnum = random.randint(1,100)
        if gnum == rnum:
            thistime = str(gnum)
            self.result = gnum + " is the magic number!\n"
        elif gnum < rnum:
            gnum = str(thistime)
            self.result = gnum + " is too low.\n"
        elif gnum > rnum:
            gnum = str(gnum)
            self.result= gnum + " is too high.\n"
        else:
            gnum = str(gnum)
            rnum = str(rnum)
            self.result= "Error! Gnum (" + gnum + ") or rnum (" + rnum + ") seem to be corrupted somehow."
        
    def giveResult(self):
        return str(self.result)
start = guihandler()
```

---

### Post by G|N| on 2009-04-01
Hmmm your code is not correct....

I would solve it like this:
```
        
class Guesser:
    def __init__(self):
        self.rnum = random.randint(1,100)

    def check_if_correct(self, gnum):
        self.result = ""
        thistime = "" #for what do you use this?
        if gnum == self.rnum:
            gnum = str(gnum)
            self.result = gnum + " is the magic number!\n"
        elif gnum < self.rnum:
            gnum = str(gnum)
            self.result = gnum + " is too low.\n"
        elif gnum > self.rnum:
            gnum = str(gnum)
            self.result= gnum + " is too high.\n"
        else:
            gnum = str(gnum)
            rnum = str(self.rnum)
            self.result= "Error! Gnum (" + gnum + ") or rnum (" + rnum + ") seem to be corrupted somehow."
        
    def giveResult(self):
        return str(self.result)

```

---

### Post by Nevon on 2009-04-01
> **G|N| said:**
> Hmmm your code is not correct....

I would solve it like this:
```
        
class Guesser:
    def __init__(self):
        self.rnum = random.randint(1,100)

    def check_if_correct(self, gnum):
        self.result = ""
        thistime = "" #for what do you use this?
        if gnum == self.rnum:
            gnum = str(gnum)
            self.result = gnum + " is the magic number!\n"
        elif gnum < self.rnum:
            gnum = str(gnum)
            self.result = gnum + " is too low.\n"
        elif gnum > self.rnum:
            gnum = str(gnum)
            self.result= gnum + " is too high.\n"
        else:
            gnum = str(gnum)
            rnum = str(self.rnum)
            self.result= "Error! Gnum (" + gnum + ") or rnum (" + rnum + ") seem to be corrupted somehow."
        
    def giveResult(self):
        return str(self.result)

```
thistime is just a typo. I have previously written this game to be used in a CLI environment, and then I used the thistime variable. But it's not supposed to be used in this version. The only variables that are used should be:
gnum = the guessed number. Comes from the textbox "entry".
rnum = The correct number. Generated via rnum = random.randomint(1,100).
result = The outcome from the comparison of gnum and rnum. 

But if you solve it like you have, wouldn't rnum be set everytime the class Guesser is initiated?

EDIT: I just tried it out, and it gave me multiple errors. First some that had to do with capitalization, but that's no big deal. Then it was complaining that I had given __init__ two arguments when it only needed one. After that, things got really hairy. 

It might be easier if you have the full source so that you can see for yourself.
Here's mainGUI.glade: [http://pastebin.com/f43760898](http://pastebin.com/f43760898)
Here's my version of numberguess.py: [http://pastebin.com/f2be06b2](http://pastebin.com/f2be06b2)
And here's the version with your changes in it: [http://pastebin.com/f3d942a48](http://pastebin.com/f3d942a48)
Just put them in the same directory and run the python program.

---

### Post by G|N| on 2009-04-01
Here is a working version :)
```


#!/usr/bin/env python
#
# A number guessing game with GUI
#
import random
import sys
try:  
    import pygtk  
    pygtk.require("2.0")  
except:  
    pass  
try:  
    import gtk  
    import gtk.glade  
except:  
    print("GTK Not Availible")
    sys.exit(1)

class guihandler:

    wTree = None

    def __init__( self ):
        self.wTree = gtk.glade.XML( "mainGUI.glade" )
        
        dic = { 
            "on_quit_clicked" : self.quit,
            "on_ok_clicked" : self.guess,
            "on_window1_destroy" : self.quit,
        }
        
        self.wTree.signal_autoconnect( dic )
        self.guesser = Guesser()
        gtk.main()
    
    def guess(self, widget):
        try:
            gnum = self.guesser.check_if_correct( self.wTree.get_widget("entry").get_text() )
        except ValueError:
            self.wTree.get_widget("warningbox").show()
            self.wTree.get_widget("entry").set_text("ERROR")
            return 0
        self.wTree.get_widget("warningbox").hide()
        log_buffer = self.wTree.get_widget("textview").get_buffer()
        log_buffer.insert_at_cursor(self.guesser.giveResult())
    def quit(self, widget):
        sys.exit(0)
        
class Guesser:
    def __init__(self):
        self.rnum = random.randint(1,100)

    def check_if_correct(self, gnum):
        self.result = ""
        gnum = int(gnum)
        if gnum == self.rnum:
            gnum = str(gnum)
            self.result = gnum + " is the magic number!\n"
        elif gnum < self.rnum:
            gnum = str(gnum)
            self.result = gnum + " is too low.\n"
        elif gnum > self.rnum:
            gnum = str(gnum)
            self.result= gnum + " is too high.\n"
        else:
            gnum = str(gnum)
            rnum = str(self.rnum)
            self.result= "Error! Gnum (" + gnum + ") or rnum (" + rnum + ") seem to be corrupted somehow."
        
    def giveResult(self):
        return str(self.result)
start = guihandler()

```

Your main problem was that you did not convert gnum to an integer :)
And the name of a class is always written with a capital letter.

---

