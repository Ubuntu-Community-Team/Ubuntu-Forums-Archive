---
title: "[gtk] Custom widget with multiple gdk windows?"
date: 2009-03-21
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2009-03-21
Is there any tutorial/example on how to create a widget with more than one gdk windows? I've been successful to create 2 windows but only the one is shown!

Can you give some example code?
or can you point me to an official gtkwidget that creates and manages multiple gdkwindows?(straight to the source :p)

Thank you in advance!

---

### Post by SledgeHammer_999 on 2009-03-22
I was able to solve my problem after taking a look at the source of GtkEntry. I think you have to pay extra attention to the "realize" part of the widget's life. Here is a commented piece of code:
video_wid.h
[php]
#ifndef VIDEO_WID_H_INCLUDED

#define VIDEO_WID_H_INCLUDED

#include <gtkmm/fixed.h>


class video_wid: public Gtk::Fixed
{
    public:
    video_wid();
    ~video_wid();

    protected:
    virtual void on_map();
    virtual void on_unmap();
    virtual void on_realize();
    virtual void on_unrealize();
    virtual bool on_expose_event(GdkEventExpose* event);

    //GUI signal handlers
    void on_resize(Gtk::Allocation& allocation);

    private:
    //pointers to our Gdk Windows for easy access
    Glib::RefPtr<Gdk::Window> video_widp;
    Glib::RefPtr<Gdk::Window> display_areap;

    //helper functions
    void manage_canvas(); //resizes windows according to the available dimensions

    //helper variables
    int vid_width, vid_height, wid_width, wid_height;

};



#endif // VIDEO_WID_H_INCLUDED[/php]

video_wid.cpp:
[php]
#include "video_wid.h"

video_wid::video_wid()
{
    set_flags(Gtk::NO_WINDOW);

    //initialize these values. otherwise segafault(division by zero)
    vid_width = 1;
    vid_height = 1;
    wid_width = 1;
    wid_height = 1;

    signal_size_allocate().connect(sigc::mem_fun(this, &video_wid::on_resize));
}

video_wid::~video_wid()
{
}

void video_wid::on_map()
{
    Gtk::Widget::on_map();
}

void video_wid::on_unmap()
{
    Gtk::Widget::on_unmap();
}

void video_wid::on_realize()
{
    Gtk::Widget::on_realize();
    GdkWindowAttr attributes;

    Gtk::Allocation allocation = get_allocation();

    attributes.x = allocation.get_x();
    attributes.y = allocation.get_y();
    attributes.width = allocation.get_width();
    attributes.height = allocation.get_height();
    attributes.event_mask = get_events () | Gdk::EXPOSURE_MASK | GDK_BUTTON_PRESS_MASK;
    attributes.window_type = GDK_WINDOW_CHILD;
    attributes.wclass = GDK_INPUT_OUTPUT;

    video_widp = Gdk::Window::create(get_parent_window(), &attributes, GDK_WA_X | GDK_WA_Y);

    unset_flags(Gtk::NO_WINDOW);
    set_window(video_widp);

    //receive events
    video_widp->set_user_data(gobj());

    attributes.x = 0;
    attributes.y = 0;
    attributes.width = allocation.get_width();
    attributes.height = allocation.get_height();
    attributes.event_mask = get_events () | Gdk::EXPOSURE_MASK | GDK_BUTTON_PRESS_MASK;
    attributes.window_type = GDK_WINDOW_CHILD;
    attributes.wclass = GDK_INPUT_OUTPUT;

    //As a parent window it has THIS widget's window(which was set above)
    display_areap = Gdk::Window::create(get_window(), &attributes, GDK_WA_X | GDK_WA_Y);
    //receive events
    display_areap->set_user_data(gobj());

    set_style(get_style()->attach(get_window()));

    //different colors to distinguish visually the 2 Gdk::Windows
    Gdk::Color color("red");
    Gdk::Color color1("green");

    get_colormap()->alloc_color(color);
    get_colormap()->alloc_color(color1);

    video_widp->set_background(color);
    display_areap->set_background(color1);

    //necessary for the second window to show
    display_areap->show();

}

void video_wid::on_unrealize()
{
    video_widp.clear();
    display_areap.clear();
    Gtk::Widget::on_unrealize();
}

bool video_wid::on_expose_event(GdkEventExpose* event)
{
    return true;
}

void video_wid::on_resize(Gtk::Allocation& allocation)
{
    if (wid_width != allocation.get_width() || wid_height != allocation.get_height())
    manage_canvas();
}

void video_wid::manage_canvas()
{
    //find the ratio of vid_width/vid_height
    float ratio = vid_width/vid_height;
    //find which is bigger and expand canvas to fill the space of the minimum size of the window
    if (vid_width <= vid_height)
    {
        vid_height = get_height();
        vid_width = vid_height*ratio;
    }
    else
    {
        vid_width = get_width();
        vid_height = vid_width/ratio;
    }

    //check if it fits on the container's size. else shrink it
    if (get_width() < vid_width)
    {
        vid_width = get_width();
        vid_height = vid_width/ratio;
    }

    if (get_height() < vid_height)
    {
        vid_height = get_height();
        vid_width = vid_height*ratio;
    }

    //if canvas size smaller than the container then center the canvs in the container
    if (get_width() > vid_width && display_areap) display_areap->move((get_width() - vid_width)/2, -1);
    if (get_height() > vid_height && display_areap) display_areap->move(-1, (get_height() - vid_height)/2);

    wid_width = get_width();
    wid_height = get_height();
    if (display_areap) display_areap->resize(vid_width, vid_height);

}[/php]

But now I have a new problem. Please take a look at this thread->[link](http://ubuntuforums.org/showthread.php?p=6936709#post6936709)

---

