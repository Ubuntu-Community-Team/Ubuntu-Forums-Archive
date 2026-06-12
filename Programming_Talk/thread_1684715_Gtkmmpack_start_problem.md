---
title: "Gtkmm::pack_start problem"
date: 2011-02-09
forum: Programming Talk
---

### Post by geltonas on 2011-02-09
Hi I new to Gtkmm and I'm gettinng runtime error with exit vaalue 1.
I assume it has something to do with the last vbox.pack_start(togglb1), but whyn I dont really dont what is causing  since the container should accept or display its contents as many as I put them. 

```

/* 
 * File:   main.cpp 
 * Author: cppguy 
 * 
 * Created on 07 February 2011, 22:20 
 */ 

#include <cstdlib> 
#include "newfile.hpp" 
#include "gtkmm/main.h" 

using namespace std; 

/* 
 * 
 */ 
int main(int argc, char** argv) { 

    Gtk::Main k(argc,argv); 
    window wi; 
    Gtk::Main::run(wi); 
    return 0; 
} 

/* 
 * File:   newfile.hpp 
 * Author: cppguy 
 * 
 * Created on 07 February 2011, 22:22 
 */ 

#ifndef NEWFILE_HPP 
#define NEWFILE_HPP 
#include "gtkmm/window.h" 
#include "gtkmm/scrollbar.h" 
#include "gtkmm/adjustment.h" 
#include "gtkmm/box.h" 
#include "gtkmm/label.h" 
#include "gtkmm/scale.h" 
#include "gtkmm/togglebutton.h" 
class window:public Gtk::Window{ 
public: 
    window(); 
    ~window(); 
private: 
    
    Gtk::VScrollbar bar; 
    Gtk::Adjustment adjust_bar; 
    Gtk::HBox hbox; 
    Gtk::VBox vbox; 
    Gtk::Label label,togg_label; 
    Gtk::HScale hscale; 
    Gtk::ToggleButton togglb,togglb1; 
}; 

#endif /* NEWFILE_HPP */ 

#include <gtkmm-2.4/gtkmm/container.h> 
#include <sigc++-2.0/sigc++/functors/ptr_fun.h> 
#include <sigc++-2.0/sigc++/functors/mem_fun.h> 

#include "newfile.hpp" 
#include "gtkmm.h" 
#include <iostream> 
#include "gtkmm/togglebutton.h" 

window::window(): 
        adjust_bar(3.0,0.0,30.0), 
        hbox(false,15), 
        vbox(false,15), 
        label("Pastumdykmane!!! "), 
        togg_label("ksdjnsd"), 
        togglb("Paspausk mane!!! "), 
        togglb1("nespausk manes!! ") 
        
        
{ 
    
    set_border_width(5); 
    set_title("slankiklis"); 
    bar.set_adjustment(adjust_bar); 
    hscale.set_adjustment(adjust_bar); 
    
    hbox.pack_start(bar); 
    hbox.pack_start(vbox); 
    
    vbox.pack_start(label); 
    vbox.pack_start(hscale); 
    vbox.pack_start(togglb); 
    vbox.add(togg_label); 
    vbox.pack_start(togglb1);  
    
    add(hbox); 
    
    show_all_children(); 
} 
window::~window(){} 


```

---

### Post by SledgeHammer_999 on 2011-02-09
Instead of **vbox.add(togg_label);** try **vbox.pack_start(togg_label);**

---

