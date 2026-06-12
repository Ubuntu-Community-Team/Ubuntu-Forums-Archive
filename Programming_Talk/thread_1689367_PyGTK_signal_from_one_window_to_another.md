---
title: "PyGTK signal from one window to another"
date: 2011-02-16
forum: Programming Talk
---

### Post by fstephens on 2011-02-16
How can I check from a parent window if a button is toggled in a child window? I need to check periodically if the button on the other window has been toggled on. The windows are created in separate files, the child window from a Glade file. The parent window is a Gnome Applet.

I have Goggled it repeatedly, but somehow I am missing the answer. None of the tutorials or examples seem to work for me.
Any ideas greatly appreciated!

---

### Post by nvteighen on 2011-02-17
What I would have done is this:

0. Encapsulate the UI layout in a class (if the UI is split into different files, I'd use importing and inheriting so that at some stage everything is packed into a single class). Call it 'View'. Here, I'd place a variable that monitors whether the button

1. Centralize all callbacks into a class 'Callbacks', with access to the 'View' instance (passing it as argument to the constructor and save a reference as an attribute). The callbacks must be static methods of the class, so I have more control on how the arguments are passed. Otherwise, the 'self' argument will get in the way.

2. Create a callback in 'Callbacks' for the button for the "clicked" event... the "toggling" would be implemented here and as the 'Callbacks' class has access to 'View', I'd modify the monitor variable from here.

The problem is that this may require a major redesign... So, something else you can do is to extend the GTK+ main loop on your own, so that it checks for the status of your button. There's the gtk.main_iteration() function, which just performs one iteration of the main loop. You may need threading though, depending on how you're doing this.

---

### Post by fstephens on 2011-02-17
Thanks allot for the ideas. Unfortunately, as I am just (re)learning Python and PyGTK, I think this is beyond my current understanding. If I do the major re-write as suggested for the first solution, I will probably break it and never be able to fix it. I have to implement only what I can (semi-)understand as I learn more. 

I don't see how the second option would help me, as I am not trying to completely stop processing in the parent window, but just stop processing in a timed loop while the button in the child window is toggled. But of course maybe I just don't understand your reasoning.
I was hoping there was a simple way to do this that I just hadn't found yet.

Lack of good, beginner friendly documentation is a criticism I had often heard about GTK, and one reason I had shied away from it before. Examples in C don't help too much if you are using Python. I was hoping with Quickly there was going to be more emphasis on making it accessible, but the documentation on Quickly is almost non-existent as well. I have gotten this applet up and running (with lots of Googling), but this issue is stopping me from moving forward. 

Anyway, I really appreciate your trying to help.

---

