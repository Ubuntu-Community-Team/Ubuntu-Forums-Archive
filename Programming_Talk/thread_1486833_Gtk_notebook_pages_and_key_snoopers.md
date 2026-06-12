---
title: "Gtk notebook pages and key snoopers"
date: 2010-05-18
forum: Programming Talk
---

### Post by bcz on 2010-05-18
I am trying to use GtkNotebook and have the following problem:

I have several tabbed pages.  One pages uses a keyboard snooper function.

If the user switches to another page, then input goes to the snooper function to the previous page.

I can user the switch-page signal to remove the previous snooper, but how do I reactivate it when I switch back to the previous page.

I guess my C programming is not up to saving and restoring the key snooper addresses in the data structure I setup for control information for each page.

Any help or documentation pointers appreciated

Rgds Bill C

---

### Post by bcz on 2011-05-01
Might as well close this, so here is current code

```
typedef struct nbPgTag{// MIPS notebookPage control
        struct nbPgTag *next;
        guint16 tag;
        gint pgNo;
        GtkWidget *sWndw,*vbox,*rowFixed[maxLix],*focus,*reply;
        GtkKeySnoopFunc snoopRtn;
        guint snooper;
        rowData *rowCtrlHead[maxLix];
        char *(*func)();
        }nbPgCtrl;
```

(func is a function returning a string)

---

