---
title: "pyGTK/Glade weird problem with hide/show of File Chooser"
date: 2011-03-30
forum: Programming Talk
---

### Post by KonfuseKitty on 2011-03-30
In a Python GUI application created with Glade, I have an Open menu command that opens a File Chooser with the following line in callback function:
 
 
```
self.openDialog1.show()
```
 
 
The File Chooser dialog window contains a Cancel button to hide the window with:
 
 
```
w=widget.get_parent_window()
w.hide()

```
The problem is that once the dialog is hidden by clicking on Cancel, it doesn't show when Open is selected from the menu again (even though I've confirmed the callback function does run, without errors). On the other hand, if the window is hidden by a callback connected to the delete-event of the window - clicking on its close button - there's no problem with re-showing it. Would anyone know what's wrong here?
 
 
I have found an inelegant workaround:
 
 
```
self.openDialog1.reshow_with_initial_size()
```
 
 
This shows the dialog again no matter how it was hidden, but it isn't ideal as it shows the dialog at minimum size first before resizing it.
 
EDIT: I have basically solved the problem by using the same callback fuction from the Cancel button as from the delete_event for the window, by calling it from the GtkWidget rather than GtkButton signal handler. The distinction matters because GtkButton passes 2 parameters, but GtkWidget 3. Still, it would be good to know why the hiding by reference to the button's parent window caused .show() not to work.

---

