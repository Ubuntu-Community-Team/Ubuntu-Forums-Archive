---
title: "[SOLVED] Beginner GTK &amp;amp; C - scrolling a text view"
date: 2008-05-07
forum: Programming Talk
---

### Post by anewguy on 2008-05-07
I have a common logging function called from various other functions in my first GTK attempt.  Everything works, but the text view doesn't scroll so the later output messages do not show unless you manually scroll.  I've been searching the net, and found this sample:

[http://search.cpan.org/src/ALEXE/gtk_new/share/gtk-2.0/demo/textscroll.c]("http://search.cpan.org/src/ALEXE/gtk_new/share/gtk-2.0/demo/textscroll.c")


When I try to pull from there what I think I need into my logging function, it looks like this:


#include <gtk/gtk.h>

extern     GtkTextBuffer *buffer;
extern     GtkTextView *textview;
extern     GtkTextIter *iter;
extern     GtkTextMark *mymark;


gboolean do_logmsg(char with_string[])

{
    char texttoshow[100];

    sprintf(texttoshow, with_string);

    buffer = gtk_text_view_get_buffer (textview);
        
    mymark = gtk_text_buffer_get_mark (buffer, "end");
    gtk_text_buffer_get_iter_at_mark (buffer, &iter, mymark);
    gtk_text_buffer_insert(buffer, &iter, texttoshow , -1);
    gtk_text_view_scroll_mark_onscreen (textview, mymark);

    while (gtk_events_pending ()) gtk_main_iteration();
    return 0;

}


I think have everything matching that sample page, but I get the following when I compile, which result in errors at run-time:


do_logmsg.c: In function ‘do_logmsg’:
do_logmsg.c:19: warning: passing argument 2 of ‘gtk_text_buffer_get_iter_at_mark’ from incompatible pointer type
do_logmsg.c:20: warning: passing argument 2 of ‘gtk_text_buffer_insert’ from incompatible pointer type


If I understand things correctly, the idea is to set a mark at the end of the text buffer that is aligned right, so all text is inserted ahead of the mark, then force a scroll to the mark.  I guess I don't understand the C syntax for the statements, nor do I see how, when the mark is set at the end before text is added, how it can scroll to the end after the text.

Any help on this would be greatly appreciated, as it's the only thing holding the application back (well, that and a "small" permissions problem on the USB device such that I have to run the app as root).

Thanks!!  :):)

---

### Post by MicahCarrick on 2008-05-07
Although I haven't tried, you could probably use gtk_text_buffer_get_end_iter() with gtk_text_view_scroll_to_iter()

---

### Post by anewguy on 2008-05-07
Hi, Micah, thanks for responding again.  Since I'm so new at this, I wonder if I'm maybe doing something wrong as well.  The text view is inside a scroll window, if that makes any difference.  I'll try what you suggested and post back.

Thanks again!  :)

---

### Post by anewguy on 2008-05-07
Okay, I tried this, and got the following error messages at run time.


#include <gtk/gtk.h>

extern     GtkTextBuffer *buffer;
extern     GtkTextView *textview;
extern     GtkTextIter *iter;
extern     GtkTextIter *enditer;


gboolean do_logmsg(char with_string[])

{
    char texttoshow[100];

    sprintf(texttoshow, with_string);

    buffer = gtk_text_view_get_buffer (textview);
        
    gtk_text_buffer_insert(buffer, iter, texttoshow , -1);
    gtk_text_buffer_get_end_iter(buffer, &enditer );
    gtk_text_view_scroll_to_iter(buffer, &enditer,0,1,0,0);
    while (gtk_events_pending ()) gtk_main_iteration();
    return 0;

}



(cvsdownload:4426): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators

(cvsdownload:4426): Gtk-CRITICAL **: gtk_text_buffer_insert: assertion `gtk_text_iter_get_buffer (iter) == buffer' failed

(cvsdownload:4426): Gtk-CRITICAL **: gtk_text_view_scroll_to_iter: assertion `GTK_IS_TEXT_VIEW (text_view)' failed

---

### Post by MicahCarrick on 2008-05-08
Here's a full example: _[Automatically scroll to end of GtkTextView]("http://www.gtkforums.com/about1307.html")_

---

### Post by kknd on 2008-05-08
Don't use GtkTextIter as a pointer!

The correct is:

GtkTextIter iter;
somFunction(&iter);

---

### Post by anewguy on 2008-05-08
Micah - thanks again for some input!  I'm thinking what I actually need to do is scroll the scroll window the text is in instead of the text view, but since I'm so new at this I'm going to your example first and see what I can do.  Again, thanks again for helping such a beginner out!

kknd - thanks for (excuse this, please) *pointing* that out!  :):)  

As you can see, I seem to remember squat about C (it's been 12 years!) so all of this input is so greatly appreciated!!  

Thanks again!! :):)

---

### Post by anewguy on 2008-05-08
Hey guys, I fixed my problem and now the entire thing works great!!  I had to add a GTKAdjustment  for the vertical scroll for the scrolled window, then get to the end.  I forgot to record which post on the internet I found this in, but it works great.  Here's the finished code for logging function:

#include <gtk/gtk.h>

extern     GtkTextBuffer *buffer;
extern     GtkWidget *textview;
extern     GtkTextIter iter;
extern     GtkTextIter enditer;
extern     GtkWidget *scrollview;
extern     GtkAdjustment *vadj;


gboolean do_logmsg(char with_string[])

{
    char texttoshow[100];

    sprintf(texttoshow, with_string);
    gtk_text_buffer_insert(buffer, &iter, texttoshow , -1);
    vadj = gtk_scrolled_window_get_vadjustment(GTK_SCROLLED_WINDOW(scrollview));
    gtk_adjustment_set_value(vadj, vadj->upper);
    gtk_scrolled_window_set_vadjustment(GTK_SCROLLED_WINDOW(scrollview), vadj);
    while (gtk_events_pending ()) gtk_main_iteration();
    return 0;

}


I'm so darn rusty at C I don't even know what half the stuff I see and copy even means anymore.  Pointers, pointers to pointers, structures, etc., could just as well be greek to me now.  I feel so ashamed.  :):)

Actually, even though it's true, I'm actually quite glad I just got the darn thing converted to use GTK so there is a GUI now.

Thanks to everyone for all your great help!!  :):):)

---

