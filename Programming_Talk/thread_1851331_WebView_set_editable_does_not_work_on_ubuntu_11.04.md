---
title: "WebView set_editable does not work on ubuntu 11.04"
date: 2011-09-28
forum: Programming Talk
---

### Post by Yoana148 on 2011-09-28
Hello all,

 I am using pywebkitgtk (version-1.1.8 ) on ubuntu 11.04 and trying to set_editable property on webkit html editor.

 Problem is in WebView.load_html_string, It displays widget with html content correctly but widget is readonly (even after set_editable(True)).

 Here, code snippets:
 
 ```
 import gtk, webkit, os

w = gtk.Window()
w.set_title("Example Editor")
w.connect("destroy", gtk.main_quit)
w.resize(500, 500)

editor = webkit.WebView()
editor.load_html_string("<p>This is a <b>test</b>", "file:///")
editor.set_editable(True)

def on_action(action):
  editor.execute_script(
    "document.execCommand('%s', false, false);" % action.get_name())

actions = gtk.ActionGroup("Actions")
actions.add_actions([
  ("bold", gtk.STOCK_BOLD, "_Bold", "<ctrl>B", None, on_action),
  ("italic", gtk.STOCK_ITALIC, "_Italic", "<ctrl>I", None, on_action),
  ("underline", gtk.STOCK_UNDERLINE, "_Underline", "<ctrl>U", None, on_action),
])

ui_def = """
<toolbar name="toolbar_format">
  <toolitem action="bold" />
  <toolitem action="italic" />
  <toolitem action="underline" />
</toolbar>
"""

ui = gtk.UIManager()
ui.insert_action_group(actions)
ui.add_ui_from_string(ui_def)

vb = gtk.VBox()
vb.pack_start(ui.get_widget("/toolbar_format"), False)
vb.pack_start(editor, True)

w.add(vb)
w.show_all()

gtk.main()
```

With same code, widget is editable in Ubuntu 10.04

What could be the problem ?

Thanks in advance!

---

