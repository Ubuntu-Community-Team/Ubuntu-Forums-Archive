---
title: "Translation app in Python - GTK?"
date: 2012-08-15
forum: Programming Talk
---

### Post by SelbyRowleyCannon on 2012-08-15
I have a small translation program, written in python (2.7), that performs this function on user-entered text:

def translate():
    Text = raw_input("Please enter your text: ")
    Text.lower()
    Text.split()
    for word in Text.split():
        try:
            print dictionary[word]
        except KeyError:
            print"Word Not Translated"

I a trying to make a GUI for this with PyGTK, and I have the necessary objects (Two buttons (To English and from English))  but I don't know how to have the user press one of the buttons and perform the corresponding function on the text in the textfield. How do I do this?

---

### Post by DarkAmbient on 2012-08-16
You need to learn about signals and callbacks. It's not as difficult as it sounds like. 

[http://www.pygtk.org/pygtk2tutorial/sec-TheoryOfSignalsAndCallbacks.html](http://www.pygtk.org/pygtk2tutorial/sec-TheoryOfSignalsAndCallbacks.html)

Every element of a gkt-window is called a widget, and every widget has its own signal-prototypes. And with every widget being a child of another widget, that child-widget inherits it's parents interface. (Widgets also implements other interfaces / widgets)

Except your buttons, to add input and get output, use either [_gtk.Entry_ (one-line input)]("http://www.pygtk.org/docs/pygtk/class-gtkentry.html") or  [_gtkTextView_]("http://www.pygtk.org/docs/pygtk/class-gtk.Textview.html") (multiline). Read up on how to catch and set text inside the your text-widget of choice.

---

