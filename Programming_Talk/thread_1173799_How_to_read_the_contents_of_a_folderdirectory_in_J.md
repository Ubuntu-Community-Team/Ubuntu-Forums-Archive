---
title: "How to read the contents of a folder/directory in Java?"
date: 2009-05-30
forum: Programming Talk
---

### Post by Gucko on 2009-05-30
hi guys, I need a way to let my program open a folder(directory) and read *all* the files in it i.e like scanning a folder. Is there any class/way to do that? I hope you understood my question.

---

### Post by PaulM1985 on 2009-05-30
I think if you create a File object eg:
File myDirectory = new File("/home/me");

You can test it to see if it is a directory using:

myDirectory.isDirectory();

which should return true if it is a directory, then use:

myDirectory.listFiles();

which returns an array of File objects.  Check out the File class [http://java.sun.com/j2se/1.5.0/docs/api/java/io/File.html](http://java.sun.com/j2se/1.5.0/docs/api/java/io/File.html).  For more info on what you can do with it.

Paul

---

### Post by Gucko on 2009-05-30
Thanks man this is very helpful.

---

