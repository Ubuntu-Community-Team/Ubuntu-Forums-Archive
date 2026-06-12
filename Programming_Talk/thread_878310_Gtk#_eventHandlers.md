---
title: "Gtk# eventHandlers"
date: 2008-08-02
forum: Programming Talk
---

### Post by bubba_169 on 2008-08-02
Straight to the point, other than using 'global' variables, is it possible to pass a value to an event handler function as you would a parameter to an ordinary function?

I.E. I have an event function that, when a button is clicked, does a series of things then closes a certain window. Most of the instructions are the same I just want to close a different window depending on which button is clicked. How could I pass the handle of the window to be closed, to the event function? (This is just hypothetical, there are many reasons I want to do this)

In pygtk this is easy as we have the 'user data' parameter in the connect method however I cant seem to find this in mono and gtk# and the usual recommended way to connect an event is to just 'button.Clicked += button_clicked;' where button is your button widget and button_clicked is your event function. It doesnt help that the mono docs are only half complete aswell (nearly at 2.0 and they still wont tell us how to use it properly :confused:)

Sorry about the long post, hope someone can help...

---

### Post by bubba_169 on 2008-08-03
*bump*

---

### Post by true_friend on 2008-08-03
[Mono forums]("http://www.go-mono.com/forums/") may answer.

---

