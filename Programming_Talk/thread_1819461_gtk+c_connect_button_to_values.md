---
title: "gtk+/c connect button to values"
date: 2011-08-06
forum: Programming Talk
---

### Post by chukchuck on 2011-08-06
```
#include <stdio.h>
#include <stdlib.h>
#include <gtk/gtk.h>

/*Devo fare un pulsante che, una volta premuto, legga
 * i due numeri e ne calcoli l'MCD
 * Compila con: gcc -o mcd-ui mcd-ui.c $(pkg-config --cflags --libs gtk+-2.0 gmodule-2.0)*/
 
int main(int argc, char *argv[]){
    
    GtkWidget *window;
    GtkWidget *table;
    
    GtkWidget *label1;
    GtkWidget *label2;
    GtkWidget *label3;
    
    GtkWidget *num1;
    GtkWidget *num2;
    GtkWidget *mcdt;
        
    GtkWidget *button;
    
    GtkWidget *box1;
    
    gtk_init(&argc, &argv);
    
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
    gtk_window_set_title(GTK_WINDOW(window), "MCD Calculator");
    gtk_container_set_border_width(GTK_CONTAINER(window), 10);
    
    box1 = gtk_vbox_new (FALSE, 0);
        
    table = gtk_table_new(4, 4, FALSE);
    
    gtk_container_add(GTK_CONTAINER (window), box1);
    gtk_box_pack_start(GTK_BOX(box1), table, TRUE, TRUE, 0);
    
    label1 = gtk_label_new("Num1");
    label2 = gtk_label_new("Num2");
    label3 = gtk_label_new("MCD");
    
    gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label2, 0, 1, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label3, 0, 1, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    
    num1 = gtk_entry_new();
    num2 = gtk_entry_new();
    mcdt = gtk_entry_new();
    gtk_entry_set_editable(GTK_ENTRY(mcdt), FALSE); 
    
    gtk_table_attach(GTK_TABLE(table), num1, 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), num2, 1, 2, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), mcdt, 1, 2, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    
    button = gtk_button_new_with_label ("Calcola MCD");
    gtk_box_pack_start(GTK_BOX(box1), button, TRUE, TRUE, 0);
    
    gtk_widget_show_all(window);
    
    g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);
    
    gtk_main();
    
    return EXIT_SUCCESS;
}

```

i need to do that: when i press the button a function read values "num1", "num2"  and do something...but i don't know how to connect button to 2 values :(

---

### Post by nvteighen on 2011-08-06
> **chukchuck said:**
> ```
#include <stdio.h>
#include <stdlib.h>
#include <gtk/gtk.h>

/*Devo fare un pulsante che, una volta premuto, legga
 * i due numeri e ne calcoli l'MCD
 * Compila con: gcc -o mcd-ui mcd-ui.c $(pkg-config --cflags --libs gtk+-2.0 gmodule-2.0)*/
 
int main(int argc, char *argv[]){
    
    GtkWidget *window;
    GtkWidget *table;
    
    GtkWidget *label1;
    GtkWidget *label2;
    GtkWidget *label3;
    
    GtkWidget *num1;
    GtkWidget *num2;
    GtkWidget *mcdt;
        
    GtkWidget *button;
    
    GtkWidget *box1;
    
    gtk_init(&argc, &argv);
    
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
    gtk_window_set_title(GTK_WINDOW(window), "MCD Calculator");
    gtk_container_set_border_width(GTK_CONTAINER(window), 10);
    
    box1 = gtk_vbox_new (FALSE, 0);
        
    table = gtk_table_new(4, 4, FALSE);
    
    gtk_container_add(GTK_CONTAINER (window), box1);
    gtk_box_pack_start(GTK_BOX(box1), table, TRUE, TRUE, 0);
    
    label1 = gtk_label_new("Num1");
    label2 = gtk_label_new("Num2");
    label3 = gtk_label_new("MCD");
    
    gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label2, 0, 1, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label3, 0, 1, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    
    num1 = gtk_entry_new();
    num2 = gtk_entry_new();
    mcdt = gtk_entry_new();
    gtk_entry_set_editable(GTK_ENTRY(mcdt), FALSE); 
    
    gtk_table_attach(GTK_TABLE(table), num1, 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), num2, 1, 2, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), mcdt, 1, 2, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    
    button = gtk_button_new_with_label ("Calcola MCD");
    gtk_box_pack_start(GTK_BOX(box1), button, TRUE, TRUE, 0);
    
    gtk_widget_show_all(window);
    
    g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);
    
    gtk_main();
    
    return EXIT_SUCCESS;
}

```

i need to do that: when i press the button a function read values "num1", "num2"  and do something...but i don't know how to connect button to 2 values :(

All actions are performed by callbacks that you connect using g_signal_connect(). The steps for doing this are usually the following:

0. Look at the signature the "clicked" signal asks for its callback function. This information is at the GTK+ API docs. For GtkButton "clicked":

```

void user_function(GtkButton *button, gpointer user_data);

```

1. Write a function that will read the data, and takes the parameters as shown in step 0. You use the user_data argument to pass any arbitrary data; gpointer is a pointer type that is equivalent to void *, so you can use that as an array.

2. g_signal_connect as usual:
```

g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(your_callback), your_data);

```

That's all there is, actually.

Also, you're not casting window using GTK_WINDOW when connecting its "destroy" signal. Fix that or undefined behaivor may arise.

---

### Post by chukchuck on 2011-08-06
Ok, THANKS a lot :) now i'm trying to implement into my code :)
I haven't understand a thing:

> 
Also, you're not casting window using GTK_WINDOW when connecting its "destroy" signal. Fix that or undefined behaivor may arise.

you mean that i have to correct this:
```
g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);
```

into this:
```
g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(gtk_main_quit), NULL);
```

or do you mean other thing?

---

### Post by chukchuck on 2011-08-06
```
#include <stdio.h>
#include <stdlib.h>
#include <gtk/gtk.h>

/*Devo fare un pulsante che, una volta premuto, legga
 * i due numeri e ne calcoli l'MCD
 * Compila con: gcc -o mcd-ui mcd-ui.c $(pkg-config --cflags --libs gtk+-2.0 gmodule-2.0)*/
 
void mcd_calc(GtkButton *button, gpointer user_data);

int main(int argc, char *argv[]){
    
    GtkWidget *window;
    GtkWidget *table;
    
    GtkWidget *label1;
    GtkWidget *label2;
    GtkWidget *label3;
    
    GtkWidget *num[2];
    GtkWidget *mcdt;
        
    GtkWidget *button;
    
    GtkWidget *box1;
    
    gtk_init(&argc, &argv);
    
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
    gtk_window_set_title(GTK_WINDOW(window), "MCD Calculator");
    gtk_container_set_border_width(GTK_CONTAINER(window), 10);
    
    box1 = gtk_vbox_new (FALSE, 0);
        
    table = gtk_table_new(4, 4, FALSE);
    
    gtk_container_add(GTK_CONTAINER (window), box1);
    gtk_box_pack_start(GTK_BOX(box1), table, TRUE, TRUE, 0);
    
    label1 = gtk_label_new("Num1");
    label2 = gtk_label_new("Num2");
    label3 = gtk_label_new("MCD");
    
    gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label2, 0, 1, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label3, 0, 1, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    
    num[0] = gtk_entry_new();
    num[1] = gtk_entry_new();
    mcdt = gtk_entry_new();
    gtk_entry_set_editable(GTK_ENTRY(mcdt), FALSE); 
    
    gtk_table_attach(GTK_TABLE(table), num[0], 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), num[1], 1, 2, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), mcdt, 1, 2, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    
    button = gtk_button_new_with_label ("Calcola MCD");
    gtk_box_pack_start(GTK_BOX(box1), button, TRUE, TRUE, 0);
    for(i=0 ; i<2 ; i++){
        g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(your_callback), num[i]);
    }
    
    gtk_widget_show_all(window);
    
    g_signal_connect(GTK_WINDOW(window), "destroy", G_CALLBACK(gtk_main_quit), NULL);
        
    gtk_main();
    
    return EXIT_SUCCESS;
}

```

i am at this dead point...i have some questions:

**1) It is right to do this thing?**
```

```    for(i=0 ; i<2 ; i++){
        g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(your_callback), num[i]);
    }

**2) into this line:**
```
void mcd_calc(GtkButton *button, gpointer user_data);
```
into *"gpointer user_data"* what have i to write?
[B]
3) the callback *your_callback* is the function mcd_calc?[/B]
```
 g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(your_callback), 
```
become
```
 g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(mcd_calc), 
```

thanks man :)

---

### Post by nvteighen on 2011-08-06
> **chukchuck said:**
> 
I haven't understand a thing:

you mean that i have to correct this:
```
g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);
```

into this:
```
g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(gtk_main_quit), NULL);
```

or do you mean other thing?

As you know, all widgets are declared as GtkWidget *. In fact, in your code *window* is of that type, which is right. But whenever a function asks for some specific widget, you have to cast it. The cast macro is usually the typename written in uppercase and with an underscore (_) used as separator, so GtkWindow -> GTK_WINDOW. So, what you should do in that case is:

```

g_signal_connect(GTK_WINDOW(window), "destroy", G_CALLBACK(gtk_main_quit), NULL);

```

> **chukchuck said:**
> 

[...]

i am at this dead point...i have some questions:

**1) It is right to do this thing?**
```

```    for(i=0 ; i<2 ; i++){
        g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(your_callback), num[i]);
    }


You got the idea. You're problem is related to pointers, actually: num should be declared a GtkWidget **, because you're making an array of GtkWidget * (the ones returned by gtk_entry_new).

If you want the button be aware of the GtkEntry widgets' values, I'd retrieve the text into an array of strings rather than passing around pointers to the widgets, but it's optional.

> 
**2) into this line:**
```
void mcd_calc(GtkButton *button, gpointer user_data);
```
into *"gpointer user_data"* what have i to write?


Nothing, that's a declaration. The user_data argument will be filled with the user_data you passed when connecting the callback to its signal.

Of course, you have to implement this function... But again, it's actually you who defines what user_data means and is meant to hold.

> 
3) the callback *your_callback* is the function mcd_calc?[/B]
```
 g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(your_callback), 
```
become
```
 g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(mcd_calc), 
```


Yes, you got it right.

---

### Post by chukchuck on 2011-08-06
Here the new code:

```
#include <stdio.h>
#include <stdlib.h>
#include <gtk/gtk.h>

/*Devo fare un pulsante che, una volta premuto, legga
 * i due numeri e ne calcoli l'MCD
 * Compila con: gcc -o mcd-ui mcd-ui.c $(pkg-config --cflags --libs gtk+-2.0 gmodule-2.0)*/
 
int mcd();
void mcd_calc(GtkWidget **num, GtkButton *button, gpointer user_data);

void mcd_calc(GtkWidget **num, GtkButton *button, gpointer user_data){
	const gchar *a;
	a = gtk_entry_get_text(GTK_ENTRY(num[0]));
	const gchar *b;
	a = gtk_entry_get_text(GTK_ENTRY(num[1]));
	int c;
	c=mcd(a,b);
	g_print("MCD between %d and %d is: %d", a,b,c);
	return EXIT_SUCCESS;
}

int mcd(int x, int y){
	if(y==0){
		return x;
	}
	else return mcd(y, x%y);
}

int main(int argc, char *argv[]){
    
    int i;
    
    GtkWidget *window;
    GtkWidget *table;
    
    GtkWidget *label1;
    GtkWidget *label2;
    GtkWidget *label3;
    
    GtkWidget **num[2];
    GtkWidget *mcdt;
        
    GtkWidget *button;
    
    GtkWidget *box1;
    
    gtk_init(&argc, &argv);
    
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
    gtk_window_set_title(GTK_WINDOW(window), "MCD Calculator");
    gtk_container_set_border_width(GTK_CONTAINER(window), 10);
    
    box1 = gtk_vbox_new (FALSE, 0);
        
    table = gtk_table_new(4, 4, FALSE);
    
    gtk_container_add(GTK_CONTAINER (window), box1);
    gtk_box_pack_start(GTK_BOX(box1), table, TRUE, TRUE, 0);
    
    label1 = gtk_label_new("Num1");
    label2 = gtk_label_new("Num2");
    label3 = gtk_label_new("MCD");
    
    gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label2, 0, 1, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label3, 0, 1, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    
    num[0] = gtk_entry_new();
    num[1] = gtk_entry_new();
    mcdt = gtk_entry_new();
    gtk_entry_set_editable(GTK_ENTRY(mcdt), FALSE); 
    
    gtk_table_attach(GTK_TABLE(table), num[0], 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), num[1], 1, 2, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), mcdt, 1, 2, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    
    button = gtk_button_new_with_label ("Calcola MCD");
    gtk_box_pack_start(GTK_BOX(box1), button, TRUE, TRUE, 0);
    for(i=0 ; i<2 ; i++){
        g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(mcd_calc), num[i]);
    }
    
    gtk_widget_show_all(window);
    
    g_signal_connect(GTK_WINDOW(window), "destroy", G_CALLBACK(gtk_main_quit), NULL);
        
    gtk_main();
    
    return EXIT_SUCCESS;
}

```

But i get these errors :(

(mcd-ui2:5677): GLib-GObject-WARNING **: invalid uninstantiatable type `<unknown>' in cast to `GtkEntry'

(mcd-ui2:5677): Gtk-CRITICAL **: IA__gtk_entry_get_text: assertion `GTK_IS_ENTRY (entry)' failed
Segmentation Fault

---

### Post by JupiterV2 on 2011-08-06
> **chukchuck said:**
> Here the new code:

```
#include <stdio.h>
#include <stdlib.h>
#include <gtk/gtk.h>

/*Devo fare un pulsante che, una volta premuto, legga
 * i due numeri e ne calcoli l'MCD
 * Compila con: gcc -o mcd-ui mcd-ui.c $(pkg-config --cflags --libs gtk+-2.0 gmodule-2.0)*/
 
int mcd();
void mcd_calc(GtkWidget **num, GtkButton *button, gpointer user_data);

void mcd_calc(GtkWidget **num, GtkButton *button, gpointer user_data){
	const gchar *a;
	a = gtk_entry_get_text(GTK_ENTRY(num[0]));
	const gchar *b;
	a = gtk_entry_get_text(GTK_ENTRY(num[1]));
	int c;
	c=mcd(a,b);
	g_print("MCD between %d and %d is: %d", a,b,c);
	return EXIT_SUCCESS;
}

int mcd(int x, int y){
	if(y==0){
		return x;
	}
	else return mcd(y, x%y);
}

int main(int argc, char *argv[]){
    
    int i;
    
    GtkWidget *window;
    GtkWidget *table;
    
    GtkWidget *label1;
    GtkWidget *label2;
    GtkWidget *label3;
    
    GtkWidget **num[2];
    GtkWidget *mcdt;
        
    GtkWidget *button;
    
    GtkWidget *box1;
    
    gtk_init(&argc, &argv);
    
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
    gtk_window_set_title(GTK_WINDOW(window), "MCD Calculator");
    gtk_container_set_border_width(GTK_CONTAINER(window), 10);
    
    box1 = gtk_vbox_new (FALSE, 0);
        
    table = gtk_table_new(4, 4, FALSE);
    
    gtk_container_add(GTK_CONTAINER (window), box1);
    gtk_box_pack_start(GTK_BOX(box1), table, TRUE, TRUE, 0);
    
    label1 = gtk_label_new("Num1");
    label2 = gtk_label_new("Num2");
    label3 = gtk_label_new("MCD");
    
    gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label2, 0, 1, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label3, 0, 1, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    
    num[0] = gtk_entry_new();
    num[1] = gtk_entry_new();
    mcdt = gtk_entry_new();
    gtk_entry_set_editable(GTK_ENTRY(mcdt), FALSE); 
    
    gtk_table_attach(GTK_TABLE(table), num[0], 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), num[1], 1, 2, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), mcdt, 1, 2, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    
    button = gtk_button_new_with_label ("Calcola MCD");
    gtk_box_pack_start(GTK_BOX(box1), button, TRUE, TRUE, 0);
    for(i=0 ; i<2 ; i++){
        g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(mcd_calc), num[i]);
    }
    
    gtk_widget_show_all(window);
    
    g_signal_connect(GTK_WINDOW(window), "destroy", G_CALLBACK(gtk_main_quit), NULL);
        
    gtk_main();
    
    return EXIT_SUCCESS;
}

```

But i get these errors :(

(mcd-ui2:5677): GLib-GObject-WARNING **: invalid uninstantiatable type `<unknown>' in cast to `GtkEntry'

(mcd-ui2:5677): Gtk-CRITICAL **: IA__gtk_entry_get_text: assertion `GTK_IS_ENTRY (entry)' failed
Segmentation Fault

That would be because 'void mcd_calc(GtkWidget **num, GtkButton *button, gpointer user_data)' is incorrect. The callback for a button does not accept a pointer to an array of widgets but a single widget, the button the signal is connected to. The callback for the button widget looks like this:

```
void user_function (GtkButton *button, gpointer   user_data);
```

Always make sure you reference the GTK+ documentation. Here is a link to the ["clicked" event]("http://developer.gnome.org/gtk3/stable/GtkButton.html#GtkButton-clicked").This is because you can connect several buttons to the same callback. I assume that you're trying to get the contents of two GtkEntry's but you have supplied no method for the callback to access the widgets. Consider doing one of the following:

1) Use a global pointer to your widgets;
2) Pass one or both of your entry widgets as the user data to the callback.

There are other methods too but are beyond the scope of this discussion.

---

### Post by chukchuck on 2011-08-06
> **JupiterV2 said:**
> 
1) Use a global pointer to your widgets;
2) Pass one or both of your entry widgets as the user data to the callback.


Thanks for your answer :)
Yes, my intention is give the 2 numbers i've entered to the callback that calculate the MCD...however i haven't understand how to use method 1 or 2 :(

---

### Post by chukchuck on 2011-08-06
I have add another callback because one is only for read numbers and the last is for calculate the MCD:

```
#include <stdio.h>
#include <stdlib.h>
#include <gtk/gtk.h>

int mcd();
void read_number(GtkButton *button, gpointer user_data);
void mcd_calc(GtkButton *button, gpointer user_data);

void read_number(GtkButton *button, gpointer user_data){
 g_printf("Here i have to read numbers..\n");
}

void mcd_calc(GtkButton *button, gpointer user_data){
 g_printf("Here i calc MCD...\n");
}

int main(int argc, char *argv[]){
    
    int i;
    
    GtkWidget *window;
    GtkWidget *table;
    
    GtkWidget *label1;
    GtkWidget *label2;
    GtkWidget *label3;
    
    GtkWidget **num[2];
    GtkWidget *mcdt;
        
    GtkWidget *button;
    
    GtkWidget *box1;
    
    gtk_init(&argc, &argv);
    
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
    gtk_window_set_title(GTK_WINDOW(window), "MCD Calculator");
    gtk_container_set_border_width(GTK_CONTAINER(window), 10);
    
    box1 = gtk_vbox_new (FALSE, 0);
        
    table = gtk_table_new(4, 4, FALSE);
    
    gtk_container_add(GTK_CONTAINER (window), box1);
    gtk_box_pack_start(GTK_BOX(box1), table, TRUE, TRUE, 0);
    
    label1 = gtk_label_new("Num1");
    label2 = gtk_label_new("Num2");
    label3 = gtk_label_new("MCD");
    
    gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label2, 0, 1, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    gtk_table_attach(GTK_TABLE(table), label3, 0, 1, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK,5, 5);
    
    num[0] = gtk_entry_new();
    num[1] = gtk_entry_new();
    mcdt = gtk_entry_new();
    gtk_entry_set_editable(GTK_ENTRY(mcdt), FALSE); 
    
    gtk_table_attach(GTK_TABLE(table), num[0], 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), num[1], 1, 2, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    gtk_table_attach(GTK_TABLE(table), mcdt, 1, 2, 2, 3, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
    
    button = gtk_button_new_with_label ("Calcola MCD");
    gtk_box_pack_start(GTK_BOX(box1), button, TRUE, TRUE, 0);
    for(i=0 ; i<2 ; i++){
        g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(read_number), num[i]);
    }
    g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(mcd_calc), NULL);
    
    gtk_widget_show_all(window);
    
    g_signal_connect(GTK_WINDOW(window), "destroy", G_CALLBACK(gtk_main_quit), NULL);
        
    gtk_main();
    
    return EXIT_SUCCESS;
}

```

---

