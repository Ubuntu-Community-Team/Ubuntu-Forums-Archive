---
title: "wxWidgets commands and events"
date: 2007-08-29
forum: Programming Talk
---

### Post by aquavitae on 2007-08-29
wxWidgets has a great framework for documents: use the right menu ids and all the open/save/close/undo/etc stuff is done automatically.  What seems strange it there doesn't seem to be an easy way to extend that.  If I want to create a new command, with menu and toolbar buttons, I need to:
1. Create a new wxCommand class.
2. Create a new event.
3. Add a menu item.
4. Link the event to the menu item
5. Add a toolbar button.
6. Link the event to the toolbar button.
7. Bind the event to a local function.
8. Within the function, call the command class.

I'm using wxPython, but the procedure seems the same with c++.  Now what would seem logical to me is this:
1. Create a new command class, defining toolbar/menu text, icon and shortcut key, as well as do() and undo() functions:
```

# In python:
class MyCommand():          # MyCommand(wxCommand)?
   def __init(self)__:
      text="my command"
      icon=newicon
      shortcut="Ctrl-M"
   def Do():
      print "Do MyCommand"
   def Undo():
      print "Undo MyCommand"

```
2. Add the command to the menu and toolbar
```

command=MyCommand()
menu.Append(command)
toolbar.Append(command)

```
The idea is this should automatically set the menu text and such like stuff, and when the menu is clicked should call command.Do().

Maybe I'm just missing something...
Is there a way to do something along the lines of what I'm talking about?  Other than rewritting wxMenu that is :)

---

