---
title: "[SOLVED] Beginner GTK - how do I add lines to a scrolling window widget?"
date: 2008-05-01
forum: Programming Talk
---

### Post by anewguy on 2008-05-01
I'm a very raw beginner at this, and very rusty at C, so please bear with me.  I have an application made up of many .C files and it currently runs in the command line.  I tried one of the tutorials but got stuck.  Someone helped me earlier with that problem, and someone helped me earlier Wednesday to declare and access a global widget.  Now I'm stuck again, and the darn tutorials just don't seem to have in them what I'm trying to do.  The current application, run from the command line, logs various status messages back to the command line window.  I want to instead write these messages (they are 1 line at a time, some with newline, some without (so I can overwrite an existing line).  In one of my earlier posts it was suggested I look into a viewport and a scrolling window.  I can't figure a viewport out to beat anything.  In my testing program, I have globally declared a scrolling window and packed into a vbox on the screen.  I at least see a scroll bar so that part I hope is working.  The callback function for a button press kicks off another .C file with the extern of the scrolling window in it.  Now, how can I write 1 line to that scrolling window each time I come through the callback function, and how do I tell it to scroll or not to scroll vertically?  I've thought maybe I need to add an input text area but mark it as not updatable, then in the callback function putting text in that widget.  I've got to tell you I've got no clue.  I want to buy the introduction book for GTK programming in C, but I'm on disability and until sometime I can save the spare money I have nowhere to go but online.  The tutorial at GTK I've been trying to use to understand the different types of widgets, but they lack an example of what I want to do (they only show filling a table with buttons, then packing that table into the scrolling window - a static application, whereas I need it to be dynamic).

I hope this makes some sense, and I really appreciate everyone taking time to answer all of my beginner's questions!  :)

---

### Post by RIchard James13 on 2008-05-01
I'm only just beginning this too. Previously I used Python and Glade.
Code to display text in a text view in a scrolled window
[PHP]int main(int argc, char *argv[])
{
	GtkWidget *window;
	gtk_init (&argc, &argv);
	GtkWidget *scrollview = gtk_scrolled_window_new( NULL, NULL );
	GtkWidget *textview = gtk_text_view_new();
	GtkTextBuffer *buffer;
	GtkWidget *avbox = gtk_vbox_new(FALSE, 0);
	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	GtkTextIter iter;
	buffer = gtk_text_view_get_buffer(GTK_TEXT_VIEW (textview));
	gtk_text_buffer_get_start_iter(buffer, &iter);
	
	g_signal_connect(G_OBJECT (window), "delete_event", G_CALLBACK (delete_event), NULL);
	g_signal_connect(G_OBJECT (window), "destroy", G_CALLBACK (destroy), NULL);
	gtk_window_set_default_size(GTK_WINDOW (window), 200, 200);
	
	gtk_container_add(GTK_CONTAINER (scrollview), textview);
	gtk_container_add(GTK_CONTAINER (avbox), scrollview);
	gtk_container_add(GTK_CONTAINER (window), avbox);
  	
	gtk_widget_show(textview);
	gtk_widget_show(scrollview);
	gtk_widget_show(avbox);
	gtk_widget_show(window);
	
	gtk_text_buffer_insert(buffer, &iter, "a line\n" , -1);
	gtk_text_buffer_insert(buffer, &iter, "another line\n" , -1);
	
	gtk_text_buffer_insert(buffer, &iter, "half a line :-" , -1);
	gtk_text_buffer_insert(buffer, &iter, ": the other half\n" , -1);
	
	

	gtk_main ();
	return 0;
}[/PHP]

A page that tells you how to use the GTKTextView [http://www.bravegnu.org/gtktext/]("http://www.bravegnu.org/gtktext/")

Basically what you need is four objects
1) A buffer this is where the text is stored
2) A text view this is what the buffer displays in
3) A scrolled window to give you scroll bars
4) A iter to enable you to insert text at different places

Once you have those four objects you can have text scrolling like in a terminal.

NOTE: using gtk the following code gives an error (actually it crashes)
[PHP]	GtkWidget *textview = gtk_text_view_new();
	buffer = gtk_text_view_get_buffer((GtkTextView *)textview);
[/PHP]
The correct way to convert between types is to use the gtk functions.
[PHP]	GtkWidget *textview = gtk_text_view_new();
	buffer = gtk_text_view_get_buffer(GTK_TEXT_VIEW (textview));
[/PHP]

---

### Post by anewguy on 2008-05-01
Thank you!!!!  Looks EXACTLY like what I need, and when I want to clear the text window I can just set the buffer to nothing.  Perfect!!

:):)

---

### Post by RIchard James13 on 2008-05-01
If you do clear the buffer make sure you reset the iter to the buffer start again, otherwise your program will probably crash.

---

