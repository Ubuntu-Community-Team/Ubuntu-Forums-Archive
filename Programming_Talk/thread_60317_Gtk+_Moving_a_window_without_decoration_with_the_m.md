---
title: "Gtk+: Moving a window without decoration with the mouse"
date: 2005-08-27
forum: Programming Talk
---

### Post by tommie-lie on 2005-08-27
Hi,

Some of you may know Windows applications with windows that don't have any border, but you can "grab" them by clicking somehwere in the window. For instance, winamp behaves this way, along with other multimedia applications.

I want to create such a window with Gtk+ (Gtkmm, to be exact) under Linux. I can remove the window decoration without any problem Gtk::window->set_decorated(false) does the job. However, moving the window does not work as I would expect it. Is attached two event handlers, one for the mouse button click event and one for the pointer motion event. The handlers look like this:
```
bool MainWindow::on_button_press_event(GdkEventButton *button)
{
        if (button->button == 1) {
                // set initial mouse position (relative to the widget)
                this->last_x = button->x;
                this->last_y = button->y;
                return true;
        }
        return false;
}

bool MainWindow::on_motion_notify_event(GdkEventMotion *motion)
{
        if ((motion->state & Gdk::BUTTON1_MASK) == Gdk::BUTTON1_MASK) {
                int cur_pos_x, cur_pos_y;

                this->get_position(cur_pos_x, cur_pos_y);
                this->move(cur_pos_x + (motion->x - this->last_x), cur_pos_y + (motion->y - this->last_y));

                return false;
        }
        return false;
}
```On pointer movement, I simply check if the first mouse button is pressed and, if this is the case, calculate the pointer movement difference and move the window by this difference. I would expect this to work fine, as I did such things under Windows with the exact same approach, but it does not. If I move the mouse slowly, the window seems to follow, but the longer I drag the window, the more unstable becomes the movement of the window (kind of "loses track"). If I move the mouse fast, the window becomes unstable almost immediately. This "instability" in movement goes that far that the window seems to become crazy, gonig backwards and jumps to weird positions where my mouse never was.

I hope some of you find some fatal mistake of mine or something else that I overlooked.

Thanks in advance
Thomas

---

### Post by Tiede on 2005-08-27
There is already such a feature in GTK+.. The Alt button. Hold it donwn, left click anywehre on the window and drag...

---

### Post by doclivingston on 2005-08-27
Some additional information that may be helpful, in addition to what Tiede said:

* The modifier (which is Alt by default) can be changed in gconf - the key is /apps/metacity/general/mouse_button_modifier.
* Using that modifier with the left mouse button lets you move windows, the right mouse button gives you the "window menu" and the third (middle) button is resize.


The problem with your code is probably that window->x (and y) are relative to the window, which you are moving. Try using x_root and y_root instead, they are relative to the screen.

---

### Post by tommie-lie on 2005-08-29
> **Tiede]There is already such a feature in GTK+.. The Alt button. Hold it donwn, left click anywehre on the window and drag...[/QUOTE]This is not a Gtk+ feature, but a feature of metacity, and I am well aware of such things. I also know what you want me to tell with that: Don't change standard behaviour of windows or you will burn in hell!  said:**
> Try using x_root and y_root instead, they are relative to the screen.Thanks, but using *_root does not work, either.

I logged the coordinates of the window as they should be and as they are after the call to move() to stdout like this:
```
this->get_position(wCur_x, wCur_y);
std::cout << wCur_x + delta_x << " - " << wCur_y + delta_y << "\n";

this->move(wCur_x + delta_x, wCur_y + delta_y);

this->get_position(wCur_x, wCur_y);
std::cout << wCur_x << " - " << wCur_y << "\n";

std::cout << "----------\n";
```(With delta_* being the amount of pixels I wnat to move the window)
And found this interesting behaviour:```
4 - 54
3 - 53
----------
4 - 54
4 - 54
----------
5 - 55
4 - 54
----------
4 - 54
4 - 54
----------
5 - 55
4 - 54
----------

```It seems as if the call to move() does not always work, as the calculated position before setting it sometimes differ from the actual position after the call to move().
Maybe this is part of the problem?

---

