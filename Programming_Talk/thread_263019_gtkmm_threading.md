---
title: "gtkmm threading"
date: 2006-09-22
forum: Programming Talk
---

### Post by MadMan2k on 2006-09-22
do you have some good tutorial about glib::thread and use with gtkmm?
I have a function which uses usleep a lot and also prints output to gtk::textview.
In order to make it not block the UI, I create a seperate thread for it, but sometimes it still locks the interface in a strange way, where there is no redraw any more but the events (button_clicked etc) are still cought.

I've got Glib::thread_init() in my main() and call the thread with:
Glib::Thread *const programm_thread = Glib::Thread::create(sigc::mem_fun(*this, &GtkAsuroFlash::Programm), false);

perhaps it has something to do with the fact that I dont call actual printing method with gobject.idle_add(), like I did during my python prototyping, since I could not find a gtkmm equvalent.

If someones willing to review the full code, Id post it, since its GPL anyway...

---

### Post by MadMan2k on 2006-09-23
push

---

