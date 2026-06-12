---
title: "Getting back from a method in gcc..."
date: 2005-11-23
forum: Programming Talk
---

### Post by YourSurrogateGod on 2005-11-23
Ok, I've read the man helper pages in gdb, but can't seem to find this feature that works well (which makes it difficult for me to switch over to Linux development completely when I know that it works well in .NET :( .) What I'm trying to do is be able to return back from an existing method. For example, you're doing C++ development and you're using STL, you go through a linked list (accidentally) and you're in the header list file. In .NET all you have to do is press Shift+F11 and you can step out of the method, but how do you do that in gdb? I can't find that feature in that debugger. Anyone know what it is?

---

### Post by Roptaty on 2005-11-23
I think the command you are looking for is: finish

---

### Post by YourSurrogateGod on 2005-11-26
[QUOTE=Roptaty]I think the command you are looking for is: finish[/QUOTE]
Ya, that did the trick, thanks. One more question, how do you set a break point in a specific file?

---

### Post by Roptaty on 2005-11-26
b filename:linenumber

---

### Post by YourSurrogateGod on 2005-11-26
[QUOTE=Roptaty]b filename:linenumber[/QUOTE]
Thanks again.

---

