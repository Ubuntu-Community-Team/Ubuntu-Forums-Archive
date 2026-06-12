---
title: "How do I align a label in a gtk table to left (not center)"
date: 2007-09-08
forum: Programming Talk
---

### Post by Thyme on 2007-09-08
I'm busy creating a small and simple application that I can use to store information about the herbs I grow. It's my first application and I'm using c and gtk. I'd like to know how to align a widget (textentry, label, button) in a table's cell so that the widget can be aligned left or right in the cell and not center.
 
Below is a screenshot of the table and the code I used to create the table:

[IMG]http://www.hobithouse.co.za/alignment.png[/IMG]

The code is:

```

table = gtk_table_new(5, 2, FALSE);	
		
label = gtk_label_new("Botanical Family (Taxonomic): ");		
gtk_table_attach(GTK_TABLE(table), label,0, 1, 0, 1, 0, 0, 0, 0);
gtk_widget_show(label);						
				
textentry = gtk_entry_new();
gtk_entry_set_width_chars(GTK_ENTRY(textentry), 35);
gtk_table_attach(GTK_TABLE(table), textentry, 1, 2, 0, 1, 0, 0, 0, 0);
gtk_widget_show(textentry);
		
label = gtk_label_new("Therapeutic Effects: ");		
gtk_table_attach(GTK_TABLE(table), label,0, 1, 1, 2, 0, 0, 0, 0);
gtk_widget_show(label);						
				
textentry = gtk_entry_new();
gtk_entry_set_width_chars(GTK_ENTRY(textentry), 35);
gtk_table_attach(GTK_TABLE(table), textentry, 1, 2, 1, 2, 0, 0, 0, 0);
gtk_widget_show(textentry);
		
label = gtk_label_new("Biochemical Constituents: ");		
gtk_table_attach(GTK_TABLE(table), label, 0, 1, 2, 3, 0, 0, 0, 0);
gtk_widget_show(label);						
				
textentry = gtk_entry_new();
gtk_entry_set_width_chars(GTK_ENTRY(textentry), 35);
gtk_table_attach(GTK_TABLE(table), textentry, 1, 2, 2, 3, 0, 0, 0, 0);
gtk_widget_show(textentry);
		
label = gtk_label_new("Plant Parts (Morphological): ");
gtk_table_attach(GTK_TABLE(table), label, 0, 1, 3, 4, 0, 0, 0, 0);
gtk_widget_show(label);
    	
hbox = gtk_hbox_new(FALSE, 0);
		
checkbutton = gtk_check_button_new_with_label("Roots");
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
checkbutton = gtk_check_button_new_with_label("Leaves");    	
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
checkbutton = gtk_check_button_new_with_label("Flowers");
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
gtk_table_attach(GTK_TABLE(table), hbox, 1, 2, 3, 4, 0, 0, 0, 0);
gtk_widget_show(hbox);
    	
hbox = gtk_hbox_new(FALSE, 0);
   	
checkbutton = gtk_check_button_new_with_label("Seeds");
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
checkbutton = gtk_check_button_new_with_label("Stems");    	
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
checkbutton = gtk_check_button_new_with_label("Whole Plant");    	
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
gtk_table_attach(GTK_TABLE(table), hbox, 1, 2, 4, 5, 0, 0, 0, 0);
gtk_widget_show(hbox);
		
label = gtk_label_new("Preferred Method of Intake: ");
gtk_table_attach(GTK_TABLE(table), label,0, 1, 5, 6, 0, 0, 0, 0);
gtk_widget_show(label);						
		
hbox = gtk_hbox_new(FALSE, 0);		
		
checkbutton = gtk_check_button_new_with_label("Infusion");
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
checkbutton = gtk_check_button_new_with_label("Tincture");    	
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
checkbutton = gtk_check_button_new_with_label("Decoction");
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);    	
    	
gtk_table_attach(GTK_TABLE(table), hbox, 1, 2, 5, 6, 0, 0, 0, 0);
gtk_widget_show(hbox);
    	
hbox = gtk_hbox_new(FALSE, 0);		
    	
checkbutton = gtk_check_button_new_with_label("Juice");    	
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
checkbutton = gtk_check_button_new_with_label("Salve/Cream/Oil");    
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
checkbutton = gtk_check_button_new_with_label("Bath");    	
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
gtk_table_attach(GTK_TABLE(table), hbox, 1, 2, 6, 7, 0, 0, 0, 0);
gtk_widget_show(hbox);
    	
hbox = gtk_hbox_new(FALSE, 0);
    	
checkbutton = gtk_check_button_new_with_label("Poultice Fomentation/Compress");    	
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
checkbutton = gtk_check_button_new_with_label("Capsule");
gtk_box_pack_start(GTK_BOX(hbox), checkbutton, FALSE, FALSE, 0);
gtk_widget_show(checkbutton);
    	
gtk_table_attach(GTK_TABLE(table), hbox, 1, 2, 7, 8, 0, 0, 0, 0);
gtk_widget_show(hbox);
		
label = gtk_label_new("Usage Info");
gtk_notebook_insert_page(GTK_NOTEBOOK(notebook), table, label , 2);
gtk_widget_show(table);


```

So what I'm trying to do is align all the labels on the left-hand side to justify to the right and align all the widgets on the right-hand side to justify to the left (against the labels). The textentry widgets are okay but the "small" widgets like the checkboxes must be justified left.

Any help would indeed be most welcome and appreciated :)

---

### Post by bashologist on 2007-09-08
I got a segment fault when I did finally compile your code. It's very hard to read. Maybe there's a way to do a for loop so it's easier to read? Maybe give us a working example?

In python I made a nice for loop like this:
```
		self.table1 = gtk.Table(rows=9, columns=7, homogeneous=True)
		self.table1.set_border_width(1)
		labels = ["CPM:", "Accuracy:", "WPM:", "Seconds:", "Date:", "Username:", "Order:"]
		for cell in range(0, 63):
			row, col = cell / 7, cell % 7
			if cell < 7:
				label = gtk.Label(labels[cell])
				label.set_alignment(0, 0.5)
				self.table1.attach(child=label, left_attach=col, right_attach=col+1, top_attach=row, bottom_attach=row+1)
			else:
				entry = gtk.Entry()
				entry.set_editable(False)
				self.table1.attach(child=entry, left_attach=col, right_attach=col+1, top_attach=row, bottom_attach=row+1)
				self.table1.set_row_spacing(row, 2)
				self.table1.set_col_spacing(col, 2)
```

In c it might be possible too something like this:
```
#include <gtk/gtk.h>

static void destroy(GtkWidget *widget, gpointer data)
{
	gtk_main_quit();
}

int main (int argc, char **argv)
{
	gtk_init (&argc, &argv);
	int cell, row, col;
	GtkWidget *window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	GtkWidget *table = gtk_table_new(9, 7, TRUE);
	
	for (cell = 0; cell < 63; cell++)
	{
		row = cell / 7;
		col = cell % 7;
		GtkWidget *label = gtk_label_new("test");
		gtk_label_set_justify(GTK_LABEL(label), GTK_JUSTIFY_LEFT);
		gtk_table_attach_defaults(GTK_TABLE(table), label, col, col+1, row, row+1);
		gtk_table_set_row_spacing(GTK_TABLE(table), row, 2);
		gtk_table_set_col_spacing(GTK_TABLE(table), col, 10);
		gtk_widget_show(label);
	}
	
	g_signal_connect(G_OBJECT(window), "destroy",
		G_CALLBACK(destroy), NULL);
	
	gtk_container_add(GTK_CONTAINER(window), table);
	gtk_widget_show(table);
	gtk_widget_show(window);
	gtk_main();
	return 0;
}

```
Maybe you wanna use set justify on the label?
```
gtk_label_set_justify(GTK_LABEL(label), GTK_JUSTIFY_LEFT);
gtk_table_attach_defaults(GTK_TABLE(table), label, col, col+1, row, row+1);
```

---

### Post by bashologist on 2007-09-08
Sorry for double post, but maybe you could have an array of GtkWidgets like this? I love for loops too much maybe, they're so fun. n_n
```
#include <gtk/gtk.h>

static void destroy(GtkWidget *widget, gpointer data)
{
	gtk_main_quit();
}

int main (int argc, char **argv)
{
	gtk_init (&argc, &argv);
	int cell, row, col, widgets;
	GtkWidget *window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	GtkWidget *table = gtk_table_new(5, 3, TRUE);
	GtkWidget *array[15];
	
	const gchar *checkbuttonlabels[14] = { "Roots", "Leaves", "Flowers", "Seeds", "Stems", "Whole Plant", "Infusion",
		"Tincture", "Decoction", "Juice", "Salve/Cream/Oil", "Bath", "Poultice Fomentation/Compress", "Capsule", };
	
	for (widgets = 0; widgets < 14; widgets++)
	{
		array[widgets] = gtk_check_button_new_with_label(checkbuttonlabels[widgets]);
	}
	
	for (cell = 0; cell < widgets; cell++)
	{
		row = cell / 3;
		col = cell % 3;
		gtk_table_attach_defaults(GTK_TABLE(table), array[cell], col, col+1, row, row+1);
		gtk_table_set_row_spacing(GTK_TABLE(table), row, 2);
		gtk_table_set_col_spacing(GTK_TABLE(table), col, 2);
		gtk_widget_show(array[cell]);
	}
	
	g_signal_connect(G_OBJECT(window), "destroy",
		G_CALLBACK(destroy), NULL);
	
	gtk_container_add(GTK_CONTAINER(window), table);
	gtk_widget_show(table);
	gtk_widget_show(window);
	gtk_main();
	return 0;
}

```

[http://img137.imagevenue.com/img.php?image=79417_Screenshot_122_578lo.jpg](http://img137.imagevenue.com/img.php?image=79417_Screenshot_122_578lo.jpg)

---

### Post by Thyme on 2007-09-12
Thanks for your help, bashologist.

I've managed to remove many lines of code by taking from your examples. I still haven't been able to align the widgets to left or right though, but I'm sure I'll get it soon enough :) The "gtk_justify_label" doesn't seem to affect the labels at all, unfortunately.

PS: I think the segfault you got was a result of me only copying the table code without the widget declatations such as the labels, textviews etc...

---

### Post by bashologist on 2007-09-12
> **Thyme said:**
> Thanks for your help, bashologist.

I've managed to remove many lines of code by taking from your examples. I still haven't been able to align the widgets to left or right though, but I'm sure I'll get it soon enough :) The "gtk_justify_label" doesn't seem to affect the labels at all, unfortunately.
From reading my previous post, maybe these lines would do it?
```
label = gtk.Label(labels[cell])
label.set_alignment(0, 0.5)
```
If it doesn't help then maybe try setting the table to homogeneous. 
```
GtkWidget *table = gtk_table_new(5, 3, TRUE);
```

That might work, idk. If you could give a working example of that section then it would be np.

---

### Post by Thyme on 2007-09-12
> **bashologist said:**
> From reading my previous post, maybe these lines would do it?
```
label = gtk.Label(labels[cell])
label.set_alignment(0, 0.5)
```
If it doesn't help then maybe try setting the table to homogeneous. 
```
GtkWidget *table = gtk_table_new(5, 3, TRUE);
```

That might work, idk. If you could give a working example of that section then it would be np.

Great, this did the trick. I've attached the code for the notebook if you ever wanna look at it :)

The following lines were added to the "Herb Type" label so that it could align to the left (I just replaced the label value and table cell for other labels):

```

label = gtk_label_new("Herb Type: ");
gtk_widget_show(label);
align = gtk_alignment_new(0.0, 0.5, 0.0, 0.0);
gtk_container_add(GTK_CONTAINER(align), label);
gtk_table_attach(GTK_TABLE(table), align,0, 1, 2, 3, GTK_FILL, GTK_FILL, 0, 0);
gtk_widget_show(align);

``` 


Result:

[IMG]http://www.hobithouse.co.za/__ArbStuff/tabB.png[/IMG]

[IMG]http://www.hobithouse.co.za/__ArbStuff/tabA.png[/IMG]

Thanks :)

---

### Post by Thyme on 2007-09-12
Sorry, I've forgotten the attachment!

---

### Post by bashologist on 2007-09-12
I really like you choice in width, it looks really good like that.

Good job. n_n

---

### Post by CptPicard on 2007-09-12
You actually take some of your herbs by infusion? :o

Well, perhaps the "spiritual" ones... ;)

---

### Post by Bapman on 2008-07-28
> **Thyme said:**
> Great, this did the trick. I've attached the code for the notebook if you ever wanna look at it :)

The following lines were added to the "Herb Type" label so that it could align to the left (I just replaced the label value and table cell for other labels):

```

label = gtk_label_new("Herb Type: ");
gtk_widget_show(label);
align = gtk_alignment_new(0.0, 0.5, 0.0, 0.0);
gtk_container_add(GTK_CONTAINER(align), label);
gtk_table_attach(GTK_TABLE(table), align,0, 1, 2, 3, GTK_FILL, GTK_FILL, 0, 0);
gtk_widget_show(align);

``` 



I had the same problem, you can also solve it by doing :
```

label = gtk_label_new("Herb Type: ");
gtk_misc_set_alignment(GTK_MISC(label),0.0,0.5);
gtk_table_attach(GTK_TABLE(table), label,0, 1, 2, 3, GTK_FILL, GTK_FILL, 0, 0);


```

It is just a little bit simpler ! The only thing to remember is to put GTK_FILL as an xoptions in gtk_table_attach().

---

