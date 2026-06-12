---
title: "How to remove pictures from menus"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by Never Age on 2012-01-09
A month or two ago I noticed that these little icons started showing up in various menus and stuff. Places like the wrench menu in chrome and when right-clicking. They appear system wide in all programs, and seem to generally use a system theme no matter which program.

Examples:
[IMG]http://img41.imageshack.us/img41/8347/rightclickicons.png[/IMG]
[IMG]http://desmond.imageshack.us/Himg268/scaled.php?server=268&filename=wrenchmenuicons.png&res=medium[/IMG]

They've really started to bug me and I'd like them gone. It was a long time ago when it first started, so I don't remember what settings I was messing with and don't see any way to remove them with compiz or my system settings.

---

### Post by lechien73 on 2012-01-09
Hi & welcome to the forums,

To change this, open a terminal window and type:

```
dconf-editor
```

Then navigate to **org -> gnome -> desktop -> interface**

Uncheck the **menus-have-icons** box.

---

### Post by Never Age on 2012-01-09
> **lechien73 said:**
> Hi & welcome to the forums,

To change this, open a terminal window and type:

```
dconf-editor
```

Then navigate to **org -> gnome -> desktop -> interface**

Uncheck the **menus-have-icons** box.
Awesome, thanks ;)

---

