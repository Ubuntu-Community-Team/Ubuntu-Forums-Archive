---
title: "Glade3.6, GtkBuilder"
date: 2009-03-20
forum: Programming Talk
---

### Post by Sprut1 on 2009-03-20
I just recently downloaded Glade 3.6 and started messing around with it. Since I know can compile the gui using GtkBuilder I thought I'd give that a shot, but when I try to start the application from Python I get this message:

```

glib.GError: /[..]/userinterface.glade: required gtk+ version 2.16, current version is 2.14

```

So obviously I have gtk+ version 2.14. In glade 3 I select to compile for version 2.16 as I get some "deprecated widgets" and version errors if I try to use 2.14. My question is if updating gtk+ will lead to any problems elsewhere in my system, and why it isn't already installed? Which packages are we actually talking about here? Sorry for being so ignorant :)

---

### Post by days_of_ruin on 2009-03-20
> **Sprut1 said:**
> I just recently downloaded Glade 3.6 and started messing around with it. Since I know can compile the gui using GtkBuilder I thought I'd give that a shot, but when I try to start the application from Python I get this message:

```

glib.GError: /[..]/userinterface.glade: required gtk+ version 2.16, current version is 2.14

```

So obviously I have gtk+ version 2.14. In glade 3 I select to compile for version 2.16 as I get some "deprecated widgets" and version errors if I try to use 2.14. My question is if updating gtk+ will lead to any problems elsewhere in my system, and why it isn't already installed? Which packages are we actually talking about here? Sorry for being so ignorant :)

ubuntu 9.04 comes out in a month and I assume it will have gtk 2.16.
Its probably safest to wait till then.

---

### Post by Sprut1 on 2009-03-20
> **days_of_ruin said:**
> ubuntu 9.04 comes out in a month and I assume it will have gtk 2.16.
Its probably safest to wait till then.

My thoughts exactly, couldn't find any information that verifies it though. I'll wait! Thanks!

---

