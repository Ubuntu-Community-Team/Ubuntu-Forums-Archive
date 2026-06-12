---
title: "Right Click for New Document"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-05-27
Hello All,
When I right click on the desktop, I get several choices, one of which is: New Document.  Following the link leads to only: Empty Document.
Questions:
1. Is "Empty Document" a text only document with no embedded formatting?
2. Is it possible to have more choices; presentation, spreadsheet, word processing, etc...

Ubuntu 13.04

Thanks for the help

---

### Post by deadflowr on 2013-05-27
You'd have to do some editing on the menus configuration file(s) and switch the link of new document from gedit to libreoffice.
Never thought of doing that, so no clue on what files would need to be edited.:D

---

### Post by Dennis N on 2013-05-27
The "empty document" (Lubuntu says "blank file") in this case is set to be a text document opened with the default text editor. In Lubuntu, that is Leafpad, in Ubuntu I assume it is still gedit (or whatever name it might have now). I don't think you can change the "blank file" to be a type other than text - at least I haven't heard of that possibility.

You can change the application to use for text documents - right click on the empty (or any) text document icon, and look at properties. Change the application shown in "open with..." (Libre Office Writer is one of the choices on my system)

After that, double clicking on a text document should open it in the chosen applicaion.

---

### Post by mc4man on 2013-05-27
> **GUZZLR said:**
> Hello All,
When I right click on the desktop, I get several choices, one of which is: New Document.  Following the link leads to only: Empty Document.
Questions:
1. Is "Empty Document" a text only document with no embedded formatting?
2. Is it possible to have more choices; presentation, spreadsheet, word processing, etc...

Ubuntu 13.04

Thanks for the help
Anything you place in the Templates folder will show in that context menu
(extensions aren't necessary, you'll get "Untitled <name>" so usually keep it simple like spread or spreadsheet, ect.

---

### Post by newb85 on 2013-05-27
Here's a thread on the subject that, while old and closed, is still useful.

[http://ubuntuforums.org/showthread.php?t=241677](http://ubuntuforums.org/showthread.php?t=241677)

Apparently, stalefries' website is coming down, but you can still run the wget command in post #1 and then extract the archive to your Templates folder.

---

### Post by GUZZLR on 2013-05-27
```
Here's a thread on the subject that, while old and closed, is still useful.

[http://ubuntuforums.org/showthread.php?t=241677](http://ubuntuforums.org/showthread.php?t=241677)

Apparently, stalefries' website is coming down, but you can still run  the wget command in post #1 and then extract the archive to your  Templates folder.
```

Wow...That was easy!  Really nice too.  Too bad it doesn't offer C++ script, like it offers Python, or does it and I missed it?

---

### Post by newb85 on 2013-05-27
> **GUZZLR said:**
> Too bad it doesn't offer C++ script, like it offers Python, or does it and I missed it?

Nope.  But really, it should be a piece of cake to create your own.

---

