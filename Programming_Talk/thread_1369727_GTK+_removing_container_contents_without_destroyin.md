---
title: "GTK+ removing container contents without destroying it"
date: 2010-01-01
forum: Programming Talk
---

### Post by bluedalmatian on 2010-01-01
Im trying to write an app whereby the contents of a vbox is changed whilst the program is running.

Ive written a set of functions which displays 'pages' of widgets in the vbox.

The first time each function is called it works fine, but the second time each one is called nothing is displayed. I can only assume its because when

 gtk_container_remove (GTK_CONTAINER (rightpanescrollview),gtk_bin_get_child(GTK_BIN(rightpanescrollview))); is called, the contents are destroyed even though Ive called gtk_widget_ref(generalpage) which I thought prevented that.

The complete, relativly short function is as follows:

```

void showGeneralPage()
{
	g_print("Showing General Page\n");
	if (generalpageinitialised==false)  //first time this func is called read widgets from glade
	{
		generalpage= glade_xml_get_widget(generalpagexml,"mainvbox");
		glade_xml_signal_autoconnect(generalpagexml);
		generalpageinitialised=true;
		gtk_widget_ref(generalpage);
		
	}


	if (pagedisplayed!="INIT") //will be INIT if no previous page was shown -app is just starting up
	{
	    
	    //remove previous 'page'
	  
	    gtk_container_remove (GTK_CONTAINER (rightpanescrollview),gtk_bin_get_child(GTK_BIN(rightpanescrollview)));
	  
	}
	
        pagedisplayed = "General";

	gtk_scrolled_window_add_with_viewport(GTK_SCROLLED_WINDOW(rightpanescrollview),GTK_WIDGET(generalpage));
	
	gtk_widget_show_all(GTK_WIDGET(generalpage));
}

```

As I say the first time this function is called it shows fine. Second time, nothing.

---

### Post by steeleyuk on 2010-01-01
Could you not use the hide_all function and [show_all]("http://library.gnome.org/devel/gtk/unstable/GtkWidget.html#gtk-widget-show-all") function for re-displaying them?

---

