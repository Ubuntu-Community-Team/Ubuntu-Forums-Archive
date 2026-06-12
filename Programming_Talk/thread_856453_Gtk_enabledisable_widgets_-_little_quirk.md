---
title: "Gtk enable/disable widgets - little quirk"
date: 2008-07-11
forum: Programming Talk
---

### Post by pcman312 on 2008-07-11
I have an application that has an "Export" functionality where it brings up a file dialog box to select the filename and location, etc etc. The details of what is being exported isn't important. What is important is that I have it set so most of the widgets in the window are disabled while exporting (with a little status message on the bottom of the window) and then reenabled when the export is complete. Right now, the functionality works perfectly, however sometimes the GUI doesn't seem to update and show the widgets as back to enabled until I perform certain types of user input (as far as I can tell, only using the scrolling window, the only other user input is 3 buttons and a small menu bar). It's a strange quirk that I haven't entirely figured out yet.

The export function is being run in a separate thread, and I am relatively new to GUI programming, specifically around multithreading in a GUI. However, I am well versed in programming overall, just not multithreading very much.

---

### Post by cdekter on 2008-07-13
Not sure what language you're using, however this applies to C, C++ and Python:

Are you calling gdk_threads_init() before calling gtk_main()? This is absolutely essential for any gtk application where you are doing anything outside the main thread. 

Additionally, in your background thread doing the export work, if you're making the call to re-enable the GUI components from this background thread, you'll need to use gdk_thread_enter() and gdk_threads_leave() for that section.

---

### Post by pcman312 on 2008-07-15
Yes, I do have the gtk_thread stuff in (and I'm writing this as a mix of C/C++). I have the init calls in my main:

```
int main(int argc, char **argv)
{
	g_thread_init(NULL);
	gdk_threads_init();
	gtk_init(&argc, &argv);

	// Do other things, not related

	setupGUI();

	gtk_main();

	return 0;
}
```

and I have two functions *disableWindow()* and *enableWindow()* which are:

Note: I am using glade, although I doubt that there is an issue here
```
void enableWindow()
{
	gdk_threads_enter();
	GtkWidget* widget;

	widget = glade_xml_get_widget(xml, "menubar2");
	gtk_widget_set_sensitive(widget, true);
	widget = glade_xml_get_widget(xml, "hbuttonbox1");
	gtk_widget_set_sensitive(widget, true);
	widget = glade_xml_get_widget(xml, "notebook");
	gtk_widget_set_sensitive(widget, true);
	gdk_threads_leave();
}

void disableWindow()
{
	gdk_threads_enter();
	GtkWidget* widget;

	widget = glade_xml_get_widget(xml, "menubar2");
	gtk_widget_set_sensitive(widget, false);
	widget = glade_xml_get_widget(xml, "hbuttonbox1");
	gtk_widget_set_sensitive(widget, false);
	widget = glade_xml_get_widget(xml, "notebook");
	gtk_widget_set_sensitive(widget, false);
	gdk_threads_leave();
}
```

---

