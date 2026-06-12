---
title: "save/restore window position in GTK+?"
date: 2008-01-20
forum: Programming Talk
---

### Post by Ansible on 2008-01-20
I'm writing an application with GTK+, and I'd like to save/restore the window position so that it is the same size as the last time the app was run.  Restoring window position is a secondary concern, but that would be nice too.

I got this to work with gtk_window_resize and gtk_window_move.  However, the GTK docs say that "It's much preferred to let the window manager handle these things rather than doing it yourself".  However, the window manager doesn't save and restore my window position or size, if I don't resize it myself it comes up in the minimum size every time, usually in a random corner of the screen.  I don't see anything in the GTK docs to enable save/restore in the window manager.

So I want to do the right/standard thing here, whatever that is.  Is there a way to tell GTK to tell the window manager to save/restore my window position?  

An additional complication is that my app is cross platform, so all this has to work in ms windows too - although I could use an alternative method on that platform if necessary.

---

### Post by Ansible on 2008-01-20
Forgot to mention that on windows the resize works, but all the widgets in the window stay their original size.  If you resize the window yourself then everything sizes correctly.  On ubuntu the widgets are sized to fit the window already.  A hint here would be appreciated as well...

---

### Post by MicahCarrick on 2008-01-20
When I develop an app (such as an IDE) in which I restore window position, size, and/or state, I always make sure it's an option which is off by default. If the window manager takes care of this for the user fine, otherwise they can turn that functionality on.

---

### Post by Geekkit on 2008-01-20
Not sure what's supposed to be right or wrong but what I do is in the following C code (header and implementation file) in the zip file attached.

---

### Post by Ansible on 2008-01-21
Ah, good stuff.  Thx for the code sample.  

So you use gtk_window_size and gtk_window_move as well - and check for it being offscreen, which I wasn't doing.  Well I won't be the only one doing that then - the GTK docs seem to imply that this is a Bad Thing in linux, but they don't really say what the right way is either.

---

### Post by Geekkit on 2008-01-21
> **Ansible said:**
> Ah, good stuff.  Thx for the code sample.  

So you use gtk_window_size and gtk_window_move as well - and check for it being offscreen, which I wasn't doing.  Well I won't be the only one doing that then - the GTK docs seem to imply that this is a Bad Thing in linux, but they don't really say what the right way is either.

You're welcome. The way I look at it is that they wouldn't include it in the API if they didn't want it to be used. I think the worst thing about GTK/GDK is that it's poorly documented. If however you dig, you'll find some very powerful API calls that can make your application quite feature laden.

:)

EDIT: the reason why I check for being off screen is what if the user changed resolutions? The window shouldn't appear off screen but if it does, resize and place it at a default size and coordinate (e.g., 0, 0). Feel free to change this behavior.

:)

---

