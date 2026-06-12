---
title: "GTK+ list selector"
date: 2010-07-12
forum: Programming Talk
---

### Post by xefix on 2010-07-12
I am trying to make a window in my GUI that will allow the user to choose from a list of options. Ideally, I would like this to look like a file/directory chooser, except that this list will be populated from a linked list of strings within my code. This linked list will change, but the list selector within the window only needs to be updated every time the window itself is brought up (by clicking a button from the home screen). Can anyone recommend the best widgets to use for this task? And also, do you recommend that I create and destroy the widget from within my code every time it is opened/closed, or create it in Glade and then simply hide/show it when needed?

---

### Post by PaulM1985 on 2010-07-12
I think you are after a gtk tree view.  If it is going to contain alot of information which remains the I would use show/hide.  Otherwise, if there isn't much in it or the information changes I would probably create and destroy them.

(Google gtk treeview and there seem to be plenty of examples)

Paul

---

### Post by StephenF on 2010-07-12
> **xefix said:**
> Can anyone recommend the best widgets to use for this task? And also, do you recommend that I create and destroy the widget from within my code every time it is opened/closed, or hide/show it when needed?
If it's a lot of options:
TreeView + ListStore wrapped in ScrolledWindow inside a Dialog.

If its a single widget show + hide works well but consider making it at the moment it is first needed. When you get a lot of things like that it increases the application start-up time.

---

### Post by xefix on 2010-07-12
Thanks for the advice. I ended up using a tree view as suggested. I followed [http://tadeboro.blogspot.com/2009/04/creatin-gtktreeview-with-glade-3.html](http://tadeboro.blogspot.com/2009/04/creatin-gtktreeview-with-glade-3.html) to add tree view to my application, and found the tutorial to be outstanding.

---

