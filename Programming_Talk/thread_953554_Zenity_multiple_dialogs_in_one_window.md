---
title: "Zenity multiple dialogs in one window?"
date: 2008-10-20
forum: Programming Talk
---

### Post by diafygi on 2008-10-20
Hey all,

I am just getting started in shell scripting, and I'm trying to understand zenity more. Does anyone know if it is possible to generate multiple dialogs in one window?

For example, I would like to create a window that has two text entry dialogs in it. However, all I can get zenity to currently do is create two separate windows, each with a text entry.

If zenity can't combine dialogs to a single window, what is the next step? Python?

---

### Post by geirha on 2008-10-20
I'm afraid zenity isn't that advanced, so I guess you'll need to program the GUI yourself. Python should be one of the easier choices for that.

---

### Post by slavik on 2008-10-20
> **geirha said:**
> I'm afraid zenity isn't that advanced, so I guess you'll need to program the GUI yourself. Python should be one of the easier choices for that.
along with Perl and Ruby. :)

---

### Post by roccivic on 2008-10-20
If you have C background, then GTK+.
Which is what zenity is written in by the way.

Rouslan

---

### Post by dtmilano on 2008-10-20
Try [autoglade]("http://autoglade.sf.net") and you will be able to design your dialogs with glade and obtain values back to your script.

---

### Post by diafygi on 2008-10-22
> **dtmilano said:**
> Try [autoglade]("http://autoglade.sf.net") and you will be able to design your dialogs with glade and obtain values back to your script.

Thanks all for your suggestions. It looks like it will be quite a bit more work to consolidate a multi-step gui script to a single-step.

---

