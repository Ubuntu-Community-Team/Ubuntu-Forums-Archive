---
title: "How to fill Treeviews from GLADE-3 gui NOT coding ??"
date: 2007-07-06
forum: Programming Talk
---

### Post by rksk16it on 2007-07-06
Hello guys !
I would like to ask anyone who has used glade-3 to build nice gui(s)...that...is there any way to fill treeviews from the gui of glade-3 ?

I am not asking how to do that from the code...i have already done so using C++, Java and Python...and the interface is same....create models containing modelcolumns...and then assigning them to treeview...blah blah

Though it is not difficult to do that through code (IT IS a bit tricky first time !!) but what i need is to do that stuff right from the glade-3. 

Though i am not able to find an answer yet...but in glade-3 (v3.3.1) when i create Treeview and lookup its properties there is an option "Treeview model" which has a button "..." beside that (like the one beside signal-handler option), and on clicking that button it asks to chhose a "treemodel" **from the project**...i have no idea what this "from the project" means, if it means i have to include the model in the project then how is it done ??

Thanks in advance :)

---

### Post by duff on 2007-07-06
You can't.  Maybe in the future with GtkBuilder.

 [http://blogs.gnome.org/johan/2007/06/15/gtkbuilder-has-landed/](http://blogs.gnome.org/johan/2007/06/15/gtkbuilder-has-landed/)

---

