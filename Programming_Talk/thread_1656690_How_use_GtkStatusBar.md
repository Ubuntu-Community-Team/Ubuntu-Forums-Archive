---
title: "How use GtkStatusBar ?"
date: 2010-12-31
forum: Programming Talk
---

### Post by worksofcraft on 2010-12-31
I want to add a status bar on my app with a message telling the user what is going on, but also showing status of chosen settings... like in my case to say whether we have Unicode Bidi algorithm enabled or disabled, and whether we are operating in Right to Left or Left to Right display mode...

... anyway there is this GtkStatusBar widget in the Gtk and documentation says it maintains a stack of messages.
I don't see how to use it because I want to have multiple status indicators and the application progresses from one thing to the next without working like a stack at all :confused:

So I'm wondering if I completely messed up on understanding what a status bar actually is for? :shock:

---

### Post by nitro_n2o on 2010-12-31
will this help? [http://www.koders.com/cpp/fid50A4D7569A6B478BF663BF7649592A5105FD582D.aspx?s=gtkstatusbar#L879](http://www.koders.com/cpp/fid50A4D7569A6B478BF663BF7649592A5105FD582D.aspx?s=gtkstatusbar#L879)

---

### Post by worksofcraft on 2010-12-31
> **nitro_n2o said:**
> will this help? [http://www.koders.com/cpp/fid50A4D7569A6B478BF663BF7649592A5105FD582D.aspx?s=gtkstatusbar#L879](http://www.koders.com/cpp/fid50A4D7569A6B478BF663BF7649592A5105FD582D.aspx?s=gtkstatusbar#L879)

Thanks, yes that looks like a very useful website :)

however IDK how to compile it so I tried...
```

gcc testgtk.c `pkg-config --cflags --libs gtk+-2.0 gmodule-2.0 gtkmm-2.4`

```

but it doesn't seem to know where to look for the header files so perhaps it needs some other options from pkg-config or maybe a different version...

Meh eventually I patched up the various paths and Google found the missing files... but it still won't compile:
```


testgtk.c: In function &#8216;create_toolbar&#8217;:
testgtk.c:716: error: too many arguments to function &#8216;gtk_toolbar_new&#8217;
testgtk.c: In function &#8216;make_toolbar&#8217;:
testgtk.c:816: error: too many arguments to function &#8216;gtk_toolbar_new&#8217;
testgtk.c: In function &#8216;statusbar_dump_stack&#8217;:
testgtk.c:957: error: &#8216;GtkStatusbarMsg&#8217; undeclared (first use in this function)
testgtk.c:957: error: (Each undeclared identifier is reported only once
testgtk.c:957: error: for each function it appears in.)
testgtk.c:957: error: &#8216;msg&#8217; undeclared (first use in this function)
testgtk.c: At top level:
testgtk.c:1074: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GtkTree&#8217;
testgtk.c: In function &#8216;cb_add_new_item&#8217;:
testgtk.c:1083: error: &#8216;tree&#8217; undeclared (first use in this function)
testgtk.c:1097: warning: assignment makes pointer from integer without a cast
testgtk.c:1102: warning: assignment makes pointer from integer without a cast
testgtk.c:1111: warning: assignment makes pointer from integer without a cast
testgtk.c: At top level:
testgtk.c:1119: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GtkTree&#8217;
testgtk.c: In function &#8216;cb_remove_item&#8217;:
testgtk.c:1124: error: &#8216;tree&#8217; undeclared (first use in this function)
testgtk.c: At top level:
testgtk.c:1141: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GtkTree&#8217;
testgtk.c: In function &#8216;cb_remove_subtree&#8217;:
testgtk.c:1144: error: &#8216;GtkTreeItem&#8217; undeclared (first use in this function)
testgtk.c:1144: error: &#8216;item&#8217; undeclared (first use in this function)
testgtk.c:1146: error: &#8216;tree&#8217; undeclared (first use in this function)
testgtk.c: At top level:
testgtk.c:1157: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
testgtk.c: In function &#8216;create_subtree&#8217;:
testgtk.c:1207: warning: assignment makes pointer from integer without a cast
testgtk.c:1214: warning: assignment makes pointer from integer without a cast
testgtk.c: In function &#8216;create_tree_sample&#8217;:
testgtk.c:1273: warning: assignment makes pointer from integer without a cast
testgtk.c:1274: error: &#8216;cb_tree_changed&#8217; undeclared (first use in this function)
testgtk.c:1292: warning: assignment makes pointer from integer without a cast
testgtk.c: In function &#8216;create_menus&#8217;:
testgtk.c:2322: error: &#8216;GTK_ACCEL_SIGNAL_VISIBLE&#8217; undeclared (first use in this function)
testgtk.c: In function &#8216;spin_button_month_input_func&#8217;:
testgtk.c:2980: error: &#8216;INPUT_ERROR&#8217; undeclared (first use in this function)
testgtk.c: In function &#8216;spin_button_hex_input_func&#8217;:
testgtk.c:3011: warning: assignment discards qualifiers from pointer target type
testgtk.c:3015: error: &#8216;INPUT_ERROR&#8217; undeclared (first use in this function)
testgtk.c: In function &#8216;set_cursor&#8217;:
testgtk.c:3301: error: &#8216;GTK_TYPE_GDK_CURSOR_TYPE&#8217; undeclared (first use in this function)
testgtk.c: In function &#8216;create_list&#8217;:
testgtk.c:3551: warning: initialization from incompatible pointer type
testgtk.c:3552: warning: initialization from incompatible pointer type
testgtk.c:3553: warning: initialization from incompatible pointer type
testgtk.c:3554: warning: initialization from incompatible pointer type
testgtk.c: In function &#8216;insert_row_clist&#8217;:
testgtk.c:3951: error: &#8216;GtkStyle&#8217; has no member named &#8216;font&#8217;
testgtk.c:3952: error: &#8216;GtkStyle&#8217; has no member named &#8216;font&#8217;
testgtk.c: In function &#8216;create_clist&#8217;:
testgtk.c:4042: warning: initialization from incompatible pointer type
testgtk.c:4043: warning: initialization from incompatible pointer type
testgtk.c:4044: warning: initialization from incompatible pointer type
testgtk.c:4045: warning: initialization from incompatible pointer type
testgtk.c:4203: error: &#8216;GtkStyle&#8217; has no member named &#8216;font&#8217;
testgtk.c:4204: error: &#8216;GtkStyle&#8217; has no member named &#8216;font&#8217;
testgtk.c: In function &#8216;change_style&#8217;:
testgtk.c:4374: error: &#8216;GtkStyle&#8217; has no member named &#8216;font&#8217;
testgtk.c:4375: error: &#8216;GtkStyle&#8217; has no member named &#8216;font&#8217;
testgtk.c: In function &#8216;create_ctree&#8217;:
testgtk.c:4829: warning: initialization from incompatible pointer type
testgtk.c:4830: warning: initialization from incompatible pointer type
testgtk.c:4831: warning: initialization from incompatible pointer type
testgtk.c:4832: warning: initialization from incompatible pointer type
testgtk.c:4837: warning: initialization from incompatible pointer type
testgtk.c:4838: warning: initialization from incompatible pointer type
testgtk.c:4839: warning: initialization from incompatible pointer type
testgtk.c:4840: warning: initialization from incompatible pointer type
testgtk.c:4845: warning: initialization from incompatible pointer type
testgtk.c:4846: warning: initialization from incompatible pointer type
testgtk.c:4851: warning: initialization from incompatible pointer type
testgtk.c:4852: warning: initialization from incompatible pointer type
testgtk.c:4853: warning: initialization from incompatible pointer type
testgtk.c:4854: warning: initialization from incompatible pointer type
testgtk.c: In function &#8216;create_rulers&#8217;:
testgtk.c:5629: error: &#8216;GtkObject&#8217; has no member named &#8216;klass&#8217;
testgtk.c:5644: error: &#8216;GtkObject&#8217; has no member named &#8216;klass&#8217;
testgtk.c: At top level:
testgtk.c:5697: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GtkText&#8217;
testgtk.c: In function &#8216;text_insert_random&#8217;:
testgtk.c:5704: error: &#8216;text&#8217; undeclared (first use in this function)
testgtk.c: In function &#8216;create_text&#8217;:
testgtk.c:5760: warning: assignment makes pointer from integer without a cast
testgtk.c:5853: warning: passing argument 5 of &#8216;gtk_signal_connect_full&#8217; makes pointer from integer without a cast
/usr/include/gtk-2.0/gtk/gtksignal.h:119: note: expected &#8216;gpointer&#8217; but argument is of type &#8216;int&#8217;
testgtk.c: In function &#8216;page_switch&#8217;:
testgtk.c:5896: error: dereferencing pointer to incomplete type
testgtk.c:5899: error: dereferencing pointer to incomplete type
testgtk.c:5905: error: dereferencing pointer to incomplete type
testgtk.c:5908: error: dereferencing pointer to incomplete type
testgtk.c: In function &#8216;create_notebook&#8217;:
testgtk.c:6102: warning: initialization from incompatible pointer type
testgtk.c:6103: warning: initialization from incompatible pointer type
testgtk.c:6104: warning: initialization from incompatible pointer type
testgtk.c: In function &#8216;create_progress_bar&#8217;:
testgtk.c:7042: warning: initialization from incompatible pointer type
testgtk.c:7043: warning: initialization from incompatible pointer type
testgtk.c:7044: warning: initialization from incompatible pointer type
testgtk.c:7045: warning: initialization from incompatible pointer type
testgtk.c:7050: warning: initialization from incompatible pointer type
testgtk.c:7051: warning: initialization from incompatible pointer type
testgtk.c: In function &#8216;layout_expose_handler&#8217;:
testgtk.c:8279: error: &#8216;GtkLayout&#8217; has no member named &#8216;xoffset&#8217;
testgtk.c:8280: error: &#8216;GtkLayout&#8217; has no member named &#8216;xoffset&#8217;
testgtk.c:8282: error: &#8216;GtkLayout&#8217; has no member named &#8216;yoffset&#8217;
testgtk.c:8283: error: &#8216;GtkLayout&#8217; has no member named &#8216;yoffset&#8217;
testgtk.c:8295: error: &#8216;GtkLayout&#8217; has no member named &#8216;xoffset&#8217;
testgtk.c:8295: error: &#8216;GtkLayout&#8217; has no member named &#8216;yoffset&#8217;

```

I suspect all this code has badly bit rotted :(

---

