---
title: "Help with structures and GTK+:  invalid uninstantiatable type `(null)' in cast"
date: 2008-11-06
forum: Programming Talk
---

### Post by mrMango on 2008-11-06
Hello all.

I'm rather new to GTK programming The Right Way(tm), as I tend to avoid structures and pointers in C like the plague. I'm designing an application for the maemo environmnet and I figured I'd do things properly this time, following the maemo tutorials. Right now it's not hildonized; I'll do that later.

The application uses glade to layout the interface. Interface data is stores in an AppUIData struct, which contains all of the GtkWidget definitions:

interface.h:
```
typedef struct _AppUIData AppUIData;
struct _AppUIData {

    /* Handle to the AppData */
    AppData *data;

    GtkWidget *window;
    GtkWidget *logview;
    GtkWidget *submitbutton;

};
```

interface.c contains a funciton which connects those definitions to the glade xml file.

interface.c:
```
AppUIData *interface_main_view_new( AppData *data ) {

    /* Zero memory with g_new0 */
    AppUIData* result = g_new0( AppUIData, 1 );

    /* Initialize interface data */
    /* Store handle to app's data to view's data */
    result->data = data;

    result->window = glade_xml_get_widget(result->data->gxml, "window");
    result->logview = glade_xml_get_widget(result->data->gxml, "logview");
    result->submitbutton = glade_xml_get_widget(result->data->gxml, "submitbutton");

    return result;
}
```

Essentially what I'm trying to do is have it so I click a button and text shows up in the GtkTextView logview. main.c connects the button to the callback.

main.c:
```
int main (int argc, char *argv[])
{
 	AppData *data;
	AppUIData *main_view;

	gtk_set_locale ();
	gtk_init (&argc, &argv);

	data = create_data();
	main_view = interface_main_view_new (data);

	glade_xml_signal_autoconnect( data->gxml );
	g_signal_connect( G_OBJECT(main_view->window), "delete_event", gtk_main_quit, NULL );

	g_signal_connect( G_OBJECT(main_view->submitbutton), "clicked", G_CALLBACK(testlog), main_view );

	gtk_widget_show( GTK_WIDGET(main_view->window) );
	gtk_main ();

	interface_main_view_destroy (main_view);
	destroy_data (data);

	exit(0);
}
```

And finally, the callback itself:

```
void testlog(AppUIData *appuidata) {
	logit("Testing", appuidata->logview);
}

void logit(char *string, GtkTextView *textview) {
	GtkTextIter iter;
	GtkTextBuffer *buffer;

	buffer = gtk_text_view_get_buffer(GTK_TEXT_VIEW(textview));
	gtk_text_buffer_get_end_iter(buffer, &iter);

	gtk_text_buffer_insert(buffer, &iter, string, -1);

	gtk_text_view_scroll_mark_onscreen(GTK_TEXT_VIEW(textview), gtk_text_buffer_get_insert(buffer));
}
```

When I click the submit button in the UI, something happens. It's obviously trying to run the logit function, but I get this:
```

(nokia_eel:26013): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkTextView'

(nokia_eel:26013): Gtk-CRITICAL **: gtk_text_view_get_buffer: assertion `GTK_IS_TEXT_VIEW (text_view)' failed

(nokia_eel:26013): Gtk-CRITICAL **: gtk_text_buffer_get_end_iter: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(nokia_eel:26013): Gtk-CRITICAL **: gtk_text_buffer_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(nokia_eel:26013): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(nokia_eel:26013): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkTextView'

(nokia_eel:26013): Gtk-CRITICAL **: gtk_text_view_scroll_mark_onscreen: assertion `GTK_IS_TEXT_VIEW (text_view)' failed
```

Now I'm pretty sure I screwed up a pointer or something somewhere, because that's typically where I screw things up, but I can't seem to find it. Any insight?

Edit: see post #3 for updated code.

---

### Post by nvteighen on 2008-11-06
> **mrMango said:**
> 
interface.h:
```
typedef struct _AppUIData AppUIData;
struct _AppUIData {

    /* Handle to the AppData */
    AppData *data;

    GtkWidget *window;
    **GtkWidget *logview;**
    GtkWidget *submitbutton;

};
```

(...)

And finally, the callback itself:

```
void testlog(AppUIData *appuidata) {
	logit("Testing", **appuidata->logview**);
}

void logit(char *string, **GtkTextView *textview**) {
	GtkTextIter iter;
	GtkTextBuffer *buffer;

	buffer = gtk_text_view_get_buffer(GTK_TEXT_VIEW(textview));
	gtk_text_buffer_get_end_iter(buffer, &iter);

	gtk_text_buffer_insert(buffer, &iter, string, -1);

	gtk_text_view_scroll_mark_onscreen(GTK_TEXT_VIEW(textview), gtk_text_buffer_get_insert(buffer));
}
```


I guess your problem is rather casting, not pointers. Let's see.

You have a certain GtkTextView widget declared in the AppUIData structure, as it should, as a GtkWidget. Perfect.

Then, you're logit() function needs a GtkTextView as argument... but you pass from testlog() you pass appuidata->logview, which is a GtkWidget! And after having passed the variable with mismatched data type (possibly corrupted, as C will do an implicit regular cast), you cast it with GTK_TEXT_VIEW...

There is one solution: consistency. And two ways to achieve the same.

Alternative 1 (the easiest, but not the best): Change testlog()'s textview argument data type to GtkWidget.

Alternative 2 (the best): Keep it as GtkTextView, delete all GTK_TEXT_VIEW inside testlog() and use that cast only on logit() when passing the GtkWidget as argument.

Why is alt. 2 better than 1? Because it keeps a transparent interface for testlog(). If you go by using GtkWidget, you'll be legally allowed to pass a GtkWindow and the only way to know why it's failing will be looking at the implementation. Alternative 2 allows you to catch possible failures just looking at the interface the function provides, not caring how it works.

(This is IMO the only advantage static typing has over dynamic... transparent APIs. Of course, dynamic typed languages aim towards genericity and things are different...)

---

### Post by mrMango on 2008-11-06
Thanks for your quick reply. I originally had the code that way, and changed some things around to try and get it to work.

I've changed the code to this:

```
void testlog(AppUIData *appuidata) {
	logit("Testing", GTK_TEXT_VIEW(appuidata->logview));
}

void logit(char *string, GtkTextView *textview) {
	GtkTextIter iter;
	GtkTextBuffer *buffer;

	buffer = gtk_text_view_get_buffer(textview);
	gtk_text_buffer_get_end_iter(buffer, &iter);

	gtk_text_buffer_insert(buffer, &iter, string, -1);

	gtk_text_view_scroll_mark_onscreen(textview, gtk_text_buffer_get_insert(buffer));	
}
```

And the errors still remain:

```
(nokia_eel:7683): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkTextView'

(nokia_eel:7683): Gtk-CRITICAL **: gtk_text_view_get_buffer: assertion `GTK_IS_TEXT_VIEW (text_view)' failed

(nokia_eel:7683): Gtk-CRITICAL **: gtk_text_buffer_get_end_iter: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(nokia_eel:7683): Gtk-CRITICAL **: gtk_text_buffer_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(nokia_eel:7683): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(nokia_eel:7683): Gtk-CRITICAL **: gtk_text_view_scroll_mark_onscreen: assertion `GTK_IS_TEXT_VIEW (text_view)' failed

```

These are, of course, runtime errors. There are no errors or warnings compile-time.

---

### Post by nvteighen on 2008-11-07
Oh, right... Now I'm sure I've catched the error.

You're actually never creating your GtkTextBuffer... you just declare a pointer of that type, but never actual data that pointer points to. Think of an arrow labeled "New York" that's pointing to a void space.

To create a GtkTextBuffer, use this:
```

GtkTextBuffer *my_buffer = gtk_text_buffer_new(NULL);

```

The gtk_text_buffer_new() function uses an argument... refer to the GTK+ API docs, but usually you use NULL.

Don't forget to gtk_widget_destroy() the GtkTextBuffer... Any widget created from a gtk_*_new() function should be passed through the destroyer to avoid memory leaks.

---

### Post by mrMango on 2008-11-07
Well, I'm not sure why this is, but that wasn't the solution. I overlooked something that I should have known from my previous programs: I got the format of my G_CALLBACK function wrong.

g_signal_connect passes a gpointer to my function, therefore my function should accept a gpointer type. Essentially, I made it look like this:

```
void testlog(GtkButton *button, gpointer user_data);
```

And the actual function like this:

```
void testlog(GtkButton *button, gpointer user_data) {
	AppUIData* data = user_data;
	logit("Testing\n", GTK_TEXT_VIEW(data->logview));
}
```

That makes all the errors go away and the function actually works now.

---

### Post by nvteighen on 2008-11-08
> **mrMango said:**
> Well, I'm not sure why this is, but that wasn't the solution. I overlooked something that I should have known from my previous programs: I got the format of my G_CALLBACK function wrong.

g_signal_connect passes a gpointer to my function, therefore my function should accept a gpointer type. Essentially, I made it look like this:

```
void testlog(GtkButton *button, gpointer user_data);
```

And the actual function like this:

```
void testlog(GtkButton *button, gpointer user_data) {
	AppUIData* data = user_data;
	logit("Testing\n", GTK_TEXT_VIEW(data->logview));
}
```

That makes all the errors go away and the function actually works now.
Wow... I also overlooked it.

I've always thought the G_CALLBACK system is a bit weird.

---

