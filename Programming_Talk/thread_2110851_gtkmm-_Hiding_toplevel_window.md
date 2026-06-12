---
title: "gtkmm- Hiding toplevel window"
date: 2013-01-31
forum: Programming Talk
---

### Post by KatiePoint on 2013-01-31
I am a new programmer, new to this forum and new to gtkmm. 
I have created an application that goes through a bunch of windows where the user must fill out fields etc all using gtkmm. I am able to hide all the other windows when I move from window to window. Except the main/ toplevel window which always stays open and if I try to hide() closes the entire program.

Any help is appreciated, thanks in advance.

---

### Post by raja.genupula on 2013-01-31
what comes to mean for top level window , explain more please

---

### Post by howefield on 2013-01-31
Thread moved to the "*Programming Talk*" forum.

---

### Post by KatiePoint on 2013-01-31
It is the first window I open. So in main when I run the "window"

Gtk::Main::run(window);

---

### Post by raja.genupula on 2013-01-31
Yeah it seems like , your program will start with opening that window.

---

### Post by bird1500 on 2013-01-31
There are 2 ways to display the toplevel window:
1) The old way, with Gtk::Main::run(window)
2) The new way, with Gtk::Application::run(window)

I'm giving an example with the latter one since they require different approaches and the latter one is the preferred one. This sample app will hide the toplevel window the first 3 times you click on "close" and the 4th time the app will exit completely.

main.cpp
[PHP]
#include "Win.h"

int
main(int argc, char *argv[])
{
    Glib::RefPtr<Gtk::Application> app = Gtk::Application::create(argc, argv,
        "com.your.appName");
    Win win(app);
    app->run(win);
    return 0;
}
[/PHP]Win.h:
[PHP]
#ifndef WIN_H
#define WIN_H

#include <gtkmm.h>

class Win : public Gtk::Window
{
public:
    Win(const Glib::RefPtr<Gtk::Application> &a);
    virtual ~Win() {}
    
    bool
    toggleVisibility();
    
    virtual bool
    windowClosing(GdkEventAny*);
    
private:
    const Glib::RefPtr<Gtk::Application> &app;
};


#endif

[/PHP]Win.cpp:
[PHP]
#include "Win.h"
#include <pthread.h>

Win::Win(const Glib::RefPtr<Gtk::Application> &a) : app(a)
{
    set_default_size(600, 400);
    signal_delete_event().connect(sigc::mem_fun(*this,
        &Win::windowClosing));
    show_all();
}

void*
showUpAgain(void *obj)
{
    pthread_detach(pthread_self());
    sleep(2);
    Win *p = (Win*)obj;
    /*using pthreads and calling toggleVisibility() directly
    from the pthread
    since Glib::signal_idle(..) doesn't work - blocks the system,
    probably because of app->hold()
    */
    p->toggleVisibility();
    return NULL;
}

bool
Win::windowClosing(GdkEventAny *pEvent)
{
    toggleVisibility();
    
    //exit completely after a few close requests
    static int count = 0;
    count++;
    if(count > 3) {
        app->quit();
    }
    
    pthread_t thread;
    pthread_create(&thread, NULL, showUpAgain, this);
    return true;
}

bool
Win::toggleVisibility()
{
    if(get_visible()) {
        app->hold();
        hide();
    } else {
        set_visible();
    }
    
    return false;
}
[/PHP]

---

