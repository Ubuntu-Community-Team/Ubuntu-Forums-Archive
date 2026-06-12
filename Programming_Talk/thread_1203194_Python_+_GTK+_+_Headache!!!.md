---
title: "Python + GTK+ + Headache!!!"
date: 2009-07-03
forum: Programming Talk
---

### Post by Empire537 on 2009-07-03
I'm a professional python programmer exploring GTK+, I'm very satisfied. One think I want to know is this:

Is it possible to do a function on every keystroke? So whenever you press a key a status updates? I want it do display you're current line and total lines in a text file. The only way I can think of doing it would be to set it up like this:

def update(self):
do_my_update

if keystroke:
self.update()

is this possible? If so how?

In case you've guessed I'm using a TextView.

---

### Post by unutbu on 2009-07-03
Every gtk.TextView has an associated gtk.TextBuffer. (gtk.TextView.get_buffer()...)

Every gtk.TextBuffer emits a "changed" signal whenever the buffer is changed. (See [http://www.pygtk.org/pygtk2reference/class-gtktextbuffer.html](http://www.pygtk.org/pygtk2reference/class-gtktextbuffer.html)). 

So if you connect a callback for the "changed" signal, you should be able to self.update() whenever a key is pressed.

---

### Post by nvteighen on 2009-07-03
Use a signal. GtkTextBuffer (which you usually have to use when using a GtkTextView) provides the "changed" signal.

Edit: Seems I've been defeated in speed! :p

---

### Post by Empire537 on 2009-07-03
I read up on the dogs. The problem is. I have to change the current line when I clickwith the mouse. And when I move the cursor posi with the arrow keys.

---

### Post by bapoumba on 2009-07-03
One post removed from this thread.

---

### Post by Can+~ on 2009-07-03
> **Empire537 said:**
> I read up on the dogs. The problem is. I have to change the current line when I clickwith the mouse. And when I move the cursor posi with the arrow keys.

Sometimes to find an event, instead of googling it up, I end up looking in glade for the signal name

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot1-3.png[/IMG]


> **bapoumba said:**
> One post removed from this thread.

what happend?

---

### Post by bapoumba on 2009-07-03
> **Can+~ said:**
> 
what happend?
Oh, some non-constructive comment :)

---

### Post by Empire537 on 2009-07-03
So then how do I trigger an event from the move_cursor command? Same with get_modified, is there a way to do get_modified == True: self.update()? Because I don't think it's constantly looping the program, so if I add that it won't constantly get triggered, right? I'm still new to the whole GTK+ thing...

---

### Post by Can+~ on 2009-07-03
Each time you click a button, a signal of certain type and name is given. This is known as [Event-Driven Programming]("http://en.wikipedia.org/wiki/Event-driven_programming")

PyGTK implementation uses a Dictionary to link between signals (strings) and function calls. 

[http://www.pygtk.org/articles/pygtk-glade-gui/Creating_a_GUI_using_PyGTK_and_Glade.htm](http://www.pygtk.org/articles/pygtk-glade-gui/Creating_a_GUI_using_PyGTK_and_Glade.htm)
(A bit old, but it's the same idea)

---

### Post by Empire537 on 2009-07-03
What if i want it to update without clicking a button? I have it so it gets the line count when you save, but I want it to update when you type, click, or move the arrow keys.

---

### Post by Can+~ on 2009-07-03
> **Empire537 said:**
> What if i want it to update without clicking a button? I have it so it gets the line count when you save, but I want it to update when you type, click, or move the arrow keys.

Actually, I don't know why I said "a button". Pretty much anything can trigger an event.

What are you using to build your pygtk app?

---

### Post by Empire537 on 2009-07-03
I'm not using glade... I'm using gedit. Then terminal to run. No need to compile. How do I trigger an ever with it?

---

### Post by Can+~ on 2009-07-03
> **Empire537 said:**
> I'm not using glade... I'm using gedit. Then terminal to run. No need to compile. How do I trigger an ever with it?

Why would you need to compile?

You can either:
-Keep doing everything with pygtk directly and have to add a new event to the widget (look up on the pygtk tutorial)
-Make it in glade3 and just type in a signal, then use a dictionary.

Btw, using glade3 doesn't need to compile, it's a plain xml file that holds the info about the widgets and event names.

I've attached a simple example file made with glade3 (.py + .glade)

---

### Post by Empire537 on 2009-07-03
So if I make it in Glade3 I don't need to use python at all? Glade does all the work for me?

---

### Post by Can+~ on 2009-07-03
> **Empire537 said:**
> So if I make it in Glade3 I don't need to use python at all? Glade does all the work for me?

On Glade you create the visual aspect of the app, plus the event handling; and in python you code the functionality.

Tutorial:
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

---

### Post by Empire537 on 2009-07-03
Is there a way to get the current line you're on? I see how to get the total count, how do I get the current count.

Thanks so much for the glade-3 reference!! I rewrote the entire program with a toolbar in less than 30 minutes. I was trying to follow the tuts using glade2 and I couldn't figure out how to get glade3, I had to use sudo apt-get install glade-3 not glade3, it was screwing me up.

Anyway, if you know how please let me know!

---

### Post by days_of_ruin on 2009-07-04
```
text_iter = buffer.get_iter_at_mark(buffer.get_insert())
line_number = text_iter.get_line()
```

---

### Post by Empire537 on 2009-07-04
But how do I print that...

Hehe, nevermind, you forgot to add () to the end of the last function.

---

