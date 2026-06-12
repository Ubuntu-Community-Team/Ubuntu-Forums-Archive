---
title: "How to convert Windows text files to Unix format"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-07-12
I have a text file that comes from Windows, which means that is has the Windows-standard line endings.

The Text Editor (gedit) can read it perfectly well.

The program that needs to read the file, however, requires that it adhere to the Unix standard.

How do I convert plain text files from Windows format to Unix?

(I managed to do achieve this by going to a Windows computer and using "Notepad++", a free text editor with this conversion facility. But, for future use, I'd like to know how to do this in Unix.)

---

### Post by TSS on 2008-07-12
For one of my CS classes, I used the 'dos2unix' command to convert all of the Windows newlines into UNIX newlines. I'm not sure if that's the only thing you have to do, but hopefully that helps.

---

### Post by tamoneya on 2008-07-12
use sysutils.  Here is a thread detailing it:

[http://ubuntuforums.org/showthread.php?t=33886](http://ubuntuforums.org/showthread.php?t=33886)

---

### Post by Paddy Landau on 2008-07-12
Thanks for the responses.

It looks as though "flip" is the easiest and safest option to use. I've installed it, and I will test it.

---

