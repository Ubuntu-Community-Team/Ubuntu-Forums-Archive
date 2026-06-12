---
title: "[Gtk] How to get the window deiconify event?"
date: 2012-12-18
forum: Programming Talk
---

### Post by bird1500 on 2012-12-18
Hi,
There are methods for Iconifying and deiconifying a window, but there are no signals to get these events.
I found [here how to get the iconify]("http://cubicarch.wordpress.com/2012/06/11/hide-minimized-window-cgtkmm/") event, but how do I get the deiconify event?

EDIT:
[PHP]
bool
Window::stateEvent(GdkEventWindowState *pEvent) {
    const int state = pEvent->new_window_state;
    const int changed = pEvent->changed_mask;
    
    if(changed & GDK_WINDOW_STATE_ICONIFIED) {
        if(state & GDK_WINDOW_STATE_ICONIFIED) {
            printf("iconified\n");
        } else {
            printf("deiconified\n");
        }
    }
    
    return false;
}
[/PHP]

---

