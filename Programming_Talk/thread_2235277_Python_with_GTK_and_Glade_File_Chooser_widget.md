---
title: "Python with GTK and Glade: File Chooser widget"
date: 2014-07-20
forum: Programming Talk
---

### Post by Dave.YNA on 2014-07-20
Hello All,
    Bit of a novice at programming in general. Recently I have been trying to turn one of my python scripts into a GUI version using Glade. My question is what is the correct way to call the file chooser widget from a .glade file? Currently I have no problem getting dialogues and windows to appear by using the get_object() function then calling .show()

However this does not work for the file chooser widget. I am not seeing any errors being generated when calling my method but I am also not seeing the file chooser widget appear. 

```
 def file_chooser(self):
  self.builder.get_object("filechooserwidget").show()
```

Perhaps get_object is not the correct way to call it? 

I have seen examples online with GTK.FileChooserWidget but as far as I can tell that is for generating one from scratch rather than getting the one out of the glade file.

---

