---
title: "[gtkmm] Getting Reference to Menu Item from UIManager"
date: 2010-12-20
forum: Programming Talk
---

### Post by dwhitney67 on 2010-12-20
I'm evaluating gtkmm to see how it compares with OSF Motif in as far as developing a GUI is concerned.  One thing that has me stumped is how to get a reference to a ToggleButton that has been created as a menu item in a UIManager.

Here's a snip of the code I am using:
```

...
   m_refActionGroup = ActionGroup::create();
...
   m_refActionGroup->add(Action::create("OptionsMenu", "Options"));
   m_refActionGroup->add(ToggleAction::create("AlarmNotif", "Alarm Notification"), sigc::mem_fun(*this, &EventDisplay::alarmNotificationCB));
...
   m_refUIManager = UIManager::create();
   m_refUIManager->insert_action_group(m_refActionGroup);

   add_accel_group(m_refUIManager->get_accel_group());

   Glib::ustring ui_info = "<ui>"
                           "  <menubar name='MenuBar'>"
                           ...
                           "    <menu action='OptionsMenu'>"
                           "      <menuitem action='AlarmNotif'/>"
                           ...
                           "  </menubar>"
                           "</ui>";

   try
   {
      m_refUIManager->add_ui_from_string(ui_info);

      Widget* menubar = m_refUIManager->get_widget("/MenuBar");       // works!
      Widget* togBut1 = m_refUIManager->get_widget("/AlarmNotif");   // fails!

      ...
   }
   catch (const Glib::Error& e)
   {
      std::cerr << "Building menus failed: " << e.what() << std::endl;
   }

```
As shown above, I can successfully get the MenuBar, which is then packed into the VBox.  However, when I attempt to get the AlarmNotif menu item, I get a NULL pointer result.

What is the proper way to get a reference to this object?  During initialization of my Window, I want to set the ToggleButton using set_active().

Btw, I am currently referencing the following [gtkmm documentation]("http://library.gnome.org/devel/gtkmm-tutorial/stable/"); is there anything else that is better and more comprehensive in scope?

---

### Post by dwhitney67 on 2010-12-21
Well, I figured it out, after "endless" Googling.  It's unfortunate the the Gnome Gtkmm documentation was written by lazy developers.

The proper way to reference an entry within a UIManager is to provide the full-path to the object within the hierarchy, not just the end-name as I was attempting to do.

So the correct way would be:
```

...
Widget* menubar = m_refUIManager->get_widget("/ui/MenuBar");
Widget* togBut  = m_refUIManager->get_widget("/ui/MenuBar/OptionsMenu/AlarmNotif");

```

Of course, I realized that I would later require the reference to the toggle button, thus it was probably in my best interest to create a reference to it while setting up the menu, thus obviating the need to seek the reference as shown above.  So in lieu of the above, this is what I did:
```

...
m_refActionGroup->add(Gtk::Action::create("OptionsMenu", "Options"));

m_alarmNotifToggle = Gtk::ToggleAction::create("AlarmNotif",    "Alarm Notification", "", true);
m_refActionGroup->add(m_alarmNotifToggle, sigc::mem_fun(*this, &EventDisplay::alarmNotificationCB));

```
where m_alarmNotifToggle is declared in the header file as:
```

Glib::RefPtr<Gtk::ToggleAction> m_alarmNotifToggle;

```

---

