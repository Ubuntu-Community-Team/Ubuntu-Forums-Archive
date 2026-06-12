---
title: "pyGTK builder"
date: 2009-01-03
forum: Programming Talk
---

### Post by Dojan5 on 2009-01-03
Hello.
I'm sorry to post this here, but I don't know where else to post.
I and a friend have developed a OS called Velo, and as a text installer is not the funniest for everyone, I need to develop a graphical user interface for that. We have the pyGTK libraries, and python installed, obviously.

We have a installer, text one, written in python, so I thought that as we have the working installer, developing a GUI shouldn't be too difficult as we wouldn't need to change any sourcecode.

---

### Post by kaivalagi on 2009-01-03
I am not sure whether there is a simple library to use for basic gui development, but generally glade based design is a common approach.

Take a look at glade/gtk, doing a few google searches on these keywords will get you somewhere

I found this good tutorial a while back: [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

Hope that helps

---

### Post by Dojan5 on 2009-01-03
Thank you. It seems a lot better than moving around the buttons myself.
It does make pyGTK interfaces, right?
Oh, what I'm looking for is a pyGTK IDE.

---

### Post by kaivalagi on 2009-01-03
> **Dojan5 said:**
> Thank you. It seems a lot better than moving around the buttons myself.
It does make pyGTK interfaces, right?
Oh, what I'm looking for is a pyGTK IDE.

There is a glade IDE with is pretty good (package in repos is "glade-3"), and there are python IDE's (I use eclipse with pydev plugin), but nothing that joins them up that I know of...well that is free anyway

I have used something called glade2py before now to generate basic skeleton python code from a glade file, which you can then insert snippets into. You can get it from here: [http://sane-pygtk.sourceforge.net/glade2py.html](http://sane-pygtk.sourceforge.net/glade2py.html)

That's the best I can come up with :)

Anyone else got any ideas???

---

### Post by cmat on 2009-01-03
Glade no longer generates Python code. You need to use the resource XML file in creates and load it into your program. You can find some good tutorials all over the net. 

I think SPE has GUI tools for wxWidgets, it's sort of Python and GTK. I prefer to use the XML file because it make the code far less cluttered.

---

### Post by kaivalagi on 2009-01-03
> **cmat said:**
> Glade no longer generates Python code. You need to use the resource XML file in creates and load it into your program. You can find some good tutorials all over the net. 

I think SPE has GUI tools for wxWidgets, it's sort of Python and GTK. I prefer to use the XML file because it make the code far less cluttered.

Maybe I didn't explain it well enough above.

Once you have a glade xml file, you can use glade2py to generate basic python code to handle the events, then edit that python file in an editor to do more specific things. This does mean though that if you want to change the GUI and regenerate the py file, some copying and pasting will be required.

---

### Post by bruce89 on 2009-01-03
> **kaivalagi said:**
> Maybe I didn't explain it well enough above.

Once you have a glade xml file, you can use glade2py to generate basic python code to handle the events, then edit that python file in an editor to do more specific things. This does mean though that if you want to change the GUI and regenerate the py file, some copying and pasting will be required.

This is wrong for a lot of reasons:

[LIST]
[*]You can't modify the UI without rewriting it
[*]The coding style might be different (does Python have much scope for this?)
[/LIST]

It's much better to use libglade, or even more so to use GtkBuilder instead.

---

### Post by kaivalagi on 2009-01-04
> **bruce89 said:**
> This is wrong for a lot of reasons:

[LIST]
[*]You can't modify the UI without rewriting it
[*]The coding style might be different (does Python have much scope for this?)
[/LIST]

It's much better to use libglade, or even more so to use GtkBuilder instead.

Well, I created a test.glade file using glade-3, with a label and button in a window, then generated test.py from it using glade2py. Both files attached in archive.

I haven't added any code for the events but you get the idea...

Granted, gtkbuilder may be a better route, but for a simple dialog which isn't going to change, this is simple enough...

---

