---
title: "[Python] Opening a PDF document with default app"
date: 2008-12-05
forum: Programming Talk
---

### Post by dodle on 2008-12-05
In windows I can use the following code to open a .pdf file in the default viewer:[PHP]os.filestart("pathtofile.pdf")[/PHP]What would the equivalent of this be on a unix systems?

Edit:  I figured out I can do the following on an Ubuntu machine:[PHP]os.system("acroread pathtofile.pdf")[/PHP]This opens the document in Acrobat Reader.  But what if a computer uses something other than Acrobat to read pdf documents.  How can I set it up to use the default application to open?

---

### Post by unutbu on 2008-12-05
[PHP]#!/usr/bin/env python

import os
# os.system('/usr/bin/xdg-open /home/user/Examples/case_Contact.pdf')
os.system('/usr/bin/gnome-open /home/usre/Examples/case_Contact.pdf')
[/PHP]
You can use xdg-open or gnome-open. Both work on Ubuntu. I'm guessing gnome-open might not work on KDE systems, but that xdg-open might. 

These commands can open many other kinds of files too.

---

### Post by dodle on 2008-12-05
> **unutbu said:**
> [PHP]#!/usr/bin/env python

import os
# os.system('/usr/bin/xdg-open /home/user/Examples/case_Contact.pdf')
os.system('/usr/bin/gnome-open /home/usre/Examples/case_Contact.pdf')
[/PHP]


Thanks, that works well. Will this work on most Linux machines?

---

### Post by unutbu on 2008-12-05
gnome-open should be available on all GNOME-based systems.
I did a google search on "xdg-open DISTRO" and from the hits returned I'm guessing that xdg-open is available on Fedora, Mandriva, SUSE, Gentoo, Mandrake, Debian. I don't know if it is a default or extra package though...

---

### Post by dodle on 2008-12-05
That's good enough for me.  Thanks again.  Another question though:  I'm getting an error:```
Unable to run the command specified. The file or folder file:///home/user/Instructions.pdf does not exist.
```This only pops up if I double click the file.  If I use the terminal it works just fine.  The file is are the following: ```
/home/user/Desktop/test.py
/home/user/Desktop/Instructions.pdf
```So why would it try to look in /home/user instead of /home/user/Desktop?  Here is test.py:[PHP]#!/usr/bin/env python

# Testing

import os, sys

if os.name == "nt":
    os.filestart("Instructions.pdf")
elif os.name == "posix":
    os.system("/usr/bin/xdg-open Instructions.pdf")[/PHP]Edit: In case I forgot to mention, this error occurs in Ubuntu.  It works fine on Windows.

---

### Post by unutbu on 2008-12-06
I haven't been able to reproduce the behavior you described.
(Double-clicking through nautilus and running from the terminal both work for me.)

To debug this, perhaps make a second script called test2.py:

[PHP]#!/usr/bin/env python
import os
print os.getcwd()
raw_input()[/PHP]

Move the file to ~/Desktop/test2.py.

Double-click it. Does it print /home/user/Desktop ? That is what I'm getting.

If you are not getting "/home/user/Desktop", then I suspect the problem lies in some nautilus configuration option. Unfortunately, I don't know much about nautilus configuration.

If you see "/home/user/Desktop" but still get the error message when you double-click test.py, then I'm really flummoxed.

Whatever it prints is the current working directory. It is the directory that python should be searching for Instructions.pdf.

Finally, you may consider this an unsavory hack, but... if you know where the script is going to be installed, you can
set the current working directory like this:
[PHP]
os.chdir(os.path.join(os.path.expanduser('~'),'Desktop'))[/PHP]

---

### Post by WitchCraft on 2008-12-06
just use open instead of gnome-open, then it works in non-gnome systems, too!

---

