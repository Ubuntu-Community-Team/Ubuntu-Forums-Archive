---
title: "shell command to set focus to a window"
date: 2010-11-05
forum: Programming Talk
---

### Post by hakermania on 2010-11-05
I know about xwit, but i need something pre-installed. Is there any available?

---

### Post by hakermania on 2010-11-05
xmctrl does this as well with the option -a <application name>
But as I mentioned before, I need something pre-installed, so to have fewer dependencies.

---

### Post by hakermania on 2010-11-06
*bump*

---

### Post by hakermania on 2010-11-07
*bump** ???

---

### Post by Simian Man on 2010-11-07
No way that I know of.

---

### Post by hakermania on 2010-11-07
Very helpful, thx, should I mark the thread now as solved? --_--

---

### Post by nvteighen on 2010-11-08
If you're coding in a language like C, C++, Python, etc., please use the GTK+ API (This is the C signature): gtk_window_set_focus(GtkWindow *, GtkWidget *)

If you're writing a shell script, I think the only chance you have is to install any of those you mentioned. Shell scripting can't access GTK+ directly so you'll need to install a program to do it.

---

### Post by Simian Man on 2010-11-08
> **nvteighen said:**
> If you're coding in a language like C, C++, Python, etc., please use the GTK+ API (This is the C signature): gtk_window_set_focus(GtkWindow *, GtkWidget *)

Also keep in mind that will only work for windows created by GTK+.

---

### Post by nvteighen on 2010-11-08
> **Simian Man said:**
> Also keep in mind that will only work for windows created by GTK+.

Ugh... somehow I thought this was GTK+-specific :P

Well, if it's Qt, use whatever Qt offers to do this. The general criterion is: if there's an API, use it :)

---

### Post by hakermania on 2010-11-11
It is a Qt app actually but I haven't found something specific about setFocus()... I am probably searching in wrong section :/

---

