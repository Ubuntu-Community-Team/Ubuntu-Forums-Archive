---
title: "Libnotify problem"
date: 2008-05-14
forum: Programming Talk
---

### Post by nomexous on 2008-05-14
I've recently picked up C++ as a hobby, and set off on my first project. I'm creating a program that will pop up a notification from the tray, displaying how many days, hours, and minutes are left until the next episode of my favorite television series.

Using the MonoDevelop IDE, the program compiles just fine. But when the notification pops up, it's either pointing to a widget in a completely unrelated window, or partially off screen. I can't figure out whether or not it's a libnotify bug, or a mistake I made.

To compile, I needed to retrieve libnotify-dev from the package manager.

File: bones.cpp```
#include <iostream>
#include <gtk/gtk.h>
#include <libnotify/notify.h>

static void destroy_window(GtkWidget *widget, gpointer pointer)
{
	notify_uninit();
	gtk_main_quit();
}

static void click_tray(GtkStatusIcon *StatusIcon, gpointer *data)
{
	notify_uninit();
	gtk_main_quit();
}
 
int main(int argc, char *argv[])
{
	notify_init("bones");
	GtkWidget *window;
	gtk_init(&argc, &argv);
	
	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_window_set_icon_from_file(GTK_WINDOW(window), "/path/to/logo.png", NULL);
	gtk_window_set_title(GTK_WINDOW(window), "Bones");
	gtk_window_set_default_size(GTK_WINDOW(window), 200, 50);
	g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(destroy_window), NULL);
	gtk_container_add(GTK_CONTAINER(window), gtk_label_new("I don't know what that means."));
	gtk_widget_show_all(window);
	
	GtkStatusIcon *tray_icon;
	tray_icon = gtk_status_icon_new_from_file("/path/to/logo.png");
	g_signal_connect(tray_icon, "activate", G_CALLBACK(click_tray), NULL);
	gtk_status_icon_set_tooltip(tray_icon, "Bones");
	gtk_status_icon_set_visible(tray_icon, TRUE);
	
	NotifyNotification *popup;
	popup = notify_notification_new_with_status_icon("Bones", "Testing", "/path/to/logo.png", tray_icon);
	notify_notification_show(popup, NULL);
	
	gtk_main();
	
	return 0;
}

```Other applications seem to be able to use libnotify in this manner just fine. Why is mine messing up?

---

