---
title: "add items to toolbar"
date: 2008-10-02
forum: Programming Talk
---

### Post by Hairy_Palms on 2008-10-02
im writing a program, using GTK, mainly as a learning exercise, im trying to create a toolbar and add items to it, but im having problems with the code,

```
GtkWidget *label;
	GtkWidget *piccy;
	GtkWidget *holder;
	GtkWidget *eventbox;
	GtkWidget *dropdown;
	GtkWidget *dropdownbutton;

dropdown = gtk_toolbar_new (); 
dropdownbutton = gtk_tool_item_new();
label = gtk_label_new ("Menu");
gtk_toolbar_insert (dropdown, dropdownbutton, 0);
gtk_container_add (GTK_CONTAINER (dropdownbutton), label); 
```

when compiling it, i get a warning
```
my_applet.c:67: warning: passing argument 1 of ‘gtk_toolbar_insert’ from incompatible pointer type
my_applet.c:67: warning: passing argument 2 of ‘gtk_toolbar_insert’ from incompatible pointer type
```

which refers to the lines above, can anyone tell me what im doing wrong?

---

### Post by kknd on 2008-10-02
you need to cast it using GTK_TOOLBAR(dropdown)

---

### Post by Hairy_Palms on 2008-10-03
thanks for the response, worked fine. :)

---

