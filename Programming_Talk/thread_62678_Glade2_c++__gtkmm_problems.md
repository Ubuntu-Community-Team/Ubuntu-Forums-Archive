---
title: "Glade2 c++ / gtkmm problems"
date: 2005-09-05
forum: Programming Talk
---

### Post by Luggy on 2005-09-05
I've been getting this problem when I try and get glade2 to generate the files for my GUI in c++.

```
Error running glade-- to generate the C++ source code.
Check that you have glade-- installed and that it is in your PATH.
Then try running 'glade-- <project_file.glade>' in a terminal.
``` 

I've searched through many threads and i've installed:
[list]
[*]libglade2-dev
[*]glade-common-2
[*]glade-gnome-2
[*]libglade2-0
[*]libglade2-dev
[*]libglademm2.4-1
[*]libglademm2.4-dev
[/list]

but it still gives me the error.
Someone in another thread was mentioning installing glademm but I couldn't find it in the responsitories.

Any suggestions?

---

### Post by tehwa on 2005-09-06
If you haven't already found the solution, It might be libgtkmm.

---

### Post by Luggy on 2005-09-06
[QUOTE=tehwa]If you haven't already found the solution, It might be libgtkmm.[/QUOTE]

Hmm I tried that and it still didn't work.

---

### Post by tehwa on 2005-09-06
Actually, don't listen to me, I'm having the same library problems, see here:

[http://ubuntuforums.org/showthread.php?t=62622](http://ubuntuforums.org/showthread.php?t=62622)

It's like God doesn't want me to compile anything. Perhaps he's got a point.

Does your Glade setup work with C source as opposed to C++?

---

### Post by Luggy on 2005-09-06
[QUOTE=tehwa]Does your Glade setup work with C source as opposed to C++?[/QUOTE]

Everything works fine for me when I try and generate my files in C.

---

### Post by Shen on 2005-09-08
[QUOTE=Luggy]Everything works fine for me when I try and generate my files in C.[/QUOTE]
 Try this thread: [http://www.ubuntuforums.org/showthread.php?t=61221](http://www.ubuntuforums.org/showthread.php?t=61221)

---

