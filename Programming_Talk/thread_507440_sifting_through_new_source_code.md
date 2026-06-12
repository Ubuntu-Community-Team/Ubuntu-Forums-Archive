---
title: "sifting through new source code"
date: 2007-07-23
forum: Programming Talk
---

### Post by dawdler on 2007-07-23
Just wanted to know how ppl in the Ubuntu community go through new source code particularly in C/C++?

Do you use an IDE or do you use an editor with a lot of "grep"ping and "find"ing?  My difficulty is locating method declarations and definitions.

MS Visual Studio and MonoDevelop is nice b/c you open up the project and right clicking on a function will take you to its definition.

---

### Post by Mr. C. on 2007-07-23
vi + ctags.

---

### Post by hod139 on 2007-07-23
Many times I'll run doxygen on the source, and use the html output to browse the code.

---

### Post by dawdler on 2007-07-23
Thanks for the replies!  I will check out both tools: Doxygen to browse code and vim+ctags for code dissection.  I'm so glad I don't have to import the source into an IDE project nor painstakingly grep/search through the source.

I have to admit, I am not comfortable with vi/vim and hope a similar plugin will become available for gedit.

---

