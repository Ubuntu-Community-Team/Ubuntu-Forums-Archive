---
title: "Help changing MIME type"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by chickendude on 2008-08-28
The past few weeks i have been experiencing some weird issues that seem to have randomly affected a few files. One file is a .exe file that used to run with Wine, but now to get it to do that i have to do a couple workarounds. Another is a file with it's ending as .asm. I want the MIME Type for this file to be text/x-z80asmsrc, but currently it is text/x-csrc.
The error i get is:
> The filename "filename.asm" indicates that this file is of type "Assembly source code". The contents of the file indicate that the file is of type "C source code". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "C source code", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.
Now, if i rename the file, i can then double click it and it will open, however the MIME Type is still listed as text/x-csrc. I have tried saving it as a new .asm file, and when i switch to Nautilus after doing so the MIME Type says text/x-z80asmsrc for a brief second then switches back to x-csrc. Also, after renaming it i am able to open it by double clicking until i restart the computer, at which point the aforementioned error resurfaces.

I can't say for sure, but it seems like a good possibility, but i recently installed gcc and g++ and that is around the time that i started having all this trouble. Maybe it is related? Especially since it is recognized as a C source code and not Assembly source code like my other assembly files..

Anyway, is there a way to manually change it back to text/x-z80asmsrc? (I would like ALL .asm files to be recognized as "Assembly source code").

Thanks!

EDIT: I think i have figured out what is causing it to switch MIME Types: all .asm files are fine unless they have a "#include" directive (maybe others, but this is the only one i have tested). Also, i made a few copies of the same program, and after reloading the folder in Nautilus, all the file types are displayed as Assembly source code, but the second i put the selection bar over them they switch back to C source code. I'm not sure if that means anything or not, but i still am not sure how to fix it.

EDIT2: Also, for the .exe file, it's extension has changed from application/x-executable to application/x-ms-dos-executable.

---

### Post by swoll1980 on 2008-08-28
You can right click a file go to properties then open with to change the association. I don't know if that will help you.

---

### Post by chickendude on 2008-08-28
Thanks, i've already tried that, but it doesn't seem to solve my problems. Although, despite listing the incorrect MIME type (or one i don't want), it does open with the program that i want it to.

---

### Post by swoll1980 on 2008-08-28
instead were it gives you programs you don't want, click browse then go to /usr/bin/"the program you want to open the file with" and that should work I used that method to open torrents with deluge in stead of transmission

---

### Post by chickendude on 2008-09-01
Well, i already have selected the program that i want to load the file, the #include statement is just causing Nautilus to recognize it as a C file (i believe).

---

### Post by chickendude on 2008-09-08
Does anyone have any other ideas?

---

