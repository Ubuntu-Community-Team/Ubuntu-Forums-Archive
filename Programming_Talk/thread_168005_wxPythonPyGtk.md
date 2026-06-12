---
title: "wxPython/PyGtk"
date: 2006-04-29
forum: Programming Talk
---

### Post by Wallakoala on 2006-04-29
I have experimented a little with both. I am interested in learning how to make functional gui apps. There are a couple of problems apparent with both of these:

wxPython: Overall, I liked this. The main problem was that there was a minuscule amount of documentation/tutorials for it. I liked how it was pretty simple, and dialogs were very easy to make. The only thing was I couldn't figure out how to use wxGlade.

PyGtk: There was considerably more documentation for this. I found a nice tutorial on how to make guis with glade, and I enjoyed that aspect. PyGtk is more complex than wxPython, but I didn't find it to be too difficult. Most of the problems I found had to do with binding events to buttons, specifically dialogs. I spent almost two hours trying to figure out how to make dialogs do stuff. I was able to get the dialog to display, but the "Ok" button would not do anything no matter how hard I tried.

Basically what I am looking for are some **good** tutorials (or books) on either of these. Also, if there is anywhere I could find some simple programs made in either of these, that would be fantastic.

---

### Post by [woodstock] on 2006-04-29
[QUOTE=Wallakoala]PyGtk: I found a nice tutorial on how to make guis with glade,[...][/QUOTE]
Could you post a link to this tutorial, please? Hopefully that is a tutorial for beginners.
Thank you.

---

### Post by Wallakoala on 2006-04-29
[QUOTE='[woodstock]']Could you post a link to this tutorial, please? Hopefully that is a tutorial for beginners.
Thank you.[/QUOTE]

[http://www.linuxjournal.com/article/6586](http://www.linuxjournal.com/article/6586)

---

### Post by Wallakoala on 2006-04-29
Basically what I need is some good PyGtk example code and/or some more info on using Glade + PyGtk

---

### Post by gjaffe on 2006-04-29
Here's another tutorial that may be helpful.  It shows how to use glade with gladegen to create python scripts automatically with glade.

[http://www.linuxjournal.com/article/7421](http://www.linuxjournal.com/article/7421)

And here's an example of using a dialog

                # I'm using a canned dialog, the ColorSelectionDialog, but this
                # should work just the same with any dialog (I think:) )
                self.colDialog = gtk.ColorSelectionDialog(title)
                # self.apWin is my main window
                self.colDialog.set_transient_for(self.apWin)
                # The run() method of dialogs displays the window, waits for
                # the user to click on of the buttons, and then returns with
                # which button was clicked
                response = self.colDialog.run()
                if response == gtk.RESPONSE_OK:
                        color = self.colDialog.colorsel. \
                                get_current_color()
                        self.FGColor = color
                # You are responsible for destroying the dialog
                self.colDialog.destroy()

Hope this helps.

---

### Post by Wallakoala on 2006-04-29
[QUOTE=gjaffe]Here's another tutorial that may be helpful.  It shows how to use glade with gladegen to create python scripts automatically with glade.

[http://www.linuxjournal.com/article/7421](http://www.linuxjournal.com/article/7421)

And here's an example of using a dialog

                # I'm using a canned dialog, the ColorSelectionDialog, but this
                # should work just the same with any dialog (I think:) )
                self.colDialog = gtk.ColorSelectionDialog(title)
                # self.apWin is my main window
                self.colDialog.set_transient_for(self.apWin)
                # The run() method of dialogs displays the window, waits for
                # the user to click on of the buttons, and then returns with
                # which button was clicked
                response = self.colDialog.run()
                if response == gtk.RESPONSE_OK:
                        color = self.colDialog.colorsel. \
                                get_current_color()
                        self.FGColor = color
                # You are responsible for destroying the dialog
                self.colDialog.destroy()

Hope this helps.[/QUOTE]

Thanks, I understand. What I want to know though is how I could do this with a dialog I already created in glade.

edit: This method works, the only problem is that I don't know how to add text to a dialog...(I figured out how to add a button)

I would really like to know how to use a dialog I made previously in glade. I spent a long time trying to figure that out and it never worked....

---

