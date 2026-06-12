---
title: "[GTK] checkbox (with label) and entry length"
date: 2010-08-10
forum: Programming Talk
---

### Post by SpinningAround on 2010-08-10
How do you set entry to a specific length, I tried gtk_entry_set_width_chars but it don't effect the size. Other question is how to set the length of the label that is created with gtk_check_box_with_label_new. gtk_label_set_width_chars doesn't work.

EDIT:
It currently look like in the first picture and I want it to look like in the second picture.

[PHP]
gchar limits[][11] = {"Total:","Upload:","Download:"};
int lenLimits=sizeof(limits)/sizeof(char[11]);
GtkWidget *vbox = gtk_vbox_new(TRUE,2);
	for(int i=0;i<lenLimits;i++){
		GtkWidget *hbox = gtk_hbox_new(FALSE,2);
		checkboxLimits[i] =  gtk_check_button_new_with_label(&limits[i][0]);
		entryLimits[i] = gtk_entry_new ();
		gtk_box_pack_start (GTK_BOX (hbox), checkboxLimits[i], expand, fill, padding);
		gtk_box_pack_start (GTK_BOX (hbox), entryLimits[i], expand, fill, padding);
		gtk_widget_show (checkboxLimits[i]);
		gtk_widget_show (entryLimits[i]);
		gtk_box_pack_start (GTK_BOX (vbox), hbox, expand, fill, padding);
		gtk_widget_show (hbox);
	}
	gtk_widget_show(vbox);
[/PHP]

---

