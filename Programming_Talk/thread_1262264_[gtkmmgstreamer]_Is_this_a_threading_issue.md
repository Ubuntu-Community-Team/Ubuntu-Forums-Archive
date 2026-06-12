---
title: "[gtkmm/gstreamer] Is this a threading issue?"
date: 2009-09-09
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2009-09-09
Hi I am developing a media player app using gtkmm and gstreamer. Unfortunately it isn't yet in a state for sources to be released. I am encountering a problem and I can't seem to solve it. Furthermore this problem is somewhat random. The code occasionally works as it should, but most of the time it crashes. This code is called after a series of signals/callbacks. I'll attempt to explain:

main_window class is a class derived from Gtk::Window
Playfile class is my own custom class, it isn't based on any widget, it just uses libsigc for signals

In Playfile I connect a gstreamer callback to a method of Playfile which is static. When this method is called, it is passed a pointer to the instance of Playfile. I use this pointer to call another method of Playfile(needed to access the instance's vars). This method, does some work and finally it emits a signal. This signal is catched by a method in the main_window instance. Then in that method I create a Gtk::MessageDialog. But when I try to run() it the app crashes(most of the time). 
To sum up it looks something like this:
> gstreamer emits signal-> static Playfile::on_g_signal-> Playfile::handle_signal-> main_window::display_msg_dialog-> crash

The only error I get in the console is this:

> media_player: ../../src/xcb_io.c:176: process_responses: Assertion `!(req && current_request && !(((long) (req->sequence) - (long) (current_request)) <= 0))' failed.


media_player is the name of the app.

I know that I haven't given you any code, but do you have any idea what is happening? Since it sometimes works, I suspect that this is a threading issue(in gtkmm/gtk or gstreamer). I don't use threads, the app is single threaded. Do you have any suggestions on what to do?

---

### Post by SledgeHammer_999 on 2009-09-09
after some serious thought and searching I think I found a clue. The initial callback is being called in the pipeline thread context(gstreamer), so all subsequent calls are made in the pipeline thread context. Maybe this is the culprit for my problem. 

I want to test it but I don't know how. How do I execute(from inside the callback) a method/function in my program in gtkmm's thread context?
(sorry I am not familiar with the terminology).

---

### Post by jaalburquerque on 2009-09-10
Have you tried running through a debugger?  It could give you clues as to what is actually going on.

---

### Post by SledgeHammer_999 on 2009-09-10
> **jaalburquerque said:**
> Have you tried running through a debugger?  It could give you clues as to what is actually going on.

Unfortunately I don't know how to use a debugger(don't hit me).

Anyways, I solved it using a Glib::Dispatcher. So now the calls should be something like this:

> **pipeline thread context**gstreamer emits signal-> static Playfile::on_g_signal-> Glib::Dispatcher.emit()->**application thread context**Playfile::handle_signal-> main_window::display_msg_dialog-> Gtk::Messagedialog works!

---

### Post by dwhitney67 on 2009-09-10
A little advice; signal callbacks should perform limited actions so that the processing time spent within them is quick.  If you are in the middle of handling a signal, and another signal is delivered, the results could lead an app to crash.

From your OP, I understand that the signal handler needs to access the Playfile object; this is fine, however consider only setting a semaphore to indicate that the signal has been received.  The Playfile object should detect that the semaphore is set, and perform any special processing within its own thread.

Anyhow, your last post indicates that you have resolved the issue.  So I guess you are looking onward to other challenges.

---

