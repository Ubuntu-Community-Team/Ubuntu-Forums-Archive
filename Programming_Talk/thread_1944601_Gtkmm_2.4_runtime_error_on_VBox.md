---
title: "Gtkmm 2.4 runtime error on VBox"
date: 2012-03-21
forum: Programming Talk
---

### Post by marcux on 2012-03-21
Hi all!
I am following a tutorial to test menues out.
Ok, I do it my own way but using the tutorial to look at.
I have commented out most of my code and found out that I get a runtime error on a VBox.
I have doublechecked the tutorial and can not find what I am doing wrong.
Error message:
glibmm:ERROR:objectbase.cc:78:void Glib::ObjectBase::initialize(GObject*): assertion failed: (gobject_ == castitem)
Avbruten (SIGABRT)

My header file:
```

#ifndef MAINWINDOW_H
#define MAINWINDOW_H

#include <gtkmm.h>

class MainWindow : public Gtk::Window
{
 public:
  MainWindow();

 private:
  Gtk::VBox m_box;
  Glib::RefPtr<Gtk::UIManager> refUIManager;
  Glib::RefPtr<Gtk::ActionGroup> refActionGroup;
  Gtk::Button open;
  
  void create_menu();

  void on_action_file_open();
  void on_action_file_exit();
  void on_action_file_new();
  void on_action_help_help();
  void on_action_help_about();
};
#endif

```and my cpp-file:
```

#include "mainwindow.h"
#include "../files.h"
#include <glibmm/i18n.h>

MainWindow::MainWindow()
  :open(_("Open Project"))
{
  set_title("Handle Project");
  set_icon_from_file("images/HaPr_high_80x100_ver2.gif");
  show_all_children();
}

void MainWindow::create_menu()
{
 
}

void MainWindow::on_action_file_open()
{

}

void MainWindow::on_action_file_exit()
{
  hide();
}

void MainWindow::on_action_file_new()
{

}

void MainWindow::on_action_help_help()
{

}

void MainWindow::on_action_help_about()
{

}

```I have tried to create a VBox variable in the constructor ant that does not give a 
runtime error. It will not show its children though.

Many thanks in advance!
Marcux

---

