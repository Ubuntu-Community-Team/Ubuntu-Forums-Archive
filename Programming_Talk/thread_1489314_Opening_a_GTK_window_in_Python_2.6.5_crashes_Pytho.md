---
title: "Opening a GTK window in Python 2.6.5 crashes Python"
date: 2010-05-21
forum: Programming Talk
---

### Post by herdivet on 2010-05-21
When I type the following in Python IDLE -

[PHP]import gtk
window = gtk.Window()
[/PHP]

Python crashes and closes as soon as I type the second parenthesis.

If I run it in a separate window, Python hangs.

I have reviewed the FAQ.  I've run it on Ubuntu 10.04, 9.10 and 9.04 and with the same results.  I tried looking for help at GTK.org, and searched the Ubuntu Forums.  I can't figure out what I'm doing wrong here.

---

### Post by rrashkin on 2010-05-21
For reasons I can no longer remember, I include a version requirement:
```
pygtk.require('2.0')
import gtk

```

And I also pass in a window spec:  gtk.Window(gtk.WINDOW_TOPLEVEL)

---

### Post by herdivet on 2010-05-21
Thank you for the response.  I put in the requirement, but inside IDLE it still crashes.  In investigating further it's just weird.  

In IDLE interactive - it crashes and closes IDLE.
In IDLE in a separate window -
   If I change code and press F5 to run - it crashes and closes IDLE.
   If I change code, save and then press F5 - it runs fine.
   If I don't change code and run - it runs fine.

If I run Python in a terminal window it runs without any problem.

I like using IDLE to write and test code, and haven't had this problem before, but wasn't using GTK.  I guess I'll have to find another editor for Python, GTK and IDLE won't play nice.  Thanks again.

---

### Post by StephenF on 2010-05-22
Even worse, in IDLE:
```

import gtk
gtk.main()

```
Try Ctrl+C-ing your way out of that!

---

### Post by nvteighen on 2010-05-22
Ugh... it seems like a bug in IDLE... but a weird one. The only thing I can relate it to is to this bug from 2003: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=200084](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=200084)

All what we know right now is that the interactive part of using GTK+ in IDLE is failing, as any time you load a saved version of your code it works.

Anyway, your code is not completely right either. A clean PyGtk start-up would be like this. Please, try it and tell us what happens:
```

import pygtk
pygtk.require("2.0")
import gtk

mywin = gtk.Window()
mywin.connect("delete-event", gtk.main_quit)
mywin.show()

gtk.main()

```

---

### Post by herdivet on 2010-05-22
> **nvteighen said:**
> Ugh... 
...

Anyway, your code is not completely right either. A clean PyGtk start-up would be like this. Please, try it and tell us what happens:
```

import pygtk
pygtk.require("2.0")
import gtk

mywin = gtk.Window()
mywin.connect("delete-event", gtk.main_quit)
mywin.show()

gtk.main()

```


When I try the code above in IDLE interactive, as soon as I type the closed parenthesis in line 4 (mywin = gtk.Window()) IDLE crashes and closes.  That's not good, but I don't HAVE to use it interactively.  It's just convenient for small sections of code.

If I open a window in IDLE and paste in the code, press F5 to run, click OK to save the code, it does work, so it is my code that needs cleaned up.  I took the code from a tutorial on how easy it is to use GTK and it was showing how to quickly create a window.  I'll need to go to a more in depth source on programming in GTK, and not use IDLE in interactive mode.

Thanks again for all your help.  This was driving me crazy and that's a short trip.

---

### Post by wmcbrine on 2010-05-22
You shouldn't let this problem stop you from doing interactive development -- you'd just have to use the standard Python shell instead of IDLE.

---

### Post by herdivet on 2010-05-24
True - I can open IDLE and a session of Python and work that way.  Thanks for the suggestion.  I've got lots to learn, but it's good to have help so handy.

---

### Post by narnie on 2010-07-03
> **nvteighen said:**
> Ugh... it seems like a bug in IDLE... but a weird one. The only thing I can relate it to is to this bug from 2003: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=200084](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=200084)

All what we know right now is that the interactive part of using GTK+ in IDLE is failing, as any time you load a saved version of your code it works.

Anyway, your code is not completely right either. A clean PyGtk start-up would be like this. Please, try it and tell us what happens:
```

import pygtk
pygtk.require("2.0")
import gtk

mywin = gtk.Window()
mywin.connect("delete-event", gtk.main_quit)
mywin.show()

gtk.main()

```

I'm having the same bug. Very frustrating as I really like IDLE and how it gives you "hints" as you type.

I was hoping 10.04 would see this fixed, but alas.

The above code crashes for me as well. Not at the end of "mywin = gtk.Window()" as soon as I hit the first or second parenthesis (perhaps signaling something in the hints workings???).

Here is the output from running it from a shell:

> Warning (from warnings module):
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 127
    set_interactive(1)
RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
>>> The program 'idle' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 5832 error_code 3 request_code 15 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

The > RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK

is after importing gtk

The other after the parenthesis.

Any ideas?

Thanks,
Narnie

---

### Post by narnie on 2010-07-03
> **herdivet said:**
> True - I can open IDLE and a session of Python and work that way.  Thanks for the suggestion.  I've got lots to learn, but it's good to have help so handy.

I recommend checking out ipython in the repos. It is like a merger of the bash shell and the python interactive shell.

I was getting help from a Python instructor for college (I'm not in college, it was just on forum), and she recommended it.

It allows you to do cool things like:

```
In [72]: ls
alignment.py  buttons.py  calculator.py  center_window.py  fixed.py  icon.py  tooltips.py  windows.py

In [73]: pwd
Out[73]: '/home/woodnt/Projects/Learning Python/Tutorial - zetcode'

In [74]: cd ..
/home/woodnt/Projects/Learning Python

In [75]: cd Tutorial\ -\ zetcode 
/home/woodnt/Projects/Learning Python/Tutorial - zetcode

In [76]: #run alignment.py 

In [77]:
```

It does this all with tab autocompletion. It seems brilliant, but I've only touched the surface with it.

The Python autocompletion isn't quite as robust as IDLE, but ipython is great for me (a very green beginner). There is a lot to learn about ipython and I'm just on the beginnings of the learning curve, but I think it will be useful for testing gtk code.

I'm using it as a terminal in gedit which gives me highlighting and makes is somewhat close to a basic IDE. I tend to have it running (with a gnome terminal with 2 tabs {1 for shell and 1 for python shell} that I use to look up documentation and other things while testing (second screen shot all the way at the bottom).

Cheerio,
Narnie

[IMG]http://dl.dropbox.com/u/3667656/screenshot_053.jpeg[/IMG]

[IMG]http://dl.dropbox.com/u/3667656/screenshot_054.jpeg[/IMG]

---

