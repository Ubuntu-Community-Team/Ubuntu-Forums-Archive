---
title: "How to pass struct in GTK+ callback?"
date: 2007-12-23
forum: Programming Talk
---

### Post by JupiterV2 on 2007-12-23
I seem to be missing something...here's a dummied down version of my code:

[php]
/* start header */
struct myStruct {
    GtkWidget* widget;
    explicit myStruct() {}
    ~myStruct() {}
};

gboolean cb_delete(GtkWidget* widget, GdkEvent* event, gpointer data) {
  /* data dereferenced via -> or type casted with (myStruct) creates compile *
   * error  */
  gtk_main_quit();
  return false;
}
/* end header */

int main() {
  myStruct widget_list;

  GtkWidget* window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

  g_signal_connect(G_OBJECT(window), "delete-event", 
      G_CALLBACK(cb_delete), widget_list);

  gtk_main();
}

[/php]

I want to pass the struct as an argument rather than as a global variable. How do I do this properly?

Can I not use a C++ style stuct with a construct/destructor? Must I use a regular C struct? How do I overcome this?

---

### Post by dwhitney67 on 2007-12-23
> **JupiterV2 said:**
> 
I want to pass the struct as an argument rather than as a global variable. How do I do this properly?

Can I not use a C++ style stuct with a construct/destructor? Must I use a regular C struct? How do I overcome this?
Your variable, widget_list, is not a global variable.  It is local to the main() function.  You may want to pass it's address (i.e. precede the parameter with an &).

In C++, structures (structs) and classes are identical, except for one thing:  with structs all declarations (constructor, destructor, virtual methods, member data) are "public", whereas with a class all declarations, by default, they are "private", unless otherwise specified.

Don't confuse a declaration of a class/struct with the "instantiation" of such.

---

### Post by nrs on 2007-12-23
Aside from what dwhitney67 said. If you're already using C++, why not use GTKmm? Seems infinitely more preferable.

---

