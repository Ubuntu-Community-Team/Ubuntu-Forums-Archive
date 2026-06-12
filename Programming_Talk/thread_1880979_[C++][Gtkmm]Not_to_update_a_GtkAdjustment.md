---
title: "[C++][Gtkmm]Not to update a Gtk::Adjustment"
date: 2011-11-14
forum: Programming Talk
---

### Post by ehmicky on 2011-11-14
Hi everyone,

I'm currently facing a problem with Gtkmm : I've got a pop-up like this :
[IMG]http://ubuntuone.com/4OWfl9qrND4q7XpcJrvksV[/IMG]
The HScale behaves as a scrollbar for the text below (the text being inserted in a ScrolledWindow).
I think the page and step increments, i.e. the amount of space shifted  for each key stroke (Right, Left, PageUp, PageDown) is too large, and  I'd like to decrease it. So I changed the Gtk::Adjustment associated  with the HScale and the ScrolledWindow, and modified the page et step  increment. However, those attributes are being updated every single time  something changes, for example, when I resize the window. So when I  resize the window, my previous modification of the Gtk::Adjustment is  undone. I'd like to know if there was a way to keep the modifications of  those two attributes, while Gtkmm updates the other as he wants ?
Source code :
```
#include    <gtkmm.h>
#include    <iostream>
#include    <boost/bind.hpp>

class MyWindow : public Gtk::Window
{
    protected:
        Gtk::VBox m_vbox;
        Gtk::ScrolledWindow m_scrollwin;
        Gtk::Label m_label;
        Gtk::HScale m_scale;
        Glib::RefPtr<Gtk::Adjustment> m_adjust;
        Gtk::Button m_button_set_values, m_button_show_values;
        void setValues( void )
        {
            m_adjust->set_step_increment( m_adjust->get_step_increment() / 4 );
            m_adjust->set_page_increment( m_adjust->get_page_increment() / 4 );
        }        
        void showValues( void ) const
        { 
            std::cout << "Step increment : " << m_adjust->get_step_increment() 
                << ", Page increment : " << m_adjust->get_page_increment() << std::endl;
        }
    public:
        MyWindow( void ) 
            : m_label( "This text is really really, but I mean reallly long" ), 
                m_adjust( Gtk::Adjustment::create( 0, 0, 0 ) ),
                m_button_set_values( "Set values" ),
                m_button_show_values( "Show values" )
        {
            add( m_vbox );
            m_vbox.pack_start( m_scale );
            m_vbox.pack_start( m_scrollwin );
            m_vbox.pack_start( m_button_set_values );
            m_vbox.pack_start( m_button_show_values );
            m_scrollwin.add( m_label );
            m_scale.set_adjustment( m_adjust );
            m_scrollwin.set_hadjustment( m_adjust );
            m_button_set_values.signal_released().connect( boost::bind( &MyWindow::setValues, boost::ref( *this ) ) );
            m_button_show_values.signal_released().connect( boost::bind( &MyWindow::showValues, boost::cref( *this ) ) );
            show_all_children();
        }
};

int main(int argc, char* argv[])
{
    Gtk::Main kit( argc, argv );
    MyWindow mainwindow;
    Gtk::Main::run( mainwindow );
    return 0;    
}
```
Test :
```
$ g++ a.cpp -Wall -Wextra $(pkg-config gtkmm-3.0 --cflags --libs) && ./a.out
Step increment : 8.7, Page increment : 78.3
Step increment : 2.175, Page increment : 19.575
Step increment : 23.1, Page increment : 207.9
Step increment : 5.775, Page increment : 51.975
```
The button "Get values" show the values of the increment, and "Set  values" modifies it according to the way I want it to be modified.
Here the first value is the initial one, then the one after pressing  "Set values". The third one is the one after resizing the window. The  last one is the one after pressing "Set values" again.

I don't see the point of being able to change the increment property of a  Gtk::Adjustable if most actions, including window resizing, erase those  modifications : is there a solution to this problem ? Thanks a lot :)

---

### Post by ehmicky on 2011-11-14
I'm sorry, I just found out the solution, although I've been looking for it the whole day : using the signal_changed() to update the increment according to the new upper(), lower() and page_size() attributes. :)

---

