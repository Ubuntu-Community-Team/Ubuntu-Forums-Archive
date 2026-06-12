---
title: "making a windows executable"
date: 2008-01-27
forum: Programming Talk
---

### Post by nbo10 on 2008-01-27
Hi all,
I have a c++ app that is really useful. My boss found out about the program and wants a copy. The only problem is that he uses windows. How do I make a windows executable file for him? Thanks

---

### Post by Acglaphotis on 2008-01-27
Use mingw. It is in the repo. It's a cross-compiler for windows. Oh and btw use this options to reduce the size of the executable, or it will end up like 30 times its actual size (no kidding):

[php]

strip --strip-all SOMEBINARY.exe 

[/php]

---

### Post by Xealot on 2008-01-27
> **nbo10 said:**
> Hi all,
I have a c++ app that is really useful. My boss found out about the program and wants a copy. The only problem is that he uses windows. How do I make a windows executable file for him? Thanks

Hello!

First, you will have to find out if the code you are want to re-compile uses any OS specific libraries, such as a GUI.
If it does, it wont be so easy for you.

But assuming the code is good to go for win compilation, a quick google search brought this link to me:
[http://ubuntuforums.org/showthread.php?t=626932]("http://ubuntuforums.org/showthread.php?t=626932")


Hope thats to any help
 - X

---

### Post by nbo10 on 2008-01-27
Thanks that's what I needed.

---

