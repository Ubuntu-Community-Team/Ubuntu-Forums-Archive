---
title: "modifying Gtk/Python UI"
date: 2012-05-01
forum: Programming Talk
---

### Post by hojjat on 2012-05-01
I am trying to modify a GEdit plug-in that is written in Gtk/Python. The plugin adds a menu item using add_ui_from_string() function, and the UI string is this:

```

ui_str = """
<ui>
    <menubar name="MenuBar">
        <menu name="SearchMenu" action="Search">
            <placeholder name="SearchOps_3">
                <menuitem name="Regular expression..." action="RegexSearch"/>
            </placeholder>
        </menu>
    </menubar>
</ui>
"""

```
What I want to do is to add a keyboard-shortcut for this added menu item. I couldn't find the relevant documentation; any help is appreciated.

---

### Post by r-senior on 2012-05-01
The shortcut key, aka the accelerator, is associated with an action. In your case that is "RegexSearch". I believe you need to find the code that creates the action and set the accelerator key there.

It's difficult to predict exactly what you are looking for, but something along these lines:

```
actions = [
    ('[COLOR="Blue"]EditRedo[/COLOR]',
        Gtk.STOCK_REDO, None, [COLOR="Red"]'<Ctrl>Y'[/COLOR],
        'Redo',
        self.delegate.on_menu_edit_redo
    ),
]
action_group.add_actions(actions)

```

You'd be looking for RegexSearch rather than EditRedo, that's just an example.

These are the documents for PyGTK and actions/action groups, which might give you some clues as to what to search for.

[http://developer.gnome.org/pygtk/stable/class-gtkaction.html](http://developer.gnome.org/pygtk/stable/class-gtkaction.html)
[http://developer.gnome.org/pygtk/stable/class-gtkactiongroup.html](http://developer.gnome.org/pygtk/stable/class-gtkactiongroup.html)

---

### Post by hojjat on 2012-05-01
Excellent answer! Here is the relevant part of the code:

```

        action = Gtk.Action("RegexSearch", _("Regular expression..."), _("Search using regular expressions"), None)
        action.connect("activate", self.on_open_regex_dialog)

        action_group = Gtk.ActionGroup("RegexSearchActions")
        action_group.add_action(action)

        manager = self._window.get_ui_manager()
        manager.insert_action_group(action_group, -1)
        manager.add_ui_from_string(ui_str)

```

Based on the documentation, I should use add_action_with_accel instead of add_action, and then I have to define the accelerator. Can you show me an example of how an accelerator is defined?

---

### Post by r-senior on 2012-05-01
The accelerator is pretty simple, just a string. See the part I highlighted in red?

The string is parsed internally by gtk_accelerator_parse:

[http://developer.gnome.org/gtk/2.24/gtk-Keyboard-Accelerators.html#gtk-accelerator-parse](http://developer.gnome.org/gtk/2.24/gtk-Keyboard-Accelerators.html#gtk-accelerator-parse)

If you don't know the name for a particular key, you need to find gdkkeysyms.h, which is a C header file, and use the part after GDK_KEY_:

[http://developer.gnome.org/gdk/stable/gdk-Keyboard-Handling.html#gdk-keyval-from-name](http://developer.gnome.org/gdk/stable/gdk-Keyboard-Handling.html#gdk-keyval-from-name)

---

