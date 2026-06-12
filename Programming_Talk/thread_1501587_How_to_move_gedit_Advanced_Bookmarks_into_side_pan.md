---
title: "How to move gedit Advanced Bookmarks into side pane from bottom pane"
date: 2010-06-04
forum: Programming Talk
---

### Post by dubref on 2010-06-04
I have [Advanced Bookmarks]("http://code.google.com/p/advanced-bookmarks-gedit-plugin/") installed in gedit

Since screen vertical real estate is always at premium I would like to move bookmark display into the side pane. :)

Playing around with regular gedit plugin Preferences did not yield anything.

Then I took a look into Python files for the plugin.
Somewhere around lines 129-140 of window_helper.py lies the answer.
```
        # Create layout table
        table = gtk.Table(2, 1)

        table.attach(self._pane,    0, 1, 0, 1)
        table.attach(self._btn_hbox, 1, 2, 0, 1, 0)

        table.show_all()

        # Install layout table into bottom pane
        pane = window.get_bottom_panel()
        pane.add_item(table, _('Bookmarks'), self._icon)
```

It is probably something like pane = window.get_side_panel(), but perhaps someone has experience with moving gedit plugins around?

---

