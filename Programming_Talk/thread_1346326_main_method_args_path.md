---
title: "main method args path"
date: 2009-12-04
forum: Programming Talk
---

### Post by kumoshk on 2009-12-04
I have a program I've made and put in my executable path so that I can use it outside of its program directory. However, when I try to open a file with my program, it looks in the program directory for the file every time instead of where the file actually is. How do I change this? I use Vala, in case that helps.

There are so many programs that use the args without really using them that my searches haven't produced any real answers.

---

### Post by kumoshk on 2009-12-05
I've found a solution, although it requires GLib (so if you know one that doesn't feel free to mention it, still, for reference's sake):

Use GLib.Environment.get_current_dir() to get the rest of it. I would have noticed this earlier, but the script I was using to launch my program prevented this from working, somehow.

---

