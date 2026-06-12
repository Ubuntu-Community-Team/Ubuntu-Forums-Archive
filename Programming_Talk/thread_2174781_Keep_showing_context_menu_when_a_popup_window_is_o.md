---
title: "Keep showing context menu when a popup window is opened"
date: 2013-09-16
forum: Programming Talk
---

### Post by parinporecha on 2013-09-16
[COLOR=#000000][FONT=Arial]I am trying to show a calendar from a context menu. At first, I included it as a 'Gtk.MenuItem', but after reading [this]("http://stackoverflow.com/questions/11132929/showing-a-gtk-calendar-in-a-menu") answer, I am now showing the calendar as a popup window when the user hovers over a menu item.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]When the user hovers over 'Set due date', the calendar is supposed to show up right beside it. It is shown when 'activate' signal ( 'on_set_due_via_calendar' ) fires from the 'Set due date' menu item. Here's the code for it -
[/FONT][/COLOR]
```
[COLOR=#00008b]def[/COLOR] on_set_due_via_calendar(self, widget):
    rect = widget.get_allocation()
    x, y = widget.window.get_origin()
    menu_width, menu_height = widget.get_toplevel().window.get_size()
    calendar_width, calendar_height = self.calendar.get_size()
    self.calendar.show_at_position(x + rect.x + calendar_width + menu_width,
                                                 y + rect.y + calendar_height)

```[COLOR=#000000][FONT=Arial]
The problem I'm facing is that the menu disappears as soon as the window is shown ( Perhaps it works that way ). I want it to keep getting displayed until the user clicks somewhere else ( i.e. - Treat the calendar as a submenu ).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Here are the screens showing the issue - [IMG]http://i.imgur.com/OqKfgvX.png[/IMG] [IMG]http://i.imgur.com/MLraUgd.png[/IMG]


[/FONT][/COLOR]

---

### Post by ofnuts on 2013-09-16
Why don't you follow UI standards and let the menu hide? Or make your whole calendar a real submenu... there are visual clues that make users expect a given behavior. If your user has to use the submenu items in sequence, may be you should have a "wizard" instead.

---

### Post by parinporecha on 2013-09-16
Making the whole calendar a submenu will not make it work. User will be able to select it, but not the dates inside it.
Yes, UI standards dictate that arbitary widgets should not be placed inside a menu, but here the case is different. I merely want to show the calendar beside the menu, not make any big changes.

A wizard will be an overkill, as the functionality can be achieved in just 2 steps (right-click, hover on 'set due' and click on a date)

If you know a solution to this, please share it :-)

---

### Post by r-senior on 2013-09-16
I would not use the context menu to set values in the row, e.g. start date. It's too fiddly: right click, move, wait, move again and left click.

Think about trackpads as well as mice.

I'd have a left-click show the calendar directly from that column. Click, move, click. For bonus points, make it a text entry field for quick entry of date in locale format. 

Don't forget to support data entry solely from the keyboard.

---

