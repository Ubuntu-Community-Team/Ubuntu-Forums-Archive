---
title: "[Gedit] writing gedit plugin, shortcut problem"
date: 2008-11-10
forum: Programming Talk
---

### Post by kasztan on 2008-11-10
Hi,
I'm trying to develop a "text navigation" gedit plugin. Do you know how to make these shortcuts below working? (Some shortcut are working, but not all. I would like to e.g. override <control>l, and define <control>; )
```
      ('CursorRight',         None, 'Cursor Right',     '<Control>;',        'Move cursor one character right',                                           self.cursor_right),
      ('CursorRightSelection',None, 'Right Selection',  '<Shift><Control>;', 'Move cursor one character right and select',                	          self.cursor_right_selection),
      ('CursorLeft', 	      None, 'Cursor Left',      '<Control>j',        'Move cursor one character left',                				  self.cursor_left),
      ('CursorLeftSelection', None, 'Left Selection',   '<Shift><Control>j', 'Move cursor one character left and select',                	          self.cursor_left_selection),
      ('CursorUp',            None, 'Cursor Up',        '<Control>l',        'Move cursor one line up',                                                   self.cursor_up),
      ('CursorUpSelection',   None, 'Up Selection',     '<Shift><Control>l', 'Move cursor one line up and select',                                        self.cursor_up_selection),
      ('CursorDown',          None, 'Cursor Down',      '<Control>k',        'Move cursor one line down',                                                 self.cursor_down),
      ('CursorDownSelection', None, 'Down Selection',   '<Shift><Control>k', 'Move cursor one line down and select',                                      self.cursor_down_selection),
```

I paste that code into the "line_tools.py" plugin (I wanted to have a working base). Functions cursor_up, cursor_up_selection etc. are correct.

---

