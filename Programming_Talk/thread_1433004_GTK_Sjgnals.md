---
title: "GTK Sjgnals"
date: 2010-03-18
forum: Programming Talk
---

### Post by sandyd on 2010-03-18
Can someone give me a link to a site that has info on how to launch dialogs from a parent window using signals? (GTK I mean)

---

### Post by nvteighen on 2010-03-18
Er... just use the proper signal to launch it... Use a callback that makes your dialog, runs it, shows it, and does what it should. That's all you need.

GTK+ is all about creating widgets with callbacks associated to their events and let those callbacks do the interfacing between purely "View" code and functional code (either just GUI updating or backend updating).

Anyway, look at the GTK+ Official Tutorial here: [http://library.gnome.org/devel/gtk-tutorial/stable/x863.html](http://library.gnome.org/devel/gtk-tutorial/stable/x863.html)

---

### Post by roccivic on 2010-03-18
GTK+ reference is quite good. Not sure if this if something you might be looking for, but I wrote a launcher a while ago, so here's a small bit of it:


[PHP]void callback( char *cmd ) {
	system( cmd );
	//gtk_main_quit();
}[/PHP]

[PHP]....
	char		*command[16];
....
		button = gtk_button_new();
		g_signal_connect_swapped (GTK_OBJECT (button), "clicked",
				     G_CALLBACK (callback), command[i] );
....[/PHP]

---

### Post by sandyd on 2010-03-18
ooh.
need to make myself a bit clearer.
Im currently using monodevelop.

I created my main window, and I now created a (seperate) dialog for the "about" dialog.
What do I type into the action callback signal box to launch the dialog?

---

### Post by roccivic on 2010-03-19
not sure what monodevelop is, anyway here's bits from 2 of my programs.

1: It has a separate preferences window. Note that "pref_window" in this case is a global variable.

```
void show_prefs() {
	gtk_widget_show_all (pref_window);
}
```

```
/* Create preference window */
	pref_window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
	gtk_window_set_resizable (GTK_WINDOW (pref_window), FALSE);
	gtk_widget_set_size_request (pref_window, 400, 250);

	icon = gdk_pixbuf_new_from_file ("./icons/goscope.png", &error);
	gtk_window_set_icon(GTK_WINDOW(pref_window), icon);

	g_signal_connect (GTK_OBJECT (pref_window), "delete-event",
		G_CALLBACK (gtk_widget_hide_on_delete), NULL);

	gtk_window_set_title (GTK_WINDOW (pref_window), "GOscope: preferences");
	gtk_container_set_border_width (GTK_CONTAINER (pref_window), 0);

	vbox = gtk_vbox_new (FALSE, 5);
	gtk_container_add (GTK_CONTAINER (pref_window), vbox);
```

```
	button = gtk_button_new_with_label ("Settings");
	g_signal_connect (GTK_OBJECT (button), "clicked",
		G_CALLBACK (show_prefs), NULL);
	gtk_box_pack_start (GTK_BOX (vbox), button, TRUE, TRUE, 5);
	button_icon = gtk_image_new_from_file ("./icons/settings.png");
	gtk_button_set_image (GTK_BUTTON (button), button_icon);
```

2: And here's another one:
```
	button = gtk_button_new_with_label ("About");

	g_signal_connect (GTK_OBJECT (button), "clicked",

		G_CALLBACK (show_about), NULL);
```
```
void show_about (GtkWidget *widget, gpointer window) {
	GtkWidget	*dialog;

	dialog = gtk_about_dialog_new();
	gtk_about_dialog_set_name(GTK_ABOUT_DIALOG(dialog),
			"crypt-gtk");
	gtk_about_dialog_set_version(GTK_ABOUT_DIALOG(dialog),
			"0.01"); 
	gtk_about_dialog_set_copyright(GTK_ABOUT_DIALOG(dialog), 
			"(c) 2008 Rouslan Placella");
	gtk_about_dialog_set_website(GTK_ABOUT_DIALOG(dialog), 
			"http://www.placella.com/crypt-gtk/");
	gtk_about_dialog_set_license(GTK_ABOUT_DIALOG(dialog),
			"crypt-gtk is free software: you can redistribute it and/or modify\nit under the terms of the GNU General Public License as published by\nthe Free Software Foundation, either version 3 of the License, or\n(at your option) any later version.\n\ncrypt-gtk is distributed in the hope that it will be useful,\nbut WITHOUT ANY WARRANTY; without even the implied warranty of\nMERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the\nGNU General Public License for more details.\n\nYou should have received a copy of the GNU General Public License\nalong with crypt-gtk.  If not, see <http://www.gnu.org/licenses/>.\n");
	gtk_dialog_run(GTK_DIALOG (dialog));
	gtk_widget_destroy(dialog);
}
```

If it helps, you can pick the latter apart yourself, it's only a few kB and can be found here: [http://www.placella.com/software/](http://www.placella.com/software/)

Peace

---

### Post by sandyd on 2010-03-19
thanks!

I was initally doing my program in GTK#, so I got confused about the signals, but now that I switched back to GTK+, It worked perfectly!

Thanks!

---

