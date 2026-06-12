---
title: "File extension"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Niloc on 2008-09-24
Windows recognises file by their extension and then knows which application to run for that file.
Word for '.doc' etc, how do I make Ubuntu do the same?

---

### Post by NoReflex on 2008-09-24
I think it already does that. If you have OpenOffice installed it will automatically open doc, xls, ppt files.
Or you can right click a file , go to Properties -> Open With and there you can choose your applications.

Best wishes
NoReflex

---

### Post by Niloc on 2008-09-24
Umm, not exactly, I am trying to run a program I wrote myself, looks like I have to modify the code to tell it to get the name of the file from the command line...

---

### Post by Orange_and_Green on 2008-09-24
Hello Niloc.:)

I'm sorry, I'm afraid I didn't quite understand what your problem is. Could you please be a little more specific about what you are actually trying to do?

---

### Post by lisati on 2008-09-24
I'm not sure about other versions, but 7.04 has an option where you right-click on the file, choose "open with other application", and then click on "choose custom command"

EDIT: I read somewhere in these forums that Ubuntu & Linux doesn't rely on the file-type/extension nearly as much as Windows, but relies more on permissions and content.

---

### Post by bab1 on 2008-09-24
Well almost.  If you are running a script, then you need to make it executable with the chmod command.  See ```
man chmod
```

The same with binaries, and most folk want to associate it via the GUI interface as in: right click on the file>>open with.

Some of this functionality is built in to Gnome/Nautilus.  But I also have added apps (like PDF readers) and had to do the right click thing.

EDIT: The file association is a Gnome thing,** not** a Linux thing.  Also in Perl you can specify the interpreter to use on the first line of the script.

---

### Post by jemate18 on 2008-09-24
if you want your script to be executable

type
```
chmod 750 yourscript
```

7 = read write execute (for user/owner)
5 = read execute (for group)
0 = none for (others)

---

### Post by kostkon on 2008-09-24
> **Niloc said:**
> Umm, not exactly, I am trying to run a program I wrote myself, looks like I have to modify the code to tell it to get the name of the file from the command line...
Right-click on the file, then from the menu select *Properties*, and in the *Permissions* tab select the *Allow executing file as program* to make it executable.

---

