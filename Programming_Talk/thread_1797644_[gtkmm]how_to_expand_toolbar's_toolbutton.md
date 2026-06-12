---
title: "[gtkmm]how to expand toolbar's toolbutton ?"
date: 2011-07-05
forum: Programming Talk
---

### Post by yahyai-0 on 2011-07-05
Hi

how to expand toolbar's toolbutton ?
there is no 
    toolb_update.expand(true);

```
#include <gtkmm.h>




class MyWindow: public Gtk::Window 
{
public:
    MyWindow(); 
    virtual ~MyWindow();

protected:
    
    //signal handler
    void on_update_clicked();
    void on_fix_clicked();
    void on_restore_clicked();
    void on_info_clicked();
    void on_about_clicked();
    void on_close_clicked();
    
    //widgets
    Gtk::VBox main_box , toolbar_box , infobar_box; //layouts
    Gtk::Toolbar toolbar;
    Gtk::ToolButton toolb_update , toolb_fix, toolb_restore, toolb_info, toolb_about,    toolb_close; //toolbar buttons
    Gtk::TreeView treeView;
    Gtk::ScrolledWindow scrolled_treeView;
    Gtk::InfoBar infobar;
    Gtk::Label  infobar_label;
...
..
.
```imp

```
#include "mywindow.h"
MyWindow::MyWindow()
  
{
    //window properties
    set_border_width (30);
    set_title("Bug Fixer 1.0");
    
    add(main_box);

    //TOOLBAR
    //add toolbuttons to the toolbar
    main_box.add(toolbar_box);
    toolbar.append(toolb_update);
    toolbar.append(toolb_fix);
    toolbar.append(toolb_info);
    toolbar.append(toolb_about);
    toolbar.append(toolb_close);

    //packing and toolbar properties
    toolbar_box.pack_start(toolbar);
.....
...
..
.
    
```????

---

