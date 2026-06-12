---
title: "[SOLVED] Beginning GTK and C - textview buffer"
date: 2008-05-04
forum: Programming Talk
---

### Post by anewguy on 2008-05-04
Thanks to everyone who has gotten me this far on this very beginner's project.  I still have one little thing I can't figure out - when "writing" lines into a textview buffer, nothing is showing in the buffer.  This "writing" takes place in the following function:

#include <gtk/gtk.h>

extern     GtkTextBuffer *buffer;
extern     GtkTextIter iter;
extern     gboolean   downloading;
extern     gint linenum;


gboolean do_logmsg(char with_string[])

{
    char texttoshow[100];

    sprintf(texttoshow, with_string);
        
    gtk_text_buffer_insert(buffer, &iter, texttoshow , -1);
    return 0;

}

Note that the textview, buffer and scrollbox are defined in a calling function and appear on the screen fine.  Nothing shows in the scroll box until the CALLING function exits.

I tried adding the a widget show after the gtk call, but then I get GTK assertion errors on every call to the above function.

I know I've got to be doing something stupid - can someone tell me what??

Thanks in advance!!  :)

---

### Post by kknd on 2008-05-04
If you want to update the GUI inside other procedures, try to do a while(gtk_events_pending()) gtk_main_iteration();

else,

Its hard to tell without the full sources, but try this (without close callback, to be quick):

[PHP]
#include <gtk/gtk.h>

/* I didn't read right the post at the first time, sorry. This snipped is useless */ 

int main(int argc, char* argv[])
{
	gtk_init(&argc, &argv);

	GtkWidget* window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	GtkWidget* view	  = gtk_text_view_new();
	GtkTextBuffer* buffer = gtk_text_view_get_buffer(GTK_TEXT_VIEW(view));
	GtkTextIter end;

	gtk_text_buffer_get_end_iter(buffer, &end);
	gtk_text_buffer_insert(buffer, &end, "Hello ubuntuforums", -1);
	gtk_container_add(GTK_CONTAINER(window), view);
	gtk_widget_show_all(window);

	gtk_main();

	return 0;
}
[/PHP]

---

### Post by anewguy on 2008-05-04
Thanks for the reply.  It's interesting - it doesn't want to show ANY text in the text view until the return from the call out function (which in turn calls many functions, which in turn call the code above).  I added shows of the scrolled window, the textview it's in, the vbox the text view is in, and of the window, but none (even all) showed anything.

I'm starting to wonder if there is some sort of "force" option required somewhere to get it to update the screen immediately.  I thought my testing had shown this to work before I started changing all of this program, but when I think back on it, I don't think there was anyway to tell in my testing either that it had exited the call back function before it displayed anything.

Help??!!  :):):):)

---

### Post by RIchard James13 on 2008-05-05
Stupid explanation 1

You are adding the text to the textbuffer before gtk main is called and thus it is not displayed.

Question; how do you add text after gtk main is called?

Normally in an event driven program a user might say click on a button and control is returned to the program from the GUI. That click is called an event and in GTK you use the g_signal_connect to connect a button to a function so the event is taken care of.

If you are reading text from a file the user is not pressing a button to update that view so you need a different type of event.

Answer many GUI type systems enable you to trigger events based on timers.
g_timeout_add (msecs, function, pointer_arg)
is from glib and should solve the problem if your problem is what I think it is.

---

### Post by anewguy on 2008-05-05
> **RIchard James13 said:**
> Stupid explanation 1

You are adding the text to the textbuffer before gtk main is called and thus it is not displayed.

Question; how do you add text after gtk main is called?

Normally in an event driven program a user might say click on a button and control is returned to the program from the GUI. That click is called an event and in GTK you use the g_signal_connect to connect a button to a function so the event is taken care of.

If you are reading text from a file the user is not pressing a button to update that view so you need a different type of event.

Answer many GUI type systems enable you to trigger events based on timers.
g_timeout_add (msecs, function, pointer_arg)
is from glib and should solve the problem if your problem is what I think it is.

Actually, I'm writing to the text buffer after gtk_main() has been called and the main function exited.  What happens is this:  a user plugs a modified CVS one-time use digital camcorder or digital still camera into a usb port.  They click a button on the GUI, and goes to routines that open and claim the usb device, unlock the camera with a key, download the movie(s) or picture(s) and then closes the device and eventually returns back and out of the call out function.  Along the way, various status messages are issued.  This was a purely command line program, but I'm trying to change it so it has a GUI'd front end without doing much other changing.

I made this same post to a GTK forum and got the following back from Micah, which it turns out does the trick for what I needed now:

while (gtk_events_pending ()) gtk_main_iteration();

This was added in the log message routine just after the update of the buffer.

My simple understanding at this point in time is that while the writes have been made to the buffer, but are not showing since no return to main has been made yet (I think that's what gtk_events_pending is doing) then it makes a pass through main so the screen is updated.  Since the screen is updated - no more pending events, so it's kind of a one-shot deal everytime I write a "line" (technically with newline I think it's called a paragragh in GTK) to the buffer.  Works great for what I am doing.

Thanks for all the great help!!  I never would have gotten anywhere without you guys helping me out and tolerating a very beginner at all of this!!  :):)

EDIT: Just re-read the thread and noticed that kknd recommended this same thing right away - I just missed it!  Thanks kknd!!

---

### Post by anewguy on 2008-05-07
Okay, now that that part works, can someone help me with making the textview scroll?  I have tried the set mark and scroll to mark calls I have found on the web, but I keep getting type mismatches at compile time which I don't understand.  Can someone explain this to me in some pretty simple language?  Do I need to define and set the mark initially in main() before manipulating it in other functions?

Thank you!  :)

---

### Post by kknd on 2008-05-07
In a  chat client that I've done, I make the textview to always show the last text (scroll to it) manipulating the "vajustment" property of the GtkScrolledWindow.

The snippet in Lua:

[PHP]
vadj = scroll:get("vadjustment")

and

---
-- Callback for vLog[size-allocate]
function Client:vLogCallback()
	local tmp = self.vadj:get("upper") - self.vadj:get("page-size")
	self.vadj:set("value", tmp)
end
[/PHP]

In C, the logic is the same.

---

### Post by anewguy on 2008-05-07
> **kknd said:**
> In a  chat client that I've done, I make the textview to always show the last text (scroll to it) manipulating the "vajustment" property of the GtkScrolledWindow.

The snippet in Lua:

[PHP]
vadj = scroll:get("vadjustment")

and

---
-- Callback for vLog[size-allocate]
function Client:vLogCallback()
	local tmp = self.vadj:get("upper") - self.vadj:get("page-size")
	self.vadj:set("value", tmp)
end
[/PHP]

In C, the logic is the same.

I'm such a beginner at this and SO rusty in C, could you give me a sample in C that I might be able to follow?  

Thanks!:):)

---

