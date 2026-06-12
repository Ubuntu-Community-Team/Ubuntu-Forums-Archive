---
title: "corrupted after recent update"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by Autodave on 2011-11-05
Friend's computer running Ubuntu 10.04.  After recent update, desktop comes up, but top menu bar does not display Applications,Files, or System boxes in top left.  Clicking with the mouse in that area causes the pointer to leave a pointer there and where ever else you click.  Sometimes, the box will appear then, but it is still not useable.  I cannot get into anything.  Any ideas?

I thought that there used to be a "system restore" or something like that on the install disk, but I cannot find that.  Is it still there and how do I get to it?  What do I do after getting to it?

Thanks in advance!

---

### Post by enkay009 on 2011-11-05
I gotta feeling you're talking about Unity. From version 11.04 on, the default desktop has been changed to Unity.

Just to be sure, can you post a screenshot?

---

### Post by Autodave on 2011-11-05
> **enkay009 said:**
> I gotta feeling you're talking about Unity. From version 11.04 on, the default desktop has been changed to Unity.

Just to be sure, can you post a screenshot?

No.....still running 10.04: not a Unity issue at all.  The normal 10.04 screen comes up, but LS of top menu bar is not there.  Cannot post screenshot since all I can do is get the desktop up.

---

### Post by enkay009 on 2011-11-05
Okay, Update not upgrade. Got it.

You can try manually launching gnome-panels and checking if any error messages come up. These could provide some clues as to what the problem is.

Shift into a tty (ex. CTRL+ALT+F1), 
Type this in the terminal:
```
export DISPLAY=:0
gnome-panel --replace
```Then shift back and check if everything is back (either CTRL+ALT+F7 or CTRL+ALT+F8 ).

If this didn't work, check the error messages in your tty for clues.

---

### Post by Autodave on 2011-11-05
> **enkay009 said:**
> Okay, Update not upgrade. Got it.

You can try manually launching gnome-panels and checking if any error messages come up. These could provide some clues as to what the problem is.

Shift into a tty (ex. CTRL+ALT+F1), 
Type this in the terminal:
```
export DISPLAY=:0
gnome-panel --replace
```Then shift back and check if everything is back (either CTRL+ALT+F7 or CTRL+ALT+F8 ).

If this didn't work, check the error messages in your tty for clues.


Cannot get Applications, Files, or System to work.....they do not even appear until I click min the area where they are supposed to be.  Then they appear, but clicking on any one of them does nothing at all......usually just leaves mouse pointers everywhere I click.

---

### Post by enkay009 on 2011-11-05
Did you try what I suggested?
Do you get the same problem after doing that?
Are you running compiz?

---

### Post by IWantFroyo on 2011-11-05
Are you using any proprietary graphics drivers? Updating messes with these once in a while.

---

