---
title: "Am I using threads in GTK correctly?"
date: 2009-11-23
forum: Programming Talk
---

### Post by froggyswamp on 2009-11-23
Folks I'm learning using threads with Gtk, please have a look at my snippet if I'm doing something wrong. The snippet basically modifies the button label from another thread.

```

#include <gtk/gtk.h>

void run_thread(gpointer widget) {
	gdk_threads_enter();
	
	static int counter = 0;
	const gchar *label = gtk_button_get_label(GTK_BUTTON(widget));
	gchar *new_label = g_strdup_printf("%s %d", label, counter++);
	gtk_button_set_label(GTK_BUTTON(widget), new_label);
	printf("set label from other thread to: %s\n", new_label);
	g_free(new_label);
	
	gdk_threads_leave();
}

void button_clicked(GtkWidget *widget, gpointer data) {
	GError *err;
	GThread *th = g_thread_create((GThreadFunc)run_thread, widget, TRUE, &err);
	if(th == NULL) {
		printf("Error :%s\n", err->message);
		g_error_free(err);
	}
}

int main(int argc, char **argv) {
	gtk_init(&argc, &argv);
	
	if(!g_thread_supported()) {
		g_thread_init(NULL);
		gdk_threads_init();
	}
	
	GtkWidget *window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	g_signal_connect(G_OBJECT(window), "destroy", gtk_main_quit, NULL);
	gtk_widget_set_size_request(window, 200, 200);
	GtkWidget *button = gtk_button_new_with_label("Button");
	g_signal_connect(G_OBJECT(button), "clicked", G_CALLBACK(button_clicked), "button1");
	
	gtk_container_add(GTK_CONTAINER(window), button);
	gtk_widget_show_all(window);
	
	gdk_threads_enter();
	gtk_main();
	gdk_threads_leave();
}

```

---

### Post by doas777 on 2009-11-23
it has always been my understanding that you should only modify objects within the thread upon which they were created. never tried threading with gtk/C before though. it may simply be a matter of lock and synch.

good luck

---

