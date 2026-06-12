---
title: "Eclipse and gedit...help pls"
date: 2010-09-13
forum: Programming Talk
---

### Post by neiro80 on 2010-09-13
Why by opening the file in Eclipse the file is opened in gedit.
 I tried to open the file in many ways such as File->Open or clicking on file in project tree, but any way the result was the same -> the file was opened by gedit.](*,)

---

### Post by r-senior on 2010-09-13
What type of file is it?

Have a poke around in Window -> Preferences -> General -> Editors and File Associations.

---

### Post by neiro80 on 2010-09-13
> **r-senior said:**
> What type of file is it?

Have a poke around in Window -> Preferences -> General -> Editors and File Associations.

Any files. *.c , *.h

I run eclipse. then File->Open->test.c and at this time automatically starting gedit. why this happens?

---

### Post by r-senior on 2010-09-13
Probably because Eclipse has no plugin for C/C++ syntax highlighting so it gives a system editor.

Go to Help -> Install New Software, then click on "Galileo update site" (depending on which version of Eclipse you are using). You should find C/C++ development tools. If you install that plugin, you should be able to open *.c and *.h files in Eclipse.

See attached screenshot.

---

### Post by neiro80 on 2010-09-14
Very big Thank!!!!!!

---

### Post by bnuytten on 2010-10-19
I recently upgraded from ubuntu 10.04 to 10.10. Eclipse now opens *.c/*.h files in gedit.

Removing (purge) eclipse didn't solve it. Removing the C/C++ plugin and reinstalling it didn't solve it.
I have been looking in Window > Preferences > General > Editors > Restore Defaults + Apply.
Dragging & dropping a *.c/*.h file from the project explorer into the area where eclipse normally opens files works, but there's no syntax highlighting :(.

When I right click a file in the project explorer and choose "open with" > "ant editor" eclipse opens the file, but again no syntax highlighting.

---

### Post by bnuytten on 2010-10-30
Today I found out that this was a workspace specific setting. Opening another workspace on the same machine didn't have the problem. So I dissed my old workspace and created a new one.

If someone want to find out: it's probably a setting in the .metadata folder of the workspace. Good luck finding it :-)

---

### Post by bnuytten on 2010-10-30
close eclipse
cd ~
mv .eclipse .eclipse-20101031
install CDT as described previously in this thread (restart eclipse)

This is quite a blunt way 'cause it gets rid of all your settings... Works for me though.

---

