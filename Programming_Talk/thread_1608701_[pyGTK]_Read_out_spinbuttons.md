---
title: "[pyGTK] Read out spinbuttons"
date: 2010-10-29
forum: Programming Talk
---

### Post by teHIngo on 2010-10-29
For a small timer app I want to write a GTK interface where I can set the desired time. Here is a picture of the interface:

[IMG]http://i.imgur.com/shq8D.png[/IMG]

However, I am having trouble reading out the fields of the spin buttons. My envisaged procedure for this is the following:

Read out the buttons using methods for each button
Here is one of the methods that does this:

```
# Get the fields of the spinbuttons
def get_seconds(self, widget, spin):
    self.rSeconds = spin.get_value_as_int()
```

It is then called like this:

```
    button = gtk.Button("Start")
    button.connect("clicked", self.get_seconds, spinnerS)
```

Create a timer object with the data from the buttons
This is planned to be accomplished using this method:

```
    # Create the timer object ...
   def prepare_timer(self, widget, hours, minutes, seconds, title, text):
     self.timer = eggTimer(hours, minutes, seconds, title, text)
```

Which is called here:

```
button.connect("clicked", self.prepare_timer, self.rHours, self.rMinutes, self.rSeconds, "some title", "some text")
```

Unfortunately, when running the script I get the following error message:

```
Traceback (most recent call last):
File "GTKInterface.py", line 140, in <module>
SpinButtonExample()
File "GTKInterface.py", line 126, in __init__
button.connect("clicked", self.prepare_timer, self.rHours, self.rMinutes, self.rSeconds, "Title", "Text")
AttributeError: SpinButtonExample instance has no attribute 'rSeconds'
```

To check whether there really is no instance of that variable, I programmed a short method to print it:

```
   def returnS(self, widget):
       print self.rSeconds

```

And surprisingly this method can "see" self.rSeconds. This makes me wonder what determines the visibility of the variable. What am I doing wrong to read this out?

The whole code can be found here: [http://pastie.org/1255962](http://pastie.org/1255962)

Please note that I have already posted this on StackOverflow [here](http://stackoverflow.com/questions/4044759/how-can-i-properly-read-out-spin-buttons-in-pygtk). Sorry for this, I usually do not support cross-posting but I'm really destitute with this matter. Thanks in advance for any help!

---

### Post by worksofcraft on 2010-10-30
I copied your code to see if I can fix it but it just says:

ImportError: No module named Time_Calculation

---

### Post by teHIngo on 2010-10-30
That is because I did not post that module. Thanks anyway, I managed to solve the problem finally. Hope I didn't bother anyone!

---

