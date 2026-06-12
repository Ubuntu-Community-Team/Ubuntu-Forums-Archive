---
title: "Saving an xml file as root"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by pi.phage on 2008-06-16
I have a xml file that I need to save in usr->share->* and I think I need to be root to save it. when I try, text editor tells me I don't have the permissions I need to save it. How would I save it without losing changes?

---

### Post by fatality_uk on 2008-06-16
How have you opened it?
You could open it with > gksudo gedit and then save it from within gedit.

---

### Post by pi.phage on 2008-06-16
I, a Mac user, went through the gui to find it in file browser. When i told it to open in text editor, it opened in gedit. (???) From gedit, it won't let me save. I don't think opening it from the command line would help.

---

### Post by fatality_uk on 2008-06-16
If it's in one of Ubuntu's "protected" directories, you can't just open it from the broswer. Run the command and it will allow you to edit the xml file.

Run it, then use the File-Open and navigate the file system till you reach the file you want to edit.

Just be sure you know what it is your editing ;)

---

