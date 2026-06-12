---
title: "Glade dialog button response id grayed out"
date: 2014-06-23
forum: Programming Talk
---

### Post by philip10 on 2014-06-23
[http://stackoverflow.com/questions/24301475/glade-dialog-button-response-id-grayed-out](http://stackoverflow.com/questions/24301475/glade-dialog-button-response-id-grayed-out)

How do you give a button a response ID without putting it in the action area?

How do you create an extra action area to put more buttons in?

How do you put the entire dialog into the action area so that all buttons have a response ID?

Am I attacking this from the wrong angle?

---

### Post by philip10 on 2014-07-08
Ok I think I'm attacking this from the wrong angle. I will create a sub window instead of a sub dialog. Then I will try to hook button events in the same way I do for the main window.

Unfortunately I'm having problems compiling this though. Any ideas what the problem might be?

console output:
```

g++ main.cpp examplewindow.cpp subwindow.cpp -o testsubwindow.exe -I .\ %GTKMM_INCLUDES% %GTKMM_LIBS% 
\AppData\Local\Temp\ccekbJuk.o:examplewindow.cpp:(.text+0x1b0d):
undefined reference to `ExampleSubWindow::~ExampleSubWindow()'
\AppData\Local\Temp\ccekbJuk.o:examplewindow.cpp:(.text+0x1b1e):
undefined reference to `ExampleSubWindow::~ExampleSubWindow()'
c:/mingw/bin/../lib/gcc/mingw32/4.8.1/../../../../mingw32/bin/ld.exe: 
\Local\Temp\ccekbJuk.o: bad reloc address 0xf in section `.text$_ZN
4sigc8internal8slot_repC2EPFPvS2_ES4_S4_[__ZN4sigc8internal8slot_repC2EPFPvS2_ES
4_S4_]'
collect2.exe: error: ld returned 1 exit status

```

main.cpp:
```

#include "examplewindow.h"
#include <gtkmm/application.h>

int main(int argc, char *argv[])
{
  Glib::RefPtr<Gtk::Application> app = Gtk::Application::create(argc, argv, "org.gtkmm.example");

  ExampleWindow window;

  //Shows the window and returns when it is closed.
  return app->run(window);
}

```

examplewindow.h:
```

#ifndef GTKMM_EXAMPLEWINDOW_H
#define GTKMM_EXAMPLEWINDOW_H

#include <gtkmm.h>

class ExampleWindow : public Gtk::Window
{
public:
  ExampleWindow();
  virtual ~ExampleWindow();

protected:
  //Signal handlers:
  void on_button_clicked();
  void on_button2_clicked();
  void on_about_dialog_response(int response_id);

  //Child widgets:
  Gtk::Box m_VBox;
  Gtk::Label m_Label;
  Gtk::ButtonBox m_ButtonBox;
  Gtk::ButtonBox m_ButtonBox2;
  Gtk::Button m_Button;
  Gtk::Button m_Button2;
  Gtk::Window m_SubWindow;
  Gtk::AboutDialog m_Dialog;
};

class ExampleSubWindow : public Gtk::Window
{
    public:
        ExampleSubWindow();
        virtual ~ExampleSubWindow();
        
    protected:
        void on_button3_clicked();
        
        Gtk::Box s_VBox;
        Gtk::ButtonBox s_ButtonBox3;
        Gtk::Button s_Button3;
};

#endif //GTKMM_EXAMPLEWINDOW_H

```

examplewindow.cpp:
```

#include "examplewindow.h"
#include <iostream>

ExampleWindow::ExampleWindow()
: m_VBox(Gtk::ORIENTATION_VERTICAL),
  m_Label("The AboutDialog is non-modal. "
    "You can select parts of this text while the AboutDialog is shown."),
  m_ButtonBox(Gtk::ORIENTATION_VERTICAL),
  m_ButtonBox2(Gtk::ORIENTATION_VERTICAL),
  m_Button("Show AboutDialog"),
  m_Button2("Show SubWindow")
{
  set_title("Gtk::AboutDialog example");

  add(m_VBox);

  m_VBox.pack_start(m_Label);
  m_Label.set_line_wrap(true);
  m_Label.set_selectable(true);

  m_VBox.pack_start(m_ButtonBox);
  m_ButtonBox.pack_start(m_Button);
  m_Button.signal_clicked().connect(sigc::mem_fun(*this,
              &ExampleWindow::on_button_clicked) );
    
    m_VBox.pack_start(m_ButtonBox2);
    m_ButtonBox2.pack_start(m_Button2);
    m_Button2.signal_clicked().connect(sigc::mem_fun(*this, &ExampleWindow::on_button2_clicked));

  m_Dialog.set_transient_for(*this);

  m_Dialog.set_program_name("Example application");
  m_Dialog.set_version("1.0.0");
  m_Dialog.set_copyright("Murray Cumming");
  m_Dialog.set_comments("This is just an example application.");
  m_Dialog.set_license("LGPL");

  m_Dialog.set_website("http://www.gtkmm.org");
  m_Dialog.set_website_label("gtkmm website");

  std::vector<Glib::ustring> list_authors;
  list_authors.push_back("Murray Cumming");
  list_authors.push_back("Somebody Else");
  list_authors.push_back("AN Other");
  m_Dialog.set_authors(list_authors);

  m_Dialog.signal_response().connect(
    sigc::mem_fun(*this, &ExampleWindow::on_about_dialog_response) );

  show_all_children();

  // The widget must be realized and mapped before grab_focus() is called.
  // That's why it's called after show_all_children().
  m_Button.grab_focus();
}

ExampleWindow::~ExampleWindow()
{
 
}

void ExampleWindow::on_about_dialog_response(int response_id)
{
  std::cout << response_id
    << ", close=" << Gtk::RESPONSE_CLOSE
    << ", cancel=" << Gtk::RESPONSE_CANCEL
    << ", delete_event=" << Gtk::RESPONSE_DELETE_EVENT
    << std::endl;

  if((response_id == Gtk::RESPONSE_CLOSE) ||
     (response_id == Gtk::RESPONSE_CANCEL) )
  {
    m_Dialog.hide();
  }
}

void ExampleWindow::on_button_clicked()
{
  m_Dialog.show();

  //Bring it to the front, in case it was already shown:
  m_Dialog.present();
}

void ExampleWindow::on_button2_clicked()
{
    ExampleSubWindow subWindow;
    subWindow.show();
}

```

subwindow.cpp
```

#include "examplewindow.h"
#include <iostream>

ExampleSubWindow::ExampleSubWindow()
: s_VBox(Gtk::ORIENTATION_VERTICAL),
    s_ButtonBox3(Gtk::ORIENTATION_VERTICAL),
    s_Button3("Test activation")
{
    add(s_VBox);
    
    s_VBox.pack_start(s_ButtonBox3);

    s_ButtonBox3.pack_start(s_Button3);
    
    s_Button3.signal_clicked().connect(sigc::mem_fun(*this,
              &ExampleSubWindow::on_button3_clicked) );
}

void ExampleSubWindow::on_button3_clicked()
{
    std::cout << "Working yet?" << std::endl;
}

```

Edit: Nevermind I figured out what was wrong with my little project. Still don't know what is wrong with the example but the main thing for me is the subwindow need to be created with "new" otherwise it will be deleted straight away.

```

    ExampleSubWindow *subWindow = new ExampleSubWindow();

```

---

