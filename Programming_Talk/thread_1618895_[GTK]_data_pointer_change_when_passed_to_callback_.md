---
title: "[GTK] data pointer change when passed to callback function"
date: 2010-11-11
forum: Programming Talk
---

### Post by liquidator87 on 2010-11-11
Hi, I'm doing some tests with GTK, I'm stuck with this problem:

Here's my code:

```

typedef struct
{
	...
} album_info;

static gboolean free_all(GtkWidget *window, gpointer data)
{
	album_info *info = data;
	printf("%p\n", info);	
	gtk_widget_destroy(window);
	return FALSE;
}

int main(int argc, char *argv[])
{
	album_info *info = malloc(sizeof(album_info));
	...
	GtkWidget *window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	printf("%p\n", (gpointer)info);
	g_signal_connect(window, "delete-event", G_CALLBACK(free_all), (gpointer) info);
	...
}

```

The result of the two printf should be the same, shouldn't it? 
It is different, so I'm not able to manipulate the data inside the callback function.
Am I missing something?

EDIT:

SOLVED: changed the callback definition to "static gboolean free_all(GtkWidget *window, GdkEventKey *e, gpointer data)"

---

### Post by nvteighen on 2010-11-11
Yes, that's a tricky part of GTK+ programming. Each signal has its own peculiar interface for callbacks. You should always take a look at the signal's entry on the GTK+ API docs (if you haven't, install devhelp from the repos and libgtk2.0-doc... it's very handy).

---

