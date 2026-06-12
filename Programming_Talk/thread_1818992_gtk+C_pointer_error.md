---
title: "gtk+/C pointer error"
date: 2011-08-05
forum: Programming Talk
---

### Post by chukchuck on 2011-08-05
```
#include <stdio.h>
#include <stdlib.h>
#include <gtk/gtk.h>

int mcd();

static void num1( GtkWidget *entry1 )
{
	const gchar* a;
	a = gtk_entry_get_text(GTK_ENTRY (entry1));	
}

static void num2( GtkWidget *entry2)
{
	const gchar* b;
	b = gtk_entry_get_text(GTK_ENTRY (entry2));
}

/*CALCOLO MDC*/
static void callback( GtkWidget *widget,
                      gpointer   data)
{
	GtkWidget *entries = data;
	int a,b,c;
HERE	a=atoi(gtk_entry_get_text(GTK_ENTRY(entries[0])));
HERE	b=atoi(gtk_entry_get_text(GTK_ENTRY(entries[1])));
	c=mcd(a,b);
	g_print("%d\n", c);
}

int mcd(int x, int y){
		if(y==0){
		return x;
		}
	else return mcd(y, x%y);
}
/*FINE MCD*/

int main(int argc, char *argv[]) {
	GtkWidget *window;
	GtkWidget *table;

	GtkWidget *label1;
	GtkWidget *label2;

	GtkWidget *entry1;
	GtkWidget *entry2;
  
	GtkWidget *button;
    
	gtk_init(&argc, &argv);

	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
	gtk_window_set_title(GTK_WINDOW(window), "MCD Calculator");
	gtk_container_set_border_width(GTK_CONTAINER(window), 10);
  
	table = gtk_table_new(3, 2, FALSE);
	gtk_container_add(GTK_CONTAINER(window), table);
  
	label1 = gtk_label_new("Num1:");
	label2 = gtk_label_new("Num2:");


	gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
	gtk_table_attach(GTK_TABLE(table), label2, 0, 1, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
      
	entry1 = gtk_entry_new();
	g_signal_connect(G_OBJECT(entry1), "activate", G_CALLBACK(num1), &entry1);
	entry2 = gtk_entry_new();
	g_signal_connect(G_OBJECT(entry2), "activate", G_CALLBACK(num2), &entry2);

	gtk_table_attach(GTK_TABLE(table), entry1, 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
	gtk_table_attach(GTK_TABLE(table), entry2, 1, 2, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
  
	/*Pulsante calcola*/
	button = gtk_button_new_with_label ("Calcola");
	gtk_container_add (GTK_CONTAINER (window), button);
	gtk_table_attach (GTK_TABLE (table), button, 1, 5, 7, 8, GTK_FILL | GTK_EXPAND, GTK_FILL | GTK_EXPAND, 0, 0);
	GtkWidget *entries[2] = { entry1, entry2 };
	g_signal_connect (button, "clicked", G_CALLBACK (callback), entries);
	/*Fine pulsante calcola*/

	gtk_widget_show_all(window);

	g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);

	gtk_main();

	return EXIT_SUCCESS;
}

```

Where i have write the two "HERE" i get this error:
* error: cannot convert to a pointer type*
and i don't know how to solve :(

---

### Post by Bachstelze on 2011-08-05
gtk_entry_get_text() returns a gchar*, atoi expect a char*. Try

```
a=atoi((char*)gtk_entry_get_text(GTK_ENTRY(entries[0])));
```

Not sure because I don't know what GTK_ENTRY is, maybe the problem is GTK_ENTRY(entries[0]).

---

### Post by chukchuck on 2011-08-05
don't work :(
however gtk_entry is for entry text..it return a gchar!

---

### Post by Bachstelze on 2011-08-05
Maybe that's your problem then, because gtk_entry_get_text takes a GtkEntry* as its argument. [http://developer.gnome.org/gtk/2.24/GtkEntry.html#gtk-entry-get-text](http://developer.gnome.org/gtk/2.24/GtkEntry.html#gtk-entry-get-text)

---

### Post by chukchuck on 2011-08-05
i'm not sure it is a gtkentry problem because:

```
static void num1( GtkWidget *entry1 )
{
	const gchar* a;
	a = gtk_entry_get_text(GTK_ENTRY (entry1));
	g_print("%d", a);
}
```

will print the "a" value...

---

### Post by Bachstelze on 2011-08-05
Hmm, yes, could you please break it down so we can see exactly where it fails?

```
GtkEntry *tmp1 = GTK_ENTRY(entries[0]);
gchar *tmp2 = gtk_entry_get_text(tmp1);
a=atoi(tmp2);
```

---

### Post by JupiterV2 on 2011-08-05
GTK_ENTRY() casts the GtkWidget* to a GtkEntry*. gtk_entry_get_text() actually returns a const gchar * which is incompatible with a non-const variable. You'll either need to dup/copy the result if you wish to modify the contents. In this case, atoi() takes a const char * as an argument. @chukchuck correctly handles this in his example.

---

### Post by chukchuck on 2011-08-05
@jupiter: i don't want to modify inputs, i only want to read and use them to calculate MCD (math) :)
@bach: i don't understand what i have to do..sorry this is my second gtk+ program :)

---

### Post by chukchuck on 2011-08-05
> **Bachstelze said:**
> Hmm, yes, could you please break it down so we can see exactly where it fails?

```
GtkEntry *tmp1 = GTK_ENTRY(entries[0]);
gchar *tmp2 = gtk_entry_get_text(tmp1);
a=atoi(tmp2);
```

Here the new code:

```


#include <stdio.h>
#include <stdlib.h>
#include <gtk/gtk.h>

int mcd();

static void num1( GtkWidget *entry1 )
{
	const gchar* a;
	a = gtk_entry_get_text(GTK_ENTRY (entry1));	
}

static void num2( GtkWidget *entry2)
{
	const gchar* b;
	b = gtk_entry_get_text(GTK_ENTRY (entry2));
}

/*CALCOLO MDC*/
static void callback( GtkWidget *widget,
                      gpointer   data)
{
	GtkWidget *entries = data;
	int a,b,c;
	c=mcd(a,b);
	g_print("%d\n", c);
}

int mcd(int x, int y){
		if(y==0){
		return x;
		}
	else return mcd(y, x%y);
}
/*FINE MCD*/

int main(int argc, char *argv[]) {
	GtkWidget *window;
	GtkWidget *table;

	GtkWidget *label1;
	GtkWidget *label2;

	GtkWidget *entry1;
	GtkWidget *entry2;
  
	GtkWidget *button;
    
	gtk_init(&argc, &argv);

	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
	gtk_window_set_title(GTK_WINDOW(window), "MCD Calculator");
	gtk_container_set_border_width(GTK_CONTAINER(window), 10);
  
	table = gtk_table_new(3, 2, FALSE);
	gtk_container_add(GTK_CONTAINER(window), table);
  
	label1 = gtk_label_new("Num1:");
	label2 = gtk_label_new("Num2:");


	gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
	gtk_table_attach(GTK_TABLE(table), label2, 0, 1, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
      
	entry1 = gtk_entry_new();
	g_signal_connect(G_OBJECT(entry1), "activate", G_CALLBACK(num1), &entry1);
	entry2 = gtk_entry_new();
	g_signal_connect(G_OBJECT(entry2), "activate", G_CALLBACK(num2), &entry2);

	gtk_table_attach(GTK_TABLE(table), entry1, 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
	gtk_table_attach(GTK_TABLE(table), entry2, 1, 2, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
  
	/*Pulsante calcola*/
	button = gtk_button_new_with_label ("Calcola");
	gtk_container_add (GTK_CONTAINER (window), button);
	gtk_table_attach (GTK_TABLE (table), button, 1, 5, 7, 8, GTK_FILL | GTK_EXPAND, GTK_FILL | GTK_EXPAND, 0, 0);
	GtkWidget *entries[2] = { entry1, entry2 };
	GtkEntry *tmp1 = GTK_ENTRY(entries[0]);
	gchar *tmp2 = gtk_entry_get_text(tmp1);
	int a=atoi(tmp2);
	g_signal_connect (button, "clicked", G_CALLBACK (callback), entries);
	/*Fine pulsante calcola*/

	gtk_widget_show_all(window);

	g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);

	gtk_main();

	return EXIT_SUCCESS;
}

```

and it compiles successfully :)

---

