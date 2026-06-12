---
title: "[python] New Window From Main Window?"
date: 2008-08-19
forum: Programming Talk
---

### Post by safetycopy on 2008-08-19
Hi,

I'm new to Python and PyGTK/GTK+ development, but I've managed pretty well so far. I'm working on a little GUI to explore various (old and simple) encryption algorithms.

I started with the screenshot below, but what I'd like to do is take the range widget out and move it to a new window that would pop up on clicking an 'options' button that I'll add next to the 'Encrypt' button.

I know how to do various kinds of dialogs, but can't find any info on spawning a new window from the main window.

Also, do I need to know anything in particular about retrieving the values from widgets in a new window, or can I do it in the same way as I'm doing from my main window?

Anyway, here's the screenshot:

[IMG]http://safetycopy.wordpress.com/files/2008/08/screenshot-lucipher.png[/IMG]

---

### Post by days_of_ruin on 2008-08-19
Make another class that has the new window and show it when you click on the right button.

---

### Post by days_of_ruin on 2008-08-19
```
class Popup(object):
    def __init__(self):
        self.window = gtk.Window()
        self.window.show_all()

```
And then have your main window do something like this:
```
popup = Popup()

```

---

### Post by safetycopy on 2008-08-19
Okey doke - will give that a try!

Should I store an instance of the new class in the main class, or just create an instance of the new class when the button's clicked?

Also, how would I pass, say, range values from the range signal handler back to the main application?

I have this to start my application off:

```
if __name__ == "__main__":
	l = Lucipher()
	l.main()
```

So can the new class's signal handler set properties of the 'l' instance?

---

### Post by days_of_ruin on 2008-08-19
your main class can have a variable that you can set to equal the popup windows range value.In the popup class have a callback to set a variable
with the current range value.Make sure it starts with "self." so that you
can access it like this```
popup.range_value
```.

The range widget is on the popup right?

---

### Post by safetycopy on 2008-08-19
> **days_of_ruin said:**
> The range widget is on the popup right?

Yeah, the range will be in the pop-up 'options' window.

I think I get what you're saying, so I'll go play around a bit.

Thanks for your time! :-)

---

