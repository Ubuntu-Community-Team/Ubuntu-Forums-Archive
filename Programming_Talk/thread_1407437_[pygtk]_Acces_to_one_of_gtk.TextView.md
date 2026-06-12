---
title: "[pygtk] Acces to one of gtk.TextView"
date: 2010-02-15
forum: Programming Talk
---

### Post by alexster on 2010-02-15
Hi to all. I have a prob with get or set text in gtk.TextView. I have form and on it i have on gtk.Notebook with some tabs. On the my notebook in each tab i have gtk.TextView. TextViews added automatically with add new notebook's tab. I have code:
```

def new_tab(self):
      scrolled_window = gtk.ScrolledWindow()
      
      self.add(scrolled_window)
      scrolled_window.add_with_viewport(self.editor_access())
 
      scrolled_window.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
      
      label = self.create_tab_label("New File",self.editor_access)
           
      self.set_tab_label_packing(scrolled_window,False,False,2)
      self.set_tab_label(scrolled_window,label)
      
      label.show_all()

      return self.editor

```
Where editor_acces it's:
```

def editor_access(self):
      self.editor = Editor()
      return self.editor

```
and Editor:
```

class Editor(gtk.TextView):
  
  def __init__(self):
    gtk.TextView.__init__(self)

```

And i have one question. How can i get text for example from textview which locate on third notebook's tab or any. For example: I have 3 notebook's tab and textview on each. I want to save text from second textview into simple file, how can i get access to second textview?

Thank you.

---

