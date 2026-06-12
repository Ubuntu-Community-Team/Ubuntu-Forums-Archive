---
title: "[SOLVED] Tiny tiny system font size"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by jivabill on 2008-11-01
I am still stuck on the system font size.  It is so small I can't read the menus or application windows without reading glasses.  That makes Xubuntu not very useful for me.

I have tried 4 or 5 suggested remedies using various command line capers to no avail.  Most of them so far all apply to earlier versions of Xubuntu and when I try to apply them to 8.04  I find that they are already there or that the whole section that I am to modify is not there in 8.04.

So if anyone has and idea how to change the system font size I would be happy to hear it.

---

### Post by chrisme52 on 2008-11-27
if its solved whats the solution?

---

### Post by jivabill on 2008-11-27
My apologies for not posting the solution that I found.  30 lashes with a wet noodle.

I found the work a smart person and applied it and IT WORKED!

Here is the fix:

You need to edit /etc/X11/Xresources/x11-common

Add this line to the file:  Xft.dpi: 96

Be sure to leave a blank line after it at the end of the file.
Be aware that you can use a different number, like 108 or something bigger than 96 if you want the default font size bigger yet.

Worked for me, just when I was about to give up.

Regards
Bill

---

### Post by jaroodude on 2008-11-29
Thanks for the head's up. This small modification to the file has solved that crazy tiny font that was being used throughout the system. Especially in FireFox. 

Easy, no muss, no fuss, that is after I learned that Xubuntu discourages the use of root, which of course you must use to change the file :-) I did a search on root user xubuntu and quickly learned how to open the file in a root (sudo -i) terminal. Then I was able to open the mousepad program from a terminal and navigate to the file location, open it and save the changes you suggested. So far it has great for me. 

Thanks again,

Jared

---

### Post by jivabill on 2008-11-29
Hi Jared, Bill here again.  Sorry I forgot to mention that root stuff.  Yes, found the same problem.  I remember the way I got around it was I did a gksudo nautilus to open a root file browser and went and looked at the file.  Seems to me, not remember totally, that I did have to open a Terminal and get into root before I could add the line.  Glad to hear it worked OK.

Sure was a happy find for me, that small font was driving me nuts :-)
b

---

### Post by Jaxco on 2009-10-31
> **jivabill said:**
> My apologies for not posting the solution that I found.  30 lashes with a wet noodle.

I found the work a smart person and applied it and IT WORKED!

Here is the fix:

You need to edit /etc/X11/Xresources/x11-common

Add this line to the file:  Xft.dpi: 96

Be sure to leave a blank line after it at the end of the file.
Be aware that you can use a different number, like 108 or something bigger than 96 if you want the default font size bigger yet.

Worked for me, just when I was about to give up.

Regards
Bill

ALL XUBUNTU users need this stickied!

---

