---
title: "Glade troubles"
date: 2007-01-25
forum: Programming Talk
---

### Post by rulus on 2007-01-25
Hi, I'm developing a simple GUI with Glade 3 on Dapper (I built glade from source).

Facing some problems though: initially I had an About dialog which looked like this:
[IMG]http://img260.imageshack.us/img260/2991/screenshot15yt.png[/IMG]

Then I changed some properties until it looked like this:
[IMG]http://img260.imageshack.us/img260/4316/screenshot25an.png[/IMG]

Press 'Save', close Glade. Reopen Glade and it shows the first dialog again... :( 

When I run the dialog with a simple Python script, it looks like this:
[IMG]http://img260.imageshack.us/img260/2337/screenshot32iv.png[/IMG]

Not good, huh! Anyone knows how to solve this problem?

Many thanks!

---

### Post by lnostdal on 2007-01-25
hum, have you checked the path to the image-file in your .glade-file (edit: well, probably can from glade itself also .. heh)? if it is relative it might not refer to the right place at all times

---

### Post by rulus on 2007-01-25
I use the same .png image file for both logo and titlebar icon. The path is entered relative. As you can see, it shows the titlebar icon correctly, so that would be fine I think.

Secondly, in the second screenshot, I set the GtkVBox to size 2 instead of 3 in the first screenshot; and it didn't save that either...

---

### Post by rulus on 2007-01-25
This seems to be a bug in the stock Top Level 'about dialog' of Glade 3.

I rebuilt an about dialog from scratch (starting with an empty window), looking like this:
[IMG]http://img263.imageshack.us/img263/663/screenshotglade8uz.png[/IMG]

When running:
[IMG]http://img263.imageshack.us/img263/6206/screenshotaboutpywallpa1ub.png[/IMG]

So, this works.

Can anyone confirm this bug?

---

### Post by talowe on 2007-01-28
> **rulus said:**
> This seems to be a bug in the stock Top Level 'about dialog' of Glade 3.


Can anyone confirm this bug?

Yes and no.

I'm running edgy with glade3 compiled from svn a few days ago (don't remember exact revision).

Logo doesn't display when first opening glade, just like your example.  If I put cursor in "logo" entry box and hit enter, it appears in the designer window.

The .glade file has the logo property in it, and a simple "C" program displays it properly.

Interestingly, if I enter the full path to the .png, glade3 seems to copy the file to the project directory and truncates the path.  Perhaps there is a project setting to disable this.

Can't keep your .png's in one place and load them from glade without having copies all over?  Not sure I like that behavior.

---

