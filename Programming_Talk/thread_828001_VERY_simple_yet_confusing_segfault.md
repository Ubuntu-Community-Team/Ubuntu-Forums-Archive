---
title: "VERY simple yet confusing segfault"
date: 2008-06-13
forum: Programming Talk
---

### Post by harb37 on 2008-06-13
Hello everyone. I have a seemingly simple problem that is stumping me. I compiled and ran the example code for the Gtk::TextView property [**here**]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-textview-examples.html"). I tried building off of this by adding a Gtk::Entry widget to the class in the header file... 

class ExampleWindow : public Gtk::Window 
{ 
public: 
  ExampleWindow(); 
  virtual ~ExampleWindow(); 

protected: 

  virtual void fill_buffers(); 
  
  //Signal handlers: 
  virtual void on_button_quit(); 
  virtual void on_button_buffer1(); 
  virtual void on_button_buffer2(); 

  //Child widgets: 
  Gtk::VBox m_VBox; 

  Gtk::ScrolledWindow m_ScrolledWindow; 
  Gtk::TextView m_TextView; 
  
  Glib::RefPtr<Gtk::TextBuffer> m_refTextBuffer1, m_refTextBuffer2; 

  Gtk::HButtonBox m_ButtonBox; 
  **Gtk::Entry m_Entry;**
  Gtk::Button m_Button_Quit, m_Button_Buffer1, m_Button_Buffer2; 
}; 

With that one little change to the header file, the program compiles but segfaults at this location. Something else that I might note is that I tried the converse of this (tried adding a textview widget inside the entry example code) and I got the same results. Is there something I'm missing?

---

### Post by Zugzwang on 2008-06-13
> **harb37 said:**
> 
With that one little change to the header file, the program compiles but segfaults at this location. Something else that I might note is that I tried the converse of this (tried adding a textview widget inside the entry example code) and I got the same results. Is there something I'm missing?

That's a class declaration. The program can't segfault there (it might do so in the constructor). Use valgrind to find out where the first error occurs.

---

### Post by harb37 on 2008-06-15
Ok, here is the error I get...

==8635==    by 0x4A9A801: (within /usr/lib/libgobject-2.0.so.0.1200.11)
==8635==    by 0x4A98A7A: g_object_newv (in /usr/lib/libgobject-2.0.so.0.1200.11)
==8635==    by 0x4A995EE: g_object_new_valist (in /usr/lib/libgobject-2.0.so.0.1200.11)
==8635==    by 0x4A9979F: g_object_new (in /usr/lib/libgobject-2.0.so.0.1200.11)
==8635==    by 0x4801237: gdk_display_open (in /usr/lib/libgdk-x11-2.0.so.0.1000.11)
==8635==    by 0x47DECFE: gdk_display_open_default_libgtk_only (in /usr/lib/libgdk-x11-2.0.so.0.1000.11)
==8635== 
==8635== LEAK SUMMARY:
==8635==    definitely lost: 12,490 bytes in 52 blocks.
==8635==    indirectly lost: 28,240 bytes in 1,398 blocks.
==8635==      possibly lost: 89,621 bytes in 199 blocks.
==8635==    still reachable: 1,177,084 bytes in 10,823 blocks.
==8635==         suppressed: 0 bytes in 0 blocks.
==8635== Reachable blocks (those to which a pointer was found) are not shown.
==8635== To see them, rerun with: --show-reachable=yes

Not quite sure what this means, since I'm new to valgrind. Anyone have any ideas?

---

